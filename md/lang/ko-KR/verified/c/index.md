<!-- 이 번역은 ChatGPT가 생성한 것이며 인간 번역자의 검토가 필요합니다. -->
<!-- 번역이 확인된 후 pull request에서 이 줄들을 제거하십시오. -->

# 검증 세부 정보

## C

### 개요

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C 프로그래밍 언어는 2026년 7월 7일 기준으로 FDEFSPEC(Rev. 1) 및 FRELSPEC(Rev. 1) 사양에 대해 검증되었습니다.

#### 선의의 진술

우리는 선의로, C 프로그래밍 언어가 다음 사양에 정의된 개념과 조항을 합리적으로 표현할 수 있으며 이러한 사양을 준수하는 시스템을 구현하는 데 사용될 수 있다고 믿습니다.

#### 검토 진술

C는 기초 데이터 표현, 메모리 접근, 파일, 스트림, procedure, function, structure, 그리고 직접적인 시스템 지향 구현에 대해 강력한 저수준 지원을 제공합니다.

C는 여러 객체 지향 복합 구조를 네이티브로 제공하지 않지만, 이러한 제한은 특정 FRELSPEC composite 조항에 국한되며 아래에 문서화되어 있습니다. 이러한 실패 사항은 C가 전체적으로 within spec으로 간주되는 것을 막지는 않지만, C를 CatalystUI 호환 구현에 사용할 때 이해되어야 합니다.

#### 검토 전제

이 검토는 버전 의존 기능이 표시된 곳에서 현대 표준 C 지원을 전제로 합니다. 정확한 폭의 integer 지원은 구현이 해당 `<stdint.h>` 타입을 제공한다고 가정합니다.

이 검토는 C를 저수준 표현 언어로 취급합니다. 이름 있는 표준 codec이 제공되지 않는 경우 byte-exact encoding은 byte array, lookup table, 명시적 parsing logic을 통해 직접 표현될 수 있습니다.

### 경고

* 정확한 폭의 integer type은 구현 지원에 따라 달라집니다.
* CP1252는 byte-for-byte로 표현할 수 있지만, 이름 있는 표준 codec은 제공되지 않습니다.
* UTF-16LE serialization에는 명시적인 byte-order 처리가 필요합니다.
* 일부 C 구현에서는 standard thread가 생략될 수 있습니다.
* 객체 지향 패턴은 수동으로 모방할 수 있지만, 네이티브 언어 구조는 아닙니다.

### 실패 사항

* C는 native method member를 제공하지 않습니다.
* C는 native property를 제공하지 않습니다.
* C는 native class를 제공하지 않습니다.
* C는 native interface를 제공하지 않습니다.

### FDEFSPEC 검증

#### 수치

| 항목 | 검증 | 비고                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | bit-field 또는 mask를 사용합니다.                    |
| Nibble    | ⚠️       | bit-field 또는 mask를 사용합니다.                    |
| Byte      | ✅        | `unsigned char`를 통해 지원됩니다.          |
| Short     | ✅        | `int16_t` 및 `uint16_t`를 통해 지원됩니다. |
| Int       | ✅        | `int32_t` 및 `uint32_t`를 통해 지원됩니다. |
| Long      | ✅        | `int64_t` 및 `uint64_t`를 통해 지원됩니다. |
| Float     | ✅        | `float`를 통해 지원됩니다.                  |
| Double    | ✅        | `double`을 통해 지원됩니다.                 |
| Boolean   | ✅        | `bool`을 통해 지원됩니다. C99+.             |

#### 텍스트 인코딩

| 항목 | 검증 | 비고                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | `char32_t`를 통해 지원됩니다. C11+.     |
| ASCII     | ✅        | byte 값으로 표현할 수 있습니다.           |
| CP1252    | ⚠️        | 명시적인 byte mapping이 필요합니다.         |
| UTF-8     | ✅        | UTF-8 literal을 통해 지원됩니다. C11+. |
| UTF-16LE  | ⚠️        | byte-order 처리가 필요합니다.           |

#### 연산 상태

| 항목 | 검증 | 비고                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | enum으로 표현할 수 있습니다.  |
| Context   | ✅        | 값으로 표현할 수 있습니다.  |
| Operation | ✅        | 값으로 표현할 수 있습니다.  |
| Detail    | ✅        | 값으로 표현할 수 있습니다.  |
| Result    | ✅        | struct로 표현할 수 있습니다. |

### FRELSPEC 검증

#### 컬렉션

| 항목 | 검증 | 비고                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | struct로 표현할 수 있습니다. |
| Map       | ✅        | struct로 표현할 수 있습니다. |
| Array     | ✅        | native array가 지원됩니다.   |
| File      | ✅        | file API를 통해 지원됩니다.   |
| Stream    | ✅        | stream API를 통해 지원됩니다. |

#### 메모리

| 항목 | 검증 | 비고                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | address가 지원됩니다.   |
| Pointer   | ✅        | pointer가 지원됩니다.    |
| Variable  | ✅        | variable이 지원됩니다.   |
| Constant  | ✅        | `const`를 통해 지원됩니다. |

#### 연산

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | machine operation을 통해 표현됩니다. |
| Procedure   | ✅        | `void` function을 통해 지원됩니다.     |
| Function    | ✅        | returning function을 통해 지원됩니다.  |

#### 스레딩

| Provision  | Verified | Notes                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | hosted environment를 통해 지원됩니다. |
| Thread     | ⚠️        | `<threads.h>`를 통해 지원됩니다. C11+. |
| Dispatcher | ✅        | 직접 표현할 수 있습니다.           |

#### 복합체

| 항목 | 검증 | 비고                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | struct member가 지원됩니다.            |
| Object    | ✅        | struct는 addressable composite를 형성할 수 있습니다. |
| Field     | ✅        | struct field가 지원됩니다.             |
| Method    | ❌        | native method member가 없습니다.                |
| Property  | ❌        | 명시적인 Get/Set accessor map이 없습니다.        |
| Structure | ✅        | structure가 native로 지원됩니다.       |
| Class     | ❌        | native class construct가 없습니다.               |
| Interface | ❌        | native interface construct가 없습니다.           |
