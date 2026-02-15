+++
title = "Where did all the computing power go?"
date = "2025-02-09T10:48:21+01:00"
author = ""
authorTwitter = ""
cover = "covers/where-did-all-the-computing-power-go.png"
tags = ["software", "performance"]
keywords = ["bloatware", "software efficiency", "computing power", "performance", "resource consumption", "climate", "optimization"]
description = "From kilobytes to terabytes, from MHz to GHz, our computers are millions of times more powerful than they were decades ago. Yet everyday tasks don't feel that much faster. Where did all that power go? Perhaps it's time for intentional computing."
showFullContent = false
readingTime = true
hideComments = true
+++

## When bytes mattered

When I started in computing, we talked about KiB and MHz. And of course, there was only one CPU core to handle everything. Those constraints shaped how we thought about software: every byte mattered, every cycle counted.

Since then, thankfully, we've gained access to exponentially more power. Today we talk about GiB and TiB as well as GHz, and it's not unusual to have twenty or more cores—not even counting GPUs and dedicated AI chips. Even the earliest smartphones were considerably more powerful than my first few personal computers.

## The numbers don't add up

Compared to those early machines, we now have roughly 20,000 times the CPU power, a million times the RAM and storage.

Still, almost everything we did back then feels nearly as slow today. My source files aren't any bigger. And yet my compiler doesn't build projects any faster—in fact, it's often significantly slower. My applications don't launch a million times quicker. So we have to ask: where did all that extra power go?

## New capabilities, new demands

To be fair, some of that power has enabled genuinely new experiences. We can stream video on demand without hiccups, even on our phones. We can store thousands of high-resolution photos and videos that are far larger than anything we captured decades ago. We can video-call loved ones on the other side of the world for free, when international calls used to cost a dollar a minute just thirty years ago.

These are real improvements. But here's the thing: while my usage has evolved, I don't feel like it's evolved by a factor of twenty thousand, let alone a million. The math still doesn't add up.

## The bloatware reality

The truth is, much of that power has been absorbed by bloatware.

Consider operating systems. The old ones fit on a few floppy disks—tens of megabytes, maybe a hundred or two. Today, Windows, macOS, and even Linux distributions easily consume ten gigabytes or more. That's a hundred to a thousand times larger.

Applications that used to be written natively are now built on [Electron and a cascade of frameworks stacked on top of each other](/posts/the-lego-generation-software-development-then-and-now/). Between the JVM, the CLR, and various interpreted languages—both in production and on local machines—virtual machines are everywhere. In production, those VMs often run inside other VMs, frequently with Docker containers nested within. It's layer upon layer upon layer, none of them particularly conducive to performance.

But thanks to Moore's Law steadily delivering more power, nobody pays much attention to efficiency anymore—as long as things remain "reasonable". When performance does become a problem, the fix is usually to optimize a loop here, tweak an algorithm there, or swap out a data structure. What we almost never do is question the towering stack of technologies and abstractions we've built in the first place.

## A question worth asking

Of course, these new capabilities have enabled entirely new experiences. Streaming, sharing memories, staying connected: these are genuine improvements.

But it's worth pausing to consider: does the value we extract from all this computing power match its cost? Not just the financial cost, but the environmental footprint of data centers, the energy consumed by billions of devices, the rare earth minerals in our hardware—not to mention the insatiable appetite of AI models. I'm not saying we should stop watching videos or sharing photos—but perhaps we could be more intentional about it. The question isn't whether our new usages are "good" or "bad", but whether we've thought about the tradeoff at all.

And beyond our usage patterns, we can also ask why software itself has become so wasteful. Some of it comes down to convenience: yes, it's easier to write JavaScript than C. It's faster to ship something quickly than to build something well. But [convenience has a cost](/posts/java-a-revolutionary-language-that-overstayed-its-welcome/), and that cost is often paid in wasted resources—resources we can no longer afford to waste.

## A call for intentional computing

At a time when climate change demands we reconsider every aspect of how we consume resources, software efficiency shouldn't be an afterthought. The good news is that efficient software still exists. Projects like SQLite, VLC, or Nginx prove that you can build powerful, widely-used tools that remain lean and fast. Languages like Go and Rust are bringing performance back into the conversation. Some developers still care deeply about doing more with less.

Maybe we can't single-handedly reverse decades of bloat.

The pioneers of computing accomplished remarkable things with a fraction of our resources. John Carmack made Doom and Quake run on hardware that would make today's developers weep. Anders Hejlsberg wrote Turbo Pascal—a full compiler in hand-tuned assembly that compiled thousands of lines per second on a 4.77 MHz machine. If they could do that much with so little, the least we can do is not squander the rest.
