+++
title = "You don't need Kafka: building a simple yet distributed scheduler in Go"
date = "2024-06-07T12:21:12+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/golang.png"
tags = ["go", "programming"]
keywords = ["distributed scheduler", "job scheduler", "Go", "database", "multi-tenant", "SaaS", "Kafka alternative", "task scheduling"]
description = "Building a distributed job scheduler doesn't require Kafka, Redis, or complex coordination protocols. For small-to-medium scale SaaS products, your database can handle the coordination. Here's how to build one in Go."
showFullContent = false
readingTime = true
hideComments = true
+++

## The Brief

You're building a small multi-tenant SaaS product. You need to run scheduled tasks—some system-wide (cleanup, analytics aggregation), some per-tenant (sending reports, syncing data).

You may already be thinking message queues, dead letter queues, RabbitMQ, Redis, Kafka. That works—but for a SaaS running on a handful of web servers, it's probably overkill. Your servers aren't exactly overloaded at 3am anyway—why not use those idle resources for background jobs?

## A Simpler Approach

Let's start simple. On a single server, this is a solved problem: spawn a pool of worker goroutines, feed them jobs through a channel, done. Go's concurrency primitives handle all the synchronization.

But you don't have a single server, do you? And that's where things get tricky. If each server runs its own scheduler with its own goroutine pool, they'll all try to execute the same jobs. Chaos.

We need coordination between servers. And here's the insight: you already have a coordination layer. It's called your database.

Row-level locking (`SELECT FOR UPDATE`) gives us distributed coordination for free. When a job is due, multiple servers may race to claim it—but only one will win the lock. The others back off and try the next one.

So now we have two levels of synchronization: goroutines and channels within each server, database row-level locking between servers. Getting this right requires careful attention to `Commit()` and `Rollback()` calls—one misplaced transaction boundary and your locks don't protect anything. And the two layers must stay in lockstep—more on that later.

## The Data Model

A job defines *what* to run and *when*:

```go
type Job struct {
    ID         int
    Name       string
    Type       int            // Global or Tenant-scoped
    Run        int            // Execution counter
    NextRun    *time.Time
    InProgress *time.Time
    Scheduling *JobScheduling // Frequency, recurrence, days, etc.
}
```

A run is a single execution instance:

```go
type Run struct {
    ID       int
    JobID    int
    JobName  string
    TenantID int        // For tenant-scoped jobs
    Run      int        // Which execution this belongs to
    Started  *time.Time
    Ended    *time.Time
}
```

The key fields for coordination are `InProgress` on jobs and `Started` on runs.

## How It All Fits Together

Before diving into the details, here's the big picture. The scheduler works in two phases:

1. **Run creation**: When a job is due, all servers race to create the runs. One server wins the lock (via `Job.InProgress`), creates all the runs, and commits. The others see the job is already in progress and back off. This happens at execution time, not when the job is scheduled—so tenants created after the job was defined still get their runs.

2. **Run execution**: Once runs exist, all servers race to claim them. Each server locks a run (via `Run.Started`), marks it as started, and executes it. Different servers claim different runs—the work is naturally distributed.

This two-phase approach means one server handles the fan-out (creating potentially hundreds of tenant runs), then all servers share the actual execution.

## Multi-Tenant Support

The scheduler supports two job types:

- **Global jobs**: One run per execution (system-wide tasks)
- **Tenant jobs**: One run *per tenant* per execution

When a tenant-scoped job is due, we fan out:

```go
switch job.Type {
case JobTypeTenant:
    n, err = s.runSvc.BatchCreate(ctx, job) // Creates one run per tenant
case JobTypeGlobal:
    run := &Run{JobID: job.ID, JobName: job.Name, Run: job.Run}
    err = s.runSvc.Create(ctx, run) // Creates a single run
}
```

A single job definition ("send weekly reports") automatically fans out to hundreds of tenant-specific executions—all distributed across your servers.

## The Main Loop

On startup, the scheduler spawns N worker goroutines (one per CPU):

```go
maxRunners := runtime.NumCPU()
for id := range maxRunners {
    go s.runner(ctx, id, s.runChan, s.done)
}
```

The main loop is straightforward:

1. Query the database for the next job due
2. Sleep until that time
3. Create runs for the job
4. Distribute runs to workers
5. Repeat

```go
for {
    jobs, _ := s.jobSvc.List(ctx, criteriaForNextJob)
    <-time.After(time.Until(*jobs.Items[0].NextRun))
    s.createRuns(ctx, jobs)
    s.executeRuns(ctx)
}
```

## The Distribution Magic

Here's where it gets interesting. Multiple servers run this same code. When a job is due, all of them try to create and claim runs. How do we prevent chaos?

The answer is `SELECT FOR UPDATE`:

```go
func (s *Scheduler) findNextRun(ctx context.Context) (*Run, error) {
    for {
        list, _ := s.runSvc.List(ctx, criteriaForUnstartedRuns)
        for _, r := range list.Items {
            // Pessimistic lock on this row
            run, err := s.runSvc.LockRead(ctx, r.ID)
            if err != nil {
                return nil, err
            }
            // Someone else got it first
            if run.Started != nil {
                db.Rollback(ctx)
                continue
            }
            // We got it — mark as started
            now := time.Now()
            run.Started = &now
            s.runSvc.Update(ctx, run)
            db.Commit(ctx)
            return run, nil
        }
    }
}
```

The pattern:

1. Query for unstarted runs
2. Try to lock a row (`SELECT FOR UPDATE`)
3. Check if someone else already started it (they committed before us)
4. If yes, rollback and try the next one
5. If no, mark it started and commit

This is the key insight: **the database is your distributed lock**. No Redis, no Zookeeper, no Raft. Just SQL.

## Worker Execution

Once a run is claimed, it goes into a channel:

```go
func (s *Scheduler) executeRuns(ctx context.Context) error {
    for {
        run, _ := s.findNextRun(ctx)
        if run == nil {
            break
        }
        s.runChan <- run
    }
    return nil
}
```

Workers pull from the channel and execute:

```go
func (s *Scheduler) panicSafeRunner(ctx context.Context, in <-chan *Run, done chan struct{}) error {
    for {
        select {
        case run := <-in:
            ctx = auth.NewContext(ctx, run.TenantID, run.OwnerID)
            fn := s.jobs[run.JobName]
            if err := fn(ctx, run); err != nil {
                // Rollback, clear Started, let another worker retry
                db.Rollback(ctx)
                run.Started = nil
                s.runSvc.Update(ctx, run)
                db.Commit(ctx)
                return err
            }
            now := time.Now()
            run.Ended = &now
            s.runSvc.Update(ctx, run)
            db.Commit(ctx)
            s.resetJob(ctx, run.JobID)
        case <-done:
            return nil
        }
    }
}
```

Note the tenant context: each run executes in the context of its tenant, so the job function doesn't need to worry about multi-tenancy.

## Keeping the Two Layers in Sync

Remember the two synchronization layers? Here's where they meet—and where things can go wrong if you're not careful.

The key rule: a run should only enter the channel *after* the database claim is committed. Look at how `findNextRun` and `executeRuns` work together:

```go
// findNextRun: claim via DB lock, commit, THEN return
run, _ := s.runSvc.LockRead(ctx, r.ID)  // SELECT FOR UPDATE
run.Started = &now
s.runSvc.Update(ctx, run)
db.Commit(ctx)   // commit FIRST
return run, nil  // then return

// executeRuns: push to channel only AFTER findNextRun committed
run, _ := s.findNextRun(ctx)  // already committed
s.runChan <- run              // safe to push now
```

The order matters. If you pushed to the channel before committing, another server could claim the same run before your commit goes through—and now two workers are executing the same job.

By committing first, we guarantee that by the time a run enters the channel, no other server can claim it. And if the server crashes between commit and channel push? The run has `Started` set but no `Ended`—it will be picked up on restart.

## Fault Tolerance

What happens if a server crashes mid-execution?

On restart, the scheduler picks up where it left off:

```go
for {
    // Handle potentially remaining runs (if server stopped abruptly)
    s.executeRuns(ctx)
    // Then continue normal scheduling
    s.panicSafeStart(ctx)
}
```

Runs that were created but never completed (or started but never finished) are still in the database with `Ended = nil`. They'll be picked up and retried.

## Simplicity wins

For a small-to-medium multi-tenant SaaS running on a handful of servers, you don't always need Kafka. You don't always need Redis. Sometimes your database—the thing you already have, already operate, already monitor—is enough.

The key is using `SELECT FOR UPDATE` as a distributed lock. It's not as scalable as a dedicated message broker, but it's dramatically simpler. And for many applications, simplicity wins.
