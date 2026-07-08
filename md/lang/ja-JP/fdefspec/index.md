<!-- この翻訳は ChatGPT によって生成されたものであり、人間の翻訳者による確認が必要です。 -->
<!-- 翻訳が検証された後、プルリクエストでこれらの行を削除してください。 -->

# FDEFSPEC

<br/>

> **基礎定義仕様**<br/>
> リビジョン 1<br/>
> 2026年3月23日<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/>
> <br/>
> ここに示される定義と概念は、基礎的な数学的構成を記述するものであり、自由に再表現できます。

## はじめに

**Foundational Definitions Specification (FDEFSPEC)** は、CatalystUI エコシステムを支える中核概念と用語を確立します。その目的は、ドキュメント、仕様、実装、検証レビュー全体でこれらの概念に対する統一された理解を提供し、一貫性、明確さ、整合性を確保することです。

主要な用語と関係を正確で安定した形で定義することにより、FDEFSPEC は上位仕様の共通参照点を提供します。これにより、開発者、レビュー担当者、実装者は、言語、サービス、フレームワーク、システムが within spec と見なせるかどうかを判断する際に、同じ土台から推論できます。

> [!IMPORTANT]
>
> 定義は [set theory](https://en.wikipedia.org/wiki/Set_theory) 記法から派生した形式で表現します。この手法は、明確さと簡潔さを保ちながら、正確で曖昧さのない定義を提供します。これらの定義は、参照しやすく、解釈しやすく、一貫した概念階層を支えるように構成されています。

## 目次

- [FDEFSPEC](#fdefspec)
  - [はじめに](#introduction)
  - [目次](#table-of-contents)
  - [数値](#numerics)
    - [Bit](#bit)
    - [Nibble](#nibble)
      - [Nibble()](#nibble-1)
    - [Byte](#byte)
      - [Byte()](#byte-1)
      - [SByte()](#sbyte)
    - [Short](#short)
      - [Short()](#short-1)
      - [UShort()](#ushort)
    - [Int](#int)
      - [Int()](#int-1)
      - [UInt()](#uint)
    - [Long](#long)
      - [Long()](#long-1)
      - [ULong()](#ulong)
    - [Single](#single)
      - [Single()](#single-1)
    - [Double](#double)
      - [Double()](#double-1)
    - [Boolean](#boolean)
      - [Boolean()](#boolean-1)
  - [テキストエンコーディング](#text-encoding)
    - [テキストエンコーディング](#text-encoding-1)
      - [Text Encoding()](#text-encoding-2)
    - [Codepoint](#codepoint)
      - [Codepoint()](#codepoint-1)
    - [ASCII Code Unit](#ascii-code-unit)
      - [ASCII Code Unit()](#ascii-code-unit-1)
      - [ASCII()](#ascii)
    - [CP1252 Code Unit](#cp1252-code-unit)
      - [CP1252 Code Unit()](#cp1252-code-unit-1)
      - [CP1252()](#cp1252)
    - [UTF-8 Code Unit](#utf-8-code-unit)
      - [UTF-8 Code Unit()](#utf-8-code-unit-1)
      - [UTF-8()](#utf-8)
    - [UTF-16LE Code Unit](#utf-16le-code-unit)
      - [UTF-16LE Code Unit()](#utf-16le-code-unit-1)
      - [UTF-16LE()](#utf-16le)
  - [操作状態](#operation-status)
    - [Status Code](#status-code)
      - [Status Code()](#status-code-1)
      - [Status Code Level()](#status-code-level)
      - [Status Code Definition()](#status-code-definition)
        - [Success](#success)
        - [Warning](#warning)
        - [Error](#error)
        - [Fatal](#fatal)
    - [Context Code](#context-code)
      - [Context Code()](#context-code-1)
    - [Operation Code](#operation-code)
      - [Operation Code()](#operation-code-1)
    - [Detail Code](#detail-code)
      - [Detail Code()](#detail-code-1)
    - [Result](#result)
      - [Result()](#result-1)

## 数値

### Bit

bit は任意の $b \in \{0,1\}$ です。

### Nibble

nibble は任意の $(b_0,\dots,b_3)$ であり、すべての $i \in \{0,\dots,3\}$ について $b_i \in \mathrm{Bit}$ となるものです。

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

byte は任意の $(b_0,\dots,b_7)$ であり、すべての $i \in \{0,\dots,7\}$ について $b_i \in \mathrm{Bit}$ となるものです。

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

short は任意の $(b_0,\dots,b_{15})$ であり、すべての $i \in \{0,\dots,15\}$ について $b_i \in \mathrm{Bit}$ となるものです。

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

integer は任意の $(b_0,\dots,b_{31})$ であり、すべての $i \in \{0,\dots,31\}$ について $b_i \in \mathrm{Bit}$ となるものです。

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

long は任意の $(b_0,\dots,b_{63})$ であり、すべての $i \in \{0,\dots,63\}$ について $b_i \in \mathrm{Bit}$ となるものです。

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

single は任意の $(b_0,\dots,b_{31})$ であり、すべての $i \in \{0,\dots,31\}$ について $b_i \in \mathrm{Bit}$ となるものです。

#### Single()

次の定義は、単精度浮動小数点表現の IEEE 754 標準に準拠しています。これは、32-bit の binary sequence が floating-point number としてどのように解釈されるかを、zero、infinity、NaN (Not a Number) の特殊ケースを含めて定義します。

> $s = b_0$ とします。
>
> $e = \sum_{i=1}^{8} b_i 2^{8-i}$ とします。
>
> $f = \sum_{i=9}^{31} b_i 2^{31-i}$ とします。
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

double は任意の $(b_0,\dots,b_{63})$ であり、すべての $i \in \{0,\dots,63\}$ について $b_i \in \mathrm{Bit}$ となるものです。

#### Double()

次の定義は、倍精度浮動小数点表現の IEEE 754 標準に準拠しています。これは、64-bit の binary sequence が floating-point number としてどのように解釈されるかを、zero、infinity、NaN (Not a Number) の特殊ケースを含めて定義します。

> $s = b_0$ とします。
>
> $e = \sum_{i=1}^{11} b_i 2^{11-i}$ とします。
>
> $f = \sum_{i=12}^{63} b_i 2^{63-i}$ とします。
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

boolean は任意の $b \in \{0,1\}$ です。

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## テキストエンコーディング

### テキストエンコーディング

text encoding は次の集合として定義されます。

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Text Encoding()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Unicode codepoint は、$0 \leq e \leq 0x10FFFF$ を満たす任意の $e \in \mathbb{Z}$ です。

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

ASCII code unit は任意の $(b_0,\dots,b_6)$ であり、すべての $i \in \{0,\dots,6\}$, $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

性能と互換性の理由から、先頭に zero bit を追加して ASCII code unit を byte として表現することは一般的です。そのような場合、ASCII code unit は次のように表現されます。

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

それ以外の場合。

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

この定理では、どちらの定義も ASCII code unit の許容される表現です。一貫性のため、ASCII code unit を byte として表現する場合は最初の定義を使い、7-bit sequence として表現する場合は二番目の定義を使います。

#### ASCII()

ASCII は null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ であり、次を満たします。

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is an ASCII code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

この sequence は null-terminated であると言います。

### CP1252 Code Unit

CP1252 code unit は任意の $(b_0,\dots,b_7)$ であり、すべての $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 は null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ であり、次を満たします。

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a CP1252 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

この sequence は null-terminated であると言います。

### UTF-8 Code Unit

UTF-8 code unit は任意の $(b_0,\dots,b_7)$ であり、すべての $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 は null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ であり、次を満たします。

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-8 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

この sequence は null-terminated であると言います。

### UTF-16LE Code Unit

UTF-16LE code unit は任意の $(b_0,\dots,b_{15})$ であり、すべての $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE は null-terminated finite tuple $(u_0, \dots, u_k, u_{k+1})$ であり、次を満たします。

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-16LE code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

この sequence は null-terminated であると言います。

## 操作状態

### Status Code

status code は任意の $(b_0,\dots,b_7)$ であり、すべての $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

status code level は次の集合として定義されます。

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Status Code()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Status Code Level()

status code 値の集合は範囲 $[0, 255]$ であり、四つの level に分割されます。

> $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$ とします。
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Status Code Definition()

すべての status code には明示的な定義があります。次の一覧に含まれない status code は将来の使用のために予約されており、その意味は未定義です。status code の level は $\mathrm{Status\ Code\ Level}(s)$ によって決定されます。

次の一覧では、読みやすさのため入力 $s$ を hexadecimal value として表します。定義された各 status code は、該当する level、category、sub-category、description、detail を指定します。

新しい status code が定義されるに従って、この一覧は拡張される場合があります。新しく定義される status code は既存の code と衝突してはならず、明確に文書化された意味を持つ必要があります。

定義済み status code で表されない情報を伝えるには、context code、operation code、または detail code を使用する必要があります。

##### Success

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | 操作は正常に完了しました。 | |
| `0x01` | SUCCESS | NOOP | 操作は何も実行せず正常に完了しました。 | |

##### Warning

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | 操作は完了しましたが、結果は予期しないもの、または望ましくないものかもしれません。 | |
| `0x41` | WARNING | PARTIAL | 操作は完了しましたが、部分的にのみ完了しました。出力は不完全な場合があります。 | |
| `0x42` | WARNING | DEPRECATED | 操作は完了しましたが、deprecated feature または behavior を使用しました。将来この操作は機能しなくなる可能性があります。 | |

##### Error

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | recoverable error により操作は失敗しました。 | |
| `0x81` | ERROR | INVALID_ARGUMENT | 操作は失敗しました。argument が無効、または範囲外でした。 | function signature で左から右に 0 から数えた invalid argument の index。 |
| `0x82` | ERROR | INVALID_STATE | 操作は失敗しました。system は inconsistent、corrupted、またはその他の invalid state にあります。 | |
| `0x83` | ERROR | MALFORMED_INPUT | 操作は失敗しました。必要な input が malformed であるか、invalid data を含んでいました。 | |
| `0x84` | ERROR | ACCESS_DENIED | 必要な resource が access を拒否したため、操作は失敗しました。 | |
| `0x85` | ERROR | NOT_IMPLEMENTED | 要求された feature または behavior がまだ実装されていないため、操作は失敗しました。 | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | target system または configuration が要求された feature をサポートしないため、操作は失敗しました。 | |
| `0x87` | ERROR | TIMEOUT | 完了前に必要な timeout が発生したため、操作は失敗しました。 | |
| `0x88` | ERROR | NOT_FOUND | 必要な resource が存在しないため、操作は失敗しました。 | |
| `0x89` | ERROR | INTERRUPTED | external event が中断したため、操作は失敗しました。 | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | 必要な dependency が失敗したため、操作は失敗しました。 | dependency の `STATUS_CODE` 値。呼び出し元は、失敗した dependency を `OP_CODE` field で識別することが推奨されます（必須ではありません）。 |
| `0x90` | ERROR | BUFFER_OVERFLOW | 操作は失敗しました。buffer が必要な data を保持するには小さすぎました。 | |
| `0x91` | ERROR | ALLOCATION_FAILED | 操作は失敗しました。memory allocation request が成功しませんでした。 | |
| `0xA0` | ERROR | IO_ERROR | 操作は失敗しました。操作中に I/O error が発生しました。 | |

##### Fatal

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | unrecoverable error により操作は失敗しました。 | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | system が fundamental invariant に違反したため、操作は失敗しました。これは重大な logic error または data corruption を示します。 | |

### Context Code

context code は任意の $(b_0,\dots,b_7)$ であり、すべての $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Context Code()

context code value は、関連する operation によって定義される、完了した operation に関する追加の contextual information を表します。status code level が $\mathrm{Success}$ の場合は zero でなければならず、それ以外の場合は implementation-defined です。

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Operation Code

operation code は任意の $(b_0,\dots,b_7)$ であり、すべての $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Operation Code()

operation code value は result に関連付けられた operation を表します。その意味は対応する operation とそのドキュメントによって定義されます。未定義の値は unknown と見なされます。

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Detail Code

detail code は任意の $(b_0,\dots,b_7)$ であり、すべての $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Detail Code()

detail code value は完了した operation に関する追加情報を表します。その意味は、関連する status、context、operation code の順で定義され、そうでない場合は unknown です。

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Result

> [!TIP]
>
> result value は 32-bit integer として表現できます。big-endian byte order では、その値は `0xSSCCOODD` として現れ、`SS`、`CC`、`OO`、`DD` はそれぞれ status code、context code、operation code、detail code に対応します。little-endian byte order では、同じ値は `0xDDOOCCSS` として現れます。一貫して適用され、文書化されていれば、どちらの byte order も使用できます。

result は任意の $(b_0,\dots,b_{31})$ であり、すべての $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

result は四つの ordered bytes に分割されます。

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

ここで $s$、$c$、$o$、$d$ は result の構成要素です。

#### Result()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
