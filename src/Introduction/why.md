# Why Rust?

- [Rust is fast]\: Rust is beats C++ in many cases, and C in some.
- Rust is safe: Rust guarantees safety. What does that mean? Rust
  guarantees that you will never read past the end of a pointer, `free`
  something twice (or not at all), or leak memory unless you explicitly
  tell it to. Rust eliminates the concept of `null`, and instead
  replaces it with a common language item: [`Option`]. The best part:
  Rust has a concept of zero-cost abstractions. This means that safety
  doesn't have any performance penalties!
- Rust has *very* good error messages: C++ has [long and indecipherable]
  error messages for simple problems. On the other hand, Rust error
  messages will explain exactly why your program didn't compile, give
  you a suggestion to fix it, and link you to examples of similar
  problems.
- Package manager: Rust has a very good package manager, [Cargo], which
  has many packages ready to be installed—just copy and paste a line
  from a package's page, and it will be automatically installed.
- Documentation: One of the best reasons why Rust is useful is
  documentation. Web API docs are automatically generated for every
  package on Cargo, which provides examples, explanations, and types.
  [Here's][ndless] the documentation for the ndless crate.

# Sample code

Here's a comparison of common tasks in C vs Rust.

## Formatting text

**C**

(Yes, you could use `printf` directly. This is just to show how one
would store an intermediate buffer, for purposes such as passing to
another function.)

```c
const char * msg = "message";
const int num = 5;
// First, get the size needed to store the string
// Don't forget the + 1! Otherwise, you will have a buffer overflow.
size_t needed = snprintf(NULL, 0, "%s: %d", msg, num) + 1;
// Then, make the buffer
char *buffer = malloc(needed);
// Finally, actually store it
sprintf(buffer, "%s: %d", msg, num);
// Print it
printf("%s\n", buffer);
// Later...
free(buffer);
```

**Rust**

```rust
# fn main() {
let msg = "message";
let num = 5;
// All in one step
let buffer = format!("{}: {}", msg, num);
// Print it
println!("{}", buffer);
// the buffer will automatically be freed
# }
```

[Rust is Fast]: https://benchmarksgame-team.pages.debian.net/benchmarksgame/faster/rust.html
[long and indecipherable]: https://codegolf.stackexchange.com/a/10470/29261
[Cargo]: https://crates.io
[ndless]: https://docs.rs/ndless/
[`Option`]: https://doc.rust-lang.org/stable/rust-by-example/std/option.html?highlight=Option#option

