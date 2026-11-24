<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden beoordeeld. -->
<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

# FRELSPEC

<br/>

> **Fundamentele Relatie-specificatie**<br/>
> Revisie 1<br/>
> 7 juli 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/>
> <br/>
> De definities en concepten die hierin worden gepresenteerd beschrijven fundamentele wiskundige constructies en mogen vrij opnieuw worden uitgedrukt.

## Inleiding

De **Foundational Relations Specification (FRELSPEC)** legt de kernrelationele structuren vast die ten grondslag liggen aan het CatalystUI-ecosysteem. Het doel is een gezamenlijk begrip te bieden van hoe waarden, geheugen, bewerkingen en composieten met elkaar verbonden zijn in documentatie, specificaties, implementaties en verificatiebeoordelingen, zodat consistentie, duidelijkheid en afstemming worden gewaarborgd.

Door relaties tussen fundamentele concepten in een precieze en stabiele vorm te definiëren, biedt FRELSPEC een gemeenschappelijk referentiepunt voor specificaties op hoger niveau. Hierdoor kunnen ontwikkelaars, beoordelaars en implementatoren vanuit hetzelfde fundament redeneren wanneer zij bepalen of een taal, service, framework of systeem de relationele constructies kan vertegenwoordigen die nodig zijn om within spec te worden beschouwd.

> [!IMPORTANT]
>
> We drukken definities uit met een afgeleide vorm van [verzamelingenleer](https://en.wikipedia.org/wiki/Set_theory)-notatie. Deze aanpak biedt precieze, ondubbelzinnige definities terwijl duidelijkheid en beknoptheid behouden blijven. We structureren deze definities om eenvoudige verwijzing, heldere interpretatie en een consistente conceptuele hiërarchie te ondersteunen.

## Inhoudsopgave

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

## Collecties

### Set

Een set is elke collectie van afzonderlijke elementen.

### Map

Een map is elke functie $f_m : K \to V$ waarbij $K$ een set keys is en $V$ een set values is.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Een array is elke functie $f_a : I \to V$ waarbij $I \subset \mathbb{N}$, $I$ een eindige, aaneengesloten set integers is en $V$ een set values is.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Een file is elke functie $f_f : I \to B$ waarbij $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ een eindige, aaneengesloten set integers is en $b$ een set bytes is, waarbij $f_f$ voortkomt uit een mechanisme voor persistente dataopslag.

#### File(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Stream

Een stream is elke functie $f_s$ waarbij elke toepassing van $f_s$ de volgende chunk $f_c : I \to B$ in een byte sequence oplevert, waarbij $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ een eindige, aaneengesloten set integers is, $B$ een set bytes is en $f_s$ voortkomt uit een mechanisme voor sequentiële datageneratie of -opvraging.

#### Stream()

> Let $c_k : I_k \to B$ be the chunk returned by the $k\text{-th}$ application of $f_s$.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ on the $k\text{-th}$ application.

## Geheugen

### Address

Een address is elk element $a \in A$ waarbij $A$ een set addresses is en elk address $a$ een locatie in een memory structure uniek identificeert.

### Pointer

Een pointer is elke functie $f_p : \{a\} \to B$ waarbij $a \in A$ een address is en $B$ een set byte arrays is, waarbij elke toepassing van $f_p$ de byte array evalueert die is opgeslagen op de memory location die door het gebonden address wordt geïdentificeerd.

#### Pointer()

> Let $f_m : A \to B$ be a memory map.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Een variable is elke functie $f_v : \{k\} \to B$ waarbij $k$ een key is en $B$ een set byte arrays is, waarbij de variable een pointer uitbreidt door één key aan één address te binden en de byte array te evalueren die is opgeslagen op de memory location die door dat address wordt geïdentificeerd.

#### Variable(k)

> Let $f_b : \{k\} \to \{a\}$ be the variable’s binding function.
>
> Let $f_p : \{a\} \to B$ be a pointer.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Een constant is elke variable $f_c : \{k\} \to B$ waarbij $k$ een key is en $B$ een set byte arrays is, waarbij de byte array die aan $k$ is gekoppeld niet kan worden gewijzigd nadat zij is toegewezen.

#### Constant(k)

> Let $b_0 \in B$ be the byte array assigned to $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ after $b_0$ is assigned.


## Bewerkingen

### Instruction

Een instruction is elke array van bytes $i \in B$ waarbij $B$ een set byte arrays is en elke instruction één uit te voeren computationele bewerking vertegenwoordigt.

### Procedure

Een procedure is elke variable $f_{proc} : \{k\} \to B$ waarbij $k$ een key is en $B$ een set byte arrays is, waarbij elke toepassing van de procedure de byte array die aan $k$ is gekoppeld evalueert als een eindige geordende sequence van instructions en die instructions in hun weergegeven volgorde uitvoert zonder een teruggegeven waarde te definiëren.

#### Procedure(k)

> Laat $b \in B$ such that $f_{proc}(k) = b$.
>
> Let $(i_0,\dots,i_n)$ be the finite ordered sequence of instructions represented by $b$, where $\forall j \in \{0,\dots,n\}, i_j$ is an instruction.
>
> $\mathrm{Procedure}(k)$ is the execution of each $i_j$ in ascending order of $j$.

### Function

Een function is elke procedure $f_{func} : \{k\} \to B$ waarbij $k$ een key is en $B$ een set byte arrays is, waarbij elke toepassing van de function de byte array die aan $k$ is gekoppeld evalueert als een eindige geordende sequence van instructions, die instructions in hun weergegeven volgorde uitvoert en, nadat de uitvoering is voltooid, een resulterende byte array toewijst aan een address in memory dat als de teruggegeven waarde van de function kan worden geëvalueerd.

#### Function(k)

> Laat $b \in B$ such that $f_{func}(k) = b$.
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

Een process is elke begrensde flow of execution die input accepteert, één of meer instructions uitvoert en output produceert, waarbij het process een afzonderlijke transformatie-eenheid binnen een system vertegenwoordigt.

### Thread

Een thread is elke flow of execution die zich binnen een process bevindt, waarbij de thread één pad biedt waarlangs geordende sequences van instructions die tot dat process behoren kunnen worden uitgevoerd.

#### Thread(p)

> Let $p$ be a process.
>
> Let $(i_0,\dots,i_n)$ be a finite ordered sequence of instructions belonging to $p$.
>
> $\mathrm{Thread}(p)$ is the execution of each $i_j$ in ascending order of $j$ within $p$.

### Dispatcher

Een dispatcher is elke tuple $(t,W,f_d)$ waarbij $t$ een thread is, $W$ een set procedures of functions is die als work wordt geaccepteerd, en $f_d$ een dispatch rule is die work uit $W$ selecteert, waarbij de dispatcher geselecteerd work volgens de dispatch rule op $t$ laat uitvoeren.

#### Dispatcher(t)

> Let $t$ be a thread.
>
> Let $W$ be a set of procedures or functions accepted by the dispatcher, where $\forall w \in W$, $w$ is a procedure or function.
>
> Let $f_d : \mathcal{P}(W) \to W$ be a dispatch rule which selects work from a non-empty subset of accepted work.
>
> $\mathrm{Dispatcher}(t)$ is the execution of each selected $f_d(W')$ on $t$, where $W' \subseteq W$ and $W' \neq \varnothing$.

## Composieten

### Member

Een member is elk element $m \in M$ waarbij $M$ een set members is, waarbij een member een value is die aan een key binnen de member map van een object kan worden toegewezen.

### Object

Een object is elke tuple $(a,K,f_o)$ waarbij $a \in A$ een address is, $K$ een set keys is en $f_o : K \to M$ een member map is, waarbij $M$ een set members is. Hierdoor kan het object een addressable composite vertegenwoordigen waarvan de members via $f_o$ aan keys worden toegewezen.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Een field is elke tuple $(o,k,m)$ waarbij $o = (a,K,f_o)$ een object is, $k \in K$ een key is, $m \in M$ een member is en $f_o(k) = m$, waarbij het field één keyed member vertegenwoordigt dat uit de member map van een object is opgelost.

#### Field(k)

> Laat $o = (a,K,f_o)$ be an object.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Method

Een method is elk field $(o,k,m)$ waarbij $m$ een procedure of function is, waarbij de method een keyed executable member van een object vertegenwoordigt.

#### Method(k)

> Laat $o = (a,K,f_o)$ be an object.
>
> Let $k \in K$ be a key.
>
> Laat $m \in M$ be a member such that $f_o(k) = m$.
>
> $\mathrm{Method}(o,k) = (o,k,m)$ when $m$ is a procedure or function.

### Property

Een property is elk field $(o,k,m)$ waarbij $m = (A,f_a)$ een accessor map is, $A = \{ \mathrm{Get}, \mathrm{Set} \}$ en $f_a : A \to M$ elke accessor naar een member mapt, waarbij $f_a(\mathrm{Get})$ een function is en $f_a(\mathrm{Set})$ een procedure is. Hierdoor kan de property zowel het ophaalgedrag als het toewijzingsgedrag van een keyed member definiëren.

#### Property(k)

> Let $(o,k,m)$ be a field.
>
> Laat $m = (A,f_a)$ be an accessor map.
>
> Laat $A = \{ \mathrm{Get}, \mathrm{Set} \}$.
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$, where $g$ is a function.
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$, where $s$ is a procedure.
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> Let $(o,k,(A,f_a))$ be a property.
>
> Laat $g = f_a(\mathrm{Get})$.
>
> $\mathrm{Get}(k)$ is the application of $g$.

#### Set(k)

> Let $(o,k,(A,f_a))$ be a property.
>
> Laat $s = f_a(\mathrm{Set})$.
>
> $\mathrm{Set}(k)$ is the application of $s$.

### Structure

Een structure (vaak afgekort tot `struct`) is elk object $s = (a,K,f_s)$ waarbij $K$ een eindige set keys is en $f_s : K \to M$ een member map is die niet kan worden gewijzigd nadat de struct is toegewezen, waarbij de struct een gespecialiseerd object is waarvan de keyed member layout vastligt.

#### Structure(k)

> Laat $s = (a,K,f_s)$ be a structure.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Een class is elk object $c = (a_c,K_c,f_c)$ waarbij $K_c$ een eindige set keys is en $f_c : K_c \to M$ een member-definition map is, waarbij de class een gespecialiseerd object is waarvan de keyed members de member layout definiëren die wordt gebruikt om andere objecten te produceren.

#### Class(a)

> Laat $c = (a_c,K_c,f_c)$ be a class.
>
> Let $a \in A$ be an address assigned to an object produced from $c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interface

Een interface is elk object $r = (a_r,K_r,f_r)$ waarbij $K_r$ een eindige set keys is en $f_r : K_r \to M$ een member-requirement map is, waarbij de interface een gespecialiseerd object is waarvan de keyed members definiëren welke members door een ander object moeten worden geleverd.

#### Interface(o)

> Laat $r = (a_r,K_r,f_r)$ be an interface.
>
> Laat $o = (a,K,f_o)$ be an object.
>
> $\mathrm{Interface}(r,o)$ holds when $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
