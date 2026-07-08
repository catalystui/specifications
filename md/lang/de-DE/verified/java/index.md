<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->
<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

# Verifizierungsdetails

## Java

### Übersicht

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Die Programmiersprache Java wurde zum 7. Juli 2026 anhand der Spezifikationen FDEFSPEC (Rev. 1) und FRELSPEC (Rev. 1) verifiziert.

#### Erklärung nach bestem Wissen und Gewissen

Wir glauben nach bestem Wissen und Gewissen, dass die Programmiersprache Java einen großen Teil der in den folgenden Spezifikationen definierten Konzepte und Bestimmungen angemessen darstellen kann und dass sie verwendet werden kann, um Systeme zu implementieren, die mit diesen Spezifikationen konform sind.

#### Prüfannahmen

Diese Prüfung setzt moderne Java-Sprachunterstützung voraus, wobei versionsabhängige Features entsprechend vermerkt sind. Features wie lokale Variableninferenz, Records und Foreign-Memory-Zugriff können spätere Java-Versionen erfordern.

### Warnungen

* Java besitzt keine native Unterstützung für vorzeichenlose numerische Typen, was für bestimmte Bestimmungen Erweiterung oder alternative Repräsentationen erfordern kann.
* Direkte Speicheradress- und Pointer-artige Verhaltensweisen können Java 22+ Foreign Function and Memory API-Unterstützung erfordern.
* Java besitzt keine native Property-Syntax und benötigt stattdessen Getter- und Setter-Methoden.

### Fehler

* Java stellt CP1252 nicht als garantiertes Standard-Charset bereit und erfordert daher implementierungsspezifische Unterstützung, zusätzliche Bibliotheken oder eigene Behandlung für vollständige Konformität.
* Java-Properties stellen keinen expliziten schlüsselgebundenen Member bereit, der durch eine erforderliche Get/Set-Accessor-Map abgesichert ist.

### FDEFSPEC-Verifizierung

#### Numerische Werte

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | Kein 1-Bit-Zahlentyp; erweitern. |
| Nibble    | ⚠️       | Kein 4-Bit-Zahlentyp; erweitern. |
| Byte      | ⚠️       | Nur signierte 8-Bit-Werte; für unsigned erweitern. |
| Short     | ⚠️       | Nur signierte 16-Bit-Werte; für unsigned erweitern. |
| Int       | ⚠️       | Signierte 32-Bit-Werte; unsigned-Hilfen erfordern Java 8+. |
| Long      | ⚠️       | Signierte 64-Bit-Werte; unsigned-Hilfen erfordern Java 8+. |
| Float     | ✅        | 32-Bit-Gleitkomma wird unterstützt. |
| Double    | ✅        | 64-Bit-Gleitkomma wird unterstützt. |
| Boolean   | ✅        | Boolean-Typ wird unterstützt. |

#### Textcodierung

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Unterstützt durch `int` und `Character`. |
| ASCII     | ✅        | Garantiertes Standard-Charset. |
| CP1252    | ❌        | Nicht durch `StandardCharsets` garantiert. |
| UTF-8     | ✅        | Garantiertes Standard-Charset. |
| UTF-16LE  | ✅        | Garantiertes Standard-Charset. |

#### Betriebsstatus

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Kann durch einen benutzerdefinierten Typ dargestellt werden. |
| Context   | ✅        | Kann durch einen benutzerdefinierten Wert dargestellt werden. |
| Operation | ✅        | Kann durch einen benutzerdefinierten Wert dargestellt werden. |
| Detail    | ✅        | Kann durch einen benutzerdefinierten Wert dargestellt werden. |
| Result    | ✅        | Kann durch einen benutzerdefinierten Rückgabetyp dargestellt werden. |

### FRELSPEC-Verifizierung

#### Sammlungen

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Unterstützt durch `Set`. |
| Map       | ✅        | Unterstützt durch `Map`. |
| Array     | ✅        | Native Arrays werden unterstützt. |
| File      | ✅        | Unterstützt durch Datei-APIs. |
| Stream    | ✅        | Unterstützt durch Stream-APIs. |

#### Speicher

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direkte Adressen erfordern Java 22+ FFM. |
| Pointer   | ⚠️       | Pointer-artiger Zugriff erfordert Java 22+ FFM. |
| Variable  | ✅        | Deklarationen und `var` werden unterstützt; `var` erfordert Java 10+. |
| Constant  | ✅        | Unterstützt durch `final`. |

#### Operationen

| Bestimmung | Verifiziert | Hinweise |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Dargestellt durch Bytecode und Operationen. |
| Procedure   | ✅        | Unterstützt durch `void`-Methoden. |
| Function    | ✅        | Unterstützt durch Methoden mit Rückgabewert. |

#### Threading

| Bestimmung | Verifiziert | Hinweise |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Unterstützt durch Anwendungs- und `Process`-APIs. |
| Thread     | ✅        | Unterstützt durch `Thread`. |
| Dispatcher | ✅        | Unterstützt durch `Executor`-APIs. |

#### Zusammengesetzte Strukturen

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Klassen-Member werden unterstützt. |
| Object    | ✅        | Objekte werden unterstützt. |
| Field     | ✅        | Felder werden unterstützt. |
| Method    | ✅        | Methoden werden unterstützt. |
| Property  | ❌        | Keine explizite Accessor-Map. |
| Structure | ✅        | Unterstützt durch Records; Java 16+. |
| Class     | ✅        | Klassen werden unterstützt. |
| Interface | ✅        | Interfaces werden unterstützt. |
