<!-- Ang saling ito ay ginawa ng ChatGPT at dapat suriin ng isang taong tagapagsalin. -->
<!-- Alisin ang mga linyang ito sa isang pull request pagkatapos mapatunayan ang salin. -->

# FRELSPEC

<br/>

> **Espesipikasyon ng mga Pundasyong Ugnayan**<br/>
> Rebisyon 1<br/>
> Hulyo 7, 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Nakalaan ang lahat ng karapatan.<br/>
> <br/>
> Ang mga depinisyon at konseptong ipinapakita rito ay naglalarawan ng mga pundasyong matematikal na konstrukto at maaaring malayang ipahayag muli.

## Panimula

Itinatatag ng **Foundational Relations Specification (FRELSPEC)** ang mga pangunahing relasyonal na istrukturang nasa pundasyon ng CatalystUI ecosystem. Layunin nitong magbigay ng pinag-isang pagkaunawa kung paano nauugnay ang values, memory, operations, at composites sa documentation, specifications, implementations, at verification reviews, upang matiyak ang consistency, linaw, at alignment.

Sa pamamagitan ng pagtukoy sa mga ugnayan sa pagitan ng mga pundasyong konsepto sa tiyak at matatag na anyo, nagbibigay ang FRELSPEC ng karaniwang reference point para sa mas mataas na antas ng specifications. Pinapayagan nito ang developers, reviewers, at implementers na mangatuwiran mula sa parehong pundasyon kapag tinutukoy kung ang isang wika, serbisyo, framework, o sistema ay kayang katawanin ang mga relasyonal na construct na kinakailangan upang maituring na within spec.

> [!IMPORTANT]
>
> We express definitions using a derived form of [set theory](https://en.wikipedia.org/wiki/Set_theory) notation. This approach provides precise, unambiguous definitions while maintaining clarity and conciseness. We structure these definitions to support easy reference, clear interpretation, and a consistent conceptual hierarchy.

## Talaan ng Nilalaman

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

## Collections

### Set

Ang set ay anumang koleksiyon ng magkakaibang element.

### Map

Ang map ay anumang function $f_m : K \to V$ kung saan ang $K$ ay set ng keys at ang $V$ ay set ng values.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Ang array ay anumang function $f_a : I \to V$ kung saan ang $I \subset \mathbb{N}$, ang $I$ ay finite at contiguous na set ng integers, at ang $V$ ay set ng values.

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

## Memory

### Address

An address is any element $a \in A$ such that $A$ is a set of addresses, where each address $a$ uniquely identifies a location in a memory structure.

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


## Operations

### Instruction

An instruction is any array of bytes $i \in B$ such that $B$ is a set of byte arrays, where each instruction represents a single computational operation to be performed.

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

## Threading

### Process

A process is any bounded flow of execution which accepts input, executes one or more instructions, and produces output, where the process represents a distinct unit of transformation within a system.

### Thread

A thread is any flow of execution contained within a process, where the thread provides one path by which ordered sequences of instructions belonging to that process may be executed.

#### Thread(p)

> Let $p$ be a process.
>
> Let $(i_0,\dots,i_n)$ be a finite ordered sequence of instructions belonging to $p$.
>
> $\mathrm{Thread}(p)$ is the execution of each $i_j$ in ascending order of $j$ within $p$.

### Dispatcher

A dispatcher is any tuple $(t,W,f_d)$ such that $t$ is a thread, $W$ is a set of procedures or functions accepted as work, and $f_d$ is a dispatch rule which selects work from $W$, where the dispatcher causes selected work to execute on $t$ according to the dispatch rule.

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

A member is any element $m \in M$ such that $M$ is a set of members, where a member is a value which may be assigned to a key within the member map of an object.

### Object

An object is any tuple $(a,K,f_o)$ such that $a \in A$ is an address, $K$ is a set of keys, and $f_o : K \to M$ is a member map, where $M$ is a set of members, allowing the object to represent an addressable composite whose members are assigned to keys through $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

A field is any tuple $(o,k,m)$ such that $o = (a,K,f_o)$ is an object, $k \in K$ is a key, $m \in M$ is a member, and $f_o(k) = m$, where the field represents one keyed member resolved from the member map of an object.

#### Field(k)

> Let $o = (a,K,f_o)$ be an object.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Method

A method is any field $(o,k,m)$ such that $m$ is a procedure or function, where the method represents a keyed executable member of an object.

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
