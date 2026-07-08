<!-- Цей переклад було створено ChatGPT, і його має перевірити людина-перекладач. -->
<!-- Видаліть ці рядки в pull request після перевірки перекладу. -->

# Review Details

## JavaScript

### Огляд

Мову програмування JavaScript розглянуто відповідно до специфікацій FDEFSPEC (Rev. 1) і FRELSPEC (Rev. 1) станом на 7 липня 2026 р.

#### Review Statement

While JavaScript can represent some required concepts through objects, functions, arrays, and built-in language behavior, these mechanisms are not sufficient to satisfy the applicable CatalystUI specifications at the language level.

This review evaluates JavaScript itself, not the surrounding JavaScript ecosystem. Browser APIs, Node.js APIs, Deno APIs, Bun APIs, Web APIs, TypeScript, WebAssembly, external libraries, and custom validation are not treated as language-level support.

Because JavaScript lacks many required fixed-width scalar numeric types, does not provide required text encodings as language features, and does not define several required system, memory, threading, and composite constructs, we do not believe JavaScript provides a stable enough foundation for CatalystUI-compliant implementation without significant additional infrastructure.

As a result, JavaScript has not been granted CatalystUI Verified status for Programming Languages.

#### Припущення розгляду

This review applies a strict language-level standard. If a provision is not explicitly supported by JavaScript itself, it is marked as not verified.

Host-provided APIs, implementation-specific behavior, external libraries, transpilers, type systems, and custom runtime validation are excluded from verification.

### Попередження

* JavaScript can represent many numeric values through `Number`, but `Number` is a 64-bit floating point numeric type.
* JavaScript provides `BigInt`, but `BigInt` is arbitrary-width.
* Typed arrays provide binary storage views, not scalar language types.
* JavaScript strings use UTF-16 code units, not explicit text encoding values.
* `const` protects bindings, not object values.

### Невідповідності

* JavaScript does not provide most required fixed-width scalar numeric types.
* JavaScript does not provide a dedicated scalar 32-bit floating point type.
* JavaScript does not provide ASCII, CP1252, UTF-8, or UTF-16LE as language-level text encodings.
* JavaScript does not provide language-level file or stream constructs.
* JavaScript does not provide language-level address or pointer constructs.
* JavaScript does not provide language-level process, thread, or dispatcher constructs.
* JavaScript properties do not provide an explicit keyed member backed by a required Get/Set accessor map.
* JavaScript does not provide structures or interfaces.

### Верифікація FDEFSPEC

#### Числові типи

| Положення | Верифіковано | Примітки                          |
| --------- | -------- | ------------------------------ |
| Bit       | ❌        | No 1-bit numeric type.         |
| Nibble    | ❌        | No 4-bit numeric type.         |
| Byte      | ❌        | No scalar 8-bit integer type.  |
| Short     | ❌        | No scalar 16-bit integer type. |
| Int       | ❌        | No scalar 32-bit integer type. |
| Long      | ❌        | No scalar 64-bit integer type. |
| Float     | ❌        | No scalar 32-bit float type.   |
| Double    | ✅        | Підтримується через `Number`.    |
| Boolean   | ✅        | Підтримується через `boolean`.   |

#### Кодування тексту

| Положення | Верифіковано | Примітки                        |
| --------- | -------- | ---------------------------- |
| Codepoint | ❌        | No dedicated codepoint type. |
| ASCII     | ❌        | Not language-level.          |
| CP1252    | ❌        | Not language-level.          |
| UTF-8     | ❌        | Not language-level.          |
| UTF-16LE  | ❌        | Not language-level.          |

#### Статус операції

| Положення | Верифіковано | Примітки                           |
| --------- | -------- | ------------------------------- |
| Status    | ⚠️       | Representable, not enforceable. |
| Context   | ⚠️       | Representable, not enforceable. |
| Operation | ⚠️       | Representable, not enforceable. |
| Detail    | ⚠️       | Representable, not enforceable. |
| Result    | ⚠️       | Потребує runtime validation.    |

### Верифікація FRELSPEC

#### Колекції

| Положення | Верифіковано | Примітки                    |
| --------- | -------- | ------------------------ |
| Set       | ✅        | Підтримується через `Set`. |
| Map       | ✅        | Підтримується через `Map`. |
| Array     | ✅        | Arrays are supported.    |
| File      | ❌        | Not language-level.      |
| Stream    | ❌        | Not language-level.      |

#### Пам'ять

| Положення | Верифіковано | Примітки                           |
| --------- | -------- | ------------------------------- |
| Address   | ❌        | No address support.             |
| Pointer   | ❌        | No pointer support.             |
| Variable  | ✅        | Змінні підтримуються.        |
| Constant  | ⚠️       | `const` protects bindings only. |

#### Операції

| Provision   | Verified | Notes                            |
| ----------- | -------- | -------------------------------- |
| Instruction | ❌        | No defined instruction type.     |
| Procedure   | ❌        | Functions always return a value. |
| Function    | ✅        | Functions are supported.         |

#### Потоки

| Provision  | Verified | Notes                       |
| ---------- | -------- | --------------------------- |
| Process    | ❌        | Not language-level.         |
| Thread     | ⚠️        | Represented through agents. |
| Dispatcher | ❌        | Потребує host scheduling.   |


#### Композити

| Положення | Верифіковано | Примітки                                 |
| --------- | -------- | ------------------------------------- |
| Member    | ✅        | Object members are supported.         |
| Object    | ✅        | Об'єкти підтримуються.                |
| Field     | ✅        | Data properties can represent fields. |
| Method    | ✅        | Методи підтримуються.                |
| Property  | ❌        | Немає явної accessor map.             |
| Structure | ❌        | No structure support.                 |
| Class     | ✅        | Class syntax is supported.            |
| Interface | ❌        | No interface support.                 |
