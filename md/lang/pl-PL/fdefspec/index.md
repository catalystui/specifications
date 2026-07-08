<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza-człowieka. -->
<!-- Usuń te wiersze w pull requeście po zweryfikowaniu tłumaczenia. -->

# FDEFSPEC

<br/>

> **Specyfikacja definicji podstawowych**<br/>
> Rewizja 1<br/>
> 23 marca 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Wszelkie prawa zastrzeżone.<br/>
> <br/>
> Przedstawione tutaj definicje i pojęcia opisują podstawowe konstrukcje matematyczne i mogą być swobodnie wyrażane ponownie.

## Wprowadzenie

**Foundational Definitions Specification (FDEFSPEC)** ustanawia podstawowe pojęcia i terminologię, które stanowią fundament ekosystemu CatalystUI. Jej celem jest zapewnienie wspólnego rozumienia tych pojęć w dokumentacji, specyfikacjach, implementacjach oraz przeglądach weryfikacyjnych, tak aby zachować spójność, jasność i zgodność.

Definiując kluczowe terminy i relacje w precyzyjnej, stabilnej formie, FDEFSPEC zapewnia wspólny punkt odniesienia dla specyfikacji wyższego poziomu. Dzięki temu deweloperzy, recenzenci i implementatorzy mogą opierać swoje rozumowanie na tym samym fundamencie, gdy ustalają, czy język, usługa, framework albo system może zostać uznany za zgodny ze specyfikacją.

> [!IMPORTANT]
>
> Definicje wyrażamy za pomocą pochodnej formy zapisu [teorii zbiorów](https://en.wikipedia.org/wiki/Set_theory). Takie podejście zapewnia precyzyjne, jednoznaczne definicje, zachowując jednocześnie jasność i zwięzłość. Strukturyzujemy te definicje tak, aby wspierały łatwe odwoływanie się, jasną interpretację i spójną hierarchię pojęciową.

## Spis treści

- [FDEFSPEC](#fdefspec)
  - [Wprowadzenie](#introduction)
  - [Spis treści](#table-of-contents)
  - [Typy liczbowe](#numerics)
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
  - [Kodowanie tekstu](#text-encoding)
    - [Kodowanie tekstu](#text-encoding-1)
      - [Text Encoding()](#text-encoding-2)
    - [Kodpoint](#codepoint)
      - [Kodpoint()](#codepoint-1)
    - [ASCII Kod Unit](#ascii-code-unit)
      - [ASCII Kod Unit()](#ascii-code-unit-1)
      - [ASCII()](#ascii)
    - [CP1252 Kod Unit](#cp1252-code-unit)
      - [CP1252 Kod Unit()](#cp1252-code-unit-1)
      - [CP1252()](#cp1252)
    - [UTF-8 Kod Unit](#utf-8-code-unit)
      - [UTF-8 Kod Unit()](#utf-8-code-unit-1)
      - [UTF-8()](#utf-8)
    - [UTF-16LE Kod Unit](#utf-16le-code-unit)
      - [UTF-16LE Kod Unit()](#utf-16le-code-unit-1)
      - [UTF-16LE()](#utf-16le)
  - [Status operacji](#operation-status)
    - [Status Kod](#status-code)
      - [Status Kod()](#status-code-1)
      - [Status Kod Poziom()](#status-code-level)
      - [Status Kod Definition()](#status-code-definition)
        - [Sukces](#success)
        - [Ostrzeżenie](#warning)
        - [Błąd](#error)
        - [Krytyczny](#fatal)
    - [Context Kod](#context-code)
      - [Context Kod()](#context-code-1)
    - [Operation Kod](#operation-code)
      - [Operation Kod()](#operation-code-1)
    - [Szczegół Kod](#detail-code)
      - [Szczegół Kod()](#detail-code-1)
    - [Wynik](#result)
      - [Result()](#result-1)

## Typy liczbowe

### Bit

Bit to dowolne $b \in \{0,1\}$.

### Nibble

Nibble to dowolne $(b_0,\dots,b_3)$ takie, że dla każdego $i \in \{0,\dots,3\}$ zachodzi $b_i \in \mathrm{Bit}$.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

Byte to dowolne $(b_0,\dots,b_7)$ takie, że dla każdego $i \in \{0,\dots,7\}$ zachodzi $b_i \in \mathrm{Bit}$.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

Short to dowolne $(b_0,\dots,b_{15})$ takie, że dla każdego $i \in \{0,\dots,15\}$ zachodzi $b_i \in \mathrm{Bit}$.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

Integer to dowolne $(b_0,\dots,b_{31})$ takie, że dla każdego $i \in \{0,\dots,31\}$ zachodzi $b_i \in \mathrm{Bit}$.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

Long to dowolne $(b_0,\dots,b_{63})$ takie, że dla każdego $i \in \{0,\dots,63\}$ zachodzi $b_i \in \mathrm{Bit}$.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

Single to dowolne $(b_0,\dots,b_{31})$ takie, że dla każdego $i \in \{0,\dots,31\}$ zachodzi $b_i \in \mathrm{Bit}$.

#### Single()

Poniższa definicja jest zgodna ze standardem IEEE 754 dla reprezentacji liczb zmiennoprzecinkowych pojedynczej precyzji. Określa ona, jak 32-bitowy ciąg binarny jest interpretowany jako liczba zmiennoprzecinkowa, w tym szczególne przypadki zera, nieskończoności i NaN (Not a Number).

> Niech $s = b_0$
>
> Niech $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Niech $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

Double to dowolne $(b_0,\dots,b_{63})$ takie, że dla każdego $i \in \{0,\dots,63\}$ zachodzi $b_i \in \mathrm{Bit}$.

#### Double()

Poniższa definicja jest zgodna ze standardem IEEE 754 dla reprezentacji liczb zmiennoprzecinkowych podwójnej precyzji. Określa ona, jak 64-bitowy ciąg binarny jest interpretowany jako liczba zmiennoprzecinkowa, w tym szczególne przypadki zera, nieskończoności i NaN (Not a Number).

> Niech $s = b_0$
>
> Niech $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Niech $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

Boolean to dowolne $b \in \{0,1\}$.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{gdzie } b \in \mathrm{Bit}$

## Kodowanie tekstu

### Kodowanie tekstu

Kodowanie tekstu jest zdefiniowane jako następujący zbiór:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Kodowanie tekstu()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Punkt kodowy

Punkt kodowy Unicode to dowolne $e \in \mathbb{Z}$ takie, że $0 \leq e \leq 0x10FFFF$.

#### Punkt kodowy()

> $\mathrm{Kodpoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### Jednostka kodowa ASCII

An ASCII code unit is any $(b_0,\dots,b_6)$ takie, że for all $i \in \{0,\dots,6\}$, $b_i \in \mathrm{Bit}$.

#### Jednostka kodowa ASCII()

Ze względów wydajnościowych i zgodnościowych często reprezentuje się jednostkę kodową ASCII jako bajt przez dodanie początkowego bitu zerowego. W takich przypadkach jednostka kodowa ASCII jest reprezentowana następująco:

> $\mathrm{ASCII\ Kod\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

W przeciwnym razie:

> $\mathrm{ASCII\ Kod\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Na potrzeby tego twierdzenia obie definicje są dopuszczalnymi reprezentacjami jednostki kodowej ASCII. Dla spójności będziemy używać pierwszej definicji przy reprezentowaniu jednostek kodowych ASCII jako bajtów, a drugiej przy reprezentowaniu ich jako sekwencji 7-bitowych.

#### ASCII()

ASCII jest zakończoną null skończoną krotką $(u_0, \dots, u_k, u_{k+1})$ taką, że:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is an ASCII code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Kod\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Kod\ Unit}(u_{k+1}) = 0$

Mówi się, że sekwencja jest zakończona znakiem null.

### Jednostka kodowa CP1252

A CP1252 code unit is any $(b_0,\dots,b_7)$ takie, że for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Jednostka kodowa CP1252()

> $\mathrm{CP1252\ Kod\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 jest zakończoną null skończoną krotką $(u_0, \dots, u_k, u_{k+1})$ taką, że:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a CP1252 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Kod\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Kod\ Unit}(u_{k+1}) = 0$

Mówi się, że sekwencja jest zakończona znakiem null.

### Jednostka kodowa UTF-8

A UTF-8 code unit is any $(b_0,\dots,b_7)$ takie, że for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Jednostka kodowa UTF-8()

> $\mathrm{UTF\text{-}8\ Kod\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 jest zakończoną null skończoną krotką $(u_0, \dots, u_k, u_{k+1})$ taką, że:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-8 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Kod\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Kod\ Unit}(u_{k+1}) = 0$

Mówi się, że sekwencja jest zakończona znakiem null.

### Jednostka kodowa UTF-16LE

A UTF-16LE code unit is any $(b_0,\dots,b_{15})$ takie, że for all $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### Jednostka kodowa UTF-16LE()

> $\mathrm{UTF\text{-}16LE\ Kod\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE jest zakończoną null skończoną krotką $(u_0, \dots, u_k, u_{k+1})$ taką, że:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-16LE code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Kod\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Kod\ Unit}(u_{k+1}) = 0$

Mówi się, że sekwencja jest zakończona znakiem null.

## Status operacji

### Kod statusu

A status code is any $(b_0,\dots,b_7)$ takie, że for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

Poziom kodu statusu jest zdefiniowany jako następujący zbiór:

$\displaystyle \quad\mathrm{Status\ Kod\ Poziom} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Kod statusu()

> $\mathrm{Status\ Kod}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Kod statusu Poziom()

Zbiór wartości kodu statusu to zakres $[0, 255]$, który jest podzielony na cztery poziomy:

> Niech $s = \mathrm{Status\ Kod}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Kod\ Poziom}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Kod statusu Definition()

Wszystkie kody statusu mają jawne definicje. Każdy kod statusu, którego nie ma na poniższej liście, jest zarezerwowany do przyszłego użycia, a jego znaczenie jest niezdefiniowane. Poziom kodu statusu jest określany przez $\mathrm{Status\ Kod\ Poziom}(s)$.

Na poniższej liście wejście $s$ jest przedstawione jako wartość szesnastkowa dla czytelności. Każdy zdefiniowany kod statusu określa odpowiadający mu poziom, kategorię, podkategorię, opis oraz szczegół, jeśli ma zastosowanie.

Lista może być rozszerzana w miarę definiowania nowych kodów statusu. Każdy nowo zdefiniowany kod statusu nie może kolidować z istniejącymi kodami i musi mieć jasno udokumentowane znaczenie.

Do przekazywania informacji, których nie reprezentuje zdefiniowany kod statusu, należy używać kodu kontekstu, kodu operacji lub kodu szczegółu.

##### Sukces

| Kod | Poziom | Kategoria | Opis | Szczegół |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | Operacja zakończyła się pomyślnie. | |
| `0x01` | SUCCESS | NOOP | Operacja zakończyła się pomyślnie bez wykonania żadnej akcji. | |

##### Ostrzeżenie

| Kod | Poziom | Kategoria | Opis | Szczegół |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | Operacja została ukończona, ale wynik może być nieoczekiwany lub niepożądany. | |
| `0x41` | WARNING | PARTIAL | Operacja została ukończona tylko częściowo. Dane wyjściowe mogą być niekompletne. | |
| `0x42` | WARNING | DEPRECATED | Operacja została ukończona, ale użyła przestarzałej funkcji lub zachowania. Operacja może przestać działać w przyszłości. | |

##### Błąd

| Kod | Poziom | Kategoria | Opis | Szczegół |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | Operacja nie powiodła się z powodu błędu możliwego do odzyskania. | |
| `0x81` | ERROR | INVALID_ARGUMENT | Operacja nie powiodła się. Argument był nieprawidłowy lub poza zakresem. | Indeks nieprawidłowego argumentu, liczony od 0 od lewej do prawej w sygnaturze funkcji. |
| `0x82` | ERROR | INVALID_STATE | Operacja nie powiodła się. System znajduje się w niespójnym, uszkodzonym lub w inny sposób nieprawidłowym stanie. | |
| `0x83` | ERROR | MALFORMED_INPUT | Operacja nie powiodła się. Wymagane wejście było źle sformułowane lub zawierało nieprawidłowe dane. | |
| `0x84` | ERROR | ACCESS_DENIED | Operacja nie powiodła się, ponieważ wymagany zasób odmówił dostępu. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | Operacja nie powiodła się, ponieważ żądana funkcja lub zachowanie nie jest jeszcze zaimplementowane. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | Operacja nie powiodła się, ponieważ system docelowy lub konfiguracja nie obsługuje żądanej funkcji. | |
| `0x87` | ERROR | TIMEOUT | Operacja nie powiodła się, ponieważ przed jej ukończeniem wystąpiło wymagane przekroczenie limitu czasu. | |
| `0x88` | ERROR | NOT_FOUND | Operacja nie powiodła się, ponieważ wymagany zasób nie istnieje. | |
| `0x89` | ERROR | INTERRUPTED | Operacja nie powiodła się, ponieważ przerwało ją zdarzenie zewnętrzne. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | Operacja nie powiodła się, ponieważ wymagana zależność zawiodła. | Wartość `STATUS_CODE` zależności. Wywołujący są zachęcani, choć nie jest to wymagane, do identyfikowania wadliwej zależności przez pole `OP_CODE`. |
| `0x90` | ERROR | BUFFER_OVERFLOW | Operacja nie powiodła się. Bufor był zbyt mały, aby pomieścić wymagane dane. | |
| `0x91` | ERROR | ALLOCATION_FAILED | Operacja nie powiodła się. Żądanie alokacji pamięci zakończyło się niepowodzeniem. | |
| `0xA0` | ERROR | IO_ERROR | Operacja nie powiodła się. Podczas operacji wystąpił błąd wejścia/wyjścia. | |

##### Krytyczny

| Kod | Poziom | Kategoria | Opis | Szczegół |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | Operacja nie powiodła się z powodu błędu nieodwracalnego. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | Operacja nie powiodła się, ponieważ system naruszył podstawowy niezmiennik, co wskazuje na krytyczny błąd logiczny lub uszkodzenie danych. | |

### Kod kontekstu

A context code is any $(b_0,\dots,b_7)$ takie, że for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Kod kontekstu()

Wartość kodu kontekstu reprezentuje dodatkowe informacje kontekstowe o ukończonej operacji zgodnie z definicją powiązanej operacji; musi wynosić zero, gdy poziom kodu statusu to $\mathrm{Success}$, a w przeciwnym razie jest zależna od implementacji.

> $\mathrm{Context\ Kod}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Kod operacji

An operation code is any $(b_0,\dots,b_7)$ takie, że for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Kod operacji()

Wartość kodu operacji reprezentuje operację powiązaną z wynikiem. Jej znaczenie jest definiowane przez odpowiednią operację i jej dokumentację. Niezdefiniowane wartości są uznawane za nieznane.

> $\mathrm{Operation\ Kod}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Kod szczegółu

A detail code is any $(b_0,\dots,b_7)$ takie, że for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Kod szczegółu()

Wartość kodu szczegółu reprezentuje dodatkowe informacje o ukończonej operacji; jej znaczenie jest definiowane przez powiązany kod statusu, kontekstu lub operacji (w tej kolejności), a w przeciwnym razie jest nieznane.

> $\mathrm{Szczegół\ Kod}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Wynik

> [!TIP]
>
> Wartość wyniku może być reprezentowana jako 32-bitowa liczba całkowita. W kolejności bajtów big-endian wartość ma postać `0xSSCCOODD`, gdzie `SS`, `CC`, `OO` i `DD` odpowiadają kolejno kodowi statusu, kodowi kontekstu, kodowi operacji i kodowi szczegółu. W kolejności little-endian ta sama wartość ma postać `0xDDOOCCSS`. Można użyć dowolnej kolejności bajtów, pod warunkiem że jest stosowana konsekwentnie i udokumentowana.

A result is any $(b_0,\dots,b_{31})$ takie, że for all $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

Wynik jest podzielony na cztery uporządkowane bajty:

- $s = \mathrm{Status\ Kod}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Kod}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Kod}(b_{16},\dots,b_{23})$
- $d = \mathrm{Szczegół\ Kod}(b_{24},\dots,b_{31})$

gdzie $s$, $c$, $o$ i $d$ są składnikami wyniku.

#### Wynik()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
