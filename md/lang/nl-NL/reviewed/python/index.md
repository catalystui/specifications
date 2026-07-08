<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden beoordeeld. -->
<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

# Beoordelingsdetails

## Python

### Overzicht

De programmeertaal Python is op 7 juli 2026 beoordeeld aan de hand van de FDEFSPEC (Rev. 1)- en FRELSPEC (Rev. 1)-specificaties.

#### Beoordelingsverklaring

Hoewel Python veel vereiste concepten kan vertegenwoordigen via ingebouwde typen, objecten, functions, classes, standaardbibliotheekmodules en custom validation, zijn deze mechanismen niet voldoende om op taalniveau aan de toepasselijke CatalystUI-specificaties te voldoen.

Python biedt sterke ondersteuning voor tekstcodering, files, streams, objecten, functions, classes, properties, processen, threads en dispatched execution via ingebouwd gedrag en de standaardbibliotheek. Python biedt echter niet de vereiste fixed-width scalar numeric types, definieert geen echte constants en vertrouwt voor verschillende constructies op dynamisch runtimegedrag dat andere geverifieerde talen directer kunnen uitdrukken.

Daarom geloven wij niet dat Python zonder aanzienlijke aanvullende infrastructuur een stabiel genoeg fundament biedt voor CatalystUI-conforme implementatie.

Daarom heeft Python geen CatalystUI Verified-status voor programmeertalen gekregen.

#### Beoordelingsaannames

Deze beoordeling evalueert Python zelf en de meegeleverde standaardbibliotheek.

Third-party packages, implementatiespecifieke extensies, optionele native modules, externe typecheckers, transpilers en custom runtime frameworks worden niet behandeld als ondersteuning op taalniveau.

### Waarschuwingen

* Python biedt unlimited-precision integers, geen fixed-width integer primitives.
* Python `float` is meestal double precision, maar geen afzonderlijke fixed-width familie.
* Sommige low-level memory-gedragingen kunnen `ctypes` of implementatiespecifiek gedrag vereisen.
* Python type hints worden niet bij runtime afgedwongen.
* Python ondersteunt properties, maar setter-gedrag kan worden weggelaten.
* Python kan verschillende structures modelleren via standaardbibliotheekfuncties, maar niet als native structure type.

### Mislukkingen

* Python biedt de meeste vereiste fixed-width scalar numeric types niet.
* Python biedt geen dedicated scalar 32-bit floating point type.
* Python biedt geen echte constants op taalniveau.
* Python definieert procedures niet los van functions.
* Python biedt geen native pointer-ondersteuning.
* Python biedt geen native interface-ondersteuning.

### FDEFSPEC-verificatie

#### Numerieke waarden

| Bepaling | Geverifieerd | Opmerkingen                                |
| --------- | -------- | ------------------------------------ |
| Bit       | ❌        | Geen 1-bit numeric type.               |
| Nibble    | ❌        | Geen 4-bit numeric type.               |
| Byte      | ❌        | Geen scalar 8-bit integer type.        |
| Short     | ❌        | Geen scalar 16-bit integer type.       |
| Int       | ❌        | Geen scalar 32-bit integer type.       |
| Long      | ❌        | Geen scalar 64-bit integer type.       |
| Float     | ❌        | Geen scalar 32-bit float type.         |
| Double    | ⚠️       | `float` is meestal double precision. |
| Boolean   | ✅        | Ondersteund via `bool`.            |

#### Tekstcodering

| Bepaling | Geverifieerd | Opmerkingen                            |
| --------- | -------- | -------------------------------- |
| Codepoint | ✅        | Strings gebruiken Unicode code points. |
| ASCII     | ✅        | Ondersteunde codec.                 |
| CP1252    | ✅        | Ondersteunde codec.                 |
| UTF-8     | ✅        | Ondersteunde codec.                 |
| UTF-16LE  | ✅        | Ondersteunde codec.                 |

#### Bewerkingsstatus

| Bepaling | Geverifieerd | Opmerkingen                       |
| --------- | -------- | --------------------------- |
| Status    | ⚠️       | Vereist custom validation. |
| Context   | ⚠️       | Vereist custom validation. |
| Operation | ⚠️       | Vereist custom validation. |
| Detail    | ⚠️       | Vereist custom validation. |
| Result    | ⚠️       | Vereist custom validation. |

### FRELSPEC-verificatie

#### Collecties

| Bepaling | Geverifieerd | Opmerkingen                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Ondersteund via `set`.       |
| Map       | ✅        | Ondersteund via `dict`.      |
| Array     | ✅        | Ondersteund via sequences.   |
| File      | ✅        | Ondersteund via file-API's.   |
| Stream    | ✅        | Ondersteund via stream-API's. |

#### Geheugen

| Bepaling | Geverifieerd | Opmerkingen                        |
| --------- | -------- | ---------------------------- |
| Address   | ⚠️       | Alleen object identity.        |
| Pointer   | ❌        | Geen native pointer-ondersteuning.   |
| Variable  | ✅        | Name bindings worden ondersteund. |
| Constant  | ❌        | Geen echte constants.           |

#### Bewerkingen

| Provision   | Verified | Notes                             |
| ----------- | -------- | --------------------------------- |
| Instruction | ⚠️       | Bytecode is implementatieniveau. |
| Procedure   | ❌        | Functions retourneren `None`.          |
| Function    | ✅        | Functions are supported.          |

#### Threading

| Provision  | Verified | Notes                            |
| ---------- | -------- | -------------------------------- |
| Process    | ✅        | Ondersteund via process-API's.  |
| Thread     | ✅        | Supported through `threading`.   |
| Dispatcher | ✅        | Ondersteund via executor-API's. |

#### Composieten

| Bepaling | Geverifieerd | Opmerkingen                            |
| --------- | -------- | -------------------------------- |
| Member    | ✅        | Object members worden ondersteund.    |
| Object    | ✅        | Objects worden ondersteund.           |
| Field     | ✅        | Attributes kunnen fields vertegenwoordigen. |
| Method    | ✅        | Methods worden ondersteund.           |
| Property  | ⚠️       | Getter/setter-ondersteuning bestaat.    |
| Structure | ⚠️       | Alleen standaardbibliotheekmodellen.    |
| Class     | ✅        | Classes worden ondersteund.           |
| Interface | ❌        | Geen native interface-ondersteuning.     |
