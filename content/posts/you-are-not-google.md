+++
title = "You are not Google"
date = "2024-04-15T21:57:18+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/you-are-not-google.png"
tags = ["programming", "career"]
keywords = ["Google", "monorepo", "Bazel", "OKR", "cargo cult", "Big Tech", "software engineering", "best practices"]
description = "What you read about Google today is their polished answer to problems from a decade ago—problems you likely don't have. Why take their medicine for a condition you probably never had?"
showFullContent = false
readingTime = true
hideComments = true
+++

Google was founded in 1998 to revolutionize search—back when AltaVista and Yahoo dominated with their Yellow Pages-style directories. Since then, Google has grown into something unprecedented: over 250 acquisitions, 80,000 engineers, thousands of teams, and a monorepo so vast it's measured in billions of lines of code and millions of files. There's really nothing else quite like it.

But here's the thing: what you see of Google today isn't what Google is today. It's what Google was years ago. And that distinction matters more than you might think.

## The Hubble effect

What has always fascinated me about space telescopes like Hubble or James Webb is that they let us see the past. Light travels at a finite speed, so what we observe today is actually the state of the universe billions of years ago—not what it looks like now.

In a surprisingly similar way, what we see of Google today is essentially their response from years ago to problems that were already old when they started solving them.

Think about it. Say Google encountered a problem in the early 2000s. It became painful after a few years. They experimented with solutions, iterated, refined. By then it's — what, 2008? 2010? Who knows. They let the solution mature for several more years before declaring victory internally. Then they share it with the world—and suddenly it's 2018. Where are they now? Probably somewhere entirely different.

This is more or less the story of OKRs at Google.

## Two things to keep in mind

First, you are not Google. And that's fine.

Second, at the scale of our industry—young and constantly evolving—what you read about Google today is essentially a polished, industrial-age answer to what were already medieval problems. By the time their solutions reach you, both the problems and the solutions have aged considerably.

This means that when you implement [insert the latest Google trend you've read about], you might be applying a dated recipe to a problem that's even more dated—and quite possibly a problem you don't actually have.

## The monorepo example

When Google started, they had two real options for building web applications: C++ or PHP. They chose C++ (Facebook, a few years later, would choose PHP). This decision was profoundly structural—you don't reverse course on a core technology choice like that, especially during hypergrowth.

Add to this Google's acquisition appetite. Each company brought its own codebase, its own tech stack, its own way of doing things. The complexity compounded. So Google built solutions: the monorepo, then Bazel, and everything that came before and after.

But what about you? Maybe you started your company a few years ago in Java, TypeScript, or Python. You haven't acquired dozens of other companies. Your codebase has a few million lines of code at most. Yet you've read those compelling case studies about Google's monorepo and Bazel. They sound impressive.

And perhaps you've hired engineers who spent the formative years of their careers at Google. For them, the monorepo isn't a solution to a specific problem—it's just how things are done. It's the norm they've internalized, the only environment they've known. When Google is your reference point, it's natural to want to replicate what worked there.

So you adopt a monorepo with Bazel. A sophisticated answer from another era, designed for challenges you've never faced — and suddenly you've created yourself a whole new class of problems you didn't have before.

## The takeaway

The next time you read something impressive about how Google operates, pause for a moment. Remember that you're looking at the past through a very long lens. The problems that drove those solutions may have little in common with the challenges you face today.

You are not Google. You don't have their scale, their history, or their specific constraints. So why would their remedies be right for you?
