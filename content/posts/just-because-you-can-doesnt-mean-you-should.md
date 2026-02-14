+++
title = "Just because you can doesn't mean you should"
date = "2025-06-15T10:00:00+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/just-because-you-can-doesnt-mean-you-should.png"
tags = ["programming", "languages"]
keywords = ["programming languages", "legacy code", "technology choices", "go", "rust", "php", "ruby", "javascript", "technical debt", "startup technology"]
description = "Programming languages rarely die, but that doesn't mean they all deserve new projects. Languages are born from specific problems—and when better solutions emerge, holding on becomes a liability. Especially when you're building something that needs to last."
showFullContent = false
readingTime = true
hideComments = true
+++

We all know that [programming languages emerge and evolve over time](/posts/the-evolution-of-programming-languages/). What's less acknowledged is that very few of them actually die. The result? A sprawling landscape of languages, and not always the skills to match. When was the last time you met a COBOL developer?

But here's the thing: just because a language still exists doesn't mean you should use it.

## Languages are answers to yesterday's questions

Every language emerges as a response to a specific problem of its era. Ruby—and to some extent Python—arose as a reaction against Perl's write-only syntax. PHP was invented to make web development easier than C/C++, piggybacking on how Perl CGI scripts worked. Java arrived to solve the memory management nightmares of C and C++. More recently, Go and Rust answered the call for performance without sacrificing safety.

These "initial conditions" matter. They explain why a language looks and behaves the way it does. But languages don't stay frozen—they borrow from each other. Object-oriented programming spread from Smalltalk to C++, then to Java, and eventually got bolted onto PHP and Python. The C++ Standard Template Library arrived years after the language itself. Features migrate.

Yet some advances can't be retrofitted. Toolchains, package management, ecosystem coherence—these are structural. You can't easily graft Go's `go get` elegance onto a language designed before the internet mattered.

## Convergence doesn't mean equivalence

After decades of cross-pollination, most mainstream languages offer similar features. Generics, lambdas, async patterns—they're everywhere now. So it's tempting to think all languages are interchangeable.

They're not.

The difference lies in completeness, integration, and performance. Some languages bolted on features as afterthoughts; others were designed with them from the start. Some ecosystems are cohesive; others are a patchwork of competing tools. And when you look at it objectively, several popular languages have simply been surpassed.

This doesn't mean you should never touch them again. Retro gaming exists. People restore and drive vintage cars. If you love Ruby or PHP, by all means enjoy them in your side projects—there's genuine pleasure in that.

## The professional threshold

But starting a professional project is different. When you're building something meant to last, to scale, to be maintained by a team over years—that's when technology choices matter deeply.

Languages like Go and Rust represent the current state of the art. They're not perfect, and something will eventually replace them. But right now, choosing JavaScript or PHP for a new backend isn't just suboptimal—it's choosing yesterday's answer for tomorrow's problems.

I wrote about [Java's trajectory](/posts/java-a-revolutionary-language-that-overstayed-its-welcome/) not long ago—a language that was genuinely revolutionary in 1995 but has struggled to evolve gracefully. The same pattern applies elsewhere. Languages that were cutting-edge twenty years ago aren't necessarily the right choice today.

If you're a non-technical founder, this is where you make a ten-year commitment without even noticing. The freelancer willing to help knows PHP or JavaScript, and suddenly that defines your stack for the next decade. Resist that temptation. It might seem inconsequential early on, but the developer pool for aging technologies shrinks every year. And they'll bring the idioms and patterns of that era along with them. It's not a personal failing—languages train you to solve problems their way.

## The real distinction

There's a difference between maintaining legacy code and *choosing* to start fresh with legacy tools. The world changes. Those languages still work—and probably always will. But newer ones solve the same problems with less friction, better tooling, and fewer footguns. Acknowledging that isn't elitism—it's pragmatism.

Who would drive hundreds of miles for a vacation in a 1930s car? You could. But you probably shouldn't.
