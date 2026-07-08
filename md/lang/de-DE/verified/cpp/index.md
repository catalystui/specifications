<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->
<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

# Verifizierungsdetails

## C++

### Übersicht

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Die Programmiersprache C++ wurde zum 7. Juli 2026 anhand der Spezifikationen FDEFSPEC (Rev. 1) und FRELSPEC (Rev. 1) verifiziert.

#### Erklärung nach bestem Wissen und Gewissen

Wir glauben nach bestem Wissen und Gewissen, dass die Programmiersprache C++ die in den folgenden Spezifikationen definierten Konzepte und Bestimmungen angemessen darstellen kann und dass sie verwendet werden kann, um Systeme zu implementieren, die mit diesen Spezifikationen konform sind.

#### Prüfannahmen

Diese Prüfung setzt moderne Standard-C++-Unterstützung voraus, wobei versionsabhängige Features entsprechend vermerkt sind. Unterstützung für Integer mit exakter Breite setzt voraus, dass die entsprechenden `<cstdint>`-Typen von der Implementierung bereitgestellt werden.

Diese Prüfung behandelt C++ als Systemprogrammiersprache mit direkter Unterstützung für Low-Level-Repräsentation, Objektmodellierung, Speicherkontrolle, generische Programmierung und nebenläufige Ausführung.

### Warnungen

* Integer-Typen mit exakter Breite hängen von der Unterstützung der Implementierung ab.
* CP1252 kann bytegenau dargestellt werden, aber es wird kein benannter Standard-Codec bereitgestellt.
* UTF-16LE-Serialisierung erfordert explizite Behandlung der Byte-Reihenfolge.
* Einige Nebenläufigkeits- und Zeichenfeatures erfordern moderne C++-Revisionen.

### Fehler

* Während dieser Verifizierung wurden keine bekannten FDEFSPEC- oder FRELSPEC-Fehler gefunden.

### FDEFSPEC-Verifizierung

#### Numerische Werte

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Bitfelder oder Masken verwenden. |
| Nibble    | ⚠️       | Bitfelder oder Masken verwenden. |
| Byte      | ✅        | Unterstützt durch `std::byte`. |
| Short     | ✅        | Unterstützt durch `int16_t` und `uint16_t`. |
| Int       | ✅        | Unterstützt durch `int32_t` und `uint32_t`. |
| Long      | ✅        | Unterstützt durch `int64_t` und `uint64_t`. |
| Float     | ✅        | Unterstützt durch `float`. |
| Double    | ✅        | Unterstützt durch `double`. |
| Boolean   | ✅        | Unterstützt durch `bool`. |

#### Textcodierung

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Unterstützt durch `char32_t`. |
| ASCII     | ✅        | Als Bytewerte darstellbar. |
| CP1252    | ⚠️        | Erfordert explizites Byte-Mapping. |
| UTF-8     | ✅        | Unterstützt durch `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Erfordert Behandlung der Byte-Reihenfolge. |

#### Betriebsstatus

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Kann durch ein Enum dargestellt werden. |
| Context   | ✅        | Kann durch einen Wert dargestellt werden. |
| Operation | ✅        | Kann durch einen Wert dargestellt werden. |
| Detail    | ✅        | Kann durch einen Wert dargestellt werden. |
| Result    | ✅        | Kann durch eine Struct oder Klasse dargestellt werden. |

### FRELSPEC-Verifizierung

#### Sammlungen

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Unterstützt durch `std::set`. |
| Map       | ✅        | Unterstützt durch `std::map`. |
| Array     | ✅        | Unterstützt durch Arrays und `std::array`. |
| File      | ✅        | Unterstützt durch Dateistreams. |
| Stream    | ✅        | Unterstützt durch iostreams. |

#### Speicher

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Adressen werden unterstützt. |
| Pointer   | ✅        | Pointer werden unterstützt. |
| Variable  | ✅        | Variablen werden unterstützt. |
| Constant  | ✅        | Unterstützt durch `const` und `constexpr`. |

#### Operationen

| Bestimmung | Verifiziert | Hinweise |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Dargestellt durch Maschinenoperationen. |
| Procedure   | ✅        | Unterstützt durch `void`-Funktionen. |
| Function    | ✅        | Unterstützt durch Funktionen mit Rückgabewert. |

#### Threading

| Bestimmung | Verifiziert | Hinweise |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Unterstützt durch gehostete Ausführung. |
| Thread     | ✅        | Unterstützt durch `std::thread`; C++11+. |
| Dispatcher | ✅        | Unterstützt durch async und Scheduler. |

#### Zusammengesetzte Strukturen

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Klassen-Member werden unterstützt. |
| Object    | ✅        | Objekte werden unterstützt. |
| Field     | ✅        | Felder werden unterstützt. |
| Method    | ✅        | Methoden werden unterstützt. |
| Property  | ✅        | Get/Set-Maps können dargestellt werden. |
| Structure | ✅        | Strukturen werden nativ unterstützt. |
| Class     | ✅        | Klassen werden nativ unterstützt. |
| Interface | ✅        | Kann durch abstrakte Klassen dargestellt werden. |
