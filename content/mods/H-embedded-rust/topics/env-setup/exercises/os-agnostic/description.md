# `rustc` and `Cargo`
Install rustup by following the instructions at [https://rustup.rs/](https://rustup.rs/).

If you've already installed rustup, doublecheck that you are the stable channel and your stable toolchain is up-to-date. `rustc -v` should return a date and version no older than the one shown below:
```
$ rustc -v
rustc 1.79.0 (129f3b996 2024-06-10)
```

# `cargo-binutils`
```
$ rustup component add llvm-tools
$ cargo install cargo-binutils --vers 0.3.3
$ cargo size --version
cargo-size 0.3.6
```

# `probe-rs-tools`
**NOTE**: if you already have old versions of `probe-run`, `probe-rs` or `cargo-embed` installed on your system, remove them before starting this step, as they could conceivably cause problems for you down the line. In this situation, try these as needed:
```
$ cargo uninstall cargo-embed
$ cargo uninstall probe-run
$ cargo uninstall probe-rs
$ cargo uninstall probe-rs-cli
```

To install `probe-rs-tools`, first install its [prerequisites](https://probe.rs/docs/getting-started/installation/). Then install `probe-rs-tools` with Cargo.
```
$ cargo install --locked probe-rs-tools
```
**NOTE**: this may fail due to frequent changes to `probe-rs`. If so, go to [https://probe.rs/](https://probe.rs/) and follow the current installation instructions there.

Installing `probe-rs-tools` will install several useful tools, including `probe-rs` and `cargo-embed` (which is normally run as a Cargo command.) Check that things are working before proceeding:
```
$ cargo embed --version
cargo-embed 0.24.0 (git commit: crates.io)
```

# TODO port exercises?
