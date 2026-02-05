+++
title = "The evolution of programming languages"
date = "2024-11-21T18:32:41+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = ""
tags = ["programming", "languages", "go", "rust"]
keywords = ["programming languages", "go", "rust", "c", "java", "garbage collection", "memory management", "history"]
description = "A journey through four generations of programming languages—from procedural C to modern Go and Rust—exploring how each solved the problems of its predecessors while introducing new tradeoffs in memory management, performance, and developer experience."
showFullContent = false
readingTime = true
hideComments = true
+++

Programming languages have come a long way. What we write code in today looks nothing like what developers used decades ago. Over time, languages have evolved through at least four distinct generations, each one addressing the shortcomings of the previous while sometimes introducing new challenges of its own. Let's take a walk through this evolution.

## The procedural era

Languages like C and Pascal defined this first major era. They gave us structured programming and were a huge leap forward from assembly, but they came with some significant pain points.

The biggest issues were global state and manual memory management. When state is shared globally, any function can modify it without others being aware—leading to mysterious, hard-to-reproduce bugs. And manual memory management? That opened the door to classics like double frees, use-after-free bugs, dangling pointers, and all sorts of undefined behavior that could make debugging a nightmare.

## Object-oriented languages

Then came object-oriented programming with languages like C++, Object Pascal, Smalltalk, and Objective-C. The big promise was encapsulation: no more global state scattered everywhere. Data would live close to the methods that manipulate it, neatly bundled into objects.

This was a genuine improvement. But manual memory management? Still there. C++ developers still had to worry about when and how to free memory. And the standard libraries were often sparse—C++'s STL didn't arrive until relatively late in the language's life, leaving developers to reinvent common data structures and algorithms.

## Garbage-collected languages

Java and C# ushered in the next generation. The headline feature was garbage collection: no more manual memory management, no more double frees or use-after-free bugs. The runtime would handle it all.

These languages also brought rich, comprehensive standard libraries—a breath of fresh air compared to what came before. And they championed the "everything is an object" paradigm.

But there were tradeoffs. Performance took a hit since code compiled to bytecode for a virtual machine rather than native machine code. JIT compilation has narrowed this gap considerably over the years, but we're still not quite at native performance levels. And that "everything is an object" philosophy? It got pushed too far, resulting in sprawling class hierarchies that we've thankfully moved away from.

## Modern languages

This brings us to Go and Rust, two languages that set out to solve the performance overhead of VM-based languages while keeping the memory safety gains. They took very different paths to get there.

Both compile to native code, sidestepping the JVM or CLR entirely. But their approaches to memory diverge sharply. Go includes a garbage collector—a small runtime handles memory for you. Rust, on the other hand, enforces strict ownership rules through its famous borrow checker, achieving memory safety at compile time without a GC.

Both languages stepped back from the "everything is an object" mindset, embracing regular functions alongside methods. Both are careful about global state, though Rust is stricter here. And both ship with substantial standard libraries, though Go's is considerably broader than Rust's.

Another major contribution from this generation is tooling. Go and Rust didn't just ship a compiler—they brought an entire ecosystem out of the box. Language servers for IDE integration, built-in package managers for third-party libraries, formatters, linters, profilers, and more. This "batteries included" approach to developer experience set a new standard that previous generations simply didn't have.

These design choices lead to different sweet spots. Go's garbage collector means it can't quite reach the bare-metal performance needed for systems programming or real-time applications—areas where Rust truly shines. But Rust's strictness comes at a cost: a much steeper learning curve that puts more burden on the developer.

Overall, both languages have their strengths and areas of excellence. Choosing between them depends on what you're building and what tradeoffs you're willing to make.

## What's next?

The evolution isn't stopping. Several promising languages are on the horizon.

Zig is positioning itself as a path to modernize C codebases, offering a gentler migration for systems programmers. How Zig and Rust will coexist in the systems programming space remains an open question—both target similar use cases, and it's unclear today whether they'll carve out distinct niches or compete head-on. Gleam is building bridges to functional programming, bringing those concepts to a broader audience.

And there are many others vying for attention—perhaps too many to keep track of. If you're curious about what's brewing, check out [this curated list](https://news.ycombinator.com/thelang).

The only certainty is that programming languages will keep evolving, each generation learning from the last.
