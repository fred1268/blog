+++
title = "Don't be that person: learn first, blog later"
date = "2024-05-07T13:57:01+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/dont-be-that-person-learn-first-blog-later.png"
tags = ["dont-be-that-person", "go"]
keywords = ["go", "golang", "errors.Is", "sentinel errors", "performance", "benchmarking", "best practices"]
description = "A clickbait blog post claimed errors.Is() slows code by 3000%. The real lesson? The author misused sentinel errors for a non-error condition. Before writing hot takes, understand your tools—and check how the standard library does it."
showFullContent = false
readingTime = true
hideComments = true
+++

While scrolling through one of my favorite newsletters, I stumbled upon an article with a provocative title saying that Sentinel errors were slowing your code down by 3000%. Intriguing, I thought, and bookmarked it for later.

What I found when I finally read it is a cautionary tale about understanding your tools before rushing to publish.

## The incredible shrinking benchmark

When I opened the article, the first thing I noticed was that the title had changed. The dramatic 3000% slowdown had quietly become 500%. A sign, perhaps, that the benchmark hadn't been fully verified before hitting publish.

Still, I dove in. The gist was that the author was using a sentinel error in Go, which gets wrapped inside other errors as it bubbles up the call stack. To check for it, they used `errors.Is()`, which traverses the error chain recursively.

It's fairly clear that `errors.Is()` will be slower than a simple comparison—it has to unwrap potentially nested errors. A quick look at the source code makes this obvious:

```go
func Is(err, target error) bool {
    if err == nil || target == nil {
        return err == target
    }

    isComparable := reflectlite.TypeOf(target).Comparable()
    return is(err, target, isComparable)
}

func is(err, target error, targetComparable bool) bool {
    for {
        if targetComparable && err == target {
            return true
        }
        if x, ok := err.(interface{ Is(error) bool }); ok && x.Is(target) {
            return true
        }
        switch x := err.(type) {
        case interface{ Unwrap() error }:
            err = x.Unwrap()
            if err == nil {
                return false
            }
        case interface{ Unwrap() []error }:
            for _, err := range x.Unwrap() {
                if is(err, target, targetComparable) {
                    return true
                }
            }
            return false
        default:
            return false
        }
    }
}
```

Thirty-odd lines of code with reflection and recursion will obviously run slower than a simple boolean check. This isn't a revelation—it's how the function is designed to work.

## The real problem

But here's where it gets interesting. A quick look at the source reveals that this "discovery" is simply how the function is designed to work. The slowdown isn't a bug—it's the cost of traversing an error chain.

More importantly, if they had thought about their actual use case, they would have recognized the deeper issue: they were using an error for something that isn't an error.

The situation they described was checking whether a value exists in a cache. A cache miss isn't an error condition—it's a perfectly normal, expected outcome. It should be handled by returning a boolean, not by throwing and catching errors.

This is exactly what Go's standard library does. Look at any map-like structure: you get `value, ok := cache.Get(key)`, not `value, err := cache.Get(key)`. There's a reason for that.

And yes, `if errors.Is(err, ErrNotFound)` is *much* slower than `if !found`. But that's not a flaw in Go—it's a signal that errors aren't the right tool for this job.

## The takeaway

Before writing hot takes about performance, ask yourself a few questions:

1. **Am I using this tool correctly?** `errors.Is()` is powerful, but it's not meant for every situation. Errors should represent actual error conditions, not normal control flow.

2. **Do I know my toolbox?** Familiarity with the standard library matters. The patterns are there for good reasons—learn them before reinventing the wheel.

3. **Have I looked at how others solve this?** When building something that resembles an existing concept (like a cache), study how reference implementations handle their API and architecture.

So don't be that person: take the time to understand before you publish.
