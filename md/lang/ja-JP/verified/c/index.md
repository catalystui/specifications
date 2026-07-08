<!-- この翻訳は ChatGPT によって生成されたものであり、人間の翻訳者による確認が必要です。 -->
<!-- 翻訳が検証された後、プルリクエストでこれらの行を削除してください。 -->

# 検証詳細

## C

### 概要

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C プログラミング言語は、2026年7月7日時点で FDEFSPEC (Rev. 1) および FRELSPEC (Rev. 1) 仕様に照らして検証されています。

#### 善意による声明

私たちは善意に基づき、C プログラミング言語は以下の仕様で定義された概念と規定を合理的に表現でき、これらの仕様に準拠するシステムの実装に使用できると考えます。

#### レビュー声明

C は、基礎データ表現、メモリアクセス、ファイル、ストリーム、手続き、関数、構造体、直接的なシステム指向実装に対して、強力な low-level サポートを提供します。

C はいくつかの object-oriented composite constructs をネイティブには提供しませんが、これらの制限は特定の FRELSPEC composite provisions に限定されており、以下に記録されています。これらの不合格事項は、C が全体として within spec と見なされることを妨げるものではありませんが、CatalystUI 互換実装で C を使う場合には理解しておく必要があります。

#### レビュー前提

このレビューでは、バージョン依存の機能が注記されている場合に、現代的な標準 C サポートを前提とします。exact-width integer サポートは、対応する `<stdint.h>` 型が実装によって提供されることを前提とします。

このレビューでは、C を low-level representation language として扱います。名前付きの標準 codec が提供されない場合、byte-exact encodings は byte arrays、lookup tables、明示的な parsing logic を通じて直接表現できます。

### 警告

* exact-width integer types は実装サポートに依存します。
* CP1252 は byte-for-byte で表現できますが、名前付きの standard codec は提供されません。
* UTF-16LE serialization には明示的な byte-order handling が必要です。
* standard threads は一部の C 実装で省略される場合があります。
* object-oriented patterns は手動でエミュレートできますが、native language constructs ではありません。

### 不合格事項

* C は native method members を提供しません。
* C は native properties を提供しません。
* C は native classes を提供しません。
* C は native interfaces を提供しません。

### FDEFSPEC 検証

#### 数値

| Provision | Verified | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | 次を通じてサポートされます: `unsigned char`.          |
| Short     | ✅        | 次を通じてサポートされます: `int16_t` および `uint16_t`. |
| Int       | ✅        | 次を通じてサポートされます: `int32_t` および `uint32_t`. |
| Long      | ✅        | 次を通じてサポートされます: `int64_t` および `uint64_t`. |
| Float     | ✅        | 次を通じてサポートされます: `float`.                  |
| Double    | ✅        | 次を通じてサポートされます: `double`.                 |
| Boolean   | ✅        | 次を通じてサポートされます: `bool`; C99+.             |

#### テキストエンコーディング

| Provision | Verified | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | 次を通じてサポートされます: `char32_t`; C11+.     |
| ASCII     | ✅        | byte values として表現可能です。           |
| CP1252    | ⚠️        | 明示的な byte mapping が必要です。         |
| UTF-8     | ✅        | 次を通じてサポートされます: UTF-8 literals; C11+. |
| UTF-16LE  | ⚠️        | byte-order handling が必要です。           |

#### 操作状態

| Provision | Verified | Notes                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | 次によって表現できます: enum.  |
| Context   | ✅        | 次によって表現できます: value.  |
| Operation | ✅        | 次によって表現できます: value.  |
| Detail    | ✅        | 次によって表現できます: value.  |
| Result    | ✅        | 次によって表現できます: struct. |

### FRELSPEC 検証

#### コレクション

| Provision | Verified | Notes                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | 次によって表現できます: structs. |
| Map       | ✅        | 次によって表現できます: structs. |
| Array     | ✅        | native arrays がサポートされています。   |
| File      | ✅        | 次を通じてサポートされます: file APIs.   |
| Stream    | ✅        | 次を通じてサポートされます: stream APIs. |

#### メモリ

| Provision | Verified | Notes                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | addresses がサポートされています。   |
| Pointer   | ✅        | pointers がサポートされています。    |
| Variable  | ✅        | variables がサポートされています。   |
| Constant  | ✅        | 次を通じてサポートされます: `const`. |

#### 操作

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | 次を通じてサポートされます: `void` functions.     |
| Function    | ✅        | 次を通じてサポートされます: returning functions.  |

#### スレッド処理

| Provision  | Verified | Notes                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | 次を通じてサポートされます: hosted environments. |
| Thread     | ⚠️        | 次を通じてサポートされます: `<threads.h>`; C11+. |
| Dispatcher | ✅        | 直接表現できます。           |

#### 複合体

| Provision | Verified | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | struct members がサポートされています。            |
| Object    | ✅        | Structs can form addressable composites. |
| Field     | ✅        | struct fields がサポートされています。             |
| Method    | ❌        | native method members はありません。                |
| Property  | ❌        | explicit Get/Set accessor map はありません。        |
| Structure | ✅        | structures がネイティブにサポートされています。       |
| Class     | ❌        | native class construct はありません。               |
| Interface | ❌        | native interface construct はありません。           |
