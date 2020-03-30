# Getting Input

Currently, the `ndless` crate supports input from the keyboard and
touchpad. The [input] module contains these functions.

Use [`get_keys`] to get a [`Vec`] of [`Key`]s that are currently being
pressed. An empty [`Vec`] will be returned if no keys are currently
pressed. See the following example:

```rust,noplaypen
use ndless::input::{get_keys, Key};

let keys = get_keys();
if keys.len() == 0 { /* No keys currently pressed */ }
```

[`get_keys`]: https://docs.rs/ndless/*/ndless/input/fn.get_keys.html
[`Vec`]: https://doc.rust-lang.org/std/vec/struct.Vec.html
[`Key`]: https://docs.rs/ndless/*/ndless/input/enum.Key.html

However, a more efficient way is to use [`iter_keys`], which does not
allocate. However, it must be used immediately, as each iteration of the
loop checks if the key is being pressed at that time. For example:

```rust,noplaypen
use ndless::prelude::*;
use ndless::input::iter_keys;
for key in iter_keys() {
    println!("Key {:?} is being pressed.", key);
}
```

Additionally, it may be used like any other [`Iterator`] in Rust:

```rust,noplaypen
// Print all keys except escape
use ndless::prelude::*;
use ndless::input::{iter_keys, Key};
iter_keys()
    .filter(|key| key != Key::Esc)
    .for_each(|key| println!("Key {:?} is being pressed.", key));
```
[`iter_keys`]: https://docs.rs/ndless/*/ndless/input/fn.iter_keys.html
[`Iterator`]: https://doc.rust-lang.org/core/iter/trait.Iterator.html

## Simple (boolean) functions

| Description                                                                                                                | Function                |
|:---------------------------------------------------------------------------------------------------------------------------|:------------------------|
| Returns true if the specific key is pressed. Note that you may pass either an owned [`Key`] or a borrowed [`&Key`][`Key`]. | [`is_key_pressed`]      |
| Returns true if any buttons are currently pressed, including pushing the touchpad.                                         | [`any_key_pressed`]     |
| Returns true if the "On" key is currently pressed.                                                                         | [`key_on_pressed`]      |
| Suspends the program until [`any_key_pressed`] returns true.                                                               | [`wait_key_pressed`]    |
| Suspends the program until [`any_key_pressed`] returns false.                                                              | [`wait_no_key_pressed`] |

[`is_key_pressed`]: https://docs.rs/ndless/*/ndless/input/fn.is_key_pressed.html
[`any_key_pressed`]: https://docs.rs/ndless/*/ndless/input/fn.any_key_pressed.html
[`key_on_pressed`]: https://docs.rs/ndless/*/ndless/input/fn.key_on_pressed.html
[`wait_key_pressed`]: https://docs.rs/ndless/*/ndless/input/fn.wait_key_pressed.html
[`wait_no_key_pressed`]: https://docs.rs/ndless/*/ndless/input/fn.wait_no_key_pressed.html

[input]: https://docs.rs/ndless/input/index.html

