<!-- यह अनुवाद ChatGPT द्वारा जनरेट किया गया था और किसी मानव अनुवादक द्वारा इसकी समीक्षा की जानी चाहिए। -->
<!-- अनुवाद सत्यापित हो जाने के बाद पुल रिक्वेस्ट में इन पंक्तियों को हटा दें। -->

# Verification Details

## Java

### अवलोकन

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Java programming language को July 7th, 2026 तक FDEFSPEC (Rev. 1) और FRELSPEC (Rev. 1) specifications के विरुद्ध verified किया गया है।

#### Good Faith Statement

हम good faith में मानते हैं कि Java programming language निम्न specifications में defined concepts और provisions के बड़े हिस्से को reasonably represent कर सकती है, और इसका उपयोग ऐसे systems implement करने के लिए किया जा सकता है जो इन specifications के compliance में हों।

#### Review Assumptions

यह review modern Java language support मानता है जहाँ version-dependent features note किए गए हैं। Local variable inference, records, और foreign memory access जैसी features को later Java versions की आवश्यकता हो सकती है।

### चेतावनियाँ

* Java में unsigned numeric types के लिए native support नहीं है, इसलिए कुछ provisions के लिए widening या alternative representations की आवश्यकता हो सकती है।
* Direct memory address और pointer-style behavior को Java 22+ Foreign Function and Memory API support की आवश्यकता हो सकती है।
* Java में native property syntax नहीं है, इसलिए उसके स्थान पर getter और setter methods की आवश्यकता होती है।

### विफलताएँ

* Java CP1252 को guaranteed standard charset के रूप में provide नहीं करता, इसलिए full compliance के लिए implementation-specific support, additional libraries, या custom handling की आवश्यकता हो सकती है।
* Java properties required Get/Set accessor map द्वारा backed explicit keyed member provide नहीं करतीं।

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | 1-bit numeric नहीं; widen करें।                         |
| Nibble    | ⚠️       | 4-bit numeric नहीं; widen करें।                         |
| Byte      | ⚠️       | केवल signed 8-bit; unsigned के लिए widen करें।           |
| Short     | ⚠️       | केवल signed 16-bit; unsigned के लिए widen करें।          |
| Int       | ⚠️       | Signed 32-bit; unsigned helpers को Java 8+ चाहिए। |
| Long      | ⚠️       | Signed 64-bit; unsigned helpers को Java 8+ चाहिए। |
| Float     | ✅        | 32-bit floating point supported है।              |
| Double    | ✅        | 64-bit floating point supported है।              |
| Boolean   | ✅        | Boolean type supported है।                       |

#### Text Encoding

| Provision | Verified | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | `int` और `Character` के माध्यम से supported। |
| ASCII     | ✅        | Guaranteed standard charset।             |
| CP1252    | ❌        | `StandardCharsets` द्वारा guaranteed नहीं।    |
| UTF-8     | ✅        | Guaranteed standard charset।             |
| UTF-16LE  | ✅        | Guaranteed standard charset।             |

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

| Provision | Verified | Notes                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | `Set` के माध्यम से supported।       |
| Map       | ✅        | `Map` के माध्यम से supported।       |
| Array     | ✅        | Native arrays supported हैं।   |
| File      | ✅        | File APIs के माध्यम से supported।   |
| Stream    | ✅        | Stream APIs के माध्यम से supported। |

#### Memory

| Provision | Verified | Notes                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses को Java 22+ FFM चाहिए।                         |
| Pointer   | ⚠️       | Pointer-like access को Java 22+ FFM चाहिए।                     |
| Variable  | ✅        | Declarations और `var` supported हैं; `var` को Java 10+ चाहिए। |
| Constant  | ✅        | `final` के माध्यम से supported।                                     |

#### Operations

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Bytecode और operations के माध्यम से represented। |
| Procedure   | ✅        | `void` methods के माध्यम से supported।            |
| Function    | ✅        | Returning methods के माध्यम से supported।         |

#### Threading

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Application और `Process` APIs के माध्यम से supported। |
| Thread     | ✅        | `Thread` के माध्यम से supported।                       |
| Dispatcher | ✅        | `Executor` APIs के माध्यम से supported।                |

#### Composites

| Provision | Verified | Notes                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Class members supported हैं।           |
| Object    | ✅        | Objects supported हैं।                 |
| Field     | ✅        | Fields supported हैं।                  |
| Method    | ✅        | Methods supported हैं।                 |
| Property  | ❌        | Explicit accessor map नहीं।              |
| Structure | ✅        | Records के माध्यम से supported; Java 16+।   |
| Class     | ✅        | Classes supported हैं।                 |
| Interface | ✅        | Interfaces supported हैं।              |
