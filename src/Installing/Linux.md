# Installing on Linux & Mac

## Install Rust
You need:
- Ndless toolchain installed and added to path
- Rustup installed
- Latest Rust Nightly installed (nightly-2020-05-07 works)
- Unix-like (tested on Linux, most likely Mac and Cygwin will work as well)

Complete install script:
```bash
curl https://sh.rustup.rs -sSf | sh # skip if rustup already installed
rustup install nightly # skip if nightly already installed
cargo install cargo-ndless
```

## Install ndless

Follow the steps described in the [Ndless wiki].

> ## Pro tip
>
> Although you can permanently add the ndless tools to your PATH as suggested in the wiki, you may not want to as that will mess with other projects that use `arm-none-eabi-gcc` and similar commands. Instead, you may set the environment variable `NDLESS_HOME` to the path to your installation of Ndless, i.e. the folder that you `git clone`d.
>
>For example, if you ran `git clone --recursive https://github.com/ndless-nspire/Ndless.git` in your home directory, you could add `export NDLESS_HOME="$HOME/Ndless"` to the end of your `~/.bash_profile`. If you're using cargo-ndless as suggested, the correct directories will automatically be added to your `PATH` variable.

[Ndless wiki]: https://github.com/ndless-nspire/Ndless/wiki/Ndless-SDK:-C-and-assembly-development-introduction
