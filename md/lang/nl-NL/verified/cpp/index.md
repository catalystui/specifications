<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden beoordeeld. -->
<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

# Verificatiedetails

## C++

### Overzicht

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


De programmeertaal C++ is op 7 juli 2026 geverifieerd aan de hand van de FDEFSPEC (Rev. 1)- en FRELSPEC (Rev. 1)-specificaties.

#### Verklaring te goeder trouw

Wij geloven te goeder trouw dat de programmeertaal C++ de concepten en bepalingen die in de volgende specificaties zijn gedefinieerd redelijkerwijs kan vertegenwoordigen, en dat zij kan worden gebruikt om systemen te implementeren die aan deze specificaties voldoen.

#### Beoordelingsaannames

Deze beoordeling gaat uit van moderne standaard-C++-ondersteuning waar versieafhankelijke functies worden genoemd. Exact-width integer-ondersteuning veronderstelt dat de bijbehorende `<cstdint>`-typen door de implementatie worden geleverd.

Deze beoordeling behandelt C++ als een systems programming language met directe ondersteuning voor low-level representatie, objectmodellering, geheugencontrole, generiek programmeren en concurrente uitvoering.

### Waarschuwingen

* Exact-width integer-typen zijn afhankelijk van implementatieondersteuning.
* CP1252 kan byte-for-byte worden weergegeven, maar er wordt geen benoemde standaardcodec geleverd.
* UTF-16LE-serialisatie vereist expliciete byte-order-afhandeling.
* Sommige concurrency- en character-functies vereisen moderne C++-revisies.

### Mislukkingen

* Tijdens deze verificatie zijn geen bekende FDEFSPEC- of FRELSPEC-mislukkingen gevonden.

### FDEFSPEC-verificatie

#### Numerieke waarden

| Bepaling | Geverifieerd | Opmerkingen                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Gebruik bit-fields of masks.                    |
| Nibble    | ⚠️       | Gebruik bit-fields of masks.                    |
| Byte      | ✅        | Supported through `std::byte`.              |
| Short     | ✅        | Ondersteund via `int16_t` en `uint16_t`. |
| Int       | ✅        | Ondersteund via `int32_t` en `uint32_t`. |
| Long      | ✅        | Ondersteund via `int64_t` en `uint64_t`. |
| Float     | ✅        | Ondersteund via `float`.                  |
| Double    | ✅        | Ondersteund via `double`.                 |
| Boolean   | ✅        | Ondersteund via `bool`.                   |

#### Tekstcodering

| Bepaling | Geverifieerd | Opmerkingen                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Ondersteund via `char32_t`.        |
| ASCII     | ✅        | Weer te geven als bytewaarden.        |
| CP1252    | ⚠️        | Vereist expliciete byte mapping.      |
| UTF-8     | ✅        | Ondersteund via `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Vereist byte-order-afhandeling.        |

#### Bewerkingsstatus

| Bepaling | Geverifieerd | Opmerkingen                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Kan worden weergegeven door een enum.           |
| Context   | ✅        | Kan worden weergegeven door een waarde.           |
| Operation | ✅        | Kan worden weergegeven door een waarde.           |
| Detail    | ✅        | Kan worden weergegeven door een waarde.           |
| Result    | ✅        | Kan worden weergegeven door een struct of class. |

### FRELSPEC-verificatie

#### Collecties

| Bepaling | Geverifieerd | Opmerkingen                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Ondersteund via `std::set`.              |
| Map       | ✅        | Ondersteund via `std::map`.              |
| Array     | ✅        | Ondersteund via arrays en `std::array`. |
| File      | ✅        | Ondersteund via file streams.            |
| Stream    | ✅        | Ondersteund via iostreams.               |

#### Geheugen

| Bepaling | Geverifieerd | Opmerkingen                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Addresses worden ondersteund.                   |
| Pointer   | ✅        | Pointers worden ondersteund.                    |
| Variable  | ✅        | Variables worden ondersteund.                   |
| Constant  | ✅        | Ondersteund via `const` en `constexpr`. |

#### Bewerkingen

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Weergegeven via machine operations. |
| Procedure   | ✅        | Ondersteund via `void` functions.     |
| Function    | ✅        | Ondersteund via returning functions.  |

#### Threading

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Ondersteund via hosted execution.      |
| Thread     | ✅        | Ondersteund via `std::thread`; C++11+. |
| Dispatcher | ✅        | Ondersteund via async en schedulers.  |

#### Composieten

| Bepaling | Geverifieerd | Opmerkingen                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Class members worden ondersteund.            |
| Object    | ✅        | Objects worden ondersteund.                  |
| Field     | ✅        | Fields worden ondersteund.                   |
| Method    | ✅        | Methods worden ondersteund.                  |
| Property  | ✅        | Get/Set maps kunnen worden weergegeven.        |
| Structure | ✅        | Structures worden native ondersteund.      |
| Class     | ✅        | Classes worden native ondersteund.         |
| Interface | ✅        | Can be represented by abstract classes. |
