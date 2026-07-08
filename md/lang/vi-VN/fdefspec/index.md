<!-- Bản dịch này được tạo bởi ChatGPT và nên được một người dịch xem xét lại. -->
<!-- Hãy xóa các dòng này trong pull request sau khi bản dịch đã được xác minh. -->

# FDEFSPEC

<br/>

> **Đặc tả định nghĩa nền tảng**<br/>
> Bản sửa đổi 1<br/>
> Ngày 23 tháng 3 năm 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Bảo lưu mọi quyền.<br/>
> <br/>
> Các định nghĩa và khái niệm được trình bày ở đây mô tả những cấu trúc toán học nền tảng và có thể được diễn đạt lại một cách tự do.

## Giới thiệu

**Foundational Definitions Specification (FDEFSPEC)** thiết lập các khái niệm cốt lõi và thuật ngữ làm nền cho hệ sinh thái CatalystUI. Mục đích của nó là cung cấp cách hiểu thống nhất về các khái niệm này trong tài liệu, đặc tả, implementation và verification review, bảo đảm tính nhất quán, rõ ràng và đồng bộ.

Bằng cách định nghĩa các thuật ngữ và quan hệ chính ở dạng chính xác và ổn định, FDEFSPEC cung cấp một điểm tham chiếu chung cho các đặc tả cấp cao hơn. Điều này cho phép developer, reviewer và implementer suy luận từ cùng một nền tảng khi xác định liệu một ngôn ngữ, service, framework hoặc system có thể được xem là within spec hay không.

> [!IMPORTANT]
>
> Chúng tôi diễn đạt định nghĩa bằng một dạng dẫn xuất của ký hiệu [lý thuyết tập hợp](https://en.wikipedia.org/wiki/Set_theory). Cách tiếp cận này cung cấp các định nghĩa chính xác, không mơ hồ trong khi vẫn giữ sự rõ ràng và ngắn gọn. Chúng tôi cấu trúc các định nghĩa này để hỗ trợ việc tra cứu dễ dàng, diễn giải rõ ràng và một hệ phân cấp khái niệm nhất quán.

## Mục lục

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

## Số học

### Bit

Bit là bất kỳ $b \in \{0,1\}$ nào.

### Nibble

Nibble là bất kỳ $(b_0,\dots,b_3)$ nào sao cho với mọi $i \in \{0,\dots,3\}$, $b_i \in \mathrm{Bit}$.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

Byte là bất kỳ $(b_0,\dots,b_7)$ nào sao cho với mọi $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

Short là bất kỳ $(b_0,\dots,b_{15})$ nào sao cho với mọi $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

Integer là bất kỳ $(b_0,\dots,b_{31})$ nào sao cho với mọi $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

Long là bất kỳ $(b_0,\dots,b_{63})$ nào sao cho với mọi $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

Single là bất kỳ $(b_0,\dots,b_{31})$ nào sao cho với mọi $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Single()

Định nghĩa sau tuân theo tiêu chuẩn IEEE 754 cho biểu diễn số chấm động độ chính xác đơn. Nó định nghĩa cách một chuỗi nhị phân 32 bit được diễn giải như một số chấm động, bao gồm các trường hợp đặc biệt cho zero, infinity và NaN (Not a Number).

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Let $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

Double là bất kỳ $(b_0,\dots,b_{63})$ nào sao cho với mọi $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Double()

Định nghĩa sau tuân theo tiêu chuẩn IEEE 754 cho biểu diễn số chấm động độ chính xác kép. Nó định nghĩa cách một chuỗi nhị phân 64 bit được diễn giải như một số chấm động, bao gồm các trường hợp đặc biệt cho zero, infinity và NaN (Not a Number).

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Let $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

Boolean là bất kỳ $b \in \{0,1\}$ nào.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## Mã hóa văn bản

### Mã hóa văn bản

Text encoding được định nghĩa là tập hợp sau:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Mã hóa văn bản()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Unicode codepoint là bất kỳ $e \in \mathbb{Z}$ nào sao cho $0 \leq e \leq 0x10FFFF$.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

An ASCII code unit is any $(b_0,\dots,b_6)$ such that for all $i \in \{0,\dots,6\}$, $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

It is common to represent an ASCII code unit as a byte by appending a leading zero bit, for performance and compatibility reasons. In such cases, the ASCII code unit is represented as:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Ngược lại:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

In the case of this theorem, both definitions are acceptable representations of an ASCII code unit. For consistency, we will use the first definition when representing ASCII code units as bytes, and the second definition when representing them as 7-bit sequences.

#### ASCII()

ASCII is a null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ such that:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is an ASCII code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

Chuỗi này được gọi là null-terminated.

### CP1252 Code Unit

A CP1252 code unit is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 is a null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ such that:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a CP1252 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

Chuỗi này được gọi là null-terminated.

### UTF-8 Code Unit

A UTF-8 code unit is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 is a null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ such that:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-8 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

Chuỗi này được gọi là null-terminated.

### UTF-16LE Code Unit

A UTF-16LE code unit is any $(b_0,\dots,b_{15})$ such that for all $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE is a null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ such that:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-16LE code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

Chuỗi này được gọi là null-terminated.

## Trạng thái thao tác

### Status Code

A status code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

A status code level is defined as the following set:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Status Code()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Status Code Level()

The set of status code values is the range $[0, 255]$, which is partitioned into four levels:

> Let $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Status Code Definition()

All status codes have explicit definitions. Any status code not included in the following list is reserved for future use, and its meaning is undefined. The level of a status code is determined by $\mathrm{Status\ Code\ Level}(s)$.

In the following list, the input $s$ is represented as a hexadecimal value for readability. Each defined status code specifies its corresponding level, category, sub-category, description, and detail, where applicable.

This list may be extended as new status codes are defined. Any newly defined status code must not conflict with existing codes and must have a clearly documented meaning.

To convey information not represented by a defined status code, the context code, operation code, or detail code should be used.

##### Success

| Mã | Cấp độ | Danh mục | Mô tả | Chi tiết |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | Operation hoàn tất thành công. | |
| `0x01` | SUCCESS | NOOP | Operation hoàn tất thành công mà không thực hiện action nào. | |

##### Warning

| Mã | Cấp độ | Danh mục | Mô tả | Chi tiết |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | Operation đã hoàn tất, nhưng result có thể không mong đợi hoặc không mong muốn. | |
| `0x41` | WARNING | PARTIAL | Operation đã hoàn tất, nhưng chỉ một phần. Output có thể không đầy đủ. | |
| `0x42` | WARNING | DEPRECATED | The operation completed, but it used a deprecated feature or behavior. The operation may no longer work in the future. | |

##### Error

| Mã | Cấp độ | Danh mục | Mô tả | Chi tiết |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | Operation thất bại do lỗi có thể khôi phục. | |
| `0x81` | ERROR | INVALID_ARGUMENT | Operation thất bại. An argument was invalid or out of range. | The index of the invalid argument, starting at 0 from left to right in the function's signature. |
| `0x82` | ERROR | INVALID_STATE | Operation thất bại. The system is in an inconsistent, corrupted, or otherwise invalid state. | |
| `0x83` | ERROR | MALFORMED_INPUT | Operation thất bại. A required input was malformed or contained invalid data. | |
| `0x84` | ERROR | ACCESS_DENIED | The operation failed because a required resource denied access. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | The operation failed because the requested feature or behavior is not yet implemented. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | The operation failed because the target system or configuration does not support the requested feature. | |
| `0x87` | ERROR | TIMEOUT | The operation failed because a required timeout occurred before completion. | |
| `0x88` | ERROR | NOT_FOUND | The operation failed because a required resource does not exist. | |
| `0x89` | ERROR | INTERRUPTED | The operation failed because an external event interrupted it. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | The operation failed because a required dependency failed. | The dependency's `STATUS_CODE` value. Callers are encouraged (but not required) to identify the failing dependency via the `OP_CODE` field. |
| `0x90` | ERROR | BUFFER_OVERFLOW | Operation thất bại. A buffer was too small to hold the required data. | |
| `0x91` | ERROR | ALLOCATION_FAILED | Operation thất bại. A memory allocation request was unsuccessful. | |
| `0xA0` | ERROR | IO_ERROR | Operation thất bại. An I/O error occurred during the operation. | |

##### Fatal

| Mã | Cấp độ | Danh mục | Mô tả | Chi tiết |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | Operation thất bại do lỗi không thể khôi phục. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | The operation failed because the system violated a fundamental invariant, indicating a critical logic error or data corruption. | |

### Context Code

A context code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Context Code()

A context code value represents additional contextual information about a completed operation, as defined by the associated operation; it must be zero when the status code level is $\mathrm{Success}$, and is otherwise implementation-defined.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Operation Code

An operation code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Operation Code()

An operation code value represents the operation associated with a result. Its meaning is defined by the corresponding operation and its documentation. Undefined values are considered unknown.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Detail Code

A detail code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Detail Code()

A detail code value represents additional information about a completed operation; its meaning is defined by the associated status, context, or operation code (in that order), and is otherwise unknown.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Result

> [!TIP]
>
> A result value may be represented as a 32-bit integer. In big-endian byte order, the value appears as `0xSSCCOODD`, where `SS`, `CC`, `OO`, and `DD` correspond to the status code, context code, operation code, and detail code, respectively. In little-endian byte order, the same value appears as `0xDDOOCCSS`. Either byte order may be used, provided it is applied consistently and documented.

A result is any $(b_0,\dots,b_{31})$ such that for all $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

A result is partitioned into four ordered bytes:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

where $s$, $c$, $o$, and $d$ are the components of the result.

#### Result()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
