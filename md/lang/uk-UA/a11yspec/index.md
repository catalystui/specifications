<!-- Цей переклад створено ChatGPT, і його має перевірити людина-перекладач. -->

<!-- Видаліть ці рядки в pull request після перевірки перекладу. -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Definitions, requirements і concepts, представлені тут, описують practical accessibility support і можуть бути вільно переказані.

<a id="introduction"></a>

## Вступ

**Accessibility Specification (A11YSPEC)** встановлює core concepts, terminology і requirements, які використовуються для оцінювання accessibility support в ecosystem CatalystUI. Її мета — надати clear standard для визначення, чи system, service, framework, application, library або implementation залишається meaningfully usable, коли один primary sensory pathway unavailable.

Accessibility важлива, тому що user interface не має повністю залежати від одного чуття, коли той самий essential meaning можна reasonable communicated through another. System може бути technically functional, але якщо user не може understand, navigate, configure або operate its essential behavior without sight, sound, or touch individually, тоді system failed to provide reasonable access for that condition.

Ця specification не намагається verify кожну possible disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard або specialized use case. Instead, вона defines minimum accessibility foundation required for users to meaningfully access and operate essential portions of a system, коли один із трьох primary accessibility senses unavailable.

Простіше кажучи, A11YSPEC ставить три primary questions:

1. Чи можуть users understand essential system без relying on sight?
2. Чи можуть users understand essential system без relying on sound?
3. Чи можуть users operate essential system без relying on touch?

> [!IMPORTANT]
>
> A11YSPEC defines accessibility requirements for verification. Вона не є replacement for legal accessibility standards, platform certification requirements або specialized assistive-technology review. System може бути within A11YSPEC і все одно require additional review для other accessibility standards.

<a id="table-of-contents"></a>

## Зміст

- [A11YSPEC](#a11yspec)
  - [Вступ](#introduction)
  - [Зміст](#table-of-contents)
  - [Conformance](#conformance)
  - [Primary Accessibility Senses](#primary-accessibility-senses)
    - [Зір](#sight)
    - [Звук](#sound)
    - [Дотик](#touch)
    - [Додаткові Sensory Domains](#additional-sensory-domains)
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
  - [Коли зір недоступний](#sight-unavailable)
  - [Коли звук недоступний](#sound-unavailable)
  - [Коли дотик недоступний](#touch-unavailable)
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

System вважається conformant with A11YSPEC, коли вона satisfies requirements, defined by this document, for each required accessibility case.

Conforming system must:

1. Remain reasonably usable when sight is unavailable.
2. Remain reasonably usable when sound is unavailable.
3. Remain reasonably usable when touch is unavailable.
4. Preserve access to essential functionality in each required accessibility case.
5. Preserve access to all critical functionality in each required accessibility case.
6. Provide reasonable alternate access paths when essential meaning або operation would otherwise depend on the unavailable sense.
7. Use a stable accessibility mechanism appropriate to the reviewed system.
8. Avoid relying exclusively on one primary sense for essential functionality.

System does not need to provide identical experiences across every sensory path. Non-visual experience may be slower than visual one. Sound-free experience may require captions, visual indicators або haptic confirmation. Touch-free experience may require keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction або another non-touch method.

Verification concerned with practical access to essential functionality, not identical presentation.

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

For A11YSPEC, three primary accessibility senses are **зір**, **звук** і **дотик**.

These senses are primary because they are the most common sensory pathways involved in user-interface interaction. System may provide output through sight, sound, or touch, and may receive interaction through touch, motion, voice, keyboard input, pointer input, switch input або another available input path.

<a id="sight"></a>

### Зір

Зір — це visual sensory pathway, через який user perceives visual output.

Sight may be involved in perceiving:

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

System depends on sight when essential meaning or operation requires the user to visually perceive information.

<a id="sound"></a>

### Звук

Звук — це auditory sensory pathway, через який user perceives audio output.

Sound may be involved in perceiving:

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

System depends on sound when essential meaning or operation requires the user to hear information.

<a id="touch"></a>

### Дотик

Дотик — це tactile sensory pathway, через який user perceives physical or haptic output, і physical interaction pathway, через який user may operate controls through direct contact, pressure, gesture або movement.

Touch may be involved in perceiving or performing:

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

System depends on touch when essential meaning or operation requires tactile perception або touch-based interaction without a reasonable alternate input or output path.

<a id="additional-sensory-domains"></a>

### Додаткові Sensory Domains

CatalystUI також recognizes **смак** і **нюх** as sensory domains.

Taste and smell may be considered during accessibility review when they are meaningfully used by the system. These senses are inclusive for verification, meaning they may strengthen or support an accessibility review when they provide meaningful alternate access або additional context.

Taste and smell are not currently exclusive for failure. System does not fail A11YSPEC simply because it does not provide taste-based or smell-based interaction.

A11YSPEC primarily concerned with whether the system remains reasonably usable when sight, sound, or touch is individually unavailable.

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

Conforming system must be reviewed against each required accessibility case.

| Недоступне чуття | Required Accessibility Behavior |
| ---------------- | ------------------------------- |
| Зір              | System must remain reasonably usable through sound and touch. |
| Звук             | System must remain reasonably usable through sight and touch. |
| Дотик            | System must remain reasonably usable through sight and sound. |

Each case is reviewed individually.

System is not required to remain fully usable when multiple primary senses are unavailable at the same time unless that condition is included in the reviewed scope.

System is not required to provide every possible accommodation. It must provide reasonable access to essential functionality under each required accessibility case.

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality is any behavior, content, control, output, input, workflow, or configuration that user reasonably needs in order to understand, navigate, configure, or operate the essential behavior of a system.

Essential functionality may include:

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
* any interaction required for normal use

System does not need to make every decorative, optional, redundant, or nonessential feature equally available through every sensory path. However, user must not be blocked from using essential system by unavailable sense.

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality is essential functionality where loss of access may prevent meaningful use, create serious error, or cause user to make important decision without understanding consequence.

Critical functionality may include:

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
* core navigation required to reach accessibility settings

Critical functionality must remain accessible in each required accessibility case.

System may fail A11YSPEC if critical functionality depends exclusively on unavailable sense.

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality is functionality that is not reasonably required for user to understand, navigate, configure, or operate essential behavior of system.

Nonessential functionality may include:

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

Nonessential functionality may be inaccessible under one or more accessibility cases without automatically causing failure. However, nonessential functionality should not be confused with essential functionality merely because it is inconvenient to support.

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

System satisfies essential access requirement when essential functionality remains reasonably understandable, navigable, configurable, and operable in each required accessibility case.

Essential experience does not need to be identical across all senses.

Essential experience must remain meaningfully usable.

<a id="critical-access-requirement"></a>

### Critical Access Requirement

System satisfies critical access requirement when all critical functionality remains accessible in each required accessibility case.

Critical functionality must not be hidden behind one required sensory pathway.

For example, system should not provide accessible interface for ordinary use while leaving account deletion warnings, payment confirmations, privacy decisions, or accessibility settings dependent on sight, sound, or touch alone.

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

System satisfies alternate access requirement when essential meaning or operation provided through one primary sense is also reasonably available through another sensory or interaction path when that sense is unavailable.

Alternate access may be provided through:

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

Alternate path does not need to match original path perfectly. It must preserve essential meaning and operation.

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

System must not require one primary sense as the only path to essential functionality.

System may use sight, sound, or touch as primary experience. However, when that sense is unavailable, user must still have reasonable way to understand and operate essential system through remaining sensory paths.

System may fail review when essential information or interaction is available only through:

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

## Коли зір недоступний

When sight is unavailable, system must remain reasonably usable through sound and touch.

This means essential visual information must have meaningful non-visual access path.

System may satisfy this requirement through:

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

System should not rely exclusively on:

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

when that information is required to understand or operate essential functionality.

System may fail this case if user cannot reasonably navigate, understand, or operate essential system without sight.

<a id="sound-unavailable"></a>

## Коли звук недоступний

When sound is unavailable, system must remain reasonably usable through sight and touch.

This means essential auditory information must have meaningful non-auditory access path.

System may satisfy this requirement through:

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

System should not rely exclusively on:

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

when that information is required to understand or operate essential functionality.

System may fail this case if user cannot reasonably navigate, understand, or operate essential system without sound.

<a id="touch-unavailable"></a>

## Коли дотик недоступний

When touch is unavailable, system must remain reasonably usable through sight and sound.

This means essential tactile information and touch-based operation must have meaningful non-touch access path.

System may satisfy this requirement through:

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

System should not rely exclusively on:

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

when that interaction is required to understand or operate essential functionality.

System may fail this case if user cannot reasonably navigate, understand, or operate essential system without touch.

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

Conforming system must use stable accessibility mechanism appropriate to system being reviewed.

Stable accessibility mechanism should allow accessibility behavior to be maintained, updated, reviewed, and extended without relying on fragile or undocumented behavior.

Stable accessibility mechanism may include:

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

System should avoid implementing essential functionality in a way that prevents reasonable alternate access.

<a id="semantic-structure"></a>

### Semantic Structure

Conforming system should provide semantic structure when system presents meaningful content or controls.

Semantic structure may include:

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

Semantic structure is especially important when sight is unavailable, because assistive technologies often rely on semantic information to communicate visual interfaces through non-visual output.

System may fail review if essential controls or content cannot be understood because their structure, labels, or relationships are unavailable through alternate access paths.

<a id="alternate-output"></a>

### Alternate Output

Conforming system must provide reasonable alternate output when essential meaning would otherwise depend on unavailable sense.

Alternate output may include:

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

Alternate output must preserve essential meaning.

<a id="alternate-input"></a>

### Alternate Input

Conforming system must provide reasonable alternate input when essential operation would otherwise depend on touch alone.

Alternate input may include:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input does not need to be fastest or most convenient input method. It must be sufficient for essential operation.

<a id="accessible-feedback"></a>

### Accessible Feedback

Conforming system must provide accessible feedback for essential actions.

Accessible feedback may include:

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

Feedback must not rely exclusively on unavailable sense in related accessibility case.

For example, sound-only success chime is not sufficient when sound is unavailable. Color-only error state is not sufficient when sight is unavailable. Vibration-only confirmation is not sufficient when touch is unavailable.

<a id="accessible-configuration"></a>

### Accessible Configuration

Conforming system must allow users to reach and use required accessibility settings through same accessibility requirements defined by this specification.

Accessibility settings must not be hidden behind inaccessible path.

For example, screen-reader-compatible mode is not sufficient if user must first navigate unlabeled visual-only menu to enable it.

System may fail review if its accessibility configuration cannot be reached or operated in condition it is intended to support.

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

System considered within spec when CatalystUI Team has reviewed system and found it reasonable to conclude that it satisfies A11YSPEC.

System may be within spec when:

* sight-unavailable use remains reasonably supported
* sound-unavailable use remains reasonably supported
* touch-unavailable use remains reasonably supported
* essential functionality remains accessible in each required case
* critical functionality remains accessible in each required case
* alternate access paths preserve essential meaning and operation
* accessibility settings, when present, can be reached and used accessibly
* the system does not trap essential functionality behind one required sense
* the system uses a stable accessibility mechanism appropriate to its design

System may be within spec even if experiences are not identical across all sensory paths.

System may be within spec even if some nonessential functionality is not equally available in every required accessibility case.

<a id="warnings"></a>

### Warnings

Warning may be issued when system appears to satisfy A11YSPEC but contains concerns that should be documented.

Warnings may include:

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

Warnings do not necessarily prevent verification.

<a id="failures"></a>

### Failures

Failure occurs when system does not satisfy one or more required conditions of A11YSPEC.

Failures may include:

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

Failures prevent verification until resolved.

<a id="verification-validity"></a>

### Verification Validity

A11YSPEC verification applies only to reviewed state of system at time verification is issued.

System may retain verification across later updates so long as it preserves verified accessibility foundation.

Minor wording changes, visual refinements, performance improvements, added accessibility features, and ordinary content updates do not automatically invalidate verification.

New review may be required if system:

* removes alternate access paths
* breaks assistive-technology support
* substantially changes essential navigation
* removes required accessibility settings
* changes interaction behavior in a way that affects verified accessibility
* introduces new essential workflows without accessible alternatives
* makes previously accessible critical functionality inaccessible
* replaces accessible behavior with single-sense-dependent behavior

In other words, improving accessibility is usually fine.

Breaking the verified access model may require review.
