**We recommend that if you've never used Rust before, you should check out the [Getting started guide]
in addition to [the Rust book]. There are also many other great tools available at the [Rust learning page].
You should also check out the [Rust website] for up-to-date information.**

# Introduction

The TI-Nspire has many options for writing programs. The calculator officially supports Lua, and
Ndless programs are typically written in C or C++. This project aims to add Rust to that list of
supported languages.

## What is Ndless?

[Ndless] is a popular program written for the TI-Nspire, which allows running arbitrary code,
bypassing TI's restrictions. It has a complete toolchain for compiling, linking, and packaging
TI-Nspire programs.

## What is Rust?

[Rust] is a modern language that's main focus is safety. For example, if you never type the word
`unsafe` in your code, **your program will never segfault**. It has no runtime or overhead (such
as in Python, Go, Java, JS, or C#)—just
straight machine code. Its zero-cost abstractions allow you to feel like you're writing in a high
level language, but compiles down to exactly what you would write in C or assembly. Rust was the
most loved language in the 2016, 2017, 2018, and 2019 StackOverflow Developer Survey. In
benchmarks, Rust is usually in between C and C++ in terms of speed, but while maintaining an
easy-to-use syntax with extremely helpful error messages, that often provide the fix in the
message. Rust uses [RAII], meaning that no garbage collector is needed, but there is no need to
manually allocate and free memory. Rust combines speed of procedural languages with the ease-of-use
of functional languages in one, creating one powerful language.

> # Note
> As ndless does not feature a full OS, only `#![no_std]` features are available. These include the
> [core], [alloc], and [ndless][ndless-rs] libraries. The Rust `std` library **is not available**.
> However, the [ndless][ndless-rs] crate attempts to recreate as many of the features in `std`.
> This means that any crates used will need to support `no_std`. This may involve configuring
> special features in your `Cargo.toml`.

[core]: https://doc.rust-lang.org/nightly/core/
[alloc]: https://doc.rust-lang.org/nightly/alloc/
[ndless-rs]: http://docs.rs/ndless/
[Ndless]: https://github.com/ndless-nspire/Ndless 
[Getting started guide]: https://www.rust-lang.org/learn/get-started
[the Rust book]: https://doc.rust-lang.org/book/
[Rust learning page]: https://www.rust-lang.org/learn
[Rust website]: https://www.rust-lang.org/
[RAII]: https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization
[Rust]: https://en.wikipedia.org/wiki/Rust_(programming_language)
