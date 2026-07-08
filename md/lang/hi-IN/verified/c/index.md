<!-- यह अनुवाद ChatGPT द्वारा जनरेट किया गया था और किसी मानव अनुवादक द्वारा इसकी समीक्षा की जानी चाहिए। -->
<!-- अनुवाद सत्यापित हो जाने के बाद पुल रिक्वेस्ट में इन पंक्तियों को हटा दें। -->

# Verification Details

## C

### अवलोकन

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C programming language को July 7th, 2026 तक FDEFSPEC (Rev. 1) और FRELSPEC (Rev. 1) specifications के विरुद्ध verified किया गया है।

#### Good Faith Statement

हम good faith में मानते हैं कि C programming language निम्न specifications में defined concepts और provisions को reasonably represent कर सकती है, और इसका उपयोग ऐसे systems implement करने के लिए किया जा सकता है जो इन specifications के compliance में हों।

#### Review Statement

C foundational data representation, memory access, files, streams, procedures, functions, structures, और direct system-oriented implementation के लिए strong low-level support प्रदान करता है।

हालाँकि C कई object-oriented composite constructs natively provide नहीं करता, ये limitations specific FRELSPEC composite provisions तक सीमित हैं और नीचे documented हैं। ये failures C को overall within spec माने जाने से नहीं रोकते, लेकिन CatalystUI-compatible implementations के लिए C का उपयोग करते समय इन्हें समझना चाहिए।

#### Review Assumptions

यह review modern standard C support मानता है जहाँ version-dependent features note किए गए हैं। Exact-width integer support यह मानता है कि implementation corresponding `<stdint.h>` types provide करता है।

यह review C को low-level representation language मानता है। जब कोई named standard codec प्रदान नहीं किया जाता, byte-exact encodings को byte arrays, lookup tables, और explicit parsing logic के माध्यम से directly represent किया जा सकता है।

### चेतावनियाँ

* Exact-width integer types implementation support पर निर्भर करते हैं।
* CP1252 को byte-for-byte represent किया जा सकता है, लेकिन कोई named standard codec provide नहीं किया गया है।
* UTF-16LE serialization को explicit byte-order handling की आवश्यकता होती है।
* कुछ C implementations standard threads omit कर सकती हैं।
* Object-oriented patterns manually emulate किए जा सकते हैं, लेकिन वे native language constructs नहीं हैं।

### विफलताएँ

* C native method members provide नहीं करता।
* C native properties provide नहीं करता।
* C native classes provide नहीं करता।
* C native interfaces provide नहीं करता।

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Bit-fields या masks का उपयोग करें।                    |
| Nibble    | ⚠️       | Bit-fields या masks का उपयोग करें।                    |
| Byte      | ✅        | `unsigned char` के माध्यम से supported।          |
| Short     | ✅        | `int16_t` और `uint16_t` के माध्यम से supported। |
| Int       | ✅        | `int32_t` और `uint32_t` के माध्यम से supported। |
| Long      | ✅        | `int64_t` और `uint64_t` के माध्यम से supported। |
| Float     | ✅        | `float` के माध्यम से supported।                  |
| Double    | ✅        | `double` के माध्यम से supported।                 |
| Boolean   | ✅        | `bool` के माध्यम से supported; C99+।             |

#### Text Encoding

| Provision | Verified | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | `char32_t` के माध्यम से supported; C11+।     |
| ASCII     | ✅        | Byte values के रूप में representable।           |
| CP1252    | ⚠️        | Explicit byte mapping चाहिए।         |
| UTF-8     | ✅        | UTF-8 literals के माध्यम से supported; C11+। |
| UTF-16LE  | ⚠️        | Byte-order handling चाहिए।           |

#### Operation Status

| Provision | Verified | Notes                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Enum द्वारा represent किया जा सकता है।  |
| Context   | ✅        | Value द्वारा represent किया जा सकता है।  |
| Operation | ✅        | Value द्वारा represent किया जा सकता है।  |
| Detail    | ✅        | Value द्वारा represent किया जा सकता है।  |
| Result    | ✅        | Struct द्वारा represent किया जा सकता है। |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Structs द्वारा represent किया जा सकता है। |
| Map       | ✅        | Structs द्वारा represent किया जा सकता है। |
| Array     | ✅        | Native arrays supported हैं।   |
| File      | ✅        | File APIs के माध्यम से supported।   |
| Stream    | ✅        | Stream APIs के माध्यम से supported। |

#### Memory

| Provision | Verified | Notes                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Addresses supported हैं।   |
| Pointer   | ✅        | Pointers supported हैं।    |
| Variable  | ✅        | Variables supported हैं।   |
| Constant  | ✅        | `const` के माध्यम से supported। |

#### Operations

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Machine operations के माध्यम से represented। |
| Procedure   | ✅        | `void` functions के माध्यम से supported।     |
| Function    | ✅        | Returning functions के माध्यम से supported।  |

#### Threading

| Provision  | Verified | Notes                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Hosted environments के माध्यम से supported। |
| Thread     | ⚠️        | `<threads.h>` के माध्यम से supported; C11+। |
| Dispatcher | ✅        | Directly represent किया जा सकता है।           |

#### Composites

| Provision | Verified | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Struct members supported हैं।            |
| Object    | ✅        | Structs addressable composites बना सकते हैं। |
| Field     | ✅        | Struct fields supported हैं।             |
| Method    | ❌        | Native method members नहीं।                |
| Property  | ❌        | Explicit Get/Set accessor map नहीं।        |
| Structure | ✅        | Structures natively supported हैं।       |
| Class     | ❌        | Native class construct नहीं।               |
| Interface | ❌        | Native interface construct नहीं।           |
