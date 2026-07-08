<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden beoordeeld. -->
<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

# Beoordelingsdetails

## JavaScript

### Overzicht

De programmeertaal JavaScript is op 7 juli 2026 beoordeeld aan de hand van de FDEFSPEC (Rev. 1)- en FRELSPEC (Rev. 1)-specificaties.

#### Beoordelingsverklaring

While JavaScript can represent some required concepts through objects, functions, arrays, and built-in language behavior, these mechanisms are not sufficient to satisfy the applicable CatalystUI specifications at the language level.

This review evaluates JavaScript itself, not the surrounding JavaScript ecosystem. Browser APIs, Node.js APIs, Deno APIs, Bun APIs, Web APIs, TypeScript, WebAssembly, external libraries, and custom validation are not treated as language-level support.

Because JavaScript lacks many required fixed-width scalar numeric types, does not provide required text encodings as language features, and does not define several required system, memory, threading, and composite constructs, we do not believe JavaScript provides a stable enough foundation for CatalystUI-compliant implementation without significant additional infrastructure.

Daarom heeft JavaScript geen CatalystUI Verified-status voor programmeertalen gekregen.

#### Beoordelingsaannames

This review applies a strict language-level standard. If a provision is not explicitly supported by JavaScript itself, it is marked as not verified.

Host-provided APIs, implementation-specific behavior, external libraries, transpilers, type systems, and custom runtime validation are excluded from verification.

### Waarschuwingen

* JavaScript can represent many numeric values through `Number`, but `Number` is a 64-bit floating point numeric type.
* JavaScript provides `BigInt`, but `BigInt` is arbitrary-width.
* Typed arrays provide binary storage views, not scalar language types.
* JavaScript-strings gebruiken UTF-16-code-units, geen expliciete tekstcoderingswaarden.
* `const` beschermt bindings, niet objectwaarden.

### Mislukkingen

* JavaScript biedt de meeste vereiste fixed-width scalar numeric types niet.
* JavaScript biedt geen dedicated scalar 32-bit floating point type.
* JavaScript biedt ASCII, CP1252, UTF-8 of UTF-16LE niet als tekstcoderingen op taalniveau.
* JavaScript biedt geen file- of stream-constructies op taalniveau.
* JavaScript biedt geen address- of pointer-constructies op taalniveau.
* JavaScript biedt geen process-, thread- of dispatcher-constructies op taalniveau.
* JavaScript-properties bieden geen expliciet keyed member dat wordt ondersteund door een vereiste Get/Set accessor map.
* JavaScript biedt geen structures of interfaces.

### FDEFSPEC-verificatie

#### Numerieke waarden

| Bepaling | Geverifieerd | Opmerkingen                          |
| --------- | -------- | ------------------------------ |
| Bit       | ❌        | Geen 1-bit numeric type.         |
| Nibble    | ❌        | Geen 4-bit numeric type.         |
| Byte      | ❌        | Geen scalar 8-bit integer type.  |
| Short     | ❌        | Geen scalar 16-bit integer type. |
| Int       | ❌        | Geen scalar 32-bit integer type. |
| Long      | ❌        | Geen scalar 64-bit integer type. |
| Float     | ❌        | Geen scalar 32-bit float type.   |
| Double    | ✅        | Ondersteund via `Number`.    |
| Boolean   | ✅        | Supported through `boolean`.   |

#### Tekstcodering

| Bepaling | Geverifieerd | Opmerkingen                        |
| --------- | -------- | ---------------------------- |
| Codepoint | ❌        | Geen dedicated codepoint type. |
| ASCII     | ❌        | Niet op taalniveau.          |
| CP1252    | ❌        | Niet op taalniveau.          |
| UTF-8     | ❌        | Niet op taalniveau.          |
| UTF-16LE  | ❌        | Niet op taalniveau.          |

#### Bewerkingsstatus

| Bepaling | Geverifieerd | Opmerkingen                           |
| --------- | -------- | ------------------------------- |
| Status    | ⚠️       | Weer te geven, niet afdwingbaar. |
| Context   | ⚠️       | Weer te geven, niet afdwingbaar. |
| Operation | ⚠️       | Weer te geven, niet afdwingbaar. |
| Detail    | ⚠️       | Weer te geven, niet afdwingbaar. |
| Result    | ⚠️       | Vereist runtime validation.    |

### FRELSPEC-verificatie

#### Collecties

| Bepaling | Geverifieerd | Opmerkingen                    |
| --------- | -------- | ------------------------ |
| Set       | ✅        | Ondersteund via `Set`. |
| Map       | ✅        | Ondersteund via `Map`. |
| Array     | ✅        | Arrays worden ondersteund.    |
| File      | ❌        | Niet op taalniveau.      |
| Stream    | ❌        | Niet op taalniveau.      |

#### Geheugen

| Bepaling | Geverifieerd | Opmerkingen                           |
| --------- | -------- | ------------------------------- |
| Address   | ❌        | Geen address-ondersteuning.             |
| Pointer   | ❌        | Geen pointer-ondersteuning.             |
| Variable  | ✅        | Variables worden ondersteund.        |
| Constant  | ⚠️       | `const` beschermt alleen bindings. |

#### Bewerkingen

| Provision   | Verified | Notes                            |
| ----------- | -------- | -------------------------------- |
| Instruction | ❌        | Geen gedefinieerd instruction type.     |
| Procedure   | ❌        | Functions retourneren altijd een waarde. |
| Function    | ✅        | Functions are supported.         |

#### Threading

| Provision  | Verified | Notes                       |
| ---------- | -------- | --------------------------- |
| Process    | ❌        | Niet op taalniveau.         |
| Thread     | ⚠️        | Weergegeven via agents. |
| Dispatcher | ❌        | Vereist host scheduling.   |


#### Composieten

| Bepaling | Geverifieerd | Opmerkingen                                 |
| --------- | -------- | ------------------------------------- |
| Member    | ✅        | Object members worden ondersteund.         |
| Object    | ✅        | Objects worden ondersteund.                |
| Field     | ✅        | Data properties kunnen fields vertegenwoordigen. |
| Method    | ✅        | Methods worden ondersteund.                |
| Property  | ❌        | Geen expliciete accessor map.             |
| Structure | ❌        | Geen structure-ondersteuning.                 |
| Class     | ✅        | Class-syntaxis wordt ondersteund.            |
| Interface | ❌        | Geen interface-ondersteuning.                 |
