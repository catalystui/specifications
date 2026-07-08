<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden beoordeeld. -->
<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

# Verificatiedetails

## C#

### Overzicht

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


De programmeertaal C# is op 7 juli 2026 geverifieerd aan de hand van de FDEFSPEC (Rev. 1)- en FRELSPEC (Rev. 1)-specificaties.

#### Verklaring te goeder trouw

Wij geloven te goeder trouw dat de programmeertaal C# de concepten en bepalingen die in de volgende specificaties zijn gedefinieerd redelijkerwijs kan vertegenwoordigen, en dat zij kan worden gebruikt om systemen te implementeren die aan deze specificaties voldoen.

#### Beoordelingsaannames

Deze beoordeling gaat uit van moderne C#- en .NET-ondersteuning waar versieafhankelijke functies worden genoemd.

### Waarschuwingen

* CP1252-ondersteuning is beschikbaar via de officiële .NET code pages provider, maar kan afhankelijk van de target runtime providerregistratie of een aanvullend package vereisen.
* Unsafe pointer-gedrag kan expliciete unsafe-autorisatie vereisen.

### Mislukkingen

* Tijdens deze verificatie zijn geen bekende FDEFSPEC- of FRELSPEC-mislukkingen gevonden.

### FDEFSPEC-verificatie

#### Numerieke waarden

| Bepaling | Geverifieerd | Opmerkingen                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | Geen 1-bit numeric; widen.                |
| Nibble    | ⚠️       | Geen 4-bit numeric; widen.                |
| Byte      | ✅        | Supported through `byte` and `sbyte`.   |
| Short     | ✅        | Supported through `short` and `ushort`. |
| Int       | ✅        | Supported through `int` and `uint`.     |
| Long      | ✅        | Supported through `long` and `ulong`.   |
| Float     | ✅        | Ondersteund via `float`.              |
| Double    | ✅        | Ondersteund via `double`.             |
| Boolean   | ✅        | Ondersteund via `bool`.               |

#### Tekstcodering

| Bepaling | Geverifieerd | Opmerkingen                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | Ondersteund via numerics en `Rune`. |
| ASCII     | ✅        | Ondersteund via `Encoding.ASCII`.    |
| CP1252    | ⚠️       | Vereist code pages provider.          |
| UTF-8     | ✅        | Ondersteund via `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | Ondersteund via `Encoding.Unicode`.  |

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

| Bepaling | Geverifieerd | Opmerkingen                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Ondersteund via `HashSet<T>`.              |
| Map       | ✅        | Ondersteund via `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Native arrays worden ondersteund.                 |
| File      | ✅        | Ondersteund via file-API's.                 |
| Stream    | ✅        | Supported through `Stream`.                  |

#### Geheugen

| Bepaling | Geverifieerd | Opmerkingen                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Supported through references and pointers. |
| Pointer   | ✅        | Supported through unsafe pointers.         |
| Variable  | ✅        | Variables worden ondersteund.                   |
| Constant  | ✅        | Ondersteund via `const` en `readonly`.  |

#### Bewerkingen

| Provision   | Verified | Notes                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Weergegeven via IL en operations. |
| Procedure   | ✅        | Ondersteund via `void` methods.      |
| Function    | ✅        | Ondersteund via returning methods.   |

#### Threading

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Ondersteund via application- en `Process`-API's. |
| Thread     | ✅        | Ondersteund via `Thread`.                       |
| Dispatcher | ✅        | Ondersteund via tasks en schedulers.           |

#### Composieten

| Bepaling | Geverifieerd | Opmerkingen                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Type members worden ondersteund.        |
| Object    | ✅        | Objects worden ondersteund.             |
| Field     | ✅        | Fields worden ondersteund.              |
| Method    | ✅        | Methods worden ondersteund.             |
| Property  | ✅        | Properties worden native ondersteund. |
| Structure | ✅        | Structures worden native ondersteund. |
| Class     | ✅        | Classes worden ondersteund.             |
| Interface | ✅        | Interfaces worden ondersteund.          |
