<!-- この翻訳は ChatGPT によって生成されたものであり、人間の翻訳者による確認が必要です。 -->
<!-- 翻訳が検証された後、プルリクエストでこれらの行を削除してください。 -->

# FRELSPEC

<br/>

> **基礎関係仕様**<br/>
> リビジョン 1<br/>
> 2026年7月7日<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/>
> <br/>
> ここに示される定義と概念は、基礎的な数学的構成を記述するものであり、自由に再表現できます。

## はじめに

**Foundational Relations Specification (FRELSPEC)** は、CatalystUI エコシステムを支える中核的な関係構造を確立します。その目的は、値、メモリ、操作、複合体がドキュメント、仕様、実装、検証レビュー全体でどのように関連付けられるかについて統一された理解を提供し、一貫性、明確さ、整合性を確保することです。

基礎概念間の関係を正確で安定した形で定義することにより、FRELSPEC は上位仕様の共通参照点を提供します。これにより、開発者、レビュー担当者、実装者は、言語、サービス、フレームワーク、システムが within spec と見なされるために必要な関係構造を表現できるかどうかを判断する際に、同じ土台から推論できます。

> [!IMPORTANT]
>
> 定義は [set theory](https://en.wikipedia.org/wiki/Set_theory) 記法から派生した形式で表現します。この手法は、明確さと簡潔さを保ちながら、正確で曖昧さのない定義を提供します。これらの定義は、参照しやすく、解釈しやすく、一貫した概念階層を支えるように構成されています。

## 目次

- [FRELSPEC](#frelspec)
  - [はじめに](#introduction)
  - [目次](#table-of-contents)
  - [コレクション](#collections)
    - [Set](#set)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [メモリ](#memory)
    - [Address](#address)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [操作](#operations)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [スレッド処理](#threading)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [複合体](#composites)
    - [Member](#member)
    - [Object](#object)
      - [Object(k)](#objectk)
    - [Field](#field)
      - [Field(k)](#fieldk)
    - [Method](#method)
      - [Method(k)](#methodk)
    - [Property](#property)
      - [Property(k)](#propertyk)
      - [Get(k)](#getk)
      - [Set(k)](#setk)
    - [Structure](#structure)
      - [Structure(k)](#structurek)
    - [Class](#class)
      - [Class(a)](#classa)
    - [Interface](#interface)
      - [Interface(o)](#interfaceo)

## コレクション

### Set

set は、重複しない要素の任意の collection です。

### Map

map は任意の function $f_m : K \to V$ であり、$K$ が keys の set、$V$ が values の set であるものです。

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

array は任意の function $f_a : I \to V$ であり、$I \subset \mathbb{N}$、$I$ が有限で連続した integers の set、$V$ が values の set であるものです。

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

file は任意の function $f_f : I \to B$ であり、$I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ が有限で連続した integers の set、$b$ が bytes の set であり、$f_f$ が永続的 data storage の仕組みに由来するものです。

#### File(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Stream

stream は任意の function $f_s$ であり、$f_s$ を適用するたびに byte sequence 内の次の chunk $f_c : I \to B$ を生成するものです。ここで $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ は有限で連続した integers の set、$B$ は bytes の set、$f_s$ は sequential data generation または retrieval の仕組みに由来します。

#### Stream()

> $c_k : I_k \to B$ を、$f_s$ の $k$ 番目の適用によって返される chunk とします。
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ on the $k\text{-th}$ application.

## メモリ

### Address

address は任意の element $a \in A$ であり、$A$ が addresses の set で、各 address $a$ が memory structure 内の location を一意に識別するものです。

### Pointer

pointer は任意の function $f_p : \{a\} \to B$ であり、$a \in A$ が address、$B$ が byte arrays の set で、$f_p$ を適用するたびに、その束縛された address によって識別される memory location に格納された byte array を評価するものです。

#### Pointer()

> $f_m : A \to B$ を memory map とします。
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

variable は任意の function $f_v : \{k\} \to B$ であり、$k$ が key、$B$ が byte arrays の set で、variable が一つの key を一つの address に束縛し、その address によって識別される memory location に格納された byte array を評価することで pointer を拡張するものです。

#### Variable(k)

> $f_b : \{k\} \to \{a\}$ を variable の binding function とします。
>
> $f_p : \{a\} \to B$ を pointer とします。
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

constant は任意の variable $f_c : \{k\} \to B$ であり、$k$ が key、$B$ が byte arrays の set で、$k$ に関連付けられた byte array が割り当て後に変更できないものです。

#### Constant(k)

> $b_0 \in B$ を $k$ に割り当てられた byte array とします。
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ after $b_0$ is assigned.


## 操作

### Instruction

instruction は任意の bytes の array $i \in B$ であり、$B$ が byte arrays の set で、各 instruction が実行される単一の computational operation を表すものです。

### Procedure

procedure は任意の variable $f_{proc} : \{k\} \to B$ であり、$k$ が key、$B$ が byte arrays の set であるものです。procedure を適用するたびに、$k$ に関連付けられた byte array を finite ordered sequence of instructions として評価し、それらの instructions を表現された順序で実行しますが、returned value は定義しません。

#### Procedure(k)

> $b \in B$ such that $f_{proc}(k) = b$. とします。
>
> $(i_0,\dots,i_n)$ を、$b$ によって表される finite ordered sequence of instructions とします。ここで $\forall j \in \{0,\dots,n\}, i_j$ は instruction です。
>
> $\mathrm{Procedure}(k)$ は、各 $i_j$ を $j$ の昇順で実行することです。

### Function

function は任意の procedure $f_{func} : \{k\} \to B$ であり、$k$ が key、$B$ が byte arrays の set であるものです。function を適用するたびに、$k$ に関連付けられた byte array を finite ordered sequence of instructions として評価し、それらの instructions を表現された順序で実行し、実行完了後に resulting byte array を memory 内の何らかの address に割り当てます。この値は function の returned value として評価できます。

#### Function(k)

> $b \in B$ such that $f_{func}(k) = b$. とします。
>
> $(i_0,\dots,i_n)$ を、$b$ によって表される finite ordered sequence of instructions とします。ここで $\forall j \in \{0,\dots,n\}, i_j$ は instruction です。
>
> $a_r \in A$ を実行完了後に割り当てられる address とします。
>
> $f_m : A \to B$ を memory map とします。
>
> $\mathrm{Function}(k)$ は、各 $i_j$ を $j$ の昇順で実行することです。ここで、実行完了後に $\exists b_r \in B : f_m(a_r) = b_r$ となります。
>
> $\mathrm{Function}(k) = b_r$

## スレッド処理

### Process

process は、input を受け取り、一つ以上の instructions を実行し、output を生成する、任意の bounded flow of execution です。process は system 内の distinct unit of transformation を表します。

### Thread

thread は process 内に含まれる任意の flow of execution であり、その process に属する ordered sequences of instructions を実行できる一つの path を提供します。

#### Thread(p)

> $p$ を process とします。
>
> $(i_0,\dots,i_n)$ を、$p$ に属する有限の ordered sequence of instructions とします。
>
> $\mathrm{Thread}(p)$ は、$p$ の内部で各 $i_j$ を $j$ の昇順で実行することです。

### Dispatcher

dispatcher は任意の tuple $(t,W,f_d)$ であり、$t$ が thread、$W$ が work として受け付けられる procedures または functions の set、$f_d$ が $W$ から work を選択する dispatch rule であり、dispatcher はその dispatch rule に従って選択された work を $t$ 上で実行させます。

#### Dispatcher(t)

> $t$ を thread とします。
>
> $W$ を dispatcher が受け付ける procedures または functions の set とします。ここで $\forall w \in W$, $w$ は procedure または function です。
>
> $f_d : \mathcal{P}(W) \to W$ を、受け付けられた work の空でない subset から work を選択する dispatch rule とします。
>
> $\mathrm{Dispatcher}(t)$ は、選択された各 $f_d(W')$ を $t$ 上で実行することです。ここで $W' \subseteq W$ かつ $W' \neq \varnothing$ です。

## 複合体

### Member

member は任意の element $m \in M$ であり、$M$ が members の set で、member が object の member map 内で key に割り当てられる可能性のある value であるものです。

### Object

object は任意の tuple $(a,K,f_o)$ であり、$a \in A$ が address、$K$ が keys の set、$f_o : K \to M$ が member map で、$M$ が members の set であるものです。これにより object は、members が $f_o$ を通じて keys に割り当てられる addressable composite を表現できます。

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

field は任意の tuple $(o,k,m)$ であり、$o = (a,K,f_o)$ が object、$k \in K$ が key、$m \in M$ が member、$f_o(k) = m$ であるものです。field は object の member map から解決された一つの keyed member を表します。

#### Field(k)

> $o = (a,K,f_o)$ を object とします。
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Method

method は任意の field $(o,k,m)$ であり、$m$ が procedure または function で、method が object の keyed executable member を表すものです。

#### Method(k)

> $o = (a,K,f_o)$ を object とします。
>
> $k \in K$ を key とします。
>
> $m \in M$ be a member such that $f_o(k) = m$. とします。
>
> $\mathrm{Method}(o,k) = (o,k,m)$ when $m$ is a procedure or function.

### Property

property は任意の field $(o,k,m)$ であり、$m = (A,f_a)$ が accessor map、$A = \{ \mathrm{Get}, \mathrm{Set} \}$、$f_a : A \to M$ が各 accessor を member に map するものです。ここで $f_a(\mathrm{Get})$ は function、$f_a(\mathrm{Set})$ は procedure であり、property は keyed member の retrieval behavior と assignment behavior の両方を定義できます。

#### Property(k)

> $(o,k,m)$ be a field. とします。
>
> $m = (A,f_a)$ be an accessor map. とします。
>
> $A = \{ \mathrm{Get}, \mathrm{Set} \}$. とします。
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$。ここで $g$ は function です。
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$。ここで $s$ は procedure です。
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> $(o,k,(A,f_a))$ be a property. とします。
>
> $g = f_a(\mathrm{Get})$. とします。
>
> $\mathrm{Get}(k)$ は $g$ の適用です。

#### Set(k)

> $(o,k,(A,f_a))$ be a property. とします。
>
> $s = f_a(\mathrm{Set})$. とします。
>
> $\mathrm{Set}(k)$ は $s$ の適用です。

### Structure

structure（しばしば `struct` と略されます）は任意の object $s = (a,K,f_s)$ であり、$K$ が keys の有限集合、$f_s : K \to M$ が struct の割り当て後に変更できない member map で、struct が keyed member layout の固定された特殊な object であるものです。

#### Structure(k)

> $s = (a,K,f_s)$ be structure. とします。
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

class は任意の object $c = (a_c,K_c,f_c)$ であり、$K_c$ が keys の有限集合、$f_c : K_c \to M$ が member-definition map で、class が他の objects を生成するために使われる member layout を keyed members によって定義する特殊な object であるものです。

#### Class(a)

> $c = (a_c,K_c,f_c)$ be a class. とします。
>
> $a \in A$ be an address assigned to an object produced from $c$. とします。
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interface

interface は任意の object $r = (a_r,K_r,f_r)$ であり、$K_r$ が keys の有限集合、$f_r : K_r \to M$ が member-requirement map で、interface が別の object によって提供される必要のある members を keyed members によって定義する特殊な object であるものです。

#### Interface(o)

> $r = (a_r,K_r,f_r)$ be an interface. とします。
>
> $o = (a,K,f_o)$ を object とします。
>
> $\mathrm{Interface}(r,o)$ holds when $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
