<!-- この翻訳は ChatGPT によって生成されたものであり、人間の翻訳者による確認が必要です。 -->

<!-- 翻訳が確認された後、pull request でこれらの行を削除してください。 -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> ここに提示される definitions、requirements、concepts は practical accessibility support を説明するものであり、自由に再表現できます。

<a id="introduction"></a>

## Introduction

**Accessibility Specification (A11YSPEC)** は、CatalystUI ecosystem 内で accessibility support を評価するために使用される core concepts、terminology、requirements を定めます。その目的は、primary sensory pathway の一つが利用できない場合でも、system、service、framework、application、library、または implementation が meaningfully usable のままであるかを判断する明確な standard を提供することです。

Accessibility が重要なのは、同じ essential meaning を別の sense で合理的に伝えられる場合、user interface が一つの sense に完全に依存すべきではないからです。system は technically functional であっても、user が sight、sound、touch のいずれかを個別に使わずに essential behavior を理解し、移動し、設定し、操作できないなら、その condition に対して reasonable access を提供できていません。

この specification は、あらゆる disability、device、assistive technology、medical condition、legal requirement、regional accessibility standard、または specialized use case を検証しようとするものではありません。代わりに、三つの primary accessibility senses のうち一つが利用できない場合でも、users が system の essential portions に意味ある形で access し操作するために必要な最小限の accessibility foundation を定義します。

より簡単に言えば、A11YSPEC は三つの主要な questions を問います。

1. users は sight に頼らず essential system を理解できますか？
2. users は sound に頼らず essential system を理解できますか？
3. users は touch に頼らず essential system を操作できますか？

> [!IMPORTANT]
>
> A11YSPEC は verification のための accessibility requirements を定義します。これは legal accessibility standards、platform certification requirements、または specialized assistive-technology review の代替ではありません。system は A11YSPEC の範囲内であっても、他の accessibility standards のために additional review を必要とする場合があります。

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

system は、required accessibility case ごとにこの document で定義された requirements を満たすとき、A11YSPEC に conformant であると見なされます。

conforming system は次を満たさなければなりません。

1. sight が利用できない場合でも reasonably usable のままであること。
2. sound が利用できない場合でも reasonably usable のままであること。
3. touch が利用できない場合でも reasonably usable のままであること。
4. 各 required accessibility case で essential functionality への access を維持すること。
5. 各 required accessibility case ですべての critical functionality への access を維持すること。
6. essential meaning または operation が unavailable sense に依存してしまう場合、reasonable alternate access paths を提供すること。
7. reviewed system に適した stable accessibility mechanism を使用すること。
8. essential functionality のために one primary sense のみに依存することを避けること。

system は、すべての sensory path で同一の experience を提供する必要はありません。non-visual experience は visual one より遅いことがあります。sound-free experience は captions、visual indicators、または haptic confirmation を必要とすることがあります。touch-free experience は keyboard navigation、pointer alternatives、voice interaction、switch-compatible interaction、または別の non-touch method を必要とすることがあります。

Verification は identical presentation ではなく、essential functionality への practical access に関心を置きます。

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

A11YSPEC において、三つの primary accessibility senses は **sight**、**sound**、**touch** です。

これらの senses が primary なのは、user-interface interaction に関わる最も一般的な sensory pathways だからです。system は sight、sound、touch を通じて output を提供でき、touch、motion、voice、keyboard input、pointer input、switch input、または別の available input path を通じて interaction を受け取ることができます。

<a id="sight"></a>

### Sight

Sight は、user が visual output を知覚する visual sensory pathway です。

Sight は次の知覚に関わることがあります。

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

essential meaning または operation が user の visual information の知覚を必要とするとき、system は sight に依存しています。

<a id="sound"></a>

### Sound

Sound は、user が audio output を知覚する auditory sensory pathway です。

Sound は次の知覚に関わることがあります。

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

essential meaning または operation が user の hearing information を必要とするとき、system は sound に依存しています。

<a id="touch"></a>

### Touch

Touch は、user が physical または haptic output を知覚する tactile sensory pathway であり、direct contact、pressure、gesture、または movement によって controls を操作する physical interaction pathway でもあります。

Touch は次の知覚または実行に関わることがあります。

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

essential meaning または operation が reasonable alternate input or output path なしに tactile perception または touch-based interaction を必要とするとき、system は touch に依存しています。

<a id="additional-sensory-domains"></a>

### Additional Sensory Domains

CatalystUI は **taste** と **smell** も sensory domains として認識します。

Taste と smell は、system が意味ある形で使用している場合、accessibility review で考慮されることがあります。これらの senses は verification において inclusive であり、meaningful alternate access または additional context を提供するとき review を強化または支援できます。

Taste と smell は現在、failure のために exclusive ではありません。system が taste-based または smell-based interaction を提供しないだけで A11YSPEC に fail することはありません。

A11YSPEC は主に、sight、sound、touch のいずれか一つが個別に unavailable であるとき、system が reasonably usable のままであるかに関心を置きます。

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

conforming system は、各 required accessibility case に対して reviewed されなければなりません。

| Unavailable Sense | Required Accessibility Behavior                                   |
| ----------------- | ----------------------------------------------------------------- |
| Sight             | system は sound と touch を通じて reasonably usable のままでなければなりません。 |
| Sound             | system は sight と touch を通じて reasonably usable のままでなければなりません。 |
| Touch             | system は sight と sound を通じて reasonably usable のままでなければなりません。 |

各 case は個別に review されます。

reviewed scope にその condition が含まれていない限り、system は複数の primary senses が同時に unavailable である場合に fully usable のままである必要はありません。

system はあらゆる possible accommodation を提供する必要はありません。各 required accessibility case において essential functionality への reasonable access を提供しなければなりません。

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality は、user が system の essential behavior を理解し、移動し、設定し、操作するために合理的に必要とする behavior、content、control、output、input、workflow、または configuration です。

Essential functionality には次が含まれることがあります。

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
* normal use に必要な interaction

system は、decorative、optional、redundant、nonessential な features をすべての sensory path で同等に利用可能にする必要はありません。ただし、user が unavailable sense によって essential system の使用を blocked されてはなりません。

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality は essential functionality のうち、access を失うと meaningful use を妨げたり、serious error を引き起こしたり、user が consequence を理解せずに important decision を行う原因となったりするものです。

Critical functionality には次が含まれることがあります。

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
* accessibility settings に到達するために必要な core navigation

Critical functionality は各 required accessibility case で accessible のままでなければなりません。

critical functionality が unavailable sense のみに依存している場合、system は A11YSPEC に fail することがあります。

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality は、user が system の essential behavior を理解し、移動し、設定し、操作するために合理的に必要ではない functionality です。

Nonessential functionality には次が含まれることがあります。

* decorative animation
* optional effects
* cosmetic visual polish
* nonessential sound effects
* redundant haptic effects
* optional marketing content
* optional tutorial content
* hidden diagnostic behavior
* developer-facing controls
* reviewed scope 外の experimental features

Nonessential functionality は、一つ以上の accessibility cases で inaccessible であっても、自動的に failure になるとは限りません。ただし、support するのが不便だからといって nonessential functionality を essential functionality と混同すべきではありません。

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

system は、各 required accessibility case で essential functionality が reasonably understandable、navigable、configurable、operable のままであるとき、essential access requirement を満たします。

essential experience はすべての senses で同一である必要はありません。

essential experience は meaningfully usable のままでなければなりません。

<a id="critical-access-requirement"></a>

### Critical Access Requirement

system は、すべての critical functionality が各 required accessibility case で accessible のままであるとき、critical access requirement を満たします。

Critical functionality は one required sensory pathway の背後に隠されてはなりません。

たとえば、ordinary use のために accessible interface を提供している一方で、account deletion warnings、payment confirmations、privacy decisions、または accessibility settings を sight、sound、touch の一つだけに依存させるべきではありません。

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

system は、one primary sense を通じて提供される essential meaning または operation が、その sense が unavailable のとき別の sensory or interaction path でも合理的に利用可能である場合、alternate access requirement を満たします。

Alternate access は次によって提供されることがあります。

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
* system に適した別の stable mechanism

alternate path は original path と完全に一致する必要はありません。essential meaning と operation を維持しなければなりません。

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

system は、essential functionality への唯一の path として one primary sense を要求してはなりません。

system は sight、sound、touch を primary experience として使用できます。ただし、その sense が unavailable のとき、user は残りの sensory paths を通じて essential system を理解し操作する合理的な方法を持たなければなりません。

essential information または interaction が次のみによって利用可能な場合、system は review に fail することがあります。

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

sight が unavailable である場合、system は sound と touch を通じて reasonably usable のままでなければなりません。

これは、essential visual information が meaningful non-visual access path を持たなければならないことを意味します。

system は次によってこの requirement を満たすことがあります。

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

system は次に exclusively rely すべきではありません。

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

その information が essential functionality を理解または操作するために必要な場合。

user が sight なしで essential system を合理的に navigate、understand、operate できない場合、system はこの case に fail することがあります。

<a id="sound-unavailable"></a>

## Sound Unavailable

sound が unavailable である場合、system は sight と touch を通じて reasonably usable のままでなければなりません。

これは、essential auditory information が meaningful non-auditory access path を持たなければならないことを意味します。

system は次によってこの requirement を満たすことがあります。

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

system は次に exclusively rely すべきではありません。

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

その information が essential functionality を理解または操作するために必要な場合。

user が sound なしで essential system を合理的に navigate、understand、operate できない場合、system はこの case に fail することがあります。

<a id="touch-unavailable"></a>

## Touch Unavailable

touch が unavailable である場合、system は sight と sound を通じて reasonably usable のままでなければなりません。

これは、essential tactile information と touch-based operation が meaningful non-touch access path を持たなければならないことを意味します。

system は次によってこの requirement を満たすことがあります。

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

system は次に exclusively rely すべきではありません。

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
* alternatives のない direct manipulation

その interaction が essential functionality を理解または操作するために必要な場合。

user が touch なしで essential system を合理的に navigate、understand、operate できない場合、system はこの case に fail することがあります。

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

conforming system は、reviewed system に適した stable accessibility mechanism を使用しなければなりません。

stable accessibility mechanism は、fragile または undocumented behavior に依存せずに accessibility behavior を維持、更新、review、拡張できるようにすべきです。

stable accessibility mechanism には次が含まれることがあります。

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
* system に適した別の stable structure

system は reasonable alternate access を妨げる方法で essential functionality を実装することを避けるべきです。

<a id="semantic-structure"></a>

### Semantic Structure

conforming system は、meaningful content または controls を提示するとき semantic structure を提供すべきです。

Semantic structure には次が含まれることがあります。

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

Semantic structure は sight が unavailable のとき特に重要です。assistive technologies は visual interfaces を non-visual output として伝えるために semantic information に依存することが多いからです。

essential controls または content が、その structure、labels、relationships を alternate access paths を通じて利用できないために理解できない場合、system は review に fail することがあります。

<a id="alternate-output"></a>

### Alternate Output

conforming system は、essential meaning が unavailable sense に依存してしまう場合、reasonable alternate output を提供しなければなりません。

Alternate output には次が含まれることがあります。

* auditory information のための visual output
* visual information のための auditory output
* visual または auditory information のための tactile output
* text equivalents
* captions
* transcripts
* spoken descriptions
* visible status messages
* haptic confirmation
* another appropriate output path

Alternate output は essential meaning を維持しなければなりません。

<a id="alternate-input"></a>

### Alternate Input

conforming system は、essential operation が touch alone に依存してしまう場合、reasonable alternate input を提供しなければなりません。

Alternate input には次が含まれることがあります。

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input は最速または最も便利な input method である必要はありません。essential operation に十分でなければなりません。

<a id="accessible-feedback"></a>

### Accessible Feedback

conforming system は、essential actions に対して accessible feedback を提供しなければなりません。

Accessible feedback には次が含まれることがあります。

* action が発生した confirmation
* action が失敗した indication
* progress information
* validation messages
* warning messages
* error messages
* completion status
* current selection
* current focus
* current mode
* current system state

Feedback は関連する accessibility case で unavailable sense のみに依存してはなりません。

たとえば、sound が unavailable のとき sound-only success chime は十分ではありません。sight が unavailable のとき color-only error state は十分ではありません。touch が unavailable のとき vibration-only confirmation は十分ではありません。

<a id="accessible-configuration"></a>

### Accessible Configuration

conforming system は、この specification によって定義される同じ accessibility requirements を通じて、users が required accessibility settings に到達し使用できるようにしなければなりません。

Accessibility settings は inaccessible path の背後に隠されてはなりません。

たとえば、screen-reader-compatible mode は、user がそれを有効にするために最初に unlabeled visual-only menu を navigate しなければならないなら十分ではありません。

system の accessibility configuration が、それが support する intended condition で到達または操作できない場合、system は review に fail することがあります。

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

system は、CatalystUI Team が system を review し、A11YSPEC を満たしていると合理的に結論づけたとき within spec と見なされます。

system は次の場合 within spec であり得ます。

* sight-unavailable use が reasonably supported のままである
* sound-unavailable use が reasonably supported のままである
* touch-unavailable use が reasonably supported のままである
* essential functionality が各 required case で accessible のままである
* critical functionality が各 required case で accessible のままである
* alternate access paths が essential meaning と operation を維持している
* accessibility settings が存在する場合、accessible に到達し使用できる
* system が essential functionality を one required sense の背後に閉じ込めていない
* system がその design に適した stable accessibility mechanism を使用している

experiences がすべての sensory paths で identical でなくても、system は within spec であり得ます。

some nonessential functionality が各 required accessibility case で同等に利用可能でなくても、system は within spec であり得ます。

<a id="warnings"></a>

### Warnings

system が A11YSPEC を満たしているように見えるものの、documented すべき concerns を含む場合、warning が issued されることがあります。

Warnings には次が含まれることがあります。

* one accessibility case で利用できない minor nonessential content
* slower but usable alternate access paths
* imperfect but understandable captions or transcripts
* limited but functional keyboard navigation
* limited but functional screen-reader support
* essential use を妨げない minor focus-order concerns
* one path から missing している redundant visual, auditory, or tactile cues
* usable だが見つけにくい accessibility settings
* works するが clearer にできる assistive-technology support
* equally accessible ではない optional workflows

Warnings は必ずしも verification を妨げません。

<a id="failures"></a>

### Failures

failure は、system が A11YSPEC の一つ以上の required conditions を満たさない場合に発生します。

Failures には次が含まれることがあります。

* sight が unavailable のとき essential functionality が unavailable
* sound が unavailable のとき essential functionality が unavailable
* touch が unavailable のとき essential functionality が unavailable
* required accessibility case のいずれかで critical functionality が unavailable
* essential visual information に reasonable alternate access path がない
* essential auditory information に reasonable alternate access path がない
* essential touch-based operation に reasonable alternate access path がない
* intended condition で accessibility settings に到達できない
* non-visual use に必要なとき meaningful labels or structure のない controls
* visual、tactile、text equivalent のない sound-only warnings
* non-visual equivalent のない color-only status
* keyboard、pointer、voice、switch、または other alternative のない gesture-only operation
* visual または auditory equivalent のない haptic-only confirmation
* essential workflows の broken assistive-technology support
* major navigation traps
* unavailable sense なしでは完了できない essential workflows

Failures は resolved されるまで verification を妨げます。

<a id="verification-validity"></a>

### Verification Validity

A11YSPEC verification は、verification が issued された時点の reviewed state of the system にのみ適用されます。

system は、verified accessibility foundation を維持する限り、later updates across verification を保持できます。

minor wording changes、visual refinements、performance improvements、added accessibility features、ordinary content updates は verification を自動的に invalidate しません。

system が次を行う場合、新しい review が必要になることがあります。

* alternate access paths を削除する
* assistive-technology support を壊す
* essential navigation を大幅に変更する
* required accessibility settings を削除する
* verified accessibility に影響する方法で interaction behavior を変更する
* accessible alternatives のない new essential workflows を導入する
* previously accessible critical functionality を inaccessible にする
* accessible behavior を single-sense-dependent behavior に置き換える

言い換えれば、accessibility を改善することは通常問題ありません。

verified access model を壊すことは review を必要とする場合があります。
