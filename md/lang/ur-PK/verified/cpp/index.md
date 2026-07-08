<!-- یہ ترجمہ ChatGPT کے ذریعے بنایا گیا ہے اور اسے ایک انسانی مترجم سے جائزہ لینا چاہیے۔ -->
<!-- ترجمہ کی تصدیق کے بعد ان سطروں کو pull request میں ہٹا دیں۔ -->

# Verification کی تفصیلات

## C++

### جائزہ

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C++ programming language کو 7 جولائی 2026 تک FDEFSPEC (Rev. 1) اور FRELSPEC (Rev. 1) specifications کے مقابل verified کیا گیا ہے۔

#### Good Faith Statement

ہم good faith میں believe کرتے ہیں کہ C++ programming language درج ذیل specifications میں defined concepts اور provisions کو reasonably represent کر سکتی ہے، اور اسے ایسے systems implement کرنے کے لیے استعمال کیا جا سکتا ہے جو ان specifications کے compliant ہوں۔

#### Review Assumptions

This review assumes modern standard C++ support where version-dependent features are noted. Exact-width integer support assumes the corresponding `<cstdint>` types are provided by the implementation.

This review treats C++ as a systems programming language with direct support for low-level representation, object modeling, memory control, generic programming, and concurrent execution.

### انتباہات

* Exact-width integer types depend on implementation support.
* CP1252 can be represented byte-for-byte, but no named standard codec is provided.
* UTF-16LE serialization requires explicit byte-order handling.
* Some concurrency and character features require modern C++ revisions.

### ناکامیاں

* اس verification کے دوران کوئی known FDEFSPEC یا FRELSPEC failures نہیں ملیں۔

### FDEFSPEC Verification

#### عددی اقسام

| Provision | Verified | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | کے ذریعے supported `std::byte`.              |
| Short     | ✅        | کے ذریعے supported `int16_t` and `uint16_t`. |
| Int       | ✅        | کے ذریعے supported `int32_t` and `uint32_t`. |
| Long      | ✅        | کے ذریعے supported `int64_t` and `uint64_t`. |
| Float     | ✅        | کے ذریعے supported `float`.                  |
| Double    | ✅        | کے ذریعے supported `double`.                 |
| Boolean   | ✅        | کے ذریعے supported `bool`.                   |

#### متن کی Encoding

| Provision | Verified | Notes                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | کے ذریعے supported `char32_t`.        |
| ASCII     | ✅        | کے طور پر representable byte values.        |
| CP1252    | ⚠️        | درکار ہے explicit byte mapping.      |
| UTF-8     | ✅        | کے ذریعے supported `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | درکار ہے byte-order handling.        |

#### Operation Status

| Provision | Verified | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | سے represent کیا جا سکتا ہے an enum.           |
| Context   | ✅        | سے represent کیا جا سکتا ہے a value.           |
| Operation | ✅        | سے represent کیا جا سکتا ہے a value.           |
| Detail    | ✅        | سے represent کیا جا سکتا ہے a value.           |
| Result    | ✅        | سے represent کیا جا سکتا ہے a struct or class. |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | کے ذریعے supported `std::set`.              |
| Map       | ✅        | کے ذریعے supported `std::map`.              |
| Array     | ✅        | کے ذریعے supported arrays and `std::array`. |
| File      | ✅        | کے ذریعے supported file streams.            |
| Stream    | ✅        | کے ذریعے supported iostreams.               |

#### Memory

| Provision | Verified | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Addresses are supported.                   |
| Pointer   | ✅        | Pointers are supported.                    |
| Variable  | ✅        | Variables supported ہیں۔                   |
| Constant  | ✅        | کے ذریعے supported `const` and `constexpr`. |

#### Operations

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | کے ذریعے supported `void` functions.     |
| Function    | ✅        | کے ذریعے supported returning functions.  |

#### Threading

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | کے ذریعے supported hosted execution.      |
| Thread     | ✅        | کے ذریعے supported `std::thread`; C++11+. |
| Dispatcher | ✅        | کے ذریعے supported async and schedulers.  |

#### Composites

| Provision | Verified | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Class members are supported.            |
| Object    | ✅        | Objects supported ہیں۔                  |
| Field     | ✅        | Fields supported ہیں۔                   |
| Method    | ✅        | Methods supported ہیں۔                  |
| Property  | ✅        | Get/Set maps can be represented.        |
| Structure | ✅        | Structures natively supported ہیں۔      |
| Class     | ✅        | Classes are natively supported.         |
| Interface | ✅        | سے represent کیا جا سکتا ہے abstract classes. |
