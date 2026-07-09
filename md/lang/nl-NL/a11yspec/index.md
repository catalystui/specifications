<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden gecontroleerd. -->

<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> De definities, eisen en concepten die hierin worden gepresenteerd beschrijven praktische toegankelijkheidsondersteuning en mogen vrij opnieuw worden uitgedrukt.

<a id="introduction"></a>

## Introduction

De **Accessibility Specification (A11YSPEC)** stelt de kernconcepten, terminologie en eisen vast die worden gebruikt om accessibility support binnen het CatalystUI ecosystem te evalueren. Het doel is een duidelijke standaard te bieden om te bepalen of een system, service, framework, application, library of implementation betekenisvol bruikbaar blijft wanneer één primary sensory pathway niet beschikbaar is.

Toegankelijkheid is belangrijk omdat een user interface niet volledig afhankelijk zou moeten zijn van één sense wanneer dezelfde essential meaning redelijkerwijs via een ander sense kan worden gecommuniceerd. Een systeem kan technisch functioneel zijn, maar als een user het essentiële gedrag niet kan begrijpen, navigeren, configureren of bedienen zonder afzonderlijk sight, sound of touch, dan heeft het systeem geen reasonable access voor die condition geboden.

Deze specification probeert niet elke mogelijke disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard of specialized use case te verifiëren. In plaats daarvan definieert het de minimale accessibility foundation die nodig is zodat users de essentiële delen van een systeem betekenisvol kunnen benaderen en bedienen wanneer één van de drie primary accessibility senses niet beschikbaar is.

In eenvoudiger termen stelt A11YSPEC drie hoofdvragen:

1. Kunnen users het essentiële systeem begrijpen zonder op sight te vertrouwen?
2. Kunnen users het essentiële systeem begrijpen zonder op sound te vertrouwen?
3. Kunnen users het essentiële systeem bedienen zonder op touch te vertrouwen?

> [!IMPORTANT]
>
> A11YSPEC definieert accessibility requirements voor verification. Het is geen vervanging voor legal accessibility standards, platform certification requirements of specialized assistive-technology review. Een systeem kan binnen A11YSPEC vallen en toch aanvullende review nodig hebben voor andere accessibility standards.

<a id="table-of-contents"></a>

## Table of Contents

- [A11YSPEC](#a11yspec)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Conformance](#conformance)
  - [Primary Accessibility Senses](#primary-accessibility-senses)
    - [Sight](#sight)
    - [Sound](#sound)
    - [Touch](#touch)
    - [Additional Sensory Domains](#additional-sensory-domains)
  - [Required Accessibility Cases](#required-accessibility-cases)
  - [Essential Functionality](#essential-functionality)
    - [Essential Functionality](#essential-functionality-1)
    - [Critical Functionality](#critical-functionality)
    - [Nonessential Functionality](#nonessential-functionality)
  - [Accessibility Requirements](#accessibility-requirements)
    - [Essential Access Requirement](#essential-access-requirement)
    - [Critical Access Requirement](#critical-access-requirement)
    - [Alternate Access Requirement](#alternate-access-requirement)
    - [No Single-Sense Dependency](#no-single-sense-dependency)
  - [Sight Unavailable](#sight-unavailable)
  - [Sound Unavailable](#sound-unavailable)
  - [Touch Unavailable](#touch-unavailable)
  - [Implementation Requirements](#implementation-requirements)
    - [Stable Accessibility Mechanism](#stable-accessibility-mechanism)
    - [Semantic Structure](#semantic-structure)
    - [Alternate Output](#alternate-output)
    - [Alternate Input](#alternate-input)
    - [Accessible Feedback](#accessible-feedback)
    - [Accessible Configuration](#accessible-configuration)
  - [Verification](#verification)
    - [Within Spec](#within-spec)
    - [Warnings](#warnings)
    - [Failures](#failures)
    - [Verification Validity](#verification-validity)

<a id="conformance"></a>

## Conformance

Een systeem wordt als conformant met A11YSPEC beschouwd wanneer het voldoet aan de eisen die dit document definieert voor elke required accessibility case.

Een conforming system moet:

1. Redelijk bruikbaar blijven wanneer sight niet beschikbaar is.
2. Redelijk bruikbaar blijven wanneer sound niet beschikbaar is.
3. Redelijk bruikbaar blijven wanneer touch niet beschikbaar is.
4. Toegang tot essential functionality behouden in elke required accessibility case.
5. Toegang tot alle critical functionality behouden in elke required accessibility case.
6. Reasonable alternate access paths bieden wanneer essential meaning of operation anders afhankelijk zou zijn van het unavailable sense.
7. Een stable accessibility mechanism gebruiken dat passend is voor het reviewed system.
8. Vermijden dat essential functionality uitsluitend afhankelijk is van één primary sense.

Een systeem hoeft geen identieke ervaringen te bieden via elk sensory path. Een non-visual experience kan langzamer zijn dan een visuele. Een sound-free experience kan captions, visual indicators of haptic confirmation vereisen. Een touch-free experience kan keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction of een andere non-touch method vereisen.

Verification gaat over practical access tot essential functionality, niet over identieke presentatie.

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

Voor A11YSPEC zijn de drie primary accessibility senses **sight**, **sound** en **touch**.

Deze senses zijn primary omdat ze de meest voorkomende sensory pathways zijn in user-interface interaction. Een system kan output bieden via sight, sound of touch, en kan interaction ontvangen via touch, motion, voice, keyboard input, pointer input, switch input of een ander available input path.

<a id="sight"></a>

### Sight

Sight is het visuele sensory pathway waardoor een user visual output waarneemt.

Sight kan betrokken zijn bij het waarnemen van:

* text
* color
* shape
* position
* layout
* animation
* icons
* images
* video
* visual warnings
* visual status indicators
* visible controls

Een system is afhankelijk van sight wanneer essential meaning of operation vereist dat de user information visueel waarneemt.

<a id="sound"></a>

### Sound

Sound is het auditieve sensory pathway waardoor een user audio output waarneemt.

Sound kan betrokken zijn bij het waarnemen van:

* spoken instructions
* alerts
* alarms
* music cues
* sound effects
* audio prompts
* audio descriptions
* auditory status indicators
* spoken confirmation
* spoken navigation

Een system is afhankelijk van sound wanneer essential meaning of operation vereist dat de user information hoort.

<a id="touch"></a>

### Touch

Touch is het tactiele sensory pathway waardoor een user physical of haptic output waarneemt, en het fysieke interaction pathway waardoor een user controls kan bedienen via direct contact, pressure, gesture of movement.

Touch kan betrokken zijn bij het waarnemen of uitvoeren van:

* touch gestures
* haptic feedback
* vibration
* physical texture
* force
* pressure
* touch-only controls
* physical buttons
* direct manipulation
* touchscreen interaction
* drag actions
* swipe actions

Een system is afhankelijk van touch wanneer essential meaning of operation tactile perception of touch-based interaction vereist zonder een reasonable alternate input or output path.

<a id="additional-sensory-domains"></a>

### Additional Sensory Domains

CatalystUI herkent ook **taste** en **smell** als sensory domains.

Taste en smell kunnen worden overwogen tijdens accessibility review wanneer ze betekenisvol door het system worden gebruikt. Deze senses zijn inclusive voor verification, wat betekent dat ze een accessibility review kunnen versterken of ondersteunen wanneer ze meaningful alternate access of additional context bieden.

Taste en smell zijn momenteel niet exclusive voor failure. Een system faalt A11YSPEC niet alleen omdat het geen taste-based of smell-based interaction biedt.

A11YSPEC richt zich vooral op de vraag of het system reasonably usable blijft wanneer sight, sound of touch afzonderlijk unavailable is.

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

Een conforming system moet worden reviewed tegen elke required accessibility case.

| Unavailable Sense | Required Accessibility Behavior                                   |
| ----------------- | ----------------------------------------------------------------- |
| Sight             | Het systeem moet redelijk bruikbaar blijven via sound en touch. |
| Sound             | Het systeem moet redelijk bruikbaar blijven via sight en touch. |
| Touch             | Het systeem moet redelijk bruikbaar blijven via sight en sound. |

Elke case wordt afzonderlijk reviewed.

Een system hoeft niet volledig bruikbaar te blijven wanneer meerdere primary senses tegelijk unavailable zijn, tenzij die condition is opgenomen in de reviewed scope.

Een system hoeft niet elke possible accommodation te bieden. Het moet reasonable access tot essential functionality bieden onder elke required accessibility case.

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality is elk behavior, content, control, output, input, workflow of configuration die een user redelijkerwijs nodig heeft om het essential behavior van een system te begrijpen, te navigeren, te configureren of te bedienen.

Essential functionality kan onder meer omvatten:

* primary navigation
* core workflows
* required controls
* important warnings
* important errors
* required confirmation messages
* account or session access
* settings and preferences
* language configuration
* accessibility configuration
* essential instructions
* user-facing status information
* elke interaction die nodig is voor normal use

Een system hoeft niet elke decorative, optional, redundant of nonessential feature via elk sensory path gelijk beschikbaar te maken. De user mag echter niet worden geblokkeerd van het gebruik van het essential system door het unavailable sense.

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality is essential functionality waarbij verlies van access meaningful use kan voorkomen, een serious error kan veroorzaken of ertoe kan leiden dat de user een belangrijke beslissing neemt zonder de consequentie te begrijpen.

Critical functionality kan onder meer omvatten:

* accessibility settings
* language settings
* destructive action warnings
* account deletion warnings
* payment confirmations
* purchase confirmations
* privacy choices
* security warnings
* consent prompts
* required safety instructions
* required setup instructions
* required error messages
* session access
* emergency stop or cancel behavior
* core navigation die nodig is om accessibility settings te bereiken

Critical functionality moet accessible blijven in elke required accessibility case.

Een system kan A11YSPEC falen als critical functionality uitsluitend afhankelijk is van het unavailable sense.

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality is functionality die niet redelijkerwijs nodig is voor een user om het essential behavior van een system te begrijpen, te navigeren, te configureren of te bedienen.

Nonessential functionality kan onder meer omvatten:

* decorative animation
* optional effects
* cosmetic visual polish
* nonessential sound effects
* redundant haptic effects
* optional marketing content
* optional tutorial content
* hidden diagnostic behavior
* developer-facing controls
* experimental features outside the reviewed scope

Nonessential functionality kan inaccessible zijn onder één of meer accessibility cases zonder automatisch failure te veroorzaken. Nonessential functionality mag echter niet worden verward met essential functionality alleen omdat ondersteuning ervan lastig is.

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

Een system voldoet aan de essential access requirement wanneer essential functionality reasonably understandable, navigable, configurable en operable blijft in elke required accessibility case.

De essential experience hoeft niet identiek te zijn over alle senses.

De essential experience moet meaningfully usable blijven.

<a id="critical-access-requirement"></a>

### Critical Access Requirement

Een system voldoet aan de critical access requirement wanneer alle critical functionality accessible blijft in elke required accessibility case.

Critical functionality mag niet verborgen zijn achter één required sensory pathway.

Een system moet bijvoorbeeld niet een accessible interface bieden voor ordinary use terwijl account deletion warnings, payment confirmations, privacy decisions of accessibility settings afhankelijk blijven van alleen sight, sound of touch.

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

Een system voldoet aan de alternate access requirement wanneer essential meaning of operation die via één primary sense wordt geboden ook redelijk beschikbaar is via een ander sensory of interaction path wanneer dat sense unavailable is.

Alternate access kan worden geboden via:

* text alternatives
* captions
* transcripts
* spoken output
* screen-reader-compatible structure
* keyboard navigation
* pointer alternatives
* switch-compatible interaction
* voice control
* visual alerts
* haptic feedback
* focus indicators
* semantic structure
* accessible platform APIs
* device-level accessibility integration
* another stable mechanism appropriate to the system

Het alternate path hoeft niet perfect overeen te komen met het original path. Het moet essential meaning en operation behouden.

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

Een system mag niet één primary sense vereisen als enige path naar essential functionality.

Een system mag sight, sound of touch gebruiken als primary experience. Wanneer dat sense unavailable is, moet de user echter nog steeds een redelijke manier hebben om het essential system te begrijpen en te bedienen via de remaining sensory paths.

Een system kan review falen wanneer essential information of interaction alleen beschikbaar is via:

* visual-only meaning
* audio-only meaning
* touch-only meaning
* gesture-only operation
* haptic-only confirmation
* color-only status
* sound-only alerts
* layout-only instructions
* physical texture-only guidance

<a id="sight-unavailable"></a>

## Sight Unavailable

Wanneer sight unavailable is, moet het system reasonably usable blijven via sound en touch.

Dit betekent dat essential visual information een meaningful non-visual access path moet hebben.

Een system kan aan deze requirement voldoen via:

* spoken output
* screen-reader-compatible structure
* meaningful focus order
* keyboard access
* tactile controls
* haptic confirmation
* audio descriptions
* text-to-speech support
* semantic labels
* accessible names
* accessible roles
* accessible state information
* another reasonable non-visual mechanism

Een system mag niet uitsluitend vertrouwen op:

* visual position
* color
* shape
* animation
* icons
* layout
* images
* video
* visual-only warnings
* visual-only status indicators

wanneer die information nodig is om essential functionality te begrijpen of te bedienen.

Een system kan deze case falen als een user het essential system niet redelijk kan navigeren, begrijpen of bedienen zonder sight.

<a id="sound-unavailable"></a>

## Sound Unavailable

Wanneer sound unavailable is, moet het system reasonably usable blijven via sight en touch.

Dit betekent dat essential auditory information een meaningful non-auditory access path moet hebben.

Een system kan aan deze requirement voldoen via:

* captions
* transcripts
* visual alerts
* text equivalents
* progress indicators
* visible status messages
* haptic feedback
* visual confirmation
* written instructions
* symbolic indicators
* another reasonable non-auditory mechanism

Een system mag niet uitsluitend vertrouwen op:

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

wanneer die information nodig is om essential functionality te begrijpen of te bedienen.

Een system kan deze case falen als een user het essential system niet redelijk kan navigeren, begrijpen of bedienen zonder sound.

<a id="touch-unavailable"></a>

## Touch Unavailable

Wanneer touch unavailable is, moet het system reasonably usable blijven via sight en sound.

Dit betekent dat essential tactile information en touch-based operation een meaningful non-touch access path moeten hebben.

Een system kan aan deze requirement voldoen via:

* keyboard navigation
* pointer alternatives
* voice control
* remote controls
* gaze-compatible interaction
* switch-compatible interaction
* spoken prompts
* visual confirmation
* accessible shortcut systems
* command palettes
* focus-based interaction
* another reasonable non-touch mechanism

Een system mag niet uitsluitend vertrouwen op:

* touch gestures
* haptic feedback
* physical texture
* vibration
* force
* pressure
* touch-only controls
* drag-only behavior
* swipe-only behavior
* pinch-only behavior
* direct manipulation without alternatives

wanneer die interaction nodig is om essential functionality te begrijpen of te bedienen.

Een system kan deze case falen als een user het essential system niet redelijk kan navigeren, begrijpen of bedienen zonder touch.

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

Een conforming system moet een stable accessibility mechanism gebruiken dat passend is voor het system dat wordt reviewed.

Een stable accessibility mechanism moet toelaten dat accessibility behavior wordt onderhouden, bijgewerkt, reviewed en uitgebreid zonder te vertrouwen op fragile of undocumented behavior.

Een stable accessibility mechanism kan onder meer omvatten:

* native platform accessibility APIs
* semantic structure
* alternate input methods
* alternate output methods
* assistive-technology support
* built-in accessibility settings
* device-level integration
* documented keyboard interaction
* documented voice interaction
* documented non-visual interaction
* another stable structure appropriate to the system

Een system moet vermijden essential functionality te implementeren op een manier die reasonable alternate access voorkomt.

<a id="semantic-structure"></a>

### Semantic Structure

Een conforming system zou semantic structure moeten bieden wanneer het system meaningful content of controls presenteert.

Semantic structure kan onder meer omvatten:

* names
* roles
* states
* relationships
* ordering
* grouping
* labels
* descriptions
* focus behavior
* control purpose
* content hierarchy

Semantic structure is vooral belangrijk wanneer sight unavailable is, omdat assistive technologies vaak afhankelijk zijn van semantic information om visual interfaces via non-visual output te communiceren.

Een system kan review falen als essential controls of content niet kunnen worden begrepen omdat hun structure, labels of relationships niet beschikbaar zijn via alternate access paths.

<a id="alternate-output"></a>

### Alternate Output

Een conforming system moet reasonable alternate output bieden wanneer essential meaning anders afhankelijk zou zijn van het unavailable sense.

Alternate output kan onder meer omvatten:

* visual output for auditory information
* auditory output for visual information
* tactile output for visual or auditory information
* text equivalents
* captions
* transcripts
* spoken descriptions
* visible status messages
* haptic confirmation
* another appropriate output path

Alternate output moet essential meaning behouden.

<a id="alternate-input"></a>

### Alternate Input

Een conforming system moet reasonable alternate input bieden wanneer essential operation anders afhankelijk zou zijn van touch alone.

Alternate input kan onder meer omvatten:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input hoeft niet de snelste of meest handige input method te zijn. Het moet voldoende zijn voor essential operation.

<a id="accessible-feedback"></a>

### Accessible Feedback

Een conforming system moet accessible feedback bieden voor essential actions.

Accessible feedback kan onder meer omvatten:

* confirmation that an action occurred
* indication that an action failed
* progress information
* validation messages
* warning messages
* error messages
* completion status
* current selection
* current focus
* current mode
* current system state

Feedback mag in de gerelateerde accessibility case niet uitsluitend vertrouwen op het unavailable sense.

Bijvoorbeeld: een sound-only success chime is niet voldoende wanneer sound unavailable is. Een color-only error state is niet voldoende wanneer sight unavailable is. Een vibration-only confirmation is niet voldoende wanneer touch unavailable is.

<a id="accessible-configuration"></a>

### Accessible Configuration

Een conforming system moet users in staat stellen required accessibility settings te bereiken en te gebruiken via dezelfde accessibility requirements die door deze specification worden gedefinieerd.

Accessibility settings mogen niet verborgen zijn achter een inaccessible path.

Een screen-reader-compatible mode is bijvoorbeeld niet voldoende als de user eerst een unlabeled visual-only menu moet navigeren om het in te schakelen.

Een system kan review falen als zijn accessibility configuration niet kan worden bereikt of bediend in de condition die het bedoeld is te ondersteunen.

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

Een system wordt considered within spec wanneer het CatalystUI Team het system heeft reviewed en redelijkerwijs heeft geconcludeerd dat het A11YSPEC satisfies.

Een system kan within spec zijn wanneer:

* sight-unavailable use reasonably supported blijft
* sound-unavailable use reasonably supported blijft
* touch-unavailable use reasonably supported blijft
* essential functionality accessible blijft in elke required case
* critical functionality accessible blijft in elke required case
* alternate access paths essential meaning en operation behouden
* accessibility settings, wanneer aanwezig, toegankelijk kunnen worden bereikt en gebruikt
* het system essential functionality niet achter één required sense opsluit
* het system een stable accessibility mechanism gebruikt dat passend is voor zijn design

Een system kan within spec zijn ook als experiences niet identiek zijn over alle sensory paths.

Een system kan within spec zijn ook als sommige nonessential functionality niet gelijk beschikbaar is in elke required accessibility case.

<a id="warnings"></a>

### Warnings

Een warning kan worden issued wanneer een system A11YSPEC lijkt te satisfy maar concerns bevat die documented moeten worden.

Warnings kunnen onder meer omvatten:

* minor nonessential content unavailable in one accessibility case
* slower but usable alternate access paths
* imperfect but understandable captions or transcripts
* limited but functional keyboard navigation
* limited but functional screen-reader support
* minor focus-order concerns that do not block essential use
* redundant visual, auditory, or tactile cues missing from one path
* accessibility settings that are usable but difficult to find
* assistive-technology support that works but could be clearer
* optional workflows that are not equally accessible

Warnings voorkomen verification niet noodzakelijk.

<a id="failures"></a>

### Failures

Een failure treedt op wanneer een system niet voldoet aan één of meer required conditions van A11YSPEC.

Failures kunnen onder meer omvatten:

* essential functionality unavailable when sight is unavailable
* essential functionality unavailable when sound is unavailable
* essential functionality unavailable when touch is unavailable
* critical functionality unavailable in any required accessibility case
* no reasonable alternate access path for essential visual information
* no reasonable alternate access path for essential auditory information
* no reasonable alternate access path for essential touch-based operation
* accessibility settings unreachable under the condition they are meant to support
* controls without meaningful labels or structure when required for non-visual use
* sound-only warnings with no visual, tactile, or text equivalent
* color-only status with no non-visual equivalent
* gesture-only operation with no keyboard, pointer, voice, switch, or other alternative
* haptic-only confirmation with no visual or auditory equivalent
* broken assistive-technology support for essential workflows
* major navigation traps
* essential workflows that cannot be completed without the unavailable sense

Failures voorkomen verification totdat ze zijn opgelost.

<a id="verification-validity"></a>

### Verification Validity

A11YSPEC verification is alleen van toepassing op de reviewed state van het system op het moment dat verification wordt issued.

Een system kan verification behouden bij latere updates zolang het de verified accessibility foundation behoudt.

Minor wording changes, visual refinements, performance improvements, added accessibility features en ordinary content updates maken verification niet automatisch ongeldig.

Een nieuwe review kan vereist zijn als een system:

* alternate access paths verwijdert
* assistive-technology support breekt
* essential navigation substantieel wijzigt
* required accessibility settings verwijdert
* interaction behavior verandert op een manier die verified accessibility beïnvloedt
* new essential workflows introduceert zonder accessible alternatives
* previously accessible critical functionality inaccessible maakt
* accessible behavior vervangt door single-sense-dependent behavior

Met andere woorden: toegankelijkheid verbeteren is meestal prima.

Het verified access model breken kan review vereisen.
