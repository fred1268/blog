+++
title = "The productivity tax nobody is counting"
date = "2026-09-01T00:00:00+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/the-productivity-tax-nobody-is-counting.png"
tags = ["ai", "reflections"]
keywords = ["ai productivity", "artificial intelligence", "code comprehension", "code review", "developer experience", "ai coding tools", "software craftsmanship", "technical debt"]
description = "AI is making developers faster — the dashboards say so, the line counts confirm it. But writing code was never where the time actually went. Somewhere in that speed, something got lost. Nobody put it on the dashboard."
showFullContent = false
readingTime = true
hideComments = true
+++

Writing code used to be slow. Apparently, that was the problem. AI fixed it: lines per hour, features per sprint, PRs per week — the numbers are up across the board. And if you believe the dashboards, productivity has never looked better.

There's just one thing those dashboards miss: writing code was never where the time went.

## Thinking with your hands

Here's something that took me years to articulate: the act of writing code isn't primarily about producing code. It's about *thinking*.

When you sit down to implement something you've already designed, you're not just transcribing a mental blueprint — you're testing it. Each function you name, each edge case you encounter, each "wait, that won't work" moment is your brain doing real work under the cover of typing. The low cognitive load of the *act* of writing creates space for reflection. Your hands are busy; your mind is free to wander productively. It's the same reason a long walk helps untangle a hard problem, or why some people think better when they talk out loud.

I've realized over the years that what I called "writing" code was mostly *re-reading* it — passing over the same lines again and again, testing assumptions, spotting inconsistencies, making it mine. The writing was the excuse. The understanding was the point.

AI has taken that away. The writing happens in seconds. The understanding doesn't follow.

## The code that isn't yours

When the time comes for a personal review — before opening a pull request — you're now staring at code you didn't write. Not in the "I wrote this six months ago" sense, but in a deeper one: you were never fully present for its creation. You didn't feel the resistance of the tricky parts, didn't negotiate the edge cases, didn't live through the choices. It landed in your editor, and now you have to figure it out.

You know what it does — you prompted it into existence. But knowing what a piece of code does and knowing how it does it are two very different things — and it's the second kind that lets you debug it, extend it, and trust it at 3 AM.

That takes longer than people admit. What used to be a natural conclusion to a thought process is now a reverse-engineering exercise. As I've written, [programming was always an intellectual game](/posts/why-i-code-it-was-never-about-the-output/) — the output was just proof you'd played it well. When you didn't play the game, the proof feels hollow.

And peer reviewers have it even worse. Where a teammate once read your PR with the full context of the system in mind — having touched that part of the codebase, having heard you discuss the approach — they now arrive with a vague inherited understanding, largely frozen from the pre-AI era. The deeper into an AI-assisted codebase you get, the less anyone truly understands what's going out to production.

## The bill arrives at 3 AM

None of this is immediately visible. A codebase can absorb a lot of misunderstanding before it shows. Features ship, tests pass, dashboards stay green. Most developers won't review AI-generated code carefully — by pressure, by habit, or simply because nobody asks them to. So the code accumulates: vast, fast-growing, and largely unowned.

Until something breaks in production. Faster has a cost. We just haven't put it on the invoice yet.

The obvious rebuttal is that AI will solve this problem too — in a few months, it will debug and fix its own code automatically, no human required. Probably. But that only deepens the concern. We've always shipped software built on layers we didn't fully understand: the OS, the runtime, the framework. The difference is those layers were built by humans who did understand them. AI is already the first exception to that rule — we built it, we ship it, and we largely don't understand how it reaches its conclusions. An AI that now generates and maintains code is simply extending that pattern. The full stack, unknowable by design.

## Same time, more frustration

Here's the honest truth from my own experience: I've been working this way for over a year now — AI-assisted professionally, by hand on personal projects — and I don't think it's faster. Not for me, not when understanding is part of the goal.

The code writes itself quickly, yes. But to reach a pull request I can stand behind — code I understand, can explain, and would be comfortable defending at any hour — the time is roughly the same as before. The process is just different: less thinking-with-your-hands, more reverse-engineering what the AI produced. Less flow, more friction. And at the end of it, a vague dissatisfaction that didn't used to be there.

I'm also glad I still code by hand on personal projects — not just for the pleasure of it, but because it's become the only way to rebuild what AI-assisted work quietly takes away. I can understand the code AI writes at work; I'm not always sure I could reproduce it from scratch.

I'm not anti-AI. I think it has genuine strengths, and I use it every day. But I'd like us to stop calling it a productivity gain when what we're really measuring is speed, not comprehension — understanding traded quietly for throughput, and everyone hoping nobody notices until much later. Some companies have seen impressive numbers. I don't doubt it. But those numbers aren't at equal understanding, equal ownership, or equal resilience. The tax is real. It's not on the dashboard yet — but the invoice is coming.
