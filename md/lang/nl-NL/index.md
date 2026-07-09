<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden gecontroleerd. -->

<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Welkom bij de CatalystUI Verification-documentatie voor toegankelijkheid.

**CatalystUI Verified for Accessibility** geeft aan dat een service, framework, applicatie, library of systeem is beoordeeld door het CatalystUI Team en redelijk bruikbaar blijft wanneer één van de drie primaire zintuigen die betrokken zijn bij user-interface interaction afzonderlijk niet beschikbaar is.

Voor deze verificatie identificeert CatalystUI de drie primaire toegankelijkheidszintuigen als **zicht**, **geluid** en **aanraking**. Een geverifieerd systeem moet redelijke toegang tot zijn essentiële functionaliteit behouden wanneer één van deze zintuigen niet beschikbaar is, door te vertrouwen op de overige beschikbare sensory domains.

Eenvoudiger gezegd vraagt deze verificatie of een gebruiker de essentiële delen van een systeem nog steeds betekenisvol kan begrijpen, navigeren en bedienen als die gebruiker afzonderlijk niet op zicht, geluid of aanraking kan vertrouwen.

## Purpose

Toegankelijkheid is belangrijk omdat een user interface niet volledig afhankelijk zou moeten zijn van één zintuiglijk pad wanneer dezelfde essentiële betekenis redelijkerwijs via een ander pad kan worden gecommuniceerd.

CatalystUI is ontworpen rond de trouwe verplaatsing van data tussen systemen en menselijke waarneming. Als belangrijke informatie alleen zichtbaar, alleen hoorbaar of alleen via aanraking beschikbaar is, kan het systeem onbruikbaar worden voor gebruikers die niet op dat zintuig kunnen vertrouwen. Accessibility Verification bestaat om systemen te identificeren die toegang behouden door essentiële informatie en interactie via alternatieve zintuiglijke routes voort te zetten.

Het doel is niet om elke mogelijke interaction method, elke assistive technology of elke gespecialiseerde accommodation te eisen. Het doel is om te bepalen of het essentiële systeem betekenisvol bruikbaar blijft wanneer zicht, geluid of aanraking afzonderlijk niet beschikbaar is.

## What Verification Means

Een systeem wordt **CatalystUI Verified for Accessibility** wanneer het is beoordeeld volgens de eisen in deze sectie en within spec is bevonden.

Om geverifieerd te worden, moet een systeem redelijk bruikbaar blijven in elk van de volgende gevallen:

| Unavailable Sense | Required Accessibility Behavior                                   |
| ----------------- | ----------------------------------------------------------------- |
| Zicht             | Het systeem moet redelijk bruikbaar blijven via geluid en aanraking. |
| Geluid            | Het systeem moet redelijk bruikbaar blijven via zicht en aanraking. |
| Aanraking         | Het systeem moet redelijk bruikbaar blijven via zicht en geluid. |

Een systeem hoeft geen identieke ervaringen te bieden via elk sensory path. Een non-visual experience kan langzamer zijn dan een visuele. Een sound-free experience kan captions, visual indicators of andere vervangingen vereisen. Een touch-free experience kan alternate controls, voice interaction, keyboard navigation, pointer navigation of andere non-touch methods vereisen.

Waar het om gaat, is of de essentiële functionaliteit toegankelijk, begrijpelijk en bedienbaar blijft zonder het unavailable sense te vereisen.

## Essential Functionality

Voor Accessibility Verification verwijst **essential functionality** naar de delen van een systeem die een gebruiker redelijkerwijs nodig heeft om het systeem te begrijpen, te navigeren, te configureren en te bedienen.

Essential functionality kan onder meer omvatten:

* primary navigation
* core workflows
* required controls
* important warnings
* important errors
* required confirmation messages
* account or session access
* settings and preferences
* language or accessibility configuration
* essential instructions
* user-facing status information
* elke interactie die nodig is voor normaal gebruik

Een systeem kan nog steeds within spec zijn als decoratieve, redundante, optionele of niet-essentiële functies niet via elk sensory path gelijk beschikbaar zijn. De gebruiker mag echter niet worden geblokkeerd in het gebruik van het essentiële systeem door het ontbrekende zintuig.

## Sight Unavailable

Wanneer zicht niet beschikbaar is, moet het systeem redelijk bruikbaar blijven via geluid en aanraking.

Dit kan spoken output, screen-reader-compatible structure, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions of een andere redelijke non-visual method omvatten om essentiële informatie te communiceren.

Een systeem mag niet uitsluitend vertrouwen op visual position, color, shape, animation, icons of layout wanneer die informatie nodig is om essentiële functionaliteit te begrijpen of te bedienen.

## Sound Unavailable

Wanneer geluid niet beschikbaar is, moet het systeem redelijk bruikbaar blijven via zicht en aanraking.

Dit kan captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback of een andere redelijke non-auditory method omvatten om essentiële informatie te communiceren.

Een systeem mag niet uitsluitend vertrouwen op sound effects, spoken instructions, alerts, alarms, music cues of audio-only prompts wanneer die informatie nodig is om essentiële functionaliteit te begrijpen of te bedienen.

## Touch Unavailable

Wanneer aanraking niet beschikbaar is, moet het systeem redelijk bruikbaar blijven via zicht en geluid.

Dit kan voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation of een andere redelijke methode omvatten die geen touch-based interaction of tactile perception vereist.

Een systeem mag niet uitsluitend vertrouwen op touch gestures, haptic feedback, physical texture, vibration, force, pressure of touch-only controls wanneer die interacties nodig zijn om essentiële functionaliteit te begrijpen of te bedienen.

## Additional Sensory Domains

CatalystUI herkent ook **taste** en **smell** als sensory domains. Deze domains kunnen worden meegenomen in toegankelijkheidsbeoordeling wanneer ze betekenisvol door het systeem worden gebruikt.

Taste en smell zijn **inclusive** voor verificatie, wat betekent dat ze een accessibility review kunnen versterken of ondersteunen wanneer ze betekenisvolle alternatieve toegang of extra context bieden.

Taste en smell zijn momenteel niet **exclusive** voor falen, wat betekent dat een systeem niet faalt voor Accessibility Verification alleen omdat het geen taste-based of smell-based interaction biedt.

CatalystUI Accessibility Verification richt zich vooral op de vraag of het systeem redelijk bruikbaar blijft wanneer zicht, geluid of aanraking afzonderlijk niet beschikbaar is.

## What “Within Spec” Means

Wanneer een systeem als **within spec** wordt beschouwd, betekent dit dat het CatalystUI Team het systeem handmatig heeft beoordeeld en redelijkerwijs heeft geconcludeerd dat het voldoet aan de accessibility requirements die door deze verificatiecategorie worden beschreven.

Dit vereist geen enkel strak implementation pattern. Een systeem kan accessibility requirements vervullen via native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration of een ander stabiel mechanisme dat passend is voor het systeem.

Verification gaat over het praktische vermogen van gebruikers om toegang te krijgen tot het essentiële systeem wanneer één primary sense niet beschikbaar is, niet over het gebruik van één specifieke accessibility architecture.

## What Verification Does Not Mean

CatalystUI Verified for Accessibility garandeert niet dat elke mogelijke disability, device, assistive technology, medical condition, legal requirement, regional standard of specialized use case volledig is beoordeeld.

Het verifieert ook niet automatisch internationalization, translation quality, typography, localization, regional compliance of algemene design quality, tenzij die onderwerpen zijn opgenomen in de reviewed accessibility scope.

Een systeem kan redelijk toegankelijk zijn onder CatalystUI’s accessibility model en toch afzonderlijke beoordeling nodig hebben voor legal compliance, platform certification, specialized assistive technology support of andere accessibility standards.

## Why This Verification Exists

Een user interface is alleen succesvol wanneer gebruikers deze daadwerkelijk kunnen gebruiken.

Veel systemen behandelen toegankelijkheid als een bijzaak, checklist of smalle technische eis in plaats van als fundamenteel onderdeel van human-computer interaction. CatalystUI kiest een eenvoudigere en directere benadering: als een systeem afhankelijk is van menselijke waarneming, moet het essentiële betekenis behouden wanneer één primair zintuiglijk pad niet beschikbaar is.

Accessibility Verification bestaat om systemen te herkennen die deze verantwoordelijkheid serieus nemen. Het erkent systemen die betekenisvolle alternatieve toegang bieden, essentiële functionaliteit behouden en gebruikers niet opsluiten achter één vereist zintuig.

## Verification Scope

CatalystUI Verification for Accessibility is van toepassing op het beoordeelde systeem, de service, het framework, de applicatie, library of implementatie zoals die bestond op het moment waarop verificatie werd afgegeven.

Een geverifieerd systeem biedt redelijke toegankelijkheid voor zijn essentiële functionaliteit onder de beoordeelde omstandigheden. Dit garandeert niet dat elke toekomstige pagina, feature, release, plugin, extension, third-party integration, device of platform-specific version automatisch within spec is.

Afzonderlijke producten, modules, services, major revisions of platform-specific builds kunnen hun eigen review vereisen, afhankelijk van de aangevraagde verificatiecategorie.

## Verification Validity

CatalystUI Verification geldt alleen voor de beoordeelde staat van het systeem op het moment waarop verificatie wordt afgegeven.

Een systeem kan zijn verificatie behouden bij latere updates zolang het de verified accessibility foundation bewaart. Kleine woordwijzigingen, visuele verfijningen, performance improvements en gewone content updates maken verification niet automatisch ongeldig.

Een nieuwe review kan vereist zijn als een systeem alternate access paths verwijdert, assistive-technology support breekt, essential navigation substantieel wijzigt, required accessibility settings verwijdert of interaction behavior verandert op een manier die de verified accessibility foundation beïnvloedt.

Met andere woorden: toegankelijkheid verbeteren is meestal prima. Het verified access model breken kan review vereisen.

## Verified Systems

Bekende systemen die zijn verified voor toegankelijkheid worden afzonderlijk vermeld op de passende CatalystUI Verified-pagina.
