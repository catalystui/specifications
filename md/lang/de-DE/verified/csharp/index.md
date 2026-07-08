<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->
<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

# Verifizierungsdetails

## C#

### Übersicht

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Die Programmiersprache C# wurde zum 7. Juli 2026 anhand der Spezifikationen FDEFSPEC (Rev. 1) und FRELSPEC (Rev. 1) verifiziert.

#### Erklärung nach bestem Wissen und Gewissen

Wir glauben nach bestem Wissen und Gewissen, dass die Programmiersprache C# die in den folgenden Spezifikationen definierten Konzepte und Bestimmungen angemessen darstellen kann und dass sie verwendet werden kann, um Systeme zu implementieren, die mit diesen Spezifikationen konform sind.

#### Prüfannahmen

Diese Prüfung setzt moderne C#- und .NET-Unterstützung voraus, wobei versionsabhängige Features entsprechend vermerkt sind.

### Warnungen

* CP1252-Unterstützung ist über den offiziellen .NET-Codepages-Provider verfügbar, kann aber je nach Ziel-Laufzeitumgebung eine Provider-Registrierung oder ein zusätzliches Paket erfordern.
* Unsicheres Pointer-Verhalten kann eine explizite `unsafe`-Autorisierung erfordern.

### Fehler

* Während dieser Verifizierung wurden keine bekannten FDEFSPEC- oder FRELSPEC-Fehler gefunden.

### FDEFSPEC-Verifizierung

#### Numerische Werte

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | Kein 1-Bit-Zahlentyp; erweitern. |
| Nibble    | ⚠️       | Kein 4-Bit-Zahlentyp; erweitern. |
| Byte      | ✅        | Unterstützt durch `byte` und `sbyte`. |
| Short     | ✅        | Unterstützt durch `short` und `ushort`. |
| Int       | ✅        | Unterstützt durch `int` und `uint`. |
| Long      | ✅        | Unterstützt durch `long` und `ulong`. |
| Float     | ✅        | Unterstützt durch `float`. |
| Double    | ✅        | Unterstützt durch `double`. |
| Boolean   | ✅        | Unterstützt durch `bool`. |

#### Textcodierung

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | Unterstützt durch numerische Werte und `Rune`. |
| ASCII     | ✅        | Unterstützt durch `Encoding.ASCII`. |
| CP1252    | ⚠️       | Erfordert Codepages-Provider. |
| UTF-8     | ✅        | Unterstützt durch `Encoding.UTF8`. |
| UTF-16LE  | ✅        | Unterstützt durch `Encoding.Unicode`. |

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
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Unterstützt durch `HashSet<T>`. |
| Map       | ✅        | Unterstützt durch `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Native Arrays werden unterstützt. |
| File      | ✅        | Unterstützt durch Datei-APIs. |
| Stream    | ✅        | Unterstützt durch `Stream`. |

#### Speicher

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Unterstützt durch Referenzen und Pointer. |
| Pointer   | ✅        | Unterstützt durch unsichere Pointer. |
| Variable  | ✅        | Variablen werden unterstützt. |
| Constant  | ✅        | Unterstützt durch `const` und `readonly`. |

#### Operationen

| Bestimmung | Verifiziert | Hinweise |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Dargestellt durch IL und Operationen. |
| Procedure   | ✅        | Unterstützt durch `void`-Methoden. |
| Function    | ✅        | Unterstützt durch Methoden mit Rückgabewert. |

#### Threading

| Bestimmung | Verifiziert | Hinweise |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Unterstützt durch Anwendungs- und `Process`-APIs. |
| Thread     | ✅        | Unterstützt durch `Thread`. |
| Dispatcher | ✅        | Unterstützt durch Tasks und Scheduler. |

#### Zusammengesetzte Strukturen

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Typ-Member werden unterstützt. |
| Object    | ✅        | Objekte werden unterstützt. |
| Field     | ✅        | Felder werden unterstützt. |
| Method    | ✅        | Methoden werden unterstützt. |
| Property  | ✅        | Eigenschaften werden nativ unterstützt. |
| Structure | ✅        | Strukturen werden nativ unterstützt. |
| Class     | ✅        | Klassen werden unterstützt. |
| Interface | ✅        | Interfaces werden unterstützt. |
