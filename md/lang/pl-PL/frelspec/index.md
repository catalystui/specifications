<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza. -->
<!-- Usuń te wiersze w pull requeście po zweryfikowaniu tłumaczenia. -->

# FRELSPEC

<br/>

> **Specyfikacja relacji fundamentalnych**<br/>
> Rewizja 2.1<br/>
> 24 listopada 2026 r.<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Wszelkie prawa zastrzeżone.<br/>
> <br/>
> Przedstawione tu definicje i pojęcia opisują fundamentalne konstrukcje matematyczne i mogą być swobodnie przeformułowywane.

## Wprowadzenie

**Specyfikacja relacji fundamentalnych (FRELSPEC)** ustanawia podstawowe struktury relacyjne leżące u podstaw ekosystemu CatalystUI. Jej celem jest zapewnienie jednolitego rozumienia powiązań między pamięcią, kolekcjami, operacjami i strukturami złożonymi w dokumentacji, specyfikacjach, implementacjach i przeglądach weryfikacyjnych, zapewniając spójność, jasność i zgodność.

Definiując relacje między podstawowymi pojęciami w precyzyjny i stabilny sposób, FRELSPEC zapewnia wspólny punkt odniesienia dla specyfikacji wyższego poziomu, pozwalając poszczególnym implementacjom określać własne reguły i zachowania. Dzięki temu programiści, recenzenci i implementatorzy mogą rozumować na tej samej podstawie, ustalając, czy język, usługa, framework lub system może reprezentować konstrukcje relacyjne wymagane do zgodności ze specyfikacją.

> [!IMPORTANT]
>
> Wyrażamy definicje za pomocą pochodnej postaci notacji [teorii mnogości](https://en.wikipedia.org/wiki/Set_theory). Podejście to zapewnia precyzyjne i jednoznaczne definicje przy zachowaniu jasności i zwięzłości. Porządkujemy je, aby ułatwić odwoływanie się do nich, jasną interpretację i spójną hierarchię pojęciową.

## Spis treści

- [FRELSPEC](#frelspec)
  - [Wprowadzenie](#wprowadzenie)
  - [Spis treści](#spis-treści)
  - [Rewizje](#rewizje)
    - [Rewizja 2.1](#rewizja-21)
    - [Rewizja 2](#rewizja-2)
  - [Pamięć](#pamięć)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Kolekcje](#kolekcje)
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
  - [Operacje](#operacje)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [Wątkowanie](#wątkowanie)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Struktury złożone](#struktury-złożone)
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

## Rewizje

### Rewizja 2.1

**24 listopada 2026 r.**

Doprecyzowaliśmy definicję File, ustanawiając rozwiązywanie danych sterowane metadanymi, i na nowo zdefiniowaliśmy Stream jako niezależny mechanizm sekwencyjnego generowania lub pobierania danych. Zmiany te pozwalają strumieniom reprezentować skończone lub nieskończone ciągi bez nakładania dodatkowych ograniczeń na inne kolekcje.

### Rewizja 2

**21 listopada 2026 r.**

Zidentyfikowaliśmy niespójności w reprezentowaniu pamięci i przechowywanych wartości za pomocą bajtów i tablic bajtów. Ustanowiliśmy Word jako fundamentalną reprezentację pamięci, ujednolicając relacje między pamięcią, operacjami i strukturami złożonymi.

Zidentyfikowaliśmy niespójności w indeksowaniu tablic i relacjach między kolekcjami. Ustandaryzowaliśmy skończone, ciągłe indeksy i wyjaśniliśmy relacje między Array, File i Stream.

Zidentyfikowaliśmy nadmiarowości i niejednoznaczności w relacjach wykonania i kompozycji. Doprecyzowaliśmy procedury, funkcje, dyspozytory i relacje obiektów, rozwiązując te problemy z zachowaniem niezależności od implementacji.

## Pamięć

### Word

Słowo to dowolny ciąg bitów $w \in \mathrm{Bit}^n$ przechowywany w pamięci, taki, że $n \in \mathbb{N}^+$.

### Address

Adres to dowolne słowo $a \in A$, gdzie $A$ jest zbiorem słów, takie, że $a$ jednoznacznie identyfikuje miejsce w określonej strukturze pamięci.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

Wskaźnik to dowolna funkcja $f_p : \{a\} \to B$, taka, że $a \in A$ jest adresem, a $B$ zbiorem słów, przy czym każde zastosowanie $f_p$ oblicza słowo przechowywane w miejscu pamięci określonym przez $a$.

#### Pointer()

> Niech $f_m : A \to B$ będzie odwzorowaniem pamięci.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Zmienna to dowolna funkcja $f_v : \{k\} \to B$, taka, że $k$ jest kluczem, a $B$ zbiorem słów, przy czym zmienna rozszerza wskaźnik przez związanie klucza z adresem i obliczenie słowa przechowywanego pod tym adresem.

#### Variable(k)

> Niech $f_b : \{k\} \to \{a\}$ będzie funkcją wiążącą zmiennej.
>
> Niech $f_p : \{a\} \to B$ będzie wskaźnikiem.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Stała to dowolna zmienna $f_c : \{k\} \to B$, taka, że $k$ jest kluczem, a $B$ zbiorem słów, przy czym słowa powiązanego z $k$ nie można zmienić po przypisaniu.

#### Constant(k)

> Niech $b_0 \in B$ będzie słowem przypisanym do $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ po przypisaniu $b_0$.

## Kolekcje

### Set

Zbiór to dowolna skończona, nieuporządkowana kolekcja różnych słów.

#### Set()

> Niech $B$ będzie zbiorem słów.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

Mapa to dowolna funkcja $f_m : K \to V$, taka, że $K$ jest zbiorem kluczy, a $V$ zbiorem wartości, przy czym każdemu kluczowi odpowiada dokładnie jedna wartość.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Tablica to dowolna funkcja $f_a : I \to V$, taka, że $I \subseteq \mathbb{N}$ jest skończonym, ciągłym zbiorem indeksów całkowitych, a $V$ zbiorem słów, przy czym każdy indeks identyfikuje dokładnie jedną wartość.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Plik to dowolna krotka $(f_m,d)$, taka, że $d$ jest tablicą słów, a $f_m : I \times \{d\} \to \mathrm{Array}$ funkcją metadanych reprezentowaną przez tablicę słów, gdzie $I$ jest skończonym, ciągłym zbiorem indeksów całkowitych, a $f_m$ określa sposób rozwiązywania danych z $d$.

#### File(i)

> Niech $(f_m,d)$ będzie plikiem.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

Strumień to dowolna funkcja $f_s$, taka, że każde zastosowanie $f_s$ zwraca kolejny fragment $c$ skończonego lub nieskończonego ciągu, gdzie $f_s$ ustanawia mechanizm sekwencyjnego generowania lub pobierania danych.

#### Stream()

> Niech $f_c : K \to C$ będzie funkcją rozwiązywania fragmentów, gdzie $K \subseteq \mathbb{N}$ jest ciągłym zbiorem indeksów całkowitych, a $C$ zbiorem fragmentów.
>
> Niech $k \in K$ będzie indeksem kolejnego fragmentu.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$, przesuwając $k$ po każdym zastosowaniu.

## Operacje

### Instruction

Instrukcja to dowolne słowo lub skończona krotka słów $i \in B$, takie, że $B$ jest zbiorem słów lub skończonych krotek słów, przy czym każda instrukcja reprezentuje pojedynczą operację obliczeniową do wykonania.

### Procedure

Procedura to dowolna zmienna $f_{proc} : \{k\} \to B$, taka, że $f_{proc}(k)$ reprezentuje tablicę instrukcji $f_a : I \to V$, przy czym wykonanie procedury wykonuje każdą instrukcję w kolejności indeksów.

#### Procedure(k)

> $\mathrm{Procedure}(k)$ jest wykonaniem każdego $f_a(i)$ w rosnącej kolejności $i \in I$.

### Function

Funkcja to dowolna procedura $f_{func} : \{k\} \to B$, której wykonanie zwraca adres $a_r \in A$ identyfikujący słowo wynikowe lub pierwsze słowo tablicy słów reprezentującej wynik.

#### Function(k)

> Niech $f_m : A \to B$ będzie odwzorowaniem pamięci, gdzie $a_r \in A$ identyfikuje słowo wynikowe $r \in B$.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## Wątkowanie

### Process

Proces to dowolny ograniczony przepływ wykonania, który przyjmuje dane wejściowe, wykonuje jedną lub więcej procedur lub funkcji i wytwarza dane wyjściowe, przy czym proces reprezentuje odrębną jednostkę transformacji w systemie.

### Thread

Wątek to dowolny przepływ wykonania zawarty w procesie, zapewniający jedną ścieżkę, na której mogą być wykonywane procedury lub funkcje należące do tego procesu.

#### Thread(p)

> Niech $p$ będzie procesem.
>
> Niech $(w_0, \dots, w_n)$ będzie skończoną krotką procedur lub funkcji należących do $p$.
>
> $\mathrm{Thread}(p)$ jest wykonaniem każdego $w_j$ w rosnącej kolejności $j$ w ramach $p$.

### Dispatcher

Dyspozytor to dowolna krotka $(t,W,f_d)$, taka, że $t$ jest wątkiem, $W$ zbiorem procedur lub funkcji przyjętych jako praca, a $f_d$ regułą dyspozycji wybierającą pracę z $W$, przy czym dyspozytor powoduje wykonanie wybranej pracy w $t$ zgodnie z tą regułą.

#### Dispatcher(t)

> Niech $t$ będzie wątkiem.
>
> Niech $W$ będzie zbiorem procedur lub funkcji przyjętych przez dyspozytor, gdzie $\forall w \in W$, $w$ jest procedurą lub funkcją.
>
> Niech $f_d : \mathcal{P}^+(W) \to W$ będzie regułą dyspozycji wybierającą pracę z niepustego podzbioru przyjętej pracy.
>
> $\mathrm{Dispatcher}(t)$ jest wykonaniem każdego wybranego $f_d(W')$ w $t$, gdzie $W' \subseteq W$, $W' \neq \varnothing$ i $f_d(W') \in W'$.

## Struktury złożone

### Member

Składowa to dowolny element $m \in M$, taki, że $M$ jest zbiorem elementów, a $f_o : K \to M$ odwzorowaniem składowych obiektu, gdzie $m = f_o(k)$ dla pewnego klucza $k \in K$.

### Object

Obiekt to dowolna krotka $(a,K,f_o)$, taka, że $a \in A$ jest adresem, $K$ zbiorem kluczy, a $f_o : K \to M$ odwzorowaniem składowych, gdzie $M$ jest zbiorem elementów, co pozwala obiektowi reprezentować adresowalną strukturę złożoną, której składowe są przypisane do kluczy przez $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Pole to dowolna krotka $(o,k,m)$, taka, że $o = (a,K,f_o)$ jest obiektem, $k \in K$ kluczem, a $m = f_o(k)$ składową, przy czym pole reprezentuje jedną składową określoną kluczem i rozwiązaną z odwzorowania składowych obiektu.

#### Field(o,k)

> Niech $o = (a,K,f_o)$ będzie obiektem.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

Metoda to dowolne pole $(o,k,m)$, takie, że $m$ jest procedurą lub funkcją, przy czym metoda reprezentuje wykonywalną składową obiektu określoną kluczem.

#### Method(o,k)

> Niech $(o,k,m)$ będzie polem.
>
> $\mathrm{Method}(o,k) = (o,k,m)$, gdzie $m$ jest procedurą lub funkcją.

### Property

Właściwość to dowolne pole $(o,k,m)$, takie, że $m = (X,f_a)$ jest odwzorowaniem akcesorów, $X = \{\mathrm{Get}, \mathrm{Set}\}$, a $f_a : X \to M$ przyporządkowuje każdy akcesor składowej, gdzie $f_a(\mathrm{Get})$ jest funkcją, a $f_a(\mathrm{Set})$ procedurą, umożliwiając właściwości określenie zarówno pobierania, jak i przypisywania składowej określonej kluczem.

#### Property(o,k)

> Niech $(o,k,m)$ będzie polem, gdzie $m = (X,f_a)$ jest odwzorowaniem akcesorów.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> Niech $(o,k,(X,f_a))$ będzie właściwością.
>
> $\mathrm{Get}(o,k)$ jest zastosowaniem $f_a(\mathrm{Get})$.

#### Set(o,k)

> Niech $(o,k,(X,f_a))$ będzie właściwością.
>
> $\mathrm{Set}(o,k)$ jest zastosowaniem $f_a(\mathrm{Set})$.

### Structure

Struktura (często skracana do `struct`) to dowolny obiekt $s = (a,K,f_s)$, taki, że $K$ jest skończonym zbiorem kluczy, a $f_s : K \to M$ odwzorowaniem składowych, którego kluczy nie można zmienić po przypisaniu struktury, przy czym struktura jest wyspecjalizowanym obiektem o stałym układzie składowych określonych kluczami.

#### Structure(s,k)

> Niech $s = (a,K,f_s)$ będzie strukturą.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Klasa to dowolny obiekt $c = (a_c,K_c,f_c)$, taki, że $K_c$ jest skończonym zbiorem kluczy, a $f_c : K_c \to M$ odwzorowaniem definicji składowych, przy czym klasa jest wyspecjalizowanym obiektem, którego składowe określone kluczami definiują układ składowych używany do tworzenia innych obiektów.

#### Class(c,a)

> Niech $c = (a_c,K_c,f_c)$ będzie klasą.
>
> Niech $a \in A$ będzie adresem przypisanym obiektowi utworzonemu z $c$.
>
> Niech $f_o : K_c \to M$ będzie odwzorowaniem składowych zgodnym z definicjami $f_c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

Interfejs to dowolny obiekt $r = (a_r,K_r,f_r)$, taki, że $K_r$ jest skończonym zbiorem kluczy, a $f_r : K_r \to M$ odwzorowaniem wymagań składowych, przy czym interfejs jest wyspecjalizowanym obiektem, którego składowe określone kluczami definiują składowe wymagane od innego obiektu.

#### Interface(r,o)

> Niech $r = (a_r,K_r,f_r)$ będzie interfejsem.
>
> Niech $o = (a,K,f_o)$ będzie obiektem.
>
> Niech $f_v : M \times M \to \{0,1\}$ będzie regułą walidacji określającą, czy składowa spełnia wymagania innej składowej.
>
> $\mathrm{Interface}(r,o)$ zachodzi, gdy $K_r \subseteq K$ i $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$.
