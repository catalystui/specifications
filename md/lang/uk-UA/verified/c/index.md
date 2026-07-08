<!-- Цей переклад було створено ChatGPT, і його має перевірити людина-перекладач. -->
<!-- Видаліть ці рядки в pull request після перевірки перекладу. -->

# Деталі верифікації

## C

### Огляд

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Мову програмування C верифіковано відповідно до специфікацій FDEFSPEC (Rev. 1) і FRELSPEC (Rev. 1) станом на 7 липня 2026 р.

#### Заява доброї віри

Ми добросовісно вважаємо, що мова програмування C може розумно представляти поняття й положення, визначені в наведених нижче специфікаціях, і що її можна використовувати для реалізації систем, які відповідають цим специфікаціям.

#### Review Statement

C provides strong low-level support for foundational data representation, memory access, files, streams, procedures, functions, structures, and direct system-oriented implementation.

While C does not natively provide several object-oriented composite constructs, these limitations are isolated to specific FRELSPEC composite provisions and are documented below. These failures do not prevent C from being considered within spec overall, but they should be understood when using C for CatalystUI-compatible implementations.

#### Припущення розгляду

This review assumes modern standard C support where version-dependent features are noted. Exact-width integer support assumes the corresponding `<stdint.h>` types are provided by the implementation.

This review treats C as a low-level representation language. Byte-exact encodings may be represented directly through byte arrays, lookup tables, and explicit parsing logic when no named standard codec is provided.

### Попередження

* Exact-width integer types depend on implementation support.
* CP1252 can be represented byte-for-byte, but no named standard codec is provided.
* UTF-16LE serialization requires explicit byte-order handling.
* Standard threads may be omitted by some C implementations.
* Object-oriented patterns may be manually emulated, but are not native language constructs.

### Невідповідності

* C does not provide native method members.
* C does not provide native properties.
* C does not provide native classes.
* C does not provide native interfaces.

### Верифікація FDEFSPEC

#### Числові типи

| Положення | Верифіковано | Примітки                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | Підтримується через `unsigned char`.          |
| Short     | ✅        | Підтримується через `int16_t` and `uint16_t`. |
| Int       | ✅        | Підтримується через `int32_t` and `uint32_t`. |
| Long      | ✅        | Підтримується через `int64_t` and `uint64_t`. |
| Float     | ✅        | Підтримується через `float`.                  |
| Double    | ✅        | Підтримується через `double`.                 |
| Boolean   | ✅        | Підтримується через `bool`; C99+.             |

#### Кодування тексту

| Положення | Верифіковано | Примітки                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | Підтримується через `char32_t`; C11+.     |
| ASCII     | ✅        | Може бути представлено як byte values.           |
| CP1252    | ⚠️        | Потребує explicit byte mapping.         |
| UTF-8     | ✅        | Підтримується через UTF-8 literals; C11+. |
| UTF-16LE  | ⚠️        | Потребує byte-order handling.           |

#### Статус операції

| Положення | Верифіковано | Примітки                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Може бути представлено через an enum.  |
| Context   | ✅        | Може бути представлено через a value.  |
| Operation | ✅        | Може бути представлено через a value.  |
| Detail    | ✅        | Може бути представлено через a value.  |
| Result    | ✅        | Може бути представлено через a struct. |

### Верифікація FRELSPEC

#### Колекції

| Положення | Верифіковано | Примітки                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Може бути представлено через structs. |
| Map       | ✅        | Може бути представлено через structs. |
| Array     | ✅        | Нативні масиви підтримуються.   |
| File      | ✅        | Підтримується через file APIs.   |
| Stream    | ✅        | Підтримується через stream APIs. |

#### Пам'ять

| Положення | Верифіковано | Примітки                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Addresses are supported.   |
| Pointer   | ✅        | Pointers are supported.    |
| Variable  | ✅        | Змінні підтримуються.   |
| Constant  | ✅        | Підтримується через `const`. |

#### Операції

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | Підтримується через `void` functions.     |
| Function    | ✅        | Підтримується через returning functions.  |

#### Потоки

| Provision  | Verified | Notes                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Підтримується через hosted environments. |
| Thread     | ⚠️        | Підтримується через `<threads.h>`; C11+. |
| Dispatcher | ✅        | Can be represented directly.           |

#### Композити

| Положення | Верифіковано | Примітки                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Struct members are supported.            |
| Object    | ✅        | Structs can form addressable composites. |
| Field     | ✅        | Struct fields are supported.             |
| Method    | ❌        | No native method members.                |
| Property  | ❌        | No explicit Get/Set accessor map.        |
| Structure | ✅        | Структури підтримуються нативно.       |
| Class     | ❌        | No native class construct.               |
| Interface | ❌        | No native interface construct.           |
