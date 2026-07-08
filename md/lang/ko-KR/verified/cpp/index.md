<!-- 이 번역은 ChatGPT가 생성한 것이며 인간 번역자의 검토가 필요합니다. -->
<!-- 번역이 확인된 후 pull request에서 이 줄들을 제거하십시오. -->

# 검증 세부 정보

## C++

### 개요

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C++ 프로그래밍 언어는 2026년 7월 7일 기준으로 FDEFSPEC(Rev. 1) 및 FRELSPEC(Rev. 1) 사양에 대해 검증되었습니다.

#### 선의의 진술

우리는 선의로, C++ 프로그래밍 언어가 다음 사양에 정의된 개념과 조항을 합리적으로 표현할 수 있으며 이러한 사양을 준수하는 시스템을 구현하는 데 사용될 수 있다고 믿습니다.

#### 검토 전제

이 검토는 버전 의존 기능이 표시된 곳에서 현대 표준 C++ 지원을 전제로 합니다. 정확한 폭의 integer 지원은 구현이 해당 `<cstdint>` 타입을 제공한다고 가정합니다.

이 검토는 C++를 저수준 표현, object modeling, memory control, generic programming, concurrent execution을 직접 지원하는 시스템 프로그래밍 언어로 취급합니다.

### 경고

* 정확한 폭의 integer type은 구현 지원에 따라 달라집니다.
* CP1252는 byte-for-byte로 표현할 수 있지만, 이름 있는 표준 codec은 제공되지 않습니다.
* UTF-16LE serialization에는 명시적인 byte-order 처리가 필요합니다.
* 일부 concurrency 및 character 기능은 현대 C++ 개정판이 필요합니다.

### 실패 사항

* 이 검증 중 알려진 FDEFSPEC 또는 FRELSPEC 실패 사항은 발견되지 않았습니다.

### FDEFSPEC 검증

#### 수치

| 항목 | 검증 | 비고                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | bit-field 또는 mask를 사용합니다.                    |
| Nibble    | ⚠️       | bit-field 또는 mask를 사용합니다.                    |
| Byte      | ✅        | `std::byte`를 통해 지원됩니다.              |
| Short     | ✅        | `int16_t` 및 `uint16_t`를 통해 지원됩니다. |
| Int       | ✅        | `int32_t` 및 `uint32_t`를 통해 지원됩니다. |
| Long      | ✅        | `int64_t` 및 `uint64_t`를 통해 지원됩니다. |
| Float     | ✅        | `float`를 통해 지원됩니다.                  |
| Double    | ✅        | `double`을 통해 지원됩니다.                 |
| Boolean   | ✅        | `bool`을 통해 지원됩니다.                   |

#### 텍스트 인코딩

| 항목 | 검증 | 비고                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | `char32_t`를 통해 지원됩니다.        |
| ASCII     | ✅        | byte 값으로 표현할 수 있습니다.        |
| CP1252    | ⚠️        | 명시적인 byte mapping이 필요합니다.      |
| UTF-8     | ✅        | `char8_t`를 통해 지원됩니다. C++20+. |
| UTF-16LE  | ⚠️        | byte-order 처리가 필요합니다.        |

#### 연산 상태

| 항목 | 검증 | 비고                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | enum으로 표현할 수 있습니다.           |
| Context   | ✅        | 값으로 표현할 수 있습니다.           |
| Operation | ✅        | 값으로 표현할 수 있습니다.           |
| Detail    | ✅        | 값으로 표현할 수 있습니다.           |
| Result    | ✅        | struct 또는 class로 표현할 수 있습니다. |

### FRELSPEC 검증

#### 컬렉션

| 항목 | 검증 | 비고                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | `std::set`을 통해 지원됩니다.              |
| Map       | ✅        | `std::map`을 통해 지원됩니다.              |
| Array     | ✅        | array 및 `std::array`를 통해 지원됩니다. |
| File      | ✅        | file stream을 통해 지원됩니다.            |
| Stream    | ✅        | iostream을 통해 지원됩니다.               |

#### 메모리

| 항목 | 검증 | 비고                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | address가 지원됩니다.                   |
| Pointer   | ✅        | pointer가 지원됩니다.                    |
| Variable  | ✅        | variable이 지원됩니다.                   |
| Constant  | ✅        | `const` 및 `constexpr`를 통해 지원됩니다. |

#### 연산

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | machine operation을 통해 표현됩니다. |
| Procedure   | ✅        | `void` function을 통해 지원됩니다.     |
| Function    | ✅        | returning function을 통해 지원됩니다.  |

#### 스레딩

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | hosted execution을 통해 지원됩니다.      |
| Thread     | ✅        | `std::thread`를 통해 지원됩니다. C++11+. |
| Dispatcher | ✅        | async 및 scheduler를 통해 지원됩니다.  |

#### 복합체

| 항목 | 검증 | 비고                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | class member가 지원됩니다.            |
| Object    | ✅        | object가 지원됩니다.                  |
| Field     | ✅        | field가 지원됩니다.                   |
| Method    | ✅        | method가 지원됩니다.                  |
| Property  | ✅        | Get/Set map을 표현할 수 있습니다.        |
| Structure | ✅        | structure가 native로 지원됩니다.      |
| Class     | ✅        | class가 native로 지원됩니다.         |
| Interface | ✅        | Can be represented by abstract classes. |
