<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->

<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

# A11YSPEC

<br/>

> **Barrierefreiheitsspezifikation**<br/>
> Revision 1<br/>
> 8. Juli 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Alle Rechte vorbehalten.<br/> <br/>
> Die hier vorgestellten Definitionen, Anforderungen und Konzepte beschreiben praktische Unterstützung für Barrierefreiheit und dürfen frei neu ausgedrückt werden.

<a id="introduction"></a>

## Einführung

Die **Barrierefreiheitsspezifikation (A11YSPEC)** legt die zentralen Konzepte, Begriffe und Anforderungen fest, die zur Bewertung von Barrierefreiheitsunterstützung im CatalystUI-Ökosystem verwendet werden. Ihr Zweck ist es, einen klaren Standard dafür bereitzustellen, ob ein System, Dienst, Framework, eine Anwendung, Bibliothek oder Implementierung sinnvoll nutzbar bleibt, wenn ein primärer Sinnesweg nicht verfügbar ist.

Barrierefreiheit ist wichtig, weil eine Benutzeroberfläche nicht vollständig von einem Sinn abhängen sollte, wenn dieselbe wesentliche Bedeutung angemessen durch einen anderen vermittelt werden kann. Ein System kann technisch funktionsfähig sein; wenn ein Benutzer sein wesentliches Verhalten jedoch nicht ohne Sehen, Hören oder Berühren jeweils einzeln verstehen, navigieren, konfigurieren oder bedienen kann, hat das System für diese Bedingung keinen angemessenen Zugang bereitgestellt.

Diese Spezifikation versucht nicht, jede mögliche Behinderung, jedes Gerät, jede assistive Technologie, jeden medizinischen Zustand, jede gesetzliche Anforderung, jeden regionalen Barrierefreiheitsstandard oder jeden spezialisierten Anwendungsfall zu verifizieren. Stattdessen definiert sie die Mindestgrundlage an Barrierefreiheit, die erforderlich ist, damit Benutzer auf die wesentlichen Teile eines Systems sinnvoll zugreifen und sie bedienen können, wenn einer der drei primären Barrierefreiheitssinne nicht verfügbar ist.

Einfacher gesagt stellt A11YSPEC drei Hauptfragen:

1. Können Benutzer das wesentliche System verstehen, ohne sich auf Sehen zu verlassen?
2. Können Benutzer das wesentliche System verstehen, ohne sich auf Hören zu verlassen?
3. Können Benutzer das wesentliche System bedienen, ohne sich auf Berühren zu verlassen?

> [!IMPORTANT]
>
> A11YSPEC definiert Barrierefreiheitsanforderungen für die Verifizierung. Sie ist kein Ersatz für gesetzliche Barrierefreiheitsstandards, Plattformzertifizierungsanforderungen oder spezialisierte Prüfungen assistiver Technologien. Ein System kann innerhalb von A11YSPEC liegen und dennoch zusätzliche Prüfung für andere Barrierefreiheitsstandards benötigen.

<a id="table-of-contents"></a>

## Inhaltsverzeichnis

- [A11YSPEC](#a11yspec)
  - [Einführung](#introduction)
  - [Inhaltsverzeichnis](#table-of-contents)
  - [Konformität](#conformance)
  - [Primäre Barrierefreiheitssinne](#primary-accessibility-senses)
    - [Sehen](#sight)
    - [Hören](#sound)
    - [Berühren](#touch)
    - [Zusätzliche Sinnesdomänen](#additional-sensory-domains)
  - [Erforderliche Barrierefreiheitsfälle](#required-accessibility-cases)
  - [Wesentliche Funktionalität](#essential-functionality)
    - [Wesentliche Funktionalität](#essential-functionality-1)
    - [Kritische Funktionalität](#critical-functionality)
    - [Nicht wesentliche Funktionalität](#nonessential-functionality)
  - [Barrierefreiheitsanforderungen](#accessibility-requirements)
    - [Anforderung an wesentlichen Zugang](#essential-access-requirement)
    - [Anforderung an kritischen Zugang](#critical-access-requirement)
    - [Anforderung an alternativen Zugang](#alternate-access-requirement)
    - [Keine Abhängigkeit von einem einzigen Sinn](#no-single-sense-dependency)
  - [Sehen nicht verfügbar](#sight-unavailable)
  - [Hören nicht verfügbar](#sound-unavailable)
  - [Berühren nicht verfügbar](#touch-unavailable)
  - [Implementierungsanforderungen](#implementation-requirements)
    - [Stabiler Barrierefreiheitsmechanismus](#stable-accessibility-mechanism)
    - [Semantische Struktur](#semantic-structure)
    - [Alternative Ausgabe](#alternate-output)
    - [Alternative Eingabe](#alternate-input)
    - [Zugängliches Feedback](#accessible-feedback)
    - [Zugängliche Konfiguration](#accessible-configuration)
  - [Verifizierung](#verification)
    - [Innerhalb der Spezifikation](#within-spec)
    - [Warnungen](#warnings)
    - [Fehler](#failures)
    - [Gültigkeit der Verifizierung](#verification-validity)

<a id="conformance"></a>

## Konformität

Ein System gilt als konform mit A11YSPEC, wenn es die in diesem Dokument definierten Anforderungen für jeden erforderlichen Barrierefreiheitsfall erfüllt.

Ein konformes System muss:

1. angemessen nutzbar bleiben, wenn Sehen nicht verfügbar ist.
2. angemessen nutzbar bleiben, wenn Hören nicht verfügbar ist.
3. angemessen nutzbar bleiben, wenn Berühren nicht verfügbar ist.
4. Zugang zu wesentlicher Funktionalität in jedem erforderlichen Barrierefreiheitsfall bewahren.
5. Zugang zu aller kritischen Funktionalität in jedem erforderlichen Barrierefreiheitsfall bewahren.
6. angemessene alternative Zugangswege bereitstellen, wenn wesentliche Bedeutung oder Bedienung andernfalls vom nicht verfügbaren Sinn abhängen würde.
7. einen stabilen Barrierefreiheitsmechanismus verwenden, der für das geprüfte System geeignet ist.
8. vermeiden, sich für wesentliche Funktionalität ausschließlich auf einen primären Sinn zu verlassen.

Ein System muss nicht über jeden Sinnesweg identische Erfahrungen bereitstellen. Eine nicht-visuelle Erfahrung kann langsamer sein als eine visuelle. Eine tonfreie Erfahrung kann Untertitel, visuelle Hinweise oder haptische Bestätigung erfordern. Eine berührungsfreie Erfahrung kann Tastaturnavigation, Zeigeralternativen, Sprachinteraktion, schalterkompatible Interaktion oder eine andere alternative Methode erfordern.

Die alternative Erfahrung muss jedoch für die wesentliche und kritische Funktionalität des Systems verständlich, bedienbar und ausreichend bleiben.

<a id="primary-accessibility-senses"></a>

## Primäre Barrierefreiheitssinne

A11YSPEC erkennt drei primäre Barrierefreiheitssinne an: **Sehen**, **Hören** und **Berühren**.

<a id="sight"></a>

### Sehen

**Sehen** bezeichnet die Fähigkeit eines Benutzers, visuelle Ausgabe wahrzunehmen und zu verstehen, einschließlich Text, Bildern, Layout, Position, Farbe, Bewegung und anderen visuellen Hinweisen.

Zugang über Sehen kann umfassen:

* sichtbaren Text
* Bilder
* Symbole
* Layout
* Farbe
* Bewegung
* Fokusumrisse
* Statusanzeigen
* Untertitel
* Diagramme
* Video
* visuelle Steuerelemente

Wenn Sehen nicht verfügbar ist, darf das System für wesentliche Bedeutung oder Bedienung nicht allein auf visuelle Informationen angewiesen sein.

<a id="sound"></a>

### Hören

**Hören** bezeichnet die Fähigkeit eines Benutzers, auditive Ausgabe wahrzunehmen und zu verstehen, einschließlich Sprache, Soundeffekten, Audiohinweisen, Musik und anderen auditiven Signalen.

Zugang über Hören kann umfassen:

* Sprache
* Audiohinweise
* Soundeffekte
* musikalische Hinweise
* Screenreader
* Audiobeschreibungen
* gesprochene Anleitung
* auditives Feedback
* gesprochene Bestätigungen
* hörbare Warnungen

Wenn Hören nicht verfügbar ist, darf das System für wesentliche Bedeutung oder Bedienung nicht allein auf auditive Informationen angewiesen sein.

<a id="touch"></a>

### Berühren

**Berühren** bezeichnet die Fähigkeit eines Benutzers, berührungsbasierte Interaktion wahrzunehmen oder bereitzustellen. Dazu gehören die Nutzung von Touchscreens, physischen Tasten, Gesten, Vibration, Textur, Druck, Kraft und anderen Formen taktiler Eingabe oder Ausgabe.

Zugang über Berühren kann umfassen:

* Touchscreens
* physische Tasten
* Gesten
* Vibration
* haptisches Feedback
* Textur
* Druck
* Kraft
* Steuerschalter
* direkte Berührungseingabe
* taktile Unterscheidung

Wenn Berühren nicht verfügbar ist, darf das System für wesentliche Bedienung nicht allein auf berührungsbasierte Interaktion angewiesen sein.

<a id="additional-sensory-domains"></a>

### Zusätzliche Sinnesdomänen

CatalystUI erkennt auch **Geschmack** und **Geruch** als Sinnesdomänen an. Diese können in spezialisierten oder experimentellen Systemen relevant sein.

Für A11YSPEC sind Geschmack und Geruch **inklusiv**, nicht **exklusiv**.

Das bedeutet:

* Geschmack oder Geruch kann eine Barrierefreiheitsprüfung unterstützen, wenn er sinnvollen alternativen Zugang oder zusätzlichen Kontext bereitstellt.
* Ein System scheitert nicht an A11YSPEC, nur weil es keine geschmacksbasierte Interaktion bereitstellt.
* Ein System scheitert nicht an A11YSPEC, nur weil es keine geruchsbasierte Interaktion bereitstellt.

A11YSPEC konzentriert sich primär auf Sehen, Hören und Berühren, weil diese die häufigsten Sinneswege in praktischen Benutzeroberflächen sind.

<a id="required-accessibility-cases"></a>

## Erforderliche Barrierefreiheitsfälle

Ein konformes System muss in jedem der folgenden Barrierefreiheitsfälle angemessen nutzbar bleiben:

| Fall | Nicht verfügbarer Sinn | Erwartete verbleibende Wege |
| ---- | ----------------- | ------------------------- |
| 1 | Sehen | Hören und Berühren |
| 2 | Hören | Sehen und Berühren |
| 3 | Berühren | Sehen und Hören |

Jeder Fall muss unabhängig bewertet werden.

Ein System kann einen Fall bestehen und einen anderen nicht bestehen. Für die Verifizierung muss das System die Anforderungen in allen drei Fällen erfüllen.

<a id="essential-functionality"></a>

## Wesentliche Funktionalität

<a id="essential-functionality-1"></a>

### Wesentliche Funktionalität

**Wesentliche Funktionalität** bezeichnet die Teile eines Systems, die ein Benutzer angemessenerweise benötigt, um das System zu verstehen, zu navigieren, zu konfigurieren und zu bedienen.

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

Wesentliche Funktionalität muss in jedem erforderlichen Barrierefreiheitsfall zugänglich bleiben.

<a id="critical-functionality"></a>

### Kritische Funktionalität

**Kritische Funktionalität** bezeichnet wesentliche Funktionalität, die Sicherheit, Schutz, Datenverlust, Zahlungen, Kontozugriff, irreversible Systemänderungen oder andere Hochrisikoaktionen betrifft.

Kritische Funktionalität kann umfassen:

* Sicherheitswarnungen
* Notfallhinweise
* Authentifizierung
* Kontowiederherstellung
* Zahlungsbestätigungen
* destruktive Aktionen
* Datenlöschung
* Datenschutzeinstellungen
* Sicherheitseinstellungen
* Systemberechtigungen
* Befehle, die nicht rückgängig gemacht werden können
* Fehlermeldungen, die den Abschluss eines Ablaufs beeinflussen
* Anweisungen, die erforderlich sind, um Schaden oder Verlust zu vermeiden

Kritische Funktionalität muss in jedem erforderlichen Barrierefreiheitsfall klar zugänglich sein.

Ein Versäumnis, Zugang zu kritischer Funktionalität bereitzustellen, wird strenger geprüft als ein Versäumnis, Zugang zu nicht wesentlicher Funktionalität bereitzustellen.

<a id="nonessential-functionality"></a>

### Nicht wesentliche Funktionalität

**Nicht wesentliche Funktionalität** bezeichnet Teile eines Systems, die ein Benutzer nicht angemessenerweise benötigt, um das wesentliche System zu verstehen, zu navigieren, zu konfigurieren oder zu bedienen.

Nicht wesentliche Funktionalität kann umfassen:

* visuelle Dekoration
* optionale Animationen
* dekorative Klänge
* redundantes haptisches Feedback
* optionale Abkürzungen
* nicht erforderliche Verbesserungen
* zusätzliche Marketinginhalte
* experimentelle Funktionen
* Komfortabläufe, die den wesentlichen Zugang nicht verändern

Nicht wesentliche Funktionalität muss nicht immer über jeden Sinnesweg gleich verfügbar sein. Das Fehlen nicht wesentlicher Funktionalität darf jedoch den Zugang zu wesentlicher oder kritischer Funktionalität nicht blockieren.

<a id="accessibility-requirements"></a>

## Barrierefreiheitsanforderungen

<a id="essential-access-requirement"></a>

### Anforderung an wesentlichen Zugang

Wesentliche Funktionalität muss in jedem erforderlichen Barrierefreiheitsfall zugänglich, verständlich und bedienbar bleiben.

Ein System kann diese Anforderung durch jeden stabilen Mechanismus erfüllen, der angemessenen alternativen Zugang bereitstellt.

<a id="critical-access-requirement"></a>

### Anforderung an kritischen Zugang

Kritische Funktionalität muss in jedem erforderlichen Barrierefreiheitsfall klar zugänglich, verständlich und bedienbar bleiben.

Kritische Funktionalität darf nicht allein vom nicht verfügbaren Sinn abhängen.

<a id="alternate-access-requirement"></a>

### Anforderung an alternativen Zugang

Wenn wesentliche Bedeutung oder Bedienung andernfalls vom nicht verfügbaren Sinn abhängen würde, muss das System einen angemessenen alternativen Zugangsweg bereitstellen.

Der alternative Zugangsweg muss die wesentliche Bedeutung oder die wesentliche Bedienfähigkeit bewahren.

Alternative Zugangswege können umfassen:

* Textäquivalente
* Untertitel
* Transkripte
* Screenreader
* gesprochene Ausgabe
* visuelle Ausgabe
* taktile Ausgabe
* Tastaturnavigation
* Zeigernavigation
* Sprachsteuerung
* Schaltersteuerung
* Gestenalternativen
* visuelle Statusanzeigen
* nicht-auditive Warnungen
* nicht-taktile Bestätigungen
* einen anderen stabilen und geeigneten Mechanismus

Der alternative Zugangsweg muss nicht identisch mit dem ursprünglichen Weg sein. Er muss für wesentliche Nutzung ausreichend sein.

<a id="no-single-sense-dependency"></a>

### Keine Abhängigkeit von einem einzigen Sinn

Wesentliche Funktionalität darf nicht nur einen primären Sinn erfordern, wenn dieser Sinn in einem erforderlichen Fall nicht verfügbar ist.

Ein System darf wesentliche Bedeutung oder Bedienung nicht einsperren hinter:

* rein visuellen Informationen
* rein auditiven Informationen
* rein berührungsbasierter Interaktion
* Farbe ohne Alternative
* Klang ohne Alternative
* Vibration ohne Alternative
* Geste ohne Alternative
* Textur ohne Alternative
* Bewegung ohne Alternative
* direkter Manipulation ohne Alternativen

wenn diese Interaktion erforderlich ist, um wesentliche Funktionalität zu verstehen oder zu bedienen.

Ein System kann diesen Fall nicht bestehen, wenn ein Benutzer das wesentliche System ohne diesen Sinn nicht angemessen navigieren, verstehen oder bedienen kann.

<a id="sight-unavailable"></a>

## Sehen nicht verfügbar

Wenn Sehen nicht verfügbar ist, muss das System über Hören und Berühren angemessen nutzbar bleiben.

Ein System kann diesen Fall durch Mechanismen erfüllen wie:

* semantische Struktur für Screenreader
* sinnvolle Fokusreihenfolge
* Tastaturnavigation
* klare Beschriftungen von Steuerelementen
* gesprochene Ausgabe
* Audiobeschreibungen
* nicht-visuelle Anweisungen
* taktile Bestätigung
* physische Steuerelemente
* Audiobestätigung
* Textbeschreibung wichtiger Bilder
* Alternativen für Diagramme oder Schaubilder
* Statusmeldungen, die von assistiven Technologien gelesen werden können
* einen anderen stabilen nicht-visuellen Mechanismus

Das System darf sich nicht ausschließlich verlassen auf:

* visuelle Position
* Farbe
* Form
* Symbole allein
* Layout allein
* Animation allein
* Bilder ohne Beschreibung
* Video ohne wesentliche Beschreibung
* Fokuszustände, die für assistive Technologien unsichtbar sind
* Steuerelemente ohne Beschriftung

wenn diese Informationen erforderlich sind, um wesentliche Funktionalität zu verstehen oder zu bedienen.

Ein System kann diesen Fall nicht bestehen, wenn ein Benutzer das wesentliche System ohne Sehen nicht angemessen navigieren, verstehen oder bedienen kann.

<a id="sound-unavailable"></a>

## Hören nicht verfügbar

Wenn Hören nicht verfügbar ist, muss das System über Sehen und Berühren angemessen nutzbar bleiben.

Ein System kann diesen Fall durch Mechanismen erfüllen wie:

* Untertitel
* Transkripte
* visuelle Alarme
* visuelle Statusanzeigen
* Textäquivalente
* visuelle Warnmeldungen
* visuelle Benachrichtigungen
* visuelle Fortschrittsanzeigen
* taktile Bestätigung
* Vibration
* visuelle Anweisungen
* Alternativen für Alarme oder Audiohinweise
* einen anderen stabilen nicht-auditiven Mechanismus

Das System darf sich nicht ausschließlich verlassen auf:

* gesprochene Anweisungen
* Soundeffekte
* Audiohinweise
* Alarme
* musikalische Hinweise
* Ton oder Tonhöhe
* Dialog ohne Untertitel
* reine Audioaufforderungen
* reine Tonwarnungen
* reine akustische Erfolgsbestätigungen

wenn diese Informationen erforderlich sind, um wesentliche Funktionalität zu verstehen oder zu bedienen.

Ein System kann diesen Fall nicht bestehen, wenn ein Benutzer das wesentliche System ohne Hören nicht angemessen navigieren, verstehen oder bedienen kann.

<a id="touch-unavailable"></a>

## Berühren nicht verfügbar

Wenn Berühren nicht verfügbar ist, muss das System über Sehen und Hören angemessen nutzbar bleiben.

Ein System kann diesen Fall durch Mechanismen erfüllen wie:

* Tastaturnavigation
* Zeigernavigation
* Sprachsteuerung
* gesprochene Befehle
* Schaltersteuerung
* Ferneingabe
* blickkompatible Interaktion
* visuelle Anweisungen
* gesprochene Anweisungen
* visuelle Bestätigung
* Audiobestätigung
* Gestenalternativen
* Alternativen für druckbasierte Aktionen
* einen anderen stabilen nicht-berührungsbasierten Mechanismus

Das System darf sich nicht ausschließlich verlassen auf:

* Berührungsgesten
* direkte Berührungsmanipulation
* Vibration
* haptisches Feedback
* Textur
* Druck
* Kraft
* physische Tasten ohne Alternative
* Multi-Touch ohne Alternative
* reine Ziehbedienung
* reine Wischbedienung
* rein berührungsbasiertes Verhalten

wenn diese Interaktion erforderlich ist, um wesentliche Funktionalität zu verstehen oder zu bedienen.

Ein System kann diesen Fall nicht bestehen, wenn ein Benutzer das wesentliche System ohne Berühren nicht angemessen navigieren, verstehen oder bedienen kann.

<a id="implementation-requirements"></a>

## Implementierungsanforderungen

<a id="stable-accessibility-mechanism"></a>

### Stabiler Barrierefreiheitsmechanismus

Ein konformes System muss einen stabilen Barrierefreiheitsmechanismus verwenden, der für das geprüfte System geeignet ist.

Ein stabiler Barrierefreiheitsmechanismus sollte es ermöglichen, Barrierefreiheitsverhalten zu warten, zu aktualisieren, zu prüfen und zu erweitern, ohne sich auf fragiles oder undokumentiertes Verhalten zu verlassen.

Ein stabiler Barrierefreiheitsmechanismus kann umfassen:

* native Barrierefreiheits-APIs der Plattform
* semantische Struktur
* alternative Eingabemethoden
* alternative Ausgabemethoden
* Unterstützung assistiver Technologien
* integrierte Barrierefreiheitseinstellungen
* geräteweite Integration
* dokumentierte Tastaturinteraktion
* dokumentierte Sprachinteraktion
* dokumentierte nicht-visuelle Interaktion
* eine andere stabile Struktur, die für das System geeignet ist

Ein System sollte vermeiden, wesentliche Funktionalität so zu implementieren, dass angemessener alternativer Zugang verhindert wird.

<a id="semantic-structure"></a>

### Semantische Struktur

Ein konformes System sollte semantische Struktur bereitstellen, wenn das System bedeutungsvollen Inhalt oder Steuerelemente präsentiert.

Semantische Struktur kann umfassen:

* Namen
* Rollen
* Zustände
* Beziehungen
* Reihenfolge
* Gruppierung
* Beschriftungen
* Beschreibungen
* Fokusverhalten
* Zweck des Steuerelements
* Inhaltshierarchie

Semantische Struktur ist besonders wichtig, wenn Sehen nicht verfügbar ist, weil assistive Technologien häufig auf semantische Informationen angewiesen sind, um visuelle Oberflächen über nicht-visuelle Ausgabe zu vermitteln.

Ein System kann die Prüfung nicht bestehen, wenn wesentliche Steuerelemente oder Inhalte nicht verstanden werden können, weil ihre Struktur, Beschriftungen oder Beziehungen über alternative Zugangswege nicht verfügbar sind.

<a id="alternate-output"></a>

### Alternative Ausgabe

Ein konformes System muss angemessene alternative Ausgabe bereitstellen, wenn wesentliche Bedeutung andernfalls vom nicht verfügbaren Sinn abhängen würde.

Alternative Ausgabe kann umfassen:

* visuelle Ausgabe für auditive Informationen
* auditive Ausgabe für visuelle Informationen
* taktile Ausgabe für visuelle oder auditive Informationen
* Textäquivalente
* Untertitel
* Transkripte
* gesprochene Beschreibungen
* sichtbare Statusmeldungen
* haptische Bestätigung
* einen anderen geeigneten Ausgabeweg

Alternative Ausgabe muss wesentliche Bedeutung bewahren.

<a id="alternate-input"></a>

### Alternative Eingabe

Ein konformes System muss angemessene alternative Eingabe bereitstellen, wenn wesentliche Bedienung andernfalls allein von Berührung abhängen würde.

Alternative Eingabe kann umfassen:

* Tastatureingabe
* Zeigereingabe
* Spracheingabe
* Schaltereingabe
* Ferneingabe
* blickkompatible Eingabe
* Befehlseingabe
* einen anderen geeigneten Eingabeweg

Alternative Eingabe muss nicht die schnellste oder bequemste Eingabemethode sein. Sie muss für wesentliche Bedienung ausreichend sein.

<a id="accessible-feedback"></a>

### Zugängliches Feedback

Ein konformes System muss zugängliches Feedback für wesentliche Aktionen bereitstellen.

Zugängliches Feedback kann umfassen:

* Bestätigung, dass eine Aktion erfolgt ist
* Hinweis, dass eine Aktion fehlgeschlagen ist
* Fortschrittsinformationen
* Validierungsmeldungen
* Warnmeldungen
* Fehlermeldungen
* Abschlussstatus
* aktuelle Auswahl
* aktueller Fokus
* aktueller Modus
* aktueller Systemzustand

Feedback darf sich im jeweiligen Barrierefreiheitsfall nicht ausschließlich auf den nicht verfügbaren Sinn verlassen.

Zum Beispiel ist ein reiner Erfolgsjingle nicht ausreichend, wenn Hören nicht verfügbar ist. Ein rein farbbasierter Fehlerzustand ist nicht ausreichend, wenn Sehen nicht verfügbar ist. Eine reine Vibrationsbestätigung ist nicht ausreichend, wenn Berühren nicht verfügbar ist.

<a id="accessible-configuration"></a>

### Zugängliche Konfiguration

Ein konformes System muss Benutzern ermöglichen, erforderliche Barrierefreiheitseinstellungen über dieselben Barrierefreiheitsanforderungen zu erreichen und zu verwenden, die durch diese Spezifikation definiert werden.

Barrierefreiheitseinstellungen dürfen nicht hinter einem unzugänglichen Pfad verborgen sein.

Zum Beispiel ist ein screenreader-kompatibler Modus nicht ausreichend, wenn der Benutzer zuerst ein unbeschriftetes rein visuelles Menü navigieren muss, um ihn zu aktivieren.

Ein System kann die Prüfung nicht bestehen, wenn seine Barrierefreiheitskonfiguration in der Bedingung, die sie unterstützen soll, nicht erreicht oder bedient werden kann.

<a id="verification"></a>

## Verifizierung

<a id="within-spec"></a>

### Innerhalb der Spezifikation

Ein System gilt als innerhalb der Spezifikation, wenn das CatalystUI Team das System geprüft hat und es angemessen findet, daraus zu schließen, dass es A11YSPEC erfüllt.

Ein System kann innerhalb der Spezifikation liegen, wenn:

* Nutzung ohne Sehen angemessen unterstützt bleibt
* Nutzung ohne Hören angemessen unterstützt bleibt
* Nutzung ohne Berühren angemessen unterstützt bleibt
* wesentliche Funktionalität in jedem erforderlichen Fall zugänglich bleibt
* kritische Funktionalität in jedem erforderlichen Fall zugänglich bleibt
* alternative Zugangswege wesentliche Bedeutung und Bedienung bewahren
* Barrierefreiheitseinstellungen, sofern vorhanden, zugänglich erreicht und verwendet werden können
* das System wesentliche Funktionalität nicht hinter einem erforderlichen Sinn einsperrt
* das System einen stabilen Barrierefreiheitsmechanismus verwendet, der zu seinem Design passt

Ein System kann innerhalb der Spezifikation liegen, auch wenn Erfahrungen nicht über alle Sinneswege identisch sind.

Ein System kann innerhalb der Spezifikation liegen, auch wenn einige nicht wesentliche Funktionalität nicht in jedem erforderlichen Barrierefreiheitsfall gleich verfügbar ist.

<a id="warnings"></a>

### Warnungen

Eine Warnung kann ausgegeben werden, wenn ein System A11YSPEC zu erfüllen scheint, aber Bedenken enthält, die dokumentiert werden sollten.

Warnungen können umfassen:

* geringfügiger nicht wesentlicher Inhalt, der in einem Barrierefreiheitsfall nicht verfügbar ist
* langsamere, aber nutzbare alternative Zugangswege
* unvollkommene, aber verständliche Untertitel oder Transkripte
* begrenzte, aber funktionale Tastaturnavigation
* begrenzte, aber funktionale Screenreader-Unterstützung
* geringfügige Bedenken zur Fokusreihenfolge, die wesentliche Nutzung nicht blockieren
* redundante visuelle, auditive oder taktile Hinweise, die auf einem Weg fehlen
* Barrierefreiheitseinstellungen, die nutzbar, aber schwer zu finden sind
* Unterstützung assistiver Technologien, die funktioniert, aber klarer sein könnte
* optionale Abläufe, die nicht gleichermaßen zugänglich sind

Warnungen verhindern die Verifizierung nicht notwendigerweise.

<a id="failures"></a>

### Fehler

Ein Fehler tritt auf, wenn ein System eine oder mehrere erforderliche Bedingungen von A11YSPEC nicht erfüllt.

Fehler können umfassen:

* wesentliche Funktionalität nicht verfügbar, wenn Sehen nicht verfügbar ist
* wesentliche Funktionalität nicht verfügbar, wenn Hören nicht verfügbar ist
* wesentliche Funktionalität nicht verfügbar, wenn Berühren nicht verfügbar ist
* kritische Funktionalität in einem erforderlichen Barrierefreiheitsfall nicht verfügbar
* kein angemessener alternativer Zugangsweg für wesentliche visuelle Informationen
* kein angemessener alternativer Zugangsweg für wesentliche auditive Informationen
* kein angemessener alternativer Zugangsweg für wesentliche berührungsbasierte Bedienung
* Barrierefreiheitseinstellungen in der Bedingung, die sie unterstützen sollen, nicht erreichbar
* Steuerelemente ohne sinnvolle Beschriftungen oder Struktur, wenn diese für nicht-visuelle Nutzung erforderlich sind
* reine Tonwarnungen ohne visuelles, taktiles oder textliches Äquivalent
* rein farbbasierter Status ohne nicht-visuelles Äquivalent
* rein gestenbasierte Bedienung ohne Tastatur, Zeiger, Sprache, Schalter oder andere Alternative
* rein haptische Bestätigung ohne visuelles oder auditives Äquivalent
* defekte Unterstützung assistiver Technologien für wesentliche Abläufe
* größere Navigationsfallen
* wesentliche Abläufe, die ohne den nicht verfügbaren Sinn nicht abgeschlossen werden können

Fehler verhindern die Verifizierung, bis sie behoben sind.

<a id="verification-validity"></a>

### Gültigkeit der Verifizierung

A11YSPEC-Verifizierung gilt nur für den geprüften Zustand des Systems zum Zeitpunkt der Ausstellung der Verifizierung.

Ein System kann seine Verifizierung über spätere Updates hinweg behalten, solange es die verifizierte Barrierefreiheitsgrundlage bewahrt.

Geringfügige Formulierungsänderungen, visuelle Verfeinerungen, Leistungsverbesserungen, hinzugefügte Barrierefreiheitsfunktionen und gewöhnliche Inhaltsupdates machen die Verifizierung nicht automatisch ungültig.

Eine neue Prüfung kann erforderlich sein, wenn ein System:

* alternative Zugangswege entfernt
* Unterstützung für assistive Technologien bricht
* wesentliche Navigation erheblich verändert
* erforderliche Barrierefreiheitseinstellungen entfernt
* Interaktionsverhalten so verändert, dass verifizierte Barrierefreiheit betroffen ist
* neue wesentliche Abläufe ohne zugängliche Alternativen einführt
* zuvor zugängliche kritische Funktionalität unzugänglich macht
* zugängliches Verhalten durch Verhalten ersetzt, das von einem einzigen Sinn abhängt

Anders gesagt: Barrierefreiheit zu verbessern ist normalerweise in Ordnung.

Das verifizierte Zugangsmodell zu brechen, kann eine Prüfung erfordern.
