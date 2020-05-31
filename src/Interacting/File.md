# File I/O

The `ndless` crate has the ability to interact with the nspire's file
system. It does so by maintaining an API similar to that of the Rust
standard library. [Check out the documentation][ndless::fs] for
up-to-date information.

> # Note
>
> If an absolute path is not specified, all paths are relative to the
> executable. For example, `/documents/test.tns` will always reference
> that file. However, if the executable is at
> `/documents/ndless/app.tns`, both `test.tns` and `./test.tns` will
> refer to `/documents/ndless/test.tns`. **This is different from the
> default behavior of the C version.**
>
> Remember that all paths on the TI-Nspire start with `/documents`, and
> all visible files have the extension `.tns`.
>
> Many examples here use several advanced Rust features. If you are new
> to the language, we recommend checking out the [question mark] and
> [returning from main] features.

[question mark]: ../Language/question.md
[returning from main]: ../Language/main.md

## Creating a new file

```rust
use ndless::prelude::*;
use ndless::fs::File;
use ndless::io::prelude::*;

fn main() -> ndless::io::Result<()> {
    let mut file = File::create("/documents/test.txt.tns")?;
    file.write_all(b"This replaces the contents of test.txt.tns, or creates the file")?;
    Ok(())
}
```

Another option to do the same thing:

```rust
use ndless::prelude::*;
use ndless::fs::OpenOptions;
use ndless::io::prelude::*;

fn main() -> ndless::io::Result<()> {
    let mut file = OpenOptions::new().write(true).open("/documents/test.txt.tns")?;
    file.write_all(b"This replaces the contents of test.txt.tns, or creates the file")?;
    Ok(())
}
```

## Reading a file

```rust
use ndless::prelude::*;
use ndless::fs::File;
use ndless::io::prelude::*;

fn main() -> ndless::io::Result<()> {
    let mut file = File::open("/documents/test.txt.tns")?;
    let mut contents = String::new();
    file.read_to_string(&mut contents)?;
    assert_eq!(contents, "This replaces the contents of test.txt.tns, or creates the file!");
    Ok(())
}
```

Another option to do the same thing:

```rust
use ndless::prelude::*;
use ndless::fs::OpenOptions;
use ndless::io::prelude::*;

fn main() -> ndless::io::Result<()> {
    let mut file = OpenOptions::new().read(true).open("/documents/test.txt.tns")?;
    let mut contents = String::new();
    file.read_to_string(&mut contents)?;
    assert_eq!(contents, "This replaces the contents of test.txt.tns, or creates the file!");
    Ok(())
}
```

## Viewing the contents of a directory

Be sure to check out the
[docs](https://docs.rs/ndless/*/ndless/fs/fn.read_dir.html) on this, as
there are great examples available.

```rust
use ndless::prelude::*;
use ndless::fs::PathBuf;

fn main() -> ndless::io::Result<()> {
    let path = PathBuf::from("/documents");
    let files = path.read_dir()?;
    for file in files {
        let file = file?;
        println!("Path: {:?}", file.path());
    }
    Ok(())
}
```

Another option to do the same thing:

```rust
use ndless::prelude::*;
use ndless::fs;

fn main() -> ndless::io::Result<()> {
    let files = fs::read_dir("/documents");
    for file in files {
        let file = file?;
        println!("Path: {:?}", file.path());
    }
    Ok(())
}
```

[ndless::fs]: https://docs.rs/ndless/*/ndless/fs/struct.File.html

