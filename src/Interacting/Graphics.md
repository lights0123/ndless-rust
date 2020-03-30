Currently, graphics is done with SDL. Use the [ndless-sdl] crate to do
so. You'll first need to initialize the screen at the beginning of your
`main` function:

```rust,noplaypen
use ndless_sdl::{SurfaceFlag, VideoFlag};
ndless_sdl::init(&[ndless_sdl::InitFlag::Video]);
let screen = ndless_sdl::video::set_video_mode(
    320,
    240,
    16,
    &[SurfaceFlag::SWSurface],
    &[VideoFlag::NoFrame],
)
.expect("failed to set video mode");
```

Then, at the end, stop it:

```rust,noplaypen
ndless_sdl::quit();
```

Now, you can draw on the screen with the `screen` variable, which is a
[`Surface`]. Typically, you'll want to use [`fill_rect`] to draw
rectangles, [`draw_str`] to draw low-res text, and [`blit_rect`] to draw
images loaded by the [`image`] module. When you're ready to display to
the screen, call [`screen.flip()`][flip]. For a basic example, see
[hello-world-sdl]. For a more advanced example loading a real font, see
[hello-world-text]. For a real program using fonts and images, see
[n-flashcards].

[ndless-sdl]: https://docs.rs/ndless-sdl
[`Surface`]: https://docs.rs/ndless-sdl/*/ndless_sdl/video/struct.Surface.html
[`fill_rect`]: https://docs.rs/ndless-sdl/*/ndless_sdl/video/struct.Surface.html#method.fill_rect
[`draw_str`]: https://docs.rs/ndless-sdl/*/ndless_sdl/video/struct.Surface.html#method.draw_str
[`blit_rect`]: https://docs.rs/ndless-sdl/*/ndless_sdl/video/struct.Surface.html#method.blit_rect
[`image`]: https://docs.rs/ndless-sdl/*/ndless_sdl/image/index.html
[flip]: https://docs.rs/ndless-sdl/*/ndless_sdl/video/struct.Surface.html#method.flip
[hello-world-sdl]: https://github.com/lights0123/example-nspire/tree/master/hello-world-sdl
[hello-world-text]: https://github.com/lights0123/example-nspire/tree/master/hello-world-text
[n-flashcards]: https://github.com/lights0123/n-flashcards
