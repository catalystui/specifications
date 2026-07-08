<!-- この翻訳は ChatGPT によって生成されたものであり、人間の翻訳者による確認が必要です。 -->
<!-- 翻訳が検証された後、プルリクエストでこれらの行を削除してください。 -->

# 検証詳細

## C++

### 概要

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C++ プログラミング言語は、2026年7月7日時点で FDEFSPEC (Rev. 1) および FRELSPEC (Rev. 1) 仕様に照らして検証されています。

#### 善意による声明

私たちは善意に基づき、C++ プログラミング言語は以下の仕様で定義された概念と規定を合理的に表現でき、これらの仕様に準拠するシステムの実装に使用できると考えます。

#### レビュー前提

このレビューでは、バージョン依存の機能が注記されている場合に、現代的な標準 C++ サポートを前提とします。exact-width integer サポートは、対応する `<cstdint>` 型が実装によって提供されることを前提とします。

このレビューでは、C++ を low-level representation、object modeling、memory control、generic programming、concurrent execution を直接サポートする systems programming language として扱います。

### 警告

* exact-width integer types は実装サポートに依存します。
* CP1252 は byte-for-byte で表現できますが、名前付きの standard codec は提供されません。
* UTF-16LE serialization には明示的な byte-order handling が必要です。
* 一部の concurrency および character features には、現代的な C++ revisions が必要です。

### 不合格事項

* この検証中に既知の FDEFSPEC または FRELSPEC の不合格事項は見つかりませんでした。

### FDEFSPEC 検証

#### 数値

| Provision | Verified | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | 次を通じてサポートされます: `std::byte`.              |
| Short     | ✅        | 次を通じてサポートされます: `int16_t` および `uint16_t`. |
| Int       | ✅        | 次を通じてサポートされます: `int32_t` および `uint32_t`. |
| Long      | ✅        | 次を通じてサポートされます: `int64_t` および `uint64_t`. |
| Float     | ✅        | 次を通じてサポートされます: `float`.                  |
| Double    | ✅        | 次を通じてサポートされます: `double`.                 |
| Boolean   | ✅        | 次を通じてサポートされます: `bool`.                   |

#### テキストエンコーディング

| Provision | Verified | Notes                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | 次を通じてサポートされます: `char32_t`.        |
| ASCII     | ✅        | byte values として表現可能です。        |
| CP1252    | ⚠️        | 明示的な byte mapping が必要です。      |
| UTF-8     | ✅        | 次を通じてサポートされます: `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | byte-order handling が必要です。        |

#### 操作状態

| Provision | Verified | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | 次によって表現できます: enum.           |
| Context   | ✅        | 次によって表現できます: value.           |
| Operation | ✅        | 次によって表現できます: value.           |
| Detail    | ✅        | 次によって表現できます: value.           |
| Result    | ✅        | 次によって表現できます: struct または class. |

### FRELSPEC 検証

#### コレクション

| Provision | Verified | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | 次を通じてサポートされます: `std::set`.              |
| Map       | ✅        | 次を通じてサポートされます: `std::map`.              |
| Array     | ✅        | 次を通じてサポートされます: arrays および `std::array`. |
| File      | ✅        | 次を通じてサポートされます: file streams.            |
| Stream    | ✅        | 次を通じてサポートされます: iostreams.               |

#### メモリ

| Provision | Verified | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | addresses がサポートされています。                   |
| Pointer   | ✅        | pointers がサポートされています。                    |
| Variable  | ✅        | variables がサポートされています。                   |
| Constant  | ✅        | 次を通じてサポートされます: `const` および `constexpr`. |

#### 操作

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | 次を通じてサポートされます: `void` functions.     |
| Function    | ✅        | 次を通じてサポートされます: returning functions.  |

#### スレッド処理

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | 次を通じてサポートされます: hosted execution.      |
| Thread     | ✅        | 次を通じてサポートされます: `std::thread`; C++11+. |
| Dispatcher | ✅        | 次を通じてサポートされます: async and schedulers.  |

#### 複合体

| Provision | Verified | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | class members がサポートされています。            |
| Object    | ✅        | objects がサポートされています。                  |
| Field     | ✅        | fields がサポートされています。                   |
| Method    | ✅        | methods がサポートされています。                  |
| Property  | ✅        | Get/Set maps can be represented.        |
| Structure | ✅        | structures がネイティブにサポートされています。      |
| Class     | ✅        | classes がネイティブにサポートされています。         |
| Interface | ✅        | 次によって表現できます: abstract classes. |
