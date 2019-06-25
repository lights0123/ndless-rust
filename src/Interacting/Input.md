# Getting Input

Currently, the `ndless` crate supports input from the keyboard and touchpad.
The [input] module contains these functions.

Use [`get_keys`] to get a [`Vec`] of [`Key`]s that are currently being pressed.
An empty [`Vec`] will be returned if no keys are currently pressed. See the following
example:

```rust,noplaypen
use ndless::input::{get_keys, Key};

let keys = get_keys();
if keys.len() == 0 { /* No keys currently pressed */ }
```

[`get_keys`]: https://docs.rs/ndless/0.8.0/ndless/input/fn.get_keys.html
[`Vec`]: https://doc.rust-lang.org/std/vec/struct.Vec.html
[`Key`]: https://docs.rs/ndless/0.8.0/ndless/input/enum.Key.html

## Simple (boolean) functions

| Description                                                                          | Function                |
|--------------------------------------------------------------------------------------|-------------------------|
| Returns true if any buttons are currently pressed, including pushing the touchpad.   | [`any_key_pressed`]     |
| Returns true if the "On" key is currently pressed.                                   | [`key_on_pressed`]      |
| Suspends the program until [`any_key_pressed`] returns true.                         | [`wait_key_pressed`]    |
| Suspends the program until [`any_key_pressed`] returns false.                        | [`wait_no_key_pressed`] |

[`any_key_pressed`]: https://docs.rs/ndless/0.8.0/ndless/input/fn.any_key_pressed.html
[`key_on_pressed`]: https://docs.rs/ndless/0.8.0/ndless/input/fn.key_on_pressed.html
[`wait_key_pressed`]: https://docs.rs/ndless/0.8.0/ndless/input/fn.wait_key_pressed.html
[`wait_no_key_pressed`]: https://docs.rs/ndless/0.8.0/ndless/input/fn.wait_no_key_pressed.html

[input]: https://docs.rs/ndless/input/index.html
