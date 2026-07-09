<!-- Questa traduzione è stata generata da ChatGPT e deve essere revisionata da un traduttore umano. -->

<!-- Rimuovere queste righe in una pull request dopo che la traduzione è stata verificata. -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Le definizioni, i requirements e i concetti presentati qui descrivono supporto pratico per l’accessibilità e possono essere riespressi liberamente.

<a id="introduction"></a>

## Introduction

La **Accessibility Specification (A11YSPEC)** stabilisce i core concepts, la terminology e i requirements usati per valutare l’accessibility support nell’ecosistema CatalystUI. Il suo scopo è fornire uno standard chiaro per determinare se un system, service, framework, application, library o implementation resta meaningfully usable quando un primary sensory pathway non è disponibile.

Accessibility è importante perché una user interface non dovrebbe dipendere interamente da un solo sense quando lo stesso essential meaning può ragionevolmente essere comunicato attraverso un altro. Un system può essere technically functional, ma se un user non può comprendere, navigare, configurare o operare il suo essential behavior senza sight, sound o touch singolarmente, allora il system non ha fornito reasonable access per quella condizione.

Questa specification non tenta di verificare ogni possible disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard o specialized use case. Definisce invece la minimum accessibility foundation richiesta affinché gli user possano accedere e operare in modo significativo le essential portions di un system quando uno dei tre primary accessibility senses non è disponibile.

In termini più semplici, A11YSPEC pone tre domande principali:

1. Gli user possono comprendere l’essential system senza fare affidamento su sight?
2. Gli user possono comprendere l’essential system senza fare affidamento su sound?
3. Gli user possono operare l’essential system senza fare affidamento su touch?

> [!IMPORTANT]
>
> A11YSPEC definisce accessibility requirements per verification. Non sostituisce legal accessibility standards, platform certification requirements o specialized assistive-technology review. Un system può essere within A11YSPEC e richiedere comunque additional review per altri accessibility standards.

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

Un system è considerato conformant con A11YSPEC quando soddisfa i requirements definiti da questo document per ciascun required accessibility case.

Un conforming system deve:

1. Restare reasonably usable quando sight non è disponibile.
2. Restare reasonably usable quando sound non è disponibile.
3. Restare reasonably usable quando touch non è disponibile.
4. Preservare l’accesso alla essential functionality in ogni required accessibility case.
5. Preservare l’accesso a tutta la critical functionality in ogni required accessibility case.
6. Fornire reasonable alternate access paths quando essential meaning o operation altrimenti dipenderebbero dall’unavailable sense.
7. Usare uno stable accessibility mechanism appropriato al reviewed system.
8. Evitare di fare affidamento esclusivo su un primary sense per essential functionality.

Un system non deve fornire esperienze identiche in ogni sensory path. Un’esperienza non visuale può essere più lenta di una visuale. Un’esperienza sound-free può richiedere captions, visual indicators o haptic confirmation. Un’esperienza touch-free può richiedere keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction o un altro metodo non-touch.

Verification riguarda l’accesso pratico alla essential functionality, non una presentation identica.

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

Per A11YSPEC, i tre primary accessibility senses sono **sight**, **sound** e **touch**.

Questi senses sono primary perché sono i sensory pathways più comuni coinvolti nella user-interface interaction. Un system può fornire output tramite sight, sound o touch, e può ricevere interaction tramite touch, motion, voice, keyboard input, pointer input, switch input o un altro input path disponibile.

<a id="sight"></a>

### Sight

Sight è il visual sensory pathway attraverso cui un user percepisce visual output.

Sight può essere coinvolto nel percepire:

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

Un system dipende da sight quando essential meaning o operation richiede all’user di percepire visivamente information.

<a id="sound"></a>

### Sound

Sound è l’auditory sensory pathway attraverso cui un user percepisce audio output.

Sound può essere coinvolto nel percepire:

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

Un system dipende da sound quando essential meaning o operation richiede all’user di sentire information.

<a id="touch"></a>

### Touch

Touch è il tactile sensory pathway attraverso cui un user percepisce physical o haptic output, e il physical interaction pathway con cui un user può operare controls tramite direct contact, pressure, gesture o movement.

Touch può essere coinvolto nel percepire o eseguire:

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

Un system dipende da touch quando essential meaning o operation richiede tactile perception o touch-based interaction senza un reasonable alternate input o output path.

<a id="additional-sensory-domains"></a>

### Additional Sensory Domains

CatalystUI riconosce anche **taste** e **smell** come sensory domains.

Taste e smell possono essere considerati durante l’accessibility review quando sono usati in modo significativo dal system. Questi senses sono inclusive per verification, cioè possono rafforzare o supportare un’accessibility review quando forniscono meaningful alternate access o additional context.

Taste e smell non sono attualmente exclusive per failure. Un system non fallisce A11YSPEC semplicemente perché non fornisce taste-based o smell-based interaction.

A11YSPEC riguarda principalmente se il system resta reasonably usable quando sight, sound o touch non è disponibile singolarmente.

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

Un conforming system deve essere esaminato rispetto a ciascun required accessibility case.

| Unavailable Sense | Required Accessibility Behavior |
| ----------------- | ----------------------------------------------------------------- |
| Sight             | Il system deve restare reasonably usable tramite sound e touch. |
| Sound             | Il system deve restare reasonably usable tramite sight e touch. |
| Touch             | Il system deve restare reasonably usable tramite sight e sound. |

Ogni case viene esaminato individualmente.

Un system non è tenuto a restare fully usable quando più primary senses non sono disponibili nello stesso momento, salvo che quella condizione sia inclusa nel reviewed scope.

Un system non è tenuto a fornire ogni possible accommodation. Deve fornire reasonable access alla essential functionality in ogni required accessibility case.

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality è qualsiasi behavior, content, control, output, input, workflow o configuration di cui un user ha ragionevolmente bisogno per comprendere, navigare, configurare o operare l’essential behavior di un system.

Essential functionality può includere:

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
* qualsiasi interaction richiesta per l’uso normale

Un system non deve rendere ogni decorative, optional, redundant o nonessential feature ugualmente disponibile attraverso ogni sensory path. Tuttavia, l’user non deve essere bloccato dall’uso dell’essential system a causa dell’unavailable sense.

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality è essential functionality la cui perdita di accesso può impedire meaningful use, creare un serious error o portare l’user a prendere un important decision senza comprenderne la consequence.

Critical functionality può includere:

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
* core navigation richiesta per raggiungere accessibility settings

Critical functionality deve restare accessible in ogni required accessibility case.

Un system può fallire A11YSPEC se critical functionality dipende esclusivamente dall’unavailable sense.

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality è functionality che non è ragionevolmente richiesta affinché un user comprenda, navighi, configuri o operi l’essential behavior di un system.

Nonessential functionality può includere:

* decorative animation
* optional effects
* cosmetic visual polish
* nonessential sound effects
* redundant haptic effects
* optional marketing content
* optional tutorial content
* hidden diagnostic behavior
* developer-facing controls
* experimental features fuori dal reviewed scope

Nonessential functionality può essere inaccessible in uno o più accessibility cases senza causare automaticamente failure. Tuttavia, non deve essere confusa con essential functionality solo perché è scomoda da supportare.

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

Un system soddisfa l’essential access requirement quando essential functionality resta reasonably understandable, navigable, configurable e operable in ogni required accessibility case.

L’essential experience non deve essere identica in tutti i senses.

L’essential experience deve restare meaningfully usable.

<a id="critical-access-requirement"></a>

### Critical Access Requirement

Un system soddisfa il critical access requirement quando tutta la critical functionality resta accessible in ogni required accessibility case.

Critical functionality non deve essere nascosta dietro un solo required sensory pathway.

Per esempio, un system non dovrebbe fornire un’interfaccia accessible per ordinary use lasciando account deletion warnings, payment confirmations, privacy decisions o accessibility settings dipendenti solo da sight, sound o touch.

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

Un system soddisfa l’alternate access requirement quando essential meaning o operation forniti tramite un primary sense sono anche reasonably available tramite un altro sensory o interaction path quando quel sense non è disponibile.

Alternate access può essere fornito tramite:

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
* un altro stable mechanism appropriato al system

L’alternate path non deve corrispondere perfettamente all’original path. Deve preservare essential meaning e operation.

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

Un system non deve richiedere un primary sense come unico path verso essential functionality.

Un system può usare sight, sound o touch come primary experience. Tuttavia, quando quel sense non è disponibile, l’user deve comunque avere un modo ragionevole per comprendere e operare l’essential system attraverso i sensory paths rimanenti.

Un system può fallire review quando essential information o interaction è disponibile solo tramite:

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

Quando sight non è disponibile, il system deve restare reasonably usable tramite sound e touch.

Questo significa che essential visual information deve avere un meaningful non-visual access path.

Un system può soddisfare questo requirement tramite:

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

Un system non dovrebbe fare affidamento esclusivamente su:

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

quando tali informazioni sono richieste per comprendere o operare essential functionality.

Un system può fallire questo case se un user non può ragionevolmente navigare, comprendere o operare l’essential system senza sight.

<a id="sound-unavailable"></a>

## Sound Unavailable

Quando sound non è disponibile, il system deve restare reasonably usable tramite sight e touch.

Questo significa che essential auditory information deve avere un meaningful non-auditory access path.

Un system può soddisfare questo requirement tramite:

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

Un system non dovrebbe fare affidamento esclusivamente su:

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

quando tali informazioni sono richieste per comprendere o operare essential functionality.

Un system può fallire questo case se un user non può ragionevolmente navigare, comprendere o operare l’essential system senza sound.

<a id="touch-unavailable"></a>

## Touch Unavailable

Quando touch non è disponibile, il system deve restare reasonably usable tramite sight e sound.

Questo significa che essential tactile information e touch-based operation devono avere un meaningful non-touch access path.

Un system può soddisfare questo requirement tramite:

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

Un system non dovrebbe fare affidamento esclusivamente su:

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

quando quell’interaction è richiesta per comprendere o operare essential functionality.

Un system può fallire questo case se un user non può ragionevolmente navigare, comprendere o operare l’essential system senza touch.

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

Un conforming system deve usare uno stable accessibility mechanism appropriato al system in review.

Uno stable accessibility mechanism dovrebbe permettere di mantenere, aggiornare, esaminare ed estendere accessibility behavior senza fare affidamento su behavior fragile o non documentati.

Uno stable accessibility mechanism può includere:

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
* un’altra stable structure appropriata al system

Un system dovrebbe evitare di implementare essential functionality in modo da impedire reasonable alternate access.

<a id="semantic-structure"></a>

### Semantic Structure

Un conforming system dovrebbe fornire semantic structure quando presenta meaningful content o controls.

Semantic structure può includere:

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

Semantic structure è particolarmente importante quando sight non è disponibile, perché assistive technologies spesso dipendono da semantic information per comunicare visual interfaces tramite non-visual output.

Un system può fallire review se essential controls o content non possono essere compresi perché structure, labels o relationships non sono disponibili attraverso alternate access paths.

<a id="alternate-output"></a>

### Alternate Output

Un conforming system deve fornire reasonable alternate output quando essential meaning altrimenti dipenderebbe dall’unavailable sense.

Alternate output può includere:

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

Alternate output deve preservare essential meaning.

<a id="alternate-input"></a>

### Alternate Input

Un conforming system deve fornire reasonable alternate input quando essential operation altrimenti dipenderebbe solo da touch.

Alternate input può includere:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input non deve essere il metodo input più veloce o più comodo. Deve essere sufficiente per essential operation.

<a id="accessible-feedback"></a>

### Accessible Feedback

Un conforming system deve fornire accessible feedback per essential actions.

Accessible feedback può includere:

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

Feedback non deve fare affidamento esclusivamente sull’unavailable sense nel related accessibility case.

Per esempio, un sound-only success chime non è sufficiente quando sound non è disponibile. Uno stato di errore color-only non è sufficiente quando sight non è disponibile. Una vibration-only confirmation non è sufficiente quando touch non è disponibile.

<a id="accessible-configuration"></a>

### Accessible Configuration

Un conforming system deve consentire agli user di raggiungere e usare required accessibility settings tramite gli stessi accessibility requirements definiti da questa specification.

Accessibility settings non devono essere nascoste dietro un inaccessible path.

Per esempio, una screen-reader-compatible mode non è sufficiente se l’user deve prima navigare un unlabeled visual-only menu per abilitarla.

Un system può fallire review se la sua accessibility configuration non può essere raggiunta o operata nella condition che dovrebbe supportare.

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

Un system è considerato within spec quando il CatalystUI Team ha esaminato il system e ha ritenuto ragionevole concludere che soddisfi A11YSPEC.

Un system può essere within spec quando:

* sight-unavailable use remains reasonably supported
* sound-unavailable use remains reasonably supported
* touch-unavailable use remains reasonably supported
* essential functionality remains accessible in each required case
* critical functionality remains accessible in each required case
* alternate access paths preserve essential meaning and operation
* accessibility settings, when present, can be reached and used accessibly
* the system does not trap essential functionality behind one required sense
* the system uses a stable accessibility mechanism appropriate to its design

Un system può essere within spec anche se le esperienze non sono identiche in tutti i sensory paths.

Un system può essere within spec anche se alcune nonessential functionality non sono ugualmente disponibili in ogni required accessibility case.

<a id="warnings"></a>

### Warnings

Una warning può essere emessa quando un system sembra soddisfare A11YSPEC ma contiene concerns che dovrebbero essere documentati.

Warnings possono includere:

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

Warnings non impediscono necessariamente verification.

<a id="failures"></a>

### Failures

Un failure si verifica quando un system non soddisfa una o più required conditions di A11YSPEC.

Failures possono includere:

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

Failures impediscono verification finché non vengono risolti.

<a id="verification-validity"></a>

### Verification Validity

A11YSPEC verification si applica solo al reviewed state del system al momento dell’emissione della verification.

Un system può mantenere verification negli update successivi finché preserva la verified accessibility foundation.

Minor wording changes, visual refinements, performance improvements, added accessibility features e ordinary content updates non invalidano automaticamente verification.

Una nuova review può essere richiesta se un system:

* removes alternate access paths
* breaks assistive-technology support
* substantially changes essential navigation
* removes required accessibility settings
* changes interaction behavior in a way that affects verified accessibility
* introduces new essential workflows without accessible alternatives
* makes previously accessible critical functionality inaccessible
* replaces accessible behavior with single-sense-dependent behavior

In altre parole, migliorare accessibility di solito va bene.

Rompere il verified access model può richiedere review.
