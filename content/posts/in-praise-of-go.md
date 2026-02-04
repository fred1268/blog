+++
title = "In praise of Go"
date = "2026-02-04T18:10:31+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = ""
tags = ["go", "rust", "programming"]
keywords = ["", ""]
description = "After diving seriously into Rust, I gained a fresh appreciation for Go's elegance. It fits in your head, adds features thoughtfully, ships a massive standard library, and maintains incredible backward compatibility. Far from stuck in the 70s—Go is built to last."
showFullContent = false
readingTime = true
hideComments = true
+++

Two recent events inspired me to write this post.

First, I've been getting serious about Rust. I'd dabbled before—written a few small things, read "The Book"—but recently I started using it professionally. I've read more books, written considerably more code, and I'm still very much learning. To be clear: I don't consider myself competent in Rust yet.

Second, during this learning journey, I came across an interview with Jon Gjengset where he dismissed a question about Go, arguing that the language was stuck in the 1970s.

That rubbed me the wrong way—and I say this as someone who genuinely loves Rust too. Because spending time with Rust has actually made me appreciate Go even more.

## The beauty of Go

Go isn't a perfect language. But it has qualities that are hard to ignore—and increasingly rare.

### It fits in your head

Few languages can claim this. In Go, there's almost always one—and only one—way to do something. The cognitive load stays low.

Compare this to C#. I have a project I've been porting through versions since C# 2.0, and I think I've updated how I create a data structure four times now. That simply doesn't happen in Go.

The constructs are simple, making Go approachable for beginners. But don't mistake "easy to pick up" for "easy to master"—there's depth here for those who look.

### Features are carefully weighed

The Go team doesn't add features lightly. Generics didn't arrive until 1.18 (2022). Iterators came in 1.23 (2024). Each addition is deliberate.

This stands in stark contrast to C++, Java, or C#, where it often feels like an arms race rather than a coherent vision. In Go, the language evolves thoughtfully.

### A magnificent standard library

This might be Go's greatest strength. The standard library isn't just extensive—it's well-designed and production-grade.

Where Rust took a minimalist approach, Go went maximalist. The result? You can build substantial projects importing very few external dependencies without reinventing the wheel.

In Rust, it's more complicated. Cryptography, JSON serialization, TOML parsing—none of these are in the standard library. You're reaching for crates from day one.

### Forward compatibility

Perhaps the most beautiful thing about Go is its commitment to compatibility—backward, obviously, but also to a remarkable extent, forward. Code written years ago still compiles and runs. That's incredible, and it's not something you can take for granted.

## The drawbacks are minor

Sure, Go has its annoyances. The error handling is verbose—Rust's approach with `Result` and `?` is cleaner and more modern. And one might wonder why the Go team chose `[]` for generics instead of `<>`. (I suspect it was to maintain compatibility with the pre-generics `map` syntax, but I'm not certain.)

These quirks, as tedious as they can be, pale in comparison to what Go gets right.

This doesn't mean Go should be used everywhere, or that it should replace languages like Rust. Each has its domain. But the Go authors have done masterful work.

## Built to last

Go's strengths come down to three things:

- **Purity of design** — a language that fits in your head
- **Restraint with features** — every addition carefully considered
- **Breadth of the standard library** — batteries included, and good ones

Far from being stuck in the 1970s, Go is a thoroughly modern language—just in a different register than Rust. And in my view, it will likely age better than Java ever did.
