<!-- Diese Übersetzung wurde von ChatGPT erstellt und sollte von einem menschlichen Übersetzer überprüft werden. -->
<!-- Entfernen Sie diese Zeilen in einem Pull Request, nachdem die Übersetzung verifiziert wurde. -->

![CatalystUI Verified for Programming Languages](/images/verification/verified-logo-languages.png)

# CatalystUI Verified für Programmiersprachen

Willkommen in der CatalystUI-Verifizierungsdokumentation für Programmiersprachen.

**CatalystUI Verified für Programmiersprachen** bedeutet, dass eine Programmiersprache vom CatalystUI-Team geprüft wurde und dass festgestellt wurde, dass sie die grundlegenden Datenrepräsentationen und relationalen Strukturen bereitstellt, die erforderlich sind, um CatalystUI-kompatible Systeme auszudrücken.

Diese Verifizierung ist keine allgemeine Rangliste von Programmiersprachen. Sie entscheidet nicht, ob eine Sprache besser, schneller, einfacher, neuer, beliebter oder angenehmer ist als eine andere. Stattdessen stellt sie fest, ob die Sprache eine stabile und praktische Grundlage für die Spezifikationen bereitstellt, die für die CatalystUI-Verifizierung erforderlich sind.

Einfacher gesagt fragt diese Verifizierung, ob eine Programmiersprache die grundlegenden Daten und Beziehungen, von denen CatalystUI abhängt, zuverlässig darstellen kann.

## Zweck

Programmiersprachen bilden die repräsentative Grundlage unter jeder CatalystUI-Implementierung. Bevor ein Framework, eine Bibliothek, eine Laufzeitumgebung, eine Anwendung oder ein Dienst dem CatalystUI-Stack folgen kann, muss die Sprache, mit der es gebaut wird, in der Lage sein, die grundlegenden Konzepte auszudrücken, auf denen das Modell beruht.

Für Programmiersprachen bedeutet dies hauptsächlich zwei Dinge:

1. Die Sprache muss grundlegende Daten darstellen können.
2. Die Sprache muss grundlegende Beziehungen zwischen Daten darstellen können.

Diese Anliegen werden durch die grundlegenden CatalystUI-Spezifikationen definiert. FDEFSPEC definiert die erwarteten grundlegenden Datenrepräsentationen. FRELSPEC definiert die erwarteten grundlegenden Relationen zwischen diesen Repräsentationen, einschließlich Sammlungen, Speicherbeziehungen, Operationen, Threading-Beziehungen und zusammengesetzten Strukturen.

Eine verifizierte Programmiersprache gibt Entwicklern genug Klarheit und Kontrolle, um CatalystUI-kompatible Systeme zu bauen, ohne sich für die grundlegenden Konzepte, die CatalystUI benötigt, auf fragile, unklare oder instabile Ausweichlösungen verlassen zu müssen.

## Was Verifizierung bedeutet

Eine Programmiersprache wird **CatalystUI Verified**, wenn sie anhand der in diesem Abschnitt aufgeführten Spezifikationen geprüft und als spezifikationskonform befunden wurde.

Bei der Verifizierung von Programmiersprachen konzentriert sich die Prüfung darauf, ob die Sprache die grundlegenden Anforderungen ausdrücken kann, die durch die anwendbaren Spezifikationen definiert sind. Das bedeutet nicht, dass die Sprache selbst eine CatalystUI-Implementierung ist. Es bedeutet, dass die Sprache eine geeignete Grundlage bereitstellt, auf der CatalystUI-kompatible Implementierungen aufgebaut werden können.

Eine Sprache muss diese Anforderungen nicht auf dieselbe Weise erfüllen wie eine andere Sprache. Verschiedene Sprachen verwenden unterschiedliche Syntax, Typsysteme, Standardbibliotheken, Compiler, Laufzeitumgebungen und Entwurfsmuster. CatalystUI-Verifizierung lässt diese Unterschiede zu, solange die erforderlichen Konzepte klar, zuverlässig und konsistent ausgedrückt werden können.

## Was „Within Spec“ bedeutet

Wenn eine Programmiersprache als **within spec** betrachtet wird, bedeutet dies, dass das CatalystUI-Team die Sprache manuell geprüft hat und es für vernünftig hält, zu dem Schluss zu kommen, dass das durch die anwendbaren Spezifikationen beschriebene erforderliche Verhalten innerhalb dieser Sprache ausgedrückt werden kann.

Dies erfordert kein starres Implementierungsmuster. Eine Sprache kann eine Anforderung durch eingebaute Primitive, Funktionen der Standardbibliothek, Compilerverhalten, Laufzeitverhalten, dokumentierte Garantien oder einen anderen stabilen Mechanismus erfüllen, der zu dieser Sprache passt.

Bei der Verifizierung geht es um die praktische Fähigkeit, die Bedeutung der Spezifikation darzustellen und zu bewahren, nicht darum, ob die Sprache genau dieselben Namen, Strukturen, dieselbe Syntax oder dasselbe interne Design wie der Spezifikationstext verwendet.

## Warum diese Verifizierung existiert

CatalystUI ist auf Klarheit, Konsistenz und die getreue Darstellung davon ausgelegt, wie Menschen und Computer miteinander interagieren. Programmiersprachen sind wichtig, weil sie bestimmen, was Entwickler realistisch ausdrücken können, wie sicher diese Systeme modelliert werden können und wie klar höherstufige Implementierungen aufgebaut werden können.

Wenn eine Sprache die erforderlichen grundlegenden Konzepte nicht auf stabile Weise bereitstellen kann, werden höherstufige CatalystUI-Implementierungen schwerer vertrauenswürdig. Entwickler könnten zu unklaren Abstraktionen, unvorhersehbarem Verhalten, fragilen Abhängigkeiten oder unnötigen Neuschreibungen gedrängt werden, nur um Ideen auszudrücken, die von Anfang an zuverlässig sein sollten.

Die Verifizierung von Programmiersprachen existiert, um festzustellen, welche Sprachen eine ausreichend starke Grundlage für CatalystUI-Arbeit bereitstellen. Sie gibt Entwicklern, Sprachdesignern und Organisationen ein klareres Verständnis davon, ob eine Sprache geeignet ist, um CatalystUI-kompatible Systeme zu bauen.

## Wie eine Sprache verifiziert wird

Um **CatalystUI Verified für Programmiersprachen** zu werden, muss eine Sprache anhand der in diesem Abschnitt aufgeführten Spezifikationen geprüft werden.

Der allgemeine Prozess ist:

1. Die anwendbaren CatalystUI-Spezifikationen werden identifiziert.
2. Die Sprache wird anhand jeder erforderlichen Spezifikation geprüft.
3. Das CatalystUI-Team bestimmt, ob die Sprache die Absicht und Anforderungen der Spezifikationen erfüllt.
4. Wenn die Sprache als spezifikationskonform befunden wird, kann ihr CatalystUI-Verifizierung gewährt werden.
5. Nach der Verifizierung kann die Sprache auf der Seite [Verifizierte Sprachen](/verified/) aufgeführt werden.

Die Prüfung kann offizielle Sprachdokumentation, Verhalten der Standardbibliothek, Compilerverhalten, Laufzeitverhalten, Implementierungsbeispiele, Testfälle und andere Nachweise berücksichtigen, die erforderlich sind, um zu bestimmen, ob die Sprache die Anforderungen erfüllt.

Compiler- und Laufzeitverhalten können während der Prüfung berücksichtigt werden, wenn dieses Verhalten Teil der üblichen und offiziellen Nutzung der Sprache ist. Die Verifizierung einer Programmiersprache verifiziert jedoch nicht automatisch jeden Compiler, jede Laufzeitumgebung, jedes Paket, Framework, jede Bibliothek, Anwendung oder jedes Werkzeug im Ökosystem dieser Sprache.

## Anwendbare Spezifikationen

Die in diesem Abschnitt aufgeführten Spezifikationen definieren die Anforderungen, die für die Verifizierung von Programmiersprachen verwendet werden.

Für Programmiersprachen ist die aktive Grundlage derzeit auf die folgenden Spezifikationskategorien ausgerichtet:

* **FDEFSPEC**, die grundlegende Datenrepräsentationen definiert.
* **FRELSPEC**, die grundlegende Relationen zwischen Datenrepräsentationen definiert.

Zusammen legen diese Spezifikationen die Mindestgrundlage fest, die erforderlich ist, damit eine Programmiersprache CatalystUI-kompatible Systeme darstellen kann.

Später können zusätzliche Spezifikationen für spezialisiertere Verifizierungskategorien eingeführt werden. Diese Spezifikationen können Anforderungen an höherstufige Implementierung, Plattform, Barrierefreiheit, Internationalisierung, Frameworks, Dienste oder Laufzeitumgebungen definieren. Diese späteren Spezifikationen bauen jedoch auf der Grundlage auf, anstatt sie zu ersetzen.

Eine Programmiersprache wird verifiziert, indem sie die erforderlichen Spezifikationen für diese Kategorie erfüllt. Von ihr wird nicht erwartet, dass sie nicht zusammenhängende implementierungsspezifische Anforderungen erfüllt, es sei denn, diese Anforderungen werden der Verifizierung von Programmiersprachen hinzugefügt.

## Umfang der Verifizierung

CatalystUI-Verifizierung für Programmiersprachen gilt für die geprüfte Programmiersprache.

Eine verifizierte Sprache stellt eine geeignete Grundlage für CatalystUI-kompatible Entwicklung bereit. Sie garantiert nicht, dass jedes in dieser Sprache geschriebene Projekt CatalystUI korrekt folgt, und verifiziert auch nicht automatisch das umliegende Ökosystem.

Separate Werkzeuge, Bibliotheken, Frameworks, Laufzeitumgebungen, Anwendungen, Dienste oder Implementierungen können je nach angeforderter Verifizierungskategorie eine eigene Prüfung erfordern.

Die Verifizierung von Programmiersprachen sollte daher als Grundlagenprüfung verstanden werden. Sie bestätigt, dass die Sprache die erforderlichen Konzepte darstellen kann. Sie bestätigt nicht, dass jede Verwendung der Sprache diese Konzepte korrekt anwendet.

## Gültigkeit der Verifizierung

CatalystUI-Verifizierung gilt nur für den geprüften Zustand einer Programmiersprache zum Zeitpunkt der Ausstellung der Verifizierung.

Programmiersprachen werden als Sonderfall behandelt, weil viele Sprachen über mehrere Versionen hinweg Kompatibilität bewahren. Eine Sprache kann ihre Verifizierung über spätere Versionen hinweg behalten, solange sie Abwärtskompatibilität mit den Features, Primitiven, Repräsentationen und dem Verhalten bewahrt, auf denen die ursprüngliche Prüfung beruhte.

Neue Sprachfeatures allein machen eine Verifizierung nicht ungültig. Eine zukünftige Version kann nur dann eine neue Prüfung erfordern, wenn sie die verifizierte Grundlage entfernt, bricht oder wesentlich verändert.

Mit anderen Worten: Eine Sprache zu erweitern ist normalerweise in Ordnung. Die verifizierte Basis zu brechen kann eine erneute Prüfung erforderlich machen.

## Verifizierte Sprachen

Bekannte verifizierte Programmiersprachen sind separat auf der Seite [Verifizierte Sprachen](/verified/) aufgeführt.
