---
layout: section
---

# Setting Up a Development Environment
<!-- Working with microcontrollers involves using several tools, since we're dealing with an architecture different from your computer's and we'll have to run and debug our programs on a "remote" device. -->

---
layout: default
----

# Documentation
Without documentation, a microcontroller is pretty much impossible to work with.

The official microbit documentation is at [https://tech.microbit.org/.](https://tech.microbit.org/)

We'll also reference other technical documentation throughout.

---

# Tools
We'll use all the tools listed below.

- Rust 1.79.0 or newer toolchain.
- `gdb-multiarch`. This is a debugging tool. The oldest tested version is 10.2, but other versions will probably work as well. If your platform doesn't have `gdb-multiarch` available, `arm-none-eabi-gdb` will work.
- [`cargo-binutils`](https://github.com/rust-embedded/cargo-binutils). Version 0.3.6 or newer.
- [`probe-rs-tools`](https://probe.rs/docs/overview/about-probe-rs/). Version 0.24.0 or newer.
- On Linux and macOS: `minicom`. Version 2.7.1 is tested but others will most likely work as well.
- On Windows: `PuTTY`.

<!-- Where a minimum version is not specified, any recent version should work, but we've listed the version we have tested. -->

---
