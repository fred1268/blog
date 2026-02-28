+++
title = "Understanding Go's string to byte slice conversion"
date = "2025-07-01T00:00:00+01:00"
author = ""
cover = "covers/golang.png"
tags = ["go", "performance"]
keywords = ["go", "golang", "memory allocation", "unsafe"]
description = "Ever wondered what happens when you cast a string to a byte slice in Go? This deep dive explores the runtime mechanics, memory allocation implications, and why understanding immutability matters for writing efficient Go code."
showFullContent = false
readingTime = true
hideComments = true
+++

The other day, I stumbled upon a piece of Go code that looked something like this:

```go
func StringToByteArray(s string) []byte {
    return unsafe.Slice(unsafe.StringData(s), len(s))
}
```

At first glance, this seemed odd. Was the author really reimplementing the standard `[]byte()` cast? Intrigued, I decided to dig deeper.

## The initial analysis

Looking at this code, it was clear this had to be some kind of optimization—most likely a memory optimization. But logically, a simple cast should just interpret the data (like in C), not create a new copy of it... or shouldn't it?

To find out, I headed over to my favorite tool, [Godbolt](https://godbolt.org/z/TezMhMhY8), and compiled a simple `[]byte(s)` conversion. Here's what the assembly revealed:

```assembly
MOVQ    BX, CX
MOVQ    AX, BX
XORL    AX, AX
PCDATA  $1, $1
NOP
CALL    runtime.stringtoslicebyte(SB)
ADDQ    $24, SP
POPQ    BP
RET
```

Interesting—it's calling a function!

## Digging into the runtime

So I went straight to the source: the [`runtime.stringtoslicebyte()`](https://go.dev/src/runtime/string.go) function in Go's runtime package:

```go
func stringtoslicebyte(buf *tmpBuf, s string) []byte {
    var b []byte
    if buf != nil && len(s) <= len(buf) {
        *buf = tmpBuf{}
        b = buf[:len(s)]
    } else {
        b = rawbyteslice(len(s))
    }
    copy(b, s)
    return b
}
```

Looking closer at `rawbyteslice()`, it eventually calls `mallocgc()` to allocate memory. So when you write `[]byte(s)`, you're actually calling `stringtoslicebyte()` with `buf = nil`, which means you're allocating new memory every single time.

## Lesson from the Gopher hole

There are several takeaways from this little exploration.

### Don't trust appearances

First and foremost, don't take things at face value—dig into the "why" yourself. This is especially important in the age of AI, which makes everything seem easy and has a tendency to mask the very real complexity lurking beneath the surface.

### Casts aren't always free

Second, a cast isn't always a trivial operation. Sometimes it reinterprets the data in place, and sometimes it converts it (with allocation). In this specific case, it's a conversion. Rust, by the way, would probably have made this distinction much more explicit.

Could I have figured this out without all this exploration? Absolutely. If I had taken the time to think more carefully about string immutability in Go, it would have been obvious that a simple reinterpretation—turning something immutable into something mutable—couldn't possibly be what's happening here.

### Choose the right tool for the job

Finally, if you find yourself needing to do this kind of thing in Go, maybe Go isn't the right language for your use case. Rust gives you much finer control over memory management and makes conversions like this explicit, rather than relying on implicit conventions like "don't modify the `[]byte` after conversion".

## Back to fundamentals

What started as curiosity about an unusual piece of code turned into a valuable reminder: understanding the fundamentals—like immutability—helps you reason about what the language must be doing under the hood. And when in doubt, there's no substitute for reading the source.
