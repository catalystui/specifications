<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->
<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

# Verifizierungsdetails

## C

### Übersicht

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Die Programmiersprache C wurde zum 7. Juli 2026 anhand der Spezifikationen FDEFSPEC (Rev. 1) und FRELSPEC (Rev. 1) verifiziert.

#### Erklärung nach bestem Wissen und Gewissen

Wir glauben nach bestem Wissen und Gewissen, dass die Programmiersprache C die in den folgenden Spezifikationen definierten Konzepte und Bestimmungen angemessen darstellen kann und dass sie verwendet werden kann, um Systeme zu implementieren, die mit diesen Spezifikationen konform sind.

#### Prüferklärung

C bietet starke Low-Level-Unterstützung für grundlegende Datenrepräsentation, Speicherzugriff, Dateien, Streams, Prozeduren, Funktionen, Strukturen und direkte systemorientierte Implementierung.

Obwohl C mehrere objektorientierte zusammengesetzte Konstrukte nicht nativ bereitstellt, sind diese Einschränkungen auf bestimmte FRELSPEC-Bestimmungen für zusammengesetzte Strukturen beschränkt und unten dokumentiert. Diese Fehler verhindern nicht, dass C insgesamt als spezifikationskonform betrachtet wird, sollten aber beim Einsatz von C für CatalystUI-kompatible Implementierungen verstanden werden.

#### Prüfannahmen

Diese Prüfung setzt moderne Standard-C-Unterstützung voraus, wobei versionsabhängige Features entsprechend vermerkt sind. Unterstützung für Integer mit exakter Breite setzt voraus, dass die entsprechenden `<stdint.h>`-Typen von der Implementierung bereitgestellt werden.

Diese Prüfung behandelt C als Low-Level-Repräsentationssprache. Bytegenaue Codierungen können direkt durch Bytearrays, Nachschlagetabellen und explizite Parsing-Logik dargestellt werden, wenn kein benannter Standard-Codec bereitgestellt wird.

### Warnungen

* Integer-Typen mit exakter Breite hängen von der Unterstützung der Implementierung ab.
* CP1252 kann bytegenau dargestellt werden, aber es wird kein benannter Standard-Codec bereitgestellt.
* UTF-16LE-Serialisierung erfordert explizite Behandlung der Byte-Reihenfolge.
* Standard-Threads können von einigen C-Implementierungen ausgelassen werden.
* Objektorientierte Muster können manuell emuliert werden, sind aber keine nativen Sprachkonstrukte.

### Fehler

* C stellt keine nativen Methoden-Member bereit.
* C stellt keine nativen Eigenschaften bereit.
* C stellt keine nativen Klassen bereit.
* C stellt keine nativen Interfaces bereit.

### FDEFSPEC-Verifizierung

#### Numerische Werte

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Bitfelder oder Masken verwenden. |
| Nibble    | ⚠️       | Bitfelder oder Masken verwenden. |
| Byte      | ✅        | Unterstützt durch `unsigned char`. |
| Short     | ✅        | Unterstützt durch `int16_t` und `uint16_t`. |
| Int       | ✅        | Unterstützt durch `int32_t` und `uint32_t`. |
| Long      | ✅        | Unterstützt durch `int64_t` und `uint64_t`. |
| Float     | ✅        | Unterstützt durch `float`. |
| Double    | ✅        | Unterstützt durch `double`. |
| Boolean   | ✅        | Unterstützt durch `bool`; C99+. |

#### Textcodierung

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | Unterstützt durch `char32_t`; C11+. |
| ASCII     | ✅        | Als Bytewerte darstellbar. |
| CP1252    | ⚠️        | Erfordert explizites Byte-Mapping. |
| UTF-8     | ✅        | Unterstützt durch UTF-8-Literale; C11+. |
| UTF-16LE  | ⚠️        | Erfordert Behandlung der Byte-Reihenfolge. |

#### Betriebsstatus

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Kann durch ein Enum dargestellt werden. |
| Context   | ✅        | Kann durch einen Wert dargestellt werden. |
| Operation | ✅        | Kann durch einen Wert dargestellt werden. |
| Detail    | ✅        | Kann durch einen Wert dargestellt werden. |
| Result    | ✅        | Kann durch eine Struct dargestellt werden. |

### FRELSPEC-Verifizierung

#### Sammlungen

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Kann durch Structs dargestellt werden. |
| Map       | ✅        | Kann durch Structs dargestellt werden. |
| Array     | ✅        | Native Arrays werden unterstützt. |
| File      | ✅        | Unterstützt durch Datei-APIs. |
| Stream    | ✅        | Unterstützt durch Stream-APIs. |

#### Speicher

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Adressen werden unterstützt. |
| Pointer   | ✅        | Pointer werden unterstützt. |
| Variable  | ✅        | Variablen werden unterstützt. |
| Constant  | ✅        | Unterstützt durch `const`. |

#### Operationen

| Bestimmung | Verifiziert | Hinweise |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Dargestellt durch Maschinenoperationen. |
| Procedure   | ✅        | Unterstützt durch `void`-Funktionen. |
| Function    | ✅        | Unterstützt durch Funktionen mit Rückgabewert. |

#### Threading

| Bestimmung | Verifiziert | Hinweise |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Unterstützt durch gehostete Umgebungen. |
| Thread     | ⚠️        | Unterstützt durch `<threads.h>`; C11+. |
| Dispatcher | ✅        | Kann direkt dargestellt werden. |

#### Zusammengesetzte Strukturen

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Struct-Member werden unterstützt. |
| Object    | ✅        | Structs können adressierbare zusammengesetzte Strukturen bilden. |
| Field     | ✅        | Struct-Felder werden unterstützt. |
| Method    | ❌        | Keine nativen Methoden-Member. |
| Property  | ❌        | Keine explizite Get/Set-Accessor-Map. |
| Structure | ✅        | Strukturen werden nativ unterstützt. |
| Class     | ❌        | Kein natives Klassenkonstrukt. |
| Interface | ❌        | Kein natives Interface-Konstrukt. |
