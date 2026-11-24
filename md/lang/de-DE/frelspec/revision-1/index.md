<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->
<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

# FRELSPEC

<br/>

> **Spezifikation der grundlegenden Relationen**<br/>
> Revision 1<br/>
> 7. Juli 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Alle Rechte vorbehalten.<br/>
> <br/>
> Die hier vorgestellten Definitionen und Konzepte beschreiben grundlegende mathematische Konstrukte und dürfen frei neu ausgedrückt werden.

## Einführung

Die **Spezifikation der grundlegenden Relationen (FRELSPEC)** legt die zentralen relationalen Strukturen fest, auf denen das CatalystUI-Ökosystem aufbaut. Ihr Zweck besteht darin, über Dokumentation, Spezifikationen, Implementierungen und Verifizierungsprüfungen hinweg ein einheitliches Verständnis davon zu schaffen, wie Werte, Speicher, Operationen und zusammengesetzte Strukturen miteinander verbunden sind, und dadurch Konsistenz, Klarheit und Ausrichtung sicherzustellen.

Indem Beziehungen zwischen grundlegenden Konzepten in einer präzisen und stabilen Form definiert werden, stellt FRELSPEC einen gemeinsamen Bezugspunkt für höherstufige Spezifikationen bereit. Dadurch können Entwickler, Prüfer und Implementierer von derselben Grundlage aus beurteilen, ob eine Sprache, ein Dienst, ein Framework oder ein System die relationalen Konstrukte darstellen kann, die erforderlich sind, um als spezifikationskonform zu gelten.

> [!IMPORTANT]
>
> Wir drücken Definitionen mithilfe einer abgeleiteten Form der Notation der [Mengenlehre](https://en.wikipedia.org/wiki/Set_theory) aus. Dieser Ansatz ermöglicht präzise, eindeutige Definitionen, während Klarheit und Kürze erhalten bleiben. Wir strukturieren diese Definitionen so, dass sie leicht nachgeschlagen, klar interpretiert und in eine konsistente begriffliche Hierarchie eingeordnet werden können.

## Inhaltsverzeichnis

- [FRELSPEC](#frelspec)
  - [Einführung](#einführung)
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
  - [Sammlungen](#sammlungen)
    - [Set](#set)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [Speicher](#speicher)
    - [Address](#address)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
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

## Sammlungen

### Set

Ein Set ist jede Sammlung unterschiedlicher Elemente.

### Map

Eine Map ist jede Funktion $f_m : K \to V$, sodass $K$ eine Menge von Schlüsseln und $V$ eine Menge von Werten ist.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Ein Array ist jede Funktion $f_a : I \to V$, sodass $I \subset \mathbb{N}$ gilt, $I$ eine endliche, zusammenhängende Menge von Ganzzahlen ist und $V$ eine Menge von Werten ist.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Eine Datei ist jede Funktion $f_f : I \to B$, sodass $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ eine endliche, zusammenhängende Menge von Ganzzahlen ist und $B$ eine Menge von Bytes ist, wobei $f_f$ aus einem Mechanismus persistenter Datenspeicherung stammt.

#### File(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Stream

Ein Stream ist jede Funktion $f_s$, sodass jede Anwendung von $f_s$ den nächsten Chunk $f_c : I \to B$ in einer Bytefolge liefert, wobei $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ eine endliche, zusammenhängende Menge von Ganzzahlen ist, $B$ eine Menge von Bytes ist und $f_s$ aus einem Mechanismus sequenzieller Datenerzeugung oder -abfrage stammt.

#### Stream()

> Sei $c_k : I_k \to B$ der Chunk, der von der $k$-ten Anwendung von $f_s$ zurückgegeben wird.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ bei der $k$-ten Anwendung.

## Speicher

### Address

Eine Adresse ist jedes Element $a \in A$, sodass $A$ eine Menge von Adressen ist, wobei jede Adresse $a$ einen Ort in einer Speicherstruktur eindeutig identifiziert.

### Pointer

Ein Pointer ist jede Funktion $f_p : \{a\} \to B$, sodass $a \in A$ eine Adresse und $B$ eine Menge von Bytearrays ist, wobei jede Anwendung von $f_p$ das Bytearray auswertet, das an der durch die gebundene Adresse identifizierten Speicherstelle gespeichert ist.

#### Pointer()

> Sei $f_m : A \to B$ eine Speicher-Map.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Eine Variable ist jede Funktion $f_v : \{k\} \to B$, sodass $k$ ein Schlüssel und $B$ eine Menge von Bytearrays ist, wobei die Variable einen Pointer erweitert, indem sie einen Schlüssel an eine Adresse bindet und das Bytearray auswertet, das an der durch diese Adresse identifizierten Speicherstelle gespeichert ist.

#### Variable(k)

> Sei $f_b : \{k\} \to \{a\}$ die Bindungsfunktion der Variable.
>
> Sei $f_p : \{a\} \to B$ ein Pointer.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Eine Konstante ist jede Variable $f_c : \{k\} \to B$, sodass $k$ ein Schlüssel und $B$ eine Menge von Bytearrays ist, wobei das mit $k$ verbundene Bytearray nach seiner Zuweisung nicht geändert werden kann.

#### Constant(k)

> Sei $b_0 \in B$ das Bytearray, das $k$ zugewiesen wurde.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ nachdem $b_0$ zugewiesen wurde.


## Operationen

### Instruction

Eine Instruktion ist jedes Bytearray $i \in B$, sodass $B$ eine Menge von Bytearrays ist, wobei jede Instruktion eine einzelne auszuführende Rechenoperation darstellt.

### Procedure

Eine Prozedur ist jede Variable $f_{proc} : \{k\} \to B$, sodass $k$ ein Schlüssel und $B$ eine Menge von Bytearrays ist, wobei jede Anwendung der Prozedur das mit $k$ verbundene Bytearray als endliche geordnete Folge von Instruktionen auswertet und diese Instruktionen in ihrer dargestellten Reihenfolge ausführt, ohne einen Rückgabewert zu definieren.

#### Procedure(k)

> Sei $b \in B$, sodass $f_{proc}(k) = b$ gilt.
>
> Sei $(i_0,\dots,i_n)$ die endliche geordnete Folge von Instruktionen, die durch $b$ dargestellt wird, wobei $\forall j \in \{0,\dots,n\}, i_j$ eine Instruktion ist.
>
> $\mathrm{Procedure}(k)$ ist die Ausführung jedes $i_j$ in aufsteigender Reihenfolge von $j$.

### Function

Eine Funktion ist jede Prozedur $f_{func} : \{k\} \to B$, sodass $k$ ein Schlüssel und $B$ eine Menge von Bytearrays ist, wobei jede Anwendung der Funktion das mit $k$ verbundene Bytearray als endliche geordnete Folge von Instruktionen auswertet, diese Instruktionen in ihrer dargestellten Reihenfolge ausführt und nach Abschluss der Ausführung ein resultierendes Bytearray einer Adresse im Speicher zuweist, die als Rückgabewert der Funktion ausgewertet werden kann.

#### Function(k)

> Sei $b \in B$, sodass $f_{func}(k) = b$ gilt.
>
> Sei $(i_0,\dots,i_n)$ die endliche geordnete Folge von Instruktionen, die durch $b$ dargestellt wird, wobei $\forall j \in \{0,\dots,n\}, i_j$ eine Instruktion ist.
>
> Sei $a_r \in A$ eine Adresse, die nach Abschluss der Ausführung zugewiesen wurde.
>
> Sei $f_m : A \to B$ eine Speicher-Map.
>
> $\mathrm{Function}(k)$ ist die Ausführung jedes $i_j$ in aufsteigender Reihenfolge von $j$, wobei $\exists b_r \in B : f_m(a_r) = b_r$ gilt, nachdem die Ausführung abgeschlossen wurde.
>
> $\mathrm{Function}(k) = b_r$

## Threading

### Process

Ein Prozess ist jeder begrenzte Ausführungsfluss, der Eingabe annimmt, eine oder mehrere Instruktionen ausführt und Ausgabe erzeugt, wobei der Prozess eine eigenständige Transformationseinheit innerhalb eines Systems darstellt.

### Thread

Ein Thread ist jeder Ausführungsfluss, der innerhalb eines Prozesses enthalten ist, wobei der Thread einen Pfad bereitstellt, über den geordnete Folgen von Instruktionen, die zu diesem Prozess gehören, ausgeführt werden können.

#### Thread(p)

> Sei $p$ ein Prozess.
>
> Sei $(i_0,\dots,i_n)$ eine endliche geordnete Folge von Instruktionen, die zu $p$ gehört.
>
> $\mathrm{Thread}(p)$ ist die Ausführung jedes $i_j$ in aufsteigender Reihenfolge von $j$ innerhalb von $p$.

### Dispatcher

Ein Dispatcher ist jedes Tupel $(t,W,f_d)$, sodass $t$ ein Thread ist, $W$ eine Menge von Prozeduren oder Funktionen ist, die als Arbeit akzeptiert werden, und $f_d$ eine Dispatch-Regel ist, die Arbeit aus $W$ auswählt, wobei der Dispatcher veranlasst, dass die ausgewählte Arbeit gemäß der Dispatch-Regel auf $t$ ausgeführt wird.

#### Dispatcher(t)

> Sei $t$ ein Thread.
>
> Sei $W$ eine Menge von Prozeduren oder Funktionen, die vom Dispatcher akzeptiert werden, wobei $\forall w \in W$ gilt: $w$ ist eine Prozedur oder Funktion.
>
> Sei $f_d : \mathcal{P}(W) \to W$ eine Dispatch-Regel, die Arbeit aus einer nichtleeren Teilmenge akzeptierter Arbeit auswählt.
>
> $\mathrm{Dispatcher}(t)$ ist die Ausführung jedes ausgewählten $f_d(W')$ auf $t$, wobei $W' \subseteq W$ und $W' \neq \varnothing$ gilt.

## Zusammengesetzte Strukturen

### Member

Ein Member ist jedes Element $m \in M$, sodass $M$ eine Menge von Membern ist, wobei ein Member ein Wert ist, der einem Schlüssel innerhalb der Member-Map eines Objekts zugewiesen werden kann.

### Object

Ein Objekt ist jedes Tupel $(a,K,f_o)$, sodass $a \in A$ eine Adresse ist, $K$ eine Menge von Schlüsseln ist und $f_o : K \to M$ eine Member-Map ist, wobei $M$ eine Menge von Membern ist. Dadurch kann das Objekt eine adressierbare zusammengesetzte Struktur darstellen, deren Member über $f_o$ Schlüsseln zugewiesen werden.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Ein Feld ist jedes Tupel $(o,k,m)$, sodass $o = (a,K,f_o)$ ein Objekt ist, $k \in K$ ein Schlüssel ist, $m \in M$ ein Member ist und $f_o(k) = m$ gilt, wobei das Feld einen schlüsselgebundenen Member darstellt, der aus der Member-Map eines Objekts aufgelöst wird.

#### Field(k)

> Sei $o = (a,K,f_o)$ ein Objekt.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Method

Eine Methode ist jedes Feld $(o,k,m)$, sodass $m$ eine Prozedur oder Funktion ist, wobei die Methode einen schlüsselgebundenen ausführbaren Member eines Objekts darstellt.

#### Method(k)

> Sei $o = (a,K,f_o)$ ein Objekt.
>
> Sei $k \in K$ ein Schlüssel.
>
> Sei $m \in M$ ein Member, sodass $f_o(k) = m$ gilt.
>
> $\mathrm{Method}(o,k) = (o,k,m)$, wenn $m$ eine Prozedur oder Funktion ist.

### Property

Eine Eigenschaft ist jedes Feld $(o,k,m)$, sodass $m = (A,f_a)$ eine Accessor-Map ist, $A = \{ \mathrm{Get}, \mathrm{Set} \}$ gilt und $f_a : A \to M$ jeden Accessor einem Member zuordnet, wobei $f_a(\mathrm{Get})$ eine Funktion und $f_a(\mathrm{Set})$ eine Prozedur ist. Dadurch kann die Eigenschaft sowohl das Abruf- als auch das Zuweisungsverhalten eines schlüsselgebundenen Members definieren.

#### Property(k)

> Sei $(o,k,m)$ ein Feld.
>
> Sei $m = (A,f_a)$ eine Accessor-Map.
>
> Sei $A = \{ \mathrm{Get}, \mathrm{Set} \}$.
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$, wobei $g$ eine Funktion ist.
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$, wobei $s$ eine Prozedur ist.
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> Sei $(o,k,(A,f_a))$ eine Eigenschaft.
>
> Sei $g = f_a(\mathrm{Get})$.
>
> $\mathrm{Get}(k)$ ist die Anwendung von $g$.

#### Set(k)

> Sei $(o,k,(A,f_a))$ eine Eigenschaft.
>
> Sei $s = f_a(\mathrm{Set})$.
>
> $\mathrm{Set}(k)$ ist die Anwendung von $s$.

### Structure

Eine Struktur (häufig als `struct` abgekürzt) ist jedes Objekt $s = (a,K,f_s)$, sodass $K$ eine endliche Menge von Schlüsseln ist und $f_s : K \to M$ eine Member-Map ist, die nach der Zuweisung der Struktur nicht geändert werden kann, wobei die Struktur ein spezialisiertes Objekt ist, dessen schlüsselgebundenes Member-Layout fest ist.

#### Structure(k)

> Sei $s = (a,K,f_s)$ eine Struktur.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Eine Klasse ist jedes Objekt $c = (a_c,K_c,f_c)$, sodass $K_c$ eine endliche Menge von Schlüsseln ist und $f_c : K_c \to M$ eine Member-Definitions-Map ist, wobei die Klasse ein spezialisiertes Objekt ist, dessen schlüsselgebundene Member das Member-Layout definieren, mit dem andere Objekte erzeugt werden.

#### Class(a)

> Sei $c = (a_c,K_c,f_c)$ eine Klasse.
>
> Sei $a \in A$ eine Adresse, die einem aus $c$ erzeugten Objekt zugewiesen wurde.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interface

Ein Interface ist jedes Objekt $r = (a_r,K_r,f_r)$, sodass $K_r$ eine endliche Menge von Schlüsseln ist und $f_r : K_r \to M$ eine Member-Anforderungs-Map ist, wobei das Interface ein spezialisiertes Objekt ist, dessen schlüsselgebundene Member die Member definieren, die von einem anderen Objekt bereitgestellt werden müssen.

#### Interface(o)

> Sei $r = (a_r,K_r,f_r)$ ein Interface.
>
> Sei $o = (a,K,f_o)$ ein Objekt.
>
> $\mathrm{Interface}(r,o)$ gilt, wenn $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
