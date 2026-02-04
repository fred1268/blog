+++
title = "The Lego generation: software development then and now"
date = "2024-01-27T21:53:33+01:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = ""
authorTwitter = "" #do not include @
cover = ""
tags = ["programming", "career", "history"]
keywords = ["", ""]
description = "A young client asked what's changed in 30 years of software development. The answer: everything and nothing. We've traded assembly for JavaScript, deep understanding for fast results, and monolithic codebases for complex toolchains. Was it better before? No. Is it perfect now? Also no."
showFullContent = false
readingTime = true
hideComments = true
+++

The other day, a young client asked me what had changed in 30 years of software development. Good question! Here's what I told him.

## Simpler and more complex at the same time

Development has become much simpler. Where we once wrote C or C++ with frequent detours into assembly—understanding how CPUs worked, how data was laid out in RAM—we now "just" write JavaScript, Python, or other high-level languages.

And yet, development has also become much more complex. Back then, we wrote all the code ourselves, in a single technology. Now, code is split across multiple technologies (at minimum, backend and frontend) and is often a complicated assembly of proprietary and open-source components.

This split has created specializations. Backend and frontend each have their own frameworks, paradigms, and best practices. Being truly "full stack" is increasingly difficult—modern frameworks demand deep knowledge that's hard to maintain across the board.

## The evolution of the developer

The developer has changed too. First, we understood things by reading documentation, books, and running experiments. Then came the Google generation, who learned to search. Then the Stack Overflow generation, who learned to copy and paste. And now we're heading straight toward the Lego generation—assembling pre-built blocks without necessarily understanding what's inside.

The result? We focus more on making things work than on understanding why they work. This gets us to results faster, sure. But when something breaks, the cost of not understanding becomes prohibitive.

## We don't optimize anymore—or not the right things

Moore's Law and the cloud have made us stop caring about what happens behind a frontend component. We'll spend time optimizing a JavaScript loop while happily making 17 REST API calls—16 of which are unnecessary.

The megabyte has become obsolete. We only talk in terabytes now. Yet I don't write more code, and my programs aren't a million times bigger. Why optimize when storage is essentially free?

## The explosion of everything

The number of languages has exploded—just look at the Stack Overflow or GitHub surveys. We often need to know several to do our jobs well. And paradoxically, we know each one less deeply than we used to.

But these languages come with standard libraries that would have seemed like magic 30 years ago. Two lines of Go to create a web server, where the simplest useful program in Windows C++ took hundreds if not thousands of lines. And don't even mention assembly.

On the flip side, languages no longer come with dedicated IDEs. Now we use the same editor for everything. (Who said VS Code?)

The number of tools has also exploded: CI, linters, code analyzers, packers, transpilers, containers, message queues, service discovery... The smallest project now involves a dozen technologies you need to know and use—even if you don't fully understand them.

## What we got right

Not everything is worse. Those deep class hierarchies from the '90s? Thankfully gone. Inheritance, once gospel, has wisely given way to composition. The "everything is an object" dogma hit its limits, and we can write procedural code again when it makes sense. Thank you, Go and Rust.

Manual memory management—responsible for countless bugs when not perfectly implemented—is largely a thing of the past. Garbage collection has become standard, with clever alternatives like Rust's borrow checker for those who need more control.

Native applications and client-server architectures have given way to web apps. More complex architecturally, yes, but so much easier to deploy and maintain. No more installing megabytes of software and pushing constant updates.

And security has finally become a topic—even if, sadly, few developers think about it daily.

## Was it better before?

No, I don't think so. Is it perfect now? Also no.

Too many technologies, too many tools doing the same thing (or not much at all). This diversity prevents us from focusing on what matters: building quality products, on time, that meet our clients' needs.

If there's a hint of nostalgia in this post, it's because I miss the emphasis on *understanding* over *making it work*. I'm not sure this shift is good for developers in the long run.

That said, I'm convinced that software development today is more interesting than ever. You can build something usable much faster. It requires knowledge across very different technologies and tools, but that diversity also gives everyone a domain to be passionate about.

We just need to remember the fundamentals: understanding *why* things work, *how* they work—rather than getting swept up in the arms race that development has become.
