# Verification Details

## C#

### Overview

The C# programming language has been verified against the FDEFSPEC (Rev. 1) specification as of July 4th, 2026.

#### Good Faith Statement

We believe in good faith that the C# programming language can reasonably represent a large portion of the concepts and provisions defined in the following specifications, and that it can be used to implement systems which are in compliance with these specifications.

### Warnings

- C# does not provide dedicated 1-bit or 4-bit numeric primitive types, which may require widening or custom representations for certain provisions.
- CP1252 support is available through the official .NET code pages provider, but may require provider registration or an additional package depending on the target runtime.

### Failures

- No known FDEFSPEC failures were found during this verification.

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Bit | ⚠️ | No 1-bit numeric, must be widened or otherwise represented. |
| Nibble | ⚠️ | No 4-bit numeric, must be widened or otherwise represented. |
| Byte | ✅ | Unsigned 8-bit numeric is supported by `byte`. |
| Short | ✅ | Signed 16-bit numeric is supported by `short`; unsigned 16-bit numeric is supported by `ushort`. |
| Int | ✅ | Signed 32-bit numeric is supported by `int`; unsigned 32-bit numeric is supported by `uint`. |
| Long | ✅ | Signed 64-bit numeric is supported by `long`; unsigned 64-bit numeric is supported by `ulong`. |
| Float | ✅ | 32-bit floating point numeric is supported by `float`. |
| Double | ✅ | 64-bit floating point numeric is supported by `double`. |
| Boolean | ✅ | Boolean type is supported by `bool`. |

#### Text Encoding

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Codepoint | ✅ | Representation of Unicode codepoints is supported through numeric types; Unicode scalar values are also supported through `System.Text.Rune`. |
| ASCII | ✅ | ASCII text encoding is supported. |
| CP1252 | ⚠️ | CP1252 can be supported through the official .NET code pages provider, but may require provider registration or an additional package depending on the target runtime. |
| UTF-8 | ✅ | UTF-8 text encoding is supported. |
| UTF-16LE | ✅ | UTF-16LE text encoding is supported. |

#### Operation Status

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Status | ✅ | Can be represented by a custom type which distinguishes `Success`, `Warning`, `Error`, and `Fatal`. |
| Context | ✅ | Can be represented by a custom type or value which provides additional operation-specific context. |
| Operation | ✅ | Can be represented by a custom type or value which identifies the operation being reported. |
| Detail | ✅ | Can be represented by a custom type or value which provides additional result information. |
| Result | ✅ | Can be represented by one custom returnable type containing status, context, operation, and detail, with support for any status level. |
