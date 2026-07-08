<!-- এই অনুবাদটি ChatGPT দ্বারা তৈরি করা হয়েছে এবং একজন মানব অনুবাদকের দ্বারা পর্যালোচনা করা উচিত। -->
<!-- অনুবাদটি যাচাই হওয়ার পরে একটি pull request-এ এই লাইনগুলো সরিয়ে ফেলুন। -->

# Verification Details

## Java

### Overview


![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)

Java programming language-টি July 7th, 2026 অনুযায়ী FDEFSPEC (Rev. 1) এবং FRELSPEC (Rev. 1) specifications-এর বিরুদ্ধে verified হয়েছে।

#### Good Faith Statement

আমরা good faith-এ বিশ্বাস করি যে Java programming language নিম্নের specifications-এ defined concepts এবং provisions-এর একটি বড় অংশ যুক্তিসঙ্গতভাবে represent করতে পারে, এবং এই specifications-এর সঙ্গে compliance-এ থাকা systems implement করতে ব্যবহার করা যেতে পারে।

#### Review Assumptions

এই review modern Java language support assume করে, যেখানে version-dependent features উল্লেখ করা হয়েছে। local variable inference, records, এবং foreign memory access-এর মতো features later Java versions require করতে পারে।

### Warnings

* Java unsigned numeric types-এর জন্য native support প্রদান করে না, যা কিছু provisions-এর জন্য widening বা alternative representations require করতে পারে।
* Direct memory address এবং pointer-style behavior Java 22+ Foreign Function and Memory API support require করতে পারে।
* Java native property syntax প্রদান করে না; এর পরিবর্তে getter এবং setter methods require করে।

### Failures

* Java CP1252-কে guaranteed standard charset হিসেবে প্রদান করে না; full compliance-এর জন্য implementation-specific support, additional libraries, বা custom handling require করে।
* Java properties required Get/Set accessor map দ্বারা backed explicit keyed member প্রদান করে না।

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Bit       | ⚠️       | 1-bit numeric নেই; widen করুন। |
| Nibble    | ⚠️       | 4-bit numeric নেই; widen করুন। |
| Byte      | ⚠️       | শুধু signed 8-bit; unsigned-এর জন্য widen করুন। |
| Short     | ⚠️       | শুধু signed 16-bit; unsigned-এর জন্য widen করুন। |
| Int       | ⚠️       | signed 32-bit; unsigned helpers Java 8+ require করে। |
| Long      | ⚠️       | signed 64-bit; unsigned helpers Java 8+ require করে। |
| Float     | ✅        | 32-bit floating point supported। |
| Double    | ✅        | 64-bit floating point supported। |
| Boolean   | ✅        | Boolean type supported। |

#### Text Encoding

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Codepoint | ✅        | `int` এবং `Character`-এর মাধ্যমে supported। |
| ASCII     | ✅        | guaranteed standard charset। |
| CP1252    | ❌        | `StandardCharsets` দ্বারা guaranteed নয়। |
| UTF-8     | ✅        | guaranteed standard charset। |
| UTF-16LE  | ✅        | guaranteed standard charset। |

#### Operation Status

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Status    | ✅        | custom type দ্বারা represented হতে পারে। |
| Context   | ✅        | custom value দ্বারা represented হতে পারে। |
| Operation | ✅        | custom value দ্বারা represented হতে পারে। |
| Detail    | ✅        | custom value দ্বারা represented হতে পারে। |
| Result    | ✅        | custom return type দ্বারা represented হতে পারে। |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Set       | ✅        | `Set`-এর মাধ্যমে supported। |
| Map       | ✅        | `Map`-এর মাধ্যমে supported। |
| Array     | ✅        | Native arrays supported। |
| File      | ✅        | file APIs-এর মাধ্যমে supported। |
| Stream    | ✅        | stream APIs-এর মাধ্যমে supported। |

#### Memory

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Address   | ⚠️       | Direct addresses Java 22+ FFM require করে। |
| Pointer   | ⚠️       | Pointer-like access Java 22+ FFM require করে। |
| Variable  | ✅        | Declarations এবং `var` supported; `var` Java 10+ require করে। |
| Constant  | ✅        | `final`-এর মাধ্যমে supported। |

#### Operations

| Provision   | Verified | Notes |
| ----------- | -------- | ----- |
| Instruction | ✅        | bytecode এবং operations-এর মাধ্যমে represented। |
| Procedure   | ✅        | `void` methods-এর মাধ্যমে supported। |
| Function    | ✅        | returning methods-এর মাধ্যমে supported। |

#### Threading

| Provision  | Verified | Notes |
| ---------- | -------- | ----- |
| Process    | ✅        | application এবং `Process` APIs-এর মাধ্যমে supported। |
| Thread     | ✅        | `Thread`-এর মাধ্যমে supported। |
| Dispatcher | ✅        | `Executor` APIs-এর মাধ্যমে supported। |

#### Composites

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Member    | ✅        | Class members supported। |
| Object    | ✅        | Objects supported। |
| Field     | ✅        | Fields supported। |
| Method    | ✅        | Methods supported। |
| Property  | ❌        | explicit accessor map নেই। |
| Structure | ✅        | records-এর মাধ্যমে supported; Java 16+। |
| Class     | ✅        | Classes supported। |
| Interface | ✅        | Interfaces supported। |
