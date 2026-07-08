<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden beoordeeld. -->
<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

![CatalystUI Verified for Programming Languages](/images/verification/verified-logo-languages.png)

# CatalystUI Verified voor programmeertalen

Welkom bij de CatalystUI Verification-documentatie voor programmeertalen.

**CatalystUI Verified voor programmeertalen** betekent dat een programmeertaal door het CatalystUI-team is beoordeeld en dat is vastgesteld dat de taal de fundamentele datarepresentaties en relationele structuren biedt die nodig zijn om systemen te beschrijven die met CatalystUI compatibel zijn.

Deze verificatie is geen algemene ranglijst van programmeertalen. Ze bepaalt niet of de ene taal beter, sneller, eenvoudiger, nieuwer, populairder of prettiger is dan een andere. In plaats daarvan beoordeelt ze of de taal een stabiele en praktische basis biedt voor de specificaties die CatalystUI Verification vereist.

Eenvoudiger gezegd vraagt deze verificatie: “Kan deze programmeertaal de fundamentele data en relaties waarop CatalystUI vertrouwt getrouw weergeven?”

## Doel

Programmeertalen vormen de representatieve basis onder elke CatalystUI-implementatie. Voordat een framework, bibliotheek, runtime, toepassing of service de CatalystUI Stack kan volgen, moet de taal waarmee die wordt gebouwd de fundamentele concepten kunnen uitdrukken waarop het model vertrouwt.

Voor programmeertalen betekent dit vooral twee dingen.

1. De taal moet fundamentele data kunnen weergeven.
2. De taal moet fundamentele relaties tussen data kunnen weergeven.

Deze aandachtspunten worden gedefinieerd door de fundamentele specificaties van CatalystUI. FDEFSPEC definieert de verwachte fundamentele datarepresentaties. FRELSPEC definieert de verwachte fundamentele relaties tussen die representaties, waaronder collecties, geheugenrelaties, bewerkingen, threading-relaties en composieten.

Een geverifieerde programmeertaal biedt voldoende duidelijkheid en controle om ontwikkelaars CatalystUI-compatibele systemen te laten bouwen zonder te vertrouwen op kwetsbare, onduidelijke of instabiele omwegen voor de basisconcepten die CatalystUI vereist.

## Wat Verification betekent

Een programmeertaal wordt **CatalystUI Verified** wanneer deze is beoordeeld aan de hand van de specificaties die in deze sectie zijn genoemd en is vastgesteld dat zij within spec is.

Bij Programming Language Verification ligt de beoordeling op de vraag of de taal de fundamentele vereisten kan uitdrukken die door de toepasselijke specificaties worden gedefinieerd. Dit betekent niet dat de taal zelf een CatalystUI-implementatie is. Het betekent dat de taal een geschikte basis biedt waarop CatalystUI-compatibele implementaties kunnen worden gebouwd.

Een taal hoeft deze vereisten niet op dezelfde manier te vervullen als een andere taal. Verschillende talen hebben verschillende syntaxis, typesystemen, standaardbibliotheken, compilers, runtimes en ontwerppatronen. CatalystUI Verification staat die verschillen toe zolang de vereiste concepten duidelijk, betrouwbaar en consequent kunnen worden uitgedrukt.

## Wat “Within Spec” betekent

Wanneer een programmeertaal als **within spec** wordt beschouwd, betekent dit dat het CatalystUI-team de taal handmatig heeft beoordeeld en heeft vastgesteld dat het redelijk is om te concluderen dat de taal de vereiste gedragingen kan uitdrukken die door de toepasselijke specificaties worden beschreven.

Dit vereist geen enkel strikt implementatiepatroon. Een taal kan aan de vereisten voldoen via ingebouwde primitives, standaardbibliotheekfuncties, compiler-gedrag, runtime-gedrag, gedocumenteerde garanties of andere stabiele mechanismen die geschikt zijn voor die taal.

Verificatie gaat over het vermogen om de betekenis van de specificatie werkelijk te vertegenwoordigen en te behouden, niet over de vraag of de taal exact dezelfde namen, structuren, syntaxis of interne ontwerpen gebruikt als de specificatiedocumenten.

## Waarom deze Verification bestaat

CatalystUI benadert menselijke-computerinteractie met nadruk op duidelijkheid, consistentie en getrouwe representatie. Programmeertalen zijn belangrijk omdat zij bepalen wat ontwikkelaars realistisch kunnen uitdrukken, hoe veilig zij een systeem kunnen modelleren en hoe duidelijk zij hogere implementatielagen kunnen bouwen.

Als een taal de vereiste fundamentele concepten niet op een stabiele manier kan leveren, wordt een hogere CatalystUI-implementatie moeilijk te vertrouwen. Ontwikkelaars kunnen dan worden gedwongen tot onduidelijke abstracties, onvoorspelbaar gedrag, kwetsbare afhankelijkheden of onnodige herschrijvingen om concepten weer te geven die vanaf het begin betrouwbaar zouden moeten zijn.

Programming Language Verification bestaat om talen te identificeren die een stevig genoeg fundament bieden voor CatalystUI-werk. Daardoor krijgen ontwikkelaars, taalontwerpers en organisaties duidelijker inzicht in welke talen geschikt zijn voor het bouwen van CatalystUI-compatibele systemen.

## Hoe een taal Verified wordt

Om **CatalystUI Verified voor programmeertalen** te worden, moet een taal worden beoordeeld aan de hand van de specificaties die in deze sectie worden genoemd.

Het algemene proces is als volgt:

1. Identificeer de toepasselijke CatalystUI-specificaties.
2. Beoordeel de taal aan de hand van elke vereiste specificatie.
3. Het CatalystUI-team bepaalt of de taal voldoet aan de bedoeling en vereisten van de specificatie.
4. Als de taal within spec wordt bevonden, kan CatalystUI Verification worden toegekend.
5. Nadat verificatie is voltooid, kan de taal worden vermeld op de pagina [Verified Languages](/verified/).

De beoordeling kan officiële taaldocumentatie, standaardbibliotheekgedrag, compiler-gedrag, runtime-gedrag, voorbeeldimplementaties, testgevallen en ander bewijs meenemen dat nodig is om te bepalen of de taal aan de vereisten voldoet.

Compiler- en runtime-gedrag kunnen in de beoordeling worden meegenomen wanneer zij deel uitmaken van het normale en officiële gebruik van de taal. Verificatie van een programmeertaal verifieert echter niet automatisch elke compiler, runtime, package, framework, bibliotheek, toepassing of tool binnen het ecosysteem van die taal.

## Toepasselijke specificaties

De specificaties in deze sectie definiëren de vereisten die worden gebruikt voor Programming Language Verification.

Voor programmeertalen is de huidige actieve basis gecentreerd rond de volgende specificatiecategorieën:

* **FDEFSPEC**: definieert fundamentele datarepresentaties.
* **FRELSPEC**: definieert fundamentele relaties tussen datarepresentaties.

Samen vormen deze twee specificaties de minimale basis die een programmeertaal nodig heeft om CatalystUI-compatibele systemen te kunnen vertegenwoordigen.

Later kunnen aanvullende specificaties worden geïntroduceerd voor meer gespecialiseerde verificatiecategorieën. Zulke specificaties kunnen vereisten definiëren voor hogere implementaties, platforms, toegankelijkheid, internationalisering, frameworks, services of runtimes. Latere specificaties vervangen deze basis echter niet; ze bouwen erop voort.

Een programmeertaal wordt geverifieerd door te voldoen aan de specificaties die voor deze categorie vereist zijn. Niet-gerelateerde implementatiespecifieke vereisten hoeven niet te worden vervuld tenzij zij expliciet aan Programming Language Verification worden toegevoegd.

## Reikwijdte van Verification

CatalystUI Verification voor een programmeertaal is van toepassing op de programmeertaal zoals die op het moment van de beoordeling is onderzocht.

Een geverifieerde taal biedt een geschikte basis voor CatalystUI-compatibele ontwikkeling. Dit garandeert echter niet dat elk project dat in die taal is geschreven CatalystUI correct volgt, en het verifieert ook niet automatisch het omliggende ecosysteem.

Afzonderlijke tools, bibliotheken, frameworks, runtimes, toepassingen, services of implementaties kunnen hun eigen beoordeling vereisen, afhankelijk van de aangevraagde verificatiecategorie.

Programming Language Verification moet daarom worden gezien als een basiscontrole. Ze bevestigt dat de taal de vereiste concepten kan vertegenwoordigen. Ze bevestigt niet dat elk gebruik van die taal die concepten correct toepast.

## Geldigheid van Verification

CatalystUI Verification is alleen van toepassing op de staat van de programmeertaal zoals die is beoordeeld op het moment waarop de verificatie is uitgegeven.

Veel talen behouden compatibiliteit tussen versies, daarom worden programmeertalen als een bijzonder geval behandeld. Een taal kan in latere versies geverifieerd blijven zolang zij achterwaartse compatibiliteit behoudt met de functies, primitives, representaties en gedragingen waarop de oorspronkelijke beoordeling vertrouwde.

Nieuwe taalfuncties maken een verificatie op zichzelf niet ongeldig. Een nieuwe beoordeling kan alleen nodig zijn wanneer een toekomstige versie de geverifieerde basis verwijdert, verbreekt of wezenlijk verandert.

Met andere woorden: het uitbreiden van een taal is meestal prima. Het verbreken van de geverifieerde basis kan een nieuwe beoordeling vereisen.

## Verified Languages

Bekende geverifieerde programmeertalen worden afzonderlijk vermeld op de pagina [Verified Languages](/verified/).
