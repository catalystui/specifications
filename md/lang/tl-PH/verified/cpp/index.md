<!-- Ang saling ito ay ginawa ng ChatGPT at dapat suriin ng isang taong tagapagsalin. -->
<!-- Alisin ang mga linyang ito sa isang pull request pagkatapos mapatunayan ang salin. -->

# Mga Detalye ng Beripikasyon

## C++

### Pangkalahatang-ideya

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Naberipika ang wikang pamprogramang C++ laban sa mga espesipikasyong FDEFSPEC (Rev. 1) at FRELSPEC (Rev. 1) noong Hulyo 7, 2026.

#### Pahayag ng Mabuting Pananalig

We believe in good faith that the C++ programming language can reasonably represent the concepts and provisions defined in the following specifications, and that it can be used to implement systems which are in compliance with these specifications.

#### Mga Palagay sa Pagsusuri

This review assumes modern standard C++ support where version-dependent features are noted. Exact-width integer support assumes the corresponding `<cstdint>` types are provided by the implementation.

This review treats C++ as a systems programming language with direct support for low-level representation, object modeling, memory control, generic programming, and concurrent execution.

### Mga Babala

* Exact-width integer types depend on implementation support.
* CP1252 can be represented byte-for-byte, but no named standard codec is provided.
* UTF-16LE serialization requires explicit byte-order handling.
* Some concurrency and character features require modern C++ revisions.

### Mga Pagkabigo

* Walang natagpuang kilalang failure sa FDEFSPEC o FRELSPEC sa panahon ng beripikasyong ito.

### Beripikasyon ng FDEFSPEC

#### Numerics

| Probisyon | Beripikado | Mga Tala                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | Sinusuportahan sa pamamagitan ng `std::byte`.              |
| Short     | ✅        | Sinusuportahan sa pamamagitan ng `int16_t` and `uint16_t`. |
| Int       | ✅        | Sinusuportahan sa pamamagitan ng `int32_t` and `uint32_t`. |
| Long      | ✅        | Sinusuportahan sa pamamagitan ng `int64_t` and `uint64_t`. |
| Float     | ✅        | Sinusuportahan sa pamamagitan ng `float`.                  |
| Double    | ✅        | Sinusuportahan sa pamamagitan ng `double`.                 |
| Boolean   | ✅        | Sinusuportahan sa pamamagitan ng `bool`.                   |

#### Text Encoding

| Probisyon | Beripikado | Mga Tala                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Sinusuportahan sa pamamagitan ng `char32_t`.        |
| ASCII     | ✅        | Maaaring katawanin bilang byte values.        |
| CP1252    | ⚠️        | Nangangailangan ng explicit byte mapping.      |
| UTF-8     | ✅        | Sinusuportahan sa pamamagitan ng `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Nangangailangan ng byte-order handling.        |

#### Status ng Operasyon

| Probisyon | Beripikado | Mga Tala                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Maaaring katawanin sa pamamagitan ng an enum.           |
| Context   | ✅        | Maaaring katawanin sa pamamagitan ng a value.           |
| Operation | ✅        | Maaaring katawanin sa pamamagitan ng a value.           |
| Detail    | ✅        | Maaaring katawanin sa pamamagitan ng a value.           |
| Result    | ✅        | Maaaring katawanin sa pamamagitan ng a struct or class. |

### Beripikasyon ng FRELSPEC

#### Collections

| Probisyon | Beripikado | Mga Tala                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Sinusuportahan sa pamamagitan ng `std::set`.              |
| Map       | ✅        | Sinusuportahan sa pamamagitan ng `std::map`.              |
| Array     | ✅        | Sinusuportahan sa pamamagitan ng arrays and `std::array`. |
| File      | ✅        | Sinusuportahan sa pamamagitan ng file streams.            |
| Stream    | ✅        | Sinusuportahan sa pamamagitan ng iostreams.               |

#### Memory

| Probisyon | Beripikado | Mga Tala                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Addresses are supported.                   |
| Pointer   | ✅        | Pointers are supported.                    |
| Variable  | ✅        | Sinusuportahan ang variables.                   |
| Constant  | ✅        | Sinusuportahan sa pamamagitan ng `const` and `constexpr`. |

#### Operations

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | Sinusuportahan sa pamamagitan ng `void` functions.     |
| Function    | ✅        | Sinusuportahan sa pamamagitan ng returning functions.  |

#### Threading

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Sinusuportahan sa pamamagitan ng hosted execution.      |
| Thread     | ✅        | Sinusuportahan sa pamamagitan ng `std::thread`; C++11+. |
| Dispatcher | ✅        | Sinusuportahan sa pamamagitan ng async and schedulers.  |

#### Composites

| Probisyon | Beripikado | Mga Tala                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Class members are supported.            |
| Object    | ✅        | Sinusuportahan ang objects.                  |
| Field     | ✅        | Sinusuportahan ang fields.                   |
| Method    | ✅        | Sinusuportahan ang methods.                  |
| Property  | ✅        | Get/Set maps can be represented.        |
| Structure | ✅        | Native na sinusuportahan ang structures.      |
| Class     | ✅        | Classes are natively supported.         |
| Interface | ✅        | Maaaring katawanin sa pamamagitan ng abstract classes. |
