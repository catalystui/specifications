<!-- Этот перевод был создан ChatGPT и должен быть проверен человеком-переводчиком. -->
<!-- Удалите эти строки в pull request после проверки перевода. -->

# Сведения о проверке

## Java

### Обзор

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Язык программирования Java был проверен по спецификациям FDEFSPEC (Rev. 1) и FRELSPEC (Rev. 1) по состоянию на 7 июля 2026 г.

#### Заявление о добросовестности

Мы добросовестно считаем, что язык программирования Java может разумно представлять большую часть понятий и положений, определенных в следующих спецификациях, и может использоваться для реализации систем, соответствующих этим спецификациям.

#### Предположения обзора

Этот обзор предполагает современную поддержку языка Java там, где отмечены возможности, зависящие от версии. Такие возможности, как вывод типов локальных переменных, records и доступ к внешней памяти, могут требовать более поздних версий Java.

### Предупреждения

* Java does not have native support for unsigned numeric types, which may require widening or alternative representations for certain provisions.
* Direct memory address and pointer-style behavior may require Java 22+ Foreign Function and Memory API support.
* Java does not have native property syntax, requiring getter and setter methods instead.

### Сбои

* Java does not provide CP1252 as a guaranteed standard charset, requiring implementation-specific support, additional libraries, or custom handling for full compliance.
* Java properties do not provide an explicit keyed member backed by a required Get/Set accessor map.

### Проверка FDEFSPEC

#### Числовые типы

| Положение | Проверено | Примечания                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | Нет 1-битного числового типа; требуется расширение.                         |
| Nibble    | ⚠️       | Нет 4-битного числового типа; требуется расширение.                         |
| Byte      | ⚠️       | Signed 8-bit only; widen for unsigned.           |
| Short     | ⚠️       | Signed 16-bit only; widen for unsigned.          |
| Int       | ⚠️       | Signed 32-bit; unsigned helpers require Java 8+. |
| Long      | ⚠️       | Signed 64-bit; unsigned helpers require Java 8+. |
| Float     | ✅        | 32-bit floating point is supported.              |
| Double    | ✅        | 64-bit floating point is supported.              |
| Boolean   | ✅        | Boolean type is supported.                       |

#### Кодирование текста

| Положение | Проверено | Примечания                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Поддерживается через `int` and `Character`. |
| ASCII     | ✅        | Гарантированная стандартная кодировка.             |
| CP1252    | ❌        | Не гарантируется через `StandardCharsets`.    |
| UTF-8     | ✅        | Гарантированная стандартная кодировка.             |
| UTF-16LE  | ✅        | Гарантированная стандартная кодировка.             |

#### Статус операции

| Положение | Проверено | Примечания                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Может быть представлен через a custom type.        |
| Context   | ✅        | Может быть представлен через a custom value.       |
| Operation | ✅        | Может быть представлен через a custom value.       |
| Detail    | ✅        | Может быть представлен через a custom value.       |
| Result    | ✅        | Может быть представлен через a custom return type. |

### Проверка FRELSPEC

#### Коллекции

| Положение | Проверено | Примечания                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Поддерживается через `Set`.       |
| Map       | ✅        | Поддерживается через `Map`.       |
| Array     | ✅        | Встроенные массивы поддерживаются.   |
| File      | ✅        | Поддерживается через file APIs.   |
| Stream    | ✅        | Поддерживается через stream APIs. |

#### Память

| Положение | Проверено | Примечания                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses require Java 22+ FFM.                         |
| Pointer   | ⚠️       | Pointer-like access requires Java 22+ FFM.                     |
| Variable  | ✅        | Declarations and `var` are supported; `var` requires Java 10+. |
| Constant  | ✅        | Поддерживается через `final`.                                     |

#### Операции

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Represented through bytecode and operations. |
| Procedure   | ✅        | Поддерживается через `void` methods.            |
| Function    | ✅        | Поддерживается через returning methods.         |

#### Потоки

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Поддерживается через application and `Process` APIs. |
| Thread     | ✅        | Поддерживается через `Thread`.                       |
| Dispatcher | ✅        | Поддерживается через `Executor` APIs.                |

#### Составные конструкции

| Положение | Проверено | Примечания                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Class members are supported.           |
| Object    | ✅        | Объекты поддерживаются.                 |
| Field     | ✅        | Поля поддерживаются.                  |
| Method    | ✅        | Методы поддерживаются.                 |
| Property  | ❌        | Нет явной карты аксессоров.              |
| Structure | ✅        | Поддерживается через records; Java 16+.   |
| Class     | ✅        | Классы поддерживаются.                 |
| Interface | ✅        | Интерфейсы поддерживаются.              |
