<!-- 이 번역은 ChatGPT가 생성한 것이며 인간 번역자의 검토가 필요합니다. -->
<!-- 번역이 확인된 후 pull request에서 이 줄들을 제거하십시오. -->

# FDEFSPEC

<br/>

> **기초 정의 사양**<br/>
> 개정 1<br/>
> 2026년 3월 23일<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/>
> <br/>
> 여기에 제시된 정의와 개념은 기초적인 수학적 구성 요소를 설명하며 자유롭게 다시 표현될 수 있습니다.

## 소개

**Foundational Definitions Specification (FDEFSPEC)**은 CatalystUI 생태계를 뒷받침하는 핵심 개념과 용어를 확립합니다. 그 목적은 문서, 사양, 구현, 검증 검토 전반에서 이러한 개념에 대한 통일된 이해를 제공하여 일관성, 명확성, 정렬성을 보장하는 것입니다.

핵심 용어와 관계를 정확하고 안정적인 형식으로 정의함으로써 FDEFSPEC은 더 높은 수준의 사양을 위한 공통 기준점을 제공합니다. 이를 통해 개발자, 검토자, 구현자는 언어, 서비스, 프레임워크 또는 시스템이 within spec으로 간주될 수 있는지 판단할 때 같은 기반에서 추론할 수 있습니다.

> [!IMPORTANT]
>
> 우리는 [집합론](https://en.wikipedia.org/wiki/Set_theory) 표기법에서 파생된 형식을 사용하여 정의를 표현합니다. 이 방식은 명확성과 간결성을 유지하면서 정확하고 모호하지 않은 정의를 제공합니다. 이러한 정의는 쉬운 참조, 명확한 해석, 일관된 개념 계층을 지원하도록 구성됩니다.

## 목차

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

## 수치

### Bit

bit는 $b \in \{0,1\}$인 임의의 값입니다.

### Nibble

nibble은 모든 $i \in \{0,\dots,3\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_3)$입니다.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

byte는 모든 $i \in \{0,\dots,7\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_7)$입니다.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

short는 모든 $i \in \{0,\dots,15\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_{15})$입니다.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

integer는 모든 $i \in \{0,\dots,31\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_{31})$입니다.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

long은 모든 $i \in \{0,\dots,63\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_{63})$입니다.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

single은 모든 $i \in \{0,\dots,31\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_{31})$입니다.

#### Single()

다음 정의는 단정밀도 부동소수점 표현에 대한 IEEE 754 표준을 따릅니다. 이 정의는 0, 무한대, NaN(Not a Number)의 특수한 경우를 포함하여 32비트 이진 시퀀스가 부동소수점 수로 해석되는 방식을 정의합니다.

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Let $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

double은 모든 $i \in \{0,\dots,63\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_{63})$입니다.

#### Double()

다음 정의는 배정밀도 부동소수점 표현에 대한 IEEE 754 표준을 따릅니다. 이 정의는 0, 무한대, NaN(Not a Number)의 특수한 경우를 포함하여 64비트 이진 시퀀스가 부동소수점 수로 해석되는 방식을 정의합니다.

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Let $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

boolean은 $b \in \{0,1\}$인 임의의 값입니다.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{여기서 } b \in \mathrm{Bit}$

## 텍스트 인코딩

### 텍스트 인코딩

텍스트 인코딩은 다음 집합으로 정의됩니다.

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### 텍스트 인코딩()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Unicode codepoint는 $0 \leq e \leq 0x10FFFF$를 만족하는 임의의 $e \in \mathbb{Z}$입니다.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

ASCII code unit은 모든 $i \in \{0,\dots,6\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_6)$입니다.

#### ASCII Code Unit()

성능과 호환성 때문에 앞에 0 bit를 붙여 ASCII code unit을 byte로 표현하는 것은 일반적입니다. 이런 경우 ASCII code unit은 다음과 같이 표현됩니다.

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

그렇지 않은 경우:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

이 정리에서는 두 정의 모두 ASCII code unit의 허용 가능한 표현입니다. 일관성을 위해 ASCII code unit을 byte로 표현할 때는 첫 번째 정의를 사용하고, 7-bit sequence로 표현할 때는 두 번째 정의를 사용합니다.

#### ASCII()

ASCII는 다음 조건을 만족하는 null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$입니다.

- $\forall i \in \{0,\dots,k+1\}$에 대해, $u_i$는 ASCII code unit입니다.
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

이 sequence는 null-terminated라고 합니다.

### CP1252 Code Unit

CP1252 code unit은 모든 $i \in \{0,\dots,7\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_7)$입니다.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252는 다음 조건을 만족하는 null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$입니다.

- $\forall i \in \{0,\dots,k+1\}$에 대해, $u_i$는 CP1252 code unit입니다.
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

이 sequence는 null-terminated라고 합니다.

### UTF-8 Code Unit

UTF-8 code unit은 모든 $i \in \{0,\dots,7\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_7)$입니다.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8은 다음 조건을 만족하는 null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$입니다.

- $\forall i \in \{0,\dots,k+1\}$에 대해, $u_i$는 UTF-8 code unit입니다.
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

이 sequence는 null-terminated라고 합니다.

### UTF-16LE Code Unit

UTF-16LE code unit은 모든 $i \in \{0,\dots,15\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_{15})$입니다.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE는 다음 조건을 만족하는 null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$입니다.

- $\forall i \in \{0,\dots,k+1\}$에 대해, $u_i$는 UTF-16LE code unit입니다.
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

이 sequence는 null-terminated라고 합니다.

## 연산 상태

### Status Code

status code는 모든 $i \in \{0,\dots,7\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_7)$입니다.

status code level은 다음 집합으로 정의됩니다.

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Status Code()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Status Code Level()

status code 값의 집합은 $[0, 255]$ 범위이며, 네 level로 나뉩니다.

> $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$라고 합니다.
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Status Code Definition()

모든 status code에는 명시적인 정의가 있습니다. 다음 목록에 포함되지 않은 status code는 향후 사용을 위해 예약되어 있으며 그 의미는 정의되지 않았습니다. status code의 level은 $\mathrm{Status\ Code\ Level}(s)$에 의해 결정됩니다.

다음 목록에서 입력 $s$는 가독성을 위해 16진수 값으로 표시됩니다. 정의된 각 status code는 해당되는 level, category, sub-category, description, detail을 지정합니다.

새로운 status code가 정의되면 이 목록은 확장될 수 있습니다. 새로 정의되는 status code는 기존 code와 충돌해서는 안 되며 명확히 문서화된 의미를 가져야 합니다.

정의된 status code로 표현되지 않는 정보를 전달하려면 context code, operation code 또는 detail code를 사용해야 합니다.

##### Success

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | operation이 성공적으로 완료되었습니다. | |
| `0x01` | SUCCESS | NOOP | operation이 아무 작업도 수행하지 않고 성공적으로 완료되었습니다. | |

##### Warning

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | operation은 완료되었지만 결과가 예상 밖이거나 바람직하지 않을 수 있습니다. | |
| `0x41` | WARNING | PARTIAL | operation은 완료되었지만 부분적으로만 완료되었습니다. output이 불완전할 수 있습니다. | |
| `0x42` | WARNING | DEPRECATED | operation은 완료되었지만 deprecated feature 또는 behavior를 사용했습니다. 이 operation은 향후 더 이상 작동하지 않을 수 있습니다. | |

##### Error

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | operation이 복구 가능한 error로 인해 실패했습니다. | |
| `0x81` | ERROR | INVALID_ARGUMENT | operation이 실패했습니다. argument가 잘못되었거나 범위를 벗어났습니다. | function signature에서 왼쪽에서 오른쪽으로 0부터 시작하는 잘못된 argument의 index입니다. |
| `0x82` | ERROR | INVALID_STATE | operation이 실패했습니다. system이 일관되지 않거나, 손상되었거나, 그 밖의 잘못된 상태입니다. | |
| `0x83` | ERROR | MALFORMED_INPUT | operation이 실패했습니다. 필요한 input이 malformed 상태이거나 invalid data를 포함했습니다. | |
| `0x84` | ERROR | ACCESS_DENIED | 필요한 resource가 access를 거부했기 때문에 operation이 실패했습니다. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | 요청된 feature 또는 behavior가 아직 구현되지 않았기 때문에 operation이 실패했습니다. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | 대상 system 또는 configuration이 요청된 feature를 지원하지 않기 때문에 operation이 실패했습니다. | |
| `0x87` | ERROR | TIMEOUT | 완료 전에 필요한 timeout이 발생했기 때문에 operation이 실패했습니다. | |
| `0x88` | ERROR | NOT_FOUND | 필요한 resource가 존재하지 않기 때문에 operation이 실패했습니다. | |
| `0x89` | ERROR | INTERRUPTED | external event가 중단했기 때문에 operation이 실패했습니다. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | 필요한 dependency가 실패했기 때문에 operation이 실패했습니다. | dependency의 `STATUS_CODE` 값입니다. caller는 `OP_CODE` field를 통해 실패한 dependency를 식별하는 것이 권장되지만 필수는 아닙니다. |
| `0x90` | ERROR | BUFFER_OVERFLOW | operation이 실패했습니다. buffer가 필요한 data를 담기에 너무 작았습니다. | |
| `0x91` | ERROR | ALLOCATION_FAILED | operation이 실패했습니다. memory allocation request가 성공하지 못했습니다. | |
| `0xA0` | ERROR | IO_ERROR | operation이 실패했습니다. operation 중 I/O error가 발생했습니다. | |

##### Fatal

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | operation이 복구할 수 없는 error로 인해 실패했습니다. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | system이 fundamental invariant를 위반했기 때문에 operation이 실패했습니다. 이는 critical logic error 또는 data corruption을 나타냅니다. | |

### Context Code

context code는 모든 $i \in \{0,\dots,7\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_7)$입니다.

#### Context Code()

context code 값은 연결된 operation이 정의하는 완료된 operation에 대한 추가 context information을 나타냅니다. status code level이 $\mathrm{Success}$인 경우 0이어야 하며, 그 외의 경우에는 implementation-defined입니다.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Operation Code

operation code는 모든 $i \in \{0,\dots,7\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_7)$입니다.

#### Operation Code()

operation code 값은 result와 연결된 operation을 나타냅니다. 그 의미는 해당 operation과 그 문서에 의해 정의됩니다. 정의되지 않은 값은 unknown으로 간주됩니다.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Detail Code

detail code는 모든 $i \in \{0,\dots,7\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_7)$입니다.

#### Detail Code()

detail code 값은 완료된 operation에 대한 추가 정보를 나타냅니다. 그 의미는 연결된 status, context 또는 operation code의 순서에 따라 정의되며, 그렇지 않으면 unknown입니다.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Result

> [!TIP]
>
> result 값은 32-bit integer로 표현될 수 있습니다. big-endian byte order에서는 값이 `0xSSCCOODD`로 나타나며, 여기서 `SS`, `CC`, `OO`, `DD`는 각각 status code, context code, operation code, detail code에 대응합니다. little-endian byte order에서는 같은 값이 `0xDDOOCCSS`로 나타납니다. 일관되게 적용되고 문서화된다면 어느 byte order든 사용할 수 있습니다.

result는 모든 $i \in \{0,\dots,31\}$에 대해 $b_i \in \mathrm{Bit}$인 임의의 $(b_0,\dots,b_{31})$입니다.

result는 네 개의 ordered byte로 나뉩니다.

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

여기서 $s$, $c$, $o$, $d$는 result의 구성 요소입니다.

#### Result()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
