<!-- 이 번역은 ChatGPT가 생성한 것이며 인간 번역자의 검토가 필요합니다. -->
<!-- 번역이 확인된 후 pull request에서 이 줄들을 제거하십시오. -->

# FRELSPEC

<br/>

> **기초 관계 사양**<br/>
> 개정 1<br/>
> 2026년 7월 7일<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/>
> <br/>
> 여기에 제시된 정의와 개념은 기초적인 수학적 구성 요소를 설명하며 자유롭게 다시 표현될 수 있습니다.

## 소개

**Foundational Relations Specification (FRELSPEC)**은 CatalystUI 생태계를 뒷받침하는 핵심 관계 구조를 확립합니다. 그 목적은 문서, 사양, 구현, 검증 검토 전반에서 값, 메모리, 연산, 복합체가 어떻게 연결되는지에 대한 통일된 이해를 제공하여 일관성, 명확성, 정렬성을 보장하는 것입니다.

기초 개념 사이의 관계를 정확하고 안정적인 형식으로 정의함으로써 FRELSPEC은 더 높은 수준의 사양을 위한 공통 기준점을 제공합니다. 이를 통해 개발자, 검토자, 구현자는 언어, 서비스, 프레임워크 또는 시스템이 within spec으로 간주되기 위해 필요한 관계 구성 요소를 표현할 수 있는지 판단할 때 같은 기반에서 추론할 수 있습니다.

> [!IMPORTANT]
>
> 우리는 [집합론](https://en.wikipedia.org/wiki/Set_theory) 표기법에서 파생된 형식을 사용하여 정의를 표현합니다. 이 방식은 명확성과 간결성을 유지하면서 정확하고 모호하지 않은 정의를 제공합니다. 이러한 정의는 쉬운 참조, 명확한 해석, 일관된 개념 계층을 지원하도록 구성됩니다.

## 목차

- [FRELSPEC](#frelspec)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Collections](#collections)
    - [Set](#set)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [Memory](#memory)
    - [Address](#address)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Operations](#operations)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [Threading](#threading)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Composites](#composites)
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

## 컬렉션

### Set

set은 서로 구별되는 element들의 임의의 collection입니다.

### Map

map은 $K$가 key의 set이고 $V$가 value의 set인 임의의 function $f_m : K \to V$입니다.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

array는 $I \subset \mathbb{N}$이고, $I$가 유한하고 연속적인 integer의 set이며, $V$가 value의 set인 임의의 function $f_a : I \to V$입니다.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

file은 $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$가 유한하고 연속적인 integer의 set이고 $b$가 byte의 set이며, $f_f$가 persistent data storage 메커니즘에서 비롯되는 임의의 function $f_f : I \to B$입니다.

#### File(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Stream

stream은 $f_s$를 적용할 때마다 byte sequence 안의 다음 chunk $f_c : I \to B$를 산출하는 임의의 function $f_s$입니다. 여기서 $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$는 유한하고 연속적인 integer의 set이고, $B$는 byte의 set이며, $f_s$는 sequential data generation 또는 retrieval 메커니즘에서 비롯됩니다.

#### Stream()

> $c_k : I_k \to B$를 the chunk returned by the $k\text{-th}$ application of $f_s$라고 합니다.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$이며, 이는 $k$번째 적용에서 성립합니다.

## 메모리

### Address

address는 $A$가 address의 set이고 각 address $a$가 memory structure 안의 location을 고유하게 식별하는 임의의 element $a \in A$입니다.

### Pointer

pointer는 $a \in A$가 address이고 $B$가 byte array의 set인 임의의 function $f_p : \{a\} \to B$입니다. $f_p$를 적용할 때마다 bound address가 식별하는 memory location에 저장된 byte array를 평가합니다.

#### Pointer()

> $f_m : A \to B$를 memory map이라고 합니다.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

variable은 $k$가 key이고 $B$가 byte array의 set인 임의의 function $f_v : \{k\} \to B$입니다. variable은 하나의 key를 하나의 address에 binding하고 그 address가 식별하는 memory location에 저장된 byte array를 평가함으로써 pointer를 확장합니다.

#### Variable(k)

> $f_b : \{k\} \to \{a\}$를 the variable’s binding function라고 합니다.
>
> $f_p : \{a\} \to B$를 pointer라고 합니다.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

constant는 $k$가 key이고 $B$가 byte array의 set이며, $k$와 연결된 byte array가 할당된 후 변경될 수 없는 임의의 variable $f_c : \{k\} \to B$입니다.

#### Constant(k)

> $b_0 \in B$를 the byte array assigned to $k$라고 합니다.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$이며, 이는 $b_0$가 할당된 후 성립합니다.


## 연산

### Instruction

instruction은 $B$가 byte array의 set이고 각 instruction이 수행될 하나의 computational operation을 나타내는 임의의 byte array $i \in B$입니다.

### Procedure

procedure는 $k$가 key이고 $B$가 byte array의 set인 임의의 variable $f_{proc} : \{k\} \to B$입니다. procedure를 적용할 때마다 $k$와 연결된 byte array를 instructions의 유한한 ordered sequence로 평가하고, 반환 값을 정의하지 않은 채 그 instructions를 표현된 순서대로 실행합니다.

#### Procedure(k)

> $f_{proc}(k) = b$를 만족하는 $b \in B$라고 합니다.
>
> $(i_0,\dots,i_n)$을 $b$가 표현하는 instructions의 유한한 ordered sequence라고 합니다. 여기서 모든 $j \in \{0,\dots,n\}$에 대해 $i_j$는 instruction입니다.
>
> $\mathrm{Procedure}(k)$는 각 $i_j$를 $j$의 오름차순으로 실행하는 것입니다.

### Function

function은 $k$가 key이고 $B$가 byte array의 set인 임의의 procedure $f_{func} : \{k\} \to B$입니다. function을 적용할 때마다 $k$와 연결된 byte array를 instructions의 유한한 ordered sequence로 평가하고, 그 instructions를 표현된 순서대로 실행한 뒤, 실행이 완료되면 function의 반환 값으로 평가될 수 있는 resulting byte array를 memory의 어떤 address에 할당합니다.

#### Function(k)

> $f_{func}(k) = b$를 만족하는 $b \in B$라고 합니다.
>
> $(i_0,\dots,i_n)$을 $b$가 표현하는 instructions의 유한한 ordered sequence라고 합니다. 여기서 모든 $j \in \{0,\dots,n\}$에 대해 $i_j$는 instruction입니다.
>
> $a_r \in A$를 실행 완료 후 할당된 address라고 합니다.
>
> $f_m : A \to B$를 memory map이라고 합니다.
>
> $\mathrm{Function}(k)$는 각 $i_j$를 $j$의 오름차순으로 실행하는 것입니다. 실행이 완료된 후 $\exists b_r \in B : f_m(a_r) = b_r$가 성립합니다.
>
> $\mathrm{Function}(k) = b_r$

## 스레딩

### Process

process는 input을 받아 하나 이상의 instruction을 실행하고 output을 생성하는 임의의 bounded flow of execution입니다. 여기서 process는 system 안의 구별되는 transformation 단위를 나타냅니다.

### Thread

thread는 process 안에 포함된 임의의 flow of execution이며, 해당 process에 속한 instructions의 ordered sequence가 실행될 수 있는 하나의 path를 제공합니다.

#### Thread(p)

> $p$를 process라고 합니다.
>
> $(i_0,\dots,i_n)$을 $p$에 속한 instructions의 유한한 ordered sequence라고 합니다.
>
> $\mathrm{Thread}(p)$는 $p$ 안에서 각 $i_j$를 $j$의 오름차순으로 실행하는 것입니다.

### Dispatcher

dispatcher는 $t$가 thread이고, $W$가 work로 받아들여지는 procedure 또는 function의 set이며, $f_d$가 $W$에서 work를 선택하는 dispatch rule인 임의의 tuple $(t,W,f_d)$입니다. dispatcher는 dispatch rule에 따라 선택된 work가 $t$에서 실행되도록 합니다.

#### Dispatcher(t)

> $t$를 thread라고 합니다.
>
> $W$를 dispatcher가 받아들이는 procedure 또는 function의 set이라고 합니다. 여기서 모든 $w \in W$에 대해 $w$는 procedure 또는 function입니다.
>
> $f_d : \mathcal{P}(W) \to W$를 accepted work의 비어 있지 않은 subset에서 work를 선택하는 dispatch rule이라고 합니다.
>
> $\mathrm{Dispatcher}(t)$는 선택된 각 $f_d(W')$를 $t$에서 실행하는 것입니다. 여기서 $W' \subseteq W$이고 $W' \neq \varnothing$입니다.

## 복합체

### Member

member는 $M$이 member의 set이고, member가 object의 member map 안에서 key에 할당될 수 있는 value인 임의의 element $m \in M$입니다.

### Object

object는 $a \in A$가 address이고, $K$가 key의 set이며, $f_o : K \to M$이 member map이고, $M$이 member의 set인 임의의 tuple $(a,K,f_o)$입니다. 이를 통해 object는 member가 $f_o$를 통해 key에 할당되는 addressable composite를 나타낼 수 있습니다.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

field는 $o = (a,K,f_o)$가 object이고, $k \in K$가 key이며, $m \in M$이 member이고, $f_o(k) = m$인 임의의 tuple $(o,k,m)$입니다. field는 object의 member map에서 해석된 하나의 keyed member를 나타냅니다.

#### Field(k)

> $o = (a,K,f_o)$를 object라고 합니다.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Method

method는 $m$이 procedure 또는 function인 임의의 field $(o,k,m)$입니다. method는 object의 keyed executable member를 나타냅니다.

#### Method(k)

> $o = (a,K,f_o)$를 object라고 합니다.
>
> $k \in K$를 key라고 합니다.
>
> $m \in M$를 $f_o(k) = m$을 만족하는 member라고 합니다.
>
> $m$이 procedure 또는 function인 경우 $\mathrm{Method}(o,k) = (o,k,m)$입니다.

### Property

property는 $m = (A,f_a)$가 accessor map이고, $A = \{ \mathrm{Get}, \mathrm{Set} \}$이며, $f_a : A \to M$이 각 accessor를 member에 mapping하는 임의의 field $(o,k,m)$입니다. 여기서 $f_a(\mathrm{Get})$은 function이고 $f_a(\mathrm{Set})$은 procedure이므로, property는 keyed member의 retrieval 및 assignment behavior를 모두 정의할 수 있습니다.

#### Property(k)

> $(o,k,m)$를 field라고 합니다.
>
> $m = (A,f_a)$를 accessor map이라고 합니다.
>
> $A = \{ \mathrm{Get}, \mathrm{Set} \}$라고 합니다.
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$이며, 여기서 $g$는 function입니다.
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$이며, 여기서 $s$는 procedure입니다.
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> $(o,k,(A,f_a))$를 property라고 합니다.
>
> $g = f_a(\mathrm{Get})$라고 합니다.
>
> $\mathrm{Get}(k)$는 $g$를 적용한 것입니다.

#### Set(k)

> $(o,k,(A,f_a))$를 property라고 합니다.
>
> $s = f_a(\mathrm{Set})$라고 합니다.
>
> $\mathrm{Set}(k)$는 $s$를 적용한 것입니다.

### Structure

structure(흔히 `struct`로 줄여 부름)는 $K$가 유한한 key의 set이고, $f_s : K \to M$이 struct가 할당된 후 변경될 수 없는 member map인 임의의 object $s = (a,K,f_s)$입니다. 여기서 struct는 keyed member layout이 고정된 specialized object입니다.

#### Structure(k)

> $s = (a,K,f_s)$를 structure라고 합니다.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

class는 $K_c$가 유한한 key의 set이고, $f_c : K_c \to M$이 member-definition map인 임의의 object $c = (a_c,K_c,f_c)$입니다. class는 다른 object를 생성하는 데 사용되는 member layout을 keyed member가 정의하는 specialized object입니다.

#### Class(a)

> $c = (a_c,K_c,f_c)$를 class라고 합니다.
>
> $a \in A$를 $c$에서 생성된 object에 할당된 address라고 합니다.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interface

interface는 $K_r$가 유한한 key의 set이고, $f_r : K_r \to M$이 member-requirement map인 임의의 object $r = (a_r,K_r,f_r)$입니다. interface는 다른 object가 제공해야 하는 member를 keyed member가 정의하는 specialized object입니다.

#### Interface(o)

> $r = (a_r,K_r,f_r)$를 interface라고 합니다.
>
> $o = (a,K,f_o)$를 object라고 합니다.
>
> $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$일 때 $\mathrm{Interface}(r,o)$가 성립합니다.
