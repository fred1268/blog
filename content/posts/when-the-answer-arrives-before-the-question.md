+++
title = "When the answer arrives before the question"
date = "2026-06-01T00:00:00+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/when-the-answer-arrives-before-the-question.png"
tags = ["ai", "learning"]
keywords = ["ai", "knowledge", "learning", "llm", "junior developers", "rust", "software craftsmanship", "coding tools"]
description = "The demo was impressive. The slides were polished, the use cases relevant. But the moment questions started, there was nothing behind it. Producing content and having knowledge are not the same thing — and the gap between them may be wider than we think."
showFullContent = false
readingTime = true
hideComments = true
+++

A while back, a salesperson from a well-known AI lab came to visit us. Before diving in, he paused — proudly — to show us how the day's deck had been made: his model had researched our company, pulled our branding, assembled use cases tailored to our industry. To prove the point, he ran the whole thing again, live. It was polished. It was convincing. The room was impressed.

Then someone asked a follow-up question.

The answer came out thin. Then another question. Thinner still. The slides had been impressive, but there was nothing behind them. Our guest didn't know our business, hadn't worked in our sector, had never grappled with our actual challenges. He had content. He just didn't have knowledge.

## Fluent, but hollow

It won't surprise you that LLMs are exceptionally good at producing content, and getting better at it every month. That's exactly what the demo was designed to show — and on that score, it delivered.

But content and knowledge are not the same thing. Content is the output. Knowledge is what lets you interrogate that output, push back on it, know when it's wrong. The salesperson in that room had one without the other. The deck could hold up a presentation, but not a conversation.

The distinction matters more than it might seem.

## The skipped chapters

In software development, the dynamic is strikingly similar. Claude Code, Codex, Gemini — pick your tool — can implement a feature in minutes. They produce the content: working code, with explanations if you ask for them. What they can't produce is the knowledge underneath.

The problem is that knowledge doesn't come from reading the solution. It comes from *chasing* it. From hitting a wall, finding an article that points somewhere… or nowhere, following a thread, trying something that half-works, reading more, and eventually arriving at an answer that you now *own*. That process is how concepts move from abstract to intuitive. It's not efficient. It's not the point.

As I argued in [AI as an exoskeleton](/posts/ai-as-an-exoskeleton/), you can't really learn by watching YouTube videos. Watching someone else solve a problem gives you a front-row seat to the outcome while skipping everything that makes it stick. LLMs have the same effect — only faster, and more convincing.

## The language I half-learned

I've learned every programming language I know on my own, mostly through books — and the practice that made them stick. All of them except one: Rust.

I started the right way — *The Book*, then a few other well-crafted resources, then an open source backup tool and some personal projects. I built a real foundation. Then came professional code, and with it, a heavy reliance on Claude.

Suddenly I was encountering Rust concepts I hadn't reached yet — and at first, I thought I was keeping up. I understood what the generated code was doing, and that felt like enough. But understanding what something does and knowing how to wield it yourself are very different things. I'd ask the LLM to explain further, and the explanations were good — on the happy path. What they couldn't replicate was the trial and error, the wrong turns, the debugging sessions that burn a concept into memory.

The difference was striking.

## The answer that arrives too soon

My Rust experience isn't an edge case — it's the pattern. The struggle isn't a tax on learning — it *is* the learning. And with an LLM, the first several steps of that pattern simply vanish. You describe what you want, and the solution appears. This leaves you with two options, neither particularly good.

You notice something in the generated code you don't recognize, and you ask for an explanation. This requires knowing that you don't know something — and even then, the explanation arrives without the experience that would make it land. You understand the words; the concept doesn't fully root.

Or you don't notice, you review the code, it looks reasonable, you ship something you only half-understood.

I'd like to believe most developers catch these moments. I only did because I'd learned enough languages the hard way to recognize when something wasn't sticking. Most junior developers don't have that reference point.

## Tomorrow's seniors

When I see an intern or a junior developer submit concurrent code in their first pull request, I can't pretend they fully understand what a deadlock is. Not how it happens, not the conditions that produce a race condition, not the patterns that prevent them. They've shipped something that works — until it doesn't.

And those developers will soon be seniors. The ones expected to review AI-generated code critically, spot its mistakes, challenge its assumptions — work that demands exactly the kind of deep, hard-won knowledge that LLM-assisted development quietly skips.

It's hard to be optimistic about that. And if the knowledge gap widens fast enough, the question may not be whether tomorrow's seniors can challenge the machines — it may be whether we still need anyone to.
