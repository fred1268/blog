+++
title = "The myth of technical complexity at scale"
date = "2024-08-01T00:00:00+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/the-myth-of-technical-complexity-at-scale.png"
tags = ["career", "startups", "tech"]
keywords = ["big tech", "startups", "scale", "software engineering", "technical complexity", "error handling", "code quality", "engineering culture"]
description = "Developers at large companies often believe they're solving harder technical problems than their startup counterparts. The reality? The technical challenges are often similar—it's the politics and disengagement that make things complicated."
showFullContent = false
readingTime = true
hideComments = true
+++

## The complexity myth

There's a curious belief among developers at large companies: they tend to think they're solving far more complex technical problems than engineers at smaller shops. After spending time on both sides of that fence, I can tell you the reality is quite different. The technical challenges are roughly equivalent. What actually gets harder at scale are the political and managerial problems—and those have surprisingly little to do with engineering.

## What really happens when companies grow

As organizations expand, they face two fundamental challenges that have nothing to do with technology.

The first is communication. As the number of teams grows, the complexity of coordination increases exponentially. What used to be a hallway conversation becomes a cross-functional initiative requiring stakeholder alignment and roadmap negotiations.

The second is ownership. Early employees tend to care deeply about the product—they built it, after all. But as companies grow and new engineers join, that sense of ownership dilutes. The codebase becomes something you work *in*, not something you own.

These two forces combine to create what we politely call "organizational complexity", but what often looks more like politics. Need something from another team? You'll have to convince them it's worth their time—or negotiate a compromise that delivers half of what users actually need. And when errors pile up in production? Well, as long as nobody gets paged at 3 AM, it's easier to roll back or slap a workaround on it than to actually fix the root cause.

## The Gack Watchers

I remember when we joined Salesforce, we were asked to stay late—sometimes into the night—for production deployments. No problem; we were used to that. At our previous company, release nights meant last-minute adjustments: final tests, documentation updates, deployment pipeline tweaks.

But at Salesforce, there were no adjustments to make. Instead, our job was to watch the logs. For hours. Looking for *new* errors.

You see, the existing logs were so polluted with unaddressed errors that the only way to spot a genuine new problem was to have human eyes scanning for unfamiliar patterns. They called us "Gack Watchers"—don't ask me where the name came from.

When I asked about this, the answer was almost philosophical: "You have to understand, with this many users, there are bound to be errors. It's normal".

I found that hard to accept. At my previous company, we'd run a web application with clients handling up to 40,000 concurrent users—which translates to a much larger total user base. And yet our logs were clean. Zero errors, unless there was an actual bug to fix.

## Code is functionally deterministic

This wasn't the first time I'd heard that kind of reasoning, and it always strikes me as a fundamental misunderstanding of how software works.

Code is functionally deterministic. Given the same inputs, it produces the same outputs. Yes, even concurrent code—when written correctly. In fact, it's precisely the *non-determinism* of poorly written concurrent code that causes bugs. Sure, a network packet might occasionally vanish into the ether, or a piece of hardware might fail. But let's be honest: that doesn't happen often enough to fill your logs with errors.

So I'll say it plainly: well-written code should not produce errors under normal operation. And yet, I see more and more systems spewing exceptions like it's perfectly acceptable behavior. The worst part? Nobody seems to care. Teams normalize it. Downstream systems inherit those errors, add their own, and the whole thing compounds into a cascade of incidents.

And no, I refuse to believe that dozens of incidents per day is "normal". Some incidents are inevitable, of course. But thirty, forty, eighty a day? That's not scale—that's neglect.

## The uncomfortable truth

So here's the uncomfortable truth: developers at large companies aren't dealing with harder technical problems. They're dealing with the side effects of organizational scale—the politics, the negotiations, the gradual erosion of ownership and accountability.

The next time someone tells you in an interview that joining Big Tech will teach you so much more than a startup, take it with a grain of salt. You might learn a lot about navigating bureaucracy. But technically? The problems are the same. The difference is in how much people still care about solving them well.
