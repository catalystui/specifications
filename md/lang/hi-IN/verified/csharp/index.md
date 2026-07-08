<!-- यह अनुवाद ChatGPT द्वारा जनरेट किया गया था और किसी मानव अनुवादक द्वारा इसकी समीक्षा की जानी चाहिए। -->
<!-- अनुवाद सत्यापित हो जाने के बाद पुल रिक्वेस्ट में इन पंक्तियों को हटा दें। -->

# Verification Details

## C#

### अवलोकन

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C# programming language को July 7th, 2026 तक FDEFSPEC (Rev. 1) और FRELSPEC (Rev. 1) specifications के विरुद्ध verified किया गया है।

#### Good Faith Statement

हम good faith में मानते हैं कि C# programming language निम्न specifications में defined concepts और provisions को reasonably represent कर सकती है, और इसका उपयोग ऐसे systems implement करने के लिए किया जा सकता है जो इन specifications के compliance में हों।

#### Review Assumptions

यह review modern C# और .NET support मानता है जहाँ version-dependent features note किए गए हैं।

### चेतावनियाँ

* CP1252 support official .NET code pages provider के माध्यम से उपलब्ध है, लेकिन target runtime के आधार पर provider registration या additional package की आवश्यकता हो सकती है।
* Unsafe pointer behavior को explicit unsafe authorization की आवश्यकता हो सकती है।

### विफलताएँ

* इस verification के दौरान कोई known FDEFSPEC या FRELSPEC failures नहीं पाए गए।

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | 1-bit numeric नहीं; widen करें।                |
| Nibble    | ⚠️       | 4-bit numeric नहीं; widen करें।                |
| Byte      | ✅        | `byte` और `sbyte` के माध्यम से supported।   |
| Short     | ✅        | `short` और `ushort` के माध्यम से supported। |
| Int       | ✅        | `int` और `uint` के माध्यम से supported।     |
| Long      | ✅        | `long` और `ulong` के माध्यम से supported।   |
| Float     | ✅        | `float` के माध्यम से supported।              |
| Double    | ✅        | `double` के माध्यम से supported।             |
| Boolean   | ✅        | `bool` के माध्यम से supported।               |

#### Text Encoding

| Provision | Verified | Notes                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | Numerics और `Rune` के माध्यम से supported। |
| ASCII     | ✅        | `Encoding.ASCII` के माध्यम से supported।    |
| CP1252    | ⚠️       | Code pages provider चाहिए।          |
| UTF-8     | ✅        | `Encoding.UTF8` के माध्यम से supported।     |
| UTF-16LE  | ✅        | `Encoding.Unicode` के माध्यम से supported।  |

#### Operation Status

| Provision | Verified | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Custom type द्वारा represent किया जा सकता है।        |
| Context   | ✅        | Custom value द्वारा represent किया जा सकता है।       |
| Operation | ✅        | Custom value द्वारा represent किया जा सकता है।       |
| Detail    | ✅        | Custom value द्वारा represent किया जा सकता है।       |
| Result    | ✅        | Custom return type द्वारा represent किया जा सकता है। |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | `HashSet<T>` के माध्यम से supported।              |
| Map       | ✅        | `Dictionary<TKey,TValue>` के माध्यम से supported। |
| Array     | ✅        | Native arrays supported हैं।                 |
| File      | ✅        | File APIs के माध्यम से supported।                 |
| Stream    | ✅        | `Stream` के माध्यम से supported।                  |

#### Memory

| Provision | Verified | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | References और pointers के माध्यम से supported। |
| Pointer   | ✅        | Unsafe pointers के माध्यम से supported।         |
| Variable  | ✅        | Variables supported हैं।                   |
| Constant  | ✅        | `const` और `readonly` के माध्यम से supported।  |

#### Operations

| Provision   | Verified | Notes                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | IL और operations के माध्यम से represented। |
| Procedure   | ✅        | `void` methods के माध्यम से supported।      |
| Function    | ✅        | Returning methods के माध्यम से supported।   |

#### Threading

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Application और `Process` APIs के माध्यम से supported। |
| Thread     | ✅        | `Thread` के माध्यम से supported।                       |
| Dispatcher | ✅        | Tasks और schedulers के माध्यम से supported।           |

#### Composites

| Provision | Verified | Notes                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Type members supported हैं।        |
| Object    | ✅        | Objects supported हैं।             |
| Field     | ✅        | Fields supported हैं।              |
| Method    | ✅        | Methods supported हैं।             |
| Property  | ✅        | Properties natively supported हैं। |
| Structure | ✅        | Structures natively supported हैं। |
| Class     | ✅        | Classes supported हैं।             |
| Interface | ✅        | Interfaces supported हैं।          |
