+++
title = "Shipping fast, breaking slowly"
date = "2026-10-01T00:00:00+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/shipping-fast-breaking-slowly.png"
tags = ["ai", "reflections"]
keywords = ["100x engineer", "ai productivity", "software architecture", "code comprehension", "technical debt", "ai coding", "pull requests", "developer productivity"]
description = "AI is turning developers into pull-request machines — the numbers are real, the stories are everywhere. But shipping code and building software aren't quite the same thing. Something in the math doesn't add up."
showFullContent = false
readingTime = true
hideComments = true
+++

It's getting hard to ignore the stories. OpenAI and Anthropic have both claimed their engineers now ship dozens — sometimes over a hundred — pull requests per day. On LinkedIn and Twitter, a steady stream of startup CEOs are posting similar numbers, each one more staggering than the last. The narrative has solidified into conventional wisdom: AI makes you a 100x engineer, and if you're not seeing those numbers on your team, you're falling behind.

The story is tempting. And parts of it are even true.

## Where AI genuinely delivers

When the task in front of you is pure code production — tests, boilerplate, scaffolding, repetitive adaptations — AI is a genuine multiplier. The copy-paste-and-adapt loop that used to eat hours of a developer's week is essentially gone. Ask for a test suite, get a test suite. Ask for a migration script, get a migration script. This is real, it's valuable, and it compounds over time.

But here's the thing: tests and scaffolding represent a fraction of what developers actually do.

## The part that isn't just code

The bulk of a developer's work is building features — some highly visible, most quietly essential. And building a feature isn't just writing code. It requires something AI consistently struggles with: *architecture*.

Not architecture in the grand, whiteboard-with-rectangles sense. Architecture in the everyday sense: the decisions that determine how pieces fit together, where boundaries sit, what a module is responsible for, and what it isn't. Those decisions, made thousands of times across a codebase, are what determine whether the system stays understandable and maintainable — or quietly becomes a trap.

AI can write code. It cannot own a codebase. Left unsupervised, it will produce something that works today and fights you tomorrow. Continuously babysitting it to maintain architectural coherence isn't a productivity gain — it's a different kind of work, and a demanding one.

## The warts compound

The inevitable objection: "Architecture doesn't matter as long as it ships." And there's a version of this that's true — until it isn't.

Technical debt isn't a metaphor. It's the real, compounding cost of decisions deferred. Patch a fragile design long enough and you stop patching features — you start patching patches. Bugs multiply. Every new addition destabilizes something else. The product becomes brittle, and users notice, even if they can't name what's wrong.

So yes: a developer can absolutely ship 30 pull requests a day — provided they're willing to sit on architecture and quality. That's not a trade-off. That's borrowing against a future that will eventually collect.

## The slow work your brain does while your hands type

There's another cost, less obvious and more personal: comprehension.

Writing code is not primarily about producing code. It's about thinking. The slow, deliberate act of turning an idea into syntax is also the act of testing that idea. You feel the resistance of the tricky parts. You negotiate edge cases. You catch the assumption that doesn't hold three functions later. Your hands are busy; your mind is working.

Strip that process away — replace it with a generated block of code that appeared in under three seconds — and the understanding doesn't follow automatically. You can read the output, reason about it, convince yourself you understand it. But there's a difference between understanding what code does and knowing it deeply enough to extend, debug, or defend it under pressure. The first comes from reading. The second comes from writing.

If you want to feel this rather than just read about it, try the following: ask AI to implement something reasonably complex, review what it produces, throw the code away, and write it yourself from scratch — no AI, no peeking. If you can't, you probably shouldn't ship it. It sounds like a harsh standard, but what's surprising is how often you can't. Not because you lack the skills, but because you never really understood the code deeply enough to own it. You knew what it did. You just didn't know it.

## The review chain is also broken

At this point, the natural rebuttal is: "That's what code review is for." And it's a fair point — or it was.

Code reviews are increasingly done by AI as well. And developers are increasingly encouraged — sometimes explicitly — not to read every line in depth. After all, the AI wrote it; surely the AI can check it.

The result is a pipeline where code is generated without full comprehension, then reviewed without full comprehension, then shipped. Each step in that chain makes the next one harder: the less you understand what you're reviewing, the less useful your feedback; the less useful your feedback, the less anyone truly understands what ships.

## The reckoning doesn't come today

To ship many more PRs per day with AI, you have to be willing to compromise on architecture and quality, to accept reduced comprehension of the generated code, and to stop reading pull requests carefully. That's a lot to trade away — and the troubling part is that none of it shows up immediately.

Codebases can absorb a surprising amount of misunderstanding before the cracks appear. The metrics stay green, the features keep shipping, the dashboards look great. And then, somewhere between six months and two years later, the compound interest comes due: escalating bug rates, slowdowns in delivery, a codebase that nobody fully owns anymore. As I wrote in [The productivity tax nobody is counting](/posts/the-productivity-tax-nobody-is-counting/), the invoice is real — we just haven't received it yet.

The 100x engineer is a mirage. Not because AI isn't powerful, but because software was never mostly about writing code. It was about understanding systems, making decisions, and keeping complexity at bay. Faster typing never solved that problem. Faster generation doesn't either.
