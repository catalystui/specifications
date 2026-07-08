# Verification Details

## Java

### Overview


![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)

The Java programming language has been verified against the FDEFSPEC (Rev. 1) and FRELSPEC (Rev. 1) specifications as of July 7th, 2026.

#### Good Faith Statement

We believe in good faith that the Java programming language can reasonably represent a large portion of the concepts and provisions defined in the following specifications, and that it can be used to implement systems which are in compliance with these specifications.

#### Review Assumptions

This review assumes modern Java language support where version-dependent features are noted. Features such as local variable inference, records, and foreign memory access may require later Java versions.

### Warnings

* Java does not have native support for unsigned numeric types, which may require widening or alternative representations for certain provisions.
* Direct memory address and pointer-style behavior may require Java 22+ Foreign Function and Memory API support.
* Java does not have native property syntax, requiring getter and setter methods instead.

### Failures

* Java does not provide CP1252 as a guaranteed standard charset, requiring implementation-specific support, additional libraries, or custom handling for full compliance.
* Java properties do not provide an explicit keyed member backed by a required Get/Set accessor map.

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | No 1-bit numeric; widen.                         |
| Nibble    | ⚠️       | No 4-bit numeric; widen.                         |
| Byte      | ⚠️       | Signed 8-bit only; widen for unsigned.           |
| Short     | ⚠️       | Signed 16-bit only; widen for unsigned.          |
| Int       | ⚠️       | Signed 32-bit; unsigned helpers require Java 8+. |
| Long      | ⚠️       | Signed 64-bit; unsigned helpers require Java 8+. |
| Float     | ✅        | 32-bit floating point is supported.              |
| Double    | ✅        | 64-bit floating point is supported.              |
| Boolean   | ✅        | Boolean type is supported.                       |

#### Text Encoding

| Provision | Verified | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Supported through `int` and `Character`. |
| ASCII     | ✅        | Guaranteed standard charset.             |
| CP1252    | ❌        | Not guaranteed by `StandardCharsets`.    |
| UTF-8     | ✅        | Guaranteed standard charset.             |
| UTF-16LE  | ✅        | Guaranteed standard charset.             |

#### Operation Status

| Provision | Verified | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Can be represented by a custom type.        |
| Context   | ✅        | Can be represented by a custom value.       |
| Operation | ✅        | Can be represented by a custom value.       |
| Detail    | ✅        | Can be represented by a custom value.       |
| Result    | ✅        | Can be represented by a custom return type. |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Supported through `Set`.       |
| Map       | ✅        | Supported through `Map`.       |
| Array     | ✅        | Native arrays are supported.   |
| File      | ✅        | Supported through file APIs.   |
| Stream    | ✅        | Supported through stream APIs. |

#### Memory

| Provision | Verified | Notes                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses require Java 22+ FFM.                         |
| Pointer   | ⚠️       | Pointer-like access requires Java 22+ FFM.                     |
| Variable  | ✅        | Declarations and `var` are supported; `var` requires Java 10+. |
| Constant  | ✅        | Supported through `final`.                                     |

#### Operations

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Represented through bytecode and operations. |
| Procedure   | ✅        | Supported through `void` methods.            |
| Function    | ✅        | Supported through returning methods.         |

#### Threading

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Supported through application and `Process` APIs. |
| Thread     | ✅        | Supported through `Thread`.                       |
| Dispatcher | ✅        | Supported through `Executor` APIs.                |

#### Composites

| Provision | Verified | Notes                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Class members are supported.           |
| Object    | ✅        | Objects are supported.                 |
| Field     | ✅        | Fields are supported.                  |
| Method    | ✅        | Methods are supported.                 |
| Property  | ❌        | No explicit accessor map.              |
| Structure | ✅        | Supported through records; Java 16+.   |
| Class     | ✅        | Classes are supported.                 |
| Interface | ✅        | Interfaces are supported.              |
