<!-- 此翻译由 ChatGPT 生成，应由人工译者审阅。 -->

<!-- 翻译经过验证后，请在 pull request 中移除这些行。 -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> 本文提出的 definitions、requirements 和 concepts 描述 practical accessibility support，并可被自由重新表述。

<a id="introduction"></a>

## 引言

**Accessibility Specification (A11YSPEC)** 建立了在 CatalystUI ecosystem 中用于 evaluate accessibility support 的 core concepts、terminology 和 requirements。它的目的，是为判断某个 system、service、framework、application、library 或 implementation 在一个 primary sensory pathway unavailable 时是否仍然 meaningfully usable 提供 clear standard。

Accessibility 很重要，因为当同样的 essential meaning 可以通过另一种方式合理传达时，user interface 不应完全依赖某一个 sense。System 可能 technically functional，但如果 user 无法在没有 sight、sound 或 touch 的单独情况下 understand、navigate、configure 或 operate its essential behavior，那么 system 就未能为该 condition provide reasonable access。

本 specification 并不试图 verify 每一种 possible disability、device、assistive technology、medical condition、legal requirement、regional accessibility standard 或 specialized use case。相反，它 define users 在三个 primary accessibility senses 中有一个 unavailable 时，meaningfully access 和 operate system 的 essential portions 所 required 的 minimum accessibility foundation。

更简单地说，A11YSPEC 提出三个 primary questions：

1. Users 能否在不 relying on sight 的情况下 understand essential system？
2. Users 能否在不 relying on sound 的情况下 understand essential system？
3. Users 能否在不 relying on touch 的情况下 operate essential system？

> [!IMPORTANT]
>
> A11YSPEC define verification 所用的 accessibility requirements。它不是 legal accessibility standards、platform certification requirements 或 specialized assistive-technology review 的 replacement。System 可以 within A11YSPEC，但仍 require additional review for other accessibility standards。

<a id="table-of-contents"></a>

## 目录

- [A11YSPEC](#a11yspec)
  - [引言](#introduction)
  - [目录](#table-of-contents)
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

当 system satisfies 本 document 为每个 required accessibility case define 的 requirements 时，该 system 被认为 conformant with A11YSPEC。

Conforming system 必须：

1. 在 sight unavailable 时 remain reasonably usable。
2. 在 sound unavailable 时 remain reasonably usable。
3. 在 touch unavailable 时 remain reasonably usable。
4. 在每个 required accessibility case 中 preserve access to essential functionality。
5. 在每个 required accessibility case 中 preserve access to all critical functionality。
6. 当 essential meaning 或 operation otherwise depend on unavailable sense 时，provide reasonable alternate access paths。
7. 使用适合 reviewed system 的 stable accessibility mechanism。
8. 避免 essential functionality exclusively relying on one primary sense。

System 不需要在每条 sensory path 上 provide identical experiences。Non-visual experience 可以比 visual one 慢。Sound-free experience 可能 require captions、visual indicators 或 haptic confirmation。Touch-free experience 可能 require keyboard navigation、pointer alternatives、voice interaction、switch-compatible interaction 或 another non-touch method。

Verification concerned with practical access to essential functionality, not identical presentation。

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

对于 A11YSPEC，三个 primary accessibility senses 是 **sight**、**sound** 和 **touch**。

这些 senses 是 primary，因为它们是 user-interface interaction 中最常见的 sensory pathways。System 可以通过 sight、sound 或 touch provide output，也可以通过 touch、motion、voice、keyboard input、pointer input、switch input 或 another available input path receive interaction。

<a id="sight"></a>

### Sight

Sight 是 user perceive visual output 的 visual sensory pathway。

Sight 可能 involved in perceiving：

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

当 essential meaning 或 operation requires user to visually perceive information 时，system depends on sight。

<a id="sound"></a>

### Sound

Sound 是 user perceive audio output 的 auditory sensory pathway。

Sound 可能 involved in perceiving：

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

当 essential meaning 或 operation requires user to hear information 时，system depends on sound。

<a id="touch"></a>

### Touch

Touch 是 user perceive physical 或 haptic output 的 tactile sensory pathway，也是 user 可通过 direct contact、pressure、gesture 或 movement operate controls 的 physical interaction pathway。

Touch 可能 involved in perceiving or performing：

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

当 essential meaning 或 operation requires tactile perception 或 touch-based interaction 且没有 reasonable alternate input or output path 时，system depends on touch。

<a id="additional-sensory-domains"></a>

### Additional Sensory Domains

CatalystUI also recognizes **taste** and **smell** as sensory domains。

当 system meaningful 地使用 taste 和 smell 时，它们可以在 accessibility review 中被 considered。这些 senses 对 verification 是 inclusive，也就是说，当它们 provide meaningful alternate access 或 additional context 时，可以 strengthen 或 support accessibility review。

Taste 和 smell 当前并非 failure 的 exclusive 条件。System 不会 simply because it does not provide taste-based or smell-based interaction 而 fail A11YSPEC。

A11YSPEC primarily concerned with whether system remains reasonably usable when sight, sound, or touch is individually unavailable。

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

Conforming system 必须 against each required accessibility case 进行 review。

| Unavailable Sense | Required Accessibility Behavior |
| ----------------- | -------------------------------- |
| Sight             | System 必须通过 sound 和 touch remain reasonably usable。 |
| Sound             | System 必须通过 sight 和 touch remain reasonably usable。 |
| Touch             | System 必须通过 sight 和 sound remain reasonably usable。 |

Each case is reviewed individually。

除非该 condition included in reviewed scope，system 不 required to remain fully usable when multiple primary senses are unavailable at the same time。

System 不 required to provide every possible accommodation。它必须 under each required accessibility case provide reasonable access to essential functionality。

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality 是 user reasonably needs in order to understand, navigate, configure, or operate the essential behavior of a system 的任何 behavior、content、control、output、input、workflow 或 configuration。

Essential functionality 可以 include：

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

System 不需要 make every decorative, optional, redundant, or nonessential feature equally available through every sensory path。然而，user must not be blocked from using the essential system by unavailable sense。

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality 是 essential functionality，其中 loss of access 可能 prevent meaningful use、create a serious error，或 cause user to make an important decision without understanding the consequence。

Critical functionality 可以 include：

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

Critical functionality must remain accessible in each required accessibility case。

如果 critical functionality depends exclusively on unavailable sense，system may fail A11YSPEC。

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality 是 user understand、navigate、configure 或 operate system 的 essential behavior 时并不 reasonably required 的 functionality。

Nonessential functionality 可以 include：

* decorative animation
* optional effects
* cosmetic visual polish
* nonessential sound effects
* redundant haptic effects
* optional marketing content
* optional tutorial content
* hidden diagnostic behavior
* developer-facing controls
* experimental features outside reviewed scope

Nonessential functionality may be inaccessible under one or more accessibility cases without automatically causing failure。然而，不应 merely because it is inconvenient to support 而将 nonessential functionality 与 essential functionality 混淆。

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

当 essential functionality remains reasonably understandable、navigable、configurable and operable in each required accessibility case 时，system satisfies the essential access requirement。

Essential experience 不需要 identical across all senses。

Essential experience must remain meaningfully usable。

<a id="critical-access-requirement"></a>

### Critical Access Requirement

当 all critical functionality remains accessible in each required accessibility case 时，system satisfies the critical access requirement。

Critical functionality must not be hidden behind one required sensory pathway。

例如，system 不应 provide accessible interface for ordinary use，却让 account deletion warnings、payment confirmations、privacy decisions 或 accessibility settings dependent on sight, sound, or touch alone。

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

当通过 one primary sense provided 的 essential meaning 或 operation，在该 sense unavailable 时也 reasonably available through another sensory or interaction path，system satisfies alternate access requirement。

Alternate access may be provided through：

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

Alternate path does not need to match original path perfectly。It must preserve essential meaning and operation。

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

System must not require one primary sense as the only path to essential functionality。

System 可以 use sight, sound, or touch as the primary experience。然而，当 that sense unavailable 时，user must still have a reasonable way to understand and operate the essential system through remaining sensory paths。

System may fail review when essential information or interaction is available only through：

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

When sight is unavailable, system must remain reasonably usable through sound and touch。

这意味着 essential visual information 必须有 meaningful non-visual access path。

System may satisfy this requirement through：

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

System should not rely exclusively on：

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

when that information is required to understand or operate essential functionality。

如果 user cannot reasonably navigate, understand, or operate essential system without sight，system may fail this case。

<a id="sound-unavailable"></a>

## Sound Unavailable

When sound is unavailable, system must remain reasonably usable through sight and touch。

这意味着 essential auditory information 必须有 meaningful non-auditory access path。

System may satisfy this requirement through：

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

System should not rely exclusively on：

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

when that information is required to understand or operate essential functionality。

如果 user cannot reasonably navigate, understand, or operate essential system without sound，system may fail this case。

<a id="touch-unavailable"></a>

## Touch Unavailable

When touch is unavailable, system must remain reasonably usable through sight and sound。

这意味着 essential tactile information 和 touch-based operation 必须有 meaningful non-touch access path。

System may satisfy this requirement through：

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

System should not rely exclusively on：

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

when that interaction is required to understand or operate essential functionality。

如果 user cannot reasonably navigate, understand, or operate essential system without touch，system may fail this case。

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

Conforming system must use a stable accessibility mechanism appropriate to system being reviewed。

Stable accessibility mechanism should allow accessibility behavior to be maintained, updated, reviewed, and extended without relying on fragile or undocumented behavior。

Stable accessibility mechanism may include：

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

System should avoid implementing essential functionality in a way that prevents reasonable alternate access。

<a id="semantic-structure"></a>

### Semantic Structure

Conforming system should provide semantic structure when system presents meaningful content or controls。

Semantic structure may include：

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

Semantic structure 在 sight unavailable 时尤其 important，因为 assistive technologies often rely on semantic information to communicate visual interfaces through non-visual output。

如果 essential controls or content cannot be understood because their structure, labels, or relationships are unavailable through alternate access paths，system may fail review。

<a id="alternate-output"></a>

### Alternate Output

Conforming system must provide reasonable alternate output when essential meaning would otherwise depend on unavailable sense。

Alternate output may include：

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

Alternate output must preserve essential meaning。

<a id="alternate-input"></a>

### Alternate Input

Conforming system must provide reasonable alternate input when essential operation would otherwise depend on touch alone。

Alternate input may include：

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input does not need to be fastest or most convenient input method。It must be sufficient for essential operation。

<a id="accessible-feedback"></a>

### Accessible Feedback

Conforming system must provide accessible feedback for essential actions。

Accessible feedback may include：

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

Feedback must not rely exclusively on unavailable sense in related accessibility case。

例如，当 sound unavailable 时，sound-only success chime 不 sufficient。当 sight unavailable 时，color-only error state 不 sufficient。当 touch unavailable 时，vibration-only confirmation 不 sufficient。

<a id="accessible-configuration"></a>

### Accessible Configuration

Conforming system must allow users to reach and use required accessibility settings through same accessibility requirements defined by this specification。

Accessibility settings must not be hidden behind inaccessible path。

例如，如果 user 必须先 navigate 一个 unlabeled visual-only menu 才能 enable screen-reader-compatible mode，那么该 mode 不 sufficient。

如果 accessibility configuration cannot be reached or operated in condition it is intended to support，system may fail review。

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

当 CatalystUI Team has reviewed system and found it reasonable to conclude that it satisfies A11YSPEC 时，system is considered within spec。

System may be within spec when：

* sight-unavailable use remains reasonably supported
* sound-unavailable use remains reasonably supported
* touch-unavailable use remains reasonably supported
* essential functionality remains accessible in each required case
* critical functionality remains accessible in each required case
* alternate access paths preserve essential meaning and operation
* accessibility settings, when present, can be reached and used accessibly
* system does not trap essential functionality behind one required sense
* system uses a stable accessibility mechanism appropriate to its design

System may be within spec even if experiences are not identical across all sensory paths。

System may be within spec even if some nonessential functionality is not equally available in every required accessibility case。

<a id="warnings"></a>

### Warnings

当 system appears to satisfy A11YSPEC but contains concerns that should be documented 时，warning may be issued。

Warnings may include：

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

Warnings do not necessarily prevent verification。

<a id="failures"></a>

### Failures

当 system does not satisfy one or more required conditions of A11YSPEC 时，failure occurs。

Failures may include：

* essential functionality unavailable when sight is unavailable
* essential functionality unavailable when sound is unavailable
* essential functionality unavailable when touch is unavailable
* critical functionality unavailable in any required accessibility case
* no reasonable alternate access path for essential visual information
* no reasonable alternate access path for essential auditory information
* no reasonable alternate access path for essential touch-based operation
* accessibility settings unreachable under condition they are meant to support
* controls without meaningful labels or structure when required for non-visual use
* sound-only warnings with no visual, tactile, or text equivalent
* color-only status with no non-visual equivalent
* gesture-only operation with no keyboard, pointer, voice, switch, or other alternative
* haptic-only confirmation with no visual or auditory equivalent
* broken assistive-technology support for essential workflows
* major navigation traps
* essential workflows that cannot be completed without unavailable sense

Failures prevent verification until resolved。

<a id="verification-validity"></a>

### Verification Validity

A11YSPEC verification applies only to reviewed state of system at time verification is issued。

System may retain verification across later updates so long as it preserves verified accessibility foundation。

Minor wording changes, visual refinements, performance improvements, added accessibility features, and ordinary content updates do not automatically invalidate verification。

A new review may be required if system：

* removes alternate access paths
* breaks assistive-technology support
* substantially changes essential navigation
* removes required accessibility settings
* changes interaction behavior in a way that affects verified accessibility
* introduces new essential workflows without accessible alternatives
* makes previously accessible critical functionality inaccessible
* replaces accessible behavior with single-sense-dependent behavior

换句话说，improving accessibility is usually fine。

Breaking the verified access model may require review。
