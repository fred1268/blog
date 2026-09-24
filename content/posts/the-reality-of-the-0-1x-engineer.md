+++
title = "The reality of the 0.1x engineer"
date = "2026-11-01T00:00:00+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/the-reality-of-the-0-1x-engineer.png"
tags = ["ai", "reflections"]
keywords = ["0.1x engineer", "100x engineer", "code review", "technical debt", "software architecture", "code comprehension", "ai coding", "security"]
description = "In a previous post, we wondered why everyone else seemed to be turning into 100x engineers while we stayed at 1x. A recent all-hands gave me the answer, and it wasn't the one I expected."
showFullContent = false
readingTime = true
hideComments = true
+++

In [Shipping fast, breaking slowly](/posts/shipping-fast-breaking-slowly/), I wrote about the gap between the 100x engineer narrative and what actually happens when you try to ship that much code without sacrificing architecture, comprehension, and review quality. I wasn't seeing those numbers, and I had a theory why. What I didn't expect was for our CTO to confirm it outright, in an all-hands, a few weeks ago: stop reading and caring about every line of code.

## The Linux defense

When someone in the room asked how we'd keep understanding our own codebase if we stopped reviewing everything, the response was quick: "We run Linux in production, and none of us understand its codebase either."

It's worth sitting with that comparison for a second, because it falls apart the moment you do. It's true that nobody on our team has read the Linux kernel source. But that's not because nobody understands it. Thousands of contributors understand it extremely well, deeply, continuously, and specifically enough to review every patch that goes in. The kernel isn't uncomprehended code running on faith. It's comprehended code, just not by us.

What was being proposed at that all-hands was something else entirely: code that nobody, anywhere, fully understands anymore. That's not the Linux model. That's the opposite of it.

## Coupling doesn't care who wrote the code

Once you accept that nobody needs to fully understand the codebase, you've also, quietly, implicitly, accepted that it can accumulate coupling without anyone noticing. It's easy to quickly bolt a feature onto whatever's already there; it's much harder to do so within an architecture built to outlive that feature. Skip that harder step often enough, and the shortcuts start touching each other. And coupling is where the real damage lives.

We already know, from decades of hard-won experience, that this kind of problem gets exponentially harder to fix the longer it's left alone. And we know that throwing more hands at it, human or artificial, doesn't solve it, because the fix was never about hands. It's about having a coherent mental model of how the system is supposed to work, and disciplined enough engineering to keep the code faithful to that model over time.

That model is abstract. It lives in judgment, in context, in years of scar tissue from past incidents. It's about as human a thing as software engineering has left. AI doesn't have one, and asking it to maintain architectural coherence is asking it to do the one thing it fundamentally can't.

## Beyond the functional bugs

And that's just the functional risk, the bugs that make a feature misbehave. There's a second category that worries me more: nobody is auditing this code for security anymore either. If no one is reading it, how would anyone catch the flaw before it ships? Vulnerabilities don't announce themselves; they hide in exactly the kind of code nobody looked at closely.

Dependencies make this worse, not better. An AI assistant is perpetually happy to pull in a new package to solve a problem, with no particular preference for whether that package is well-maintained, audited, or even still supported. And if nobody's reviewing what gets pulled in, that gap goes unnoticed until it's a headline.

## QA was never the job

What struck me most about that all-hands is that it made explicit something that had been quietly implied for a while: developers are now here to verify that the code works, not to write it. I'm not sure most developers signed up for that. If they'd wanted to spend their days verifying other people's output rather than building things, they'd have applied for QA roles.

But set that aside for a moment, because there's a harder question underneath it: what does "works correctly" even mean? In a small, single-user, single-threaded program, you can answer that with reasonable confidence. In a SaaS product, and especially in a backend service sitting near the center of your architecture, the question gets a lot less comfortable. Code can seem to run successfully and still be riddled with race conditions or wide open from a security standpoint. "It works," "it's correct," and "it's correct 100% of the time" are not the same claim, and the gap between them is exactly where the danger lives.

## Fast over good, once again

What's genuinely sad about all this is that we're rotting our codebases from the inside while simultaneously reducing our own understanding of them, a two-for-one loss that doesn't show up on any dashboard until much later. And that's before even counting the intellectual surrender involved in outsourcing your judgment wholesale, or the environmental cost of running the models that make it possible.

None of this is really new, though. It fits neatly into a trend that's been building for years: the relentless push to move fast, ship fast, decide fast, at the direct expense of quality. We've just found a new, more efficient way to do the same old thing. Faster over sound. Faster over understood. Fast, once again, over good.
