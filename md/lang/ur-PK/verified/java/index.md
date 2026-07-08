<!-- یہ ترجمہ ChatGPT کے ذریعے بنایا گیا ہے اور اسے ایک انسانی مترجم سے جائزہ لینا چاہیے۔ -->
<!-- ترجمہ کی تصدیق کے بعد ان سطروں کو pull request میں ہٹا دیں۔ -->

# Verification کی تفصیلات

## Java

### جائزہ

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Java programming language کو 7 جولائی 2026 تک FDEFSPEC (Rev. 1) اور FRELSPEC (Rev. 1) specifications کے مقابل verified کیا گیا ہے۔

#### Good Faith Statement

ہم good faith میں believe کرتے ہیں کہ Java programming language درج ذیل specifications میں defined concepts اور provisions کے بڑے حصے کو reasonably represent کر سکتی ہے، اور اسے ایسے systems implement کرنے کے لیے استعمال کیا جا سکتا ہے جو ان specifications کے compliant ہوں۔

#### Review Assumptions

This review assumes modern Java language support where version-dependent features are noted. Features such as local variable inference, records, and foreign memory access may require later Java versions.

### انتباہات

* Java does not have native support for unsigned numeric types, which may require widening or alternative representations for certain provisions.
* Direct memory address and pointer-style behavior may require Java 22+ Foreign Function and Memory API support.
* Java does not have native property syntax, requiring getter and setter methods instead.

### ناکامیاں

* Java does not provide CP1252 as a guaranteed standard charset, requiring implementation-specific support, additional libraries, or custom handling for full compliance.
* Java properties do not provide an explicit keyed member backed by a required Get/Set accessor map.

### FDEFSPEC Verification

#### عددی اقسام

| Provision | Verified | Notes                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | 1-bit numeric نہیں؛ widen کریں۔                         |
| Nibble    | ⚠️       | 4-bit numeric نہیں؛ widen کریں۔                         |
| Byte      | ⚠️       | Signed 8-bit only; widen for unsigned.           |
| Short     | ⚠️       | Signed 16-bit only; widen for unsigned.          |
| Int       | ⚠️       | Signed 32-bit; unsigned helpers require Java 8+. |
| Long      | ⚠️       | Signed 64-bit; unsigned helpers require Java 8+. |
| Float     | ✅        | 32-bit floating point is supported.              |
| Double    | ✅        | 64-bit floating point is supported.              |
| Boolean   | ✅        | Boolean type is supported.                       |

#### متن کی Encoding

| Provision | Verified | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | کے ذریعے supported `int` and `Character`. |
| ASCII     | ✅        | guaranteed standard charset۔             |
| CP1252    | ❌        | اس کے ذریعے guaranteed نہیں `StandardCharsets`.    |
| UTF-8     | ✅        | guaranteed standard charset۔             |
| UTF-16LE  | ✅        | guaranteed standard charset۔             |

#### Operation Status

| Provision | Verified | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | سے represent کیا جا سکتا ہے a custom type.        |
| Context   | ✅        | سے represent کیا جا سکتا ہے a custom value.       |
| Operation | ✅        | سے represent کیا جا سکتا ہے a custom value.       |
| Detail    | ✅        | سے represent کیا جا سکتا ہے a custom value.       |
| Result    | ✅        | سے represent کیا جا سکتا ہے a custom return type. |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | کے ذریعے supported `Set`.       |
| Map       | ✅        | کے ذریعے supported `Map`.       |
| Array     | ✅        | Native arrays supported ہیں۔   |
| File      | ✅        | کے ذریعے supported file APIs.   |
| Stream    | ✅        | کے ذریعے supported stream APIs. |

#### Memory

| Provision | Verified | Notes                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses require Java 22+ FFM.                         |
| Pointer   | ⚠️       | Pointer-like access requires Java 22+ FFM.                     |
| Variable  | ✅        | Declarations and `var` are supported; `var` requires Java 10+. |
| Constant  | ✅        | کے ذریعے supported `final`.                                     |

#### Operations

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Represented through bytecode and operations. |
| Procedure   | ✅        | کے ذریعے supported `void` methods.            |
| Function    | ✅        | کے ذریعے supported returning methods.         |

#### Threading

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | کے ذریعے supported application and `Process` APIs. |
| Thread     | ✅        | کے ذریعے supported `Thread`.                       |
| Dispatcher | ✅        | کے ذریعے supported `Executor` APIs.                |

#### Composites

| Provision | Verified | Notes                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Class members are supported.           |
| Object    | ✅        | Objects supported ہیں۔                 |
| Field     | ✅        | Fields supported ہیں۔                  |
| Method    | ✅        | Methods supported ہیں۔                 |
| Property  | ❌        | explicit accessor map موجود نہیں۔              |
| Structure | ✅        | کے ذریعے supported records; Java 16+.   |
| Class     | ✅        | Classes supported ہیں۔                 |
| Interface | ✅        | Interfaces supported ہیں۔              |
