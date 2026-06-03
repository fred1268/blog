+++
title = "The comparison Rustaceans avoid"
date = "2026-08-01T00:00:00+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = "covers/the-comparison-rustaceans-avoid.png"
tags = ["go", "rust"]
keywords = ["rust", "go", "golang", "programming languages", "comparison", "standard library", "crates", "learning curve"]
description = "After a year of professional Rust, one pattern stands out in how the community talks about the language: the comparisons always win — but only because they pick the wrong opponent. Go, the one language that belongs in the same conversation, is conspicuously absent."
showFullContent = false
readingTime = true
hideComments = true
+++

After over a year of professional Rust — the books, the articles, the deep-dive conference talks, and a lot of practice — I have a genuine love for the language. What strikes me most is its meticulous nature: you define the rules, and the compiler enforces them with ruthless consistency. It forces you to think before you write, rather than patching up afterthoughts at runtime. It is, without a doubt, becoming my go-to language.

But even as a convert, I've noticed a pattern in how the community makes its case for the language. Engineers who've earned their stripes all agree: Rust is exceptional. And they're right. But the argument always feels tilted: the comparisons are invariably against older languages — Python, TypeScript, C++, or Java. And every time, Rust wins. Of course it does.

## Shooting fish in a barrel

Python has no serious memory safety story. TypeScript is JavaScript with a type checker bolted on and a standard library that barely exists. C++ is powerful but carries forty years of accumulated scar tissue with no memory safety by default. Java was [genuinely revolutionary](/posts/java-a-revolutionary-language-that-overstayed-its-welcome/), but spent decades adding features at the expense of coherence.

Compared to any of these, Rust looks like a spaceship — but that's not a fair fight. These languages were designed in a different era, before the industry had fully figured out memory safety, what a standard library should contain, or what first-class tooling looks like. Of course Rust wins.

Go, on the other hand, was built at the same time, with all of the above — [I've sung its praises before](/posts/in-praise-of-go/). And yet, in most Rust comparisons, it barely gets a mention.

## The opponent they'd rather not fight

Go and Rust are the same [generation of language](/posts/the-evolution-of-programming-languages/), born from the same frustrations. Comparing them requires actual nuance — which might explain why it's so rarely done thoroughly.

When comparisons do happen, some criticisms of Go are completely valid. The garbage collector is a real constraint: it makes Go a non-starter for low-level systems programming, embedded work, or anything requiring hard latency guarantees. Go's error handling, while a genuine step forward from Java and C#, can't match the expressiveness of `Result<T, E>` and `Option<T>`. And Rust's enums have no real equivalent in Go. These aren't opinions; they're architectural facts.

But then things get murkier.

## The footnote treatment

Some critics bring up Go's lack of generics before version 1.18 as if it were an embarrassing oversight. I'd argue the opposite: the Go team took the time to design the feature properly, ensuring it would integrate naturally with the rest of the language rather than feel bolted on. The result speaks for itself.

Compilation speed gets a dismissive "it's faster" in these comparisons. It's not faster — it's lightning fast.

The learning curve gets the same footnote treatment. Rust is acknowledged as "a bit steep," Go as "fairly accessible." Neither phrase comes close to reality. Beyond writing it, reading Rust from the outside is its own challenge — Go code, by contrast, tends to be self-explanatory even to the uninitiated.

## What doesn't make the scoreboard

Beyond the underplayed points, some things don't get mentioned at all.

Go's standard library is genuinely comprehensive, production-ready and maintained by the core team. Rust's ecosystem is far more uneven: serious, battle-tested crates like Tokio sit alongside a long tail of 0.x crates with no stability or maintenance guarantees — and chances are, your project will depend on at least one of them. This is a maturity issue the ecosystem will likely resolve, but right now it's a real operational concern.

Go also "fits in your head." There is generally one idiomatic way to do each thing, and that way is usually obvious. Code written by any Go developer looks roughly like code written by any other.

Rust, by contrast, has accumulated overlapping constructs for expressing similar logic. Need to test a condition and act on a value? You have `if`, `match`, `if let`, and `let else` — each with its own idiomatic context, each appropriate in slightly different situations. Learning Rust means learning not just the syntax, but the meta-rules for when each form is the *correct* one. This adds real cognitive overhead, and it's reminiscent — in spirit if not in scale — of the feature accumulation that made Java increasingly heavy over the decades.

Go evolves slowly and deliberately. New features integrate naturally because there aren't many of them. Every addition feels like it belongs.

## At least name the opponent

Go is an excellent language, and it deserves to be treated as a genuine peer rather than quietly dropped from the comparison. So is Rust — a language I've come to deeply respect, and one that keeps surprising me the more I use it. They are different tools, built for different constraints, and both deserve an honest conversation.

My probably-naive dream is a language that synthesizes the best of both: Go's simplicity, coherence, and standard library depth; Rust's type system, error handling, and performance ceiling. A language built by synthesis rather than by opposition to what came before.

Until then, at least we can stop pretending the comparison doesn't exist.
