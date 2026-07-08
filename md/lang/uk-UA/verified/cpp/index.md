<!-- Цей переклад було створено ChatGPT, і його має перевірити людина-перекладач. -->
<!-- Видаліть ці рядки в pull request після перевірки перекладу. -->

# Деталі верифікації

## C++

### Огляд

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Мову програмування C++ верифіковано відповідно до специфікацій FDEFSPEC (Rev. 1) і FRELSPEC (Rev. 1) станом на 7 липня 2026 р.

#### Заява доброї віри

Ми добросовісно вважаємо, що мова програмування C++ може розумно представляти поняття й положення, визначені в наведених нижче специфікаціях, і що її можна використовувати для реалізації систем, які відповідають цим специфікаціям.

#### Припущення розгляду

This review assumes modern standard C++ support where version-dependent features are noted. Exact-width integer support assumes the corresponding `<cstdint>` types are provided by the implementation.

This review treats C++ as a systems programming language with direct support for low-level representation, object modeling, memory control, generic programming, and concurrent execution.

### Попередження

* Exact-width integer types depend on implementation support.
* CP1252 can be represented byte-for-byte, but no named standard codec is provided.
* UTF-16LE serialization requires explicit byte-order handling.
* Some concurrency and character features require modern C++ revisions.

### Невідповідності

* Під час цієї верифікації не було знайдено відомих невідповідностей FDEFSPEC або FRELSPEC.

### Верифікація FDEFSPEC

#### Числові типи

| Положення | Верифіковано | Примітки                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | Підтримується через `std::byte`.              |
| Short     | ✅        | Підтримується через `int16_t` and `uint16_t`. |
| Int       | ✅        | Підтримується через `int32_t` and `uint32_t`. |
| Long      | ✅        | Підтримується через `int64_t` and `uint64_t`. |
| Float     | ✅        | Підтримується через `float`.                  |
| Double    | ✅        | Підтримується через `double`.                 |
| Boolean   | ✅        | Підтримується через `bool`.                   |

#### Кодування тексту

| Положення | Верифіковано | Примітки                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Підтримується через `char32_t`.        |
| ASCII     | ✅        | Може бути представлено як byte values.        |
| CP1252    | ⚠️        | Потребує explicit byte mapping.      |
| UTF-8     | ✅        | Підтримується через `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Потребує byte-order handling.        |

#### Статус операції

| Положення | Верифіковано | Примітки                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Може бути представлено через an enum.           |
| Context   | ✅        | Може бути представлено через a value.           |
| Operation | ✅        | Може бути представлено через a value.           |
| Detail    | ✅        | Може бути представлено через a value.           |
| Result    | ✅        | Може бути представлено через a struct or class. |

### Верифікація FRELSPEC

#### Колекції

| Положення | Верифіковано | Примітки                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Підтримується через `std::set`.              |
| Map       | ✅        | Підтримується через `std::map`.              |
| Array     | ✅        | Підтримується через arrays and `std::array`. |
| File      | ✅        | Підтримується через file streams.            |
| Stream    | ✅        | Підтримується через iostreams.               |

#### Пам'ять

| Положення | Верифіковано | Примітки                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Addresses are supported.                   |
| Pointer   | ✅        | Pointers are supported.                    |
| Variable  | ✅        | Змінні підтримуються.                   |
| Constant  | ✅        | Підтримується через `const` and `constexpr`. |

#### Операції

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | Підтримується через `void` functions.     |
| Function    | ✅        | Підтримується через returning functions.  |

#### Потоки

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Підтримується через hosted execution.      |
| Thread     | ✅        | Підтримується через `std::thread`; C++11+. |
| Dispatcher | ✅        | Підтримується через async and schedulers.  |

#### Композити

| Положення | Верифіковано | Примітки                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Class members are supported.            |
| Object    | ✅        | Об'єкти підтримуються.                  |
| Field     | ✅        | Поля підтримуються.                   |
| Method    | ✅        | Методи підтримуються.                  |
| Property  | ✅        | Get/Set maps can be represented.        |
| Structure | ✅        | Структури підтримуються нативно.      |
| Class     | ✅        | Classes are natively supported.         |
| Interface | ✅        | Може бути представлено через abstract classes. |
