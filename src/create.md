# Creating a Project

Run `cargo generate --git
https://github.com/lights0123/nspire-rust-template.git`. It will prompt
you to name it. After naming your project, it will create a new folder
with a Rust template.

Get started by running

```bash
cargo make dev
```

to start development. Your .tns file will be available in
`target/armv5te-nspire-eabi/debug/{{project-name}}.tns`.

When you're ready to release your application, don't forget to compile
in release mode with

```bash
cargo make release
```

Your .tns file will be available in
`target/armv5te-nspire-eabi/release/{{project-name}}.tns`
