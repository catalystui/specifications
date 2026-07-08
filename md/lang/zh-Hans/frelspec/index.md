<!-- 此翻译由 ChatGPT 生成，应由人工译者审核。 -->

# 在翻译经验证后，请在拉取请求中删除这些行。

# FRELSPEC

<br/>

> **基础关系规范**<br/>
> 修订版 1<br/>
> July 7th, 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> 保留所有权利。<br/>
> <br/>
> The definitions and concepts presented herein describe fundamental mathematical constructs and may be freely re-expressed.

## 引言

The **Foundational Relations Specification (FRELSPEC)** establishes the core relational structures that underpin the CatalystUI ecosystem. Its purpose is to provide a unified understanding of how values, memory, operations, and composites are associated across documentation, specifications, implementations, and verification reviews, ensuring consistency, clarity, and alignment.

By defining relationships between foundational concepts in a precise and stable form, FRELSPEC provides a common reference point for higher-level specifications. This allows developers, reviewers, and implementers to reason from the same foundation when determining whether a language, service, framework, or system can represent the relational constructs required to be considered within spec.

> [!IMPORTANT]
>
> We express definitions using a derived form of [set theory](https://en.wikipedia.org/wiki/Set_theory) notation. This approach provides precise, unambiguous definitions while maintaining clarity and conciseness. We structure these definitions to support easy reference, clear interpretation, and a consistent conceptual hierarchy.

## 目录

- [FRELSPEC](#frelspec)
  - [引言](#introduction)
  - [目录](#table-of-contents)
  - [集合](#collections)
    - [Set](#set)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [内存](#memory)
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
  - [线程](#threading)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [复合结构](#composites)
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

## 集合

### Set

集合（set）是任意由互异元素组成的集合体。

### Map

A map is any function $f_m : K \to V$ such that $K$ is a set of keys and $V$ is a set of values.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

An array is any function $f_a : I \to V$ such that $I \subset \mathbb{N}$, $I$ is a finite, contiguous set of integers, and $V$ is a set of values.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

A file is any function $f_f : I \to B$ such that $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ is a finite, contiguous set of integers and $b$ is a set of bytes, where $f_f$ originates from a mechanism of persistent data storage.

#### File(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Stream

A stream is any function $f_s$ such that each application of $f_s$ yields the next chunk $f_c : I \to B$ in a byte sequence, where $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ is a finite, contiguous set of integers, $B$ is a set of bytes, and $f_s$ originates from a mechanism of sequential data generation or retrieval.

#### Stream()

> Let $c_k : I_k \to B$ be the chunk returned by the $k$-th application of $f_s$.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ on the $k$-th application.

## 内存

### Address

地址（address）是任意元素 $a \in A$，其中 $A$ 是地址集合，并且每个地址 $a$ 都唯一标识内存结构中的一个位置。

### Pointer

A pointer is any function $f_p : \{a\} \to B$ such that $a \in A$ is an address and $B$ is a set of byte arrays, where each application of $f_p$ evaluates the byte array stored at the memory location identified by its bound address.

#### Pointer()

> Let $f_m : A \to B$ be a memory map.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

A variable is any function $f_v : \{k\} \to B$ such that $k$ is a key and $B$ is a set of byte arrays, where the variable extends a pointer by binding one key to one address and evaluating the byte array stored at the memory location identified by that address.

#### Variable(k)

> Let $f_b : \{k\} \to \{a\}$ be the variable’s binding function.
>
> Let $f_p : \{a\} \to B$ be a pointer.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

A constant is any variable $f_c : \{k\} \to B$ such that $k$ is a key and $B$ is a set of byte arrays, where the byte array associated with $k$ cannot be changed after it is assigned.

#### Constant(k)

> Let $b_0 \in B$ be the byte array assigned to $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ after $b_0$ is assigned.


## 操作

### Instruction

指令（instruction）是任意字节数组 $i \in B$，其中 $B$ 是字节数组集合，而每条指令表示要执行的单个计算操作。

### Procedure

A procedure is any variable $f_{proc} : \{k\} \to B$ such that $k$ is a key and $B$ is a set of byte arrays, where each application of the procedure evaluates the byte array associated with $k$ as a finite ordered sequence of instructions and executes those instructions in their represented order without defining a returned value.

#### Procedure(k)

> Let $b \in B$ such that $f_{proc}(k) = b$.
>
> Let $(i_0,\dots,i_n)$ be the finite ordered sequence of instructions represented by $b$, where $\forall j \in \{0,\dots,n\}, i_j$ is an instruction.
>
> $\mathrm{Procedure}(k)$ is the execution of each $i_j$ in ascending order of $j$.

### Function

A function is any procedure $f_{func} : \{k\} \to B$ such that $k$ is a key and $B$ is a set of byte arrays, where each application of the function evaluates the byte array associated with $k$ as a finite ordered sequence of instructions, executes those instructions in their represented order, and, after execution is completed, assigns a resulting byte array to some address in memory which may be evaluated as the function’s returned value.

#### Function(k)

> Let $b \in B$ such that $f_{func}(k) = b$.
>
> Let $(i_0,\dots,i_n)$ be the finite ordered sequence of instructions represented by $b$, where $\forall j \in \{0,\dots,n\}, i_j$ is an instruction.
>
> Let $a_r \in A$ be an address assigned after execution is completed.
>
> Let $f_m : A \to B$ be a memory map.
>
> $\mathrm{Function}(k)$ is the execution of each $i_j$ in ascending order of $j$, where $\exists b_r \in B : f_m(a_r) = b_r$ after execution is completed.
>
> $\mathrm{Function}(k) = b_r$

## 线程

### Process

进程（process）是任意有界执行流，它接收输入、执行一条或多条指令并产生输出；该进程表示系统中的一个独立变换单元。

### Thread

线程（thread）是包含在某个进程中的任意执行流；线程提供了一条路径，用于执行属于该进程的有序指令序列。

#### Thread(p)

> Let $p$ be a process.
>
> Let $(i_0,\dots,i_n)$ be a finite ordered sequence of instructions belonging to $p$.
>
> $\mathrm{Thread}(p)$ is the execution of each $i_j$ in ascending order of $j$ within $p$.

### Dispatcher

调度器（dispatcher）是任意元组 $(t,W,f_d)$，其中 $t$ 是一个线程，$W$ 是被接受为工作的过程或函数集合，$f_d$ 是从 $W$ 中选择工作的调度规则；调度器会根据该规则使被选中的工作在 $t$ 上执行。

#### Dispatcher(t)

> Let $t$ be a thread.
>
> Let $W$ be a set of procedures or functions accepted by the dispatcher, where $\forall w \in W$, $w$ is a procedure or function.
>
> Let $f_d : \mathcal{P}(W) \to W$ be a dispatch rule which selects work from a non-empty subset of accepted work.
>
> $\mathrm{Dispatcher}(t)$ is the execution of each selected $f_d(W')$ on $t$, where $W' \subseteq W$ and $W' \neq \varnothing$.

## 复合结构

### Member

成员（member）是任意元素 $m \in M$，其中 $M$ 是成员集合，而成员是可以被赋给对象成员映射中某个键的值。

### Object

An object is any tuple $(a,K,f_o)$ such that $a \in A$ is an address, $K$ is a set of keys, and $f_o : K \to M$ is a member map, where $M$ is a set of members, allowing the object to represent an addressable composite whose members are assigned to keys through $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

字段（field）是任意元组 $(o,k,m)$，其中 $o = (a,K,f_o)$ 是一个对象，$k \in K$ 是一个键，$m \in M$ 是一个成员，且 $f_o(k) = m$；字段表示从对象成员映射中解析出的一个键控成员。

#### Field(k)

> Let $o = (a,K,f_o)$ be an object.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Method

方法（method）是任意字段 $(o,k,m)$，其中 $m$ 是一个过程或函数；方法表示对象的一个可执行键控成员。

#### Method(k)

> Let $o = (a,K,f_o)$ be an object.
>
> Let $k \in K$ be a key.
>
> Let $m \in M$ be a member such that $f_o(k) = m$.
>
> $\mathrm{Method}(o,k) = (o,k,m)$ when $m$ is a procedure or function.

### Property

A property is any field $(o,k,m)$ such that $m = (A,f_a)$ is an accessor map, $A = \{ \mathrm{Get}, \mathrm{Set} \}$, and $f_a : A \to M$ maps each accessor to a member, where $f_a(\mathrm{Get})$ is a function and $f_a(\mathrm{Set})$ is a procedure, allowing the property to define both the retrieval and assignment behavior of a keyed member.

#### Property(k)

> Let $(o,k,m)$ be a field.
>
> Let $m = (A,f_a)$ be an accessor map.
>
> Let $A = \{ \mathrm{Get}, \mathrm{Set} \}$.
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$, where $g$ is a function.
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$, where $s$ is a procedure.
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> Let $(o,k,(A,f_a))$ be a property.
>
> Let $g = f_a(\mathrm{Get})$.
>
> $\mathrm{Get}(k)$ is the application of $g$.

#### Set(k)

> Let $(o,k,(A,f_a))$ be a property.
>
> Let $s = f_a(\mathrm{Set})$.
>
> $\mathrm{Set}(k)$ is the application of $s$.

### Structure

A structure (often abbreviated to `struct`) is any object $s = (a,K,f_s)$ such that $K$ is a finite set of keys and $f_s : K \to M$ is a member map which cannot be changed after the struct is assigned, where the struct is a specialized object whose keyed member layout is fixed.

#### Structure(k)

> Let $s = (a,K,f_s)$ be a structure.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

A class is any object $c = (a_c,K_c,f_c)$ such that $K_c$ is a finite set of keys and $f_c : K_c \to M$ is a member-definition map, where the class is a specialized object whose keyed members define the member layout used to produce other objects.

#### Class(a)

> Let $c = (a_c,K_c,f_c)$ be a class.
>
> Let $a \in A$ be an address assigned to an object produced from $c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interface

An interface is any object $r = (a_r,K_r,f_r)$ such that $K_r$ is a finite set of keys and $f_r : K_r \to M$ is a member-requirement map, where the interface is a specialized object whose keyed members define the members required to be provided by another object.

#### Interface(o)

> Let $r = (a_r,K_r,f_r)$ be an interface.
>
> Let $o = (a,K,f_o)$ be an object.
>
> $\mathrm{Interface}(r,o)$ holds when $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
