<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->
<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

# FDEFSPEC

<br/>

> **Spezifikation der grundlegenden Definitionen**<br/>
> Revision 1<br/>
> 23. März 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Alle Rechte vorbehalten.<br/>
> <br/>
> Die hier vorgestellten Definitionen und Konzepte beschreiben grundlegende mathematische Konstrukte und dürfen frei neu ausgedrückt werden.

## Einführung

Die **Spezifikation der grundlegenden Definitionen (FDEFSPEC)** legt die Kernkonzepte und die Terminologie fest, auf denen das CatalystUI-Ökosystem aufbaut. Ihr Zweck besteht darin, über Dokumentation, Spezifikationen, Implementierungen und Verifizierungsprüfungen hinweg ein einheitliches Verständnis dieser Konzepte zu schaffen und dadurch Konsistenz, Klarheit und Ausrichtung sicherzustellen.

Indem zentrale Begriffe und Beziehungen in einer präzisen und stabilen Form definiert werden, stellt FDEFSPEC einen gemeinsamen Bezugspunkt für höherstufige Spezifikationen bereit. Dadurch können Entwickler, Prüfer und Implementierer von derselben Grundlage aus beurteilen, ob eine Sprache, ein Dienst, ein Framework oder ein System als spezifikationskonform betrachtet werden kann.

> [!IMPORTANT]
>
> Wir drücken Definitionen mithilfe einer abgeleiteten Form der Notation der [Mengenlehre](https://en.wikipedia.org/wiki/Set_theory) aus. Dieser Ansatz ermöglicht präzise, eindeutige Definitionen, während Klarheit und Kürze erhalten bleiben. Wir strukturieren diese Definitionen so, dass sie leicht nachgeschlagen, klar interpretiert und in eine konsistente begriffliche Hierarchie eingeordnet werden können.

## Inhaltsverzeichnis

- [FDEFSPEC](#fdefspec)
  - [Einführung](#einführung)
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
  - [Numerische Werte](#numerische-werte)
    - [Bit](#bit)
    - [Nibble](#nibble)
      - [Nibble()](#nibble-1)
    - [Byte](#byte)
      - [Byte()](#byte-1)
      - [SByte()](#sbyte)
    - [Short](#short)
      - [Short()](#short-1)
      - [UShort()](#ushort)
    - [Int](#int)
      - [Int()](#int-1)
      - [UInt()](#uint)
    - [Long](#long)
      - [Long()](#long-1)
      - [ULong()](#ulong)
    - [Single](#single)
      - [Single()](#single-1)
    - [Double](#double)
      - [Double()](#double-1)
    - [Boolean](#boolean)
      - [Boolean()](#boolean-1)
  - [Textcodierung](#textcodierung)
    - [Text Encoding](#text-encoding)
      - [Text Encoding()](#text-encoding-1)
    - [Codepoint](#codepoint)
      - [Codepoint()](#codepoint-1)
    - [ASCII Code Unit](#ascii-code-unit)
      - [ASCII Code Unit()](#ascii-code-unit-1)
      - [ASCII()](#ascii)
    - [CP1252 Code Unit](#cp1252-code-unit)
      - [CP1252 Code Unit()](#cp1252-code-unit-1)
      - [CP1252()](#cp1252)
    - [UTF-8 Code Unit](#utf-8-code-unit)
      - [UTF-8 Code Unit()](#utf-8-code-unit-1)
      - [UTF-8()](#utf-8)
    - [UTF-16LE Code Unit](#utf-16le-code-unit)
      - [UTF-16LE Code Unit()](#utf-16le-code-unit-1)
      - [UTF-16LE()](#utf-16le)
  - [Betriebsstatus](#betriebsstatus)
    - [Status Code](#status-code)
      - [Status Code()](#status-code-1)
      - [Status Code Level()](#status-code-level)
      - [Status Code Definition()](#status-code-definition)
        - [Success](#success)
        - [Warning](#warning)
        - [Error](#error)
        - [Fatal](#fatal)
    - [Context Code](#context-code)
      - [Context Code()](#context-code-1)
    - [Operation Code](#operation-code)
      - [Operation Code()](#operation-code-1)
    - [Detail Code](#detail-code)
      - [Detail Code()](#detail-code-1)
    - [Result](#result)
      - [Result()](#result-1)

## Numerische Werte

### Bit

Ein Bit ist jedes $b \in \{0,1\}$.

### Nibble

Ein Nibble ist jedes $(b_0,\dots,b_3)$, sodass für alle $i \in \{0,\dots,3\}$ gilt: $b_i \in \mathrm{Bit}$.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

Ein Byte ist jedes $(b_0,\dots,b_7)$, sodass für alle $i \in \{0,\dots,7\}$ gilt: $b_i \in \mathrm{Bit}$.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

Ein Short ist jedes $(b_0,\dots,b_{15})$, sodass für alle $i \in \{0,\dots,15\}$ gilt: $b_i \in \mathrm{Bit}$.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

Ein Integer ist jedes $(b_0,\dots,b_{31})$, sodass für alle $i \in \{0,\dots,31\}$ gilt: $b_i \in \mathrm{Bit}$.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

Ein Long ist jedes $(b_0,\dots,b_{63})$, sodass für alle $i \in \{0,\dots,63\}$ gilt: $b_i \in \mathrm{Bit}$.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

Ein Single ist jedes $(b_0,\dots,b_{31})$, sodass für alle $i \in \{0,\dots,31\}$ gilt: $b_i \in \mathrm{Bit}$.

#### Single()

Die folgende Definition entspricht dem IEEE-754-Standard für Gleitkommadarstellung mit einfacher Genauigkeit. Sie definiert, wie eine 32-Bit-Binärfolge als Gleitkommazahl interpretiert wird, einschließlich Sonderfällen für Null, Unendlichkeit und NaN (Not a Number).

> Sei $s = b_0$
>
> Sei $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Sei $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

Ein Double ist jedes $(b_0,\dots,b_{63})$, sodass für alle $i \in \{0,\dots,63\}$ gilt: $b_i \in \mathrm{Bit}$.

#### Double()

Die folgende Definition entspricht dem IEEE-754-Standard für Gleitkommadarstellung mit doppelter Genauigkeit. Sie definiert, wie eine 64-Bit-Binärfolge als Gleitkommazahl interpretiert wird, einschließlich Sonderfällen für Null, Unendlichkeit und NaN (Not a Number).

> Sei $s = b_0$
>
> Sei $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Sei $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

Ein Boolean ist jedes $b \in \{0,1\}$.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{wobei } b \in \mathrm{Bit}$

## Textcodierung

### Text Encoding

Eine Textcodierung ist als die folgende Menge definiert:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Text Encoding()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Ein Unicode-Codepoint ist jedes $e \in \mathbb{Z}$, sodass $0 \leq e \leq 0x10FFFF$ gilt.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

Eine ASCII-Codeeinheit ist jedes $(b_0,\dots,b_6)$, sodass für alle $i \in \{0,\dots,6\}$ gilt: $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

Es ist üblich, eine ASCII-Codeeinheit aus Leistungs- und Kompatibilitätsgründen als Byte darzustellen, indem ein führendes Nullbit angehängt wird. In solchen Fällen wird die ASCII-Codeeinheit wie folgt dargestellt:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Andernfalls:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Im Rahmen dieses Theorems sind beide Definitionen zulässige Darstellungen einer ASCII-Codeeinheit. Aus Konsistenzgründen verwenden wir die erste Definition, wenn ASCII-Codeeinheiten als Bytes dargestellt werden, und die zweite Definition, wenn sie als 7-Bit-Folgen dargestellt werden.

#### ASCII()

ASCII ist ein nullterminiertes endliches Tupel $(u_0, \dots, u_k, u_{k+1})$, sodass gilt:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ ist eine ASCII-Codeeinheit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

Die Folge wird als nullterminiert bezeichnet.

### CP1252 Code Unit

Eine CP1252-Codeeinheit ist jedes $(b_0,\dots,b_7)$, sodass für alle $i \in \{0,\dots,7\}$ gilt: $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 ist ein nullterminiertes endliches Tupel $(u_0, \dots, u_k, u_{k+1})$, sodass gilt:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ ist eine CP1252-Codeeinheit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

Die Folge wird als nullterminiert bezeichnet.

### UTF-8 Code Unit

Eine UTF-8-Codeeinheit ist jedes $(b_0,\dots,b_7)$, sodass für alle $i \in \{0,\dots,7\}$ gilt: $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 ist ein nullterminiertes endliches Tupel $(u_0, \dots, u_k, u_{k+1})$, sodass gilt:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ ist eine UTF-8-Codeeinheit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

Die Folge wird als nullterminiert bezeichnet.

### UTF-16LE Code Unit

Eine UTF-16LE-Codeeinheit ist jedes $(b_0,\dots,b_{15})$, sodass für alle $i \in \{0,\dots,15\}$ gilt: $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE ist ein nullterminiertes endliches Tupel $(u_0, \dots, u_k, u_{k+1})$, sodass gilt:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ ist eine UTF-16LE-Codeeinheit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

Die Folge wird als nullterminiert bezeichnet.

## Betriebsstatus

### Status Code

Ein Statuscode ist jedes $(b_0,\dots,b_7)$, sodass für alle $i \in \{0,\dots,7\}$ gilt: $b_i \in \mathrm{Bit}$.

Eine Statuscode-Ebene ist als die folgende Menge definiert:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Status Code()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Status Code Level()

Die Menge der Statuscode-Werte ist der Bereich $[0, 255]$, der in vier Ebenen unterteilt ist:

> Sei $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Status Code Definition()

Alle Statuscodes besitzen explizite Definitionen. Jeder Statuscode, der nicht in der folgenden Liste enthalten ist, ist für zukünftige Verwendung reserviert; seine Bedeutung ist undefiniert. Die Ebene eines Statuscodes wird durch $\mathrm{Status\ Code\ Level}(s)$ bestimmt.

In der folgenden Liste wird die Eingabe $s$ aus Gründen der Lesbarkeit als hexadezimaler Wert dargestellt. Jeder definierte Statuscode gibt seine entsprechende Ebene, Kategorie, Unterkategorie, Beschreibung und gegebenenfalls Detailinformation an.

Diese Liste kann erweitert werden, wenn neue Statuscodes definiert werden. Jeder neu definierte Statuscode darf nicht mit bestehenden Codes kollidieren und muss eine klar dokumentierte Bedeutung haben.

Um Informationen zu übermitteln, die nicht durch einen definierten Statuscode dargestellt werden, sollte der Kontextcode, Operationscode oder Detailcode verwendet werden.

##### Success

| Code | Ebene | Kategorie | Beschreibung | Detail |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | Die Operation wurde erfolgreich abgeschlossen. | |
| `0x01` | SUCCESS | NOOP | Die Operation wurde erfolgreich abgeschlossen, ohne eine Aktion auszuführen. | |

##### Warning

| Code | Ebene | Kategorie | Beschreibung | Detail |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | Die Operation wurde abgeschlossen, aber das Ergebnis kann unerwartet oder unerwünscht sein. | |
| `0x41` | WARNING | PARTIAL | Die Operation wurde abgeschlossen, jedoch nur teilweise. Die Ausgabe kann unvollständig sein. | |
| `0x42` | WARNING | DEPRECATED | Die Operation wurde abgeschlossen, verwendete jedoch ein veraltetes Feature oder Verhalten. Die Operation funktioniert in Zukunft möglicherweise nicht mehr. | |

##### Error

| Code | Ebene | Kategorie | Beschreibung | Detail |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | Die Operation ist aufgrund eines behebbaren Fehlers fehlgeschlagen. | |
| `0x81` | ERROR | INVALID_ARGUMENT | Die Operation ist fehlgeschlagen. Ein Argument war ungültig oder außerhalb des zulässigen Bereichs. | Der Index des ungültigen Arguments, beginnend bei 0 von links nach rechts in der Signatur der Funktion. |
| `0x82` | ERROR | INVALID_STATE | Die Operation ist fehlgeschlagen. Das System befindet sich in einem inkonsistenten, beschädigten oder anderweitig ungültigen Zustand. | |
| `0x83` | ERROR | MALFORMED_INPUT | Die Operation ist fehlgeschlagen. Eine erforderliche Eingabe war fehlerhaft geformt oder enthielt ungültige Daten. | |
| `0x84` | ERROR | ACCESS_DENIED | Die Operation ist fehlgeschlagen, weil eine erforderliche Ressource den Zugriff verweigert hat. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | Die Operation ist fehlgeschlagen, weil das angeforderte Feature oder Verhalten noch nicht implementiert ist. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | Die Operation ist fehlgeschlagen, weil das Zielsystem oder die Konfiguration das angeforderte Feature nicht unterstützt. | |
| `0x87` | ERROR | TIMEOUT | Die Operation ist fehlgeschlagen, weil vor dem Abschluss ein erforderliches Timeout eingetreten ist. | |
| `0x88` | ERROR | NOT_FOUND | Die Operation ist fehlgeschlagen, weil eine erforderliche Ressource nicht existiert. | |
| `0x89` | ERROR | INTERRUPTED | Die Operation ist fehlgeschlagen, weil ein externes Ereignis sie unterbrochen hat. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | Die Operation ist fehlgeschlagen, weil eine erforderliche Abhängigkeit fehlgeschlagen ist. | Der `STATUS_CODE`-Wert der Abhängigkeit. Aufrufer werden ermutigt, aber nicht verpflichtet, die fehlgeschlagene Abhängigkeit über das Feld `OP_CODE` zu identifizieren. |
| `0x90` | ERROR | BUFFER_OVERFLOW | Die Operation ist fehlgeschlagen. Ein Puffer war zu klein, um die erforderlichen Daten aufzunehmen. | |
| `0x91` | ERROR | ALLOCATION_FAILED | Die Operation ist fehlgeschlagen. Eine Speicherzuweisungsanforderung war nicht erfolgreich. | |
| `0xA0` | ERROR | IO_ERROR | Die Operation ist fehlgeschlagen. Während der Operation ist ein E/A-Fehler aufgetreten. | |

##### Fatal

| Code | Ebene | Kategorie | Beschreibung | Detail |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | Die Operation ist aufgrund eines nicht behebbaren Fehlers fehlgeschlagen. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | Die Operation ist fehlgeschlagen, weil das System eine grundlegende Invariante verletzt hat, was auf einen kritischen Logikfehler oder Datenbeschädigung hinweist. | |

### Context Code

Ein Kontextcode ist jedes $(b_0,\dots,b_7)$, sodass für alle $i \in \{0,\dots,7\}$ gilt: $b_i \in \mathrm{Bit}$.

#### Context Code()

Ein Kontextcode-Wert stellt zusätzliche Kontextinformationen über eine abgeschlossene Operation dar, wie sie durch die zugehörige Operation definiert werden; er muss null sein, wenn die Statuscode-Ebene $\mathrm{Success}$ ist, und ist andernfalls implementierungsdefiniert.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Operation Code

Ein Operationscode ist jedes $(b_0,\dots,b_7)$, sodass für alle $i \in \{0,\dots,7\}$ gilt: $b_i \in \mathrm{Bit}$.

#### Operation Code()

Ein Operationscode-Wert stellt die Operation dar, die mit einem Ergebnis verbunden ist. Seine Bedeutung wird durch die entsprechende Operation und deren Dokumentation definiert. Undefinierte Werte gelten als unbekannt.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Detail Code

Ein Detailcode ist jedes $(b_0,\dots,b_7)$, sodass für alle $i \in \{0,\dots,7\}$ gilt: $b_i \in \mathrm{Bit}$.

#### Detail Code()

Ein Detailcode-Wert stellt zusätzliche Informationen über eine abgeschlossene Operation dar; seine Bedeutung wird durch den zugehörigen Status-, Kontext- oder Operationscode definiert, in dieser Reihenfolge, und ist andernfalls unbekannt.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Result

> [!TIP]
>
> Ein Ergebniswert kann als 32-Bit-Integer dargestellt werden. In Big-Endian-Byte-Reihenfolge erscheint der Wert als `0xSSCCOODD`, wobei `SS`, `CC`, `OO` und `DD` jeweils dem Statuscode, Kontextcode, Operationscode und Detailcode entsprechen. In Little-Endian-Byte-Reihenfolge erscheint derselbe Wert als `0xDDOOCCSS`. Jede der beiden Byte-Reihenfolgen darf verwendet werden, sofern sie konsistent angewendet und dokumentiert wird.

Ein Ergebnis ist jedes $(b_0,\dots,b_{31})$, sodass für alle $i \in \{0,\dots,31\}$ gilt: $b_i \in \mathrm{Bit}$.

Ein Ergebnis wird in vier geordnete Bytes unterteilt:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

wobei $s$, $c$, $o$ und $d$ die Bestandteile des Ergebnisses sind.

#### Result()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
