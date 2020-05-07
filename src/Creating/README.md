# Creating a Project

Run `cargo generate --git
https://github.com/lights0123/nspire-rust-template.git`. It will prompt
you to name it. After naming your project, it will create a new folder
with a Rust template.

Get started by running

```bash
cargo +nightly ndless build
```

to start development. Your .tns file will be available in
`target/armv5te-nspire-eabi/debug/{{project-name}}.tns`.

When you're ready to release your application,
**don't forget to compile in release mode** with

```bash
cargo +nightly ndless build -- --release
```

Your .tns file will be available in
`target/armv5te-nspire-eabi/release/{{project-name}}.tns`.

If you have the Firebird emulator installed, you can also send the compiled
binary straight to it. Just run:

```bash
cargo +nightly ndless run
cargo +nightly ndless run -- --release
```

You may skip `+nightly` if you set nightly as your default compiler
(`rustup default nightly`), or
[set a directory override](https://github.com/rust-lang/rustup.rs#directory-overrides).
