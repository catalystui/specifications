<!-- Bản dịch này được tạo bởi ChatGPT và nên được một biên dịch viên con người xem xét lại. -->

<!-- Hãy xóa các dòng này trong pull request sau khi bản dịch đã được xác minh. -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Các definitions, requirements và concepts được trình bày tại đây mô tả practical accessibility support và có thể được diễn đạt lại tự do.

<a id="introduction"></a>

## Giới thiệu

**Accessibility Specification (A11YSPEC)** thiết lập core concepts, terminology và requirements được dùng để evaluate accessibility support trong CatalystUI ecosystem. Mục đích của nó là cung cấp một clear standard để xác định liệu một system, service, framework, application, library hoặc implementation có còn meaningfully usable khi một primary sensory pathway unavailable hay không.

Accessibility quan trọng vì user interface không nên phụ thuộc hoàn toàn vào một sense khi cùng một essential meaning có thể được communicate hợp lý qua một sense khác. Một system có thể technically functional, nhưng nếu user không thể understand, navigate, configure hoặc operate essential behavior của nó khi không có sight, sound hoặc touch riêng lẻ, thì system đã không provide reasonable access cho condition đó.

Specification này không cố verify mọi possible disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard hoặc specialized use case. Thay vào đó, nó define minimum accessibility foundation required để users có thể meaningfully access và operate essential portions của system khi một trong ba primary accessibility senses unavailable.

Nói đơn giản, A11YSPEC đặt ra ba câu hỏi chính:

1. Users có thể understand essential system mà không relying on sight không?
2. Users có thể understand essential system mà không relying on sound không?
3. Users có thể operate essential system mà không relying on touch không?

> [!IMPORTANT]
>
> A11YSPEC define accessibility requirements for verification. Nó không phải replacement cho legal accessibility standards, platform certification requirements hoặc specialized assistive-technology review. Một system có thể within A11YSPEC và vẫn require additional review cho other accessibility standards.

<a id="table-of-contents"></a>

## Mục lục

- [A11YSPEC](#a11yspec)
  - [Giới thiệu](#introduction)
  - [Mục lục](#table-of-contents)
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

Một system được coi là conformant với A11YSPEC khi nó satisfies các requirements được define bởi document này cho từng required accessibility case.

Một conforming system phải:

1. Remain reasonably usable khi sight unavailable.
2. Remain reasonably usable khi sound unavailable.
3. Remain reasonably usable khi touch unavailable.
4. Preserve access to essential functionality trong từng required accessibility case.
5. Preserve access to all critical functionality trong từng required accessibility case.
6. Provide reasonable alternate access paths khi essential meaning hoặc operation otherwise depend on unavailable sense.
7. Use a stable accessibility mechanism appropriate to reviewed system.
8. Avoid relying exclusively on one primary sense for essential functionality.

System không cần provide identical experiences trên mọi sensory path. Non-visual experience có thể slower hơn visual one. Sound-free experience có thể require captions, visual indicators hoặc haptic confirmation. Touch-free experience có thể require keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction hoặc another non-touch method.

Verification concerned with practical access to essential functionality, not identical presentation.

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

Đối với A11YSPEC, ba primary accessibility senses là **sight**, **sound** và **touch**.

Những senses này là primary vì chúng là most common sensory pathways involved in user-interface interaction. System có thể provide output through sight, sound hoặc touch, và có thể receive interaction through touch, motion, voice, keyboard input, pointer input, switch input hoặc another available input path.

<a id="sight"></a>

### Sight

Sight là visual sensory pathway mà user dùng để perceive visual output.

Sight có thể involved in perceiving:

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

System depends on sight khi essential meaning hoặc operation requires user to visually perceive information.

<a id="sound"></a>

### Sound

Sound là auditory sensory pathway mà user dùng để perceive audio output.

Sound có thể involved in perceiving:

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

System depends on sound khi essential meaning hoặc operation requires user to hear information.

<a id="touch"></a>

### Touch

Touch là tactile sensory pathway mà user dùng để perceive physical hoặc haptic output, đồng thời là physical interaction pathway mà user có thể operate controls thông qua direct contact, pressure, gesture hoặc movement.

Touch có thể involved in perceiving or performing:

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

System depends on touch khi essential meaning hoặc operation requires tactile perception hoặc touch-based interaction without a reasonable alternate input or output path.

<a id="additional-sensory-domains"></a>

### Additional Sensory Domains

CatalystUI cũng recognizes **taste** và **smell** as sensory domains.

Taste và smell có thể được considered during accessibility review khi system sử dụng chúng meaningfully. These senses are inclusive for verification, nghĩa là chúng có thể strengthen hoặc support an accessibility review khi chúng provide meaningful alternate access hoặc additional context.

Taste và smell currently not exclusive for failure. System không fail A11YSPEC simply because it does not provide taste-based or smell-based interaction.

A11YSPEC primarily concerned with whether system remains reasonably usable when sight, sound, or touch is individually unavailable.

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

Conforming system phải được reviewed against each required accessibility case.

| Unavailable Sense | Required Accessibility Behavior |
| ----------------- | -------------------------------- |
| Sight             | System phải remain reasonably usable through sound and touch. |
| Sound             | System phải remain reasonably usable through sight and touch. |
| Touch             | System phải remain reasonably usable through sight and sound. |

Mỗi case được reviewed individually.

System không required to remain fully usable khi multiple primary senses unavailable at the same time unless condition đó included in reviewed scope.

System không required to provide every possible accommodation. Nó phải provide reasonable access to essential functionality under each required accessibility case.

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality là bất kỳ behavior, content, control, output, input, workflow hoặc configuration nào mà user reasonably needs để understand, navigate, configure hoặc operate essential behavior của system.

Essential functionality có thể include:

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

System không cần make every decorative, optional, redundant hoặc nonessential feature equally available through every sensory path. Tuy nhiên, user must not be blocked from using essential system by unavailable sense.

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality là essential functionality mà loss of access có thể prevent meaningful use, create a serious error hoặc cause user to make an important decision without understanding the consequence.

Critical functionality có thể include:

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

Critical functionality phải remain accessible in each required accessibility case.

System có thể fail A11YSPEC nếu critical functionality depends exclusively on unavailable sense.

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality là functionality không reasonably required để user understand, navigate, configure hoặc operate essential behavior của system.

Nonessential functionality có thể include:

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

Nonessential functionality có thể inaccessible under one or more accessibility cases without automatically causing failure. Tuy nhiên, nonessential functionality should not be confused with essential functionality merely because it is inconvenient to support.

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

System satisfies essential access requirement khi essential functionality remains reasonably understandable, navigable, configurable và operable in each required accessibility case.

Essential experience không cần identical across all senses.

Essential experience phải remain meaningfully usable.

<a id="critical-access-requirement"></a>

### Critical Access Requirement

System satisfies critical access requirement khi all critical functionality remains accessible in each required accessibility case.

Critical functionality must not be hidden behind one required sensory pathway.

Ví dụ, system không nên provide accessible interface for ordinary use while leaving account deletion warnings, payment confirmations, privacy decisions hoặc accessibility settings dependent on sight, sound, or touch alone.

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

System satisfies alternate access requirement khi essential meaning hoặc operation provided through one primary sense cũng reasonably available through another sensory or interaction path khi sense đó unavailable.

Alternate access có thể provided through:

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
* another stable mechanism appropriate to system

Alternate path không cần match original path perfectly. Nó phải preserve essential meaning và operation.

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

System must not require one primary sense as the only path to essential functionality.

System có thể use sight, sound hoặc touch as primary experience. Tuy nhiên, khi sense đó unavailable, user vẫn phải có reasonable way to understand and operate essential system through remaining sensory paths.

System có thể fail review khi essential information hoặc interaction chỉ available through:

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

Khi sight unavailable, system phải remain reasonably usable through sound and touch.

Điều này nghĩa là essential visual information phải có meaningful non-visual access path.

System có thể satisfy requirement này through:

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

khi information đó required to understand or operate essential functionality.

System có thể fail case này nếu user cannot reasonably navigate, understand hoặc operate essential system without sight.

<a id="sound-unavailable"></a>

## Sound Unavailable

Khi sound unavailable, system phải remain reasonably usable through sight and touch.

Điều này nghĩa là essential auditory information phải có meaningful non-auditory access path.

System có thể satisfy requirement này through:

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

khi information đó required to understand or operate essential functionality.

System có thể fail case này nếu user cannot reasonably navigate, understand hoặc operate essential system without sound.

<a id="touch-unavailable"></a>

## Touch Unavailable

Khi touch unavailable, system phải remain reasonably usable through sight and sound.

Điều này nghĩa là essential tactile information và touch-based operation phải có meaningful non-touch access path.

System có thể satisfy requirement này through:

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

khi interaction đó required to understand or operate essential functionality.

System có thể fail case này nếu user cannot reasonably navigate, understand hoặc operate essential system without touch.

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

Conforming system phải use a stable accessibility mechanism appropriate to system being reviewed.

Stable accessibility mechanism nên allow accessibility behavior to be maintained, updated, reviewed, and extended without relying on fragile or undocumented behavior.

Stable accessibility mechanism có thể include:

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
* another stable structure appropriate to system

System should avoid implementing essential functionality in a way that prevents reasonable alternate access.

<a id="semantic-structure"></a>

### Semantic Structure

Conforming system nên provide semantic structure khi system presents meaningful content or controls.

Semantic structure có thể include:

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

Semantic structure đặc biệt important khi sight unavailable, vì assistive technologies thường rely on semantic information để communicate visual interfaces through non-visual output.

System có thể fail review nếu essential controls hoặc content cannot be understood vì structure, labels hoặc relationships unavailable through alternate access paths.

<a id="alternate-output"></a>

### Alternate Output

Conforming system phải provide reasonable alternate output khi essential meaning otherwise depend on unavailable sense.

Alternate output có thể include:

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

Alternate output phải preserve essential meaning.

<a id="alternate-input"></a>

### Alternate Input

Conforming system phải provide reasonable alternate input khi essential operation otherwise depend on touch alone.

Alternate input có thể include:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input không cần là fastest hoặc most convenient input method. Nó phải sufficient for essential operation.

<a id="accessible-feedback"></a>

### Accessible Feedback

Conforming system phải provide accessible feedback for essential actions.

Accessible feedback có thể include:

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

Ví dụ, sound-only success chime không sufficient khi sound unavailable. Color-only error state không sufficient khi sight unavailable. Vibration-only confirmation không sufficient khi touch unavailable.

<a id="accessible-configuration"></a>

### Accessible Configuration

Conforming system phải allow users to reach and use required accessibility settings through the same accessibility requirements defined by this specification.

Accessibility settings must not be hidden behind inaccessible path.

Ví dụ, screen-reader-compatible mode không sufficient nếu user trước tiên phải navigate an unlabeled visual-only menu để enable nó.

System có thể fail review nếu accessibility configuration của nó cannot be reached or operated in the condition it is intended to support.

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

System considered within spec khi CatalystUI Team đã reviewed system và found it reasonable to conclude that it satisfies A11YSPEC.

System có thể within spec khi:

* sight-unavailable use remains reasonably supported
* sound-unavailable use remains reasonably supported
* touch-unavailable use remains reasonably supported
* essential functionality remains accessible in each required case
* critical functionality remains accessible in each required case
* alternate access paths preserve essential meaning and operation
* accessibility settings, when present, can be reached and used accessibly
* system does not trap essential functionality behind one required sense
* system uses a stable accessibility mechanism appropriate to its design

System có thể within spec even if experiences are not identical across all sensory paths.

System có thể within spec even if some nonessential functionality is not equally available in every required accessibility case.

<a id="warnings"></a>

### Warnings

Warning có thể issued khi system appears to satisfy A11YSPEC but contains concerns that should be documented.

Warnings có thể include:

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

Failure occurs khi system does not satisfy one or more required conditions of A11YSPEC.

Failures có thể include:

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

Failures prevent verification until resolved.

<a id="verification-validity"></a>

### Verification Validity

A11YSPEC verification applies only to reviewed state of system at the time verification is issued.

System may retain verification across later updates so long as it preserves verified accessibility foundation.

Minor wording changes, visual refinements, performance improvements, added accessibility features và ordinary content updates do not automatically invalidate verification.

New review có thể required nếu system:

* removes alternate access paths
* breaks assistive-technology support
* substantially changes essential navigation
* removes required accessibility settings
* changes interaction behavior in a way that affects verified accessibility
* introduces new essential workflows without accessible alternatives
* makes previously accessible critical functionality inaccessible
* replaces accessible behavior with single-sense-dependent behavior

Nói cách khác, improving accessibility thường là fine.

Breaking the verified access model may require review.
