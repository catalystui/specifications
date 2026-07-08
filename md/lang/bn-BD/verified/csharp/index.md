<!-- এই অনুবাদটি ChatGPT দ্বারা তৈরি করা হয়েছে এবং একজন মানব অনুবাদকের দ্বারা পর্যালোচনা করা উচিত। -->
<!-- অনুবাদটি যাচাই হওয়ার পরে একটি pull request-এ এই লাইনগুলো সরিয়ে ফেলুন। -->

# Verification Details

## C#

### Overview


![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)

C# programming language-টি July 7th, 2026 অনুযায়ী FDEFSPEC (Rev. 1) এবং FRELSPEC (Rev. 1) specifications-এর বিরুদ্ধে verified হয়েছে।

#### Good Faith Statement

আমরা good faith-এ বিশ্বাস করি যে C# programming language নিম্নের specifications-এ defined concepts এবং provisions যুক্তিসঙ্গতভাবে represent করতে পারে, এবং এই specifications-এর সঙ্গে compliance-এ থাকা systems implement করতে ব্যবহার করা যেতে পারে।

#### Review Assumptions

এই review modern C# এবং .NET support assume করে, যেখানে version-dependent features উল্লেখ করা হয়েছে।

### Warnings

* CP1252 support official .NET code pages provider-এর মাধ্যমে available, কিন্তু target runtime অনুযায়ী provider registration বা additional package require করতে পারে।
* Unsafe pointer behavior explicit unsafe authorization require করতে পারে।

### Failures

* এই verification-এ কোনো known FDEFSPEC বা FRELSPEC failures পাওয়া যায়নি।

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Bit       | ⚠️       | 1-bit numeric নেই; widen করুন। |
| Nibble    | ⚠️       | 4-bit numeric নেই; widen করুন। |
| Byte      | ✅        | `byte` এবং `sbyte`-এর মাধ্যমে supported। |
| Short     | ✅        | `short` এবং `ushort`-এর মাধ্যমে supported। |
| Int       | ✅        | `int` এবং `uint`-এর মাধ্যমে supported। |
| Long      | ✅        | `long` এবং `ulong`-এর মাধ্যমে supported। |
| Float     | ✅        | `float`-এর মাধ্যমে supported। |
| Double    | ✅        | `double`-এর মাধ্যমে supported। |
| Boolean   | ✅        | `bool`-এর মাধ্যমে supported। |

#### Text Encoding

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Codepoint | ✅        | numerics এবং `Rune`-এর মাধ্যমে supported। |
| ASCII     | ✅        | `Encoding.ASCII`-এর মাধ্যমে supported। |
| CP1252    | ⚠️       | code pages provider require করে। |
| UTF-8     | ✅        | `Encoding.UTF8`-এর মাধ্যমে supported। |
| UTF-16LE  | ✅        | `Encoding.Unicode`-এর মাধ্যমে supported। |

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
| Set       | ✅        | `HashSet<T>`-এর মাধ্যমে supported। |
| Map       | ✅        | `Dictionary<TKey,TValue>`-এর মাধ্যমে supported। |
| Array     | ✅        | Native arrays supported। |
| File      | ✅        | file APIs-এর মাধ্যমে supported। |
| Stream    | ✅        | `Stream`-এর মাধ্যমে supported। |

#### Memory

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Address   | ✅        | references এবং pointers-এর মাধ্যমে supported। |
| Pointer   | ✅        | unsafe pointers-এর মাধ্যমে supported। |
| Variable  | ✅        | Variables supported। |
| Constant  | ✅        | `const` এবং `readonly`-এর মাধ্যমে supported। |

#### Operations

| Provision   | Verified | Notes |
| ----------- | -------- | ----- |
| Instruction | ✅        | IL এবং operations-এর মাধ্যমে represented। |
| Procedure   | ✅        | `void` methods-এর মাধ্যমে supported। |
| Function    | ✅        | returning methods-এর মাধ্যমে supported। |

#### Threading

| Provision  | Verified | Notes |
| ---------- | -------- | ----- |
| Process    | ✅        | application এবং `Process` APIs-এর মাধ্যমে supported। |
| Thread     | ✅        | `Thread`-এর মাধ্যমে supported। |
| Dispatcher | ✅        | tasks এবং schedulers-এর মাধ্যমে supported। |

#### Composites

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Member    | ✅        | Type members supported। |
| Object    | ✅        | Objects supported। |
| Field     | ✅        | Fields supported। |
| Method    | ✅        | Methods supported। |
| Property  | ✅        | Properties natively supported। |
| Structure | ✅        | Structures natively supported। |
| Class     | ✅        | Classes supported। |
| Interface | ✅        | Interfaces supported। |
