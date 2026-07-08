<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden beoordeeld. -->
<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

# FDEFSPEC

<br/>

> **Fundamentele Definitie-specificatie**<br/>
> Revisie 1<br/>
> 23 maart 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/>
> <br/>
> De definities en concepten die hierin worden gepresenteerd beschrijven fundamentele wiskundige constructies en mogen vrij opnieuw worden uitgedrukt.

## Inleiding

De **Foundational Definitions Specification (FDEFSPEC)** legt de kernconcepten en terminologie vast die ten grondslag liggen aan het CatalystUI-ecosysteem. Het doel is een gezamenlijk begrip van deze concepten te bieden in documentatie, specificaties, implementaties en verificatiebeoordelingen, zodat consistentie, duidelijkheid en afstemming worden gewaarborgd.

Door sleuteltermen en relaties in een precieze en stabiele vorm te definiëren, biedt FDEFSPEC een gemeenschappelijk referentiepunt voor specificaties op hoger niveau. Hierdoor kunnen ontwikkelaars, beoordelaars en implementatoren vanuit hetzelfde fundament redeneren wanneer zij bepalen of een taal, service, framework of systeem als within spec kan worden beschouwd.

> [!IMPORTANT]
>
> We drukken definities uit met een afgeleide vorm van [verzamelingenleer](https://en.wikipedia.org/wiki/Set_theory)-notatie. Deze aanpak biedt precieze, ondubbelzinnige definities terwijl duidelijkheid en beknoptheid behouden blijven. We structureren deze definities om eenvoudige verwijzing, heldere interpretatie en een consistente conceptuele hiërarchie te ondersteunen.

## Inhoudsopgave

- [FDEFSPEC](#fdefspec)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Numerics](#numerics)
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
  - [Text Encoding](#text-encoding)
    - [Text Encoding](#text-encoding-1)
      - [Text Encoding()](#text-encoding-2)
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
  - [Operation Status](#operation-status)
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

## Numerieke waarden

### Bit

Een bit is elke $b \in \{0,1\}$.

### Nibble

Een nibble is elke $(b_0,\dots,b_3)$ waarvoor voor alle $i \in \{0,\dots,3\}$ geldt dat $b_i \in \mathrm{Bit}$.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

Een byte is elke $(b_0,\dots,b_7)$ waarvoor voor alle $i \in \{0,\dots,7\}$ geldt dat $b_i \in \mathrm{Bit}$.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

Een short is elke $(b_0,\dots,b_{15})$ waarvoor voor alle $i \in \{0,\dots,15\}$ geldt dat $b_i \in \mathrm{Bit}$.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

Een integer is elke $(b_0,\dots,b_{31})$ waarvoor voor alle $i \in \{0,\dots,31\}$ geldt dat $b_i \in \mathrm{Bit}$.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

Een long is elke $(b_0,\dots,b_{63})$ waarvoor voor alle $i \in \{0,\dots,63\}$ geldt dat $b_i \in \mathrm{Bit}$.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

Een single is elke $(b_0,\dots,b_{31})$ waarvoor voor alle $i \in \{0,\dots,31\}$ geldt dat $b_i \in \mathrm{Bit}$.

#### Single()

De volgende definitie voldoet aan de IEEE 754-standaard voor single-precision floating-point-representatie. Ze definieert hoe een 32-bit binaire reeks wordt geïnterpreteerd als een floating-point getal, inclusief speciale gevallen voor nul, oneindigheid en NaN (Not a Number).

> Laat $s = b_0$
>
> Laat $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Laat $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

Een double is elke $(b_0,\dots,b_{63})$ waarvoor voor alle $i \in \{0,\dots,63\}$ geldt dat $b_i \in \mathrm{Bit}$.

#### Double()

De volgende definitie voldoet aan de IEEE 754-standaard voor double-precision floating-point-representatie. Ze definieert hoe een 64-bit binaire reeks wordt geïnterpreteerd als een floating-point getal, inclusief speciale gevallen voor nul, oneindigheid en NaN (Not a Number).

> Laat $s = b_0$
>
> Laat $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Laat $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

Een boolean is elke $b \in \{0,1\}$.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## Tekstcodering

### Tekstcodering

Een tekstcodering wordt gedefinieerd als de volgende verzameling:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Tekstcodering()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Een Unicode-codepoint is elke $e \in \mathbb{Z}$ waarvoor $0 \leq e \leq 0x10FFFF$ geldt.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

An ASCII code unit is any $(b_0,\dots,b_6)$ such that for all $i \in \{0,\dots,6\}$, $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

Het is gebruikelijk om een ASCII-code-unit als byte weer te geven door een leidende nulbit toe te voegen, om redenen van prestaties en compatibiliteit. In zulke gevallen wordt de ASCII-code-unit als volgt weergegeven:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Anders:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

In het geval van deze stelling zijn beide definities aanvaardbare representaties van een ASCII-code-unit. Voor consistentie gebruiken we de eerste definitie wanneer ASCII-code-units als bytes worden weergegeven, en de tweede definitie wanneer ze als 7-bit reeksen worden weergegeven.

#### ASCII()

ASCII is een null-terminated eindige tuple $(u_0, \dots, u_k, u_{k+1})$ waarvoor geldt:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is een ASCII-code-unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

De reeks wordt null-terminated genoemd.

### CP1252 Code Unit

A CP1252 code unit is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 is een null-terminated eindige tuple $(u_0, \dots, u_k, u_{k+1})$ waarvoor geldt:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is een CP1252-code-unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

De reeks wordt null-terminated genoemd.

### UTF-8 Code Unit

A UTF-8 code unit is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 is een null-terminated eindige tuple $(u_0, \dots, u_k, u_{k+1})$ waarvoor geldt:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is een UTF-8-code-unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

De reeks wordt null-terminated genoemd.

### UTF-16LE Code Unit

A UTF-16LE code unit is any $(b_0,\dots,b_{15})$ such that for all $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE is een null-terminated eindige tuple $(u_0, \dots, u_k, u_{k+1})$ waarvoor geldt:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is een UTF-16LE-code-unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

De reeks wordt null-terminated genoemd.

## Bewerkingsstatus

### Status Code

A status code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

Een statuscodeniveau wordt gedefinieerd als de volgende verzameling:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Status Code()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Status Code Level()

De verzameling statuscodewaarden is het bereik $[0, 255]$, dat in vier niveaus is verdeeld:

> Laat $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Status Code Definition()

Alle statuscodes hebben expliciete definities. Elke statuscode die niet in de volgende lijst staat, is gereserveerd voor toekomstig gebruik en de betekenis ervan is ongedefinieerd. Het niveau van een statuscode wordt bepaald door $\mathrm{Status\ Code\ Level}(s)$.

In de volgende lijst wordt de invoer $s$ voor de leesbaarheid weergegeven als een hexadecimale waarde. Elke gedefinieerde statuscode vermeldt het bijbehorende niveau, de categorie, subcategorie, beschrijving en details waar van toepassing.

Deze lijst kan worden uitgebreid wanneer nieuwe statuscodes worden gedefinieerd. Een nieuw gedefinieerde statuscode mag niet conflicteren met bestaande codes en moet een duidelijk gedocumenteerde betekenis hebben.

Gebruik de contextcode, operation code of detailcode om informatie over te brengen die niet door een gedefinieerde statuscode wordt weergegeven.

##### Success

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | The operation completed successfully. | |
| `0x01` | SUCCESS | NOOP | The operation completed successfully without performing any action. | |

##### Warning

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | The operation completed, but the result may be unexpected or undesirable. | |
| `0x41` | WARNING | PARTIAL | The operation completed, but only partially. The output may be incomplete. | |
| `0x42` | WARNING | DEPRECATED | The operation completed, but it used a deprecated feature or behavior. The operation may no longer work in the future. | |

##### Error

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | The operation failed due to a recoverable error. | |
| `0x81` | ERROR | INVALID_ARGUMENT | The operation failed. An argument was invalid or out of range. | The index of the invalid argument, starting at 0 from left to right in the function's signature. |
| `0x82` | ERROR | INVALID_STATE | The operation failed. The system is in an inconsistent, corrupted, or otherwise invalid state. | |
| `0x83` | ERROR | MALFORMED_INPUT | The operation failed. A required input was malformed or contained invalid data. | |
| `0x84` | ERROR | ACCESS_DENIED | The operation failed because a required resource denied access. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | The operation failed because the requested feature or behavior is not yet implemented. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | The operation failed because the target system or configuration does not support the requested feature. | |
| `0x87` | ERROR | TIMEOUT | The operation failed because a required timeout occurred before completion. | |
| `0x88` | ERROR | NOT_FOUND | The operation failed because a required resource does not exist. | |
| `0x89` | ERROR | INTERRUPTED | The operation failed because an external event interrupted it. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | The operation failed because a required dependency failed. | The dependency's `STATUS_CODE` value. Callers are encouraged (but not required) to identify the failing dependency via the `OP_CODE` field. |
| `0x90` | ERROR | BUFFER_OVERFLOW | The operation failed. A buffer was too small to hold the required data. | |
| `0x91` | ERROR | ALLOCATION_FAILED | The operation failed. A memory allocation request was unsuccessful. | |
| `0xA0` | ERROR | IO_ERROR | The operation failed. An I/O error occurred during the operation. | |

##### Fatal

| Code | Level | Category | Description | Detail |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | The operation failed due to an unrecoverable error. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | The operation failed because the system violated a fundamental invariant, indicating a critical logic error or data corruption. | |

### Context Code

A context code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Context Code()

Een contextcodewaarde vertegenwoordigt aanvullende contextuele informatie over een voltooide bewerking, zoals gedefinieerd door de bijbehorende bewerking; zij moet nul zijn wanneer het statuscodeniveau $\mathrm{Success}$ is en is anders implementatiegedefinieerd.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Operation Code

An operation code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Operation Code()

Een operation-codewaarde vertegenwoordigt de bewerking die aan een resultaat is gekoppeld. De betekenis ervan wordt gedefinieerd door de overeenkomstige bewerking en de documentatie daarvan. Ongedefinieerde waarden worden als onbekend beschouwd.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Detail Code

A detail code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Detail Code()

Een detailcodewaarde vertegenwoordigt aanvullende informatie over een voltooide bewerking; de betekenis ervan wordt gedefinieerd door de bijbehorende status-, context- of operation-code (in die volgorde), en is anders onbekend.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Result

> [!TIP]
>
> Een result-waarde kan worden weergegeven als een 32-bit integer. In big-endian bytevolgorde verschijnt de waarde als `0xSSCCOODD`, waarbij `SS`, `CC`, `OO` en `DD` respectievelijk overeenkomen met de statuscode, contextcode, operation code en detailcode. In little-endian bytevolgorde verschijnt dezelfde waarde als `0xDDOOCCSS`. Elke bytevolgorde mag worden gebruikt, mits deze consequent wordt toegepast en gedocumenteerd.

A result is any $(b_0,\dots,b_{31})$ such that for all $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

Een result wordt opgedeeld in vier geordende bytes:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

waarbij $s$, $c$, $o$ en $d$ de componenten van het result zijn.

#### Result()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
