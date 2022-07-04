# Captis - A library for capturing the screen on Linux, MacOS and Windows

It's a fairly simple library that performs _good enough_, the OS level APIs that were used are inspired by [python-mss](https://github.com/BoboTiG/python-mss).

## Specification

- **Windows** uses the [Windows GDI](https://docs.microsoft.com/en-us/windows/win32/gdi/windows-gdi) API.
- **Linux X11** uses the `RandR` extension to get information about the displays, for capturing the [XShm](https://www.x.org/releases/X11R7.6/doc/man/man3/XShm.3.xhtml) extension is used if available, otherwise we fallback to the standard protocol.
- **MacOS** _Coming soon..._

## Usage

To run this code you also need to add [image](https://lib.rs/image) crate to your project and enable the **jpeg** feature, otherwise you won't be able to save the file as **JPEG**.

The same goes for any other format as well, if you wanna treat the image as **PNG** you must enable **png** feature. Check their [documentation](https://docs.rs/image/latest/image/enum.ImageFormat.html) to see which formats are available.

```rust
use captis::init_capturer;

let capturer = init_capturer().expect("Couldn't Initialize Capturer");

let image = capturer.capture(0).expect("Couldn't Capture Screen");

image.save("test.jpeg").expect("Couldn't Save Image");

```

## Supported Platforms

- [x] Windows
- [x] Linux (X11)
- [ ] MacOS
