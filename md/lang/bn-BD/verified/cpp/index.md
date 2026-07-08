<!-- এই অনুবাদটি ChatGPT দ্বারা তৈরি করা হয়েছে এবং একজন মানব অনুবাদকের দ্বারা পর্যালোচনা করা উচিত। -->
<!-- অনুবাদটি যাচাই হওয়ার পরে একটি pull request-এ এই লাইনগুলো সরিয়ে ফেলুন। -->

# Verification Details

## C++

### Overview


![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)

C++ programming language-টি July 7th, 2026 অনুযায়ী FDEFSPEC (Rev. 1) এবং FRELSPEC (Rev. 1) specifications-এর বিরুদ্ধে verified হয়েছে।

#### Good Faith Statement

আমরা good faith-এ বিশ্বাস করি যে C++ programming language নিম্নের specifications-এ defined concepts এবং provisions যুক্তিসঙ্গতভাবে represent করতে পারে, এবং এই specifications-এর সঙ্গে compliance-এ থাকা systems implement করতে ব্যবহার করা যেতে পারে।

#### Review Assumptions

এই review modern standard C++ support assume করে, যেখানে version-dependent features উল্লেখ করা হয়েছে। Exact-width integer support assume করে যে corresponding `<cstdint>` types implementation দ্বারা provided।

এই review C++-কে systems programming language হিসেবে treats করে, যেখানে low-level representation, object modeling, memory control, generic programming, এবং concurrent execution-এর জন্য direct support রয়েছে।

### Warnings

* Exact-width integer types implementation support-এর ওপর depend করে।
* CP1252 byte-for-byte represented হতে পারে, কিন্তু named standard codec provided নয়।
* UTF-16LE serialization explicit byte-order handling require করে।
* কিছু concurrency এবং character features modern C++ revisions require করে।

### Failures

* এই verification-এ কোনো known FDEFSPEC বা FRELSPEC failures পাওয়া যায়নি।

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Bit       | ⚠️       | bit-fields বা masks ব্যবহার করুন। |
| Nibble    | ⚠️       | bit-fields বা masks ব্যবহার করুন। |
| Byte      | ✅        | `std::byte`-এর মাধ্যমে supported। |
| Short     | ✅        | `int16_t` এবং `uint16_t`-এর মাধ্যমে supported। |
| Int       | ✅        | `int32_t` এবং `uint32_t`-এর মাধ্যমে supported। |
| Long      | ✅        | `int64_t` এবং `uint64_t`-এর মাধ্যমে supported। |
| Float     | ✅        | `float`-এর মাধ্যমে supported। |
| Double    | ✅        | `double`-এর মাধ্যমে supported। |
| Boolean   | ✅        | `bool`-এর মাধ্যমে supported। |

#### Text Encoding

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Codepoint | ✅        | `char32_t`-এর মাধ্যমে supported। |
| ASCII     | ✅        | byte values হিসেবে representable। |
| CP1252    | ⚠️        | explicit byte mapping require করে। |
| UTF-8     | ✅        | `char8_t`-এর মাধ্যমে supported; C++20+। |
| UTF-16LE  | ⚠️        | byte-order handling require করে। |

#### Operation Status

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Status    | ✅        | enum দ্বারা represented হতে পারে। |
| Context   | ✅        | value দ্বারা represented হতে পারে। |
| Operation | ✅        | value দ্বারা represented হতে পারে। |
| Detail    | ✅        | value দ্বারা represented হতে পারে। |
| Result    | ✅        | struct বা class দ্বারা represented হতে পারে। |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Set       | ✅        | `std::set`-এর মাধ্যমে supported। |
| Map       | ✅        | `std::map`-এর মাধ্যমে supported। |
| Array     | ✅        | arrays এবং `std::array`-এর মাধ্যমে supported। |
| File      | ✅        | file streams-এর মাধ্যমে supported। |
| Stream    | ✅        | iostreams-এর মাধ্যমে supported। |

#### Memory

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Address   | ✅        | Addresses supported। |
| Pointer   | ✅        | Pointers supported। |
| Variable  | ✅        | Variables supported। |
| Constant  | ✅        | `const` এবং `constexpr`-এর মাধ্যমে supported। |

#### Operations

| Provision   | Verified | Notes |
| ----------- | -------- | ----- |
| Instruction | ✅        | machine operations-এর মাধ্যমে represented। |
| Procedure   | ✅        | `void` functions-এর মাধ্যমে supported। |
| Function    | ✅        | returning functions-এর মাধ্যমে supported। |

#### Threading

| Provision  | Verified | Notes |
| ---------- | -------- | ----- |
| Process    | ✅        | hosted execution-এর মাধ্যমে supported। |
| Thread     | ✅        | `std::thread`-এর মাধ্যমে supported; C++11+। |
| Dispatcher | ✅        | async এবং schedulers-এর মাধ্যমে supported। |

#### Composites

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Member    | ✅        | Class members supported। |
| Object    | ✅        | Objects supported। |
| Field     | ✅        | Fields supported। |
| Method    | ✅        | Methods supported। |
| Property  | ✅        | Get/Set maps represented হতে পারে। |
| Structure | ✅        | Structures natively supported। |
| Class     | ✅        | Classes natively supported। |
| Interface | ✅        | abstract classes দ্বারা represented হতে পারে। |
