<!-- Этот перевод был создан ChatGPT и должен быть проверен человеком-переводчиком. -->
<!-- Удалите эти строки в pull request после проверки перевода. -->

# Сведения о проверке

## C++

### Обзор

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Язык программирования C++ был проверен по спецификациям FDEFSPEC (Rev. 1) и FRELSPEC (Rev. 1) по состоянию на 7 июля 2026 г.

#### Заявление о добросовестности

Мы добросовестно считаем, что язык программирования C++ может разумно представлять понятия и положения, определенные в следующих спецификациях, и может использоваться для реализации систем, соответствующих этим спецификациям.

#### Предположения обзора

This review assumes modern standard C++ support where version-dependent features are noted. Exact-width integer support assumes the corresponding `<cstdint>` types are provided by the implementation.

This review treats C++ as a systems programming language with direct support for low-level representation, object modeling, memory control, generic programming, and concurrent execution.

### Предупреждения

* Exact-width integer types depend on implementation support.
* CP1252 can be represented byte-for-byte, but no named standard codec is provided.
* UTF-16LE serialization requires explicit byte-order handling.
* Some concurrency and character features require modern C++ revisions.

### Сбои

* Во время этой проверки не было обнаружено известных несоответствий FDEFSPEC или FRELSPEC.

### Проверка FDEFSPEC

#### Числовые типы

| Положение | Проверено | Примечания                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | Поддерживается через `std::byte`.              |
| Short     | ✅        | Поддерживается через `int16_t` and `uint16_t`. |
| Int       | ✅        | Поддерживается через `int32_t` and `uint32_t`. |
| Long      | ✅        | Поддерживается через `int64_t` and `uint64_t`. |
| Float     | ✅        | Поддерживается через `float`.                  |
| Double    | ✅        | Поддерживается через `double`.                 |
| Boolean   | ✅        | Поддерживается через `bool`.                   |

#### Кодирование текста

| Положение | Проверено | Примечания                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Поддерживается через `char32_t`.        |
| ASCII     | ✅        | Представим как byte values.        |
| CP1252    | ⚠️        | Требует explicit byte mapping.      |
| UTF-8     | ✅        | Поддерживается через `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Требует byte-order handling.        |

#### Статус операции

| Положение | Проверено | Примечания                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Может быть представлен через an enum.           |
| Context   | ✅        | Может быть представлен через a value.           |
| Operation | ✅        | Может быть представлен через a value.           |
| Detail    | ✅        | Может быть представлен через a value.           |
| Result    | ✅        | Может быть представлен через a struct or class. |

### Проверка FRELSPEC

#### Коллекции

| Положение | Проверено | Примечания                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Поддерживается через `std::set`.              |
| Map       | ✅        | Поддерживается через `std::map`.              |
| Array     | ✅        | Поддерживается через arrays and `std::array`. |
| File      | ✅        | Поддерживается через file streams.            |
| Stream    | ✅        | Поддерживается через iostreams.               |

#### Память

| Положение | Проверено | Примечания                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Addresses are supported.                   |
| Pointer   | ✅        | Pointers are supported.                    |
| Variable  | ✅        | Переменные поддерживаются.                   |
| Constant  | ✅        | Поддерживается через `const` and `constexpr`. |

#### Операции

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | Поддерживается через `void` functions.     |
| Function    | ✅        | Поддерживается через returning functions.  |

#### Потоки

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Поддерживается через hosted execution.      |
| Thread     | ✅        | Поддерживается через `std::thread`; C++11+. |
| Dispatcher | ✅        | Поддерживается через async and schedulers.  |

#### Составные конструкции

| Положение | Проверено | Примечания                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Class members are supported.            |
| Object    | ✅        | Объекты поддерживаются.                  |
| Field     | ✅        | Поля поддерживаются.                   |
| Method    | ✅        | Методы поддерживаются.                  |
| Property  | ✅        | Get/Set maps can be represented.        |
| Structure | ✅        | Структуры поддерживаются на уровне языка.      |
| Class     | ✅        | Classes are natively supported.         |
| Interface | ✅        | Может быть представлен через abstract classes. |
