<!-- Этот перевод был создан ChatGPT и должен быть проверен человеком-переводчиком. -->
<!-- Удалите эти строки в pull request после проверки перевода. -->

# FDEFSPEC

<br/>

> **Спецификация фундаментальных определений**<br/>
> Ревизия 1<br/>
> 23 марта 2026 г.<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Все права защищены.<br/>
> <br/>
> Представленные здесь определения и понятия описывают фундаментальные математические конструкции и могут быть свободно переизложены.

## Введение

The **Foundational Definitions Specification (FDEFSPEC)** establishes the core concepts and terminology that underpin the CatalystUI ecosystem. Its purpose is to provide a unified understanding of these concepts across documentation, specifications, implementations, and verification reviews, ensuring consistency, clarity, and alignment.

By defining key terms and relationships in a precise and stable form, FDEFSPEC provides a common reference point for higher-level specifications. This allows developers, reviewers, and implementers to reason from the same foundation when determining whether a language, service, framework, or system can be considered within spec.

> [!IMPORTANT]
>
> We express definitions using a derived form of [set theory](https://en.wikipedia.org/wiki/Set_theory) notation. This approach provides precise, unambiguous definitions while maintaining clarity and conciseness. We structure these definitions to support easy reference, clear interpretation, and a consistent conceptual hierarchy.

## Содержание

- [FDEFSPEC](#fdefspec)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Numerics](#numerics)
    - [Bit](#bit)
    - [Nibble](#nibble)
      - [Nibble()](#nibble-1)
    - [Byte](#byte)
      - [Byte()](#byte-1)
      - [SByte()](#sbyte)
    - [Short](#short)
      - [Short()](#short-1)
      - [UShort()](#ushort)
    - [Int](#int)
      - [Int()](#int-1)
      - [UInt()](#uint)
    - [Long](#long)
      - [Long()](#long-1)
      - [ULong()](#ulong)
    - [Single](#single)
      - [Single()](#single-1)
    - [Double](#double)
      - [Double()](#double-1)
    - [Boolean](#boolean)
      - [Boolean()](#boolean-1)
  - [Text Encoding](#text-encoding)
    - [Text Encoding](#text-encoding-1)
      - [Text Encoding()](#text-encoding-2)
    - [Codepoint](#codepoint)
      - [Codepoint()](#codepoint-1)
    - [ASCII Code Unit](#ascii-code-unit)
      - [ASCII Code Unit()](#ascii-code-unit-1)
      - [ASCII()](#ascii)
    - [CP1252 Code Unit](#cp1252-code-unit)
      - [CP1252 Code Unit()](#cp1252-code-unit-1)
      - [CP1252()](#cp1252)
    - [UTF-8 Code Unit](#utf-8-code-unit)
      - [UTF-8 Code Unit()](#utf-8-code-unit-1)
      - [UTF-8()](#utf-8)
    - [UTF-16LE Code Unit](#utf-16le-code-unit)
      - [UTF-16LE Code Unit()](#utf-16le-code-unit-1)
      - [UTF-16LE()](#utf-16le)
  - [Operation Status](#operation-status)
    - [Status Code](#status-code)
      - [Status Code()](#status-code-1)
      - [Status Code Level()](#status-code-level)
      - [Status Code Definition()](#status-code-definition)
        - [Success](#success)
        - [Warning](#warning)
        - [Error](#error)
        - [Fatal](#fatal)
    - [Context Code](#context-code)
      - [Context Code()](#context-code-1)
    - [Operation Code](#operation-code)
      - [Operation Code()](#operation-code-1)
    - [Detail Code](#detail-code)
      - [Detail Code()](#detail-code-1)
    - [Result](#result)
      - [Result()](#result-1)

## Числовые типы

### Bit

Бит — это любое значение $b \in \{0,1\}$.

### Nibble

Ниббл — это любой кортеж $(b_0,\dots,b_3)$ такой, что для всех $i \in \{0,\dots,3\}$ выполняется $b_i \in \mathrm{Bit}$.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

Байт — это любой кортеж $(b_0,\dots,b_7)$ такой, что для всех $i \in \{0,\dots,7\}$ выполняется $b_i \in \mathrm{Bit}$.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

Short — это любой кортеж $(b_0,\dots,b_{15})$ такой, что для всех $i \in \{0,\dots,15\}$ выполняется $b_i \in \mathrm{Bit}$.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

Целое число — это любой кортеж $(b_0,\dots,b_{31})$ такой, что для всех $i \in \{0,\dots,31\}$ выполняется $b_i \in \mathrm{Bit}$.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

Long — это любой кортеж $(b_0,\dots,b_{63})$ такой, что для всех $i \in \{0,\dots,63\}$ выполняется $b_i \in \mathrm{Bit}$.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

Single — это любой кортеж $(b_0,\dots,b_{31})$ такой, что для всех $i \in \{0,\dots,31\}$ выполняется $b_i \in \mathrm{Bit}$.

#### Single()

Следующее определение соответствует стандарту IEEE 754 для представления чисел с плавающей точкой одинарной точности. Оно определяет, как 32-битная двоичная последовательность интерпретируется как число с плавающей точкой, включая особые случаи нуля, бесконечности и NaN (Not a Number).

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Let $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

Double — это любой кортеж $(b_0,\dots,b_{63})$ такой, что для всех $i \in \{0,\dots,63\}$ выполняется $b_i \in \mathrm{Bit}$.

#### Double()

Следующее определение соответствует стандарту IEEE 754 для представления чисел с плавающей точкой двойной точности. Оно определяет, как 64-битная двоичная последовательность интерпретируется как число с плавающей точкой, включая особые случаи нуля, бесконечности и NaN (Not a Number).

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Let $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

Булево значение — это любое $b \in \{0,1\}$.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## Кодирование текста

### Кодирование текста

Кодирование текста определяется как следующее множество:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Кодирование текста()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Кодовая точка Unicode — это любое $e \in \mathbb{Z}$ такое, что $0 \leq e \leq 0x10FFFF$.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

An ASCII code unit is any $(b_0,\dots,b_6)$ such that for all $i \in \{0,\dots,6\}$, $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

По причинам производительности и совместимости единицу кода ASCII часто представляют как байт, добавляя ведущий нулевой бит. В таких случаях единица кода ASCII представляется так:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

В противном случае:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

В рамках этой теоремы оба определения являются допустимыми представлениями единицы кода ASCII. Для согласованности мы будем использовать первое определение при представлении единиц кода ASCII как байтов, а второе — при представлении их как 7-битных последовательностей.

#### ASCII()

ASCII — это конечный кортеж с нулевым завершением $(u_0, \dots, u_k, u_{k+1})$ такой, что:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is an ASCII code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

Такая последовательность называется нуль-терминированной.

### CP1252 Code Unit

A CP1252 code unit is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 — это конечный кортеж с нулевым завершением $(u_0, \dots, u_k, u_{k+1})$ такой, что:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a CP1252 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

Такая последовательность называется нуль-терминированной.

### UTF-8 Code Unit

A UTF-8 code unit is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 — это конечный кортеж с нулевым завершением $(u_0, \dots, u_k, u_{k+1})$ такой, что:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-8 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

Такая последовательность называется нуль-терминированной.

### UTF-16LE Code Unit

A UTF-16LE code unit is any $(b_0,\dots,b_{15})$ such that for all $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE — это конечный кортеж с нулевым завершением $(u_0, \dots, u_k, u_{k+1})$ такой, что:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-16LE code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

Такая последовательность называется нуль-терминированной.

## Статус операции

### Status Code

A status code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

Уровень кода состояния определяется как следующее множество:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Status Code()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Status Code Level()

The set of status code values is the range $[0, 255]$, which is partitioned into four levels:

> Let $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Status Code Definition()

Все коды состояния имеют явные определения. Любой код состояния, не включенный в следующий список, зарезервирован для будущего использования, и его значение не определено. Уровень кода состояния определяется выражением $\mathrm{Status\ Code\ Level}(s)$.

В следующем списке входное значение $s$ для удобства чтения представлено в шестнадцатеричном виде. Каждый определенный код состояния указывает соответствующий уровень, категорию, подкатегорию, описание и, где применимо, детали.

Этот список может расширяться по мере определения новых кодов состояния. Любой новый код состояния не должен конфликтовать с существующими кодами и должен иметь ясно документированное значение.

Для передачи информации, не представленной определенным кодом состояния, следует использовать код контекста, код операции или код детализации.

##### Success

| Код | Уровень | Категория | Описание | Детали |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | Операция успешно завершена. | |
| `0x01` | SUCCESS | NOOP | Операция успешно завершена без выполнения действия. | |

##### Warning

| Код | Уровень | Категория | Описание | Детали |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | Операция завершена, но результат может быть неожиданным или нежелательным. | |
| `0x41` | WARNING | PARTIAL | Операция завершена, но только частично. Вывод может быть неполным. | |
| `0x42` | WARNING | DEPRECATED | The operation completed, but it used a deprecated feature or behavior. The operation may no longer work in the future. | |

##### Error

| Код | Уровень | Категория | Описание | Детали |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | Операция завершилась ошибкой из-за восстанавливаемой ошибки. | |
| `0x81` | ERROR | INVALID_ARGUMENT | Операция завершилась ошибкой. Аргумент был недопустимым или вне диапазона. | The index of the invalid argument, starting at 0 from left to right in the function's signature. |
| `0x82` | ERROR | INVALID_STATE | Операция завершилась ошибкой. Система находится в несогласованном, поврежденном или ином недопустимом состоянии. | |
| `0x83` | ERROR | MALFORMED_INPUT | Операция завершилась ошибкой. Требуемый ввод был неправильно сформирован или содержал недопустимые данные. | |
| `0x84` | ERROR | ACCESS_DENIED | Операция завершилась ошибкой, потому что требуемый ресурс отказал в доступе. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | Операция завершилась ошибкой, потому что запрошенная возможность или поведение еще не реализованы. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | Операция завершилась ошибкой, потому что целевая система или конфигурация не поддерживает запрошенную возможность. | |
| `0x87` | ERROR | TIMEOUT | Операция завершилась ошибкой, потому что до завершения истек требуемый тайм-аут. | |
| `0x88` | ERROR | NOT_FOUND | Операция завершилась ошибкой, потому что требуемый ресурс не существует. | |
| `0x89` | ERROR | INTERRUPTED | Операция завершилась ошибкой, потому что внешнее событие прервало ее. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | The operation failed because a required dependency failed. | The dependency's `STATUS_CODE` value. Callers are encouraged (but not required) to identify the failing dependency via the `OP_CODE` field. |
| `0x90` | ERROR | BUFFER_OVERFLOW | Операция завершилась ошибкой. Буфер был слишком мал для размещения требуемых данных. | |
| `0x91` | ERROR | ALLOCATION_FAILED | Операция завершилась ошибкой. Запрос выделения памяти не был успешным. | |
| `0xA0` | ERROR | IO_ERROR | Операция завершилась ошибкой. Во время операции произошла ошибка ввода-вывода. | |

##### Fatal

| Код | Уровень | Категория | Описание | Детали |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | Операция завершилась ошибкой из-за невосстанавливаемой ошибки. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | The operation failed because the system violated a fundamental invariant, indicating a critical logic error or data corruption. | |

### Context Code

A context code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Context Code()

Значение кода контекста представляет дополнительную контекстную информацию о завершенной операции, определяемую связанной операцией; оно должно быть равно нулю, когда уровень кода состояния равен $\mathrm{Success}$, и иначе определяется реализацией.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Operation Code

An operation code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Operation Code()

Значение кода операции представляет операцию, связанную с результатом. Его смысл определяется соответствующей операцией и ее документацией. Неопределенные значения считаются неизвестными.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Detail Code

A detail code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Detail Code()

Значение кода детализации представляет дополнительную информацию о завершенной операции; его смысл определяется связанным кодом состояния, контекста или операции (именно в этом порядке), а иначе считается неизвестным.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Result

> [!TIP]
>
> A result value may be represented as a 32-bit integer. In big-endian byte order, the value appears as `0xSSCCOODD`, where `SS`, `CC`, `OO`, and `DD` correspond to the status code, context code, operation code, and detail code, respectively. In little-endian byte order, the same value appears as `0xDDOOCCSS`. Either byte order may be used, provided it is applied consistently and documented.

A result is any $(b_0,\dots,b_{31})$ such that for all $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

Результат разбивается на четыре упорядоченных байта:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

где $s$, $c$, $o$ и $d$ являются компонентами результата.

#### Result()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
