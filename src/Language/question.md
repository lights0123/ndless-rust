# The question mark operator, `?`

When returning a [`Result`] from a function, it can get tedious to have
to continuously check for errors from each function. Use the question
mark operator to automatically return the error if one occurs. [Check
out the docs][docs] for more on this topic.

Note that this can also be used with [`Option`] as well, where using the
`?` operator will return `None` if the value is `None`.

[docs]: https://doc.rust-lang.org/std/result/index.html#the-question-mark-operator-
[`Option`]: https://doc.rust-lang.org/std/option/index.html
[`Result`]: https://doc.rust-lang.org/std/result/index.html

