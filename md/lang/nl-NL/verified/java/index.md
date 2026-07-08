<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden beoordeeld. -->
<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

# Verificatiedetails

## Java

### Overzicht

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


De programmeertaal Java is op 7 juli 2026 geverifieerd aan de hand van de FDEFSPEC (Rev. 1)- en FRELSPEC (Rev. 1)-specificaties.

#### Verklaring te goeder trouw

Wij geloven te goeder trouw dat de programmeertaal Java een groot deel van de concepten en bepalingen die in de volgende specificaties zijn gedefinieerd redelijkerwijs kan vertegenwoordigen, en dat zij kan worden gebruikt om systemen te implementeren die aan deze specificaties voldoen.

#### Beoordelingsaannames

Deze beoordeling gaat uit van moderne Java-taalondersteuning waar versieafhankelijke functies worden genoemd. Functies zoals lokale variabele-inferentie, records en foreign memory access kunnen latere Java-versies vereisen.

### Waarschuwingen

* Java heeft geen native ondersteuning voor unsigned numeric types, waardoor widening of alternatieve representaties voor bepaalde bepalingen nodig kunnen zijn.
* Direct memory address- en pointer-style gedrag kan Java 22+ Foreign Function and Memory API-ondersteuning vereisen.
* Java heeft geen native property-syntaxis en vereist in plaats daarvan getter- en setter-methods.

### Mislukkingen

* Java biedt CP1252 niet als gegarandeerde standaardcharset, waardoor implementatiespecifieke ondersteuning, aanvullende bibliotheken of custom handling nodig zijn voor volledige naleving.
* Java-properties bieden geen expliciet keyed member dat wordt ondersteund door een vereiste Get/Set accessor map.

### FDEFSPEC-verificatie

#### Numerieke waarden

| Bepaling | Geverifieerd | Opmerkingen                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | Geen 1-bit numeric; widen.                         |
| Nibble    | ⚠️       | Geen 4-bit numeric; widen.                         |
| Byte      | ⚠️       | Alleen signed 8-bit; widen voor unsigned.           |
| Short     | ⚠️       | Alleen signed 16-bit; widen voor unsigned.          |
| Int       | ⚠️       | Signed 32-bit; unsigned helpers vereisen Java 8+. |
| Long      | ⚠️       | Signed 64-bit; unsigned helpers vereisen Java 8+. |
| Float     | ✅        | 32-bit floating point is supported.              |
| Double    | ✅        | 64-bit floating point is supported.              |
| Boolean   | ✅        | Boolean type wordt ondersteund.                       |

#### Tekstcodering

| Bepaling | Geverifieerd | Opmerkingen                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Supported through `int` and `Character`. |
| ASCII     | ✅        | Gegarandeerde standaardcharset.             |
| CP1252    | ❌        | Niet gegarandeerd door `StandardCharsets`.    |
| UTF-8     | ✅        | Gegarandeerde standaardcharset.             |
| UTF-16LE  | ✅        | Gegarandeerde standaardcharset.             |

#### Bewerkingsstatus

| Bepaling | Geverifieerd | Opmerkingen                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Kan worden weergegeven door een custom type.        |
| Context   | ✅        | Kan worden weergegeven door een custom value.       |
| Operation | ✅        | Kan worden weergegeven door een custom value.       |
| Detail    | ✅        | Kan worden weergegeven door een custom value.       |
| Result    | ✅        | Kan worden weergegeven door een custom return type. |

### FRELSPEC-verificatie

#### Collecties

| Bepaling | Geverifieerd | Opmerkingen                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Ondersteund via `Set`.       |
| Map       | ✅        | Ondersteund via `Map`.       |
| Array     | ✅        | Native arrays worden ondersteund.   |
| File      | ✅        | Ondersteund via file-API's.   |
| Stream    | ✅        | Ondersteund via stream-API's. |

#### Geheugen

| Bepaling | Geverifieerd | Opmerkingen                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses vereisen Java 22+ FFM.                         |
| Pointer   | ⚠️       | Pointer-like access vereist Java 22+ FFM.                     |
| Variable  | ✅        | Declaraties en `var` worden ondersteund; `var` vereist Java 10+. |
| Constant  | ✅        | Ondersteund via `final`.                                     |

#### Bewerkingen

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Weergegeven via bytecode en operations. |
| Procedure   | ✅        | Ondersteund via `void` methods.            |
| Function    | ✅        | Ondersteund via returning methods.         |

#### Threading

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Ondersteund via application- en `Process`-API's. |
| Thread     | ✅        | Ondersteund via `Thread`.                       |
| Dispatcher | ✅        | Ondersteund via `Executor`-API's.                |

#### Composieten

| Bepaling | Geverifieerd | Opmerkingen                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Class members worden ondersteund.           |
| Object    | ✅        | Objects worden ondersteund.                 |
| Field     | ✅        | Fields worden ondersteund.                  |
| Method    | ✅        | Methods worden ondersteund.                 |
| Property  | ❌        | Geen expliciete accessor map.              |
| Structure | ✅        | Ondersteund via records; Java 16+.   |
| Class     | ✅        | Classes worden ondersteund.                 |
| Interface | ✅        | Interfaces worden ondersteund.              |
