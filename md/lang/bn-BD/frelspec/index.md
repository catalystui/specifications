<!-- এই অনুবাদটি ChatGPT দ্বারা তৈরি করা হয়েছে এবং একজন মানব অনুবাদকের দ্বারা পর্যালোচনা করা উচিত। -->
<!-- অনুবাদটি যাচাই হওয়ার পরে একটি pull request-এ এই লাইনগুলো সরিয়ে ফেলুন। -->

# FRELSPEC

<br/>

> **ভিত্তিগত সম্পর্ক নির্দিষ্টকরণ**<br/>
> Revision 1<br/>
> July 7th, 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/>
> <br/>
> এখানে উপস্থাপিত সংজ্ঞা ও ধারণাগুলি ভিত্তিগত গাণিতিক গঠন বর্ণনা করে এবং এগুলি স্বাধীনভাবে পুনরায় প্রকাশ করা যেতে পারে।

## ভূমিকা

**Foundational Relations Specification (FRELSPEC)** CatalystUI ইকোসিস্টেমের ভিত্তি হিসেবে থাকা core relational structures প্রতিষ্ঠা করে। এর উদ্দেশ্য হলো values, memory, operations, এবং composites কীভাবে documentation, specifications, implementations, এবং verification reviews জুড়ে সম্পর্কিত থাকে সে বিষয়ে একটি একীভূত বোঝাপড়া প্রদান করা, যাতে consistency, clarity, এবং alignment বজায় থাকে।

ভিত্তিগত concepts-এর মধ্যে সম্পর্কগুলি নির্ভুল এবং স্থিতিশীল আকারে সংজ্ঞায়িত করার মাধ্যমে, FRELSPEC উচ্চতর স্তরের specifications-এর জন্য একটি সাধারণ reference point প্রদান করে। এর ফলে developer, reviewer, এবং implementer-রা একই foundation থেকে বিচার করতে পারেন যে কোনো language, service, framework, বা system spec-এর মধ্যে বিবেচিত হওয়ার জন্য প্রয়োজনীয় relational constructs represent করতে পারে কি না।

> [!IMPORTANT]
>
> আমরা [set theory](https://en.wikipedia.org/wiki/Set_theory) notation-এর একটি derived form ব্যবহার করে definitions প্রকাশ করি। এই পদ্ধতি clarity এবং conciseness বজায় রেখে precise, unambiguous definitions প্রদান করে। আমরা এই definitions সাজাই যাতে easy reference, clear interpretation, এবং consistent conceptual hierarchy সমর্থিত হয়।

## সূচিপত্র

- [FRELSPEC](#frelspec)
  - [ভূমিকা](#ভূমিকা)
  - [সূচিপত্র](#সূচিপত্র)
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

## Collections

### Set

একটি set হলো distinct elements-এর যেকোনো collection।

### Map

একটি map হলো যেকোনো function $f_m : K \to V$, যেখানে $K$ হলো keys-এর একটি set এবং $V$ হলো values-এর একটি set।

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

একটি array হলো যেকোনো function $f_a : I \to V$, যেখানে $I \subset \mathbb{N}$, $I$ হলো integers-এর একটি finite, contiguous set, এবং $V$ হলো values-এর একটি set।

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

একটি file হলো যেকোনো function $f_f : I \to B$, যেখানে $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ হলো integers-এর একটি finite, contiguous set এবং $B$ হলো bytes-এর একটি set, এবং $f_f$ persistent data storage-এর একটি mechanism থেকে originate করে।

#### File(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Stream

একটি stream হলো যেকোনো function $f_s$, যেখানে $f_s$-এর প্রতিটি application byte sequence-এর পরবর্তী chunk $f_c : I \to B$ yield করে; এখানে $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ হলো integers-এর একটি finite, contiguous set, $B$ হলো bytes-এর একটি set, এবং $f_s$ sequential data generation বা retrieval-এর একটি mechanism থেকে originate করে।

#### Stream()

> Let $c_k : I_k \to B$ be the chunk returned by the $k$-th application of $f_s$.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ on the $k$-th application.

## Memory

### Address

একটি address হলো যেকোনো element $a \in A$, যেখানে $A$ হলো addresses-এর একটি set, এবং প্রতিটি address $a$ memory structure-এর একটি location-কে uniquely identify করে।

### Pointer

একটি pointer হলো যেকোনো function $f_p : \{a\} \to B$, যেখানে $a \in A$ একটি address এবং $B$ হলো byte arrays-এর একটি set; $f_p$-এর প্রতিটি application তার bound address দ্বারা identified memory location-এ stored byte array evaluate করে।

#### Pointer()

> Let $f_m : A \to B$ be a memory map.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

একটি variable হলো যেকোনো function $f_v : \{k\} \to B$, যেখানে $k$ একটি key এবং $B$ হলো byte arrays-এর একটি set; variable একটি key-কে একটি address-এর সঙ্গে bind করে এবং সেই address দ্বারা identified memory location-এ stored byte array evaluate করে pointer-কে extend করে।

#### Variable(k)

> Let $f_b : \{k\} \to \{a\}$ be the variable’s binding function.
>
> Let $f_p : \{a\} \to B$ be a pointer.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

একটি constant হলো যেকোনো variable $f_c : \{k\} \to B$, যেখানে $k$ একটি key এবং $B$ হলো byte arrays-এর একটি set; $k$-এর সঙ্গে associated byte array assign হওয়ার পরে আর পরিবর্তন করা যায় না।

#### Constant(k)

> Let $b_0 \in B$ be the byte array assigned to $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ after $b_0$ is assigned.

## Operations

### Instruction

একটি instruction হলো যেকোনো array of bytes $i \in B$, যেখানে $B$ হলো byte arrays-এর একটি set; প্রতিটি instruction সম্পাদনের জন্য একটি single computational operation represent করে।

### Procedure

একটি procedure হলো যেকোনো variable $f_{proc} : \{k\} \to B$, যেখানে $k$ একটি key এবং $B$ হলো byte arrays-এর একটি set; procedure-এর প্রতিটি application $k$-এর সঙ্গে associated byte array-কে instructions-এর finite ordered sequence হিসেবে evaluate করে এবং returned value define না করে সেই instructions তাদের represented order-এ execute করে।

#### Procedure(k)

> Let $b \in B$ such that $f_{proc}(k) = b$.
>
> Let $(i_0,\dots,i_n)$ be the finite ordered sequence of instructions represented by $b$, where $\forall j \in \{0,\dots,n\}, i_j$ is an instruction.
>
> $\mathrm{Procedure}(k)$ is the execution of each $i_j$ in ascending order of $j$.

### Function

একটি function হলো যেকোনো procedure $f_{func} : \{k\} \to B$, যেখানে $k$ একটি key এবং $B$ হলো byte arrays-এর একটি set; function-এর প্রতিটি application $k$-এর সঙ্গে associated byte array-কে instructions-এর finite ordered sequence হিসেবে evaluate করে, সেই instructions তাদের represented order-এ execute করে, এবং execution completed হওয়ার পরে memory-র কোনো address-এ একটি resulting byte array assign করে, যা function-এর returned value হিসেবে evaluate করা যেতে পারে।

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

## Threading

### Process

একটি process হলো execution-এর যেকোনো bounded flow, যা input গ্রহণ করে, এক বা একাধিক instruction execute করে, এবং output উৎপন্ন করে; process একটি system-এর মধ্যে transformation-এর একটি distinct unit represent করে।

### Thread

একটি thread হলো process-এর মধ্যে contained execution-এর যেকোনো flow; thread এমন একটি path প্রদান করে যার মাধ্যমে সেই process-এর ordered sequences of instructions execute করা যেতে পারে।

#### Thread(p)

> Let $p$ be a process.
>
> Let $(i_0,\dots,i_n)$ be a finite ordered sequence of instructions belonging to $p$.
>
> $\mathrm{Thread}(p)$ is the execution of each $i_j$ in ascending order of $j$ within $p$.

### Dispatcher

একটি dispatcher হলো যেকোনো tuple $(t,W,f_d)$, যেখানে $t$ একটি thread, $W$ হলো work হিসেবে accepted procedures বা functions-এর একটি set, এবং $f_d$ হলো একটি dispatch rule যা $W$ থেকে work select করে; dispatcher selected work-কে dispatch rule অনুযায়ী $t$-এ execute করায়।

#### Dispatcher(t)

> Let $t$ be a thread.
>
> Let $W$ be a set of procedures or functions accepted by the dispatcher, where $\forall w \in W$, $w$ is a procedure or function.
>
> Let $f_d : \mathcal{P}(W) \to W$ be a dispatch rule which selects work from a non-empty subset of accepted work.
>
> $\mathrm{Dispatcher}(t)$ is the execution of each selected $f_d(W')$ on $t$, where $W' \subseteq W$ and $W' \neq \varnothing$.

## Composites

### Member

একটি member হলো যেকোনো element $m \in M$, যেখানে $M$ হলো members-এর একটি set; একটি member হলো এমন value যা object-এর member map-এর মধ্যে একটি key-তে assign করা যেতে পারে।

### Object

একটি object হলো যেকোনো tuple $(a,K,f_o)$, যেখানে $a \in A$ একটি address, $K$ হলো keys-এর একটি set, এবং $f_o : K \to M$ একটি member map, যেখানে $M$ হলো members-এর একটি set; এটি object-কে এমন একটি addressable composite represent করতে দেয় যার members $f_o$-এর মাধ্যমে keys-এ assign করা হয়।

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

একটি field হলো যেকোনো tuple $(o,k,m)$, যেখানে $o = (a,K,f_o)$ একটি object, $k \in K$ একটি key, $m \in M$ একটি member, এবং $f_o(k) = m$; field object-এর member map থেকে resolved একটি keyed member represent করে।

#### Field(k)

> Let $o = (a,K,f_o)$ be an object.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Method

একটি method হলো যেকোনো field $(o,k,m)$, যেখানে $m$ একটি procedure বা function; method একটি object-এর keyed executable member represent করে।

#### Method(k)

> Let $o = (a,K,f_o)$ be an object.
>
> Let $k \in K$ be a key.
>
> Let $m \in M$ be a member such that $f_o(k) = m$.
>
> $\mathrm{Method}(o,k) = (o,k,m)$ when $m$ is a procedure or function.

### Property

একটি property হলো যেকোনো field $(o,k,m)$, যেখানে $m = (A,f_a)$ একটি accessor map, $A = \{ \mathrm{Get}, \mathrm{Set} \}$, এবং $f_a : A \to M$ প্রতিটি accessor-কে একটি member-এ map করে; এখানে $f_a(\mathrm{Get})$ একটি function এবং $f_a(\mathrm{Set})$ একটি procedure, যার ফলে property একটি keyed member-এর retrieval ও assignment behavior উভয়ই define করতে পারে।

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

একটি structure (প্রায়ই `struct` হিসেবে সংক্ষিপ্ত) হলো যেকোনো object $s = (a,K,f_s)$, যেখানে $K$ keys-এর একটি finite set এবং $f_s : K \to M$ হলো এমন member map যা struct assign হওয়ার পরে পরিবর্তন করা যায় না; struct হলো একটি specialized object যার keyed member layout fixed।

#### Structure(k)

> Let $s = (a,K,f_s)$ be a structure.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

একটি class হলো যেকোনো object $c = (a_c,K_c,f_c)$, যেখানে $K_c$ keys-এর একটি finite set এবং $f_c : K_c \to M$ একটি member-definition map; class হলো একটি specialized object যার keyed members অন্য objects produce করতে ব্যবহৃত member layout define করে।

#### Class(a)

> Let $c = (a_c,K_c,f_c)$ be a class.
>
> Let $a \in A$ be an address assigned to an object produced from $c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interface

একটি interface হলো যেকোনো object $r = (a_r,K_r,f_r)$, যেখানে $K_r$ keys-এর একটি finite set এবং $f_r : K_r \to M$ একটি member-requirement map; interface হলো একটি specialized object যার keyed members অন্য object দ্বারা প্রদান করা আবশ্যক members define করে।

#### Interface(o)

> Let $r = (a_r,K_r,f_r)$ be an interface.
>
> Let $o = (a,K,f_o)$ be an object.
>
> $\mathrm{Interface}(r,o)$ holds when $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
