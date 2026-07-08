<!-- 이 번역은 ChatGPT가 생성한 것이며 인간 번역자의 검토가 필요합니다. -->
<!-- 번역이 확인된 후 pull request에서 이 줄들을 제거하십시오. -->

# 검토 세부 정보

## JavaScript

### 개요

JavaScript 프로그래밍 언어는 2026년 7월 7일 기준으로 FDEFSPEC(Rev. 1) 및 FRELSPEC(Rev. 1) 사양에 대해 검토되었습니다.

#### 검토 진술

JavaScript는 object, function, array, built-in language behavior를 통해 일부 필수 개념을 표현할 수 있지만, 이러한 메커니즘은 언어 수준에서 적용 가능한 CatalystUI 사양을 만족하기에 충분하지 않습니다.

이 검토는 주변 JavaScript 생태계가 아니라 JavaScript 자체를 평가합니다. Browser API, Node.js API, Deno API, Bun API, Web API, TypeScript, WebAssembly, external library, custom validation은 언어 수준 지원으로 취급되지 않습니다.

JavaScript는 필요한 fixed-width scalar numeric type이 많이 부족하고, 필요한 text encoding을 언어 기능으로 제공하지 않으며, 여러 필수 system, memory, threading, composite 구조를 정의하지 않기 때문에, 상당한 추가 infrastructure 없이는 CatalystUI 준수 구현을 위한 충분히 안정적인 기반을 제공한다고 보지 않습니다.

따라서 JavaScript에는 프로그래밍 언어에 대한 CatalystUI Verified 상태가 부여되지 않았습니다.

#### 검토 전제

이 검토는 엄격한 언어 수준 기준을 적용합니다. 어떤 조항이 JavaScript 자체에서 명시적으로 지원되지 않으면 검증되지 않은 것으로 표시됩니다.

host-provided API, implementation-specific behavior, external library, transpiler, type system, custom runtime validation은 검증에서 제외됩니다.

### 경고

* JavaScript는 `Number`를 통해 많은 numeric value를 표현할 수 있지만, `Number`는 64-bit floating point numeric type입니다.
* JavaScript는 `BigInt`를 제공하지만 `BigInt`는 arbitrary-width입니다.
* typed array는 scalar language type이 아니라 binary storage view를 제공합니다.
* JavaScript 문자열은 explicit text encoding value가 아니라 UTF-16 code unit을 사용합니다.
* `const`는 object value가 아니라 binding을 보호합니다.

### 실패 사항

* JavaScript는 필요한 fixed-width scalar numeric type 대부분을 제공하지 않습니다.
* JavaScript는 전용 scalar 32-bit floating point type을 제공하지 않습니다.
* JavaScript는 ASCII, CP1252, UTF-8, UTF-16LE를 language-level text encoding으로 제공하지 않습니다.
* JavaScript는 language-level file 또는 stream construct를 제공하지 않습니다.
* JavaScript는 language-level address 또는 pointer construct를 제공하지 않습니다.
* JavaScript는 language-level process, thread 또는 dispatcher construct를 제공하지 않습니다.
* JavaScript property는 필요한 Get/Set accessor map으로 뒷받침되는 explicit keyed member를 제공하지 않습니다.
* JavaScript는 structure 또는 interface를 제공하지 않습니다.

### FDEFSPEC 검증

#### 수치

| 항목 | 검증 | 비고                          |
| --------- | -------- | ------------------------------ |
| Bit       | ❌        | 1-bit numeric type이 없습니다.         |
| Nibble    | ❌        | 4-bit numeric type이 없습니다.         |
| Byte      | ❌        | scalar 8-bit integer type이 없습니다.  |
| Short     | ❌        | scalar 16-bit integer type이 없습니다. |
| Int       | ❌        | scalar 32-bit integer type이 없습니다. |
| Long      | ❌        | scalar 64-bit integer type이 없습니다. |
| Float     | ❌        | scalar 32-bit float type이 없습니다.   |
| Double    | ✅        | `Number`를 통해 지원됩니다.    |
| Boolean   | ✅        | `boolean`을 통해 지원됩니다.   |

#### 텍스트 인코딩

| 항목 | 검증 | 비고                        |
| --------- | -------- | ---------------------------- |
| Codepoint | ❌        | 전용 codepoint type이 없습니다. |
| ASCII     | ❌        | language-level이 아닙니다.          |
| CP1252    | ❌        | language-level이 아닙니다.          |
| UTF-8     | ❌        | language-level이 아닙니다.          |
| UTF-16LE  | ❌        | language-level이 아닙니다.          |

#### 연산 상태

| 항목 | 검증 | 비고                           |
| --------- | -------- | ------------------------------- |
| Status    | ⚠️       | 표현 가능하지만 강제되지는 않습니다. |
| Context   | ⚠️       | 표현 가능하지만 강제되지는 않습니다. |
| Operation | ⚠️       | 표현 가능하지만 강제되지는 않습니다. |
| Detail    | ⚠️       | 표현 가능하지만 강제되지는 않습니다. |
| Result    | ⚠️       | runtime validation이 필요합니다.    |

### FRELSPEC 검증

#### 컬렉션

| 항목 | 검증 | 비고                    |
| --------- | -------- | ------------------------ |
| Set       | ✅        | `Set`을 통해 지원됩니다. |
| Map       | ✅        | `Map`을 통해 지원됩니다. |
| Array     | ✅        | array가 지원됩니다.    |
| File      | ❌        | language-level이 아닙니다.      |
| Stream    | ❌        | language-level이 아닙니다.      |

#### 메모리

| 항목 | 검증 | 비고                           |
| --------- | -------- | ------------------------------- |
| Address   | ❌        | address 지원이 없습니다.             |
| Pointer   | ❌        | pointer 지원이 없습니다.             |
| Variable  | ✅        | variable이 지원됩니다.        |
| Constant  | ⚠️       | `const`는 binding만 보호합니다. |

#### 연산

| Provision   | Verified | Notes                            |
| ----------- | -------- | -------------------------------- |
| Instruction | ❌        | 정의된 instruction type이 없습니다.     |
| Procedure   | ❌        | function은 항상 값을 반환합니다. |
| Function    | ✅        | Functions are supported.         |

#### 스레딩

| Provision  | Verified | Notes                       |
| ---------- | -------- | --------------------------- |
| Process    | ❌        | language-level이 아닙니다.         |
| Thread     | ⚠️        | agent를 통해 표현됩니다. |
| Dispatcher | ❌        | host scheduling이 필요합니다.   |


#### 복합체

| 항목 | 검증 | 비고                                 |
| --------- | -------- | ------------------------------------- |
| Member    | ✅        | object member가 지원됩니다.         |
| Object    | ✅        | object가 지원됩니다.                |
| Field     | ✅        | data property가 field를 표현할 수 있습니다. |
| Method    | ✅        | method가 지원됩니다.                |
| Property  | ❌        | 명시적인 accessor map이 없습니다.             |
| Structure | ❌        | structure 지원이 없습니다.                 |
| Class     | ✅        | class syntax가 지원됩니다.            |
| Interface | ❌        | interface 지원이 없습니다.                 |
