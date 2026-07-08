<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden beoordeeld. -->

<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

# I18NSPEC

<br/>

> **Internationalisatiespecificatie**<br/>
> Revisie 1<br/>
> 8 juli 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> De definities, vereisten en concepten die hier worden gepresenteerd beschrijven praktische ondersteuning voor internationalisatie en mogen vrij opnieuw worden geformuleerd.

<a id="introduction"></a>
## Inleiding

De **Internationalization Specification (I18NSPEC)** legt de kernconcepten, terminologie en vereisten vast die worden gebruikt om meertalige ondersteuning binnen het CatalystUI-ecosysteem te beoordelen. Het doel is een duidelijke standaard te bieden om te bepalen of een systeem, dienst, framework, applicatie of implementatie voldoende taalondersteuning biedt om als binnen de specificatie te worden beschouwd.

Internationalisatie is belangrijk omdat een gebruikersinterface niet duidelijk kan communiceren wanneer haar essentiële betekenis slechts in één taal beschikbaar is. Een systeem kan technisch functioneren, maar als gebruikers de labels, instructies, bedieningselementen, instellingen, waarschuwingen, fouten of kernwerkstromen niet begrijpen, dan heeft het systeem voor die gebruikers geen betekenisvolle interface geleverd.

Deze specificatie probeert geen perfecte vertaalkwaliteit, literaire stijl, culturele aanpassing, wettelijke naleving of volledige regionale lokalisatie te meten. In plaats daarvan definieert zij de minimale meertalige basis die nodig is zodat gebruikers de essentiële delen van een systeem binnen de vereiste CatalystUI-locale-set zinvol kunnen bereiken en bedienen.

Eenvoudiger gezegd stelt I18NSPEC drie hoofdvragen:

1. Kunnen gebruikers in elke vereiste taal toegang krijgen tot de essentiële delen van het systeem?
2. Kunnen gebruikers redelijkerwijs de taal selecteren die zij begrijpen?
3. Behoudt het systeem genoeg betekenis tussen talen om bruikbaar te blijven?

> [!IMPORTANT]
>
> I18NSPEC definieert internationalisatievereisten voor verificatie. Het is geen afzonderlijke specificatie voor elke taal. Elke vereiste locale wordt tegen dezelfde specificatie gecontroleerd.

<a id="table-of-contents"></a>
## Inhoudsopgave

* [I18NSPEC](#i18nspec)

  * [Inleiding](#introduction)
  * [Inhoudsopgave](#table-of-contents)
  * [Conformiteit](#conformance)
  * [Vereiste locale-set](#required-locale-set)
  * [Gebruikersgerichte inhoud](#user-facing-content)

    * [Gebruikersgerichte inhoud](#user-facing-content-1)
    * [Essentiële gebruikersgerichte inhoud](#essential-user-facing-content)
    * [Kritieke gebruikersgerichte inhoud](#critical-user-facing-content)
    * [Niet-essentiële inhoud](#nonessential-content)
  * [Vertaaldekking](#translation-coverage)

    * [Essentiële vertaaldekking](#essential-translation-coverage)
    * [Dekkingsvereiste](#coverage-requirement)
    * [Vereiste voor kritieke inhoud](#critical-content-requirement)
  * [Taalselectie](#language-selection)

    * [Actieve locale](#active-locale)
    * [Standaardlocale](#default-locale)
    * [Mechanisme voor taalselectie](#language-selection-mechanism)
    * [Labels voor taalopties](#language-option-labels)
  * [Fallbacks en locale-equivalentie](#fallbacks-and-locale-equivalence)

    * [Fallback-locale](#fallback-locale)
    * [Fallback-gedrag](#fallback-behavior)
    * [Locale-equivalentie](#locale-equivalence)
  * [Implementatievereisten](#implementation-requirements)

    * [Stabiel vertaalmechanisme](#stable-translation-mechanism)
    * [Behoud van betekenis](#preservation-of-meaning)
    * [Richtinggevoelige talen](#direction-sensitive-languages)
    * [Locale-gevoelige waarden](#locale-sensitive-values)
  * [Verificatie](#verification)

    * [Binnen de specificatie](#within-spec)
    * [Waarschuwingen](#warnings)
    * [Mislukkingen](#failures)
    * [Geldigheid van verificatie](#verification-validity)

<a id="conformance"></a>
## Conformiteit

Een systeem wordt als conform met I18NSPEC beschouwd wanneer het voldoet aan de vereisten die in dit document zijn gedefinieerd voor elke locale in de vereiste locale-set.

Een conform systeem moet:

1. Elke locale in de vereiste locale-set ondersteunen.
2. Vertaalde inhoud leveren voor meer dan 75% van de essentiële gebruikersgerichte inhoud in elke vereiste locale.
3. Vertaalde inhoud leveren voor alle kritieke gebruikersgerichte inhoud in elke vereiste locale.
4. Een redelijk eindgebruikersmechanisme bieden voor het selecteren van de actieve locale.
5. Een stabiel vertaalmechanisme gebruiken dat passend is voor het systeem.
6. De essentiële betekenis van vertaalde gebruikersgerichte inhoud behouden.
7. Niet vertrouwen op fallback-inhoud om vertaaldekking te claimen, behalve wanneer locale-equivalentie tijdens de review wordt geaccepteerd.

Een systeem hoeft geen specifiek implementatiepatroon te gebruiken om aan deze specificatie te voldoen. Het kan resourcebestanden, vertaaltabellen, locale-bewuste routing, gecompileerde taalbronnen, statische gelokaliseerde pagina's, runtime-taalpakketten, database-ondersteunde vertalingen of een ander stabiel mechanisme gebruiken dat geschikt is voor het systeem.

Verificatie gaat over praktische gebruikerstoegang en essentiële betekenis, niet over één starre technische architectuur.

<a id="required-locale-set"></a>
## Vereiste locale-set

De vereiste locale-set definieert de talen en regionale varianten die moeten worden beoordeeld voor CatalystUI Internationalization Verification.

De huidige vereiste locale-set bevat de volgende locales:

| Locale    | Taal                     |
| --------- | ------------------------ |
| `ar-SA`   | Arabisch (Saoedi-Arabië) |
| `bn-BD`   | Bengaals (Bangladesh)    |
| `de-DE`   | Duits (Duitsland)        |
| `en-GB`   | Engels (Verenigd Koninkrijk) |
| `en-IN`   | Engels (India)           |
| `en-US`   | Engels (Verenigde Staten) |
| `es-ES`   | Spaans (Spanje)          |
| `es-MX`   | Spaans (Mexico)          |
| `fa-IR`   | Perzisch (Iran)          |
| `fr-FR`   | Frans (Frankrijk)        |
| `hi-IN`   | Hindi (India)            |
| `id-ID`   | Indonesisch (Indonesië)  |
| `it-IT`   | Italiaans (Italië)       |
| `ja-JP`   | Japans (Japan)           |
| `ko-KR`   | Koreaans (Zuid-Korea)    |
| `nl-NL`   | Nederlands (Nederland)   |
| `pl-PL`   | Pools (Polen)            |
| `pt-BR`   | Portugees (Brazilië)     |
| `ru-RU`   | Russisch (Rusland)       |
| `tl-PH`   | Tagalog (Filipijnen)     |
| `tr-TR`   | Turks (Turkije)          |
| `uk-UA`   | Oekraïens (Oekraïne)     |
| `ur-PK`   | Urdu (Pakistan)          |
| `vi-VN`   | Vietnamees (Vietnam)     |
| `zh-CN`   | Chinees (China)          |
| `zh-Hans` | Chinees (Vereenvoudigd)  |

Een systeem moet voldoende essentiële vertaalondersteuning bieden voor elke vermelde locale om als binnen de specificatie te worden beschouwd.

De vereiste locale-set is niet bedoeld om elke taal, elk dialect, elke regio of elk schrift te vertegenwoordigen. In plaats daarvan stelt zij een praktische basis vast voor brede internationale bruikbaarheid in veel gangbare technologiegerichte taalgroepen.

<a id="user-facing-content"></a>
## Gebruikersgerichte inhoud

<a id="user-facing-content-1"></a>
### Gebruikersgerichte inhoud

Gebruikersgerichte inhoud is elke inhoud die bedoeld is om door een eindgebruiker te worden waargenomen, gelezen, gehoord, geselecteerd, begrepen of gebruikt als basis voor een handeling.

Gebruikersgerichte inhoud kan onder meer omvatten:

* navigatie
* labels
* knoppen
* menu's
* bedieningselementen
* koppen
* dialogen
* instellingen
* instructies
* prompts
* waarschuwingen
* fouten
* bevestigingen
* statusberichten
* onboardingtekst
* vereiste helptekst
* bedieningselementen voor taalselectie
* inhoud van kernwerkstromen

Gebruikersgerichte inhoud hoeft niet visueel te zijn. Zij kan ook auditieve, tactiele, symbolische of multisensorische inhoud omvatten wanneer die inhoud betekenis aan de gebruiker communiceert.

<a id="essential-user-facing-content"></a>
### Essentiële gebruikersgerichte inhoud

Essentiële gebruikersgerichte inhoud is gebruikersgerichte inhoud die een gebruiker redelijkerwijs nodig heeft om het essentiële gedrag van een systeem te begrijpen, erin te navigeren, het te configureren of het te bedienen.

Essentiële gebruikersgerichte inhoud kan onder meer omvatten:

* primaire navigatie
* kernschermen en weergaven
* instellingen en voorkeuren
* gebruikersgerichte labels
* gebruikersgerichte bedieningselementen
* vereiste instructies
* belangrijke waarschuwingen
* belangrijke fouten
* essentiële prompts
* vereiste bevestigingsberichten
* bedieningselementen voor taalselectie
* kernwerkstromen die nodig zijn voor normaal gebruik

Een systeem hoeft niet elke optionele pagina, verborgen melding, intern label of niet-essentiële tekst te vertalen om aan I18NSPEC te voldoen. De inhoud die nodig is voor normaal essentieel gebruik moet echter worden vertaald volgens de vereisten van deze specificatie.

<a id="critical-user-facing-content"></a>
### Kritieke gebruikersgerichte inhoud

Kritieke gebruikersgerichte inhoud is essentiële gebruikersgerichte inhoud waarbij misverstand zinvol gebruik kan verhinderen, een ernstige fout kan veroorzaken of de gebruiker een belangrijke beslissing kan laten nemen zonder de gevolgen te begrijpen.

Kritieke gebruikersgerichte inhoud kan onder meer omvatten:

* bedieningselementen voor taalselectie
* waarschuwingen voor destructieve acties
* waarschuwingen voor accountverwijdering
* betalingsbevestigingen
* aankoopbevestigingen
* privacykeuzes
* beveiligingswaarschuwingen
* toestemmingsprompts
* vereiste veiligheidsinstructies
* vereiste installatie-instructies
* vereiste foutmeldingen
* kernnavigatie die nodig is om taalinstellingen te bereiken

Kritieke gebruikersgerichte inhoud moet voor elke vereiste locale worden vertaald.

De drempel van 75% essentiële vertaaldekking mag niet worden gebruikt om kritieke inhoud onvertaald te laten.

<a id="nonessential-content"></a>
### Niet-essentiële inhoud

Niet-essentiële inhoud is inhoud die niet redelijkerwijs nodig is voor een gebruiker om het essentiële gedrag van een systeem te begrijpen, erin te navigeren, het te configureren of het te bedienen.

Niet-essentiële inhoud kan onder meer omvatten:

* interne identificaties
* broncodenamen
* strings die alleen voor debugging zijn
* ontwikkelaarsgerichte implementatiedetails
* verborgen diagnostische tekst
* optionele marketingpagina's
* optionele ondersteuningspagina's
* niet-essentiële juridische of zakelijke tekst buiten de beoordeelde scope
* inhoud van derden die niet door het beoordeelde systeem wordt beheerd

Niet-essentiële inhoud mag worden vertaald, maar is niet vereist voor conformiteit met I18NSPEC tenzij zij noodzakelijk wordt voor essentieel begrip of gebruik door de gebruiker.

<a id="translation-coverage"></a>
## Vertaaldekking

<a id="essential-translation-coverage"></a>
### Essentiële vertaaldekking

Essentiële vertaaldekking is de hoeveelheid essentiële gebruikersgerichte inhoud die voor een specifieke locale is vertaald.

Dekking moet worden beoordeeld op basis van betekenisvolle gebruikersgerichte inhoudseenheden in plaats van bestandsgrootte, byte-aantal, regelaantal, repositorygrootte of aantal pagina's.

Bijvoorbeeld: één onvertaalde knop die een essentiële actie bestuurt kan belangrijker zijn dan een grote onvertaalde optionele alinea die normaal gebruik niet beïnvloedt.

Vertaaldekking moet worden beoordeeld op basis van de vraag of de gebruiker het essentiële systeem in de beoordeelde locale zinvol kan begrijpen en bedienen.

<a id="coverage-requirement"></a>
### Dekkingsvereiste

Een systeem voldoet aan de vertaaldekkingsvereiste voor een locale wanneer meer dan 75% van de essentiële gebruikersgerichte inhoud voor die locale is vertaald.

Een systeem voldoet aan de I18NSPEC-dekkingsvereiste wanneer het deze drempel haalt voor elke locale in de vereiste locale-set.

In een praktische review kan dit worden weergegeven als:

| Locale  | Essentiële vertaaldekking | Resultaat |
| ------- | ------------------------- | --------- |
| `en-US` | 100%                      | Geslaagd  |
| `es-ES` | 94%                       | Geslaagd  |
| `ar-SA` | 78%                       | Geslaagd  |
| `ja-JP` | 61%                       | Mislukt   |

Een locale met 75% dekking of minder voldoet niet aan de dekkingsvereiste.

Een locale met meer dan 75% dekking kan nog steeds mislukken als kritieke gebruikersgerichte inhoud onvertaald is.

<a id="critical-content-requirement"></a>
### Vereiste voor kritieke inhoud

Alle kritieke gebruikersgerichte inhoud moet voor elke vereiste locale worden vertaald.

Een systeem kan voor I18NSPEC mislukken, ook wanneer het aan de algemene dekkingsdrempel voldoet, als een of meer kritieke gebruikersgerichte inhoudsonderdelen ontbreken, onvertaald zijn, misleidend zijn of niet zinvol begrijpelijk zijn.

Een systeem mag bijvoorbeeld niet als binnen de specificatie worden beschouwd als de algemene interface vertaald is, maar de waarschuwing voor accountverwijdering, aankoopbevestiging, beveiligingswaarschuwing of taalselector onvertaald blijft.

<a id="language-selection"></a>
## Taalselectie

<a id="active-locale"></a>
### Actieve locale

De actieve locale is de locale die momenteel voor de gebruikerservaring is geselecteerd.

De actieve locale bepaalt welke vertaalde inhoud aan de gebruiker moet worden getoond, geleverd of op een andere manier gecommuniceerd.

<a id="default-locale"></a>
### Standaardlocale

De standaardlocale is de locale die wordt gebruikt wanneer de gebruiker geen actieve locale heeft geselecteerd of wanneer er geen gebruikersvoorkeur beschikbaar is.

Een systeem moet een standaardlocale definiëren.

De standaardlocale moet gedocumenteerd zijn of redelijkerwijs door de reviewer kunnen worden afgeleid.

<a id="language-selection-mechanism"></a>
### Mechanisme voor taalselectie

Een conform systeem moet een redelijke manier bieden waarop de eindgebruiker de actieve locale kan wijzigen.

Het mechanisme voor taalselectie moet beschikbaar zijn zonder dat de gebruiker het volgende hoeft te doen:

* broncode wijzigen
* ontwikkelaarstools gebruiken
* ongedocumenteerde configuratiebestanden bewerken
* onofficiële patches installeren
* vertrouwen op verborgen gedrag
* contact opnemen met ondersteuning voor gewone taalwijzigingen

Een mechanisme voor taalselectie kan worden geleverd via:

* applicatie-instellingen
* accountvoorkeuren
* een taalselector
* een opstartprompt
* browserinstellingen
* besturingssysteeminstellingen
* apparaatinstellingen
* een ander passend mechanisme dat toegankelijk is voor eindgebruikers

Het mechanisme hoeft geen specifiek ontwerppatroon te volgen. Het moet de gebruiker redelijkerwijs in staat stellen een ondersteunde taal te selecteren.

<a id="language-option-labels"></a>
### Labels voor taalopties

Wanneer taalopties worden getoond, moet een systeem elke taal identificeren op een manier die begrijpelijk is voor gebruikers die die taal spreken.

Een taaloptie kan bevatten:

* de taalnaam in die taal
* de taalnaam in de momenteel actieve taal
* de locale-code
* een regionaal label
* een schriftlabel

Bijvoorbeeld:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

De exacte opmaak kan variëren.

De bedoeling is dat gebruikers hun eigen taal kunnen herkennen, de momenteel weergegeven taalnaam waar mogelijk kunnen begrijpen en de bijbehorende locale-code kunnen identificeren.

<a id="fallbacks-and-locale-equivalence"></a>
## Fallbacks en locale-equivalentie

<a id="fallback-locale"></a>
### Fallback-locale

Een fallback-locale is een locale die wordt gebruikt wanneer vertaalde inhoud niet beschikbaar is voor de actieve locale.

Fallback-locales kunnen helpen om bruikbaarheid te behouden, maar fallback-inhoud wordt niet automatisch beschouwd als vertaalde inhoud voor de actieve locale.

Als een systeem bijvoorbeeld is ingesteld op `es-MX` maar `en-US`-tekst toont omdat de Spaanse vertaling ontbreekt, kan die Engelse tekst nuttig zijn als fallback, maar zij mag niet worden meegeteld als Spaanse vertaaldekking.

<a id="fallback-behavior"></a>
### Fallback-gedrag

Een conform systeem mag fallback-gedrag gebruiken wanneer gelokaliseerde inhoud niet beschikbaar is.

Fallback-gedrag moet gebroken, lege of misleidende uitvoer vermijden.

Fallback-gedrag mag niet worden gebruikt om onterecht vertaaldekking voor een vereiste locale te claimen.

Een systeem kan een waarschuwing of mislukking krijgen als fallback-gedrag buitensporig, verwarrend of ongedocumenteerd is, of als het ervoor zorgt dat essentiële inhoud in een vereiste locale onvertaald lijkt.

<a id="locale-equivalence"></a>
### Locale-equivalentie

Locale-equivalentie treedt op wanneer één vertaling redelijkerwijs meer dan één locale kan bedienen zonder essentieel begrip of bediening te verhinderen.

Een systeem kan bijvoorbeeld één Engelse vertaling gebruiken voor `en-US`, `en-GB` en `en-IN` als de essentiële betekenis duidelijk blijft voor gebruikers van elke locale.

Locale-equivalentie kan tijdens review worden geaccepteerd wanneer regionale verschillen klein zijn en de essentiële bruikbaarheid niet wezenlijk beïnvloeden.

Locale-equivalentie mag niet worden gebruikt wanneer een ontbrekende locale betekenisvolle verwarring zou veroorzaken, belangrijke regionale terminologie zou weglaten, essentieel gedrag zou breken of gebruikers zou verhinderen het systeem te begrijpen.

Een systeem mag bijvoorbeeld niet aannemen dat niet-verwante talen equivalent zijn omdat zij een schrijfrichting, geografische regio, schriftfamilie of brede culturele categorie delen.

Locale-equivalentie is een reviewoordeel, geen automatische regel.

<a id="implementation-requirements"></a>
## Implementatievereisten

<a id="stable-translation-mechanism"></a>
### Stabiel vertaalmechanisme

Een conform systeem moet een stabiel vertaalmechanisme gebruiken dat passend is voor het systeem dat wordt beoordeeld.

Een stabiel vertaalmechanisme moet het mogelijk maken vertaalde inhoud te onderhouden, bij te werken, te beoordelen en uit te breiden zonder te vertrouwen op kwetsbaar of ongedocumenteerd gedrag.

Een stabiel vertaalmechanisme kan onder meer omvatten:

* resourcebestanden
* vertaaltabellen
* locale-bewuste routing
* gecompileerde taalbronnen
* statische gelokaliseerde pagina's
* runtime-taalpakketten
* database-ondersteunde vertalingen
* een andere gedocumenteerde vertaalstructuur

Een systeem moet vermijden essentiële gebruikersgerichte inhoud hard te coderen op een manier die vereiste vertaalondersteuning verhindert.

<a id="preservation-of-meaning"></a>
### Behoud van betekenis

Een vertaling behoudt betekenis wanneer de gebruiker redelijkerwijs dezelfde essentiële instructie, hetzelfde label, dezelfde waarschuwing, hetzelfde bedieningselement, dezelfde instelling of dezelfde werkstroom kan begrijpen als gebruikers van de brontaal.

Een vertaling hoeft niet woord voor woord identiek te zijn aan de broninhoud.

Een vertaling mag woordvolgorde, grammatica, zinsstructuur, idioom, toon of formulering wijzigen wanneer dat nodig is om dezelfde essentiële betekenis in de doeltaal te communiceren.

Een vertaling kan voor review mislukken als zij misleidend, onvolledig, onzinnig, machinebeschadigd of betekenisvol anders is dan de broninhoud op een manier die essentieel gebruik beïnvloedt.

<a id="direction-sensitive-languages"></a>
### Richtinggevoelige talen

Sommige vereiste locales gebruiken doorgaans tekst van rechts naar links.

Een conform systeem mag niet verhinderen dat essentiële vertaalde inhoud wordt gelezen, begrepen, geselecteerd of gebruikt omdat de actieve locale een andere tekstrichting gebruikt.

Het systeem moet leesbare volgorde, interpunctiegedrag en koppeling tussen bedieningselementen behouden voor richtinggevoelige talen.

Volledige visuele afwerking, typografische kwaliteit, toegankelijkheidsgedrag en verfijning van de lay-out kunnen afzonderlijke review vereisen. Essentiële vertaalde inhoud moet echter zinvol bruikbaar blijven.

<a id="locale-sensitive-values"></a>
### Locale-gevoelige waarden

Locale-gevoelige waarden zijn waarden waarvan betekenis of leesbaarheid kan verschillen per taal, regio, schrift of cultuur.

Locale-gevoelige waarden kunnen onder meer omvatten:

* datums
* tijden
* getallen
* valuta's
* maateenheden
* meervoudsvormen
* grammaticaal geslacht
* sorteervolgorde
* adresformaten
* telefoonnummerformaten

I18NSPEC vereist geen volledige lokalisatie van elke locale-gevoelige waarde, tenzij die waarde essentieel is voor het begrijpen of bedienen van het systeem.

Wanneer locale-gevoelige waarden essentieel zijn, moet het systeem ze weergeven op een manier die gebruikers van de actieve locale redelijkerwijs kunnen begrijpen.

<a id="verification"></a>
## Verificatie

<a id="within-spec"></a>
### Binnen de specificatie

Een systeem wordt als binnen de specificatie beschouwd wanneer het CatalystUI Team het systeem heeft beoordeeld en het redelijk vindt te concluderen dat het aan I18NSPEC voldoet.

Een systeem kan binnen de specificatie zijn wanneer:

* elke vereiste locale wordt ondersteund
* meer dan 75% van de essentiële gebruikersgerichte inhoud voor elke vereiste locale is vertaald
* alle kritieke gebruikersgerichte inhoud voor elke vereiste locale is vertaald
* gebruikers redelijkerwijs de actieve locale kunnen selecteren
* fallback-gedrag niet ten onrechte vertaaldekking claimt
* locale-equivalentie, indien gebruikt, redelijk en gedocumenteerd is
* vertaalde inhoud essentiële betekenis behoudt

Een systeem kan binnen de specificatie zijn zelfs als sommige niet-essentiële inhoud onvertaald blijft.

Een systeem kan binnen de specificatie zijn zelfs als vertalingen niet perfect zijn, mits de essentiële betekenis behouden blijft en aan de vereisten van deze specificatie is voldaan.

<a id="warnings"></a>
### Waarschuwingen

Een waarschuwing kan worden afgegeven wanneer een systeem aan I18NSPEC lijkt te voldoen maar aandachtspunten bevat die moeten worden gedocumenteerd.

Waarschuwingen kunnen onder meer omvatten:

* kleine onvertaalde niet-essentiële inhoud
* inconsistente terminologie tussen locales
* onvolmaakte maar begrijpelijke vertalingen
* aanvaardbare locale-equivalentie die moet worden gedocumenteerd
* beperkt fallback-gedrag
* gedeeltelijk vertaalde optionele pagina's
* richtinggevoelige lay-outproblemen die essentieel gebruik niet verhinderen
* locale-gevoelige waarden die begrijpelijk maar niet ideaal zijn

Waarschuwingen verhinderen verificatie niet noodzakelijk.

<a id="failures"></a>
### Mislukkingen

Een mislukking treedt op wanneer een systeem niet voldoet aan een of meer vereiste voorwaarden van I18NSPEC.

Mislukkingen kunnen onder meer omvatten:

* ontbrekende ondersteuning voor een vereiste locale
* essentiële vertaaldekking van 75% of lager voor een vereiste locale
* onvertaalde kritieke gebruikersgerichte inhoud
* geen redelijk mechanisme voor taalselectie
* taalselectie die wijziging van broncode vereist
* taalselectie die ontwikkelaarstools vereist
* kapotte laadprocedure voor vertalingen
* misleidende localeclaims
* buitensporig fallback-gedrag
* fallback-inhoud die als vertaalde inhoud wordt geteld zonder geldige locale-equivalentie
* richtinggevoelige inhoud die onleesbaar of onbruikbaar is
* essentiële werkstromen die in een of meer vereiste locales niet beschikbaar zijn

Mislukkingen verhinderen verificatie totdat ze zijn opgelost.

<a id="verification-validity"></a>
### Geldigheid van verificatie

I18NSPEC-verificatie geldt alleen voor de beoordeelde staat van het systeem op het moment dat de verificatie wordt afgegeven.

Een systeem mag verificatie behouden bij latere updates zolang het de geverifieerde internationalisatiebasis behoudt.

Kleine tekstwijzigingen, toegevoegde vertalingen, verbeterde vertalingen en gewone inhoudsupdates maken verificatie niet automatisch ongeldig.

Een nieuwe review kan vereist zijn als een systeem:

* vereiste locale-ondersteuning verwijdert
* taalselectie breekt
* essentiële vertaaldekking aanzienlijk vermindert
* nieuwe essentiële werkstromen onvertaald laat
* vertaalde inhoud vervangt door fallback-inhoud
* zijn vertaalarchitectuur wijzigt op een manier die geverifieerd gedrag beïnvloedt
* grote gebruikersgerichte wijzigingen introduceert die de beoordeelde scope veranderen

Met andere woorden: het verbeteren van vertaalondersteuning is meestal prima.

Het breken van de geverifieerde meertalige basis kan review vereisen.
