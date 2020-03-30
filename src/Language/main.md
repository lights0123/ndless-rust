# Returning from `main`

In some code, especially related to File I/O, error handling is
important. If you would prefer to allow your application to exit with an
error while still freeing memory and closing files without creating your
own error handler, this feature is perfect for you. Simply return a
`Result` from your function. If an error occurs, then a message box will
be displayed that describes the error. This is different from using
`.unwrap` or `.expect`, as resources will be properly released, and a
nicer error is shown.

You can allow this to work on arbitrary types. Follow the documentation
of the [`Termination`] trait.

[`Termination`]: https://docs.rs/ndless/*/ndless/process/trait.Termination.html

