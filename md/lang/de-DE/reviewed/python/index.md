<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->
<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

# Prüfdetails

## Python

### Übersicht

Die Programmiersprache Python wurde zum 7. Juli 2026 anhand der Spezifikationen FDEFSPEC (Rev. 1) und FRELSPEC (Rev. 1) geprüft.

#### Prüferklärung

Obwohl Python viele erforderliche Konzepte durch eingebaute Typen, Objekte, Funktionen, Klassen, Module der Standardbibliothek und benutzerdefinierte Validierung darstellen kann, reichen diese Mechanismen nicht aus, um die anwendbaren CatalystUI-Spezifikationen auf Sprachebene zu erfüllen.

Python bietet starke Unterstützung für Textcodierung, Dateien, Streams, Objekte, Funktionen, Klassen, Eigenschaften, Prozesse, Threads und dispatchte Ausführung durch sein eingebautes Verhalten und seine Standardbibliothek. Python stellt jedoch nicht die erforderlichen skalaren numerischen Typen mit fester Breite bereit, definiert keine echten Konstanten und verlässt sich bei mehreren Konstrukten auf dynamisches Laufzeitverhalten, das andere verifizierte Sprachen direkter ausdrücken können.

Aus diesem Grund glauben wir nicht, dass Python ohne erhebliche zusätzliche Infrastruktur eine ausreichend stabile Grundlage für CatalystUI-konforme Implementierung bereitstellt.

Daher wurde Python nicht der Status CatalystUI Verified für Programmiersprachen gewährt.

#### Prüfannahmen

Diese Prüfung bewertet Python selbst und seine mitgelieferte Standardbibliothek.

Drittanbieterpakete, implementierungsspezifische Erweiterungen, optionale native Module, externe Typechecker, Transpiler und benutzerdefinierte Laufzeitframeworks werden nicht als Unterstützung auf Sprachebene behandelt.

### Warnungen

* Python stellt Ganzzahlen mit unbegrenzter Genauigkeit bereit, nicht Integer-Primitive mit fester Breite.
* Python `float` ist normalerweise doppelte Genauigkeit, aber keine eigenständige Familie mit fester Breite.
* Einige Low-Level-Speicherverhaltensweisen können `ctypes` oder implementierungsspezifisches Verhalten erfordern.
* Python-Type-Hints werden zur Laufzeit nicht erzwungen.
* Python unterstützt Eigenschaften, aber Setter-Verhalten kann ausgelassen werden.
* Python kann mehrere Strukturen durch Standardbibliotheksfeatures modellieren, aber nicht als nativen Strukturtyp.

### Fehler

* Python stellt die meisten erforderlichen skalaren numerischen Typen mit fester Breite nicht bereit.
* Python stellt keinen dedizierten skalaren 32-Bit-Gleitkommatyp bereit.
* Python stellt keine echten Konstanten auf Sprachebene bereit.
* Python definiert Prozeduren nicht getrennt von Funktionen.
* Python stellt keine native Pointer-Unterstützung bereit.
* Python stellt keine native Interface-Unterstützung bereit.

### FDEFSPEC-Verifizierung

#### Numerische Werte

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------------ |
| Bit       | ❌        | Kein 1-Bit-Zahlentyp. |
| Nibble    | ❌        | Kein 4-Bit-Zahlentyp. |
| Byte      | ❌        | Kein skalarer 8-Bit-Integer-Typ. |
| Short     | ❌        | Kein skalarer 16-Bit-Integer-Typ. |
| Int       | ❌        | Kein skalarer 32-Bit-Integer-Typ. |
| Long      | ❌        | Kein skalarer 64-Bit-Integer-Typ. |
| Float     | ❌        | Kein skalarer 32-Bit-Float-Typ. |
| Double    | ⚠️       | `float` ist normalerweise doppelte Genauigkeit. |
| Boolean   | ✅        | Unterstützt durch `bool`. |

#### Textcodierung

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | -------------------------------- |
| Codepoint | ✅        | Strings verwenden Unicode-Codepoints. |
| ASCII     | ✅        | Unterstützter Codec. |
| CP1252    | ✅        | Unterstützter Codec. |
| UTF-8     | ✅        | Unterstützter Codec. |
| UTF-16LE  | ✅        | Unterstützter Codec. |

#### Betriebsstatus

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | --------------------------- |
| Status    | ⚠️       | Erfordert benutzerdefinierte Validierung. |
| Context   | ⚠️       | Erfordert benutzerdefinierte Validierung. |
| Operation | ⚠️       | Erfordert benutzerdefinierte Validierung. |
| Detail    | ⚠️       | Erfordert benutzerdefinierte Validierung. |
| Result    | ⚠️       | Erfordert benutzerdefinierte Validierung. |

### FRELSPEC-Verifizierung

#### Sammlungen

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Unterstützt durch `set`. |
| Map       | ✅        | Unterstützt durch `dict`. |
| Array     | ✅        | Unterstützt durch Sequenzen. |
| File      | ✅        | Unterstützt durch Datei-APIs. |
| Stream    | ✅        | Unterstützt durch Stream-APIs. |

#### Speicher

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ---------------------------- |
| Address   | ⚠️       | Nur Objektidentität. |
| Pointer   | ❌        | Keine native Pointer-Unterstützung. |
| Variable  | ✅        | Namensbindungen werden unterstützt. |
| Constant  | ❌        | Keine echten Konstanten. |

#### Operationen

| Bestimmung | Verifiziert | Hinweise |
| ----------- | -------- | --------------------------------- |
| Instruction | ⚠️       | Bytecode ist implementierungsspezifisch. |
| Procedure   | ❌        | Funktionen geben `None` zurück. |
| Function    | ✅        | Funktionen werden unterstützt. |

#### Threading

| Bestimmung | Verifiziert | Hinweise |
| ---------- | -------- | -------------------------------- |
| Process    | ✅        | Unterstützt durch Prozess-APIs. |
| Thread     | ✅        | Unterstützt durch `threading`. |
| Dispatcher | ✅        | Unterstützt durch Executor-APIs. |

#### Zusammengesetzte Strukturen

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | -------------------------------- |
| Member    | ✅        | Objekt-Member werden unterstützt. |
| Object    | ✅        | Objekte werden unterstützt. |
| Field     | ✅        | Attribute können Felder darstellen. |
| Method    | ✅        | Methoden werden unterstützt. |
| Property  | ⚠️       | Getter/Setter-Unterstützung existiert. |
| Structure | ⚠️       | Nur Standardbibliotheksmodelle. |
| Class     | ✅        | Klassen werden unterstützt. |
| Interface | ❌        | Keine native Interface-Unterstützung. |
