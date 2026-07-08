<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden beoordeeld. -->
<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

# Verificatiedetails

## C

### Overzicht

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


De programmeertaal C is op 7 juli 2026 geverifieerd aan de hand van de FDEFSPEC (Rev. 1)- en FRELSPEC (Rev. 1)-specificaties.

#### Verklaring te goeder trouw

Wij geloven te goeder trouw dat de programmeertaal C de concepten en bepalingen die in de volgende specificaties zijn gedefinieerd redelijkerwijs kan vertegenwoordigen, en dat zij kan worden gebruikt om systemen te implementeren die aan deze specificaties voldoen.

#### Beoordelingsverklaring

C biedt sterke low-level ondersteuning voor fundamentele datarepresentatie, geheugentoegang, files, streams, procedures, functions, structures en directe systeemgerichte implementatie.

Hoewel C verschillende objectgeoriënteerde composite-constructies niet native biedt, zijn deze beperkingen geïsoleerd tot specifieke FRELSPEC-composite-bepalingen en hieronder gedocumenteerd. Deze mislukkingen verhinderen niet dat C als geheel within spec wordt beschouwd, maar ze moeten worden begrepen wanneer C wordt gebruikt voor CatalystUI-compatibele implementaties.

#### Beoordelingsaannames

Deze beoordeling gaat uit van moderne standaard-C-ondersteuning waar versieafhankelijke functies worden genoemd. Exact-width integer-ondersteuning veronderstelt dat de bijbehorende `<stdint.h>`-typen door de implementatie worden geleverd.

Deze beoordeling behandelt C als een low-level representatietaal. Byte-exacte encoderingen kunnen direct worden weergegeven via byte arrays, lookup tables en expliciete parsinglogica wanneer geen benoemde standaardcodec wordt geleverd.

### Waarschuwingen

* Exact-width integer-typen zijn afhankelijk van implementatieondersteuning.
* CP1252 kan byte-for-byte worden weergegeven, maar er wordt geen benoemde standaardcodec geleverd.
* UTF-16LE-serialisatie vereist expliciete byte-order-afhandeling.
* Standard threads kunnen door sommige C-implementaties worden weggelaten.
* Objectgeoriënteerde patronen kunnen handmatig worden nagebootst, maar zijn geen native taalconstructies.

### Mislukkingen

* C biedt geen native method members.
* C biedt geen native properties.
* C biedt geen native classes.
* C biedt geen native interfaces.

### FDEFSPEC-verificatie

#### Numerieke waarden

| Bepaling | Geverifieerd | Opmerkingen                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Gebruik bit-fields of masks.                    |
| Nibble    | ⚠️       | Gebruik bit-fields of masks.                    |
| Byte      | ✅        | Ondersteund via `unsigned char`.          |
| Short     | ✅        | Ondersteund via `int16_t` en `uint16_t`. |
| Int       | ✅        | Ondersteund via `int32_t` en `uint32_t`. |
| Long      | ✅        | Ondersteund via `int64_t` en `uint64_t`. |
| Float     | ✅        | Ondersteund via `float`.                  |
| Double    | ✅        | Ondersteund via `double`.                 |
| Boolean   | ✅        | Ondersteund via `bool`; C99+.             |

#### Tekstcodering

| Bepaling | Geverifieerd | Opmerkingen                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | Ondersteund via `char32_t`; C11+.     |
| ASCII     | ✅        | Weer te geven als bytewaarden.           |
| CP1252    | ⚠️        | Vereist expliciete byte mapping.         |
| UTF-8     | ✅        | Ondersteund via UTF-8 literals; C11+. |
| UTF-16LE  | ⚠️        | Vereist byte-order-afhandeling.           |

#### Bewerkingsstatus

| Bepaling | Geverifieerd | Opmerkingen                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Kan worden weergegeven door een enum.  |
| Context   | ✅        | Kan worden weergegeven door een waarde.  |
| Operation | ✅        | Kan worden weergegeven door een waarde.  |
| Detail    | ✅        | Kan worden weergegeven door een waarde.  |
| Result    | ✅        | Kan worden weergegeven door een struct. |

### FRELSPEC-verificatie

#### Collecties

| Bepaling | Geverifieerd | Opmerkingen                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Kan worden weergegeven door structs. |
| Map       | ✅        | Kan worden weergegeven door structs. |
| Array     | ✅        | Native arrays worden ondersteund.   |
| File      | ✅        | Ondersteund via file-API's.   |
| Stream    | ✅        | Ondersteund via stream-API's. |

#### Geheugen

| Bepaling | Geverifieerd | Opmerkingen                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Addresses worden ondersteund.   |
| Pointer   | ✅        | Pointers worden ondersteund.    |
| Variable  | ✅        | Variables worden ondersteund.   |
| Constant  | ✅        | Ondersteund via `const`. |

#### Bewerkingen

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Weergegeven via machine operations. |
| Procedure   | ✅        | Ondersteund via `void` functions.     |
| Function    | ✅        | Ondersteund via returning functions.  |

#### Threading

| Provision  | Verified | Notes                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Ondersteund via hosted environments. |
| Thread     | ⚠️        | Ondersteund via `<threads.h>`; C11+. |
| Dispatcher | ✅        | Kan direct worden weergegeven.           |

#### Composieten

| Bepaling | Geverifieerd | Opmerkingen                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Struct members worden ondersteund.            |
| Object    | ✅        | Structs kunnen addressable composites vormen. |
| Field     | ✅        | Struct fields worden ondersteund.             |
| Method    | ❌        | Geen native method members.                |
| Property  | ❌        | Geen expliciete Get/Set accessor map.        |
| Structure | ✅        | Structures worden native ondersteund.       |
| Class     | ❌        | Geen native class construct.               |
| Interface | ❌        | Geen native interface construct.           |
