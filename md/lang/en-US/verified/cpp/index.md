# Verification Details

## C++

### Overview


![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)

The C++ programming language has been verified against the FDEFSPEC (Rev. 1) and FRELSPEC (Rev. 1) specifications as of July 7th, 2026.

#### Good Faith Statement

We believe in good faith that the C++ programming language can reasonably represent the concepts and provisions defined in the following specifications, and that it can be used to implement systems which are in compliance with these specifications.

#### Review Assumptions

This review assumes modern standard C++ support where version-dependent features are noted. Exact-width integer support assumes the corresponding `<cstdint>` types are provided by the implementation.

This review treats C++ as a systems programming language with direct support for low-level representation, object modeling, memory control, generic programming, and concurrent execution.

### Warnings

* Exact-width integer types depend on implementation support.
* CP1252 can be represented byte-for-byte, but no named standard codec is provided.
* UTF-16LE serialization requires explicit byte-order handling.
* Some concurrency and character features require modern C++ revisions.

### Failures

* No known FDEFSPEC or FRELSPEC failures were found during this verification.

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | Supported through `std::byte`.              |
| Short     | ✅        | Supported through `int16_t` and `uint16_t`. |
| Int       | ✅        | Supported through `int32_t` and `uint32_t`. |
| Long      | ✅        | Supported through `int64_t` and `uint64_t`. |
| Float     | ✅        | Supported through `float`.                  |
| Double    | ✅        | Supported through `double`.                 |
| Boolean   | ✅        | Supported through `bool`.                   |

#### Text Encoding

| Provision | Verified | Notes                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Supported through `char32_t`.        |
| ASCII     | ✅        | Representable as byte values.        |
| CP1252    | ⚠️        | Requires explicit byte mapping.      |
| UTF-8     | ✅        | Supported through `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Requires byte-order handling.        |

#### Operation Status

| Provision | Verified | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Can be represented by an enum.           |
| Context   | ✅        | Can be represented by a value.           |
| Operation | ✅        | Can be represented by a value.           |
| Detail    | ✅        | Can be represented by a value.           |
| Result    | ✅        | Can be represented by a struct or class. |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Supported through `std::set`.              |
| Map       | ✅        | Supported through `std::map`.              |
| Array     | ✅        | Supported through arrays and `std::array`. |
| File      | ✅        | Supported through file streams.            |
| Stream    | ✅        | Supported through iostreams.               |

#### Memory

| Provision | Verified | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Addresses are supported.                   |
| Pointer   | ✅        | Pointers are supported.                    |
| Variable  | ✅        | Variables are supported.                   |
| Constant  | ✅        | Supported through `const` and `constexpr`. |

#### Operations

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | Supported through `void` functions.     |
| Function    | ✅        | Supported through returning functions.  |

#### Threading

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Supported through hosted execution.      |
| Thread     | ✅        | Supported through `std::thread`; C++11+. |
| Dispatcher | ✅        | Supported through async and schedulers.  |

#### Composites

| Provision | Verified | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Class members are supported.            |
| Object    | ✅        | Objects are supported.                  |
| Field     | ✅        | Fields are supported.                   |
| Method    | ✅        | Methods are supported.                  |
| Property  | ✅        | Get/Set maps can be represented.        |
| Structure | ✅        | Structures are natively supported.      |
| Class     | ✅        | Classes are natively supported.         |
| Interface | ✅        | Can be represented by abstract classes. |
