<!-- Цей переклад було створено ChatGPT, і його має перевірити людина-перекладач. -->
<!-- Видаліть ці рядки в pull request після перевірки перекладу. -->

# Деталі верифікації

## Java

### Огляд

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Мову програмування Java верифіковано відповідно до специфікацій FDEFSPEC (Rev. 1) і FRELSPEC (Rev. 1) станом на 7 липня 2026 р.

#### Заява доброї віри

Ми добросовісно вважаємо, що мова програмування Java може розумно представляти значну частину понять і положень, визначених у наведених нижче специфікаціях, і що її можна використовувати для реалізації систем, які відповідають цим специфікаціям.

#### Припущення розгляду

This review assumes modern Java language support where version-dependent features are noted. Features such as local variable inference, records, and foreign memory access may require later Java versions.

### Попередження

* Java does not have native support for unsigned numeric types, which may require widening or alternative representations for certain provisions.
* Direct memory address and pointer-style behavior may require Java 22+ Foreign Function and Memory API support.
* Java does not have native property syntax, requiring getter and setter methods instead.

### Невідповідності

* Java does not provide CP1252 as a guaranteed standard charset, requiring implementation-specific support, additional libraries, or custom handling for full compliance.
* Java properties do not provide an explicit keyed member backed by a required Get/Set accessor map.

### Верифікація FDEFSPEC

#### Числові типи

| Положення | Верифіковано | Примітки                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | Немає 1-бітового числового типу; розширюйте.                         |
| Nibble    | ⚠️       | Немає 4-бітового числового типу; розширюйте.                         |
| Byte      | ⚠️       | Signed 8-bit only; widen for unsigned.           |
| Short     | ⚠️       | Signed 16-bit only; widen for unsigned.          |
| Int       | ⚠️       | Signed 32-bit; unsigned helpers require Java 8+. |
| Long      | ⚠️       | Signed 64-bit; unsigned helpers require Java 8+. |
| Float     | ✅        | 32-bit floating point is supported.              |
| Double    | ✅        | 64-bit floating point is supported.              |
| Boolean   | ✅        | Boolean type is supported.                       |

#### Кодування тексту

| Положення | Верифіковано | Примітки                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Підтримується через `int` and `Character`. |
| ASCII     | ✅        | Гарантований стандартний набір символів.             |
| CP1252    | ❌        | Не гарантується `StandardCharsets`.    |
| UTF-8     | ✅        | Гарантований стандартний набір символів.             |
| UTF-16LE  | ✅        | Гарантований стандартний набір символів.             |

#### Статус операції

| Положення | Верифіковано | Примітки                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Може бути представлено через a custom type.        |
| Context   | ✅        | Може бути представлено через a custom value.       |
| Operation | ✅        | Може бути представлено через a custom value.       |
| Detail    | ✅        | Може бути представлено через a custom value.       |
| Result    | ✅        | Може бути представлено через a custom return type. |

### Верифікація FRELSPEC

#### Колекції

| Положення | Верифіковано | Примітки                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Підтримується через `Set`.       |
| Map       | ✅        | Підтримується через `Map`.       |
| Array     | ✅        | Нативні масиви підтримуються.   |
| File      | ✅        | Підтримується через file APIs.   |
| Stream    | ✅        | Підтримується через stream APIs. |

#### Пам'ять

| Положення | Верифіковано | Примітки                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses require Java 22+ FFM.                         |
| Pointer   | ⚠️       | Pointer-like access requires Java 22+ FFM.                     |
| Variable  | ✅        | Declarations and `var` are supported; `var` requires Java 10+. |
| Constant  | ✅        | Підтримується через `final`.                                     |

#### Операції

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Represented through bytecode and operations. |
| Procedure   | ✅        | Підтримується через `void` methods.            |
| Function    | ✅        | Підтримується через returning methods.         |

#### Потоки

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Підтримується через application and `Process` APIs. |
| Thread     | ✅        | Підтримується через `Thread`.                       |
| Dispatcher | ✅        | Підтримується через `Executor` APIs.                |

#### Композити

| Положення | Верифіковано | Примітки                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Class members are supported.           |
| Object    | ✅        | Об'єкти підтримуються.                 |
| Field     | ✅        | Поля підтримуються.                  |
| Method    | ✅        | Методи підтримуються.                 |
| Property  | ❌        | Немає явної accessor map.              |
| Structure | ✅        | Підтримується через records; Java 16+.   |
| Class     | ✅        | Класи підтримуються.                 |
| Interface | ✅        | Інтерфейси підтримуються.              |
