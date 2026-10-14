+++
title = "Who cares?"
date = "2026-12-01T00:00:00+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/who-cares.png"
tags = ["career", "reflections"]
keywords = ["corporate waste", "company money", "frugality", "ai cost", "engineering culture", "career", "startups vs big tech", "software waste"]
description = "A manager once used the company card like it was his personal piggy bank, no shame, no hesitation. It stuck with me, because my own relationship with other people's money has always been the exact opposite. So why does one attitude seem to be winning?"
showFullContent = false
readingTime = true
hideComments = true
+++

Years ago, I worked for a company that was something of a pioneer, one of the first big SaaS CRM players out there. Yes, that one. My manager at the time used the company VISA card to buy bottles of wine, or to take his family out to dinner, without a trace of hesitation or shame. On the company.

I remember being genuinely stunned by it, not in an outraged, report-him-to-HR way, but in a "wait, people actually think this is fine?" way. Because my own relationship with other people's money has always been the exact opposite.

## Spending like it's mine, because at some point, it was

I've had the unusual experience of sitting on every side of this question. When I was running my own company, naturally, every cent that went out the door felt like it was coming out of my own pocket, because it was. At another point, I was the first employee and eventual CTO of a startup, and I treated every cent with the exact same discipline. At every stage, I spent, or more accurately, saved, the company's money with the same care I'd apply to my own savings account.

Eventually I became CTO of a company with 300 employees and $50 million in revenue. The numbers were bigger, the budget lines more abstract, but the instinct stayed exactly the same: manage this with the same seriousness and the same frugality I bring to my own household.

Today, I'm an individual contributor at a large company, and I still do the same thing: I care about what a given line of code costs, and I optimize for it using whatever metrics I can find. At our scale, a single unnecessary log line can quietly cost tens of thousands of dollars a month.

## A dwindling club

Here's the uncomfortable part: I don't think I'm alone in this, but I increasingly feel like I am. It's not that everyone else has stopped being aware of what things cost, or stopped applying the same rigor they'd use with their own money. It's that the few of us who still do are being slowly outnumbered by a growing crowd who simply doesn't care anymore.

Why is the club shrinking?

## Where the instinct goes to die

The honest answer is that there's rarely any short-term incentive to care, and no, the planet doesn't factor into most people's cost-benefit analysis.

In a small company, a sliver of that incentive still exists. If the company struggles, there's no bonus, and maybe no job. Nobody puts it that bluntly to themselves, but it's usually enough to keep people careful.

Scale changes everything. Layers of management keep you far from the results, despite the all-hands meetings and their rehearsed enthusiasm. And the big numbers they show don't help: what's $10k when the company just made $10B? So common sense quietly checks out, and waste moves in to fill the space it left behind.

But here's what nags at me: managers are supposed to be closer to the numbers than that. They sit higher up, with a clearer view of what things actually cost. If anyone should feel that instinct, it's them. And yet my manager, with his wine and his family dinners, clearly felt nothing of the sort. His case was a bit extreme, I'll admit, closer to casually helping himself than to simple carelessness, but it's the same root problem wearing a bolder outfit.

## When the mirror turns

It would be easy to stop here and point at a few careless managers. But the instinct to waste rarely arrives as a grand gesture. It arrives in small, forgivable-looking decisions, the kind that don't feel like waste until you add enough of them together. And nothing invites those small decisions more than AI.

I don't want it to become my new scapegoat, blamed for every inefficiency that happens to involve a keyboard. But there's no denying that its sheer ease invites exactly this kind of waste. Everything moves faster now, which also means code gets reviewed less carefully, and what used to be tuned and optimized often just... isn't. Something that used to run in 10 milliseconds now takes 15, and nobody notices, because why would they go looking? A few unnecessary log lines get left behind here and there, quietly accumulating somewhere, at real cost, for nobody's benefit. And there's a layer most people forget: the AI call that produced the inefficient code wasn't free, and neither will be the one that eventually fixes it, if someone even cares to address it.

As I wrote in [Shipping fast, breaking slowly](/posts/shipping-fast-breaking-slowly/), the bill for all this speed doesn't arrive today. It arrives later, quietly, long after everyone's forgotten exactly which small shortcut added up to it.

And if you ask why any of this happens, the honest answer is rarely malice, and rarely even laziness in the way we usually mean it. It's just that, in the moment, with the numbers too big and the consequences too far away, the question nobody bothers to ask anymore is the simplest one: who's paying for this?

But who cares?
