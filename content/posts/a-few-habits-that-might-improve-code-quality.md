+++
title = "A few habits that might improve code quality"
date = "2024-09-15T10:00:00+02:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/a-few-habits-that-might-improve-code-quality.png"
tags = ["career"]
keywords = ["code quality", "code review", "software development", "coding habits", "clean code", "refactoring", "best practices"]
description = "A young developer once asked me why my code needed fewer review rounds and generated fewer bugs. I'd never really thought about it before, so I took some time to observe my own habits. Here's what I found — a few simple practices around architecture, writing, and relentless rereading that might help you too."
showFullContent = false
readingTime = true
hideComments = true
+++

The other day, a junior developer made an observation: my code seemed to require fewer review rounds and generated fewer bugs than average. He asked me how I did it. I had to give him a rather vague answer — I'd never really thought about it before.

But the question stuck with me, and I've been reflecting on it since. Here's what I came up with.

## Start with architecture

The first thing I do is probably to stop and think before writing any code. What are the core concepts my feature needs? How do they relate to each other? Do they follow a sequence? Do they compose together? If they're tangled up, that's usually a sign of poor design.

Structuring code well matters a lot for quality. The old Unix philosophy — do one thing and do it well — applies beautifully here. Making sure each class follows that principle, then applying it recursively to functions, helps ensure the code will be easier to understand and maintain.

Easier said than done, I know. But here's a trick that helps: once you've designed your class or function, ask yourself a simple question — *what does this function do?*

If your answer contains an "and" or an "or", your function is probably doing too much. Time to split it.

That tip is useful, but may be hard to put into practice for less experienced developers. Here's another one that might be easier to apply.

## How I actually write code

After the architecture step, I start writing my first function: the prototype, parameter validation, early exit conditions. Then I often pause and reread everything I've written so far. This usually leads to small adjustments — better naming, cleaner conditions, that sort of thing.

Then I continue writing the function body. Inevitably, I reach a point where I need a helper function. I place it *above* the current function and apply the same process to it. There's a reason for this: we read code from top to bottom, so having the building blocks defined first helps form a mental model before reaching the main function.

Throughout this process, I keep pausing to reread all the code I've written. And every time I make a correction, I start the rereading from the beginning. It's not uncommon for me to reread the same code twenty or thirty times before I'm done. Don't be afraid to do the same — getting intimately familiar with your own code helps you see its flaws, whatever they are.

When it's time to commit, same thing: I open the diff in my IDE and read through everything. Any change triggers a complete reread. And for the pull request? Same discipline again.

I'll admit it — this approach is slow, and I'm probably not the fastest developer around. But it clearly impacts quality, and that impact is measurable: fewer comments on PRs, fewer bugs in production.

## Your mileage may vary

I'm not claiming to have invented anything here. I simply observed how I work and did my best to articulate it, hoping it might give some ideas to those looking to improve. Whether it works for you, I can't say — but I hope it helps.
