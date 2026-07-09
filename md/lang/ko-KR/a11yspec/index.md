<!-- 이 번역은 ChatGPT에 의해 생성되었으며 사람 번역자의 검토가 필요합니다. -->

<!-- 번역이 확인된 후 pull request에서 이 줄들을 삭제하세요. -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> 여기에 제시된 definitions, requirements, concepts 는 practical accessibility support 를 설명하며 자유롭게 다시 표현할 수 있습니다.

<a id="introduction"></a>

## Introduction

**Accessibility Specification (A11YSPEC)** 는 CatalystUI ecosystem 안에서 accessibility support 를 평가하는 데 사용되는 core concepts, terminology, requirements 를 설정합니다. 그 목적은 하나의 primary sensory pathway 를 사용할 수 없을 때 system, service, framework, application, library 또는 implementation 이 meaningfully usable 한 상태로 남는지를 판단하기 위한 명확한 standard 를 제공하는 것입니다.

Accessibility 가 중요한 이유는 동일한 essential meaning 을 다른 sense 로 합리적으로 전달할 수 있을 때 user interface 가 하나의 sense 에 전적으로 의존해서는 안 되기 때문입니다. system 은 technically functional 할 수 있지만 user 가 sight, sound, touch 중 하나 없이 essential behavior 를 이해하고, 탐색하고, 구성하고, 조작할 수 없다면 그 condition 에 대해 reasonable access 를 제공하지 못한 것입니다.

이 specification 은 모든 possible disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard 또는 specialized use case 를 검증하려는 것이 아닙니다. 대신 세 가지 primary accessibility senses 중 하나를 사용할 수 없을 때 users 가 system 의 essential portions 에 의미 있게 접근하고 조작하는 데 필요한 minimum accessibility foundation 을 정의합니다.

더 쉽게 말해 A11YSPEC 은 세 가지 primary questions 를 묻습니다.

1. users 는 sight 에 의존하지 않고 essential system 을 이해할 수 있습니까?
2. users 는 sound 에 의존하지 않고 essential system 을 이해할 수 있습니까?
3. users 는 touch 에 의존하지 않고 essential system 을 조작할 수 있습니까?

> [!IMPORTANT]
>
> A11YSPEC 은 verification 을 위한 accessibility requirements 를 정의합니다. 이는 legal accessibility standards, platform certification requirements 또는 specialized assistive-technology review 를 대체하지 않습니다. system 은 A11YSPEC 안에 있더라도 다른 accessibility standards 를 위해 additional review 가 필요할 수 있습니다.

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

system 은 각 required accessibility case 에 대해 이 document 가 정의한 requirements 를 만족할 때 A11YSPEC 에 conformant 한 것으로 간주됩니다.

conforming system 은 다음을 충족해야 합니다.

1. sight 를 사용할 수 없을 때 reasonably usable 한 상태로 남을 것.
2. sound 를 사용할 수 없을 때 reasonably usable 한 상태로 남을 것.
3. touch 를 사용할 수 없을 때 reasonably usable 한 상태로 남을 것.
4. 각 required accessibility case 에서 essential functionality 에 대한 access 를 보존할 것.
5. 각 required accessibility case 에서 모든 critical functionality 에 대한 access 를 보존할 것.
6. essential meaning 또는 operation 이 unavailable sense 에 의존하게 되는 경우 reasonable alternate access paths 를 제공할 것.
7. reviewed system 에 적합한 stable accessibility mechanism 을 사용할 것.
8. essential functionality 를 위해 one primary sense 에만 의존하지 않을 것.

system 은 모든 sensory path 에서 identical experiences 를 제공할 필요가 없습니다. non-visual experience 는 visual one 보다 느릴 수 있습니다. sound-free experience 는 captions, visual indicators 또는 haptic confirmation 을 요구할 수 있습니다. touch-free experience 는 keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction 또는 다른 non-touch method 를 요구할 수 있습니다.

Verification 은 identical presentation 이 아니라 essential functionality 에 대한 practical access 에 관심을 둡니다.

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

A11YSPEC 에서 세 가지 primary accessibility senses 는 **sight**, **sound**, **touch** 입니다.

이 senses 가 primary 인 이유는 user-interface interaction 에 가장 흔히 관여하는 sensory pathways 이기 때문입니다. system 은 sight, sound, touch 를 통해 output 을 제공할 수 있고 touch, motion, voice, keyboard input, pointer input, switch input 또는 다른 available input path 를 통해 interaction 을 받을 수 있습니다.

<a id="sight"></a>

### Sight

Sight 는 user 가 visual output 을 인식하는 visual sensory pathway 입니다.

Sight 는 다음을 인식하는 데 관여할 수 있습니다.

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

essential meaning 또는 operation 이 user 가 information 을 시각적으로 인식하는 것을 요구할 때 system 은 sight 에 의존합니다.

<a id="sound"></a>

### Sound

Sound 는 user 가 audio output 을 인식하는 auditory sensory pathway 입니다.

Sound 는 다음을 인식하는 데 관여할 수 있습니다.

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

essential meaning 또는 operation 이 user 가 information 을 듣는 것을 요구할 때 system 은 sound 에 의존합니다.

<a id="touch"></a>

### Touch

Touch 는 user 가 physical 또는 haptic output 을 인식하는 tactile sensory pathway 이며, direct contact, pressure, gesture 또는 movement 를 통해 controls 를 조작할 수 있는 physical interaction pathway 이기도 합니다.

Touch 는 다음을 인식하거나 수행하는 데 관여할 수 있습니다.

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

essential meaning 또는 operation 이 reasonable alternate input or output path 없이 tactile perception 또는 touch-based interaction 을 요구할 때 system 은 touch 에 의존합니다.

<a id="additional-sensory-domains"></a>

### Additional Sensory Domains

CatalystUI 는 **taste** 와 **smell** 도 sensory domains 로 인식합니다.

Taste 와 smell 은 system 이 의미 있게 사용할 때 accessibility review 에서 고려될 수 있습니다. 이 senses 는 verification 에서 inclusive 이며 meaningful alternate access 또는 additional context 를 제공할 때 review 를 강화하거나 지원할 수 있습니다.

Taste 와 smell 은 현재 failure 에 대해 exclusive 하지 않습니다. system 이 taste-based 또는 smell-based interaction 을 제공하지 않는다는 이유만으로 A11YSPEC 에 fail 하지 않습니다.

A11YSPEC 은 주로 sight, sound, touch 중 하나가 개별적으로 unavailable 할 때 system 이 reasonably usable 한 상태로 남는지를 다룹니다.

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

conforming system 은 각 required accessibility case 에 대해 reviewed 되어야 합니다.

| Unavailable Sense | Required Accessibility Behavior                                   |
| ----------------- | ----------------------------------------------------------------- |
| Sight             | system 은 sound 와 touch 를 통해 reasonably usable 한 상태로 남아야 합니다. |
| Sound             | system 은 sight 와 touch 를 통해 reasonably usable 한 상태로 남아야 합니다. |
| Touch             | system 은 sight 와 sound 를 통해 reasonably usable 한 상태로 남아야 합니다. |

각 case 는 개별적으로 review 됩니다.

reviewed scope 에 그 condition 이 포함되지 않는 한 system 은 여러 primary senses 가 동시에 unavailable 한 경우 fully usable 할 필요가 없습니다.

system 은 모든 possible accommodation 을 제공할 필요가 없습니다. 각 required accessibility case 에서 essential functionality 에 대한 reasonable access 를 제공해야 합니다.

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality 는 user 가 system 의 essential behavior 를 이해하고, 탐색하고, 구성하고, 조작하기 위해 합리적으로 필요한 behavior, content, control, output, input, workflow 또는 configuration 입니다.

Essential functionality 에는 다음이 포함될 수 있습니다.

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
* normal use 에 필요한 interaction

system 은 decorative, optional, redundant 또는 nonessential feature 를 모든 sensory path 에서 동일하게 available 하게 만들 필요는 없습니다. 그러나 user 가 unavailable sense 때문에 essential system 을 사용하는 데 blocked 되어서는 안 됩니다.

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality 는 essential functionality 중 access 를 잃으면 meaningful use 를 막거나 serious error 를 만들거나 user 가 consequence 를 이해하지 못한 채 important decision 을 내리게 할 수 있는 부분입니다.

Critical functionality 에는 다음이 포함될 수 있습니다.

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
* accessibility settings 에 도달하는 데 필요한 core navigation

Critical functionality 는 각 required accessibility case 에서 accessible 한 상태로 남아야 합니다.

critical functionality 가 unavailable sense 에만 의존하는 경우 system 은 A11YSPEC 에 fail 할 수 있습니다.

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality 는 user 가 system 의 essential behavior 를 이해하고, 탐색하고, 구성하고, 조작하는 데 합리적으로 필요하지 않은 functionality 입니다.

Nonessential functionality 에는 다음이 포함될 수 있습니다.

* decorative animation
* optional effects
* cosmetic visual polish
* nonessential sound effects
* redundant haptic effects
* optional marketing content
* optional tutorial content
* hidden diagnostic behavior
* developer-facing controls
* reviewed scope 밖의 experimental features

Nonessential functionality 는 하나 이상의 accessibility cases 에서 inaccessible 하더라도 자동으로 failure 를 일으키지 않을 수 있습니다. 그러나 support 하기 불편하다는 이유로 nonessential functionality 를 essential functionality 와 혼동해서는 안 됩니다.

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

system 은 각 required accessibility case 에서 essential functionality 가 reasonably understandable, navigable, configurable, operable 한 상태로 남을 때 essential access requirement 를 만족합니다.

essential experience 는 모든 senses 에서 동일할 필요가 없습니다.

essential experience 는 meaningfully usable 한 상태로 남아야 합니다.

<a id="critical-access-requirement"></a>

### Critical Access Requirement

system 은 모든 critical functionality 가 각 required accessibility case 에서 accessible 한 상태로 남을 때 critical access requirement 를 만족합니다.

Critical functionality 는 one required sensory pathway 뒤에 숨겨져서는 안 됩니다.

예를 들어 system 은 ordinary use 를 위해 accessible interface 를 제공하면서 account deletion warnings, payment confirmations, privacy decisions 또는 accessibility settings 를 sight, sound 또는 touch 하나에만 의존하게 해서는 안 됩니다.

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

system 은 one primary sense 를 통해 제공되는 essential meaning 또는 operation 이 그 sense 가 unavailable 할 때 다른 sensory 또는 interaction path 를 통해서도 reasonably available 할 때 alternate access requirement 를 만족합니다.

Alternate access 는 다음을 통해 제공될 수 있습니다.

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
* system 에 적합한 다른 stable mechanism

alternate path 는 original path 와 완벽히 일치할 필요가 없습니다. essential meaning 과 operation 을 보존해야 합니다.

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

system 은 essential functionality 로 가는 유일한 path 로 one primary sense 를 요구해서는 안 됩니다.

system 은 sight, sound 또는 touch 를 primary experience 로 사용할 수 있습니다. 그러나 그 sense 가 unavailable 할 때 user 는 remaining sensory paths 를 통해 essential system 을 이해하고 조작할 합리적인 방법을 가져야 합니다.

essential information 또는 interaction 이 다음만을 통해 available 한 경우 system 은 review 에 fail 할 수 있습니다.

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

sight 가 unavailable 할 때 system 은 sound 와 touch 를 통해 reasonably usable 한 상태로 남아야 합니다.

이는 essential visual information 이 meaningful non-visual access path 를 가져야 한다는 뜻입니다.

system 은 다음을 통해 이 requirement 를 만족할 수 있습니다.

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

system 은 다음에만 exclusively rely 해서는 안 됩니다.

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

그 information 이 essential functionality 를 이해하거나 조작하는 데 필요한 경우입니다.

user 가 sight 없이 essential system 을 reasonably navigate, understand 또는 operate 할 수 없다면 system 은 이 case 에 fail 할 수 있습니다.

<a id="sound-unavailable"></a>

## Sound Unavailable

sound 가 unavailable 할 때 system 은 sight 와 touch 를 통해 reasonably usable 한 상태로 남아야 합니다.

이는 essential auditory information 이 meaningful non-auditory access path 를 가져야 한다는 뜻입니다.

system 은 다음을 통해 이 requirement 를 만족할 수 있습니다.

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

system 은 다음에만 exclusively rely 해서는 안 됩니다.

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

그 information 이 essential functionality 를 이해하거나 조작하는 데 필요한 경우입니다.

user 가 sound 없이 essential system 을 reasonably navigate, understand 또는 operate 할 수 없다면 system 은 이 case 에 fail 할 수 있습니다.

<a id="touch-unavailable"></a>

## Touch Unavailable

touch 가 unavailable 할 때 system 은 sight 와 sound 를 통해 reasonably usable 한 상태로 남아야 합니다.

이는 essential tactile information 과 touch-based operation 이 meaningful non-touch access path 를 가져야 한다는 뜻입니다.

system 은 다음을 통해 이 requirement 를 만족할 수 있습니다.

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

system 은 다음에만 exclusively rely 해서는 안 됩니다.

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
* alternatives 없는 direct manipulation

그 interaction 이 essential functionality 를 이해하거나 조작하는 데 필요한 경우입니다.

user 가 touch 없이 essential system 을 reasonably navigate, understand 또는 operate 할 수 없다면 system 은 이 case 에 fail 할 수 있습니다.

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

conforming system 은 reviewed system 에 적합한 stable accessibility mechanism 을 사용해야 합니다.

stable accessibility mechanism 은 fragile 또는 undocumented behavior 에 의존하지 않고 accessibility behavior 를 유지, 업데이트, review, 확장할 수 있게 해야 합니다.

stable accessibility mechanism 에는 다음이 포함될 수 있습니다.

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
* system 에 적합한 다른 stable structure

system 은 reasonable alternate access 를 막는 방식으로 essential functionality 를 구현하는 것을 피해야 합니다.

<a id="semantic-structure"></a>

### Semantic Structure

conforming system 은 meaningful content 또는 controls 를 제시할 때 semantic structure 를 제공해야 합니다.

Semantic structure 에는 다음이 포함될 수 있습니다.

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

Semantic structure 는 sight 가 unavailable 할 때 특히 중요합니다. assistive technologies 가 visual interfaces 를 non-visual output 으로 전달하기 위해 semantic information 에 의존하는 경우가 많기 때문입니다.

essential controls 또는 content 가 그 structure, labels 또는 relationships 를 alternate access paths 를 통해 사용할 수 없어 이해될 수 없다면 system 은 review 에 fail 할 수 있습니다.

<a id="alternate-output"></a>

### Alternate Output

conforming system 은 essential meaning 이 unavailable sense 에 의존하게 될 때 reasonable alternate output 을 제공해야 합니다.

Alternate output 에는 다음이 포함될 수 있습니다.

* auditory information 을 위한 visual output
* visual information 을 위한 auditory output
* visual 또는 auditory information 을 위한 tactile output
* text equivalents
* captions
* transcripts
* spoken descriptions
* visible status messages
* haptic confirmation
* another appropriate output path

Alternate output 은 essential meaning 을 보존해야 합니다.

<a id="alternate-input"></a>

### Alternate Input

conforming system 은 essential operation 이 touch alone 에 의존하게 될 때 reasonable alternate input 을 제공해야 합니다.

Alternate input 에는 다음이 포함될 수 있습니다.

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input 은 가장 빠르거나 가장 편리한 input method 일 필요는 없습니다. essential operation 에 충분해야 합니다.

<a id="accessible-feedback"></a>

### Accessible Feedback

conforming system 은 essential actions 에 대해 accessible feedback 을 제공해야 합니다.

Accessible feedback 에는 다음이 포함될 수 있습니다.

* action 이 발생했다는 confirmation
* action 이 실패했다는 indication
* progress information
* validation messages
* warning messages
* error messages
* completion status
* current selection
* current focus
* current mode
* current system state

Feedback 은 관련 accessibility case 에서 unavailable sense 에만 exclusively rely 해서는 안 됩니다.

예를 들어 sound 가 unavailable 할 때 sound-only success chime 은 충분하지 않습니다. sight 가 unavailable 할 때 color-only error state 는 충분하지 않습니다. touch 가 unavailable 할 때 vibration-only confirmation 은 충분하지 않습니다.

<a id="accessible-configuration"></a>

### Accessible Configuration

conforming system 은 이 specification 이 정의한 같은 accessibility requirements 를 통해 users 가 required accessibility settings 에 도달하고 사용할 수 있게 해야 합니다.

Accessibility settings 는 inaccessible path 뒤에 숨겨져서는 안 됩니다.

예를 들어 user 가 먼저 unlabeled visual-only menu 를 navigate 해야만 enable 할 수 있다면 screen-reader-compatible mode 는 충분하지 않습니다.

system 의 accessibility configuration 이 support 하려는 condition 에서 도달하거나 조작할 수 없다면 system 은 review 에 fail 할 수 있습니다.

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

system 은 CatalystUI Team 이 system 을 review 하고 A11YSPEC 을 만족한다고 합리적으로 결론 내렸을 때 within spec 으로 간주됩니다.

system 은 다음 경우 within spec 일 수 있습니다.

* sight-unavailable use 가 reasonably supported 됨
* sound-unavailable use 가 reasonably supported 됨
* touch-unavailable use 가 reasonably supported 됨
* essential functionality 가 각 required case 에서 accessible 함
* critical functionality 가 각 required case 에서 accessible 함
* alternate access paths 가 essential meaning 과 operation 을 보존함
* accessibility settings 가 존재할 때 accessible 하게 도달하고 사용할 수 있음
* system 이 essential functionality 를 one required sense 뒤에 가두지 않음
* system 이 design 에 적합한 stable accessibility mechanism 을 사용함

experiences 가 모든 sensory paths 에서 identical 하지 않아도 system 은 within spec 일 수 있습니다.

some nonessential functionality 가 모든 required accessibility case 에서 equally available 하지 않아도 system 은 within spec 일 수 있습니다.

<a id="warnings"></a>

### Warnings

system 이 A11YSPEC 을 만족하는 것처럼 보이지만 documented 되어야 할 concerns 를 포함할 때 warning 이 issued 될 수 있습니다.

Warnings 에는 다음이 포함될 수 있습니다.

* one accessibility case 에서 unavailable 한 minor nonessential content
* slower but usable alternate access paths
* imperfect but understandable captions or transcripts
* limited but functional keyboard navigation
* limited but functional screen-reader support
* essential use 를 막지 않는 minor focus-order concerns
* one path 에서 missing 된 redundant visual, auditory, or tactile cues
* usable 하지만 찾기 어려운 accessibility settings
* works 하지만 더 clear 할 수 있는 assistive-technology support
* equally accessible 하지 않은 optional workflows

Warnings 는 반드시 verification 을 막지는 않습니다.

<a id="failures"></a>

### Failures

failure 는 system 이 A11YSPEC 의 하나 이상의 required conditions 를 만족하지 않을 때 발생합니다.

Failures 에는 다음이 포함될 수 있습니다.

* sight 가 unavailable 할 때 essential functionality unavailable
* sound 가 unavailable 할 때 essential functionality unavailable
* touch 가 unavailable 할 때 essential functionality unavailable
* required accessibility case 중 하나에서 critical functionality unavailable
* essential visual information 에 reasonable alternate access path 없음
* essential auditory information 에 reasonable alternate access path 없음
* essential touch-based operation 에 reasonable alternate access path 없음
* support 해야 하는 condition 에서 accessibility settings 에 도달할 수 없음
* non-visual use 에 필요할 때 meaningful labels or structure 없는 controls
* visual, tactile 또는 text equivalent 없는 sound-only warnings
* non-visual equivalent 없는 color-only status
* keyboard, pointer, voice, switch 또는 other alternative 없는 gesture-only operation
* visual 또는 auditory equivalent 없는 haptic-only confirmation
* essential workflows 에 대한 broken assistive-technology support
* major navigation traps
* unavailable sense 없이는 완료할 수 없는 essential workflows

Failures 는 resolved 될 때까지 verification 을 막습니다.

<a id="verification-validity"></a>

### Verification Validity

A11YSPEC verification 은 verification 이 issued 된 시점의 reviewed state of the system 에만 적용됩니다.

system 은 verified accessibility foundation 을 보존하는 한 later updates across verification 을 유지할 수 있습니다.

minor wording changes, visual refinements, performance improvements, added accessibility features, ordinary content updates 는 verification 을 자동으로 invalidate 하지 않습니다.

system 이 다음을 수행하면 new review 가 필요할 수 있습니다.

* alternate access paths 제거
* assistive-technology support 파손
* essential navigation 을 substantial 하게 변경
* required accessibility settings 제거
* verified accessibility 에 영향을 주는 방식으로 interaction behavior 변경
* accessible alternatives 없는 new essential workflows 도입
* previously accessible critical functionality 를 inaccessible 하게 만듦
* accessible behavior 를 single-sense-dependent behavior 로 대체

다시 말해, accessibility 를 개선하는 것은 보통 괜찮습니다.

verified access model 을 깨뜨리는 것은 review 를 필요로 할 수 있습니다.
