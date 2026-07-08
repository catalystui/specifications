<!-- এই অনুবাদটি ChatGPT দ্বারা তৈরি করা হয়েছে এবং একজন মানব অনুবাদকের দ্বারা পর্যালোচনা করা উচিত। -->
<!-- অনুবাদটি যাচাই হওয়ার পরে একটি pull request-এ এই লাইনগুলো সরিয়ে ফেলুন। -->

# FDEFSPEC

<br/>

> **ভিত্তিগত সংজ্ঞা নির্দিষ্টকরণ**<br/>
> Revision 1<br/>
> March 23rd, 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/>
> <br/>
> এখানে উপস্থাপিত সংজ্ঞা ও ধারণাগুলি ভিত্তিগত গাণিতিক গঠন বর্ণনা করে এবং এগুলি স্বাধীনভাবে পুনরায় প্রকাশ করা যেতে পারে।

## ভূমিকা

**Foundational Definitions Specification (FDEFSPEC)** CatalystUI ইকোসিস্টেমের ভিত্তি হিসেবে থাকা মূল ধারণা ও পরিভাষাগুলি প্রতিষ্ঠা করে। এর উদ্দেশ্য হলো documentation, specifications, implementations, এবং verification reviews জুড়ে এই ধারণাগুলির একটি একীভূত বোঝাপড়া প্রদান করা, যাতে সামঞ্জস্য, স্বচ্ছতা, এবং alignment বজায় থাকে।

মূল পরিভাষা ও সম্পর্কগুলি নির্ভুল এবং স্থিতিশীল আকারে সংজ্ঞায়িত করার মাধ্যমে, FDEFSPEC উচ্চতর স্তরের specifications-এর জন্য একটি সাধারণ reference point প্রদান করে। এর ফলে developer, reviewer, এবং implementer-রা একই ভিত্তি থেকে বিচার করতে পারেন যে কোনো language, service, framework, বা system spec-এর মধ্যে বিবেচিত হতে পারে কি না।

> [!IMPORTANT]
>
> আমরা [set theory](https://en.wikipedia.org/wiki/Set_theory) notation-এর একটি derived form ব্যবহার করে সংজ্ঞা প্রকাশ করি। এই পদ্ধতি স্বচ্ছতা ও সংক্ষিপ্ততা বজায় রেখে নির্ভুল, দ্ব্যর্থহীন সংজ্ঞা প্রদান করে। সহজ reference, পরিষ্কার ব্যাখ্যা, এবং সামঞ্জস্যপূর্ণ conceptual hierarchy সমর্থন করার জন্য আমরা এই সংজ্ঞাগুলি সাজাই।

## সূচিপত্র

- [FDEFSPEC](#fdefspec)
  - [ভূমিকা](#ভূমিকা)
  - [সূচিপত্র](#সূচিপত্র)
  - [সংখ্যাতত্ত্ব](#সংখ্যাতত্ত্ব)
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

## সংখ্যাতত্ত্ব

### Bit

একটি bit হলো যেকোনো $b \in \{0,1\}$।

### Nibble

একটি nibble হলো যেকোনো $(b_0,\dots,b_3)$, যেখানে সব $i \in \{0,\dots,3\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

একটি byte হলো যেকোনো $(b_0,\dots,b_7)$, যেখানে সব $i \in \{0,\dots,7\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

একটি short হলো যেকোনো $(b_0,\dots,b_{15})$, যেখানে সব $i \in \{0,\dots,15\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

একটি integer হলো যেকোনো $(b_0,\dots,b_{31})$, যেখানে সব $i \in \{0,\dots,31\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

একটি long হলো যেকোনো $(b_0,\dots,b_{63})$, যেখানে সব $i \in \{0,\dots,63\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

একটি single হলো যেকোনো $(b_0,\dots,b_{31})$, যেখানে সব $i \in \{0,\dots,31\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### Single()

নিম্নের সংজ্ঞাটি single-precision floating-point representation-এর IEEE 754 standard অনুসরণ করে। এটি বর্ণনা করে কীভাবে একটি 32-bit binary sequence floating-point number হিসেবে ব্যাখ্যা করা হয়, যার মধ্যে zero, infinity, এবং NaN (Not a Number)-এর বিশেষ ক্ষেত্রও অন্তর্ভুক্ত।

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Let $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

একটি double হলো যেকোনো $(b_0,\dots,b_{63})$, যেখানে সব $i \in \{0,\dots,63\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### Double()

নিম্নের সংজ্ঞাটি double-precision floating-point representation-এর IEEE 754 standard অনুসরণ করে। এটি বর্ণনা করে কীভাবে একটি 64-bit binary sequence floating-point number হিসেবে ব্যাখ্যা করা হয়, যার মধ্যে zero, infinity, এবং NaN (Not a Number)-এর বিশেষ ক্ষেত্রও অন্তর্ভুক্ত।

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Let $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

একটি boolean হলো যেকোনো $b \in \{0,1\}$।

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## Text Encoding

### Text Encoding

একটি text encoding নিম্নের set হিসেবে সংজ্ঞায়িত:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Text Encoding()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

একটি Unicode codepoint হলো যেকোনো $e \in \mathbb{Z}$, যেখানে $0 \leq e \leq 0x10FFFF$।

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

একটি ASCII code unit হলো যেকোনো $(b_0,\dots,b_6)$, যেখানে সব $i \in \{0,\dots,6\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### ASCII Code Unit()

performance এবং compatibility-র কারণে leading zero bit যোগ করে ASCII code unit-কে byte হিসেবে উপস্থাপন করা সাধারণ। এ ক্ষেত্রে ASCII code unit নিম্নরূপে উপস্থাপিত হয়:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

অন্যথায়:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

এই theorem-এর ক্ষেত্রে, উভয় সংজ্ঞাই ASCII code unit-এর গ্রহণযোগ্য representation। consistency-র জন্য, ASCII code units-কে bytes হিসেবে উপস্থাপন করার সময় আমরা প্রথম সংজ্ঞা ব্যবহার করব, এবং 7-bit sequences হিসেবে উপস্থাপন করার সময় দ্বিতীয় সংজ্ঞা ব্যবহার করব।

#### ASCII()

ASCII হলো একটি null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$, যেখানে:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ একটি ASCII code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

sequence-টিকে null-terminated বলা হয়।

### CP1252 Code Unit

একটি CP1252 code unit হলো যেকোনো $(b_0,\dots,b_7)$, যেখানে সব $i \in \{0,\dots,7\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 হলো একটি null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$, যেখানে:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ একটি CP1252 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

sequence-টিকে null-terminated বলা হয়।

### UTF-8 Code Unit

একটি UTF-8 code unit হলো যেকোনো $(b_0,\dots,b_7)$, যেখানে সব $i \in \{0,\dots,7\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 হলো একটি null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$, যেখানে:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ একটি UTF-8 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

sequence-টিকে null-terminated বলা হয়।

### UTF-16LE Code Unit

একটি UTF-16LE code unit হলো যেকোনো $(b_0,\dots,b_{15})$, যেখানে সব $i \in \{0,\dots,15\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE হলো একটি null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$, যেখানে:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ একটি UTF-16LE code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

sequence-টিকে null-terminated বলা হয়।

## Operation Status

### Status Code

একটি status code হলো যেকোনো $(b_0,\dots,b_7)$, যেখানে সব $i \in \{0,\dots,7\}$-এর জন্য $b_i \in \mathrm{Bit}$।

একটি status code level নিম্নের set হিসেবে সংজ্ঞায়িত:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Status Code()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Status Code Level()

status code values-এর set হলো range $[0, 255]$, যা চারটি level-এ partition করা হয়েছে:

> Let $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Status Code Definition()

সব status code-এর explicit definition আছে। নিম্নের তালিকায় অন্তর্ভুক্ত নয় এমন যেকোনো status code ভবিষ্যৎ ব্যবহারের জন্য reserved, এবং তার অর্থ undefined। একটি status code-এর level $\mathrm{Status\ Code\ Level}(s)$ দ্বারা নির্ধারিত হয়।

নিম্নের তালিকায় readability-র জন্য input $s$ hexadecimal value হিসেবে উপস্থাপিত হয়েছে। প্রতিটি defined status code তার corresponding level, category, sub-category, description, এবং যেখানে প্রযোজ্য detail নির্দিষ্ট করে।

নতুন status code সংজ্ঞায়িত হলে এই তালিকা প্রসারিত হতে পারে। যেকোনো নতুন defined status code বিদ্যমান code-এর সঙ্গে conflict করবে না এবং তার clearly documented meaning থাকতে হবে।

যে তথ্য defined status code দ্বারা represent করা হয় না, তা প্রকাশ করতে context code, operation code, অথবা detail code ব্যবহার করা উচিত।

##### Success

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | operation সফলভাবে সম্পন্ন হয়েছে। | |
| `0x01` | SUCCESS | NOOP | কোনো action না করেই operation সফলভাবে সম্পন্ন হয়েছে। | |

##### Warning

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | operation সম্পন্ন হয়েছে, কিন্তু result unexpected বা undesirable হতে পারে। | |
| `0x41` | WARNING | PARTIAL | operation সম্পন্ন হয়েছে, কিন্তু আংশিকভাবে। output অসম্পূর্ণ হতে পারে। | |
| `0x42` | WARNING | DEPRECATED | operation সম্পন্ন হয়েছে, কিন্তু এটি deprecated feature বা behavior ব্যবহার করেছে। ভবিষ্যতে operation আর কাজ নাও করতে পারে। | |

##### Error

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | recoverable error-এর কারণে operation ব্যর্থ হয়েছে। | |
| `0x81` | ERROR | INVALID_ARGUMENT | operation ব্যর্থ হয়েছে। একটি argument invalid বা range-এর বাইরে ছিল। | function signature-এ বাম থেকে ডানে 0 থেকে শুরু করে invalid argument-এর index। |
| `0x82` | ERROR | INVALID_STATE | operation ব্যর্থ হয়েছে। system inconsistent, corrupted, অথবা অন্য কোনোভাবে invalid state-এ আছে। | |
| `0x83` | ERROR | MALFORMED_INPUT | operation ব্যর্থ হয়েছে। একটি required input malformed ছিল বা invalid data ধারণ করেছিল। | |
| `0x84` | ERROR | ACCESS_DENIED | required resource access অস্বীকার করায় operation ব্যর্থ হয়েছে। | |
| `0x85` | ERROR | NOT_IMPLEMENTED | requested feature বা behavior এখনো implemented নয় বলে operation ব্যর্থ হয়েছে। | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | target system বা configuration requested feature support করে না বলে operation ব্যর্থ হয়েছে। | |
| `0x87` | ERROR | TIMEOUT | completion-এর আগে required timeout ঘটায় operation ব্যর্থ হয়েছে। | |
| `0x88` | ERROR | NOT_FOUND | required resource বিদ্যমান নেই বলে operation ব্যর্থ হয়েছে। | |
| `0x89` | ERROR | INTERRUPTED | external event operation interrupted করায় operation ব্যর্থ হয়েছে। | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | required dependency ব্যর্থ হওয়ায় operation ব্যর্থ হয়েছে। | dependency-এর `STATUS_CODE` value। callers-দের failing dependency `OP_CODE` field-এর মাধ্যমে শনাক্ত করতে উৎসাহিত করা হয়, তবে তা required নয়। |
| `0x90` | ERROR | BUFFER_OVERFLOW | operation ব্যর্থ হয়েছে। required data ধারণ করার জন্য buffer খুব ছোট ছিল। | |
| `0x91` | ERROR | ALLOCATION_FAILED | operation ব্যর্থ হয়েছে। memory allocation request সফল হয়নি। | |
| `0xA0` | ERROR | IO_ERROR | operation ব্যর্থ হয়েছে। operation চলাকালীন I/O error ঘটেছে। | |

##### Fatal

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | unrecoverable error-এর কারণে operation ব্যর্থ হয়েছে। | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | system একটি fundamental invariant লঙ্ঘন করায় operation ব্যর্থ হয়েছে, যা critical logic error বা data corruption নির্দেশ করে। | |

### Context Code

একটি context code হলো যেকোনো $(b_0,\dots,b_7)$, যেখানে সব $i \in \{0,\dots,7\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### Context Code()

একটি context code value completed operation সম্পর্কে অতিরিক্ত contextual information উপস্থাপন করে, যা associated operation দ্বারা defined; status code level $\mathrm{Success}$ হলে এটি zero হতে হবে, অন্যথায় এটি implementation-defined।

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Operation Code

একটি operation code হলো যেকোনো $(b_0,\dots,b_7)$, যেখানে সব $i \in \{0,\dots,7\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### Operation Code()

একটি operation code value result-এর সঙ্গে associated operation উপস্থাপন করে। এর meaning corresponding operation এবং তার documentation দ্বারা defined। Undefined values unknown হিসেবে বিবেচিত হয়।

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Detail Code

একটি detail code হলো যেকোনো $(b_0,\dots,b_7)$, যেখানে সব $i \in \{0,\dots,7\}$-এর জন্য $b_i \in \mathrm{Bit}$।

#### Detail Code()

একটি detail code value completed operation সম্পর্কে অতিরিক্ত information উপস্থাপন করে; তার meaning associated status, context, অথবা operation code দ্বারা defined হয়, সেই ক্রমে, এবং অন্যথায় unknown।

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Result

> [!TIP]
>
> একটি result value 32-bit integer হিসেবে উপস্থাপিত হতে পারে। big-endian byte order-এ value `0xSSCCOODD` হিসেবে দেখা যায়, যেখানে `SS`, `CC`, `OO`, এবং `DD` যথাক্রমে status code, context code, operation code, এবং detail code-এর সঙ্গে সম্পর্কিত। little-endian byte order-এ একই value `0xDDOOCCSS` হিসেবে দেখা যায়। byte order যেকোনোটি ব্যবহার করা যেতে পারে, শর্ত হলো সেটি consistently প্রয়োগ এবং documented হবে।

একটি result হলো যেকোনো $(b_0,\dots,b_{31})$, যেখানে সব $i \in \{0,\dots,31\}$-এর জন্য $b_i \in \mathrm{Bit}$।

একটি result চারটি ordered byte-এ partition করা হয়:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

যেখানে $s$, $c$, $o$, এবং $d$ result-এর components।

#### Result()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
