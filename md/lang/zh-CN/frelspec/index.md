<!-- 此翻译由 ChatGPT 生成，应由人工译者审核。 -->
<!-- 翻译经验证后，请在拉取请求中删除这些行。 -->

# FRELSPEC

<br/>

> **基础关系规范**<br/>
> 修订版 2.1<br/>
> 2026年11月24日<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> 保留所有权利。<br/>
> <br/>
> 本文所述定义和概念描述基本数学构造，可以自由地重新表述。

## 引言

**基础关系规范（FRELSPEC）**确立了支撑 CatalystUI 生态系统的核心关系结构。其目的是在文档、规范、实现及验证审查中统一对内存、集合结构、操作和复合结构之间关系的理解，确保一致性、清晰性和协调性。

通过以精确且稳定的形式定义基础概念之间的关系，FRELSPEC 为更高层级的规范提供共同参照，同时允许各个实现制定自身的规则和行为。这使开发者、审查者和实现者能够从同一基础出发，判断语言、服务、框架或系统是否能够表示符合规范所需的关系构造。

> [!IMPORTANT]
>
> 我们使用一种由[集合论](https://en.wikipedia.org/wiki/Set_theory)记法衍生而来的记法表达定义。这种方法在保持清晰和简洁的同时，提供精确且无歧义的定义。我们对定义进行结构化组织，以便查阅、清晰理解并保持一致的概念层次。

## 目录

- [FRELSPEC](#frelspec)
  - [引言](#引言)
  - [目录](#目录)
  - [修订记录](#修订记录)
    - [修订版 2.1](#修订版-21)
    - [修订版 2](#修订版-2)
  - [内存](#内存)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [集合结构](#集合结构)
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
  - [线程机制](#线程机制)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [复合结构](#复合结构)
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

## 修订记录

### 修订版 2.1

**2026年11月24日**

我们完善了 File 的定义，以确立由元数据决定的数据解析方式，并将 Stream 重新定义为一种独立的顺序数据生成或检索机制。这些变更使流能够表示有限或无限序列，而无需对其他集合结构施加额外约束。

### 修订版 2

**2026年11月21日**

我们发现使用字节及字节数组表示内存和存储值时存在不一致之处。我们将 Word 确立为基础内存表示，统一了内存、操作和复合结构之间的关系。

我们发现数组索引及集合结构之间的关系存在不一致之处。我们统一了有限、连续索引的要求，并明确了 Array、File 和 Stream 之间的关系。

我们发现执行关系与复合关系中存在冗余和歧义。我们完善了过程、函数、调度器和对象关系，以解决这些问题并保持实现独立性。

## 内存

### Word

字是存储在内存中的任意位序列 $w \in \mathrm{Bit}^n$，满足 $n \in \mathbb{N}^+$。

### Address

地址是任意字 $a \in A$，其中 $A$ 是字的集合，且 $a$ 唯一标识指定内存结构中的一个位置。

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

指针是任意函数 $f_p : \{a\} \to B$，其中 $a \in A$ 是地址，$B$ 是字的集合；每次应用 $f_p$ 都会求得由 $a$ 标识的内存位置中存储的字。

#### Pointer()

> 设 $f_m : A \to B$ 为内存映射。
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

变量是任意函数 $f_v : \{k\} \to B$，其中 $k$ 是键，$B$ 是字的集合；变量通过将键绑定到地址并求得该地址存储的字来扩展指针。

#### Variable(k)

> 设 $f_b : \{k\} \to \{a\}$ 为变量的绑定函数。
>
> 设 $f_p : \{a\} \to B$ 为指针。
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

常量是任意变量 $f_c : \{k\} \to B$，其中 $k$ 是键，$B$ 是字的集合；与 $k$ 关联的字在赋值后不可更改。

#### Constant(k)

> 设 $b_0 \in B$ 为赋给 $k$ 的字。
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$，在 $b_0$ 被赋值之后。

## 集合结构

### Set

集合是由互不相同的字组成的任意有限、无序的集合结构。

#### Set()

> 设 $B$ 为字的集合。
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

映射是任意函数 $f_m : K \to V$，其中 $K$ 是键的集合，$V$ 是值的集合；每个键恰好关联一个值。

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

数组是任意函数 $f_a : I \to V$，其中 $I \subseteq \mathbb{N}$ 是有限、连续的整数索引集合，$V$ 是字的集合；每个索引恰好标识一个值。

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

文件是任意元组 $(f_m,d)$，其中 $d$ 是字数组，$f_m : I \times \{d\} \to \mathrm{Array}$ 是以字数组表示的元数据函数；$I$ 是有限、连续的整数索引集合，$f_m$ 决定如何从 $d$ 解析数据。

#### File(i)

> 设 $(f_m,d)$ 为文件。
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

流是任意函数 $f_s$，每次应用 $f_s$ 都产生有限或无限序列中的下一个数据块 $c$，其中 $f_s$ 建立顺序生成或检索数据的机制。

#### Stream()

> 设 $f_c : K \to C$ 为数据块解析函数，其中 $K \subseteq \mathbb{N}$ 是连续的整数索引集合，$C$ 是数据块的集合。
>
> 设 $k \in K$ 为下一个数据块的索引。
>
> $\mathrm{Stream}() = f_s() = f_c(k)$，每次应用后推进 $k$。

## 操作

### Instruction

指令是任意字或有限字元组 $i \in B$，其中 $B$ 是字或有限字元组的集合；每条指令表示一个待执行的计算操作。

### Procedure

过程是任意变量 $f_{proc} : \{k\} \to B$，其中 $f_{proc}(k)$ 表示指令数组 $f_a : I \to V$；执行该过程时，按照索引顺序执行每条指令。

#### Procedure(k)

> $\mathrm{Procedure}(k)$ 表示执行每个 $f_a(i)$，顺序为 $i \in I$ 的升序。

### Function

函数是任意过程 $f_{func} : \{k\} \to B$，执行该函数会返回地址 $a_r \in A$，该地址标识结果字或表示结果的字数组中的第一个字。

#### Function(k)

> 设 $f_m : A \to B$ 为内存映射，其中 $a_r \in A$ 标识结果字 $r \in B$。
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## 线程机制

### Process

进程是任意有界的执行流，它接受输入、执行一个或多个过程或函数并产生输出；进程表示系统中独立的转换单元。

### Thread

线程是进程中包含的任意执行流，它提供一条执行该进程所属过程或函数的路径。

#### Thread(p)

> 设 $p$ 为进程。
>
> 设 $(w_0, \dots, w_n)$ 为属于 $p$ 的过程或函数的有限元组。
>
> $\mathrm{Thread}(p)$ 表示执行每个 $w_j$，顺序为 $j$ 的升序，且执行发生在 $p$ 内。

### Dispatcher

调度器是任意元组 $(t,W,f_d)$，其中 $t$ 是线程，$W$ 是被接受为工作的过程或函数的集合，$f_d$ 是从 $W$ 中选择工作的调度规则；调度器依据该规则使选定工作在 $t$ 上执行。

#### Dispatcher(t)

> 设 $t$ 为线程。
>
> 设 $W$ 为调度器接受的过程或函数的集合，其中 $\forall w \in W$，$w$ 为过程或函数。
>
> 设 $f_d : \mathcal{P}^+(W) \to W$ 为从已接受工作的非空子集中选择工作的调度规则。
>
> $\mathrm{Dispatcher}(t)$ 表示将每个选定的 $f_d(W')$ 在 $t$ 上执行，其中 $W' \subseteq W$、$W' \neq \varnothing$ 且 $f_d(W') \in W'$。

## 复合结构

### Member

成员是任意元素 $m \in M$，其中 $M$ 是元素的集合，$f_o : K \to M$ 是对象的成员映射，且 $m = f_o(k)$ 对某个键 $k \in K$ 成立。

### Object

对象是任意元组 $(a,K,f_o)$，其中 $a \in A$ 是地址，$K$ 是键的集合，$f_o : K \to M$ 是成员映射，$M$ 是元素的集合；对象因此可表示可寻址的复合结构，其成员通过 $f_o$ 分配给键。

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

字段是任意元组 $(o,k,m)$，其中 $o = (a,K,f_o)$ 是对象，$k \in K$ 是键，$m = f_o(k)$ 是成员；字段表示从对象的成员映射中解析出的一个带键成员。

#### Field(o,k)

> 设 $o = (a,K,f_o)$ 为对象。
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

方法是任意字段 $(o,k,m)$，其中 $m$ 是过程或函数；方法表示对象的一个带键可执行成员。

#### Method(o,k)

> 设 $(o,k,m)$ 为字段。
>
> $\mathrm{Method}(o,k) = (o,k,m)$，其中 $m$ 是过程或函数。

### Property

属性是任意字段 $(o,k,m)$，其中 $m = (X,f_a)$ 是访问器映射，$X = \{\mathrm{Get}, \mathrm{Set}\}$，且 $f_a : X \to M$ 将各访问器映射到成员，其中 $f_a(\mathrm{Get})$ 是函数，$f_a(\mathrm{Set})$ 是过程；属性因而可定义带键成员的获取与赋值行为。

#### Property(o,k)

> 设 $(o,k,m)$ 为字段，其中 $m = (X,f_a)$ 为访问器映射。
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> 设 $(o,k,(X,f_a))$ 为属性。
>
> $\mathrm{Get}(o,k)$ 表示对 $f_a(\mathrm{Get})$ 的应用。

#### Set(o,k)

> 设 $(o,k,(X,f_a))$ 为属性。
>
> $\mathrm{Set}(o,k)$ 表示对 $f_a(\mathrm{Set})$ 的应用。

### Structure

结构（通常缩写为 `struct`）是任意对象 $s = (a,K,f_s)$，其中 $K$ 是有限的键集合，$f_s : K \to M$ 是成员映射，其键在结构被赋值后不可更改；结构是一种带键成员布局固定的专用对象。

#### Structure(s,k)

> 设 $s = (a,K,f_s)$ 为结构。
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

类是任意对象 $c = (a_c,K_c,f_c)$，其中 $K_c$ 是有限的键集合，$f_c : K_c \to M$ 是成员定义映射；类是一种专用对象，其带键成员定义用于生成其他对象的成员布局。

#### Class(c,a)

> 设 $c = (a_c,K_c,f_c)$ 为类。
>
> 设 $a \in A$ 为分配给由 $c$ 生成的对象的地址。
>
> 设 $f_o : K_c \to M$ 为遵循 $f_c$ 中定义的成员映射。
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

接口是任意对象 $r = (a_r,K_r,f_r)$，其中 $K_r$ 是有限的键集合，$f_r : K_r \to M$ 是成员要求映射；接口是一种专用对象，其带键成员定义另一对象必须提供的成员。

#### Interface(r,o)

> 设 $r = (a_r,K_r,f_r)$ 为接口。
>
> 设 $o = (a,K,f_o)$ 为对象。
>
> 设 $f_v : M \times M \to \{0,1\}$ 为验证规则，用于判断一个成员是否满足另一成员的要求。
>
> $\mathrm{Interface}(r,o)$ 成立，当 $K_r \subseteq K$ 且 $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$。
