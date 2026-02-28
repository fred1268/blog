+++
title = "All my wrong predictions about AI (and probably a few more)"
date = "2026-03-01T00:00:00+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/all-my-wrong-predictions-about-ai.png"
tags = ["ai", "reflections"]
keywords = ["ai", "artificial intelligence", "chatgpt", "cursor", "claude code", "predictions", "machine learning", "coding tools", "software development"]
description = "When a technology is hot, everyone feels compelled to weigh in—and it's always amusing to look back at the bad takes. Rather than laughing at others, here's a chronicle of my own wrong predictions about AI, from dismissing ChatGPT to underestimating AI coding tools."
showFullContent = false
readingTime = true
hideComments = true
+++

It's easy to laugh at other people's bad AI takes. More interesting—and more honest—is to revisit your own. Here's a tour of mine. Some I wrote down, others I merely thought. For those, you'll have to take my word.

Let's go!

## First contact: ChatGPT as a toy

Setting aside AI's ancestors (Data Science, then Machine Learning), my first real contact with AI was probably the early days of ChatGPT, late 2022 to early 2023.

Like any geek, I played with that web interface. It understood what I said and could respond "intelligently". It could translate, summarize, and rephrase text reasonably well. But on code? Absolutely nothing useful.

My conclusion: nice toy. I could see how someone who writes a lot—emails, content, documentation—might find it useful. But write code? Never.

**Wrong.**

## The compiler doesn't forgive

Despite my skepticism, I kept using ChatGPT when I could, regularly testing its coding abilities. Unsurprisingly, the results were underwhelming, which only reinforced my flawed belief.

To be fair to ChatGPT, it could explain simple code snippets. But it failed miserably when things got tricky. For instance, it completely choked on this bit of code:

```java
String[] t = new String[] { "%d\n", "Fizz\n", "Buzz\n", "FizzBuzz\n" };
for (int i = 0; i < 100; ++i)
    System.out.printf(t[3 & (19142723 >> (2 * (i % 15)))], i);
```

You understand it at first glance, of course. Don't you?

> If you ask Claude today, it explains it perfectly: "This is a clever FizzBuzz implementation using bit manipulation". Progress.

My reasoning went like this: a small "mistake" in English text won't prevent your reader from understanding the sentence, but with code, it simply doesn't compile. I saw the day when AI could actually code drifting further and further away.

**Wrong.**

## First real shock: Cursor

My first genuine AI wake-up call came with Cursor, early 2024.

This was the first time you could use AI for code without it producing complete nonsense. When you made a change in a file, Cursor would suggest similar modifications elsewhere—not simple search-and-replace, but adaptations tailored to each context. A real time-saver, and the first time I could use AI professionally.

But still not for writing code. Beyond a few generated lines, things became unusable. Autocomplete on steroids—but let's be honest, it would never write entire features.

**Wrong again.**

## Second shock: Claude Code

The next wake-up call came with Claude Code, mid-2025.

At first, I dismissed the CLI approach: a "poor" integration compared to Cursor. Everyone codes in their IDE.

But here, finally, was a tool capable of generating code autonomously. Code that required extensive review, given its middling quality. Not that it didn't work—it did—but corner cases weren't always handled, and the architecture was, let's be honest, pretty weak. Quality wasn't there.

My conclusion was that AI could probably be used when you didn't care too much about code quality (who said tests?), but not in production.

**Wrong once more.**

## Where are we now, and where are we going?

Time to risk a few more predictions that will inevitably be wrong. Consider this your opportunity to laugh at me in a few months when I write the follow-up post.

In my view, we've pushed the models more or less to their maximum—parameter counts, context windows, and so on. It feels like we're approaching an asymptote. We're now bolting things onto AI (Agents, MCP, Skills, and more recently Agent Teams) to improve it.

That said, I'm now convinced generative AI will eventually generate 100% of the code, with humans responsible for building—or, increasingly, having AI build—the tools that guide it: test harnesses, controlled environments, guardrails. And soon enough, AI will generate those too. AI building the environments that constrain the AI that builds the environments...

And here's one that's less a prediction than a hope. I've written before about [where all the computing power went](/posts/where-did-all-the-computing-power-go/). AI might be our chance to reverse that. Today's programming languages exist because *we* need readable syntax, friendly error messages, and elegant abstractions. AI doesn't. It could work in something much closer to the metal, skipping all the comfort layers we built for ourselves. A language invented for AI—and maybe by AI—that also happens to produce efficient binaries. Not human-readable, but human-*auditable*—and above all, resource-conscious.

I'd love to see that happen.

And I'll be here, in a few months, waiting to be proven wrong. Again.
