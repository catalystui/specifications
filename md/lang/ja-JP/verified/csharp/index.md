<!-- この翻訳は ChatGPT によって生成されたものであり、人間の翻訳者による確認が必要です。 -->
<!-- 翻訳が検証された後、プルリクエストでこれらの行を削除してください。 -->

# 検証詳細

## C#

### 概要

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C# プログラミング言語は、2026年7月7日時点で FDEFSPEC (Rev. 1) および FRELSPEC (Rev. 1) 仕様に照らして検証されています。

#### 善意による声明

私たちは善意に基づき、C# プログラミング言語は以下の仕様で定義された概念と規定を合理的に表現でき、これらの仕様に準拠するシステムの実装に使用できると考えます。

#### レビュー前提

このレビューでは、バージョン依存の機能が注記されている場合に、現代的な C# と .NET サポートを前提とします。

### 警告

* CP1252 support は公式 .NET code pages provider を通じて利用できますが、target runtime によっては provider registration または追加 package が必要になる場合があります。
* unsafe pointer behavior には明示的な unsafe authorization が必要な場合があります。

### 不合格事項

* この検証中に既知の FDEFSPEC または FRELSPEC の不合格事項は見つかりませんでした。

### FDEFSPEC 検証

#### 数値

| Provision | Verified | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | 1-bit numeric はありません。widen してください。                |
| Nibble    | ⚠️       | 4-bit numeric はありません。widen してください。                |
| Byte      | ✅        | 次を通じてサポートされます: `byte` および `sbyte`.   |
| Short     | ✅        | 次を通じてサポートされます: `short` および `ushort`. |
| Int       | ✅        | 次を通じてサポートされます: `int` および `uint`.     |
| Long      | ✅        | 次を通じてサポートされます: `long` および `ulong`.   |
| Float     | ✅        | 次を通じてサポートされます: `float`.              |
| Double    | ✅        | 次を通じてサポートされます: `double`.             |
| Boolean   | ✅        | 次を通じてサポートされます: `bool`.               |

#### テキストエンコーディング

| Provision | Verified | Notes                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | 次を通じてサポートされます: numerics and `Rune`. |
| ASCII     | ✅        | 次を通じてサポートされます: `Encoding.ASCII`.    |
| CP1252    | ⚠️       | code pages provider が必要です。          |
| UTF-8     | ✅        | 次を通じてサポートされます: `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | 次を通じてサポートされます: `Encoding.Unicode`.  |

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

| Provision | Verified | Notes                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | 次を通じてサポートされます: `HashSet<T>`.              |
| Map       | ✅        | 次を通じてサポートされます: `Dictionary<TKey,TValue>`. |
| Array     | ✅        | native arrays がサポートされています。                 |
| File      | ✅        | 次を通じてサポートされます: file APIs.                 |
| Stream    | ✅        | 次を通じてサポートされます: `Stream`.                  |

#### メモリ

| Provision | Verified | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | 次を通じてサポートされます: references and pointers. |
| Pointer   | ✅        | 次を通じてサポートされます: unsafe pointers.         |
| Variable  | ✅        | variables がサポートされています。                   |
| Constant  | ✅        | 次を通じてサポートされます: `const` および `readonly`.  |

#### 操作

| Provision   | Verified | Notes                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Represented through IL and operations. |
| Procedure   | ✅        | 次を通じてサポートされます: `void` methods.      |
| Function    | ✅        | 次を通じてサポートされます: returning methods.   |

#### スレッド処理

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | 次を通じてサポートされます: application および `Process` APIs. |
| Thread     | ✅        | 次を通じてサポートされます: `Thread`.                       |
| Dispatcher | ✅        | 次を通じてサポートされます: tasks and schedulers.           |

#### 複合体

| Provision | Verified | Notes                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | type members がサポートされています。        |
| Object    | ✅        | objects がサポートされています。             |
| Field     | ✅        | fields がサポートされています。              |
| Method    | ✅        | methods がサポートされています。             |
| Property  | ✅        | properties がネイティブにサポートされています。 |
| Structure | ✅        | structures がネイティブにサポートされています。 |
| Class     | ✅        | classes がサポートされています。             |
| Interface | ✅        | interfaces がサポートされています。          |
