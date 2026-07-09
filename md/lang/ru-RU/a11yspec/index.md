<!-- Этот перевод был создан ChatGPT и должен быть проверен человеком-переводчиком. -->

<!-- Удалите эти строки в pull request после проверки перевода. -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Представленные здесь определения, требования и концепции описывают практическую поддержку доступности и могут свободно переизлагаться.

<a id="introduction"></a>

## Введение

**Accessibility Specification (A11YSPEC)** устанавливает core concepts, terminology и requirements, используемые для оценки accessibility support в экосистеме CatalystUI. Ее цель — предоставить ясный standard для определения того, остается ли system, service, framework, application, library или implementation meaningfully usable, когда одна primary sensory pathway недоступна.

Доступность важна, потому что user interface не должен полностью зависеть от одного sense, если то же essential meaning можно разумно передать через другой. System может быть technically functional, но если user не может понять, навигировать, настроить или использовать ее essential behavior без зрения, звука или осязания по отдельности, то system не обеспечила reasonable access для этого condition.

Эта specification не пытается проверить каждую возможную disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard или specialized use case. Вместо этого она определяет минимальную accessibility foundation, необходимую для того, чтобы users могли meaningful access и operate essential portions системы, когда один из трех primary accessibility senses недоступен.

Проще говоря, A11YSPEC задает три основных вопроса:

1. Могут ли users понять essential system, не полагаясь на зрение?
2. Могут ли users понять essential system, не полагаясь на звук?
3. Могут ли users operate essential system, не полагаясь на осязание?

> [!IMPORTANT]
>
> A11YSPEC определяет accessibility requirements для verification. Она не заменяет legal accessibility standards, platform certification requirements или specialized assistive-technology review. System может быть within A11YSPEC и все равно требовать additional review для других accessibility standards.

<a id="table-of-contents"></a>

## Содержание

- [A11YSPEC](#a11yspec)
  - [Введение](#introduction)
  - [Содержание](#table-of-contents)
  - [Соответствие](#conformance)
  - [Основные чувства доступности](#primary-accessibility-senses)
    - [Зрение](#sight)
    - [Звук](#sound)
    - [Осязание](#touch)
    - [Дополнительные сенсорные домены](#additional-sensory-domains)
  - [Обязательные случаи доступности](#required-accessibility-cases)
  - [Essential Functionality](#essential-functionality)
    - [Essential Functionality](#essential-functionality-1)
    - [Critical Functionality](#critical-functionality)
    - [Nonessential Functionality](#nonessential-functionality)
  - [Требования доступности](#accessibility-requirements)
    - [Требование essential access](#essential-access-requirement)
    - [Требование critical access](#critical-access-requirement)
    - [Требование alternate access](#alternate-access-requirement)
    - [Отсутствие зависимости от одного чувства](#no-single-sense-dependency)
  - [Недоступно зрение](#sight-unavailable)
  - [Недоступен звук](#sound-unavailable)
  - [Недоступно осязание](#touch-unavailable)
  - [Требования реализации](#implementation-requirements)
    - [Стабильный механизм доступности](#stable-accessibility-mechanism)
    - [Семантическая структура](#semantic-structure)
    - [Alternate Output](#alternate-output)
    - [Alternate Input](#alternate-input)
    - [Accessible Feedback](#accessible-feedback)
    - [Accessible Configuration](#accessible-configuration)
  - [Проверка](#verification)
    - [Within Spec](#within-spec)
    - [Предупреждения](#warnings)
    - [Ошибки проверки](#failures)
    - [Действительность проверки](#verification-validity)

<a id="conformance"></a>

## Соответствие

System считается conformant with A11YSPEC, когда она удовлетворяет requirements, определенным этим документом для каждого required accessibility case.

Conforming system должен:

1. Оставаться разумно пригодным к использованию, когда зрение недоступно.
2. Оставаться разумно пригодным к использованию, когда звук недоступен.
3. Оставаться разумно пригодным к использованию, когда осязание недоступно.
4. Сохранять access to essential functionality в каждом required accessibility case.
5. Сохранять access to all critical functionality в каждом required accessibility case.
6. Предоставлять reasonable alternate access paths, когда essential meaning или operation иначе зависели бы от unavailable sense.
7. Использовать stable accessibility mechanism, соответствующий reviewed system.
8. Избегать exclusive reliance на один primary sense для essential functionality.

System не обязана предоставлять identical experiences по всем sensory paths. Non-visual experience может быть медленнее visual. Sound-free experience может требовать captions, visual indicators или haptic confirmation. Touch-free experience может требовать keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction или другой non-touch method.

Verification касается practical access к essential functionality, а не identical presentation.

<a id="primary-accessibility-senses"></a>

## Основные чувства доступности

Для A11YSPEC три primary accessibility senses — это **зрение**, **звук** и **осязание**.

Эти senses являются primary, потому что это наиболее распространенные sensory pathways, участвующие в user-interface interaction. System может предоставлять output через зрение, звук или осязание и получать interaction через touch, motion, voice, keyboard input, pointer input, switch input или другой available input path.

<a id="sight"></a>

### Зрение

Зрение — это visual sensory pathway, через которую user воспринимает visual output.

Зрение может участвовать в восприятии:

* текста
* цвета
* формы
* позиции
* layout
* animation
* icons
* images
* video
* visual warnings
* visual status indicators
* visible controls

System зависит от зрения, когда essential meaning или operation требует, чтобы user визуально воспринимал информацию.

<a id="sound"></a>

### Звук

Звук — это auditory sensory pathway, через которую user воспринимает audio output.

Звук может участвовать в восприятии:

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

System зависит от звука, когда essential meaning или operation требует, чтобы user слышал информацию.

<a id="touch"></a>

### Осязание

Осязание — это tactile sensory pathway, через которую user воспринимает physical или haptic output, а также physical interaction pathway, через которую user может operate controls через direct contact, pressure, gesture или movement.

Осязание может участвовать в восприятии или выполнении:

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

System зависит от осязания, когда essential meaning или operation требует tactile perception или touch-based interaction без reasonable alternate input or output path.

<a id="additional-sensory-domains"></a>

### Дополнительные сенсорные домены

CatalystUI также признает **вкус** и **запах** как sensory domains.

Вкус и запах могут учитываться во время accessibility review, когда они meaningfully used by the system. Эти senses являются inclusive for verification, то есть могут усилить или поддержать accessibility review, когда дают meaningful alternate access или additional context.

Вкус и запах сейчас не являются exclusive for failure. System не проваливает A11YSPEC просто потому, что не предоставляет taste-based или smell-based interaction.

A11YSPEC прежде всего касается того, остается ли system reasonably usable, когда зрение, звук или осязание individually unavailable.

<a id="required-accessibility-cases"></a>

## Обязательные случаи доступности

Conforming system должен быть reviewed against each required accessibility case.

| Недоступное чувство | Требуемое поведение доступности |
| ------------------- | ----------------------------------------------------------------- |
| Зрение              | System должна оставаться reasonably usable через звук и осязание. |
| Звук                | System должна оставаться reasonably usable через зрение и осязание. |
| Осязание            | System должна оставаться reasonably usable через зрение и звук. |

Каждый case рассматривается индивидуально.

System не обязана оставаться fully usable, когда несколько primary senses недоступны одновременно, если этот condition не включен в reviewed scope.

System не обязана предоставлять every possible accommodation. Она должна предоставлять reasonable access to essential functionality в каждом required accessibility case.

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality — это любое behavior, content, control, output, input, workflow или configuration, которое user разумно нужно, чтобы понять, навигировать, настроить или operate essential behavior системы.

Essential functionality может включать:

* primary navigation
* core workflows
* required controls
* важные предупреждения
* важные ошибки
* required confirmation messages
* account or session access
* settings and preferences
* language configuration
* accessibility configuration
* essential instructions
* user-facing status information
* any interaction required for normal use

System не обязана делать каждую decorative, optional, redundant или nonessential feature одинаково доступной через каждый sensory path. Однако user не должен быть blocked from using the essential system из-за unavailable sense.

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality — это essential functionality, потеря доступа к которой может prevent meaningful use, создать serious error или заставить user принять важное решение без understanding the consequence.

Critical functionality может включать:

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

System может fail A11YSPEC, если critical functionality depends exclusively on the unavailable sense.

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality — это functionality, которая не является reasonably required, чтобы user понимал, навигировал, настраивал или operate essential behavior системы.

Nonessential functionality может включать:

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

Nonessential functionality может быть inaccessible в одном или нескольких accessibility cases без автоматического failure. Однако nonessential functionality не следует путать с essential functionality только потому, что ее support неудобен.

<a id="accessibility-requirements"></a>

## Требования доступности

<a id="essential-access-requirement"></a>

### Требование essential access

System satisfies the essential access requirement, когда essential functionality остается reasonably understandable, navigable, configurable и operable в каждом required accessibility case.

Essential experience не обязана быть identical across all senses.

Essential experience должна оставаться meaningfully usable.

<a id="critical-access-requirement"></a>

### Требование critical access

System satisfies the critical access requirement, когда вся critical functionality остается accessible в каждом required accessibility case.

Critical functionality не должна быть hidden behind one required sensory pathway.

Например, system не должна предоставлять accessible interface для ordinary use, оставляя account deletion warnings, payment confirmations, privacy decisions или accessibility settings зависимыми только от зрения, звука или осязания.

<a id="alternate-access-requirement"></a>

### Требование alternate access

System satisfies the alternate access requirement, когда essential meaning или operation, предоставленные через один primary sense, также reasonably available через другой sensory or interaction path, когда этот sense unavailable.

Alternate access может быть предоставлен через:

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

Alternate path не должна perfectly match original path. Она должна preserve essential meaning and operation.

<a id="no-single-sense-dependency"></a>

### Отсутствие зависимости от одного чувства

System must not require one primary sense как единственный путь к essential functionality.

System может использовать зрение, звук или осязание как primary experience. Однако когда этот sense unavailable, user все равно должен иметь reasonable way to understand and operate essential system через remaining sensory paths.

System может fail review, когда essential information или interaction доступна только через:

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

## Недоступно зрение

Когда зрение недоступно, system должна оставаться reasonably usable через звук и осязание.

Это означает, что essential visual information должна иметь meaningful non-visual access path.

System может удовлетворить это requirement через:

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

System не должна rely exclusively on:

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

когда эта information required to understand or operate essential functionality.

System может fail this case, если user не может reasonably navigate, understand, or operate essential system без зрения.

<a id="sound-unavailable"></a>

## Недоступен звук

Когда звук недоступен, system должна оставаться reasonably usable через зрение и осязание.

Это означает, что essential auditory information должна иметь meaningful non-auditory access path.

System может удовлетворить это requirement через:

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

System не должна rely exclusively on:

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

когда эта information required to understand or operate essential functionality.

System может fail this case, если user не может reasonably navigate, understand, or operate essential system без звука.

<a id="touch-unavailable"></a>

## Недоступно осязание

Когда осязание недоступно, system должна оставаться reasonably usable через зрение и звук.

Это означает, что essential tactile information и touch-based operation должны иметь meaningful non-touch access path.

System может удовлетворить это requirement через:

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

System не должна rely exclusively on:

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

когда эта interaction required to understand or operate essential functionality.

System может fail this case, если user не может reasonably navigate, understand, or operate essential system без осязания.

<a id="implementation-requirements"></a>

## Требования реализации

<a id="stable-accessibility-mechanism"></a>

### Стабильный механизм доступности

Conforming system должна использовать stable accessibility mechanism, appropriate to the system being reviewed.

Stable accessibility mechanism должен позволять accessibility behavior поддерживать, обновлять, review и расширять без reliance on fragile or undocumented behavior.

Stable accessibility mechanism может включать:

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

System должна avoid implementing essential functionality способом, который prevents reasonable alternate access.

<a id="semantic-structure"></a>

### Семантическая структура

Conforming system должна provide semantic structure, когда system представляет meaningful content или controls.

Semantic structure может включать:

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

Semantic structure особенно важна, когда зрение недоступно, потому что assistive technologies часто rely on semantic information для передачи visual interfaces через non-visual output.

System может fail review, если essential controls или content cannot be understood, потому что их structure, labels или relationships недоступны через alternate access paths.

<a id="alternate-output"></a>

### Alternate Output

Conforming system должна provide reasonable alternate output, когда essential meaning otherwise depend on the unavailable sense.

Alternate output может включать:

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

Conforming system должна provide reasonable alternate input, когда essential operation otherwise depend on touch alone.

Alternate input может включать:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input не обязан быть fastest or most convenient input method. Он должен быть sufficient for essential operation.

<a id="accessible-feedback"></a>

### Accessible Feedback

Conforming system должна provide accessible feedback for essential actions.

Accessible feedback может включать:

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

Feedback не должен rely exclusively on unavailable sense в related accessibility case.

Например, sound-only success chime недостаточен, когда звук недоступен. Color-only error state недостаточен, когда зрение недоступно. Vibration-only confirmation недостаточна, когда осязание недоступно.

<a id="accessible-configuration"></a>

### Accessible Configuration

Conforming system должна позволять users достигать и использовать required accessibility settings через те же accessibility requirements, определенные этой specification.

Accessibility settings не должны быть hidden behind an inaccessible path.

Например, screen-reader-compatible mode недостаточен, если user сначала должен пройти через unlabeled visual-only menu, чтобы включить его.

System может fail review, если ее accessibility configuration нельзя reach or operate в condition, которое она intended to support.

<a id="verification"></a>

## Проверка

<a id="within-spec"></a>

### Within Spec

System считается within spec, когда CatalystUI Team reviewed the system и сочла reasonable to conclude, что она satisfies A11YSPEC.

System может быть within spec, когда:

* sight-unavailable use remains reasonably supported
* sound-unavailable use remains reasonably supported
* touch-unavailable use remains reasonably supported
* essential functionality remains accessible in each required case
* critical functionality remains accessible in each required case
* alternate access paths preserve essential meaning and operation
* accessibility settings, when present, can be reached and used accessibly
* the system does not trap essential functionality behind one required sense
* the system uses a stable accessibility mechanism appropriate to its design

System может быть within spec, даже если experiences are not identical across all sensory paths.

System может быть within spec, даже если some nonessential functionality is not equally available in every required accessibility case.

<a id="warnings"></a>

### Предупреждения

Warning может быть выдан, когда system appears to satisfy A11YSPEC, но содержит concerns, которые should be documented.

Warnings могут включать:

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

### Ошибки проверки

Failure occurs, когда system does not satisfy one or more required conditions of A11YSPEC.

Failures могут включать:

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

### Действительность проверки

A11YSPEC verification applies only to the reviewed state системы на момент выдачи verification.

System может retain verification across later updates, пока сохраняет verified accessibility foundation.

Minor wording changes, visual refinements, performance improvements, added accessibility features и ordinary content updates не invalidate verification automatically.

New review может потребоваться, если system:

* removes alternate access paths
* breaks assistive-technology support
* substantially changes essential navigation
* removes required accessibility settings
* changes interaction behavior in a way that affects verified accessibility
* introduces new essential workflows without accessible alternatives
* makes previously accessible critical functionality inaccessible
* replaces accessible behavior with single-sense-dependent behavior

Иными словами, improving accessibility usually fine.

Breaking the verified access model may require review.
