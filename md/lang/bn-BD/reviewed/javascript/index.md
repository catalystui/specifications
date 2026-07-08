<!-- এই অনুবাদটি ChatGPT দ্বারা তৈরি করা হয়েছে এবং একজন মানব অনুবাদকের দ্বারা পর্যালোচনা করা উচিত। -->
<!-- অনুবাদটি যাচাই হওয়ার পরে একটি pull request-এ এই লাইনগুলো সরিয়ে ফেলুন। -->

# Review Details

## JavaScript

### Overview

JavaScript programming language-টি July 7th, 2026 অনুযায়ী FDEFSPEC (Rev. 1) এবং FRELSPEC (Rev. 1) specifications-এর বিরুদ্ধে reviewed হয়েছে।

#### Review Statement

JavaScript objects, functions, arrays, এবং built-in language behavior-এর মাধ্যমে কিছু required concepts represent করতে পারলেও, language level-এ applicable CatalystUI specifications satisfy করার জন্য এই mechanisms যথেষ্ট নয়।

এই review JavaScript নিজেকেই evaluate করে, surrounding JavaScript ecosystem নয়। Browser APIs, Node.js APIs, Deno APIs, Bun APIs, Web APIs, TypeScript, WebAssembly, external libraries, এবং custom validation-কে language-level support হিসেবে ধরা হয় না।

JavaScript-এ অনেক required fixed-width scalar numeric types নেই, required text encodings language features হিসেবে প্রদান করে না, এবং বেশ কিছু required system, memory, threading, ও composite constructs define করে না। তাই significant additional infrastructure ছাড়া JavaScript CatalystUI-compliant implementation-এর জন্য যথেষ্ট stable foundation প্রদান করে বলে আমরা বিশ্বাস করি না।

ফলে Programming Languages-এর জন্য JavaScript-কে CatalystUI Verified status দেওয়া হয়নি।

#### Review Assumptions

এই review strict language-level standard প্রয়োগ করে। কোনো provision JavaScript নিজে explicitly support না করলে, সেটি not verified হিসেবে marked।

Host-provided APIs, implementation-specific behavior, external libraries, transpilers, type systems, এবং custom runtime validation verification থেকে excluded।

### Warnings

* JavaScript `Number`-এর মাধ্যমে বহু numeric values represent করতে পারে, কিন্তু `Number` একটি 64-bit floating point numeric type।
* JavaScript `BigInt` প্রদান করে, কিন্তু `BigInt` arbitrary-width।
* Typed arrays binary storage views প্রদান করে, scalar language types নয়।
* JavaScript strings UTF-16 code units ব্যবহার করে, explicit text encoding values নয়।
* `const` bindings protect করে, object values নয়।

### Failures

* JavaScript অধিকাংশ required fixed-width scalar numeric types প্রদান করে না।
* JavaScript dedicated scalar 32-bit floating point type প্রদান করে না।
* JavaScript language-level text encodings হিসেবে ASCII, CP1252, UTF-8, বা UTF-16LE প্রদান করে না।
* JavaScript language-level file বা stream constructs প্রদান করে না।
* JavaScript language-level address বা pointer constructs প্রদান করে না।
* JavaScript language-level process, thread, বা dispatcher constructs প্রদান করে না।
* JavaScript properties required Get/Set accessor map দ্বারা backed explicit keyed member প্রদান করে না।
* JavaScript structures বা interfaces প্রদান করে না।

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
| Double    | ✅        | `Number`-এর মাধ্যমে supported। |
| Boolean   | ✅        | `boolean`-এর মাধ্যমে supported। |

#### Text Encoding

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Codepoint | ❌        | dedicated codepoint type নেই। |
| ASCII     | ❌        | language-level নয়। |
| CP1252    | ❌        | language-level নয়। |
| UTF-8     | ❌        | language-level নয়। |
| UTF-16LE  | ❌        | language-level নয়। |

#### Operation Status

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Status    | ⚠️       | Representable, enforceable নয়। |
| Context   | ⚠️       | Representable, enforceable নয়। |
| Operation | ⚠️       | Representable, enforceable নয়। |
| Detail    | ⚠️       | Representable, enforceable নয়। |
| Result    | ⚠️       | runtime validation require করে। |

### FRELSPEC Verification

#### Collections

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Set       | ✅        | `Set`-এর মাধ্যমে supported। |
| Map       | ✅        | `Map`-এর মাধ্যমে supported। |
| Array     | ✅        | Arrays supported। |
| File      | ❌        | language-level নয়। |
| Stream    | ❌        | language-level নয়। |

#### Memory

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Address   | ❌        | address support নেই। |
| Pointer   | ❌        | pointer support নেই। |
| Variable  | ✅        | Variables supported। |
| Constant  | ⚠️       | `const` শুধু bindings protect করে। |

#### Operations

| Provision   | Verified | Notes |
| ----------- | -------- | ----- |
| Instruction | ❌        | defined instruction type নেই। |
| Procedure   | ❌        | Functions সবসময় value return করে। |
| Function    | ✅        | Functions supported। |

#### Threading

| Provision  | Verified | Notes |
| ---------- | -------- | ----- |
| Process    | ❌        | language-level নয়। |
| Thread     | ⚠️        | agents-এর মাধ্যমে represented। |
| Dispatcher | ❌        | host scheduling require করে। |

#### Composites

| Provision | Verified | Notes |
| --------- | -------- | ----- |
| Member    | ✅        | Object members supported। |
| Object    | ✅        | Objects supported। |
| Field     | ✅        | Data properties fields represent করতে পারে। |
| Method    | ✅        | Methods supported। |
| Property  | ❌        | explicit accessor map নেই। |
| Structure | ❌        | structure support নেই। |
| Class     | ✅        | Class syntax supported। |
| Interface | ❌        | interface support নেই। |
