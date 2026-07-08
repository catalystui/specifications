<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->

<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

# I18NSPEC

<br/>

> **Spezifikation zur Internationalisierung**<br/>
> Revision 1<br/>
> 8. Juli 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Die hier vorgestellten Definitionen, Anforderungen und Konzepte beschreiben praktische Internationalisierungsunterstützung und dürfen frei neu ausgedrückt werden.

<a id="introduction"></a>
## Einführung

Die **Spezifikation zur Internationalisierung (I18NSPEC)** legt die Kernkonzepte, Terminologie und Anforderungen fest, die zur Bewertung mehrsprachiger Unterstützung innerhalb des CatalystUI-Ökosystems verwendet werden. Ihr Zweck ist es, einen klaren Standard dafür bereitzustellen, ob ein System, ein Dienst, ein Framework, eine Anwendung oder eine Implementierung ausreichende Sprachunterstützung bietet, um als innerhalb der Spezifikation zu gelten.

Internationalisierung ist wichtig, weil eine Benutzeroberfläche nicht klar kommunizieren kann, wenn ihre wesentliche Bedeutung nur in einer einzigen Sprache verfügbar ist. Ein System kann technisch funktionsfähig sein; wenn Benutzer jedoch seine Beschriftungen, Anweisungen, Steuerelemente, Einstellungen, Warnungen, Fehler oder zentralen Arbeitsabläufe nicht verstehen können, dann hat das System diesen Benutzern keine sinnvolle Schnittstelle bereitgestellt.

Diese Spezifikation versucht nicht, perfekte Übersetzungsqualität, literarischen Stil, kulturelle Anpassung, rechtliche Konformität oder vollständige regionale Lokalisierung zu messen. Stattdessen definiert sie die minimale mehrsprachige Grundlage, die erforderlich ist, damit Benutzer über den erforderlichen CatalystUI-Locale-Satz hinweg sinnvoll auf die wesentlichen Teile eines Systems zugreifen und sie bedienen können.

Einfacher gesagt stellt I18NSPEC drei Hauptfragen:

1. Können Benutzer in jeder erforderlichen Sprache auf die wesentlichen Teile des Systems zugreifen?
2. Können Benutzer die Sprache, die sie verstehen, vernünftig auswählen?
3. Bewahrt das System über Sprachen hinweg genügend Bedeutung, um benutzbar zu bleiben?

> [!IMPORTANT]
>
> I18NSPEC definiert Internationalisierungsanforderungen für die Verifizierung. Es handelt sich nicht um eine separate Spezifikation für jede Sprache. Jede erforderliche Locale wird gegen dieselbe Spezifikation geprüft.

<a id="table-of-contents"></a>
## Inhaltsverzeichnis

* [I18NSPEC](#i18nspec)

  * [Einführung](#introduction)
  * [Inhaltsverzeichnis](#table-of-contents)
  * [Konformität](#conformance)
  * [Erforderlicher Locale-Satz](#required-locale-set)
  * [Benutzerseitige Inhalte](#user-facing-content)

    * [Benutzerseitige Inhalte](#user-facing-content-1)
    * [Wesentliche benutzerseitige Inhalte](#essential-user-facing-content)
    * [Kritische benutzerseitige Inhalte](#critical-user-facing-content)
    * [Unwesentliche Inhalte](#nonessential-content)
  * [Übersetzungsabdeckung](#translation-coverage)

    * [Wesentliche Übersetzungsabdeckung](#essential-translation-coverage)
    * [Abdeckungsanforderung](#coverage-requirement)
    * [Anforderung an kritische Inhalte](#critical-content-requirement)
  * [Sprachauswahl](#language-selection)

    * [Aktive Locale](#active-locale)
    * [Standard-Locale](#default-locale)
    * [Mechanismus zur Sprachauswahl](#language-selection-mechanism)
    * [Bezeichnungen von Sprachoptionen](#language-option-labels)
  * [Fallbacks und Locale-Äquivalenz](#fallbacks-and-locale-equivalence)

    * [Fallback-Locale](#fallback-locale)
    * [Fallback-Verhalten](#fallback-behavior)
    * [Locale-Äquivalenz](#locale-equivalence)
  * [Implementierungsanforderungen](#implementation-requirements)

    * [Stabiler Übersetzungsmechanismus](#stable-translation-mechanism)
    * [Bewahrung der Bedeutung](#preservation-of-meaning)
    * [Richtungssensitive Sprachen](#direction-sensitive-languages)
    * [Locale-sensitive Werte](#locale-sensitive-values)
  * [Verifizierung](#verification)

    * [Within Spec](#within-spec)
    * [Warnungen](#warnings)
    * [Fehlschläge](#failures)
    * [Gültigkeit der Verifizierung](#verification-validity)

<a id="conformance"></a>
## Konformität

Ein System gilt als konform mit I18NSPEC, wenn es die in diesem Dokument definierten Anforderungen für jede Locale im erforderlichen Locale-Satz erfüllt.

Ein konformes System muss:

1. Jede Locale im erforderlichen Locale-Satz unterstützen.
2. Übersetzte Inhalte für mehr als 75 % der wesentlichen benutzerseitigen Inhalte in jeder erforderlichen Locale bereitstellen.
3. Übersetzte Inhalte für alle kritischen benutzerseitigen Inhalte in jeder erforderlichen Locale bereitstellen.
4. Einen vernünftigen Endbenutzermechanismus zur Auswahl der aktiven Locale bereitstellen.
5. Einen stabilen, für das System geeigneten Übersetzungsmechanismus verwenden.
6. Die wesentliche Bedeutung übersetzter benutzerseitiger Inhalte bewahren.
7. Vermeiden, sich auf Fallback-Inhalte zu stützen, um Übersetzungsabdeckung zu beanspruchen, außer wenn Locale-Äquivalenz während der Überprüfung akzeptiert wird.

Ein System muss kein bestimmtes Implementierungsmuster verwenden, um dieser Spezifikation zu entsprechen. Es kann Ressourcendateien, Übersetzungstabellen, localebewusstes Routing, kompilierte Sprachressourcen, statische lokalisierte Seiten, Laufzeit-Sprachpakete, datenbankgestützte Übersetzungen oder einen anderen stabilen, für das System geeigneten Mechanismus verwenden.

Bei der Verifizierung geht es um praktischen Benutzerzugang und wesentliche Bedeutung, nicht um eine starre technische Architektur.

<a id="required-locale-set"></a>
## Erforderlicher Locale-Satz

Der erforderliche Locale-Satz definiert die Sprachen und regionalen Varianten, die für CatalystUI Internationalization Verification überprüft werden müssen.

Der aktuelle erforderliche Locale-Satz enthält die folgenden Locales:

| Locale    | Sprache                  |
| --------- | ------------------------ |
| `ar-SA`   | Arabisch (Saudi-Arabien) |
| `bn-BD`   | Bengalisch (Bangladesch) |
| `de-DE`   | Deutsch (Deutschland)    |
| `en-GB`   | Englisch (Vereinigtes Königreich) |
| `en-IN`   | Englisch (Indien)        |
| `en-US`   | Englisch (Vereinigte Staaten) |
| `es-ES`   | Spanisch (Spanien)       |
| `es-MX`   | Spanisch (Mexiko)        |
| `fa-IR`   | Persisch (Iran)          |
| `fr-FR`   | Französisch (Frankreich) |
| `hi-IN`   | Hindi (Indien)           |
| `id-ID`   | Indonesisch (Indonesien) |
| `it-IT`   | Italienisch (Italien)    |
| `ja-JP`   | Japanisch (Japan)        |
| `ko-KR`   | Koreanisch (Südkorea)    |
| `nl-NL`   | Niederländisch (Niederlande) |
| `pl-PL`   | Polnisch (Polen)         |
| `pt-BR`   | Portugiesisch (Brasilien) |
| `ru-RU`   | Russisch (Russland)      |
| `tl-PH`   | Tagalog (Philippinen)    |
| `tr-TR`   | Türkisch (Türkei)        |
| `uk-UA`   | Ukrainisch (Ukraine)     |
| `ur-PK`   | Urdu (Pakistan)          |
| `vi-VN`   | Vietnamesisch (Vietnam)  |
| `zh-CN`   | Chinesisch (China)       |
| `zh-Hans` | Chinesisch (Vereinfacht) |

Ein System muss für jede aufgeführte Locale ausreichende wesentliche Übersetzungsunterstützung bereitstellen, um als innerhalb der Spezifikation zu gelten.

Der erforderliche Locale-Satz soll nicht jede Sprache, jeden Dialekt, jede Region oder jedes Schriftsystem darstellen. Stattdessen legt er eine praktische Grundlage für breite internationale Benutzbarkeit über viele häufige technologiebezogene Sprachgruppen hinweg fest.

<a id="user-facing-content"></a>
## Benutzerseitige Inhalte

<a id="user-facing-content-1"></a>
### Benutzerseitige Inhalte

Benutzerseitige Inhalte sind alle Inhalte, die von einem Endbenutzer wahrgenommen, gelesen, gehört, ausgewählt, verstanden oder als Grundlage für Handlungen verwendet werden sollen.

Benutzerseitige Inhalte können Folgendes umfassen:

* Navigation
* Beschriftungen
* Schaltflächen
* Menüs
* Steuerelemente
* Überschriften
* Dialoge
* Einstellungen
* Anweisungen
* Eingabeaufforderungen
* Warnungen
* Fehler
* Bestätigungen
* Statusmeldungen
* Einführungstexte
* erforderliche Hilfetexte
* Steuerelemente zur Sprachauswahl
* Inhalte zentraler Arbeitsabläufe

Benutzerseitige Inhalte müssen nicht visuell sein. Sie können auch auditive, taktile, symbolische oder multisensorische Inhalte umfassen, wenn diese Inhalte dem Benutzer Bedeutung vermitteln.

<a id="essential-user-facing-content"></a>
### Wesentliche benutzerseitige Inhalte

Wesentliche benutzerseitige Inhalte sind benutzerseitige Inhalte, die ein Benutzer vernünftigerweise benötigt, um das wesentliche Verhalten eines Systems zu verstehen, zu navigieren, zu konfigurieren oder zu bedienen.

Wesentliche benutzerseitige Inhalte können Folgendes umfassen:

* primäre Navigation
* zentrale Bildschirme und Ansichten
* Einstellungen und Präferenzen
* benutzerseitige Beschriftungen
* benutzerseitige Steuerelemente
* erforderliche Anweisungen
* wichtige Warnungen
* wichtige Fehler
* wesentliche Eingabeaufforderungen
* erforderliche Bestätigungsmeldungen
* Steuerelemente zur Sprachauswahl
* zentrale Arbeitsabläufe, die für die normale Nutzung benötigt werden

Ein System muss nicht jede optionale Seite, versteckte Meldung, interne Beschriftung oder jeden unwesentlichen Text übersetzen, um I18NSPEC zu erfüllen. Der für gewöhnliche wesentliche Nutzung erforderliche Inhalt muss jedoch gemäß den Anforderungen dieser Spezifikation übersetzt werden.

<a id="critical-user-facing-content"></a>
### Kritische benutzerseitige Inhalte

Kritische benutzerseitige Inhalte sind wesentliche benutzerseitige Inhalte, bei denen ein Missverständnis sinnvolle Nutzung verhindern, einen schwerwiegenden Fehler erzeugen oder den Benutzer dazu bringen kann, eine wichtige Entscheidung zu treffen, ohne die Konsequenz zu verstehen.

Kritische benutzerseitige Inhalte können Folgendes umfassen:

* Steuerelemente zur Sprachauswahl
* Warnungen vor destruktiven Aktionen
* Warnungen zur Kontolöschung
* Zahlungsbestätigungen
* Kaufbestätigungen
* Datenschutzentscheidungen
* Sicherheitswarnungen
* Zustimmungsaufforderungen
* erforderliche Sicherheitsanweisungen
* erforderliche Einrichtungsanweisungen
* erforderliche Fehlermeldungen
* zentrale Navigation, die erforderlich ist, um Spracheinstellungen zu erreichen

Kritische benutzerseitige Inhalte müssen für jede erforderliche Locale übersetzt werden.

Der Schwellenwert von 75 % wesentlicher Übersetzungsabdeckung darf nicht dazu verwendet werden, kritische Inhalte unübersetzt zu lassen.

<a id="nonessential-content"></a>
### Unwesentliche Inhalte

Unwesentliche Inhalte sind Inhalte, die vernünftigerweise nicht erforderlich sind, damit ein Benutzer das wesentliche Verhalten eines Systems verstehen, navigieren, konfigurieren oder bedienen kann.

Unwesentliche Inhalte können Folgendes umfassen:

* interne Bezeichner
* Quellcodenamen
* reine Debug-Zeichenketten
* entwicklerseitige Implementierungsdetails
* versteckte Diagnosetexte
* optionale Marketingseiten
* optionale Supportseiten
* unwesentliche rechtliche oder geschäftliche Texte außerhalb des geprüften Umfangs
* Drittanbieterinhalte, die nicht vom geprüften System kontrolliert werden

Unwesentliche Inhalte können übersetzt werden, sind aber für I18NSPEC-Konformität nicht erforderlich, sofern sie nicht für das wesentliche Benutzerverständnis oder die Bedienung notwendig werden.

<a id="translation-coverage"></a>
## Übersetzungsabdeckung

<a id="essential-translation-coverage"></a>
### Wesentliche Übersetzungsabdeckung

Wesentliche Übersetzungsabdeckung ist die Menge an wesentlichen benutzerseitigen Inhalten, die für eine bestimmte Locale übersetzt wurde.

Die Abdeckung sollte anhand sinnvoller benutzerseitiger Inhaltseinheiten bewertet werden, nicht anhand von Dateigröße, Byteanzahl, Zeilenanzahl, Repositorygröße oder Seitenanzahl.

Beispielsweise kann eine einzige unübersetzte Schaltfläche, die eine wesentliche Aktion steuert, wichtiger sein als ein großer unübersetzter optionaler Absatz, der die gewöhnliche Nutzung nicht beeinflusst.

Die Übersetzungsabdeckung sollte danach beurteilt werden, ob der Benutzer das wesentliche System in der geprüften Locale sinnvoll verstehen und bedienen kann.

<a id="coverage-requirement"></a>
### Abdeckungsanforderung

Ein System erfüllt die Anforderung an die Übersetzungsabdeckung für eine Locale, wenn mehr als 75 % der wesentlichen benutzerseitigen Inhalte für diese Locale übersetzt sind.

Ein System erfüllt die I18NSPEC-Abdeckungsanforderung, wenn es diesen Schwellenwert für jede Locale im erforderlichen Locale-Satz erreicht.

In einer praktischen Überprüfung kann dies so dargestellt werden:

| Locale  | Wesentliche Übersetzungsabdeckung | Ergebnis |
| ------- | --------------------------------- | -------- |
| `en-US` | 100%                              | Bestanden |
| `es-ES` | 94%                               | Bestanden |
| `ar-SA` | 78%                               | Bestanden |
| `ja-JP` | 61%                               | Fehlgeschlagen |

Eine Locale mit 75 % Abdeckung oder weniger erfüllt die Abdeckungsanforderung nicht.

Eine Locale mit mehr als 75 % Abdeckung kann dennoch fehlschlagen, wenn kritische benutzerseitige Inhalte unübersetzt sind.

<a id="critical-content-requirement"></a>
### Anforderung an kritische Inhalte

Alle kritischen benutzerseitigen Inhalte müssen für jede erforderliche Locale übersetzt werden.

Ein System kann I18NSPEC auch dann nicht erfüllen, wenn es den allgemeinen Abdeckungsschwellenwert erreicht, sofern ein oder mehrere kritische benutzerseitige Inhaltselemente fehlen, unübersetzt, irreführend oder nicht sinnvoll verständlich sind.

Beispielsweise sollte ein System nicht als innerhalb der Spezifikation betrachtet werden, wenn die allgemeine Oberfläche übersetzt ist, aber die Warnung zur Kontolöschung, die Kaufbestätigung, die Sicherheitswarnung oder der Sprachwähler unübersetzt bleibt.

<a id="language-selection"></a>
## Sprachauswahl

<a id="active-locale"></a>
### Aktive Locale

Die aktive Locale ist die Locale, die derzeit für die Benutzererfahrung ausgewählt ist.

Die aktive Locale bestimmt, welche übersetzten Inhalte dem Benutzer angezeigt, bereitgestellt oder anderweitig kommuniziert werden sollen.

<a id="default-locale"></a>
### Standard-Locale

Die Standard-Locale ist die Locale, die verwendet wird, wenn der Benutzer keine aktive Locale ausgewählt hat oder keine Benutzerpräferenz verfügbar ist.

Ein System muss eine Standard-Locale definieren.

Die Standard-Locale sollte dokumentiert oder für den Prüfer vernünftig ableitbar sein.

<a id="language-selection-mechanism"></a>
### Mechanismus zur Sprachauswahl

Ein konformes System muss eine vernünftige Möglichkeit bereitstellen, damit der Endbenutzer die aktive Locale ändern kann.

Der Sprachauswahlmechanismus muss verfügbar sein, ohne dass der Benutzer Folgendes tun muss:

* Quellcode ändern
* Entwicklertools verwenden
* undokumentierte Konfigurationsdateien bearbeiten
* inoffizielle Patches installieren
* sich auf verstecktes Verhalten verlassen
* den Support für gewöhnliche Sprachänderungen kontaktieren

Ein Sprachauswahlmechanismus kann bereitgestellt werden durch:

* Anwendungseinstellungen
* Kontopräferenzen
* einen Sprachwähler
* eine Startaufforderung
* Browsereinstellungen
* Betriebssystemeinstellungen
* Geräteeinstellungen
* einen anderen geeigneten, für Endbenutzer zugänglichen Mechanismus

Der Mechanismus muss keinem bestimmten Gestaltungsmuster folgen. Er muss dem Benutzer vernünftigerweise erlauben, eine unterstützte Sprache auszuwählen.

<a id="language-option-labels"></a>
### Bezeichnungen von Sprachoptionen

Beim Anzeigen von Sprachoptionen sollte ein System jede Sprache so kennzeichnen, dass sie für Benutzer verständlich ist, die diese Sprache sprechen.

Eine Sprachoption kann Folgendes enthalten:

* den Sprachnamen in dieser Sprache
* den Sprachnamen in der derzeit aktiven Sprache
* den Locale-Code
* eine regionale Bezeichnung
* eine Schriftbezeichnung

Zum Beispiel:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Das genaue Format kann variieren.

Die Absicht ist, dass Benutzer ihre eigene Sprache erkennen, den aktuell angezeigten Sprachnamen nach Möglichkeit verstehen und den zugehörigen Locale-Code identifizieren können.

<a id="fallbacks-and-locale-equivalence"></a>
## Fallbacks und Locale-Äquivalenz

<a id="fallback-locale"></a>
### Fallback-Locale

Eine Fallback-Locale ist eine Locale, die verwendet wird, wenn übersetzte Inhalte für die aktive Locale nicht verfügbar sind.

Fallback-Locales können helfen, Benutzbarkeit zu bewahren, aber Fallback-Inhalte gelten nicht automatisch als übersetzte Inhalte für die aktive Locale.

Wenn ein System beispielsweise auf `es-MX` eingestellt ist, aber `en-US`-Text anzeigt, weil die spanische Übersetzung fehlt, kann dieser englische Text als Fallback nützlich sein, sollte aber nicht als spanische Übersetzungsabdeckung gezählt werden.

<a id="fallback-behavior"></a>
### Fallback-Verhalten

Ein konformes System kann Fallback-Verhalten verwenden, wenn lokalisierte Inhalte nicht verfügbar sind.

Fallback-Verhalten sollte beschädigte, leere oder irreführende Ausgabe vermeiden.

Fallback-Verhalten darf nicht verwendet werden, um fälschlich Übersetzungsabdeckung für eine erforderliche Locale zu beanspruchen.

Ein System kann eine Warnung oder einen Fehlschlag erhalten, wenn Fallback-Verhalten übermäßig, verwirrend, undokumentiert ist oder dazu führt, dass wesentliche Inhalte in einer erforderlichen Locale unübersetzt erscheinen.

<a id="locale-equivalence"></a>
### Locale-Äquivalenz

Locale-Äquivalenz liegt vor, wenn eine Übersetzung vernünftigerweise mehr als eine Locale bedienen kann, ohne wesentliches Verständnis oder Bedienung zu verhindern.

Beispielsweise kann ein System eine englische Übersetzung für `en-US`, `en-GB` und `en-IN` verwenden, wenn die wesentliche Bedeutung für Benutzer jeder Locale klar bleibt.

Locale-Äquivalenz kann während der Überprüfung akzeptiert werden, wenn regionale Unterschiede gering sind und die wesentliche Benutzbarkeit nicht wesentlich beeinträchtigen.

Locale-Äquivalenz darf nicht verwendet werden, wenn eine fehlende Locale erhebliche Verwirrung verursachen, wichtige regionale Terminologie auslassen, wesentliches Verhalten beschädigen oder Benutzer am Verständnis des Systems hindern würde.

Beispielsweise sollte ein System nicht annehmen, dass nicht verwandte Sprachen äquivalent sind, weil sie eine Schreibrichtung, eine geografische Region, eine Schriftfamilie oder eine breite kulturelle Kategorie teilen.

Locale-Äquivalenz ist eine Prüfentscheidung, keine automatische Regel.

<a id="implementation-requirements"></a>
## Implementierungsanforderungen

<a id="stable-translation-mechanism"></a>
### Stabiler Übersetzungsmechanismus

Ein konformes System muss einen stabilen Übersetzungsmechanismus verwenden, der für das geprüfte System geeignet ist.

Ein stabiler Übersetzungsmechanismus sollte es ermöglichen, übersetzte Inhalte zu pflegen, zu aktualisieren, zu überprüfen und zu erweitern, ohne sich auf fragile oder undokumentierte Verhaltensweisen zu verlassen.

Ein stabiler Übersetzungsmechanismus kann Folgendes umfassen:

* Ressourcendateien
* Übersetzungstabellen
* localebewusstes Routing
* kompilierte Sprachressourcen
* statische lokalisierte Seiten
* Laufzeit-Sprachpakete
* datenbankgestützte Übersetzungen
* eine andere dokumentierte Übersetzungsstruktur

Ein System sollte vermeiden, wesentliche benutzerseitige Inhalte so fest zu codieren, dass erforderliche Übersetzungsunterstützung verhindert wird.

<a id="preservation-of-meaning"></a>
### Bewahrung der Bedeutung

Eine Übersetzung bewahrt Bedeutung, wenn der Benutzer vernünftigerweise dieselbe wesentliche Anweisung, Beschriftung, Warnung, dasselbe Steuerelement, dieselbe Einstellung oder denselben Arbeitsablauf verstehen kann wie Benutzer der Ausgangssprache.

Eine Übersetzung muss nicht wortwörtlich mit dem Ausgangsinhalt identisch sein.

Eine Übersetzung kann Wortreihenfolge, Grammatik, Satzstruktur, Idiom, Ton oder Formulierung ändern, wenn dies notwendig ist, um dieselbe wesentliche Bedeutung in der Zielsprache zu kommunizieren.

Eine Übersetzung kann die Überprüfung nicht bestehen, wenn sie irreführend, unvollständig, unsinnig, maschinell beschädigt oder in einer Weise wesentlich vom Ausgangsinhalt verschieden ist, die die wesentliche Nutzung beeinflusst.

<a id="direction-sensitive-languages"></a>
### Richtungssensitive Sprachen

Einige erforderliche Locales verwenden häufig Schreibrichtung von rechts nach links.

Ein konformes System darf nicht verhindern, dass wesentliche übersetzte Inhalte gelesen, verstanden, ausgewählt oder als Grundlage für Handlungen verwendet werden, nur weil die aktive Locale eine andere Textrichtung verwendet.

Das System sollte lesbare Reihenfolge, Zeichensetzungsverhalten und Zuordnung von Steuerelementen für richtungssensitive Sprachen bewahren.

Vollständige visuelle Verfeinerung, Typografiequalität, Barrierefreiheitsverhalten und Layoutverfeinerung können eine separate Überprüfung erfordern. Wesentliche übersetzte Inhalte müssen jedoch sinnvoll benutzbar bleiben.

<a id="locale-sensitive-values"></a>
### Locale-sensitive Werte

Locale-sensitive Werte sind Werte, deren Bedeutung oder Lesbarkeit je nach Sprache, Region, Schrift oder Kultur variieren kann.

Locale-sensitive Werte können Folgendes umfassen:

* Daten
* Uhrzeiten
* Zahlen
* Währungen
* Maßeinheiten
* Pluralformen
* grammatisches Geschlecht
* Sortierreihenfolge
* Adressformate
* Telefonnummernformate

I18NSPEC verlangt keine vollständige Lokalisierung jedes locale-sensitiven Wertes, sofern dieser Wert nicht wesentlich für das Verständnis oder die Bedienung des Systems ist.

Wenn locale-sensitive Werte wesentlich sind, sollte das System sie so darstellen, dass Benutzer der aktiven Locale sie vernünftigerweise verstehen können.

<a id="verification"></a>
## Verifizierung

<a id="within-spec"></a>
### Within Spec

Ein System gilt als within spec, wenn das CatalystUI-Team das System überprüft und es für vernünftig befunden hat, daraus zu schließen, dass es I18NSPEC erfüllt.

Ein System kann within spec sein, wenn:

* jede erforderliche Locale unterstützt wird
* mehr als 75 % der wesentlichen benutzerseitigen Inhalte für jede erforderliche Locale übersetzt sind
* alle kritischen benutzerseitigen Inhalte für jede erforderliche Locale übersetzt sind
* Benutzer die aktive Locale vernünftig auswählen können
* Fallback-Verhalten nicht fälschlich Übersetzungsabdeckung beansprucht
* Locale-Äquivalenz, falls verwendet, vernünftig und dokumentiert ist
* übersetzte Inhalte wesentliche Bedeutung bewahren

Ein System kann within spec sein, auch wenn einige unwesentliche Inhalte unübersetzt bleiben.

Ein System kann within spec sein, auch wenn Übersetzungen nicht perfekt sind, sofern die wesentliche Bedeutung bewahrt wird und die Anforderungen dieser Spezifikation erfüllt sind.

<a id="warnings"></a>
### Warnungen

Eine Warnung kann ausgesprochen werden, wenn ein System I18NSPEC offenbar erfüllt, aber Bedenken enthält, die dokumentiert werden sollten.

Warnungen können Folgendes umfassen:

* geringfügige unübersetzte unwesentliche Inhalte
* inkonsistente Terminologie über Locales hinweg
* unvollkommene, aber verständliche Übersetzungen
* akzeptable Locale-Äquivalenz, die dokumentiert werden sollte
* begrenztes Fallback-Verhalten
* teilweise übersetzte optionale Seiten
* richtungssensitive Layoutbedenken, die wesentliche Nutzung nicht verhindern
* locale-sensitive Werte, die verständlich, aber nicht ideal sind

Warnungen verhindern die Verifizierung nicht zwangsläufig.

<a id="failures"></a>
### Fehlschläge

Ein Fehlschlag tritt ein, wenn ein System eine oder mehrere erforderliche Bedingungen von I18NSPEC nicht erfüllt.

Fehlschläge können Folgendes umfassen:

* fehlende Unterstützung für eine erforderliche Locale
* wesentliche Übersetzungsabdeckung bei oder unter 75 % für eine erforderliche Locale
* unübersetzte kritische benutzerseitige Inhalte
* kein vernünftiger Mechanismus zur Sprachauswahl
* Sprachauswahl, die Quellcodeänderungen erfordert
* Sprachauswahl, die Entwicklertools erfordert
* defektes Laden von Übersetzungen
* irreführende Locale-Behauptungen
* übermäßiges Fallback-Verhalten
* Fallback-Inhalte, die ohne gültige Locale-Äquivalenz als übersetzte Inhalte gezählt werden
* richtungssensitive Inhalte, die unlesbar oder unbenutzbar sind
* wesentliche Arbeitsabläufe, die in einer oder mehreren erforderlichen Locales nicht verfügbar sind

Fehlschläge verhindern die Verifizierung, bis sie behoben sind.

<a id="verification-validity"></a>
### Gültigkeit der Verifizierung

I18NSPEC-Verifizierung gilt nur für den geprüften Zustand des Systems zum Zeitpunkt der Ausstellung der Verifizierung.

Ein System kann die Verifizierung über spätere Aktualisierungen hinweg behalten, solange es die verifizierte Internationalisierungsgrundlage bewahrt.

Kleinere Wortlautänderungen, hinzugefügte Übersetzungen, verbesserte Übersetzungen und gewöhnliche Inhaltsaktualisierungen machen die Verifizierung nicht automatisch ungültig.

Eine neue Überprüfung kann erforderlich sein, wenn ein System:

* erforderliche Locale-Unterstützung entfernt
* die Sprachauswahl beschädigt
* wesentliche Übersetzungsabdeckung erheblich reduziert
* neue wesentliche Arbeitsabläufe unübersetzt lässt
* übersetzte Inhalte durch Fallback-Inhalte ersetzt
* seine Übersetzungsarchitektur so ändert, dass das verifizierte Verhalten betroffen ist
* größere benutzerseitige Änderungen einführt, die den geprüften Umfang verändern

Anders gesagt: Die Verbesserung der Übersetzungsunterstützung ist normalerweise in Ordnung.

Das Brechen der verifizierten mehrsprachigen Grundlage kann eine Überprüfung erforderlich machen.
