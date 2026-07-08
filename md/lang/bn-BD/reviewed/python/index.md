<!-- এই অনুবাদটি ChatGPT দ্বারা তৈরি করা হয়েছে এবং একজন মানব অনুবাদকের দ্বারা পর্যালোচনা করা উচিত। -->
<!-- অনুবাদটি যাচাই হওয়ার পরে একটি pull request-এ এই লাইনগুলো সরিয়ে ফেলুন। -->

# Review Details

## Python

### Overview

Python programming language-টি July 7th, 2026 অনুযায়ী FDEFSPEC (Rev. 1) এবং FRELSPEC (Rev. 1) specifications-এর বিরুদ্ধে reviewed হয়েছে।

#### Review Statement

Python built-in types, objects, functions, classes, standard-library modules, এবং custom validation-এর মাধ্যমে বহু required concepts represent করতে পারলেও, language level-এ applicable CatalystUI specifications satisfy করার জন্য এই mechanisms যথেষ্ট নয়।

Python text encoding, files, streams, objects, functions, classes, properties, processes, threads, এবং dispatched execution-এর জন্য built-in behavior ও standard library-র মাধ্যমে শক্তিশালী support প্রদান করে। তবে Python required fixed-width scalar numeric types প্রদান করে না, true constants define করে না, এবং এমন several constructs-এর জন্য dynamic runtime behavior-এর ওপর নির্ভর করে যা অন্য verified languages আরও directly express করতে পারে।

এই কারণে, significant additional infrastructure ছাড়া Python CatalystUI-compliant implementation-এর জন্য যথেষ্ট stable foundation প্রদান করে বলে আমরা বিশ্বাস করি না।

ফলে Programming Languages-এর জন্য Python-কে CatalystUI Verified status দেওয়া হয়নি।

#### Review Assumptions

এই review Python নিজে এবং তার bundled standard library evaluate করে।

Third-party packages, implementation-specific extensions, optional native modules, external type checkers, transpilers, এবং custom runtime frameworks language-level support হিসেবে ধরা হয় না।

### Warnings

* Python unlimited-precision integers প্রদান করে, fixed-width integer primitives নয়।
* Python `float` সাধারণত double precision, কিন্তু distinct fixed-width family নয়।
* কিছু low-level memory behavior-এর জন্য `ctypes` বা implementation-specific behavior দরকার হতে পারে।
* Python type hints runtime-এ enforced নয়।
* Python properties support করে, কিন্তু setter behavior omitted হতে পারে।
* Python standard-library features-এর মাধ্যমে several structures model করতে পারে, কিন্তু native structure type হিসেবে নয়।

### Failures

* Python অধিকাংশ required fixed-width scalar numeric types প্রদান করে না।
* Python dedicated scalar 32-bit floating point type প্রদান করে না।
* Python true language-level constants প্রদান করে না।
* Python functions থেকে procedures আলাদা করে define করে না।
* Python native pointer support প্রদান করে না।
* Python native interface support প্রদান করে না।

### FDEFSPEC Verification

#### Numerics

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Bit       | ❌        | 1-bit numeric type নেই। |
| Nibble    | ❌        | 4-bit numeric type নেই। |
| Byte      | ❌        | scalar 8-bit integer type নেই। |
| Short     | ❌        | scalar 16-bit integer type নেই। |
| Int       | ❌        | scalar 32-bit integer type নেই। |
| Long      | ❌        | scalar 64-bit integer type নেই। |
| Float     | ❌        | scalar 32-bit float type নেই। |
| Double    | ⚠️       | `float` সাধারণত double precision। |
| Boolean   | ✅        | `bool`-এর মাধ্যমে supported। |

#### Text Encoding

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Codepoint | ✅        | Strings Unicode code points ব্যবহার করে। |
| ASCII     | ✅        | Supported codec। |
| CP1252    | ✅        | Supported codec। |
| UTF-8     | ✅        | Supported codec। |
| UTF-16LE  | ✅        | Supported codec। |

#### Operation Status

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Status    | ⚠️       | custom validation require করে। |
| Context   | ⚠️       | custom validation require করে। |
| Operation | ⚠️       | custom validation require করে। |
| Detail    | ⚠️       | custom validation require করে। |
| Result    | ⚠️       | custom validation require করে। |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Set       | ✅        | `set`-এর মাধ্যমে supported। |
| Map       | ✅        | `dict`-এর মাধ্যমে supported। |
| Array     | ✅        | sequences-এর মাধ্যমে supported। |
| File      | ✅        | file APIs-এর মাধ্যমে supported। |
| Stream    | ✅        | stream APIs-এর মাধ্যমে supported। |

#### Memory

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Address   | ⚠️       | শুধু object identity। |
| Pointer   | ❌        | native pointer support নেই। |
| Variable  | ✅        | Name bindings supported। |
| Constant  | ❌        | true constants নেই। |

#### Operations

| Provision   | Verified | Notes |
| ----------- | -------- | ----- |
| Instruction | ⚠️       | Bytecode implementation-level। |
| Procedure   | ❌        | Functions `None` return করে। |
| Function    | ✅        | Functions supported। |

#### Threading

| Provision  | Verified | Notes |
| ---------- | -------- | ----- |
| Process    | ✅        | process APIs-এর মাধ্যমে supported। |
| Thread     | ✅        | `threading`-এর মাধ্যমে supported। |
| Dispatcher | ✅        | executor APIs-এর মাধ্যমে supported। |

#### Composites

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Member    | ✅        | Object members supported। |
| Object    | ✅        | Objects supported। |
| Field     | ✅        | Attributes fields represent করতে পারে। |
| Method    | ✅        | Methods supported। |
| Property  | ⚠️       | Getter/setter support আছে। |
| Structure | ⚠️       | শুধু standard-library models। |
| Class     | ✅        | Classes supported। |
| Interface | ❌        | native interface support নেই। |
