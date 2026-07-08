<!-- Ang saling ito ay ginawa ng ChatGPT at dapat suriin ng isang taong tagapagsalin. -->
<!-- Alisin ang mga linyang ito sa isang pull request pagkatapos mapatunayan ang salin. -->

# Mga Detalye ng Beripikasyon

## Java

### Pangkalahatang-ideya

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Naberipika ang wikang pamprogramang Java laban sa mga espesipikasyong FDEFSPEC (Rev. 1) at FRELSPEC (Rev. 1) noong Hulyo 7, 2026.

#### Pahayag ng Mabuting Pananalig

We believe in good faith that the Java programming language can reasonably represent a large portion of the concepts and provisions defined in the following specifications, and that it can be used to implement systems which are in compliance with these specifications.

#### Mga Palagay sa Pagsusuri

This review assumes modern Java language support where version-dependent features are noted. Features such as local variable inference, records, and foreign memory access may require later Java versions.

### Mga Babala

* Java does not have native support for unsigned numeric types, which may require widening or alternative representations for certain provisions.
* Direct memory address and pointer-style behavior may require Java 22+ Foreign Function and Memory API support.
* Java does not have native property syntax, requiring getter and setter methods instead.

### Mga Pagkabigo

* Java does not provide CP1252 as a guaranteed standard charset, requiring implementation-specific support, additional libraries, or custom handling for full compliance.
* Java properties do not provide an explicit keyed member backed by a required Get/Set accessor map.

### Beripikasyon ng FDEFSPEC

#### Numerics

| Probisyon | Beripikado | Mga Tala                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | Walang 1-bit numeric; palawakin.                         |
| Nibble    | ⚠️       | Walang 4-bit numeric; palawakin.                         |
| Byte      | ⚠️       | Signed 8-bit only; widen for unsigned.           |
| Short     | ⚠️       | Signed 16-bit only; widen for unsigned.          |
| Int       | ⚠️       | Signed 32-bit; unsigned helpers require Java 8+. |
| Long      | ⚠️       | Signed 64-bit; unsigned helpers require Java 8+. |
| Float     | ✅        | 32-bit floating point is supported.              |
| Double    | ✅        | 64-bit floating point is supported.              |
| Boolean   | ✅        | Boolean type is supported.                       |

#### Text Encoding

| Probisyon | Beripikado | Mga Tala                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Sinusuportahan sa pamamagitan ng `int` and `Character`. |
| ASCII     | ✅        | Garantisadong standard charset.             |
| CP1252    | ❌        | Hindi garantisado ng `StandardCharsets`.    |
| UTF-8     | ✅        | Garantisadong standard charset.             |
| UTF-16LE  | ✅        | Garantisadong standard charset.             |

#### Status ng Operasyon

| Probisyon | Beripikado | Mga Tala                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Maaaring katawanin sa pamamagitan ng a custom type.        |
| Context   | ✅        | Maaaring katawanin sa pamamagitan ng a custom value.       |
| Operation | ✅        | Maaaring katawanin sa pamamagitan ng a custom value.       |
| Detail    | ✅        | Maaaring katawanin sa pamamagitan ng a custom value.       |
| Result    | ✅        | Maaaring katawanin sa pamamagitan ng a custom return type. |

### Beripikasyon ng FRELSPEC

#### Collections

| Probisyon | Beripikado | Mga Tala                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Sinusuportahan sa pamamagitan ng `Set`.       |
| Map       | ✅        | Sinusuportahan sa pamamagitan ng `Map`.       |
| Array     | ✅        | Sinusuportahan ang native arrays.   |
| File      | ✅        | Sinusuportahan sa pamamagitan ng file APIs.   |
| Stream    | ✅        | Sinusuportahan sa pamamagitan ng stream APIs. |

#### Memory

| Probisyon | Beripikado | Mga Tala                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses require Java 22+ FFM.                         |
| Pointer   | ⚠️       | Pointer-like access requires Java 22+ FFM.                     |
| Variable  | ✅        | Declarations and `var` are supported; `var` requires Java 10+. |
| Constant  | ✅        | Sinusuportahan sa pamamagitan ng `final`.                                     |

#### Operations

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Represented through bytecode and operations. |
| Procedure   | ✅        | Sinusuportahan sa pamamagitan ng `void` methods.            |
| Function    | ✅        | Sinusuportahan sa pamamagitan ng returning methods.         |

#### Threading

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Sinusuportahan sa pamamagitan ng application and `Process` APIs. |
| Thread     | ✅        | Sinusuportahan sa pamamagitan ng `Thread`.                       |
| Dispatcher | ✅        | Sinusuportahan sa pamamagitan ng `Executor` APIs.                |

#### Composites

| Probisyon | Beripikado | Mga Tala                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Class members are supported.           |
| Object    | ✅        | Sinusuportahan ang objects.                 |
| Field     | ✅        | Sinusuportahan ang fields.                  |
| Method    | ✅        | Sinusuportahan ang methods.                 |
| Property  | ❌        | Walang explicit accessor map.              |
| Structure | ✅        | Sinusuportahan sa pamamagitan ng records; Java 16+.   |
| Class     | ✅        | Sinusuportahan ang classes.                 |
| Interface | ✅        | Sinusuportahan ang interfaces.              |
