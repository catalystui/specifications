<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->
<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

# Prüfdetails

## JavaScript

### Übersicht

Die Programmiersprache JavaScript wurde zum 7. Juli 2026 anhand der Spezifikationen FDEFSPEC (Rev. 1) und FRELSPEC (Rev. 1) geprüft.

#### Prüferklärung

Obwohl JavaScript einige erforderliche Konzepte durch Objekte, Funktionen, Arrays und eingebautes Sprachverhalten darstellen kann, reichen diese Mechanismen nicht aus, um die anwendbaren CatalystUI-Spezifikationen auf Sprachebene zu erfüllen.

Diese Prüfung bewertet JavaScript selbst, nicht das umliegende JavaScript-Ökosystem. Browser-APIs, Node.js-APIs, Deno-APIs, Bun-APIs, Web-APIs, TypeScript, WebAssembly, externe Bibliotheken und benutzerdefinierte Validierung werden nicht als Unterstützung auf Sprachebene behandelt.

Da JavaScript viele erforderliche skalare numerische Typen mit fester Breite nicht besitzt, erforderliche Textcodierungen nicht als Sprachfeatures bereitstellt und mehrere erforderliche System-, Speicher-, Threading- und zusammengesetzte Konstrukte nicht definiert, glauben wir nicht, dass JavaScript ohne erhebliche zusätzliche Infrastruktur eine ausreichend stabile Grundlage für CatalystUI-konforme Implementierung bereitstellt.

Daher wurde JavaScript nicht der Status CatalystUI Verified für Programmiersprachen gewährt.

#### Prüfannahmen

Diese Prüfung wendet einen strengen Standard auf Sprachebene an. Wenn eine Bestimmung nicht ausdrücklich durch JavaScript selbst unterstützt wird, wird sie als nicht verifiziert markiert.

Vom Host bereitgestellte APIs, implementierungsspezifisches Verhalten, externe Bibliotheken, Transpiler, Typsysteme und benutzerdefinierte Laufzeitvalidierung sind von der Verifizierung ausgeschlossen.

### Warnungen

* JavaScript kann viele numerische Werte durch `Number` darstellen, aber `Number` ist ein 64-Bit-Gleitkommazahlentyp.
* JavaScript stellt `BigInt` bereit, aber `BigInt` besitzt beliebige Breite.
* Typed Arrays stellen binäre Speicheransichten bereit, keine skalaren Sprachtypen.
* JavaScript-Strings verwenden UTF-16-Codeeinheiten, keine expliziten Textcodierungswerte.
* `const` schützt Bindungen, nicht Objektwerte.

### Fehler

* JavaScript stellt die meisten erforderlichen skalaren numerischen Typen mit fester Breite nicht bereit.
* JavaScript stellt keinen dedizierten skalaren 32-Bit-Gleitkommatyp bereit.
* JavaScript stellt ASCII, CP1252, UTF-8 oder UTF-16LE nicht als Textcodierungen auf Sprachebene bereit.
* JavaScript stellt keine Datei- oder Stream-Konstrukte auf Sprachebene bereit.
* JavaScript stellt keine Adress- oder Pointer-Konstrukte auf Sprachebene bereit.
* JavaScript stellt keine Prozess-, Thread- oder Dispatcher-Konstrukte auf Sprachebene bereit.
* JavaScript-Properties stellen keinen expliziten schlüsselgebundenen Member bereit, der durch eine erforderliche Get/Set-Accessor-Map abgesichert ist.
* JavaScript stellt keine Strukturen oder Interfaces bereit.

### FDEFSPEC-Verifizierung

#### Numerische Werte

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------ |
| Bit       | ❌        | Kein 1-Bit-Zahlentyp. |
| Nibble    | ❌        | Kein 4-Bit-Zahlentyp. |
| Byte      | ❌        | Kein skalarer 8-Bit-Integer-Typ. |
| Short     | ❌        | Kein skalarer 16-Bit-Integer-Typ. |
| Int       | ❌        | Kein skalarer 32-Bit-Integer-Typ. |
| Long      | ❌        | Kein skalarer 64-Bit-Integer-Typ. |
| Float     | ❌        | Kein skalarer 32-Bit-Float-Typ. |
| Double    | ✅        | Unterstützt durch `Number`. |
| Boolean   | ✅        | Unterstützt durch `boolean`. |

#### Textcodierung

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ---------------------------- |
| Codepoint | ❌        | Kein dedizierter Codepoint-Typ. |
| ASCII     | ❌        | Nicht auf Sprachebene. |
| CP1252    | ❌        | Nicht auf Sprachebene. |
| UTF-8     | ❌        | Nicht auf Sprachebene. |
| UTF-16LE  | ❌        | Nicht auf Sprachebene. |

#### Betriebsstatus

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------- |
| Status    | ⚠️       | Darstellbar, nicht erzwingbar. |
| Context   | ⚠️       | Darstellbar, nicht erzwingbar. |
| Operation | ⚠️       | Darstellbar, nicht erzwingbar. |
| Detail    | ⚠️       | Darstellbar, nicht erzwingbar. |
| Result    | ⚠️       | Erfordert Laufzeitvalidierung. |

### FRELSPEC-Verifizierung

#### Sammlungen

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------ |
| Set       | ✅        | Unterstützt durch `Set`. |
| Map       | ✅        | Unterstützt durch `Map`. |
| Array     | ✅        | Arrays werden unterstützt. |
| File      | ❌        | Nicht auf Sprachebene. |
| Stream    | ❌        | Nicht auf Sprachebene. |

#### Speicher

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------- |
| Address   | ❌        | Keine Adressunterstützung. |
| Pointer   | ❌        | Keine Pointer-Unterstützung. |
| Variable  | ✅        | Variablen werden unterstützt. |
| Constant  | ⚠️       | `const` schützt nur Bindungen. |

#### Operationen

| Bestimmung | Verifiziert | Hinweise |
| ----------- | -------- | -------------------------------- |
| Instruction | ❌        | Kein definierter Instruktionstyp. |
| Procedure   | ❌        | Funktionen geben immer einen Wert zurück. |
| Function    | ✅        | Funktionen werden unterstützt. |

#### Threading

| Bestimmung | Verifiziert | Hinweise |
| ---------- | -------- | --------------------------- |
| Process    | ❌        | Nicht auf Sprachebene. |
| Thread     | ⚠️        | Durch Agents dargestellt. |
| Dispatcher | ❌        | Erfordert Host-Scheduling. |


#### Zusammengesetzte Strukturen

| Bestimmung | Verifiziert | Hinweise |
| --------- | -------- | ------------------------------------- |
| Member    | ✅        | Objekt-Member werden unterstützt. |
| Object    | ✅        | Objekte werden unterstützt. |
| Field     | ✅        | Dateneigenschaften können Felder darstellen. |
| Method    | ✅        | Methoden werden unterstützt. |
| Property  | ❌        | Keine explizite Accessor-Map. |
| Structure | ❌        | Keine Strukturunterstützung. |
| Class     | ✅        | Klassensyntax wird unterstützt. |
| Interface | ❌        | Keine Interface-Unterstützung. |
