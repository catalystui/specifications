<!-- 이 번역은 ChatGPT가 생성한 것이며 인간 번역자의 검토가 필요합니다. -->
<!-- 번역이 확인된 후 pull request에서 이 줄들을 제거하십시오. -->

# 검증 세부 정보

## Java

### 개요

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Java 프로그래밍 언어는 2026년 7월 7일 기준으로 FDEFSPEC(Rev. 1) 및 FRELSPEC(Rev. 1) 사양에 대해 검증되었습니다.

#### 선의의 진술

우리는 선의로, Java 프로그래밍 언어가 다음 사양에 정의된 개념과 조항의 상당 부분을 합리적으로 표현할 수 있으며 이러한 사양을 준수하는 시스템을 구현하는 데 사용될 수 있다고 믿습니다.

#### 검토 전제

이 검토는 버전 의존 기능이 표시된 곳에서 현대 Java 언어 지원을 전제로 합니다. 지역 변수 추론, records, foreign memory access 같은 기능은 더 이후의 Java 버전이 필요할 수 있습니다.

### 경고

* Java는 unsigned numeric type에 대한 native 지원이 없으므로 일부 조항에서는 widening 또는 대체 표현이 필요할 수 있습니다.
* 직접 memory address 및 pointer-style 동작에는 Java 22+ Foreign Function and Memory API 지원이 필요할 수 있습니다.
* Java에는 native property syntax가 없으므로 대신 getter와 setter method가 필요합니다.

### 실패 사항

* Java는 CP1252를 보장된 standard charset으로 제공하지 않으므로 완전한 준수를 위해 implementation-specific support, 추가 library 또는 custom handling이 필요합니다.
* Java property는 필요한 Get/Set accessor map으로 뒷받침되는 explicit keyed member를 제공하지 않습니다.

### FDEFSPEC 검증

#### 수치

| 항목 | 검증 | 비고                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | 1-bit numeric이 없습니다. widen이 필요합니다.                         |
| Nibble    | ⚠️       | 4-bit numeric이 없습니다. widen이 필요합니다.                         |
| Byte      | ⚠️       | signed 8-bit만 있습니다. unsigned에는 widen이 필요합니다.           |
| Short     | ⚠️       | signed 16-bit만 있습니다. unsigned에는 widen이 필요합니다.          |
| Int       | ⚠️       | signed 32-bit입니다. unsigned helper에는 Java 8+가 필요합니다. |
| Long      | ⚠️       | signed 64-bit입니다. unsigned helper에는 Java 8+가 필요합니다. |
| Float     | ✅        | 32-bit floating point is supported.              |
| Double    | ✅        | 64-bit floating point is supported.              |
| Boolean   | ✅        | boolean type이 지원됩니다.                       |

#### 텍스트 인코딩

| 항목 | 검증 | 비고                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Supported through `int` and `Character`. |
| ASCII     | ✅        | 보장된 standard charset입니다.             |
| CP1252    | ❌        | `StandardCharsets`로 보장되지 않습니다.    |
| UTF-8     | ✅        | 보장된 standard charset입니다.             |
| UTF-16LE  | ✅        | 보장된 standard charset입니다.             |

#### 연산 상태

| 항목 | 검증 | 비고                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | custom type으로 표현할 수 있습니다.        |
| Context   | ✅        | custom value로 표현할 수 있습니다.       |
| Operation | ✅        | custom value로 표현할 수 있습니다.       |
| Detail    | ✅        | custom value로 표현할 수 있습니다.       |
| Result    | ✅        | custom return type으로 표현할 수 있습니다. |

### FRELSPEC 검증

#### 컬렉션

| 항목 | 검증 | 비고                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | `Set`을 통해 지원됩니다.       |
| Map       | ✅        | `Map`을 통해 지원됩니다.       |
| Array     | ✅        | native array가 지원됩니다.   |
| File      | ✅        | file API를 통해 지원됩니다.   |
| Stream    | ✅        | stream API를 통해 지원됩니다. |

#### 메모리

| 항목 | 검증 | 비고                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | direct address에는 Java 22+ FFM이 필요합니다.                         |
| Pointer   | ⚠️       | pointer-like access에는 Java 22+ FFM이 필요합니다.                     |
| Variable  | ✅        | declaration 및 `var`가 지원됩니다. `var`에는 Java 10+가 필요합니다. |
| Constant  | ✅        | `final`을 통해 지원됩니다.                                     |

#### 연산

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | bytecode 및 operation을 통해 표현됩니다. |
| Procedure   | ✅        | `void` method를 통해 지원됩니다.            |
| Function    | ✅        | returning method를 통해 지원됩니다.         |

#### 스레딩

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | application 및 `Process` API를 통해 지원됩니다. |
| Thread     | ✅        | `Thread`를 통해 지원됩니다.                       |
| Dispatcher | ✅        | `Executor` API를 통해 지원됩니다.                |

#### 복합체

| 항목 | 검증 | 비고                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | class member가 지원됩니다.           |
| Object    | ✅        | object가 지원됩니다.                 |
| Field     | ✅        | field가 지원됩니다.                  |
| Method    | ✅        | method가 지원됩니다.                 |
| Property  | ❌        | 명시적인 accessor map이 없습니다.              |
| Structure | ✅        | record를 통해 지원됩니다. Java 16+.   |
| Class     | ✅        | class가 지원됩니다.                 |
| Interface | ✅        | interface가 지원됩니다.              |
