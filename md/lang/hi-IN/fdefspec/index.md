<!-- यह अनुवाद ChatGPT द्वारा जनरेट किया गया था और किसी मानव अनुवादक द्वारा इसकी समीक्षा की जानी चाहिए। -->
<!-- अनुवाद सत्यापित हो जाने के बाद पुल रिक्वेस्ट में इन पंक्तियों को हटा दें। -->

# FDEFSPEC

<br/>

> **Foundational Definitions Specification**<br/>
> Revision 1<br/>
> March 23rd, 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> सर्वाधिकार सुरक्षित।<br/>
> <br/>
> यहाँ प्रस्तुत definitions और concepts fundamental mathematical constructs का वर्णन करते हैं और इन्हें स्वतंत्र रूप से दोबारा व्यक्त किया जा सकता है।

## परिचय

**Foundational Definitions Specification (FDEFSPEC)** CatalystUI ecosystem के आधारभूत concepts और terminology स्थापित करता है। इसका उद्देश्य documentation, specifications, implementations, और verification reviews में इन concepts की unified understanding प्रदान करना है, ताकि consistency, clarity, और alignment सुनिश्चित हो सके।

Key terms और relationships को precise और stable form में define करके, FDEFSPEC higher-level specifications के लिए common reference point प्रदान करता है। इससे developers, reviewers, और implementers उसी foundation से reason कर सकते हैं जब वे यह निर्धारित करते हैं कि कोई language, service, framework, या system within spec माना जा सकता है या नहीं।

> [!IMPORTANT]
>
> हम definitions को [set theory](https://en.wikipedia.org/wiki/Set_theory) notation के derived form का उपयोग करके व्यक्त करते हैं। यह approach clarity और conciseness बनाए रखते हुए precise और unambiguous definitions प्रदान करती है। हम इन definitions को easy reference, clear interpretation, और consistent conceptual hierarchy का समर्थन करने के लिए structure करते हैं।

## विषय-सूची

- [FDEFSPEC](#fdefspec)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Numerics](#numerics)
    - [Bit](#bit)
    - [Nibble](#nibble)
      - [Nibble()](#nibble-1)
    - [Byte](#byte)
      - [Byte()](#byte-1)
      - [SByte()](#sbyte)
    - [Short](#short)
      - [Short()](#short-1)
      - [UShort()](#ushort)
    - [Int](#int)
      - [Int()](#int-1)
      - [UInt()](#uint)
    - [Long](#long)
      - [Long()](#long-1)
      - [ULong()](#ulong)
    - [Single](#single)
      - [Single()](#single-1)
    - [Double](#double)
      - [Double()](#double-1)
    - [Boolean](#boolean)
      - [Boolean()](#boolean-1)
  - [Text Encoding](#text-encoding)
    - [Text Encoding](#text-encoding-1)
      - [Text Encoding()](#text-encoding-2)
    - [Codepoint](#codepoint)
      - [Codepoint()](#codepoint-1)
    - [ASCII Code Unit](#ascii-code-unit)
      - [ASCII Code Unit()](#ascii-code-unit-1)
      - [ASCII()](#ascii)
    - [CP1252 Code Unit](#cp1252-code-unit)
      - [CP1252 Code Unit()](#cp1252-code-unit-1)
      - [CP1252()](#cp1252)
    - [UTF-8 Code Unit](#utf-8-code-unit)
      - [UTF-8 Code Unit()](#utf-8-code-unit-1)
      - [UTF-8()](#utf-8)
    - [UTF-16LE Code Unit](#utf-16le-code-unit)
      - [UTF-16LE Code Unit()](#utf-16le-code-unit-1)
      - [UTF-16LE()](#utf-16le)
  - [Operation Status](#operation-status)
    - [Status Code](#status-code)
      - [Status Code()](#status-code-1)
      - [Status Code Level()](#status-code-level)
      - [Status Code Definition()](#status-code-definition)
        - [Success](#success)
        - [Warning](#warning)
        - [Error](#error)
        - [Fatal](#fatal)
    - [Context Code](#context-code)
      - [Context Code()](#context-code-1)
    - [Operation Code](#operation-code)
      - [Operation Code()](#operation-code-1)
    - [Detail Code](#detail-code)
      - [Detail Code()](#detail-code-1)
    - [Result](#result)
      - [Result()](#result-1)

## Numerics

### Bit

Bit कोई भी $b \in \{0,1\}$ है।

### Nibble

Nibble कोई भी $(b_0,\dots,b_3)$ है, जहाँ सभी $i \in \{0,\dots,3\}$ के लिए, $b_i \in \mathrm{Bit}$ होता है।

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

Byte कोई भी $(b_0,\dots,b_7)$ है, जहाँ सभी $i \in \{0,\dots,7\}$ के लिए, $b_i \in \mathrm{Bit}$ होता है।

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

Short कोई भी $(b_0,\dots,b_{15})$ है, जहाँ सभी $i \in \{0,\dots,15\}$ के लिए, $b_i \in \mathrm{Bit}$ होता है।

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

Integer कोई भी $(b_0,\dots,b_{31})$ है, जहाँ सभी $i \in \{0,\dots,31\}$ के लिए, $b_i \in \mathrm{Bit}$ होता है।

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

Long कोई भी $(b_0,\dots,b_{63})$ है, जहाँ सभी $i \in \{0,\dots,63\}$ के लिए, $b_i \in \mathrm{Bit}$ होता है।

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

Single कोई भी $(b_0,\dots,b_{31})$ है, जहाँ सभी $i \in \{0,\dots,31\}$ के लिए, $b_i \in \mathrm{Bit}$ होता है।

#### Single()

निम्न definition single-precision floating-point representation के लिए IEEE 754 standard के अनुरूप है। यह बताती है कि 32-bit binary sequence को floating-point number के रूप में कैसे interpreted किया जाता है, जिसमें zero, infinity, और NaN (Not a Number) जैसे special cases शामिल हैं।

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Let $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

Double कोई भी $(b_0,\dots,b_{63})$ है, जहाँ सभी $i \in \{0,\dots,63\}$ के लिए, $b_i \in \mathrm{Bit}$ होता है।

#### Double()

निम्न definition double-precision floating-point representation के लिए IEEE 754 standard के अनुरूप है। यह बताती है कि 64-bit binary sequence को floating-point number के रूप में कैसे interpreted किया जाता है, जिसमें zero, infinity, और NaN (Not a Number) जैसे special cases शामिल हैं।

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Let $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

Boolean कोई भी $b \in \{0,1\}$ है।

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## Text Encoding

### Text Encoding

Text encoding को निम्न set के रूप में define किया गया है:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Text Encoding()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Unicode codepoint कोई भी $e \in \mathbb{Z}$ है, जहाँ $0 \leq e \leq 0x10FFFF$।

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

An ASCII code unit is any $(b_0,\dots,b_6)$ such that for all $i \in \{0,\dots,6\}$, $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

Performance और compatibility कारणों से leading zero bit जोड़कर ASCII code unit को byte के रूप में represent करना सामान्य है। ऐसे cases में ASCII code unit इस प्रकार represent किया जाता है:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

अन्यथा:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

इस theorem के case में, दोनों definitions ASCII code unit की acceptable representations हैं। Consistency के लिए, ASCII code units को bytes के रूप में represent करते समय हम पहली definition का उपयोग करेंगे, और 7-bit sequences के रूप में represent करते समय दूसरी definition का।

#### ASCII()

ASCII is a null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ such that:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is an ASCII code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

इस sequence को null-terminated कहा जाता है।

### CP1252 Code Unit

A CP1252 code unit is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 is a null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ such that:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a CP1252 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

इस sequence को null-terminated कहा जाता है।

### UTF-8 Code Unit

A UTF-8 code unit is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 is a null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ such that:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-8 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

इस sequence को null-terminated कहा जाता है।

### UTF-16LE Code Unit

A UTF-16LE code unit is any $(b_0,\dots,b_{15})$ such that for all $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE is a null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ such that:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-16LE code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

इस sequence को null-terminated कहा जाता है।

## Operation Status

### Status Code

A status code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

Status code level को निम्न set के रूप में define किया गया है:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Status Code()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Status Code Level()

The set of status code values is the range $[0, 255]$, which is partitioned into four levels:

> Let $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Status Code Definition()

सभी status codes की explicit definitions होती हैं। निम्न list में शामिल न किया गया कोई भी status code future use के लिए reserved है, और उसका meaning undefined है। Status code का level $\mathrm{Status\ Code\ Level}(s)$ द्वारा निर्धारित होता है।

In the following list, the input $s$ is represented as a hexadecimal value for readability. Each defined status code specifies its corresponding level, category, sub-category, description, and detail, where applicable.

New status codes define होने पर इस list को extend किया जा सकता है। कोई भी नया defined status code existing codes से conflict नहीं करना चाहिए और उसका clearly documented meaning होना चाहिए।

Defined status code द्वारा represent न की गई information convey करने के लिए context code, operation code, या detail code का उपयोग किया जाना चाहिए।

##### Success

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | The operation completed successfully. | |
| `0x01` | SUCCESS | NOOP | The operation completed successfully without performing any action. | |

##### Warning

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | The operation completed, but the result may be unexpected or undesirable. | |
| `0x41` | WARNING | PARTIAL | The operation completed, but only partially. The output may be incomplete. | |
| `0x42` | WARNING | DEPRECATED | The operation completed, but it used a deprecated feature or behavior. The operation may no longer work in the future. | |

##### Error

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | The operation failed due to a recoverable error. | |
| `0x81` | ERROR | INVALID_ARGUMENT | The operation failed. An argument was invalid or out of range. | The index of the invalid argument, starting at 0 from left to right in the function's signature. |
| `0x82` | ERROR | INVALID_STATE | The operation failed. The system is in an inconsistent, corrupted, or otherwise invalid state. | |
| `0x83` | ERROR | MALFORMED_INPUT | The operation failed. A required input was malformed or contained invalid data. | |
| `0x84` | ERROR | ACCESS_DENIED | The operation failed because a required resource denied access. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | The operation failed because the requested feature or behavior is not yet implemented. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | The operation failed because the target system or configuration does not support the requested feature. | |
| `0x87` | ERROR | TIMEOUT | The operation failed because a required timeout occurred before completion. | |
| `0x88` | ERROR | NOT_FOUND | The operation failed because a required resource does not exist. | |
| `0x89` | ERROR | INTERRUPTED | The operation failed because an external event interrupted it. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | The operation failed because a required dependency failed. | The dependency's `STATUS_CODE` value. Callers are encouraged (but not required) to identify the failing dependency via the `OP_CODE` field. |
| `0x90` | ERROR | BUFFER_OVERFLOW | The operation failed. A buffer was too small to hold the required data. | |
| `0x91` | ERROR | ALLOCATION_FAILED | The operation failed. A memory allocation request was unsuccessful. | |
| `0xA0` | ERROR | IO_ERROR | The operation failed. An I/O error occurred during the operation. | |

##### Fatal

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | The operation failed due to an unrecoverable error. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | The operation failed because the system violated a fundamental invariant, indicating a critical logic error or data corruption. | |

### Context Code

A context code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Context Code()

Context code value completed operation के बारे में additional contextual information represent करती है, जैसा कि associated operation define करता है; जब status code level $\mathrm{Success}$ हो तो यह zero होना चाहिए, और अन्यथा implementation-defined होता है।

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Operation Code

An operation code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Operation Code()

Operation code value किसी result से associated operation को represent करती है। इसका meaning corresponding operation और उसकी documentation द्वारा define होता है। Undefined values को unknown माना जाता है।

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Detail Code

A detail code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Detail Code()

Detail code value completed operation के बारे में additional information represent करती है; उसका meaning associated status, context, या operation code (इसी क्रम में) द्वारा define होता है, और अन्यथा unknown होता है।

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Result

> [!TIP]
>
> A result value may be represented as a 32-bit integer. In big-endian byte order, the value appears as `0xSSCCOODD`, where `SS`, `CC`, `OO`, and `DD` correspond to the status code, context code, operation code, and detail code, respectively. In little-endian byte order, the same value appears as `0xDDOOCCSS`. Either byte order may be used, provided it is applied consistently and documented.

Result कोई भी $(b_0,\dots,b_{31})$ है, जहाँ सभी $i \in \{0,\dots,31\}$ के लिए, $b_i \in \mathrm{Bit}$ होता है।

Result को चार ordered bytes में partition किया जाता है:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

where $s$, $c$, $o$, and $d$ are the components of the result.

#### Result()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
