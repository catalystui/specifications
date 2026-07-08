<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza-człowieka. -->
<!-- Usuń te wiersze w pull requeście po zweryfikowaniu tłumaczenia. -->

# FRELSPEC

<br/>

> **Specyfikacja relacji podstawowych**<br/>
> Rewizja 1<br/>
> 7 lipca 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Wszelkie prawa zastrzeżone.<br/>
> <br/>
> Przedstawione tutaj definicje i pojęcia opisują podstawowe konstrukcje matematyczne i mogą być swobodnie wyrażane ponownie.

## Wprowadzenie

**Foundational Relations Specification (FRELSPEC)** ustanawia podstawowe struktury relacyjne, które stanowią fundament ekosystemu CatalystUI. Jej celem jest zapewnienie wspólnego rozumienia tego, jak wartości, pamięć, operacje i kompozyty są ze sobą powiązane w dokumentacji, specyfikacjach, implementacjach oraz przeglądach weryfikacyjnych, tak aby zachować spójność, jasność i zgodność.

Definiując relacje między podstawowymi pojęciami w precyzyjnej, stabilnej formie, FRELSPEC zapewnia wspólny punkt odniesienia dla specyfikacji wyższego poziomu. Dzięki temu deweloperzy, recenzenci i implementatorzy mogą opierać swoje rozumowanie na tym samym fundamencie, gdy ustalają, czy język, usługa, framework albo system może reprezentować konstrukcje relacyjne wymagane do uznania go za zgodny ze specyfikacją.

> [!IMPORTANT]
>
> Definicje wyrażamy za pomocą pochodnej formy zapisu [teorii zbiorów](https://en.wikipedia.org/wiki/Set_theory). Takie podejście zapewnia precyzyjne, jednoznaczne definicje, zachowując jednocześnie jasność i zwięzłość. Strukturyzujemy te definicje tak, aby wspierały łatwe odwoływanie się, jasną interpretację i spójną hierarchię pojęciową.

## Spis treści

- [FRELSPEC](#frelspec)
  - [Wprowadzenie](#introduction)
  - [Spis treści](#table-of-contents)
  - [Kolekcje](#collections)
    - [Zbiór](#set)
    - [Mapa](#map)
      - [Map(k)](#mapk)
    - [Tablica](#array)
      - [Array(i)](#arrayi)
    - [Plik](#file)
      - [File(i)](#filei)
    - [Strumień](#stream)
      - [Stream()](#stream-1)
  - [Pamięć](#memory)
    - [Adres](#address)
    - [Wskaźnik](#pointer)
      - [Pointer()](#pointer-1)
    - [Zmienna](#variable)
      - [Variable(k)](#variablek)
    - [Stała](#constant)
      - [Constant(k)](#constantk)
  - [Operacje](#operations)
    - [Instrukcja](#instruction)
    - [Procedura](#procedure)
      - [Procedure(k)](#procedurek)
    - [Funkcja](#function)
      - [Function(k)](#functionk)
  - [Wątki](#threading)
    - [Proces](#process)
    - [Wątek](#thread)
      - [Thread(p)](#threadp)
    - [Dyspozytor](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Kompozyty](#composites)
    - [Element członkowski](#member)
    - [Obiekt](#object)
      - [Object(k)](#objectk)
    - [Pole](#field)
      - [Field(k)](#fieldk)
    - [Metoda](#method)
      - [Method(k)](#methodk)
    - [Właściwość](#property)
      - [Property(k)](#propertyk)
      - [Get(k)](#getk)
      - [Set(k)](#setk)
    - [Struktura](#structure)
      - [Structure(k)](#structurek)
    - [Klasa](#class)
      - [Class(a)](#classa)
    - [Interfejs](#interface)
      - [Interface(o)](#interfaceo)

## Kolekcje

### Zbiór

Zbiór to dowolna kolekcja odrębnych elementów.

### Mapa

Mapa to dowolna funkcja $f_m : K \to V$ taka, że $K$ jest zbiorem kluczy, a $V$ zbiorem wartości.

#### Mapa(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Tablica

Tablica to dowolna funkcja $f_a : I \to V$ taka, że $I \subset \mathbb{N}$, $I$ jest skończonym, ciągłym zbiorem liczb całkowitych, a $V$ jest zbiorem wartości.

#### Tablica(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### Plik

Plik to dowolna funkcja $f_f : I \to B$ taka, że $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ jest skończonym, ciągłym zbiorem liczb całkowitych, a $b$ jest zbiorem bajtów, przy czym $f_f$ pochodzi z mechanizmu trwałego przechowywania danych.

#### Plik(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Strumień

A stream is any function $f_s$ takie, że each application of $f_s$ yields the next chunk $f_c : I \to B$ in a byte sequence, gdzie $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ is a finite, contiguous set of integers, $B$ is a set of bytes, and $f_s$ originates from a mechanism of sequential data generation or retrieval.

#### Strumień()

> Niech $c_k : I_k \to B$ be the chunk returned by the $k$-th application of $f_s$.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ on the $k$-th application.

## Pamięć

### Adres

An address is any element $a \in A$ takie, że $A$ is a set of addresses, gdzie each address $a$ uniquely identifies a location in a memory structure.

### Wskaźnik

A pointer is any function $f_p : \{a\} \to B$ takie, że $a \in A$ is an address and $B$ is a set of byte arrays, gdzie each application of $f_p$ evaluates the byte array stored at the memory location identified by its bound address.

#### Wskaźnik()

> Niech $f_m : A \to B$ be a memory map.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Zmienna

A variable is any function $f_v : \{k\} \to B$ takie, że $k$ is a key and $B$ is a set of byte arrays, gdzie the variable extends a pointer by binding one key to one address and evaluating the byte array stored at the memory location identified by that address.

#### Zmienna(k)

> Niech $f_b : \{k\} \to \{a\}$ be the variable’s binding function.
>
> Niech $f_p : \{a\} \to B$ be a pointer.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Stała

A constant is any variable $f_c : \{k\} \to B$ takie, że $k$ is a key and $B$ is a set of byte arrays, gdzie the byte array associated with $k$ cannot be changed after it is assigned.

#### Stała(k)

> Niech $b_0 \in B$ be the byte array assigned to $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ after $b_0$ is assigned.


## Operacje

### Instrukcja

An instruction is any array of bytes $i \in B$ takie, że $B$ is a set of byte arrays, gdzie each instruction represents a single computational operation to be performed.

### Procedura

A procedure is any variable $f_{proc} : \{k\} \to B$ takie, że $k$ is a key and $B$ is a set of byte arrays, gdzie each application of the procedure evaluates the byte array associated with $k$ as a finite ordered sequence of instructions and executes those instructions in their represented order without defining a returned value.

#### Procedura(k)

> Niech $b \in B$ takie, że $f_{proc}(k) = b$.
>
> Niech $(i_0,\dots,i_n)$ be the finite ordered sequence of instructions represented by $b$, gdzie $\forall j \in \{0,\dots,n\}, i_j$ is an instruction.
>
> $\mathrm{Procedure}(k)$ is the execution of each $i_j$ in ascending order of $j$.

### Funkcja

A function is any procedure $f_{func} : \{k\} \to B$ takie, że $k$ is a key and $B$ is a set of byte arrays, gdzie each application of the function evaluates the byte array associated with $k$ as a finite ordered sequence of instructions, executes those instructions in their represented order, and, after execution is completed, assigns a resulting byte array to some address in memory which may be evaluated as the function’s returned value.

#### Funkcja(k)

> Niech $b \in B$ takie, że $f_{func}(k) = b$.
>
> Niech $(i_0,\dots,i_n)$ be the finite ordered sequence of instructions represented by $b$, gdzie $\forall j \in \{0,\dots,n\}, i_j$ is an instruction.
>
> Niech $a_r \in A$ be an address assigned after execution is completed.
>
> Niech $f_m : A \to B$ be a memory map.
>
> $\mathrm{Function}(k)$ is the execution of each $i_j$ in ascending order of $j$, gdzie $\exists b_r \in B : f_m(a_r) = b_r$ after execution is completed.
>
> $\mathrm{Function}(k) = b_r$

## Wątki

### Proces

A process is any bounded flow of execution which accepts input, executes one or more instructions, and produces output, gdzie the process represents a distinct unit of transformation within a system.

### Wątek

A thread is any flow of execution contained within a process, gdzie the thread provides one path by which ordered sequences of instructions belonging to that process may be executed.

#### Wątek(p)

> Niech $p$ be a process.
>
> Niech $(i_0,\dots,i_n)$ be a finite ordered sequence of instructions belonging to $p$.
>
> $\mathrm{Thread}(p)$ is the execution of each $i_j$ in ascending order of $j$ within $p$.

### Dyspozytor

A dispatcher is any tuple $(t,W,f_d)$ takie, że $t$ is a thread, $W$ is a set of procedures or functions accepted as work, and $f_d$ is a dispatch rule which selects work from $W$, gdzie the dispatcher causes selected work to execute on $t$ according to the dispatch rule.

#### Dyspozytor(t)

> Niech $t$ be a thread.
>
> Niech $W$ be a set of procedures or functions accepted by the dispatcher, gdzie $\forall w \in W$, $w$ is a procedure or function.
>
> Niech $f_d : \mathcal{P}(W) \to W$ be a dispatch rule which selects work from a non-empty subset of accepted work.
>
> $\mathrm{Dispatcher}(t)$ is the execution of each selected $f_d(W')$ on $t$, gdzie $W' \subseteq W$ and $W' \neq \varnothing$.

## Kompozyty

### Element członkowski

A member is any element $m \in M$ takie, że $M$ is a set of members, gdzie a member is a value which may be assigned to a key within the member map of an object.

### Obiekt

An object is any tuple $(a,K,f_o)$ takie, że $a \in A$ is an address, $K$ is a set of keys, and $f_o : K \to M$ is a member map, gdzie $M$ is a set of members, allowing the object to represent an addressable composite whose members are assigned to keys through $f_o$.

#### Obiekt(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Pole

A field is any tuple $(o,k,m)$ takie, że $o = (a,K,f_o)$ is an object, $k \in K$ is a key, $m \in M$ is a member, and $f_o(k) = m$, gdzie the field represents one keyed member resolved from the member map of an object.

#### Pole(k)

> Niech $o = (a,K,f_o)$ be an object.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Metoda

A method is any field $(o,k,m)$ takie, że $m$ is a procedure or function, gdzie the method represents a keyed executable member of an object.

#### Metoda(k)

> Niech $o = (a,K,f_o)$ be an object.
>
> Niech $k \in K$ be a key.
>
> Niech $m \in M$ be a member takie, że $f_o(k) = m$.
>
> $\mathrm{Method}(o,k) = (o,k,m)$ when $m$ is a procedure or function.

### Właściwość

A property is any field $(o,k,m)$ takie, że $m = (A,f_a)$ is an accessor map, $A = \{ \mathrm{Get}, \mathrm{Set} \}$, and $f_a : A \to M$ maps each accessor to a member, gdzie $f_a(\mathrm{Get})$ is a function and $f_a(\mathrm{Set})$ is a procedure, allowing the property to define both the retrieval and assignment behavior of a keyed member.

#### Właściwość(k)

> Niech $(o,k,m)$ be a field.
>
> Niech $m = (A,f_a)$ be an accessor map.
>
> Niech $A = \{ \mathrm{Get}, \mathrm{Set} \}$.
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$, gdzie $g$ is a function.
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$, gdzie $s$ is a procedure.
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> Niech $(o,k,(A,f_a))$ be a property.
>
> Niech $g = f_a(\mathrm{Get})$.
>
> $\mathrm{Get}(k)$ is the application of $g$.

#### Zbiór(k)

> Niech $(o,k,(A,f_a))$ be a property.
>
> Niech $s = f_a(\mathrm{Set})$.
>
> $\mathrm{Set}(k)$ is the application of $s$.

### Struktura

A structure (often abbreviated to `struct`) is any object $s = (a,K,f_s)$ takie, że $K$ is a finite set of keys and $f_s : K \to M$ is a member map which cannot be changed after the struct is assigned, gdzie the struct is a specialized object whose keyed member layout is fixed.

#### Struktura(k)

> Niech $s = (a,K,f_s)$ be a structure.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Klasa

A class is any object $c = (a_c,K_c,f_c)$ takie, że $K_c$ is a finite set of keys and $f_c : K_c \to M$ is a member-definition map, gdzie the class is a specialized object whose keyed members define the member layout used to produce other objects.

#### Klasa(a)

> Niech $c = (a_c,K_c,f_c)$ be a class.
>
> Niech $a \in A$ be an address assigned to an object produced from $c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interfejs

An interface is any object $r = (a_r,K_r,f_r)$ takie, że $K_r$ is a finite set of keys and $f_r : K_r \to M$ is a member-requirement map, gdzie the interface is a specialized object whose keyed members define the members required to be provided by another object.

#### Interfejs(o)

> Niech $r = (a_r,K_r,f_r)$ be an interface.
>
> Niech $o = (a,K,f_o)$ be an object.
>
> $\mathrm{Interface}(r,o)$ holds when $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
