<!-- この翻訳は ChatGPT によって生成されたものであり、人間の翻訳者による確認が必要です。 -->
<!-- 翻訳が検証された後、プルリクエストでこれらの行を削除してください。 -->

# FRELSPEC

<br/>

> **基礎関係仕様**<br/>
> リビジョン 2.1<br/>
> 2026年11月24日<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> すべての権利を留保します。<br/>
> <br/>
> ここで示される定義と概念は基本的な数学的構成を記述するものであり、自由に言い換えることができます。

## はじめに

**基礎関係仕様（FRELSPEC）**は、CatalystUI エコシステムの基盤となる中核的な関係構造を定めます。その目的は、文書、仕様、実装、検証レビューにおけるメモリ、コレクション、操作、複合構造の関係について統一的な理解を提供し、一貫性、明瞭性、整合性を確保することです。

基礎概念間の関係を正確かつ安定した形式で定義することにより、FRELSPEC は上位仕様の共通の参照点を提供し、個々の実装が独自の規則と振る舞いを定めることを可能にします。これにより、開発者、レビュー担当者、実装者は共通の基盤から、言語、サービス、フレームワーク、またはシステムが仕様適合に必要な関係的構成を表現できるかどうかを判断できます。

> [!IMPORTANT]
>
> 定義は[集合論](https://en.wikipedia.org/wiki/Set_theory)の記法から派生した形式を用いて表現します。この方法は明瞭性と簡潔さを保ちつつ、正確で曖昧さのない定義を提供します。参照の容易さ、明確な解釈、一貫した概念階層を支えるように定義を構成します。

## 目次

- [FRELSPEC](#frelspec)
  - [はじめに](#はじめに)
  - [目次](#目次)
  - [改訂履歴](#改訂履歴)
    - [リビジョン 2.1](#リビジョン-21)
    - [リビジョン 2](#リビジョン-2)
  - [メモリ](#メモリ)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [コレクション](#コレクション)
    - [Set](#set)
      - [Set()](#set-1)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [操作](#操作)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [スレッド処理](#スレッド処理)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [複合構造](#複合構造)
    - [Member](#member)
    - [Object](#object)
      - [Object(k)](#objectk)
    - [Field](#field)
      - [Field(o,k)](#fieldok)
    - [Method](#method)
      - [Method(o,k)](#methodok)
    - [Property](#property)
      - [Property(o,k)](#propertyok)
      - [Get(o,k)](#getok)
      - [Set(o,k)](#setok)
    - [Structure](#structure)
      - [Structure(s,k)](#structuresk)
    - [Class](#class)
      - [Class(c,a)](#classca)
    - [Interface](#interface)
      - [Interface(r,o)](#interfacero)

## 改訂履歴

### リビジョン 2.1

**2026年11月24日**

File の定義を精緻化してメタデータに基づくデータ解決を定め、Stream を逐次的なデータ生成または取得の独立した仕組みとして再定義しました。これにより、他のコレクションに追加の制約を課さず、ストリームが有限または無限の列を表現できるようになりました。

### リビジョン 2

**2026年11月21日**

バイトおよびバイト配列を用いたメモリと格納値の表現に不整合を発見しました。Word をメモリの基本表現として確立し、メモリ、操作、複合構造にまたがる関係を統一しました。

配列のインデックス付けとコレクション間の関係に不整合を発見しました。有限で連続したインデックスを標準化し、Array、File、Stream の関係を明確化しました。

実行と複合構造の関係に冗長性と曖昧さを発見しました。実装独立性を維持しながら、手続き、関数、ディスパッチャー、オブジェクトの関係を精緻化し、これらの問題を解決しました。

## メモリ

### Word

ワードとは、メモリに格納された任意のビット列 $w \in \mathrm{Bit}^n$ であり、$n \in \mathbb{N}^+$ を満たすものです。

### Address

アドレスとは任意のワード $a \in A$ であり、$A$ はワードの集合であり、$a$ が指定されたメモリ構造内の位置を一意に識別するものです。

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

ポインタとは任意の関数 $f_p : \{a\} \to B$ であり、$a \in A$ はアドレス、$B$ はワードの集合です。$f_p$ を適用するたびに、$a$ によって識別されるメモリ位置に格納されたワードを評価します。

#### Pointer()

> $f_m : A \to B$ をメモリマップとします。
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

変数とは任意の関数 $f_v : \{k\} \to B$ であり、$k$ はキー、$B$ はワードの集合です。変数はキーをアドレスに束縛し、そのアドレスに格納されたワードを評価することでポインタを拡張します。

#### Variable(k)

> $f_b : \{k\} \to \{a\}$ を変数の束縛関数とします。
>
> $f_p : \{a\} \to B$ をポインタとします。
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

定数とは任意の変数 $f_c : \{k\} \to B$ であり、$k$ はキー、$B$ はワードの集合です。$k$ に関連付けられたワードは割り当て後に変更できません。

#### Constant(k)

> $b_0 \in B$ を $k$ に割り当てられたワードとします。
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ （$b_0$ の割り当て後）。

## コレクション

### Set

集合とは、相異なるワードからなる任意の有限で順序のないコレクションです。

#### Set()

> $B$ をワードの集合とします。
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

マップとは任意の関数 $f_m : K \to V$ であり、$K$ はキーの集合、$V$ は値の集合であり、各キーがちょうど一つの値に関連付けられます。

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

配列とは任意の関数 $f_a : I \to V$ であり、$I \subseteq \mathbb{N}$ は有限で連続した整数インデックスの集合、$V$ はワードの集合であり、各インデックスがちょうど一つの値を識別します。

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

ファイルとは任意のタプル $(f_m,d)$ であり、$d$ はワードの配列、$f_m : I \times \{d\} \to \mathrm{Array}$ はワードの配列で表されるメタデータ関数です。$I$ は有限で連続した整数インデックスの集合であり、$f_m$ は $d$ からデータがどのように解決されるかを決定します。

#### File(i)

> $(f_m,d)$ をファイルとします。
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

ストリームとは任意の関数 $f_s$ であり、$f_s$ を適用するたびに有限または無限の列における次のチャンク $c$ が得られ、$f_s$ が逐次的なデータ生成または取得の仕組みを定めます。

#### Stream()

> $f_c : K \to C$ をチャンク解決関数とし、$K \subseteq \mathbb{N}$ を連続した整数インデックスの集合、$C$ をチャンクの集合とします。
>
> $k \in K$ を次のチャンクのインデックスとします。
>
> $\mathrm{Stream}() = f_s() = f_c(k)$ とし、適用のたびに $k$ を進めます。

## 操作

### Instruction

命令とは任意のワードまたはワードの有限タプル $i \in B$ であり、$B$ はワードまたはワードの有限タプルの集合です。各命令は実行される単一の計算操作を表します。

### Procedure

手続きとは任意の変数 $f_{proc} : \{k\} \to B$ であり、$f_{proc}(k)$ は命令の配列 $f_a : I \to V$ を表します。手続きの実行は各命令をインデックス順に実行します。

#### Procedure(k)

> $\mathrm{Procedure}(k)$ は各 $f_a(i)$ を $i \in I$ の昇順で実行することです。

### Function

関数とは任意の手続き $f_{func} : \{k\} \to B$ であり、その実行は結果のワード、または結果を表すワード配列の先頭ワードを識別するアドレス $a_r \in A$ を返します。

#### Function(k)

> $f_m : A \to B$ をメモリマップとし、$a_r \in A$ は結果のワード $r \in B$ を識別するものとします。
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## スレッド処理

### Process

プロセスとは、入力を受け取り、一つ以上の手続きまたは関数を実行して出力を生成する任意の有界な実行の流れであり、システム内の独立した変換単位を表します。

### Thread

スレッドとは、プロセス内に含まれる任意の実行の流れであり、そのプロセスに属する手続きまたは関数を実行できる一つの経路を提供します。

#### Thread(p)

> $p$ をプロセスとします。
>
> $(w_0, \dots, w_n)$ を $p$ に属する手続きまたは関数の有限タプルとします。
>
> $\mathrm{Thread}(p)$ は各 $w_j$ を $j$ の昇順で $p$ 内で実行することです。

### Dispatcher

ディスパッチャーとは任意のタプル $(t,W,f_d)$ であり、$t$ はスレッド、$W$ は作業として受け付けられた手続きまたは関数の集合、$f_d$ は $W$ から作業を選択するディスパッチ規則です。ディスパッチャーは規則に従って選択された作業を $t$ 上で実行させます。

#### Dispatcher(t)

> $t$ をスレッドとします。
>
> $W$ をディスパッチャーが受け付ける手続きまたは関数の集合とし、$\forall w \in W$ について $w$ は手続きまたは関数とします。
>
> $f_d : \mathcal{P}^+(W) \to W$ を受け付けられた作業の空でない部分集合から作業を選択するディスパッチ規則とします。
>
> $\mathrm{Dispatcher}(t)$ は選択された各 $f_d(W')$ を $t$ 上で実行することであり、$W' \subseteq W$、$W' \neq \varnothing$、かつ $f_d(W') \in W'$ とします。

## 複合構造

### Member

メンバーとは任意の要素 $m \in M$ であり、$M$ は要素の集合、$f_o : K \to M$ はオブジェクトのメンバーマップであり、$m = f_o(k)$ があるキー $k \in K$ について成立します。

### Object

オブジェクトとは任意のタプル $(a,K,f_o)$ であり、$a \in A$ はアドレス、$K$ はキーの集合、$f_o : K \to M$ はメンバーマップ、$M$ は要素の集合です。これによりオブジェクトは、$f_o$ を通じてメンバーがキーに割り当てられる、アドレス指定可能な複合構造を表せます。

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

フィールドとは任意のタプル $(o,k,m)$ であり、$o = (a,K,f_o)$ はオブジェクト、$k \in K$ はキー、$m = f_o(k)$ はメンバーです。フィールドはオブジェクトのメンバーマップから解決されるキー付きメンバー一つを表します。

#### Field(o,k)

> $o = (a,K,f_o)$ をオブジェクトとします。
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

メソッドとは任意のフィールド $(o,k,m)$ であり、$m$ は手続きまたは関数です。メソッドはオブジェクトのキー付き実行可能メンバーを表します。

#### Method(o,k)

> $(o,k,m)$ をフィールドとします。
>
> $\mathrm{Method}(o,k) = (o,k,m)$、ただし $m$ は手続きまたは関数です。

### Property

プロパティとは任意のフィールド $(o,k,m)$ であり、$m = (X,f_a)$ はアクセサマップ、$X = \{\mathrm{Get}, \mathrm{Set}\}$ であり、$f_a : X \to M$ は各アクセサをメンバーに対応付けます。$f_a(\mathrm{Get})$ は関数、$f_a(\mathrm{Set})$ は手続きであり、プロパティはキー付きメンバーの取得と代入の両方の振る舞いを定義できます。

#### Property(o,k)

> $(o,k,m)$ をフィールドとし、$m = (X,f_a)$ をアクセサマップとします。
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> $(o,k,(X,f_a))$ をプロパティとします。
>
> $\mathrm{Get}(o,k)$ は $f_a(\mathrm{Get})$ の適用です。

#### Set(o,k)

> $(o,k,(X,f_a))$ をプロパティとします。
>
> $\mathrm{Set}(o,k)$ は $f_a(\mathrm{Set})$ の適用です。

### Structure

構造体（しばしば `struct` と略される）とは任意のオブジェクト $s = (a,K,f_s)$ であり、$K$ は有限のキー集合、$f_s : K \to M$ は構造体が割り当てられた後にキーを変更できないメンバーマップです。構造体はキー付きメンバーの配置が固定された特殊なオブジェクトです。

#### Structure(s,k)

> $s = (a,K,f_s)$ を構造体とします。
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

クラスとは任意のオブジェクト $c = (a_c,K_c,f_c)$ であり、$K_c$ は有限のキー集合、$f_c : K_c \to M$ はメンバー定義マップです。クラスは、キー付きメンバーが他のオブジェクトの生成に用いられるメンバー配置を定義する特殊なオブジェクトです。

#### Class(c,a)

> $c = (a_c,K_c,f_c)$ をクラスとします。
>
> $a \in A$ を $c$ から生成されたオブジェクトに割り当てられたアドレスとします。
>
> $f_o : K_c \to M$ を $f_c$ の定義に従うメンバーマップとします。
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

インターフェースとは任意のオブジェクト $r = (a_r,K_r,f_r)$ であり、$K_r$ は有限のキー集合、$f_r : K_r \to M$ はメンバー要件マップです。インターフェースは、キー付きメンバーが別のオブジェクトによって提供されるべきメンバーを定義する特殊なオブジェクトです。

#### Interface(r,o)

> $r = (a_r,K_r,f_r)$ をインターフェースとします。
>
> $o = (a,K,f_o)$ をオブジェクトとします。
>
> $f_v : M \times M \to \{0,1\}$ をあるメンバーが別のメンバーの要件を満たすかどうかを決定する検証規則とします。
>
> $\mathrm{Interface}(r,o)$ は $K_r \subseteq K$ かつ $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$ のとき成立します。
