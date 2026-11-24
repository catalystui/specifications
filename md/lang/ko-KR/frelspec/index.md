<!-- 이 번역은 ChatGPT에서 생성되었으며 사람 번역자의 검토가 필요합니다. -->
<!-- 번역이 검증된 후 풀 리퀘스트에서 이 줄들을 제거하십시오. -->

# FRELSPEC

<br/>

> **기초 관계 명세**<br/>
> 개정판 2.1<br/>
> 2026년 11월 24일<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> 모든 권리 보유.<br/>
> <br/>
> 여기에 제시된 정의와 개념은 기초 수학적 구성물을 설명하며 자유롭게 다시 표현할 수 있습니다.

## 소개

**기초 관계 명세(FRELSPEC)**는 CatalystUI 생태계의 기반이 되는 핵심 관계 구조를 확립합니다. 그 목적은 문서, 명세, 구현 및 검증 검토 전반에서 메모리, 컬렉션, 연산 및 복합 구조가 어떻게 연결되는지에 대한 통일된 이해를 제공하여 일관성, 명확성 및 정합성을 보장하는 것입니다.

기초 개념 사이의 관계를 정확하고 안정적인 형태로 정의함으로써 FRELSPEC은 상위 수준의 명세에 공통 참조점을 제공하는 동시에 개별 구현이 자체 규칙과 동작을 정할 수 있게 합니다. 이를 통해 개발자, 검토자 및 구현자는 언어, 서비스, 프레임워크 또는 시스템이 명세 준수에 필요한 관계적 구성물을 표현할 수 있는지 동일한 기반에서 판단할 수 있습니다.

> [!IMPORTANT]
>
> 정의는 [집합론](https://en.wikipedia.org/wiki/Set_theory) 표기법에서 파생된 형식으로 표현합니다. 이 접근법은 명확성과 간결성을 유지하면서 정확하고 모호하지 않은 정의를 제공합니다. 정의는 쉬운 참조, 명확한 해석 및 일관된 개념 계층을 지원하도록 구성합니다.

## 목차

- [FRELSPEC](#frelspec)
  - [소개](#소개)
  - [목차](#목차)
  - [개정 이력](#개정-이력)
    - [개정판 2.1](#개정판-21)
    - [개정판 2](#개정판-2)
  - [메모리](#메모리)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [컬렉션](#컬렉션)
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
  - [연산](#연산)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [스레딩](#스레딩)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [복합 구조](#복합-구조)
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

## 개정 이력

### 개정판 2.1

**2026년 11월 24일**

File의 정의를 정교화하여 메타데이터에 따른 데이터 해석을 확립하고 Stream을 순차적 데이터 생성 또는 검색의 독립적 메커니즘으로 재정의했습니다. 이러한 변경으로 스트림은 다른 컬렉션에 추가 제약을 부과하지 않고 유한 또는 무한 수열을 표현할 수 있습니다.

### 개정판 2

**2026년 11월 21일**

바이트 및 바이트 배열을 사용하여 메모리와 저장된 값을 표현하는 방식에서 불일치를 발견했습니다. Word를 기본 메모리 표현으로 확립하여 메모리, 연산 및 복합 구조 전반의 관계를 통일했습니다.

배열 인덱싱 및 컬렉션 간 관계에서 불일치를 발견했습니다. 유한하고 연속적인 인덱스를 표준화하고 Array, File 및 Stream 간의 관계를 명확히 했습니다.

실행 및 복합 관계에서 중복과 모호성을 발견했습니다. 구현 독립성을 유지하면서 프로시저, 함수, 디스패처 및 객체 관계를 정교화하여 이러한 문제를 해결했습니다.

## 메모리

### Word

워드는 메모리에 저장된 임의의 비트열 $w \in \mathrm{Bit}^n$이며, $n \in \mathbb{N}^+$를 만족합니다.

### Address

주소는 임의의 워드 $a \in A$이며, $A$는 워드의 집합이고 $a$는 지정된 메모리 구조 내의 위치를 고유하게 식별합니다.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

포인터는 임의의 함수 $f_p : \{a\} \to B$이며, $a \in A$는 주소이고 $B$는 워드의 집합입니다. $f_p$의 각 적용은 $a$가 식별하는 메모리 위치에 저장된 워드를 평가합니다.

#### Pointer()

> $f_m : A \to B$를 메모리 맵이라 합니다.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

변수는 임의의 함수 $f_v : \{k\} \to B$이며, $k$는 키이고 $B$는 워드의 집합입니다. 변수는 키를 주소에 바인딩하고 해당 주소에 저장된 워드를 평가하여 포인터를 확장합니다.

#### Variable(k)

> $f_b : \{k\} \to \{a\}$를 변수의 바인딩 함수라 합니다.
>
> $f_p : \{a\} \to B$를 포인터라 합니다.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

상수는 임의의 변수 $f_c : \{k\} \to B$이며, $k$는 키이고 $B$는 워드의 집합입니다. $k$에 연결된 워드는 할당된 후 변경할 수 없습니다.

#### Constant(k)

> $b_0 \in B$를 $k$에 할당된 워드라 합니다.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ ( $b_0$가 할당된 후).

## 컬렉션

### Set

집합은 서로 다른 워드로 이루어진 임의의 유한하고 순서가 없는 컬렉션입니다.

#### Set()

> $B$를 워드의 집합이라 합니다.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

맵은 임의의 함수 $f_m : K \to V$이며, $K$는 키의 집합이고 $V$는 값의 집합입니다. 각 키는 정확히 하나의 값에 연결됩니다.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

배열은 임의의 함수 $f_a : I \to V$이며, $I \subseteq \mathbb{N}$는 유한하고 연속적인 정수 인덱스의 집합이고 $V$는 워드의 집합입니다. 각 인덱스는 정확히 하나의 값을 식별합니다.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

파일은 임의의 튜플 $(f_m,d)$이며, $d$는 워드의 배열이고 $f_m : I \times \{d\} \to \mathrm{Array}$는 워드 배열로 표현되는 메타데이터 함수입니다. $I$는 유한하고 연속적인 정수 인덱스의 집합이며, $f_m$는 $d$에서 데이터를 해석하는 방식을 결정합니다.

#### File(i)

> $(f_m,d)$를 파일이라 합니다.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

스트림은 임의의 함수 $f_s$이며, $f_s$를 적용할 때마다 유한 또는 무한 수열의 다음 청크 $c$를 산출하고, $f_s$는 순차적 데이터 생성 또는 검색의 메커니즘을 확립합니다.

#### Stream()

> $f_c : K \to C$를 청크 해석 함수라 하며, $K \subseteq \mathbb{N}$는 연속적인 정수 인덱스의 집합이고 $C$는 청크의 집합입니다.
>
> $k \in K$를 다음 청크의 인덱스라 합니다.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$이며, 각 적용 후 $k$를 전진시킵니다.

## 연산

### Instruction

명령은 임의의 워드 또는 워드의 유한 튜플 $i \in B$이며, $B$는 워드 또는 워드의 유한 튜플의 집합입니다. 각 명령은 수행할 단일 계산 연산을 나타냅니다.

### Procedure

프로시저는 임의의 변수 $f_{proc} : \{k\} \to B$이며, $f_{proc}(k)$는 명령의 배열 $f_a : I \to V$를 나타냅니다. 프로시저를 실행하면 각 명령을 인덱스 순서대로 수행합니다.

#### Procedure(k)

> $\mathrm{Procedure}(k)$는 각 $f_a(i)$를 $i \in I$의 오름차순으로 실행하는 것입니다.

### Function

함수는 임의의 프로시저 $f_{func} : \{k\} \to B$이며, 함수를 실행하면 결과 워드 또는 결과를 나타내는 워드 배열의 첫 번째 워드를 식별하는 주소 $a_r \in A$를 반환합니다.

#### Function(k)

> $f_m : A \to B$를 메모리 맵이라 하며, $a_r \in A$는 결과 워드 $r \in B$를 식별합니다.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## 스레딩

### Process

프로세스는 입력을 받아 하나 이상의 프로시저 또는 함수를 실행하고 출력을 생성하는 임의의 범위가 한정된 실행 흐름이며, 시스템 내의 독립적인 변환 단위를 나타냅니다.

### Thread

스레드는 프로세스 내에 포함된 임의의 실행 흐름으로, 해당 프로세스에 속하는 프로시저 또는 함수가 실행될 수 있는 하나의 경로를 제공합니다.

#### Thread(p)

> $p$를 프로세스라 합니다.
>
> $(w_0, \dots, w_n)$를 $p$에 속하는 프로시저 또는 함수의 유한 튜플이라 합니다.
>
> $\mathrm{Thread}(p)$는 각 $w_j$를 $j$의 오름차순으로 $p$ 내에서 실행하는 것입니다.

### Dispatcher

디스패처는 임의의 튜플 $(t,W,f_d)$이며, $t$는 스레드, $W$는 작업으로 수락된 프로시저 또는 함수의 집합, $f_d$는 $W$에서 작업을 선택하는 디스패치 규칙입니다. 디스패처는 해당 규칙에 따라 선택된 작업이 $t$에서 실행되도록 합니다.

#### Dispatcher(t)

> $t$를 스레드라 합니다.
>
> $W$를 디스패처가 수락한 프로시저 또는 함수의 집합이라 하며, $\forall w \in W$에 대하여 $w$는 프로시저 또는 함수입니다.
>
> $f_d : \mathcal{P}^+(W) \to W$를 수락된 작업의 공집합이 아닌 부분집합에서 작업을 선택하는 디스패치 규칙이라 합니다.
>
> $\mathrm{Dispatcher}(t)$는 선택된 각 $f_d(W')$를 $t$에서 실행하는 것이며, $W' \subseteq W$, $W' \neq \varnothing$ 및 $f_d(W') \in W'$를 만족합니다.

## 복합 구조

### Member

멤버는 임의의 원소 $m \in M$이며, $M$는 원소의 집합이고 $f_o : K \to M$는 객체의 멤버 맵입니다. $m = f_o(k)$는 어떤 키 $k \in K$에 대하여 성립합니다.

### Object

객체는 임의의 튜플 $(a,K,f_o)$이며, $a \in A$는 주소, $K$는 키의 집합, $f_o : K \to M$는 멤버 맵이고 $M$는 원소의 집합입니다. 이를 통해 객체는 멤버가 $f_o$를 통해 키에 할당되는 주소 지정 가능한 복합 구조를 나타냅니다.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

필드는 임의의 튜플 $(o,k,m)$이며, $o = (a,K,f_o)$는 객체, $k \in K$는 키, $m = f_o(k)$는 멤버입니다. 필드는 객체의 멤버 맵에서 해석되는 하나의 키 지정 멤버를 나타냅니다.

#### Field(o,k)

> $o = (a,K,f_o)$를 객체라 합니다.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

메서드는 임의의 필드 $(o,k,m)$이며, $m$는 프로시저 또는 함수입니다. 메서드는 객체의 키 지정 실행 가능 멤버를 나타냅니다.

#### Method(o,k)

> $(o,k,m)$를 필드라 합니다.
>
> $\mathrm{Method}(o,k) = (o,k,m)$이며, $m$는 프로시저 또는 함수입니다.

### Property

속성은 임의의 필드 $(o,k,m)$이며, $m = (X,f_a)$는 접근자 맵, $X = \{\mathrm{Get}, \mathrm{Set}\}$이고, $f_a : X \to M$는 각 접근자를 멤버에 대응시킵니다. $f_a(\mathrm{Get})$는 함수이고 $f_a(\mathrm{Set})$는 프로시저이며, 속성은 키 지정 멤버의 검색과 할당 동작을 모두 정의할 수 있습니다.

#### Property(o,k)

> $(o,k,m)$를 필드라 하며, $m = (X,f_a)$는 접근자 맵입니다.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> $(o,k,(X,f_a))$를 속성이라 합니다.
>
> $\mathrm{Get}(o,k)$는 $f_a(\mathrm{Get})$의 적용입니다.

#### Set(o,k)

> $(o,k,(X,f_a))$를 속성이라 합니다.
>
> $\mathrm{Set}(o,k)$는 $f_a(\mathrm{Set})$의 적용입니다.

### Structure

구조체(흔히 `struct`로 줄여 씀)는 임의의 객체 $s = (a,K,f_s)$이며, $K$는 유한한 키의 집합이고 $f_s : K \to M$는 구조체가 할당된 후 키를 변경할 수 없는 멤버 맵입니다. 구조체는 키 지정 멤버의 배치가 고정된 특수 객체입니다.

#### Structure(s,k)

> $s = (a,K,f_s)$를 구조체라 합니다.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

클래스는 임의의 객체 $c = (a_c,K_c,f_c)$이며, $K_c$는 유한한 키의 집합이고 $f_c : K_c \to M$는 멤버 정의 맵입니다. 클래스는 키 지정 멤버가 다른 객체를 생성하는 데 사용되는 멤버 배치를 정의하는 특수 객체입니다.

#### Class(c,a)

> $c = (a_c,K_c,f_c)$를 클래스라 합니다.
>
> $a \in A$를 $c$에서 생성된 객체에 할당된 주소라 합니다.
>
> $f_o : K_c \to M$를 $f_c$의 정의를 따르는 멤버 맵이라 합니다.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

인터페이스는 임의의 객체 $r = (a_r,K_r,f_r)$이며, $K_r$는 유한한 키의 집합이고 $f_r : K_r \to M$는 멤버 요구 사항 맵입니다. 인터페이스는 키 지정 멤버가 다른 객체에서 제공해야 할 멤버를 정의하는 특수 객체입니다.

#### Interface(r,o)

> $r = (a_r,K_r,f_r)$를 인터페이스라 합니다.
>
> $o = (a,K,f_o)$를 객체라 합니다.
>
> $f_v : M \times M \to \{0,1\}$를 한 멤버가 다른 멤버의 요구 사항을 만족하는지 결정하는 검증 규칙이라 합니다.
>
> $\mathrm{Interface}(r,o)$는 $K_r \subseteq K$ 및 $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$일 때 성립합니다.
