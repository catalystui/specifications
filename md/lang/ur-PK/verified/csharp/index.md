<!-- یہ ترجمہ ChatGPT کے ذریعے بنایا گیا ہے اور اسے ایک انسانی مترجم سے جائزہ لینا چاہیے۔ -->
<!-- ترجمہ کی تصدیق کے بعد ان سطروں کو pull request میں ہٹا دیں۔ -->

# Verification کی تفصیلات

## C#

### جائزہ

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C# programming language کو 7 جولائی 2026 تک FDEFSPEC (Rev. 1) اور FRELSPEC (Rev. 1) specifications کے مقابل verified کیا گیا ہے۔

#### Good Faith Statement

ہم good faith میں believe کرتے ہیں کہ C# programming language درج ذیل specifications میں defined concepts اور provisions کو reasonably represent کر سکتی ہے، اور اسے ایسے systems implement کرنے کے لیے استعمال کیا جا سکتا ہے جو ان specifications کے compliant ہوں۔

#### Review Assumptions

This review assumes modern C# and .NET support where version-dependent features are noted.

### انتباہات

* CP1252 support is available through the official .NET code pages provider, but may require provider registration or an additional package depending on the target runtime.
* Unsafe pointer behavior may require explicit unsafe authorization.

### ناکامیاں

* اس verification کے دوران کوئی known FDEFSPEC یا FRELSPEC failures نہیں ملیں۔

### FDEFSPEC Verification

#### عددی اقسام

| Provision | Verified | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | 1-bit numeric نہیں؛ widen کریں۔                |
| Nibble    | ⚠️       | 4-bit numeric نہیں؛ widen کریں۔                |
| Byte      | ✅        | کے ذریعے supported `byte` and `sbyte`.   |
| Short     | ✅        | کے ذریعے supported `short` and `ushort`. |
| Int       | ✅        | کے ذریعے supported `int` and `uint`.     |
| Long      | ✅        | کے ذریعے supported `long` and `ulong`.   |
| Float     | ✅        | کے ذریعے supported `float`.              |
| Double    | ✅        | کے ذریعے supported `double`.             |
| Boolean   | ✅        | کے ذریعے supported `bool`.               |

#### متن کی Encoding

| Provision | Verified | Notes                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | کے ذریعے supported numerics and `Rune`. |
| ASCII     | ✅        | کے ذریعے supported `Encoding.ASCII`.    |
| CP1252    | ⚠️       | درکار ہے code pages provider.          |
| UTF-8     | ✅        | کے ذریعے supported `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | کے ذریعے supported `Encoding.Unicode`.  |

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

| Provision | Verified | Notes                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | کے ذریعے supported `HashSet<T>`.              |
| Map       | ✅        | کے ذریعے supported `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Native arrays supported ہیں۔                 |
| File      | ✅        | کے ذریعے supported file APIs.                 |
| Stream    | ✅        | کے ذریعے supported `Stream`.                  |

#### Memory

| Provision | Verified | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | کے ذریعے supported references and pointers. |
| Pointer   | ✅        | کے ذریعے supported unsafe pointers.         |
| Variable  | ✅        | Variables supported ہیں۔                   |
| Constant  | ✅        | کے ذریعے supported `const` and `readonly`.  |

#### Operations

| Provision   | Verified | Notes                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Represented through IL and operations. |
| Procedure   | ✅        | کے ذریعے supported `void` methods.      |
| Function    | ✅        | کے ذریعے supported returning methods.   |

#### Threading

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | کے ذریعے supported application and `Process` APIs. |
| Thread     | ✅        | کے ذریعے supported `Thread`.                       |
| Dispatcher | ✅        | کے ذریعے supported tasks and schedulers.           |

#### Composites

| Provision | Verified | Notes                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Type members are supported.        |
| Object    | ✅        | Objects supported ہیں۔             |
| Field     | ✅        | Fields supported ہیں۔              |
| Method    | ✅        | Methods supported ہیں۔             |
| Property  | ✅        | Properties natively supported ہیں۔ |
| Structure | ✅        | Structures natively supported ہیں۔ |
| Class     | ✅        | Classes supported ہیں۔             |
| Interface | ✅        | Interfaces supported ہیں۔          |
