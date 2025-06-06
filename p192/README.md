# [RustCrypto]: NIST P-192 (secp192r1) elliptic curve

[![crate][crate-image]][crate-link]
[![Docs][docs-image]][docs-link]
[![Build Status][build-image]][build-link]
![Apache2/MIT licensed][license-image]
![Rust Version][rustc-image]
[![Project Chat][chat-image]][chat-link]

Pure Rust implementation of the NIST P-192 (a.k.a. secp192r1, prime192v1)
elliptic curve.

[Documentation][docs-link]

## ⚠️ Security Warning

### Small Key Size!

P-192 provides equivalent strength to a 96-bit symmetric key, which is
considered too weak for modern usage.

For more information, see:
[NIST Special Publication 800-131A Revision 2]:
"Transitioning the Use of Cryptographic Algorithms and Key Lengths":

> ECDSA and EdDSA: The security strength provided by an elliptic-curve-based
> signature algorithm is no greater than 1/2 of the length of the domain
> parameter n. Therefore, the length of n shall be at least 224 bits to meet
> the minimum security-strength requirement of 112 bits for Federal
> Government use.

Following the recommendations from this document, this crate only provides
public key operations intended for legacy interop purposes. There is
deliberately no `SecretKey`, ECDH support, or ECDSA `SigningKey`.

### Unaudited!

The elliptic curve arithmetic contained in this crate has never been
independently audited!

This crate has been designed with the goal of ensuring that secret-dependent
operations are performed in constant time (using the `subtle` crate and
constant-time formulas). However, it has not been thoroughly assessed to ensure
that generated assembly is constant time on common CPU architectures.

USE AT YOUR OWN RISK!

## About P-192

NIST P-192 is a Weierstrass curve specified in [FIPS 186-4].

Also known as secp192r1 (SECG).

## License

All crates licensed under either of

 * [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0)
 * [MIT license](http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.

[//]: # (badges)

[crate-image]: https://img.shields.io/crates/v/p192?logo=rust
[crate-link]: https://crates.io/crates/p192
[docs-image]: https://docs.rs/p192/badge.svg
[docs-link]: https://docs.rs/p192/
[build-image]: https://github.com/RustCrypto/elliptic-curves/actions/workflows/p192.yml/badge.svg
[build-link]: https://github.com/RustCrypto/elliptic-curves/actions/workflows/p192.yml
[license-image]: https://img.shields.io/badge/license-Apache2.0/MIT-blue.svg
[rustc-image]: https://img.shields.io/badge/rustc-1.85+-blue.svg
[chat-image]: https://img.shields.io/badge/zulip-join_chat-blue.svg
[chat-link]: https://rustcrypto.zulipchat.com/#narrow/stream/260040-elliptic-curves

[//]: # (links)

[RustCrypto]: https://github.com/rustcrypto/
[NIST Special Publication 800-131A Revision 2]: https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-131Ar2.pdf
[FIPS 186-4]: https://csrc.nist.gov/publications/detail/fips/186/4/final
