<!-- 이 번역은 ChatGPT가 생성한 것이며 인간 번역자의 검토가 필요합니다. -->
<!-- 번역이 확인된 후 pull request에서 이 줄들을 제거하십시오. -->

# 검증 세부 정보

## C#

### 개요

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C# 프로그래밍 언어는 2026년 7월 7일 기준으로 FDEFSPEC(Rev. 1) 및 FRELSPEC(Rev. 1) 사양에 대해 검증되었습니다.

#### 선의의 진술

우리는 선의로, C# 프로그래밍 언어가 다음 사양에 정의된 개념과 조항을 합리적으로 표현할 수 있으며 이러한 사양을 준수하는 시스템을 구현하는 데 사용될 수 있다고 믿습니다.

#### 검토 전제

이 검토는 버전 의존 기능이 표시된 곳에서 현대 C# 및 .NET 지원을 전제로 합니다.

### 경고

* CP1252 지원은 공식 .NET code pages provider를 통해 사용할 수 있지만, 대상 runtime에 따라 provider 등록 또는 추가 package가 필요할 수 있습니다.
* unsafe pointer 동작에는 명시적인 unsafe 권한 부여가 필요할 수 있습니다.

### 실패 사항

* 이 검증 중 알려진 FDEFSPEC 또는 FRELSPEC 실패 사항은 발견되지 않았습니다.

### FDEFSPEC 검증

#### 수치

| 항목 | 검증 | 비고                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | 1-bit numeric이 없습니다. widen이 필요합니다.                |
| Nibble    | ⚠️       | 4-bit numeric이 없습니다. widen이 필요합니다.                |
| Byte      | ✅        | `byte` 및 `sbyte`를 통해 지원됩니다.   |
| Short     | ✅        | `short` 및 `ushort`를 통해 지원됩니다. |
| Int       | ✅        | `int` 및 `uint`를 통해 지원됩니다.     |
| Long      | ✅        | `long` 및 `ulong`을 통해 지원됩니다.   |
| Float     | ✅        | `float`를 통해 지원됩니다.              |
| Double    | ✅        | `double`을 통해 지원됩니다.             |
| Boolean   | ✅        | `bool`을 통해 지원됩니다.               |

#### 텍스트 인코딩

| 항목 | 검증 | 비고                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | numeric 및 `Rune`을 통해 지원됩니다. |
| ASCII     | ✅        | `Encoding.ASCII`를 통해 지원됩니다.    |
| CP1252    | ⚠️       | code pages provider가 필요합니다.          |
| UTF-8     | ✅        | `Encoding.UTF8`을 통해 지원됩니다.     |
| UTF-16LE  | ✅        | `Encoding.Unicode`를 통해 지원됩니다.  |

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

| 항목 | 검증 | 비고                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | `HashSet<T>`를 통해 지원됩니다.              |
| Map       | ✅        | `Dictionary<TKey,TValue>`를 통해 지원됩니다. |
| Array     | ✅        | native array가 지원됩니다.                 |
| File      | ✅        | file API를 통해 지원됩니다.                 |
| Stream    | ✅        | Supported through `Stream`.                  |

#### 메모리

| 항목 | 검증 | 비고                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Supported through references and pointers. |
| Pointer   | ✅        | Supported through unsafe pointers.         |
| Variable  | ✅        | variable이 지원됩니다.                   |
| Constant  | ✅        | `const` 및 `readonly`를 통해 지원됩니다.  |

#### 연산

| Provision   | Verified | Notes                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | IL 및 operation을 통해 표현됩니다. |
| Procedure   | ✅        | `void` method를 통해 지원됩니다.      |
| Function    | ✅        | returning method를 통해 지원됩니다.   |

#### 스레딩

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | application 및 `Process` API를 통해 지원됩니다. |
| Thread     | ✅        | `Thread`를 통해 지원됩니다.                       |
| Dispatcher | ✅        | task 및 scheduler를 통해 지원됩니다.           |

#### 복합체

| 항목 | 검증 | 비고                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | type member가 지원됩니다.        |
| Object    | ✅        | object가 지원됩니다.             |
| Field     | ✅        | field가 지원됩니다.              |
| Method    | ✅        | method가 지원됩니다.             |
| Property  | ✅        | property가 native로 지원됩니다. |
| Structure | ✅        | structure가 native로 지원됩니다. |
| Class     | ✅        | class가 지원됩니다.             |
| Interface | ✅        | interface가 지원됩니다.          |
