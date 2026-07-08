<!-- 이 번역은 ChatGPT가 생성한 것이며 인간 번역자의 검토가 필요합니다. -->
<!-- 번역이 확인된 후 pull request에서 이 줄들을 제거하십시오. -->

# 검토 세부 정보

## Python

### 개요

Python 프로그래밍 언어는 2026년 7월 7일 기준으로 FDEFSPEC(Rev. 1) 및 FRELSPEC(Rev. 1) 사양에 대해 검토되었습니다.

#### 검토 진술

Python은 built-in type, object, function, class, standard-library module, custom validation을 통해 많은 필수 개념을 표현할 수 있지만, 이러한 메커니즘은 언어 수준에서 적용 가능한 CatalystUI 사양을 만족하기에 충분하지 않습니다.

Python은 내장 동작과 표준 라이브러리를 통해 text encoding, file, stream, object, function, class, property, process, thread, dispatched execution을 강력하게 지원합니다. 그러나 Python은 필요한 fixed-width scalar numeric type을 제공하지 않고, true constant를 정의하지 않으며, 다른 검증 언어가 더 직접적으로 표현할 수 있는 여러 구조에 대해 dynamic runtime behavior에 의존합니다.

이 때문에 우리는 상당한 추가 infrastructure 없이는 Python이 CatalystUI 준수 구현을 위한 충분히 안정적인 기반을 제공한다고 보지 않습니다.

따라서 Python에는 프로그래밍 언어에 대한 CatalystUI Verified 상태가 부여되지 않았습니다.

#### 검토 전제

이 검토는 Python 자체와 함께 제공되는 표준 라이브러리를 평가합니다.

third-party package, implementation-specific extension, optional native module, external type checker, transpiler, custom runtime framework는 언어 수준 지원으로 취급되지 않습니다.

### 경고

* Python은 fixed-width integer primitive가 아니라 unlimited-precision integer를 제공합니다.
* Python `float`은 보통 double precision이지만, 별도의 fixed-width family는 아닙니다.
* 일부 low-level memory behavior에는 `ctypes` 또는 implementation-specific behavior가 필요할 수 있습니다.
* Python type hint는 runtime에서 강제되지 않습니다.
* Python은 property를 지원하지만 setter 동작은 생략될 수 있습니다.
* Python은 표준 라이브러리 기능을 통해 여러 structure를 모델링할 수 있지만 native structure type으로 제공하지는 않습니다.

### 실패 사항

* Python does not provide most required fixed-width scalar numeric types.
* Python은 전용 scalar 32-bit floating point type을 제공하지 않습니다.
* Python은 true language-level constant를 제공하지 않습니다.
* Python은 procedure를 function과 별도로 정의하지 않습니다.
* Python은 native pointer 지원을 제공하지 않습니다.
* Python은 native interface 지원을 제공하지 않습니다.

### FDEFSPEC 검증

#### 수치

| 항목 | 검증 | 비고                                |
| --------- | -------- | ------------------------------------ |
| Bit       | ❌        | 1-bit numeric type이 없습니다.               |
| Nibble    | ❌        | 4-bit numeric type이 없습니다.               |
| Byte      | ❌        | scalar 8-bit integer type이 없습니다.        |
| Short     | ❌        | scalar 16-bit integer type이 없습니다.       |
| Int       | ❌        | scalar 32-bit integer type이 없습니다.       |
| Long      | ❌        | scalar 64-bit integer type이 없습니다.       |
| Float     | ❌        | scalar 32-bit float type이 없습니다.         |
| Double    | ⚠️       | `float`은 보통 double precision입니다. |
| Boolean   | ✅        | `bool`을 통해 지원됩니다.            |

#### 텍스트 인코딩

| 항목 | 검증 | 비고                            |
| --------- | -------- | -------------------------------- |
| Codepoint | ✅        | string은 Unicode code point를 사용합니다. |
| ASCII     | ✅        | 지원되는 codec입니다.                 |
| CP1252    | ✅        | 지원되는 codec입니다.                 |
| UTF-8     | ✅        | 지원되는 codec입니다.                 |
| UTF-16LE  | ✅        | 지원되는 codec입니다.                 |

#### 연산 상태

| 항목 | 검증 | 비고                       |
| --------- | -------- | --------------------------- |
| Status    | ⚠️       | custom validation이 필요합니다. |
| Context   | ⚠️       | custom validation이 필요합니다. |
| Operation | ⚠️       | custom validation이 필요합니다. |
| Detail    | ⚠️       | custom validation이 필요합니다. |
| Result    | ⚠️       | custom validation이 필요합니다. |

### FRELSPEC 검증

#### 컬렉션

| 항목 | 검증 | 비고                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | `set`을 통해 지원됩니다.       |
| Map       | ✅        | `dict`를 통해 지원됩니다.      |
| Array     | ✅        | sequence를 통해 지원됩니다.   |
| File      | ✅        | file API를 통해 지원됩니다.   |
| Stream    | ✅        | stream API를 통해 지원됩니다. |

#### 메모리

| 항목 | 검증 | 비고                        |
| --------- | -------- | ---------------------------- |
| Address   | ⚠️       | object identity만 해당됩니다.        |
| Pointer   | ❌        | native pointer 지원이 없습니다.   |
| Variable  | ✅        | name binding이 지원됩니다. |
| Constant  | ❌        | true constant가 없습니다.           |

#### 연산

| Provision   | Verified | Notes                             |
| ----------- | -------- | --------------------------------- |
| Instruction | ⚠️       | bytecode는 implementation-level입니다. |
| Procedure   | ❌        | function은 `None`을 반환합니다.          |
| Function    | ✅        | Functions are supported.          |

#### 스레딩

| Provision  | Verified | Notes                            |
| ---------- | -------- | -------------------------------- |
| Process    | ✅        | process API를 통해 지원됩니다.  |
| Thread     | ✅        | Supported through `threading`.   |
| Dispatcher | ✅        | executor API를 통해 지원됩니다. |

#### 복합체

| 항목 | 검증 | 비고                            |
| --------- | -------- | -------------------------------- |
| Member    | ✅        | object member가 지원됩니다.    |
| Object    | ✅        | object가 지원됩니다.           |
| Field     | ✅        | attribute가 field를 표현할 수 있습니다. |
| Method    | ✅        | method가 지원됩니다.           |
| Property  | ⚠️       | getter/setter 지원이 존재합니다.    |
| Structure | ⚠️       | 표준 라이브러리 모델만 해당됩니다.    |
| Class     | ✅        | class가 지원됩니다.           |
| Interface | ❌        | native interface 지원이 없습니다.     |
