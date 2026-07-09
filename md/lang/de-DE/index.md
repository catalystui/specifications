<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->

<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Willkommen in der CatalystUI-Verifizierungsdokumentation für Barrierefreiheit.

**CatalystUI Verified for Accessibility** bedeutet, dass ein Dienst, Framework, eine Anwendung, Bibliothek oder ein System vom CatalystUI Team geprüft wurde und dabei als weiterhin angemessen nutzbar befunden wurde, wenn einer der drei primären Sinne, die an der Interaktion mit Benutzeroberflächen beteiligt sind, einzeln nicht verfügbar ist.

Für diese Verifizierung identifiziert CatalystUI die drei primären Sinne der Barrierefreiheit als **Sehen**, **Hören** und **Berühren**. Ein verifiziertes System muss angemessenen Zugriff auf seine wesentliche Funktionalität erhalten, wenn einer dieser Sinne nicht verfügbar ist, indem es sich auf die verbleibenden verfügbaren Sinnesdomänen stützt.

Einfacher gesagt fragt diese Verifizierung, ob ein Benutzer die wesentlichen Teile eines Systems weiterhin sinnvoll verstehen, navigieren und bedienen kann, wenn er sich einzeln nicht auf Sehen, Hören oder Berühren verlassen kann.

## Zweck

Barrierefreiheit ist wichtig, weil eine Benutzeroberfläche nicht vollständig von einem einzigen Sinnesweg abhängen sollte, wenn dieselbe wesentliche Bedeutung angemessen über einen anderen vermittelt werden kann.

CatalystUI ist um die getreue Bewegung von Daten zwischen Systemen und menschlicher Wahrnehmung herum entworfen. Wenn wichtige Informationen nur sichtbar, nur hörbar oder nur durch Berührung verfügbar sind, kann das System für Benutzer unbenutzbar werden, die sich auf diesen Sinn nicht verlassen können. Die Barrierefreiheitsverifizierung existiert, um Systeme zu identifizieren, die Zugang bewahren, indem sie wesentliche Informationen und Interaktionen über alternative Sinneswege fortführen.

Das Ziel ist nicht, jede mögliche Interaktionsmethode, jede unterstützende Technologie oder jede spezialisierte Anpassung zu verlangen. Das Ziel ist festzustellen, ob das wesentliche System sinnvoll nutzbar bleibt, wenn Sehen, Hören oder Berühren jeweils einzeln nicht verfügbar ist.

## Was Verifizierung bedeutet

Ein System wird **CatalystUI Verified for Accessibility**, wenn es gegen die in diesem Abschnitt aufgeführten Anforderungen geprüft und als innerhalb der Spezifikation befunden wird.

Um verifiziert zu werden, muss ein System in jedem der folgenden Fälle angemessen nutzbar bleiben:

| Nicht verfügbarer Sinn | Erforderliches Barrierefreiheitsverhalten |
| ----------------- | ----------------------------------------------------------------- |
| Sehen             | Das System muss über Hören und Berühren angemessen nutzbar bleiben. |
| Hören             | Das System muss über Sehen und Berühren angemessen nutzbar bleiben. |
| Berühren          | Das System muss über Sehen und Hören angemessen nutzbar bleiben. |

Ein System muss nicht über jeden Sinnesweg identische Erfahrungen bereitstellen. Eine nicht-visuelle Erfahrung kann langsamer sein als eine visuelle. Eine tonfreie Erfahrung kann Untertitel, visuelle Hinweise oder andere Ersetzungen erfordern. Eine berührungsfreie Erfahrung kann alternative Steuerelemente, Sprachinteraktion, Tastaturnavigation, Zeigernavigation oder andere berührungsfreie Methoden erfordern.

Entscheidend ist, ob die wesentliche Funktionalität zugänglich, verständlich und bedienbar bleibt, ohne den nicht verfügbaren Sinn zu erfordern.

## Wesentliche Funktionalität

Für die Barrierefreiheitsverifizierung bezeichnet **wesentliche Funktionalität** die Teile eines Systems, die ein Benutzer angemessenerweise benötigt, um das System zu verstehen, zu navigieren, zu konfigurieren und zu bedienen.

Wesentliche Funktionalität kann umfassen:

* primäre Navigation
* Kernabläufe
* erforderliche Steuerelemente
* wichtige Warnungen
* wichtige Fehler
* erforderliche Bestätigungsnachrichten
* Konto- oder Sitzungszugriff
* Einstellungen und Präferenzen
* Sprach- oder Barrierefreiheitskonfiguration
* wesentliche Anweisungen
* benutzerseitige Statusinformationen
* jede Interaktion, die für die normale Nutzung erforderlich ist

Ein System kann weiterhin innerhalb der Spezifikation liegen, wenn dekorative, redundante, optionale oder nicht wesentliche Funktionen nicht über jeden Sinnesweg gleich verfügbar sind. Der Benutzer muss das wesentliche System jedoch weiterhin verwenden können, ohne durch den fehlenden Sinn blockiert zu werden.

## Sehen nicht verfügbar

Wenn Sehen nicht verfügbar ist, sollte das System über Hören und Berühren angemessen nutzbar bleiben.

Dies kann gesprochene Ausgabe, screenreader-kompatible Struktur, sinnvolle Fokusreihenfolge, taktile Steuerelemente, Tastaturzugriff, haptische Bestätigung, Audiobeschreibungen oder eine andere angemessene nicht-visuelle Methode zur Vermittlung wesentlicher Informationen umfassen.

Ein System sollte sich nicht ausschließlich auf visuelle Position, Farbe, Form, Animation, Symbole oder Layout verlassen, wenn diese Informationen erforderlich sind, um wesentliche Funktionalität zu verstehen oder zu bedienen.

## Hören nicht verfügbar

Wenn Hören nicht verfügbar ist, sollte das System über Sehen und Berühren angemessen nutzbar bleiben.

Dies kann Untertitel, Transkripte, visuelle Alarme, Textäquivalente, Fortschrittsanzeigen, sichtbare Statusmeldungen, haptisches Feedback oder eine andere angemessene nicht-auditive Methode zur Vermittlung wesentlicher Informationen umfassen.

Ein System sollte sich nicht ausschließlich auf Soundeffekte, gesprochene Anweisungen, Warnhinweise, Alarme, musikalische Hinweise oder reine Audioaufforderungen verlassen, wenn diese Informationen erforderlich sind, um wesentliche Funktionalität zu verstehen oder zu bedienen.

## Berühren nicht verfügbar

Wenn Berühren nicht verfügbar ist, sollte das System über Sehen und Hören angemessen nutzbar bleiben.

Dies kann Sprachsteuerung, Tastaturnavigation, Zeigeralternativen, Fernbedienungen, blickkompatible Interaktion, schalterkompatible Interaktion, gesprochene Aufforderungen, visuelle Bestätigung oder eine andere angemessene Methode umfassen, die keine berührungsbasierte Interaktion oder taktile Wahrnehmung erfordert.

Ein System sollte sich nicht ausschließlich auf Berührungsgesten, haptisches Feedback, physische Textur, Vibration, Kraft, Druck oder reine Touch-Steuerelemente verlassen, wenn diese Interaktionen erforderlich sind, um wesentliche Funktionalität zu verstehen oder zu bedienen.

## Zusätzliche Sinnesdomänen

CatalystUI erkennt auch **Geschmack** und **Geruch** als Sinnesdomänen an. Diese Domänen können während einer Barrierefreiheitsprüfung berücksichtigt werden, wenn sie vom System sinnvoll verwendet werden.

Geschmack und Geruch sind für die Verifizierung **inklusiv**, das heißt, sie können eine Barrierefreiheitsprüfung stärken oder unterstützen, wenn sie sinnvollen alternativen Zugang oder zusätzlichen Kontext bereitstellen.

Geschmack und Geruch sind derzeit nicht **exklusiv** für Fehler, das heißt, ein System scheitert nicht an der Barrierefreiheitsverifizierung, nur weil es keine geschmacks- oder geruchsbasierten Interaktionen bereitstellt.

Die CatalystUI-Barrierefreiheitsverifizierung befasst sich primär damit, ob das System angemessen nutzbar bleibt, wenn Sehen, Hören oder Berühren einzeln nicht verfügbar ist.

## Was „innerhalb der Spezifikation“ bedeutet

Wenn ein System als **innerhalb der Spezifikation** gilt, bedeutet das, dass das CatalystUI Team das System manuell geprüft und es als angemessen befunden hat, daraus zu schließen, dass es die in dieser Verifizierungskategorie beschriebenen Barrierefreiheitsanforderungen erfüllt.

Dies erfordert kein starres Implementierungsmuster. Ein System kann Barrierefreiheitsanforderungen über native Barrierefreiheits-APIs der Plattform, semantische Struktur, alternative Eingabemethoden, alternative Ausgabemethoden, Unterstützung für assistive Technologien, integrierte Barrierefreiheitseinstellungen, geräteweite Integration oder einen anderen stabilen, für das System geeigneten Mechanismus erfüllen.

Die Verifizierung betrifft die praktische Fähigkeit von Benutzern, auf das wesentliche System zuzugreifen, wenn ein primärer Sinn nicht verfügbar ist, nicht die Frage, ob das System eine bestimmte Barrierefreiheitsarchitektur verwendet.

## Was Verifizierung nicht bedeutet

CatalystUI Verified for Accessibility garantiert nicht, dass jede mögliche Behinderung, jedes Gerät, jede assistive Technologie, jeder medizinische Zustand, jede gesetzliche Anforderung, jeder regionale Standard oder jeder spezialisierte Anwendungsfall vollständig geprüft wurde.

Es verifiziert auch nicht automatisch Internationalisierung, Übersetzungsqualität, Typografie, Lokalisierung, regionale Konformität oder allgemeine Designqualität, sofern diese Anliegen nicht im geprüften Barrierefreiheitsumfang enthalten sind.

Ein System kann unter dem Barrierefreiheitsmodell von CatalystUI angemessen barrierefrei sein und dennoch eine separate Prüfung für rechtliche Konformität, Plattformzertifizierung, spezialisierte Unterstützung assistiver Technologien oder andere Barrierefreiheitsstandards benötigen.

## Warum diese Verifizierung existiert

Eine Benutzeroberfläche ist nur erfolgreich, wenn Benutzer sie tatsächlich verwenden können.

Viele Systeme behandeln Barrierefreiheit als nachträglichen Gedanken, Checkliste oder enges technisches Erfordernis statt als grundlegenden Bestandteil der Mensch-Computer-Interaktion. CatalystUI verfolgt einen einfacheren und direkteren Ansatz: Wenn ein System von menschlicher Wahrnehmung abhängt, sollte es wesentliche Bedeutung bewahren, wenn ein primärer Sinnesweg nicht verfügbar ist.

Die Barrierefreiheitsverifizierung existiert, um Systeme zu identifizieren, die diese Verantwortung ernst nehmen. Sie erkennt Systeme an, die sinnvollen alternativen Zugang bereitstellen, wesentliche Funktionalität bewahren und vermeiden, Benutzer hinter einem einzigen erforderlichen Sinn einzusperren.

## Verifizierungsumfang

Die CatalystUI-Verifizierung für Barrierefreiheit gilt für das geprüfte System, den Dienst, das Framework, die Anwendung, die Bibliothek oder die Implementierung, wie sie zum Zeitpunkt der Ausstellung der Verifizierung bestand.

Ein verifiziertes System stellt angemessene Barrierefreiheit für seine wesentliche Funktionalität unter den geprüften Bedingungen bereit. Es garantiert nicht, dass jede zukünftige Seite, Funktion, Veröffentlichung, jedes Plugin, jede Erweiterung, jede Drittanbieterintegration, jedes Gerät oder jede plattformspezifische Version automatisch innerhalb der Spezifikation liegt.

Separate Produkte, Module, Dienste, größere Revisionen oder plattformspezifische Builds können je nach angeforderter Verifizierungskategorie eine eigene Prüfung erfordern.

## Gültigkeit der Verifizierung

CatalystUI-Verifizierung gilt nur für den geprüften Zustand des Systems zum Zeitpunkt der Ausstellung der Verifizierung.

Ein System kann seine Verifizierung über spätere Updates hinweg behalten, solange es die verifizierte Barrierefreiheitsgrundlage bewahrt. Geringfügige Formulierungsänderungen, visuelle Verfeinerungen, Leistungsverbesserungen und gewöhnliche Inhaltsupdates machen die Verifizierung nicht automatisch ungültig.

Eine neue Prüfung kann erforderlich sein, wenn ein System alternative Zugangswege entfernt, Unterstützung für assistive Technologien bricht, wesentliche Navigation erheblich verändert, erforderliche Barrierefreiheitseinstellungen entfernt oder Interaktionsverhalten so ändert, dass die verifizierte Barrierefreiheitsgrundlage betroffen ist.

Anders gesagt: Barrierefreiheit zu verbessern ist normalerweise in Ordnung. Das verifizierte Zugangsmodell zu brechen, kann eine Prüfung erfordern.

## Verifizierte Systeme

Bekannte Systeme, die für Barrierefreiheit verifiziert wurden, sind separat auf der entsprechenden CatalystUI-Verified-Seite aufgeführt.
