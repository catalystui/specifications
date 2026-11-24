<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->
<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

# FRELSPEC

<br/>

> **Spezifikation der grundlegenden Relationen**<br/>
> Revision 2.1<br/>
> 24. November 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Alle Rechte vorbehalten.<br/>
> <br/>
> Die hier vorgestellten Definitionen und Konzepte beschreiben grundlegende mathematische Konstrukte und dürfen frei neu formuliert werden.

## Einführung

Die **Spezifikation der grundlegenden Relationen (FRELSPEC)** legt die zentralen relationalen Strukturen fest, auf denen das CatalystUI-Ökosystem aufbaut. Ihr Zweck ist es, über Dokumentation, Spezifikationen, Implementierungen und Verifizierungsprüfungen hinweg ein einheitliches Verständnis der Beziehungen zwischen Speicher, Sammlungen, Operationen und zusammengesetzten Strukturen zu schaffen und Konsistenz, Klarheit und Übereinstimmung sicherzustellen.

Durch die präzise und stabile Definition der Beziehungen zwischen grundlegenden Konzepten bietet FRELSPEC einen gemeinsamen Bezugspunkt für höherstufige Spezifikationen, während einzelne Implementierungen eigene Regeln und Verhaltensweisen festlegen können. Entwickler, Prüfer und Implementierer können so auf derselben Grundlage beurteilen, ob eine Sprache, ein Dienst, ein Framework oder ein System die für die Spezifikationskonformität erforderlichen relationalen Konstrukte darstellen kann.

> [!IMPORTANT]
>
> Wir drücken Definitionen mithilfe einer abgeleiteten Form der Notation der [Mengenlehre](https://en.wikipedia.org/wiki/Set_theory) aus. Dieser Ansatz liefert präzise, eindeutige Definitionen bei gleichzeitiger Klarheit und Kürze. Wir strukturieren sie für einfaches Nachschlagen, klare Interpretation und eine konsistente begriffliche Hierarchie.

## Inhaltsverzeichnis

- [FRELSPEC](#frelspec)
  - [Einführung](#einführung)
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
  - [Revisionen](#revisionen)
    - [Revision 2.1](#revision-21)
    - [Revision 2](#revision-2)
  - [Speicher](#speicher)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Sammlungen](#sammlungen)
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
  - [Operationen](#operationen)
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
  - [Zusammengesetzte Strukturen](#zusammengesetzte-strukturen)
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

## Revisionen

### Revision 2.1

**24. November 2026**

Wir haben die Definition von File präzisiert, um eine metadatengesteuerte Datenauflösung festzulegen, und Stream als unabhängigen Mechanismus zur sequenziellen Datenerzeugung oder zum sequenziellen Datenabruf neu definiert. Damit können Streams endliche oder unendliche Folgen darstellen, ohne andere Sammlungen zusätzlich einzuschränken.

### Revision 2

**21. November 2026**

Wir haben Unstimmigkeiten bei der Darstellung von Speicher und gespeicherten Werten durch Bytes und Byte-Arrays festgestellt. Wir haben Word als grundlegende Speicherdarstellung festgelegt und die Beziehungen zwischen Speicher, Operationen und zusammengesetzten Strukturen vereinheitlicht.

Wir haben Unstimmigkeiten bei der Array-Indizierung und den Beziehungen zwischen Sammlungen festgestellt. Wir haben endliche, zusammenhängende Indizes standardisiert und die Beziehungen zwischen Array, File und Stream geklärt.

Wir haben Redundanzen und Mehrdeutigkeiten in Ausführungs- und Kompositionsbeziehungen festgestellt. Wir haben Prozeduren, Funktionen, Dispatcher und Objektbeziehungen präzisiert, um diese Probleme unter Wahrung der Implementierungsunabhängigkeit zu beheben.

## Speicher

### Word

Ein Wort ist jede im Speicher abgelegte Bitfolge $w \in \mathrm{Bit}^n$, sodass $n \in \mathbb{N}^+$.

### Address

Eine Adresse ist jedes Wort $a \in A$, wobei $A$ eine Menge von Wörtern ist, sodass $a$ einen Ort in einer angegebenen Speicherstruktur eindeutig identifiziert.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

Ein Zeiger ist jede Funktion $f_p : \{a\} \to B$, sodass $a \in A$ eine Adresse und $B$ eine Menge von Wörtern ist, wobei jede Anwendung von $f_p$ das an der durch $a$ identifizierten Speicherstelle abgelegte Wort auswertet.

#### Pointer()

> Sei $f_m : A \to B$ eine Speicherabbildung.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Eine Variable ist jede Funktion $f_v : \{k\} \to B$, sodass $k$ ein Schlüssel und $B$ eine Menge von Wörtern ist, wobei die Variable einen Zeiger erweitert, indem sie einen Schlüssel an eine Adresse bindet und das dort gespeicherte Wort auswertet.

#### Variable(k)

> Sei $f_b : \{k\} \to \{a\}$ die Bindungsfunktion der Variablen.
>
> Sei $f_p : \{a\} \to B$ ein Zeiger.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Eine Konstante ist jede Variable $f_c : \{k\} \to B$, sodass $k$ ein Schlüssel und $B$ eine Menge von Wörtern ist, wobei das $k$ zugeordnete Wort nach seiner Zuweisung nicht geändert werden kann.

#### Constant(k)

> Sei $b_0 \in B$ das $k$ zugewiesene Wort.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ nach der Zuweisung von $b_0$.

## Sammlungen

### Set

Eine Menge ist jede endliche, ungeordnete Sammlung verschiedener Wörter.

#### Set()

> Sei $B$ eine Menge von Wörtern.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

Eine Map ist jede Funktion $f_m : K \to V$, sodass $K$ eine Menge von Schlüsseln und $V$ eine Menge von Werten ist, wobei jedem Schlüssel genau ein Wert zugeordnet ist.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Ein Array ist jede Funktion $f_a : I \to V$, sodass $I \subseteq \mathbb{N}$ eine endliche, zusammenhängende Menge ganzzahliger Indizes und $V$ eine Menge von Wörtern ist, wobei jeder Index genau einen Wert identifiziert.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Eine Datei ist jedes Tupel $(f_m,d)$, sodass $d$ ein Array von Wörtern und $f_m : I \times \{d\} \to \mathrm{Array}$ eine durch ein Array von Wörtern dargestellte Metadatenfunktion ist, wobei $I$ eine endliche, zusammenhängende Menge ganzzahliger Indizes ist und $f_m$ bestimmt, wie Daten aus $d$ aufgelöst werden.

#### File(i)

> Sei $(f_m,d)$ eine Datei.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

Ein Stream ist jede Funktion $f_s$, sodass jede Anwendung von $f_s$ den nächsten Abschnitt $c$ in einer endlichen oder unendlichen Folge liefert, wobei $f_s$ einen Mechanismus zur sequenziellen Datenerzeugung oder zum sequenziellen Datenabruf festlegt.

#### Stream()

> Sei $f_c : K \to C$ eine Funktion zur Abschnittsauflösung, wobei $K \subseteq \mathbb{N}$ eine zusammenhängende Menge ganzzahliger Indizes und $C$ eine Menge von Abschnitten ist.
>
> Sei $k \in K$ der Index des nächsten Abschnitts.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$, wobei $k$ nach jeder Anwendung weitergeschaltet wird.

## Operationen

### Instruction

Eine Anweisung ist jedes Wort oder endliche Tupel von Wörtern $i \in B$, sodass $B$ eine Menge von Wörtern oder endlichen Tupeln von Wörtern ist, wobei jede Anweisung eine einzelne auszuführende Rechenoperation darstellt.

### Procedure

Eine Prozedur ist jede Variable $f_{proc} : \{k\} \to B$, sodass $f_{proc}(k)$ ein Array von Anweisungen $f_a : I \to V$ darstellt, wobei die Ausführung der Prozedur jede Anweisung in ihrer Indexreihenfolge ausführt.

#### Procedure(k)

> $\mathrm{Procedure}(k)$ ist die Ausführung jedes $f_a(i)$ in aufsteigender Reihenfolge von $i \in I$.

### Function

Eine Funktion ist jede Prozedur $f_{func} : \{k\} \to B$, deren Ausführung eine Adresse $a_r \in A$ zurückgibt, die das Ergebniswort oder das erste Wort eines das Ergebnis darstellenden Wort-Arrays identifiziert.

#### Function(k)

> Sei $f_m : A \to B$ eine Speicherabbildung, wobei $a_r \in A$ das Ergebniswort $r \in B$ identifiziert.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## Threading

### Process

Ein Prozess ist jeder begrenzte Ausführungsfluss, der Eingaben annimmt, eine oder mehrere Prozeduren oder Funktionen ausführt und Ausgaben erzeugt, wobei er eine eigenständige Transformationseinheit innerhalb eines Systems darstellt.

### Thread

Ein Thread ist jeder in einem Prozess enthaltene Ausführungsfluss, der einen Pfad zur Ausführung der zu diesem Prozess gehörenden Prozeduren oder Funktionen bereitstellt.

#### Thread(p)

> Sei $p$ ein Prozess.
>
> Sei $(w_0, \dots, w_n)$ ein endliches Tupel von Prozeduren oder Funktionen, die zu $p$ gehören.
>
> $\mathrm{Thread}(p)$ ist die Ausführung jedes $w_j$ in aufsteigender Reihenfolge von $j$ innerhalb von $p$.

### Dispatcher

Ein Dispatcher ist jedes Tupel $(t,W,f_d)$, sodass $t$ ein Thread, $W$ eine Menge als Arbeit akzeptierter Prozeduren oder Funktionen und $f_d$ eine Dispatch-Regel zur Auswahl von Arbeit aus $W$ ist, wobei der Dispatcher die ausgewählte Arbeit gemäß der Regel auf $t$ ausführen lässt.

#### Dispatcher(t)

> Sei $t$ ein Thread.
>
> Sei $W$ eine Menge vom Dispatcher akzeptierter Prozeduren oder Funktionen, wobei $\forall w \in W$, $w$ eine Prozedur oder Funktion ist.
>
> Sei $f_d : \mathcal{P}^+(W) \to W$ eine Dispatch-Regel, die Arbeit aus einer nichtleeren Teilmenge der akzeptierten Arbeit auswählt.
>
> $\mathrm{Dispatcher}(t)$ ist die Ausführung jedes ausgewählten $f_d(W')$ auf $t$, wobei $W' \subseteq W$, $W' \neq \varnothing$ und $f_d(W') \in W'$.

## Zusammengesetzte Strukturen

### Member

Ein Mitglied ist jedes Element $m \in M$, sodass $M$ eine Menge von Elementen und $f_o : K \to M$ die Mitgliederabbildung eines Objekts ist, wobei $m = f_o(k)$ für einen Schlüssel $k \in K$ gilt.

### Object

Ein Objekt ist jedes Tupel $(a,K,f_o)$, sodass $a \in A$ eine Adresse, $K$ eine Menge von Schlüsseln und $f_o : K \to M$ eine Mitgliederabbildung ist, wobei $M$ eine Menge von Elementen ist, sodass das Objekt eine adressierbare zusammengesetzte Struktur darstellen kann, deren Mitglieder über $f_o$ Schlüsseln zugeordnet sind.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Ein Feld ist jedes Tupel $(o,k,m)$, sodass $o = (a,K,f_o)$ ein Objekt, $k \in K$ ein Schlüssel und $m = f_o(k)$ ein Mitglied ist, wobei das Feld ein einzelnes über einen Schlüssel aufgelöstes Mitglied der Mitgliederabbildung des Objekts darstellt.

#### Field(o,k)

> Sei $o = (a,K,f_o)$ ein Objekt.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

Eine Methode ist jedes Feld $(o,k,m)$, sodass $m$ eine Prozedur oder Funktion ist, wobei die Methode ein ausführbares, einem Schlüssel zugeordnetes Mitglied eines Objekts darstellt.

#### Method(o,k)

> Sei $(o,k,m)$ ein Feld.
>
> $\mathrm{Method}(o,k) = (o,k,m)$, wobei $m$ eine Prozedur oder Funktion ist.

### Property

Eine Eigenschaft ist jedes Feld $(o,k,m)$, sodass $m = (X,f_a)$ eine Accessor-Abbildung ist, $X = \{\mathrm{Get}, \mathrm{Set}\}$ gilt und $f_a : X \to M$ jeden Accessor einem Mitglied zuordnet, wobei $f_a(\mathrm{Get})$ eine Funktion und $f_a(\mathrm{Set})$ eine Prozedur ist, sodass die Eigenschaft sowohl das Abruf- als auch das Zuweisungsverhalten eines einem Schlüssel zugeordneten Mitglieds definieren kann.

#### Property(o,k)

> Sei $(o,k,m)$ ein Feld, wobei $m = (X,f_a)$ eine Accessor-Abbildung ist.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> Sei $(o,k,(X,f_a))$ eine Eigenschaft.
>
> $\mathrm{Get}(o,k)$ ist die Anwendung von $f_a(\mathrm{Get})$.

#### Set(o,k)

> Sei $(o,k,(X,f_a))$ eine Eigenschaft.
>
> $\mathrm{Set}(o,k)$ ist die Anwendung von $f_a(\mathrm{Set})$.

### Structure

Eine Struktur (oft als `struct` abgekürzt) ist jedes Objekt $s = (a,K,f_s)$, sodass $K$ eine endliche Menge von Schlüsseln und $f_s : K \to M$ eine Mitgliederabbildung ist, deren Schlüssel nach der Zuweisung der Struktur nicht geändert werden können, wobei die Struktur ein spezialisiertes Objekt mit festem Layout der schlüsselgebundenen Mitglieder ist.

#### Structure(s,k)

> Sei $s = (a,K,f_s)$ eine Struktur.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Eine Klasse ist jedes Objekt $c = (a_c,K_c,f_c)$, sodass $K_c$ eine endliche Menge von Schlüsseln und $f_c : K_c \to M$ eine Abbildung von Mitgliedsdefinitionen ist, wobei die Klasse ein spezialisiertes Objekt ist, dessen schlüsselgebundene Mitglieder das zur Erzeugung anderer Objekte verwendete Mitgliederlayout definieren.

#### Class(c,a)

> Sei $c = (a_c,K_c,f_c)$ eine Klasse.
>
> Sei $a \in A$ eine Adresse, die einem aus $c$ erzeugten Objekt zugewiesen ist.
>
> Sei $f_o : K_c \to M$ eine Mitgliederabbildung gemäß den Definitionen von $f_c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

Eine Schnittstelle ist jedes Objekt $r = (a_r,K_r,f_r)$, sodass $K_r$ eine endliche Menge von Schlüsseln und $f_r : K_r \to M$ eine Abbildung von Mitgliedsanforderungen ist, wobei die Schnittstelle ein spezialisiertes Objekt ist, dessen schlüsselgebundene Mitglieder die von einem anderen Objekt bereitzustellenden Mitglieder definieren.

#### Interface(r,o)

> Sei $r = (a_r,K_r,f_r)$ eine Schnittstelle.
>
> Sei $o = (a,K,f_o)$ ein Objekt.
>
> Sei $f_v : M \times M \to \{0,1\}$ eine Validierungsregel, die bestimmt, ob ein Mitglied die Anforderungen eines anderen Mitglieds erfüllt.
>
> $\mathrm{Interface}(r,o)$ gilt, wenn $K_r \subseteq K$ und $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$.
