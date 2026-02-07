+++
title = "Don't be that person: find, don't hide"
date = "2025-11-05T11:49:58+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = ""
tags = ["dont-be-that-person", "go"]
keywords = ["go", "golang", "debugging", "mutex", "root cause analysis", "software engineering", "best practices"]
description = "A mysterious exitFunc led me to a 4-year-old workaround hiding a mutex bug. Instead of fixing the root cause, someone had silently restarted the pod on panic. A reminder that masking problems robs you of growth—always dig deeper and find the real bug."
showFullContent = false
readingTime = true
hideComments = true
+++

The other day, I was working on improving some cache code when I stumbled upon something peculiar: a struct member that turned out to be a function. Its name? `exitFunc`. That's... unusual, to say the least. My curiosity was piqued, and I decided to dig deeper. What I found is a cautionary tale about the temptation to sweep problems under the rug.

## Down the Rabbit Hole

I started by tracing what `exitFunc` was initialized to: `os.Exit()`. Even more intriguing! So I followed the trail to see where this function was actually being called.

What I found was a function preceded by an enormous comment—over 30 lines long. The gist of it went something like this:

> Four years ago, all goroutines got blocked and the system came to a halt. We didn't really understand what happened, but if it ever occurs again, we'll just exit the binary completely so that Kubernetes can restart the pod. So we added a panic handler that calls `os.Exit()`.

Oh, and that panic handler? It doesn't log anything at all. Silent failure at its finest.

In other words: "Out of sight, out of mind. Nobody will notice."

## Finding the Real Bug

Curious about what could cause all goroutines to block, I started examining the code more closely. That's when I found this gem:

```go
mu.Lock()
// lots of stuff that can panic
// including array lookups
mu.Unlock()
```

The mutex lock is acquired, then a bunch of operations that can panic are performed, and only then is the mutex unlocked. If any of those operations panic, the mutex is never released—and every other goroutine waiting for that lock will be stuck forever.

The irony (or perhaps the frustrating part) is that this pattern appeared in multiple places throughout the code, including about ten lines above that very comment explaining the mysterious four-year-old incident.

The fix was straightforward: properly handle the lock/unlock with a deferred unlock, add actual logging to the panic handler, and then wait for the problem to resurface so we could identify and fix the true root cause.

## Don't Be That Person

It's easy to mask the consequences of a problem. It's much harder to actually fix its root cause. But taking the harder path always pays off in the end.

Finding the real source of a bug requires patience, skill, and perseverance. These aren't always easy to muster, especially when you're under pressure and a quick workaround is staring you in the face.

If you ever find yourself in this situation, resist the urge to hide the problem. Dig in and search for the cause. If you can't figure it out on your own, ask for help. But never settle for a band-aid solution.

When you sweep bugs under the rug, you're not just leaving a ticking time bomb for your colleagues—you're also robbing yourself of an opportunity to learn and grow as an engineer. Every hard bug you solve makes you better at your craft.

So please: find, don't hide.
