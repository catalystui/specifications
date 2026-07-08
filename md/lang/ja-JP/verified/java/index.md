<!-- この翻訳は ChatGPT によって生成されたものであり、人間の翻訳者による確認が必要です。 -->
<!-- 翻訳が検証された後、プルリクエストでこれらの行を削除してください。 -->

# 検証詳細

## Java

### 概要

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Java プログラミング言語は、2026年7月7日時点で FDEFSPEC (Rev. 1) および FRELSPEC (Rev. 1) 仕様に照らして検証されています。

#### 善意による声明

私たちは善意に基づき、Java プログラミング言語は以下の仕様で定義された概念と規定の大部分を合理的に表現でき、これらの仕様に準拠するシステムの実装に使用できると考えます。

#### レビュー前提

このレビューでは、バージョン依存の機能が注記されている場合に、現代的な Java 言語サポートを前提とします。local variable inference、records、foreign memory access などの機能には、より新しい Java バージョンが必要な場合があります。

### 警告

* Java には unsigned numeric types の native support がないため、一部の provisions では widening または代替表現が必要になる場合があります。
* direct memory address と pointer-style behavior には Java 22+ Foreign Function and Memory API support が必要な場合があります。
* Java には native property syntax がないため、代わりに getter と setter methods が必要です。

### 不合格事項

* Java は CP1252 を guaranteed standard charset として提供しないため、完全な準拠には implementation-specific support、追加 libraries、または custom handling が必要です。
* Java properties は、必要な Get/Set accessor map に支えられた explicit keyed member を提供しません。

### FDEFSPEC 検証

#### 数値

| Provision | Verified | Notes                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | 1-bit numeric はありません。widen してください。                         |
| Nibble    | ⚠️       | 4-bit numeric はありません。widen してください。                         |
| Byte      | ⚠️       | signed 8-bit のみです。unsigned には widen してください。           |
| Short     | ⚠️       | signed 16-bit のみです。unsigned には widen してください。          |
| Int       | ⚠️       | signed 32-bit です。unsigned helpers には Java 8+ が必要です。 |
| Long      | ⚠️       | signed 64-bit です。unsigned helpers には Java 8+ が必要です。 |
| Float     | ✅        | 32-bit floating point がサポートされています。              |
| Double    | ✅        | 64-bit floating point がサポートされています。              |
| Boolean   | ✅        | Boolean type がサポートされています。                       |

#### テキストエンコーディング

| Provision | Verified | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | 次を通じてサポートされます: `int` および `Character`. |
| ASCII     | ✅        | guaranteed standard charset です。             |
| CP1252    | ❌        | 次によって保証されません: `StandardCharsets`.    |
| UTF-8     | ✅        | guaranteed standard charset です。             |
| UTF-16LE  | ✅        | guaranteed standard charset です。             |

#### 操作状態

| Provision | Verified | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | 次によって表現できます: custom type.        |
| Context   | ✅        | 次によって表現できます: custom value.       |
| Operation | ✅        | 次によって表現できます: custom value.       |
| Detail    | ✅        | 次によって表現できます: custom value.       |
| Result    | ✅        | 次によって表現できます: custom return type. |

### FRELSPEC 検証

#### コレクション

| Provision | Verified | Notes                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | 次を通じてサポートされます: `Set`.       |
| Map       | ✅        | 次を通じてサポートされます: `Map`.       |
| Array     | ✅        | native arrays がサポートされています。   |
| File      | ✅        | 次を通じてサポートされます: file APIs.   |
| Stream    | ✅        | 次を通じてサポートされます: stream APIs. |

#### メモリ

| Provision | Verified | Notes                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | direct addresses には Java 22+ FFM が必要です。                         |
| Pointer   | ⚠️       | pointer-like access には Java 22+ FFM が必要です。                     |
| Variable  | ✅        | declarations と `var` がサポートされています。`var` には Java 10+ が必要です。 |
| Constant  | ✅        | 次を通じてサポートされます: `final`.                                     |

#### 操作

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | bytecode と operations を通じて表現されます。 |
| Procedure   | ✅        | 次を通じてサポートされます: `void` methods.            |
| Function    | ✅        | 次を通じてサポートされます: returning methods.         |

#### スレッド処理

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | 次を通じてサポートされます: application および `Process` APIs. |
| Thread     | ✅        | 次を通じてサポートされます: `Thread`.                       |
| Dispatcher | ✅        | 次を通じてサポートされます: `Executor` APIs.                |

#### 複合体

| Provision | Verified | Notes                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | class members がサポートされています。           |
| Object    | ✅        | objects がサポートされています。                 |
| Field     | ✅        | fields がサポートされています。                  |
| Method    | ✅        | methods がサポートされています。                 |
| Property  | ❌        | explicit accessor map はありません。              |
| Structure | ✅        | 次を通じてサポートされます: records; Java 16+.   |
| Class     | ✅        | classes がサポートされています。                 |
| Interface | ✅        | interfaces がサポートされています。              |
