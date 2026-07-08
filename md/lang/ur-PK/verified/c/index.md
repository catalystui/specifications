<!-- یہ ترجمہ ChatGPT کے ذریعے بنایا گیا ہے اور اسے ایک انسانی مترجم سے جائزہ لینا چاہیے۔ -->
<!-- ترجمہ کی تصدیق کے بعد ان سطروں کو pull request میں ہٹا دیں۔ -->

# Verification کی تفصیلات

## C

### جائزہ

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C programming language کو 7 جولائی 2026 تک FDEFSPEC (Rev. 1) اور FRELSPEC (Rev. 1) specifications کے مقابل verified کیا گیا ہے۔

#### Good Faith Statement

ہم good faith میں believe کرتے ہیں کہ C programming language درج ذیل specifications میں defined concepts اور provisions کو reasonably represent کر سکتی ہے، اور اسے ایسے systems implement کرنے کے لیے استعمال کیا جا سکتا ہے جو ان specifications کے compliant ہوں۔

#### Review Statement

C provides strong low-level support for foundational data representation, memory access, files, streams, procedures, functions, structures, and direct system-oriented implementation.

While C does not natively provide several object-oriented composite constructs, these limitations are isolated to specific FRELSPEC composite provisions and are documented below. These failures do not prevent C from being considered within spec overall, but they should be understood when using C for CatalystUI-compatible implementations.

#### Review Assumptions

This review assumes modern standard C support where version-dependent features are noted. Exact-width integer support assumes the corresponding `<stdint.h>` types are provided by the implementation.

This review treats C as a low-level representation language. Byte-exact encodings may be represented directly through byte arrays, lookup tables, and explicit parsing logic when no named standard codec is provided.

### انتباہات

* Exact-width integer types depend on implementation support.
* CP1252 can be represented byte-for-byte, but no named standard codec is provided.
* UTF-16LE serialization requires explicit byte-order handling.
* Standard threads may be omitted by some C implementations.
* Object-oriented patterns may be manually emulated, but are not native language constructs.

### ناکامیاں

* C does not provide native method members.
* C does not provide native properties.
* C does not provide native classes.
* C does not provide native interfaces.

### FDEFSPEC Verification

#### عددی اقسام

| Provision | Verified | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | کے ذریعے supported `unsigned char`.          |
| Short     | ✅        | کے ذریعے supported `int16_t` and `uint16_t`. |
| Int       | ✅        | کے ذریعے supported `int32_t` and `uint32_t`. |
| Long      | ✅        | کے ذریعے supported `int64_t` and `uint64_t`. |
| Float     | ✅        | کے ذریعے supported `float`.                  |
| Double    | ✅        | کے ذریعے supported `double`.                 |
| Boolean   | ✅        | کے ذریعے supported `bool`; C99+.             |

#### متن کی Encoding

| Provision | Verified | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | کے ذریعے supported `char32_t`; C11+.     |
| ASCII     | ✅        | کے طور پر representable byte values.           |
| CP1252    | ⚠️        | درکار ہے explicit byte mapping.         |
| UTF-8     | ✅        | کے ذریعے supported UTF-8 literals; C11+. |
| UTF-16LE  | ⚠️        | درکار ہے byte-order handling.           |

#### Operation Status

| Provision | Verified | Notes                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | سے represent کیا جا سکتا ہے an enum.  |
| Context   | ✅        | سے represent کیا جا سکتا ہے a value.  |
| Operation | ✅        | سے represent کیا جا سکتا ہے a value.  |
| Detail    | ✅        | سے represent کیا جا سکتا ہے a value.  |
| Result    | ✅        | سے represent کیا جا سکتا ہے a struct. |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | سے represent کیا جا سکتا ہے structs. |
| Map       | ✅        | سے represent کیا جا سکتا ہے structs. |
| Array     | ✅        | Native arrays supported ہیں۔   |
| File      | ✅        | کے ذریعے supported file APIs.   |
| Stream    | ✅        | کے ذریعے supported stream APIs. |

#### Memory

| Provision | Verified | Notes                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Addresses are supported.   |
| Pointer   | ✅        | Pointers are supported.    |
| Variable  | ✅        | Variables supported ہیں۔   |
| Constant  | ✅        | کے ذریعے supported `const`. |

#### Operations

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | کے ذریعے supported `void` functions.     |
| Function    | ✅        | کے ذریعے supported returning functions.  |

#### Threading

| Provision  | Verified | Notes                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | کے ذریعے supported hosted environments. |
| Thread     | ⚠️        | کے ذریعے supported `<threads.h>`; C11+. |
| Dispatcher | ✅        | Can be represented directly.           |

#### Composites

| Provision | Verified | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Struct members are supported.            |
| Object    | ✅        | Structs can form addressable composites. |
| Field     | ✅        | Struct fields are supported.             |
| Method    | ❌        | No native method members.                |
| Property  | ❌        | No explicit Get/Set accessor map.        |
| Structure | ✅        | Structures natively supported ہیں۔       |
| Class     | ❌        | No native class construct.               |
| Interface | ❌        | No native interface construct.           |
