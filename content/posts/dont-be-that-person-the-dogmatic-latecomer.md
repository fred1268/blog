+++
title = "Don't be that person: the dogmatic latecomer"
date = "2024-07-18T21:50:49+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/dont-be-that-person-the-dogmatic-latecomer.png"
tags = ["programming", "career", "dont-be-that-person"]
keywords = ["CQRS", "best practices", "software development", "dogmatism", "technical decisions", "engineering culture"]
description = "Best practices don't age well. They emerge to solve specific problems, and when those problems fade, so should the dogma. Before adopting any technique, ask: do the original conditions still apply?"
showFullContent = false
readingTime = true
hideComments = true
+++

The other day I met a relatively young developer who was talking to me about CQRS. Nothing wrong with that—except it wasn't really a discussion. No weighing pros and cons, no "here's when it makes sense". More like uncritical evangelism, as if CQRS were the latest breakthrough about to revolutionize everything.

In the 2020s.

I later learned he'd been implementing it systematically at every company he worked for—he was a freelancer—regardless of the actual problem at hand.

## A Brief History of CQRS

I won't attempt to plagiarize the excellent Wikipedia article or the broader literature on the subject. But here's the short version.

CQRS emerged in the late 1990s to address a fundamental tension in relational databases: it's difficult to optimize for both reads and writes simultaneously. The solution? Separate them. Optimize each independently. That's the core insight.

To understand why this mattered, you need to remember the context. SaaS was barely a concept. Coming out of the client-server era, everyone stored everything in a single RDBMS. We were still in single-core territory, and databases were notoriously hard to scale.

In that world, CQRS could make perfect sense.

## Where It Falls Short Today

First, context has changed dramatically. Multi-core processors are everywhere. Storage options have multiplied beyond recognition. Cloud infrastructure offers scaling options that didn't exist. The constraints that made CQRS necessary have largely dissolved.

Second—and the people who developed CQRS will tell you this themselves—it only makes sense in specific scenarios. You need a significant asymmetry between reads and writes to justify the added complexity. The benefits must substantially outweigh the cost of maintaining what is essentially two systems instead of one.

For most applications, a well-designed CRUD approach is simpler and sufficient.

## The Hype Cycle Problem

This brings me to a broader point about our industry.

Software development moves faster than almost any other field. What's revolutionary today is forgotten tomorrow. EJB. SOAP. XML databases. Web Components. The hype cycle is relentless.

I've [written elsewhere](/posts/the-evolution-of-programming-languages/) about how programming languages evolve in response to their era's constraints. The same applies to architectural patterns. They emerge to solve specific problems, and when those problems fade, so does their relevance.

This means dogmatism has no place in our profession. You can have convictions, certainly. But you must hold them loosely, ready to revisit them as the landscape shifts.

## Before You Adopt Anything

When you encounter a technique that's new to you, resist the urge to implement it everywhere.

Start by understanding its historical context—why was it invented, what problems did it solve? This helps you grasp not just the *what* but the *why*. Then ask yourself whether those original conditions still apply. If the constraints that justified the technique have disappeared, there's a good chance the technique has quietly expired.

And remember: truly universal techniques are rare. Most appear and disappear based on the specific problems at hand. Our industry's pace of change is simply incompatible with dogmatism.

So don't be that person: think before you implement. Understand before you preach. And regularly question your past choices against present realities—what made sense five years ago might be baggage today.
