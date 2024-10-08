## What?

Cabish is kind of, sort of like [Wasm component model ABI] with native endian and pointer size, it's _cabi-ish_.

## How?

Essentially it's just direct implementation of [Wasm component model ABI], but alignment and size of values depends on the platform and may not correspond to the spec, for example, alignment of `string` type will generally be 8 on a 64-bit system as opposed to `4` used by 32-bit Wasm.

## Why?

Cabish allows reuse of existing tooling targeting canonical ABI in native code, for example, [`wadge`](https://github.com/wasmCloud/wadge) replaces Go Wasm imports generated by [`wit-bindgen-go`](https://github.com/bytecodealliance/wasm-tools-go) by calls to an embedded Wasmtime instance via Rust FFI in native code and uses cabish to read and write values.

[Wasm component model ABI]: https://github.com/WebAssembly/component-model/blob/c5f8f25ceb9388431f32943bb21a36d991cfbe91/design/mvp/CanonicalABI.md
