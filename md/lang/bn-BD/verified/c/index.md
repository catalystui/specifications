<!-- এই অনুবাদটি ChatGPT দ্বারা তৈরি করা হয়েছে এবং একজন মানব অনুবাদকের দ্বারা পর্যালোচনা করা উচিত। -->
<!-- অনুবাদটি যাচাই হওয়ার পরে একটি pull request-এ এই লাইনগুলো সরিয়ে ফেলুন। -->

# Verification Details

## C

### Overview


![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)

C programming language-টি July 7th, 2026 অনুযায়ী FDEFSPEC (Rev. 1) এবং FRELSPEC (Rev. 1) specifications-এর বিরুদ্ধে verified হয়েছে।

#### Good Faith Statement

আমরা good faith-এ বিশ্বাস করি যে C programming language নিম্নের specifications-এ defined concepts এবং provisions যুক্তিসঙ্গতভাবে represent করতে পারে, এবং এই specifications-এর সঙ্গে compliance-এ থাকা systems implement করতে ব্যবহার করা যেতে পারে।

#### Review Statement

C foundational data representation, memory access, files, streams, procedures, functions, structures, এবং direct system-oriented implementation-এর জন্য শক্তিশালী low-level support প্রদান করে।

C বেশ কিছু object-oriented composite constructs nativeভাবে প্রদান না করলেও, এই limitations নির্দিষ্ট FRELSPEC composite provisions-এ সীমাবদ্ধ এবং নিচে documented। এই failures C-কে overall within spec বিবেচনা করা থেকে prevent করে না, তবে CatalystUI-compatible implementations-এর জন্য C ব্যবহার করার সময় এগুলি বোঝা উচিত।

#### Review Assumptions

এই review modern standard C support assume করে, যেখানে version-dependent features উল্লেখ করা হয়েছে। Exact-width integer support assume করে যে corresponding `<stdint.h>` types implementation দ্বারা provided।

এই review C-কে low-level representation language হিসেবে treats করে। কোনো named standard codec না থাকলে byte-exact encodings direct byte arrays, lookup tables, এবং explicit parsing logic-এর মাধ্যমে represented হতে পারে।

### Warnings

* Exact-width integer types implementation support-এর ওপর depend করে।
* CP1252 byte-for-byte represented হতে পারে, কিন্তু named standard codec provided নয়।
* UTF-16LE serialization explicit byte-order handling require করে।
* Standard threads কিছু C implementations-এ omitted হতে পারে।
* Object-oriented patterns manually emulated হতে পারে, কিন্তু native language constructs নয়।

### Failures

* C native method members প্রদান করে না।
* C native properties প্রদান করে না।
* C native classes প্রদান করে না।
* C native interfaces প্রদান করে না।

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Bit       | ⚠️       | bit-fields বা masks ব্যবহার করুন। |
| Nibble    | ⚠️       | bit-fields বা masks ব্যবহার করুন। |
| Byte      | ✅        | `unsigned char`-এর মাধ্যমে supported। |
| Short     | ✅        | `int16_t` এবং `uint16_t`-এর মাধ্যমে supported। |
| Int       | ✅        | `int32_t` এবং `uint32_t`-এর মাধ্যমে supported। |
| Long      | ✅        | `int64_t` এবং `uint64_t`-এর মাধ্যমে supported। |
| Float     | ✅        | `float`-এর মাধ্যমে supported। |
| Double    | ✅        | `double`-এর মাধ্যমে supported। |
| Boolean   | ✅        | `bool`-এর মাধ্যমে supported; C99+। |

#### Text Encoding

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Codepoint | ✅        | `char32_t`-এর মাধ্যমে supported; C11+। |
| ASCII     | ✅        | byte values হিসেবে representable। |
| CP1252    | ⚠️        | explicit byte mapping require করে। |
| UTF-8     | ✅        | UTF-8 literals-এর মাধ্যমে supported; C11+। |
| UTF-16LE  | ⚠️        | byte-order handling require করে। |

#### Operation Status

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Status    | ✅        | enum দ্বারা represented হতে পারে। |
| Context   | ✅        | value দ্বারা represented হতে পারে। |
| Operation | ✅        | value দ্বারা represented হতে পারে। |
| Detail    | ✅        | value দ্বারা represented হতে পারে। |
| Result    | ✅        | struct দ্বারা represented হতে পারে। |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Set       | ✅        | structs দ্বারা represented হতে পারে। |
| Map       | ✅        | structs দ্বারা represented হতে পারে। |
| Array     | ✅        | Native arrays supported। |
| File      | ✅        | file APIs-এর মাধ্যমে supported। |
| Stream    | ✅        | stream APIs-এর মাধ্যমে supported। |

#### Memory

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Address   | ✅        | Addresses supported। |
| Pointer   | ✅        | Pointers supported। |
| Variable  | ✅        | Variables supported। |
| Constant  | ✅        | `const`-এর মাধ্যমে supported। |

#### Operations

| Provision   | Verified | Notes |
| ----------- | -------- | ----- |
| Instruction | ✅        | machine operations-এর মাধ্যমে represented। |
| Procedure   | ✅        | `void` functions-এর মাধ্যমে supported। |
| Function    | ✅        | returning functions-এর মাধ্যমে supported। |

#### Threading

| Provision  | Verified | Notes |
| ---------- | -------- | ----- |
| Process    | ✅        | hosted environments-এর মাধ্যমে supported। |
| Thread     | ⚠️        | `<threads.h>`-এর মাধ্যমে supported; C11+। |
| Dispatcher | ✅        | directly represented হতে পারে। |

#### Composites

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Member    | ✅        | Struct members supported। |
| Object    | ✅        | Structs addressable composites গঠন করতে পারে। |
| Field     | ✅        | Struct fields supported। |
| Method    | ❌        | native method members নেই। |
| Property  | ❌        | explicit Get/Set accessor map নেই। |
| Structure | ✅        | Structures natively supported। |
| Class     | ❌        | native class construct নেই। |
| Interface | ❌        | native interface construct নেই। |
