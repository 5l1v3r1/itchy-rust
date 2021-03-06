# itchy

[![Build Status](https://travis-ci.org/adwhit/itchy-rust.svg?branch=master)](https://travis-ci.org/adwhit/itchy-rust)
[![Crates.io Version](https://img.shields.io/crates/v/itchy.svg)](https://crates.io/crates/itchy)

ITCH parser library for Rust. Implements the NASDAQ 5.0 spec which can be found [here](http://www.nasdaqtrader.com/content/technicalsupport/specifications/dataproducts/NQTVITCHSpecification_5.0.pdf).

It is based on [nom](http://github.com/geal/nom) and despite not having
been optimized much, it is zero-allocation and pretty fast, benching
~7M messages/second on my laptop (Intel Core m3-6Y30).

## Usage

Add this to your `Cargo.toml`:
```toml
[dependencies]
itchy = "0.1"
```
and this to your crate root:

```rust
extern crate itchy;
```

Simple example:

```rust
let stream = itchy::MessageStream::from_file("/path/to/file.itch").unwrap();
for msg in stream {
    println!("{:?}", msg.unwrap())
}
```

See the [API docs](https://docs.rs/itchy/0.1.0/) for more information.
