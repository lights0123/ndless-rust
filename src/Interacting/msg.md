# Message Boxes
There are various types of message boxes with `ndless`.
The following message boxes are supported:

| Type                                                 | Function         |
|------------------------------------------------------|------------------|
| Title, message, OK Button                            | [`msg`]          |
| Title, message, 2 custom buttons                     | [`msg_2b`]       |
| Title, message, 3 custom buttons                     | [`msg_3b`]       |
| Title, message, string input with default            | [`msg_input`]    |
| Title, message, numeric input with min/max           | [`msg_numeric`]  |
| Title and two messages & numeric inputs with min/max | [`msg_2numeric`] |

[`msg`]: https://docs.rs/ndless/0.8.0/ndless/msg/fn.msg.html
[`msg_2b`]: https://docs.rs/ndless/0.8.0/ndless/msg/fn.msg_2b.html            
[`msg_3b`]: https://docs.rs/ndless/0.8.0/ndless/msg/fn.msg_3b.html            
[`msg_input`]: https://docs.rs/ndless/0.8.0/ndless/msg/fn.msg_input.html      
[`msg_numeric`]: https://docs.rs/ndless/0.8.0/ndless/msg/fn.msg_numeric.html  
[`msg_2numeric`]: https://docs.rs/ndless/0.8.0/ndless/msg/fn.msg_2numeric.html

Use it like this:

```rust,noplaypen
fn main() {
	ndless::msg::msg("Title", "Message");
}
```

Message boxes with more than one button return a variant of
[Button]. Use it like:

```rust,noplaypen
fn main() {
	let button_pressed = msg_3b("Hello", "Hello, World!", "1", "2", "3");
	let message = match button_pressed {
		Button::ONE => "one",
		Button::TWO => "two",
		Button::THREE => "three",
	};
}
```

Pressing escape will return the [first button].

[Button]: https://docs.rs/ndless/0.8.0/ndless/msg/enum.Button.html
[first button]: https://docs.rs/ndless/0.8.0/ndless/msg/enum.Button.html#variant.ONE
