<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->

<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified for Internationalization

Willkommen in der CatalystUI-Verifizierungsdokumentation für Internationalisierung.

**CatalystUI Verified for Internationalization** zeigt an, dass ein System, ein Dienst, ein Framework, eine Anwendung oder eine Implementierung vom CatalystUI-Team überprüft wurde und als ausreichend mehrsprachig für den erforderlichen CatalystUI-Sprachsatz zur Internationalisierung gilt.

Diese Verifizierung ist keine allgemeine Bewertung der Übersetzungsqualität, des Schreibstils, der Lokalisierungstiefe oder der kulturellen Anpassung. Stattdessen zeigt sie an, ob das geprüfte System eine stabile und praktische Grundlage bietet, damit Benutzer in den erforderlichen unterstützten Sprachen auf seine wesentlichen Funktionen zugreifen können.

Einfacher gesagt fragt diese Verifizierung, ob Benutzer die wesentlichen Teile eines Systems in den erforderlichen Sprachen sinnvoll verwenden können und ob ihnen eine vernünftige Möglichkeit gegeben wird, die Sprache auszuwählen, die sie verstehen.

<a id="purpose"></a>
## Zweck

Internationalisierung ist wichtig, weil ein System nicht als breit zugänglich gelten kann, wenn seine wesentliche Bedeutung hinter einer einzigen Sprache eingeschlossen ist.

CatalystUI ist auf Klarheit, Konsistenz und die getreue Darstellung der Mensch-Computer-Interaktion ausgelegt. Sprache ist Teil dieser Interaktion. Wenn ein Benutzer die Beschriftungen, Anweisungen, Warnungen, Steuerelemente, Einstellungen oder wesentlichen Inhalte eines Systems nicht verstehen kann, hat das System nicht klar kommuniziert, selbst wenn die zugrunde liegende Funktionalität technisch funktioniert.

Die Internationalisierungsverifizierung existiert, um Systeme zu identifizieren, die genügend übersetzte Unterstützung für Benutzer im gesamten erforderlichen CatalystUI-Sprachsatz bereitstellen. Das Ziel besteht nicht darin, eine perfekte Übersetzung jedes optionalen Wortes, jeder versteckten Entwicklermeldung oder jeder unwesentlichen Seite zu verlangen. Das Ziel besteht darin zu bestimmen, ob die wesentlichen Teile des Systems von Menschen in jeder erforderlichen Sprache verstanden und verwendet werden können.

<a id="what-verification-means"></a>
## Was Verifizierung bedeutet

Ein System wird **CatalystUI Verified for Internationalization**, wenn es anhand der in diesem Abschnitt aufgeführten Anforderungen überprüft und als innerhalb der Spezifikation befunden wird.

Um verifiziert zu werden, muss ein System Übersetzungen für mehr als 75 % der wesentlichen benutzerseitigen Teile des Systems in jeder erforderlichen Sprache bereitstellen. Außerdem muss es einen vernünftigen Mechanismus für Endbenutzer bereitstellen, um die aktive Sprache zu ändern.

Ein System muss nicht jeden internen Bezeichner, jedes entwicklerseitige Implementierungsdetail, jede Debug-Zeichenkette, jede optionale Marketingseite oder jeden unwesentlichen Supporttext übersetzen. Die benutzerseitigen Bereiche, die erforderlich sind, um das wesentliche System zu verstehen und zu bedienen, müssen jedoch in jeder erforderlichen Sprache verfügbar sein.

<a id="required-languages"></a>
## Erforderliche Sprachen

Der aktuelle CatalystUI-Sprachsatz zur Internationalisierung wurde aus einer praktischen Betrachtung von Sprachen ausgewählt, die in Technologiekontexten häufig benötigt werden, einschließlich globaler Sprecherreichweite, verbreiteter Online-Nutzung, mehrsprachiger Softwareerwartungen und breiter regionaler Zugänglichkeitsanforderungen.

Dieser Sprachsatz soll nicht jede Sprache, jeden Dialekt oder jede regionale Variante darstellen. Stattdessen legt er eine praktische Grundlage für Systeme fest, die eine breite internationale Benutzbarkeit über viele der weltweit häufigsten technologiebezogenen Sprachgruppen hinweg anstreben.

Der aktuelle CatalystUI-Sprachsatz zur Internationalisierung enthält die folgenden Locales:

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

Ein System muss für jede aufgeführte Sprachgruppe ausreichende wesentliche Übersetzungsabdeckung bereitstellen, um als innerhalb der Spezifikation zu gelten.

Regionale Varianten können jedoch mit angemessener Flexibilität überprüft werden, wenn die Unterschiede zwischen den Varianten gering sind und die Fähigkeit des Benutzers, das System zu verstehen oder zu bedienen, nicht wesentlich beeinträchtigen. Beispielsweise kann ein System weiterhin für eine Verifizierung infrage kommen, wenn es eine starke englische Übersetzung bereitstellt, aber nicht jede regionale englische Variante separat übersetzt, solange wesentliche Bedeutung, Navigation, Anweisungen, Warnungen und Steuerelemente für Benutzer der fehlenden Varianten klar bleiben.

Diese Flexibilität gilt nicht, wenn eine fehlende Variante erhebliche Verwirrung verursachen, regional wichtige Terminologie auslassen, localeabhängiges Verhalten beschädigen oder Benutzer daran hindern würde, wesentliche Teile des Systems zu verstehen.

<a id="essential-translation-coverage"></a>
## Wesentliche Übersetzungsabdeckung

Für die Internationalisierungsverifizierung bezeichnet **wesentliche Übersetzungsabdeckung** die Teile eines Systems, die ein Benutzer vernünftigerweise benötigt, um das System zu verstehen, zu navigieren, zu konfigurieren und zu bedienen.

Wesentliche Teile können Folgendes umfassen:

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

Ein System gilt als erfüllend für die Anforderung an die Übersetzungsabdeckung, wenn mehr als 75 % seiner wesentlichen benutzerseitigen Inhalte in jeder erforderlichen Sprache verfügbar sind.

Dieser Schwellenwert existiert, weil Internationalisierungsarbeit umfangreich, fortlaufend und kontextabhängig sein kann. Ein System kann weiterhin innerhalb der Spezifikation liegen, auch wenn einige unwesentliche oder nachrangige Inhalte unübersetzt bleiben. Die wesentliche Erfahrung muss jedoch in jeder erforderlichen Sprache sinnvoll verfügbar sein.

<a id="language-selection"></a>
## Sprachauswahl

Ein verifiziertes System muss eine vernünftige Möglichkeit für den Endbenutzer bereitstellen, die aktive Sprache zu ändern.

Der Sprachauswahlmechanismus sollte leicht zu finden, verständlich und ohne technisches Wissen verfügbar sein. Benutzer sollten keine Konfigurationsdateien bearbeiten, Quellcode ändern, Entwicklertools installieren oder sich auf undokumentiertes Verhalten verlassen müssen, nur um die Sprache zu ändern.

Beim Anzeigen von Sprachoptionen sollte das System jede Sprache so kennzeichnen, dass sie sowohl für Benutzer verständlich ist, die diese Sprache sprechen, als auch für Benutzer, die derzeit eine andere ausgewählte Sprache verwenden.

Beispielsweise kann eine Sprachoption so angezeigt werden:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Das genaue Format kann variieren, aber die Absicht sollte dieselbe bleiben: Benutzer sollten ihre eigene Sprache erkennen, den aktuell angezeigten Sprachnamen nach Möglichkeit verstehen und den zugehörigen Locale-Code erkennen können.

<a id="what-within-spec-means"></a>
## Was „Within Spec“ bedeutet

Wenn ein System als **within spec** betrachtet wird, bedeutet dies, dass das CatalystUI-Team das System manuell überprüft und es für vernünftig befunden hat, daraus zu schließen, dass es die durch diese Verifizierungskategorie beschriebenen Internationalisierungsanforderungen erfüllt.

Dies erfordert kein starres Implementierungsmuster. Ein System kann die Anforderung durch Ressourcendateien, Übersetzungstabellen, localebewusstes Routing, kompilierte Sprachressourcen, datenbankgestützte Übersetzungen, Laufzeit-Sprachpakete oder einen anderen stabilen, für das System geeigneten Mechanismus erfüllen.

Bei der Verifizierung geht es um die praktische Fähigkeit der Benutzer, auf das wesentliche System in den erforderlichen Sprachen zuzugreifen, nicht darum, ob das System eine bestimmte Übersetzungsarchitektur verwendet.

<a id="what-verification-does-not-mean"></a>
## Was Verifizierung nicht bedeutet

CatalystUI Verified for Internationalization garantiert nicht, dass jede Übersetzung perfekt, literarisch, idiomatisch, kulturell vollständig oder rechtlich ausreichend für jede Region ist.

Es verifiziert auch nicht automatisch Barrierefreiheit, Typografie, Rechts-nach-links-Layout, localeabhängige Formatierung, Währungsformatierung, Datumsformatierung, Rechtskonformität oder regionale Geschäftsanforderungen, sofern diese Belange nicht im überprüften Internationalisierungsumfang enthalten sind.

Ein System kann eine starke Übersetzungsabdeckung bieten und dennoch eine separate Überprüfung für Barrierefreiheit, Lokalisierungsqualität, regionale Konformität oder andere spezialisierte Belange erfordern.

<a id="why-this-verification-exists"></a>
## Warum diese Verifizierung existiert

Eine Benutzeroberfläche ist nur dann nützlich, wenn der Benutzer verstehen kann, was sie kommuniziert.

Viele Systeme behaupten Sprachunterstützung, übersetzen aber nur einen kleinen Teil der Erfahrung, verstecken die Sprachauswahl, lassen wichtige Meldungen aus oder lassen wesentliche Arbeitsabläufe teilweise unübersetzt. Das schafft Verwirrung und hindert Benutzer daran, dem System zu vertrauen.

Die Internationalisierungsverifizierung existiert, um einen klareren Standard zu setzen. Sie identifiziert Systeme, die ernsthafte, praktische Anstrengungen unternehmen, um Benutzer im gesamten erforderlichen CatalystUI-Sprachsatz zu unterstützen, und die eine vernünftige Möglichkeit bieten, die benötigte Sprache auszuwählen.

<a id="verification-scope"></a>
## Verifizierungsumfang

CatalystUI Verification for Internationalization gilt für das geprüfte System, den Dienst, das Framework, die Anwendung oder die Implementierung in dem Zustand, in dem sie zum Zeitpunkt der Ausstellung der Verifizierung existierte.

Ein verifiziertes System bietet ausreichende wesentliche Übersetzungsabdeckung für die erforderlichen Sprachen. Es garantiert nicht, dass jede zukünftige Seite, Funktion, Veröffentlichung, jedes Plugin, jede Erweiterung oder jede Drittanbieterintegration automatisch innerhalb der Spezifikation liegt.

Separate Produkte, Module, Dienste, Sprachpakete oder größere Revisionen können je nach angeforderter Verifizierungskategorie eine eigene Überprüfung erfordern.

<a id="verification-validity"></a>
## Gültigkeit der Verifizierung

CatalystUI-Verifizierung gilt nur für den geprüften Zustand des Systems zum Zeitpunkt der Ausstellung der Verifizierung.

Ein System kann seine Verifizierung über spätere Aktualisierungen hinweg behalten, solange es die verifizierte Internationalisierungsgrundlage bewahrt. Kleinere Wortlautänderungen, hinzugefügte Übersetzungen und gewöhnliche Inhaltsaktualisierungen machen die Verifizierung nicht automatisch ungültig.

Eine neue Überprüfung kann erforderlich sein, wenn ein System erforderliche Sprachunterstützung entfernt, die Sprachauswahl beschädigt, die wesentliche Übersetzungsabdeckung erheblich reduziert oder seine Internationalisierungsarchitektur so ändert, dass das verifizierte Verhalten betroffen ist.

Anders gesagt: Die Verbesserung der Übersetzungsunterstützung ist normalerweise in Ordnung. Das Brechen der verifizierten mehrsprachigen Grundlage kann eine Überprüfung erforderlich machen.

<a id="verified-systems"></a>
## Verifizierte Systeme

Bekannte für Internationalisierung verifizierte Systeme sind separat auf der entsprechenden CatalystUI-Verified-Seite aufgeführt.
