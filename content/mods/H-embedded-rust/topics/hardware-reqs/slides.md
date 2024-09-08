---
layout: cover
---

# Hardware/Knowledge Requirements

---
layout: default
---

# Knowledge
You must know *some* Rust. It's hard to define "some", but some specifics you should be comfortable with include:
- The basics of generics and traits.
- How to use closures.
- The idioms of the current Rust edition.

---

# Hardware
To follow along with this material, you'll need
- A Micro:Bit v2 (MB2) board.
  - There are several versions of the `V2` board available. While this material was written for the `V2.00`, any `V2` board should work.

<img src="/images/microbit-v2.jpg" style="margin-top: 20%; margin-left:5%;max-width: 100%; max-height: 90%;">
- A micro-B USB cable.
  - Powers the MB2 when not using batteries, and enables communication with the board. Make sure the cable you use supports data transfer - some only support charging.

<img src="/images/usb-cable.jpg" style="margin-top: 20%; margin-left:5%;max-width: 100%; max-height: 90%;">
The official `micro:bit Go` kit provides both the USB cable and a helpful battery pack for powering the MB2 without USB.

---
# FAQ
## Why do I need this specific hardware?
It makes my life and yours much easier.
The material is much more approachable if we don't have to worry about hardware differences.
## Can I follow this material with a different development board?
This depends on your previous experience with microcontrollers and/or whether a high level crate already exists for your development board somewhere. If you plan to use a different microcontroller, check out [Awesome Embedded Rust](https://github.com/rust-embedded/awesome-embedded-rust) or search the web to find supported crates.
However, with a different development board, this material loses most if not all of its begeinner friendliness - you have been warned.
