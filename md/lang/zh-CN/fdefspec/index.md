<!-- 此翻译由 ChatGPT 生成，应由人工译者审核。 -->

# 在翻译经验证后，请在拉取请求中删除这些行。

# FDEFSPEC

<br/>

> **基础定义规范**<br/>
> 修订版 1<br/>
> 2026 年 3 月 23 日<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> 保留所有权利。<br/>
> <br/>
> 此处提出的定义和概念描述的是基础数学构造，可被自由地重新表述。

## 引言

The **Foundational Definitions Specification (FDEFSPEC)** establishes the core concepts and terminology that underpin the CatalystUI ecosystem. Its purpose is to provide a unified understanding of these concepts across documentation, specifications, implementations, and verification reviews, ensuring consistency, clarity, and alignment.

By defining key terms and relationships in a precise and stable form, FDEFSPEC provides a common reference point for higher-level specifications. This allows developers, reviewers, and implementers to reason from the same foundation when determining whether a language, service, framework, or system can be considered within spec.

> [!IMPORTANT]
>
> 我们使用一种派生自 [集合论](https://en.wikipedia.org/wiki/Set_theory) 的记号形式来表达定义。这种方法在保持清晰与简洁的同时，提供了精确且无歧义的定义。我们对这些定义进行结构化组织，以支持便捷引用、清晰解释以及一致的概念层级。

## 目录

- [FDEFSPEC](#fdefspec)
  - [引言](#introduction)
  - [目录](#table-of-contents)
  - [数值](#numerics)
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
  - [文本编码](#text-encoding)
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
  - [操作状态](#operation-status)
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

## 数值

### Bit

位（bit）是任意满足 $b \in \{0,1\}$ 的值。

### Nibble

半字节（nibble）是任意 $(b_0,\dots,b_3)$，其中对所有 $i \in \{0,\dots,3\}$，都有 $b_i \in \mathrm{Bit}$。

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

字节（byte）是任意 $(b_0,\dots,b_7)$，其中对所有 $i \in \{0,\dots,7\}$，都有 $b_i \in \mathrm{Bit}$。

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

短整数（short）是任意 $(b_0,\dots,b_{15})$，其中对所有 $i \in \{0,\dots,15\}$，都有 $b_i \in \mathrm{Bit}$。

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

整数（int）是任意 $(b_0,\dots,b_{31})$，其中对所有 $i \in \{0,\dots,31\}$，都有 $b_i \in \mathrm{Bit}$。

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

长整数（long）是任意 $(b_0,\dots,b_{63})$，其中对所有 $i \in \{0,\dots,63\}$，都有 $b_i \in \mathrm{Bit}$。

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

单精度数（single）是任意 $(b_0,\dots,b_{31})$，其中对所有 $i \in \{0,\dots,31\}$，都有 $b_i \in \mathrm{Bit}$。

#### Single()

下列定义符合 IEEE 754 单精度浮点表示标准。它定义了如何将 32 位二进制序列解释为浮点数，包括零、无穷大和 NaN（非数）等特殊情况。

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Let $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

双精度数（double）是任意 $(b_0,\dots,b_{63})$，其中对所有 $i \in \{0,\dots,63\}$，都有 $b_i \in \mathrm{Bit}$。

#### Double()

下列定义符合 IEEE 754 双精度浮点表示标准。它定义了如何将 64 位二进制序列解释为浮点数，包括零、无穷大和 NaN（非数）等特殊情况。

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Let $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

布尔值（boolean）是任意满足 $b \in \{0,1\}$ 的值。

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## 文本编码

### 文本编码

文本编码定义为如下集合：

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### 文本编码()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Unicode 码点是任意满足 $e \in \mathbb{Z}$ 且 $0 \leq e \leq 0x10FFFF$ 的值。

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII 码单元

ASCII 码单元是任意 $(b_0,\dots,b_6)$，其中对所有 $i \in \{0,\dots,6\}$，都有 $b_i \in \mathrm{Bit}$。

#### ASCII 码单元()

出于性能与兼容性原因，通常会在前面附加一个 0 位，将 ASCII 码单元表示为一个字节。在这种情况下，ASCII 码单元表示如下：

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

否则：

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

在本定理中，这两种定义都可作为 ASCII 码单元的可接受表示。为保持一致，当将 ASCII 码单元表示为字节时，我们使用第一种定义；当将其表示为 7 位序列时，我们使用第二种定义。

#### ASCII()

ASCII 是一个以空值终止的有限元组 $(u_0, \dots, u_k, u_{k+1})$，满足：

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is an ASCII code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

该序列称为以空值终止。

### CP1252 码单元

CP1252 码单元是任意 $(b_0,\dots,b_7)$，其中对所有 $i \in \{0,\dots,7\}$，都有 $b_i \in \mathrm{Bit}$。

#### CP1252 码单元()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 是一个以空值终止的有限元组 $(u_0, \dots, u_k, u_{k+1})$，满足：

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a CP1252 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

该序列称为以空值终止。

### UTF-8 码单元

UTF-8 码单元是任意 $(b_0,\dots,b_7)$，其中对所有 $i \in \{0,\dots,7\}$，都有 $b_i \in \mathrm{Bit}$。

#### UTF-8 码单元()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 是一个以空值终止的有限元组 $(u_0, \dots, u_k, u_{k+1})$，满足：

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-8 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

该序列称为以空值终止。

### UTF-16LE 码单元

UTF-16LE 码单元是任意 $(b_0,\dots,b_{15})$，其中对所有 $i \in \{0,\dots,15\}$，都有 $b_i \in \mathrm{Bit}$。

#### UTF-16LE 码单元()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE 是一个以空值终止的有限元组 $(u_0, \dots, u_k, u_{k+1})$，满足：

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-16LE code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

该序列称为以空值终止。

## 操作状态

### 状态码

状态码是任意 $(b_0,\dots,b_7)$，其中对所有 $i \in \{0,\dots,7\}$，都有 $b_i \in \mathrm{Bit}$。

状态码级别定义为如下集合：

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### 状态码()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### 状态码 Level()

状态码取值集合为区间 $[0, 255]$，其被划分为四个级别：

> Let $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### 状态码 Definition()

所有状态码都有显式定义。未包含在下列列表中的任何状态码都保留供未来使用，其含义未定义。状态码的级别由 $\mathrm{Status\ Code\ Level}(s)$ 决定。

在下列列表中，为便于阅读，输入 $s$ 以十六进制值表示。每个已定义状态码都指定了其对应的级别、类别、子类别、描述以及（如适用）细节。

随着新状态码的定义，此列表可以继续扩展。任何新定义的状态码都不得与现有代码冲突，并且必须具有清晰记录的含义。

若要传达已定义状态码未表示的信息，应使用上下文码、操作码或细节码。

##### 成功

| 代码 | 级别 | 类别 | 描述 | 细节 |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | The operation completed successfully. | |
| `0x01` | SUCCESS | NOOP | The operation completed successfully without performing any action. | |

##### 警告

| 代码 | 级别 | 类别 | 描述 | 细节 |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | The operation completed, but the result may be unexpected or undesirable. | |
| `0x41` | WARNING | PARTIAL | The operation completed, but only partially. The output may be incomplete. | |
| `0x42` | WARNING | DEPRECATED | The operation completed, but it used a deprecated feature or behavior. The operation may no longer work in the future. | |

##### 错误

| 代码 | 级别 | 类别 | 描述 | 细节 |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | The operation failed due to a recoverable error. | |
| `0x81` | ERROR | INVALID_ARGUMENT | The operation failed. An argument was invalid or out of range. | The index of the invalid argument, starting at 0 from left to right in the function's signature. |
| `0x82` | ERROR | INVALID_STATE | The operation failed. The system is in an inconsistent, corrupted, or otherwise invalid state. | |
| `0x83` | ERROR | MALFORMED_INPUT | The operation failed. A required input was malformed or contained invalid data. | |
| `0x84` | ERROR | ACCESS_DENIED | The operation failed because a required resource denied access. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | The operation failed because the requested feature or behavior is not yet implemented. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | The operation failed because the target system or configuration does not support the requested feature. | |
| `0x87` | ERROR | TIMEOUT | The operation failed because a required timeout occurred before completion. | |
| `0x88` | ERROR | NOT_FOUND | The operation failed because a required resource does not exist. | |
| `0x89` | ERROR | INTERRUPTED | The operation failed because an external event interrupted it. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | The operation failed because a required dependency failed. | The dependency's `STATUS_CODE` value. Callers are encouraged (but not required) to identify the failing dependency via the `OP_CODE` field. |
| `0x90` | ERROR | BUFFER_OVERFLOW | The operation failed. A buffer was too small to hold the required data. | |
| `0x91` | ERROR | ALLOCATION_FAILED | The operation failed. A memory allocation request was unsuccessful. | |
| `0xA0` | ERROR | IO_ERROR | The operation failed. An I/O error occurred during the operation. | |

##### 致命

| 代码 | 级别 | 类别 | 描述 | 细节 |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | The operation failed due to an unrecoverable error. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | The operation failed because the system violated a fundamental invariant, indicating a critical logic error or data corruption. | |

### 上下文码

上下文码是任意 $(b_0,\dots,b_7)$，其中对所有 $i \in \{0,\dots,7\}$，都有 $b_i \in \mathrm{Bit}$。

#### 上下文码()

上下文码值表示与已完成操作相关的额外上下文信息，其含义由关联操作定义；当状态码级别为 $\mathrm{Success}$ 时，它必须为零，否则由实现定义。

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### 操作码

操作码是任意 $(b_0,\dots,b_7)$，其中对所有 $i \in \{0,\dots,7\}$，都有 $b_i \in \mathrm{Bit}$。

#### 操作码()

操作码值表示与某个结果相关联的操作。其含义由相应操作及其文档定义。未定义的值被视为未知。

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### 细节码

细节码是任意 $(b_0,\dots,b_7)$，其中对所有 $i \in \{0,\dots,7\}$，都有 $b_i \in \mathrm{Bit}$。

#### 细节码()

细节码值表示关于已完成操作的额外信息；其含义依次由关联的状态码、上下文码或操作码定义，否则视为未知。

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### 结果

> [!TIP]
>
> 结果值可以表示为一个 32 位整数。在大端字节序中，该值显示为 `0xSSCCOODD`，其中 `SS`、`CC`、`OO` 和 `DD` 分别对应状态码、上下文码、操作码和细节码。在小端字节序中，同一值显示为 `0xDDOOCCSS`。只要使用一致并有文档说明，任意一种字节序都可以采用。

结果（result）是任意 $(b_0,\dots,b_{31})$，其中对所有 $i \in \{0,\dots,31\}$，都有 $b_i \in \mathrm{Bit}$。

一个结果被划分为四个有序字节：

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

其中 $s$、$c$、$o$ 和 $d$ 是该结果的组成部分。

#### 结果()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
