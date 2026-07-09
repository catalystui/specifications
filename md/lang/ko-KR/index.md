<!-- 이 번역은 ChatGPT에 의해 생성되었으며 사람 번역자의 검토가 필요합니다. -->

<!-- 번역이 확인된 후 pull request에서 이 줄들을 삭제하세요. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

CatalystUI 접근성 검증 문서에 오신 것을 환영합니다.

**CatalystUI Verified for Accessibility** 는 service, framework, application, library 또는 system 이 CatalystUI Team 의 검토를 받았으며, user-interface interaction 에 관여하는 세 가지 주요 감각 중 하나가 개별적으로 사용할 수 없는 상태에서도 합리적으로 사용할 수 있다고 판단되었음을 나타냅니다.

이 검증에서 CatalystUI 는 세 가지 primary accessibility senses 를 **sight**, **sound**, **touch** 로 식별합니다. verified system 은 이 중 어느 하나가 사용할 수 없을 때에도 남아 있는 sensory domains 를 통해 essential functionality 에 대한 reasonable access 를 보존해야 합니다.

더 쉽게 말하면, 이 검증은 user 가 sight, sound, touch 중 하나에 개별적으로 의존할 수 없을 때에도 system 의 essential parts 를 의미 있게 이해하고, 탐색하고, 조작할 수 있는지를 묻습니다.

## Purpose

Accessibility 가 중요한 이유는, 동일한 essential meaning 을 다른 sensory pathway 로 합리적으로 전달할 수 있다면 user interface 가 하나의 sensory pathway 에 전적으로 의존해서는 안 되기 때문입니다.

CatalystUI 는 systems 와 human perception 사이에서 data 가 충실하게 이동하는 것을 중심으로 설계되었습니다. 중요한 information 이 오직 visible 하거나, 오직 audible 하거나, 오직 touch 를 통해서만 제공된다면, 그 sense 에 의존할 수 없는 users 에게 system 은 사용할 수 없게 될 수 있습니다. Accessibility Verification 은 essential information 과 interaction 이 alternate sensory routes 를 통해 계속될 수 있도록 access 를 보존하는 systems 를 식별하기 위해 존재합니다.

목표는 모든 possible interaction method, 모든 assistive technology, 모든 specialized accommodation 을 요구하는 것이 아닙니다. 목표는 sight, sound, touch 중 하나가 개별적으로 사용할 수 없을 때에도 essential system 이 meaningfully usable 한 상태로 남는지를 판단하는 것입니다.

## What Verification Means

system 은 이 section 에 나열된 requirements 에 따라 review 되고 within spec 으로 판단될 때 **CatalystUI Verified for Accessibility** 가 됩니다.

검증을 받으려면 system 은 다음 각 경우에 합리적으로 usable 해야 합니다.

| Unavailable Sense | Required Accessibility Behavior                                   |
| ----------------- | ----------------------------------------------------------------- |
| Sight             | system 은 sound 와 touch 를 통해 reasonable usable 상태를 유지해야 합니다. |
| Sound             | system 은 sight 와 touch 를 통해 reasonable usable 상태를 유지해야 합니다. |
| Touch             | system 은 sight 와 sound 를 통해 reasonable usable 상태를 유지해야 합니다. |

system 이 모든 sensory path 에서 동일한 experiences 를 제공할 필요는 없습니다. non-visual experience 는 visual one 보다 느릴 수 있습니다. sound-free experience 는 captions, visual indicators 또는 다른 substitutions 를 요구할 수 있습니다. touch-free experience 는 alternate controls, voice interaction, keyboard navigation, pointer navigation 또는 다른 non-touch methods 를 요구할 수 있습니다.

중요한 것은 essential functionality 가 unavailable sense 를 요구하지 않고도 accessible, understandable, operable 한 상태로 남는지입니다.

## Essential Functionality

Accessibility Verification 에서 **essential functionality** 는 user 가 system 을 이해하고, 탐색하고, 설정하고, 조작하기 위해 합리적으로 필요한 부분을 의미합니다.

Essential functionality 에는 다음이 포함될 수 있습니다.

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
* normal use 에 필요한 interaction

decorative, redundant, optional 또는 nonessential features 가 모든 sensory path 에서 동등하게 제공되지 않더라도 system 은 within spec 일 수 있습니다. 그러나 user 가 missing sense 때문에 essential system 을 사용할 수 없게 막혀서는 안 됩니다.

## Sight Unavailable

sight 를 사용할 수 없을 때 system 은 sound 와 touch 를 통해 합리적으로 usable 해야 합니다.

여기에는 spoken output, screen-reader-compatible structure, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions 또는 essential information 을 전달하기 위한 다른 reasonable non-visual method 가 포함될 수 있습니다.

essential functionality 를 이해하거나 조작하는 데 필요한 information 에 대해 system 은 visual position, color, shape, animation, icons 또는 layout 에만 의존해서는 안 됩니다.

## Sound Unavailable

sound 를 사용할 수 없을 때 system 은 sight 와 touch 를 통해 합리적으로 usable 해야 합니다.

여기에는 captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback 또는 essential information 을 전달하기 위한 다른 reasonable non-auditory method 가 포함될 수 있습니다.

essential functionality 를 이해하거나 조작하는 데 필요한 information 에 대해 system 은 sound effects, spoken instructions, alerts, alarms, music cues 또는 audio-only prompts 에만 의존해서는 안 됩니다.

## Touch Unavailable

touch 를 사용할 수 없을 때 system 은 sight 와 sound 를 통해 합리적으로 usable 해야 합니다.

여기에는 voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation 또는 touch-based interaction 이나 tactile perception 을 요구하지 않는 다른 reasonable method 가 포함될 수 있습니다.

essential functionality 를 이해하거나 조작하는 데 필요한 interactions 에 대해 system 은 touch gestures, haptic feedback, physical texture, vibration, force, pressure 또는 touch-only controls 에만 의존해서는 안 됩니다.

## Additional Sensory Domains

CatalystUI 는 **taste** 와 **smell** 도 sensory domains 로 인식합니다. system 이 이 domains 를 의미 있게 사용할 때 accessibility review 에서 고려될 수 있습니다.

taste 와 smell 은 verification 에서 **inclusive** 입니다. 즉, meaningful alternate access 또는 additional context 를 제공할 때 accessibility review 를 강화하거나 지원할 수 있습니다.

taste 와 smell 은 현재 failure 에 대해 **exclusive** 하지 않습니다. 즉 system 이 taste-based 또는 smell-based interaction 을 제공하지 않는다는 이유만으로 Accessibility Verification 에 실패하지 않습니다.

CatalystUI Accessibility Verification 은 주로 sight, sound, touch 중 하나가 개별적으로 unavailable 할 때 system 이 reasonably usable 한지에 관심을 둡니다.

## What “Within Spec” Means

system 이 **within spec** 으로 간주된다는 것은 CatalystUI Team 이 system 을 수동으로 review 했고, 이 verification category 가 설명하는 accessibility requirements 를 만족한다고 합리적으로 결론 내렸다는 뜻입니다.

이는 하나의 rigid implementation pattern 을 요구하지 않습니다. system 은 native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration 또는 system 에 적합한 다른 stable mechanism 을 통해 accessibility requirements 를 만족할 수 있습니다.

verification 은 system 이 특정 accessibility architecture 를 사용하는지보다, one primary sense 가 unavailable 할 때 users 가 essential system 에 practical access 할 수 있는지에 관심을 둡니다.

## What Verification Does Not Mean

CatalystUI Verified for Accessibility 는 가능한 모든 disability, device, assistive technology, medical condition, legal requirement, regional standard 또는 specialized use case 가 완전히 review 되었다는 것을 보장하지 않습니다.

또한 reviewed accessibility scope 에 포함되지 않는 한 internationalization, translation quality, typography, localization, regional compliance 또는 general design quality 를 자동으로 검증하지 않습니다.

system 은 CatalystUI 의 accessibility model 아래에서 reasonably accessible 할 수 있지만, legal compliance, platform certification, specialized assistive technology support 또는 다른 accessibility standards 를 위해 별도 review 가 필요할 수 있습니다.

## Why This Verification Exists

user interface 는 users 가 실제로 사용할 수 있을 때에만 성공합니다.

많은 systems 는 accessibility 를 human-computer interaction 의 fundamental part 가 아니라 사후 처리, checklist 또는 좁은 technical requirement 로 취급합니다. CatalystUI 는 더 단순하고 직접적인 approach 를 취합니다. system 이 human perception 에 의존한다면, one primary sensory path 가 unavailable 할 때에도 essential meaning 을 보존해야 합니다.

Accessibility Verification 은 이 책임을 진지하게 받아들이는 systems 를 식별하기 위해 존재합니다. meaningful alternate access 를 제공하고, essential functionality 를 보존하며, users 를 하나의 required sense 뒤에 가두지 않는 systems 를 인정합니다.

## Verification Scope

CatalystUI Verification for Accessibility 는 verification 이 issued 되었을 때 존재했던 reviewed system, service, framework, application, library 또는 implementation 에 적용됩니다.

verified system 은 reviewed conditions 아래에서 essential functionality 에 대해 reasonable accessibility 를 제공합니다. 이것은 모든 future page, feature, release, plugin, extension, third-party integration, device 또는 platform-specific version 이 자동으로 within spec 이라는 뜻이 아닙니다.

Separate products, modules, services, major revisions 또는 platform-specific builds 는 requested verification category 에 따라 별도 review 를 필요로 할 수 있습니다.

## Verification Validity

CatalystUI Verification 은 verification 이 issued 되었을 때 system 의 reviewed state 에만 적용됩니다.

system 은 verified accessibility foundation 을 보존하는 한 later updates 에서도 verification 을 유지할 수 있습니다. minor wording changes, visual refinements, performance improvements 및 ordinary content updates 는 verification 을 자동으로 invalidate 하지 않습니다.

system 이 alternate access paths 를 제거하거나, assistive-technology support 를 깨뜨리거나, essential navigation 을 크게 변경하거나, required accessibility settings 를 제거하거나, verified accessibility foundation 에 영향을 주는 방식으로 interaction behavior 를 변경하면 new review 가 필요할 수 있습니다.

다시 말해, accessibility 를 개선하는 것은 보통 괜찮습니다. verified access model 을 깨뜨리는 것은 review 를 필요로 할 수 있습니다.

## Verified Systems

accessibility 에 대해 verified 된 알려진 systems 는 적절한 CatalystUI Verified page 에 별도로 나열됩니다.
