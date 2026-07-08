<!-- यह अनुवाद ChatGPT द्वारा जनरेट किया गया था और किसी मानव अनुवादक द्वारा इसकी समीक्षा की जानी चाहिए। -->
<!-- अनुवाद सत्यापित हो जाने के बाद पुल रिक्वेस्ट में इन पंक्तियों को हटा दें। -->

# Verification Details

## C++

### अवलोकन

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C++ programming language को July 7th, 2026 तक FDEFSPEC (Rev. 1) और FRELSPEC (Rev. 1) specifications के विरुद्ध verified किया गया है।

#### Good Faith Statement

हम good faith में मानते हैं कि C++ programming language निम्न specifications में defined concepts और provisions को reasonably represent कर सकती है, और इसका उपयोग ऐसे systems implement करने के लिए किया जा सकता है जो इन specifications के compliance में हों।

#### Review Assumptions

यह review modern standard C++ support मानता है जहाँ version-dependent features note किए गए हैं। Exact-width integer support यह मानता है कि implementation corresponding `<cstdint>` types provide करता है।

यह review C++ को systems programming language मानता है जिसमें low-level representation, object modeling, memory control, generic programming, और concurrent execution के लिए direct support है।

### चेतावनियाँ

* Exact-width integer types implementation support पर निर्भर करते हैं।
* CP1252 को byte-for-byte represent किया जा सकता है, लेकिन कोई named standard codec provide नहीं किया गया है।
* UTF-16LE serialization को explicit byte-order handling की आवश्यकता होती है।
* कुछ concurrency और character features को modern C++ revisions की आवश्यकता होती है।

### विफलताएँ

* इस verification के दौरान कोई known FDEFSPEC या FRELSPEC failures नहीं पाए गए।

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Bit-fields या masks का उपयोग करें।                    |
| Nibble    | ⚠️       | Bit-fields या masks का उपयोग करें।                    |
| Byte      | ✅        | `std::byte` के माध्यम से supported।              |
| Short     | ✅        | `int16_t` और `uint16_t` के माध्यम से supported। |
| Int       | ✅        | `int32_t` और `uint32_t` के माध्यम से supported। |
| Long      | ✅        | `int64_t` और `uint64_t` के माध्यम से supported। |
| Float     | ✅        | `float` के माध्यम से supported।                  |
| Double    | ✅        | `double` के माध्यम से supported।                 |
| Boolean   | ✅        | `bool` के माध्यम से supported।                   |

#### Text Encoding

| Provision | Verified | Notes                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | `char32_t` के माध्यम से supported।        |
| ASCII     | ✅        | Byte values के रूप में representable।        |
| CP1252    | ⚠️        | Explicit byte mapping चाहिए।      |
| UTF-8     | ✅        | `char8_t` के माध्यम से supported; C++20+। |
| UTF-16LE  | ⚠️        | Byte-order handling चाहिए।        |

#### Operation Status

| Provision | Verified | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Enum द्वारा represent किया जा सकता है।           |
| Context   | ✅        | Value द्वारा represent किया जा सकता है।           |
| Operation | ✅        | Value द्वारा represent किया जा सकता है।           |
| Detail    | ✅        | Value द्वारा represent किया जा सकता है।           |
| Result    | ✅        | Struct या class द्वारा represent किया जा सकता है। |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | `std::set` के माध्यम से supported।              |
| Map       | ✅        | `std::map` के माध्यम से supported।              |
| Array     | ✅        | Arrays और `std::array` के माध्यम से supported। |
| File      | ✅        | File streams के माध्यम से supported।            |
| Stream    | ✅        | Iostreams के माध्यम से supported।               |

#### Memory

| Provision | Verified | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Addresses supported हैं।                   |
| Pointer   | ✅        | Pointers supported हैं।                    |
| Variable  | ✅        | Variables supported हैं।                   |
| Constant  | ✅        | `const` और `constexpr` के माध्यम से supported। |

#### Operations

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Machine operations के माध्यम से represented। |
| Procedure   | ✅        | `void` functions के माध्यम से supported।     |
| Function    | ✅        | Returning functions के माध्यम से supported।  |

#### Threading

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Hosted execution के माध्यम से supported।      |
| Thread     | ✅        | `std::thread` के माध्यम से supported; C++11+। |
| Dispatcher | ✅        | Async और schedulers के माध्यम से supported।  |

#### Composites

| Provision | Verified | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Class members supported हैं।            |
| Object    | ✅        | Objects supported हैं।                  |
| Field     | ✅        | Fields supported हैं।                   |
| Method    | ✅        | Methods supported हैं।                  |
| Property  | ✅        | Get/Set maps represent किए जा सकते हैं।        |
| Structure | ✅        | Structures natively supported हैं।      |
| Class     | ✅        | Classes natively supported हैं।         |
| Interface | ✅        | Abstract classes द्वारा represent किया जा सकता है। |
