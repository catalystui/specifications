<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->

<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request içinde kaldırın. -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Burada sunulan definitions, requirements ve concepts practical accessibility support’u açıklar ve serbestçe yeniden ifade edilebilir.

<a id="introduction"></a>

## Giriş

**Accessibility Specification (A11YSPEC)**, CatalystUI ecosystem içinde accessibility support’u değerlendirmek için kullanılan core concepts, terminology ve requirements’ı oluşturur. Amacı, bir system, service, framework, application, library veya implementation’ın bir primary sensory pathway unavailable olduğunda meaningfully usable kalıp kalmadığını belirlemek için açık bir standard sağlamaktır.

Accessibility önemlidir, çünkü bir user interface aynı essential meaning makul şekilde başka bir yolla iletilebiliyorsa tek bir duyuya tamamen bağlı olmamalıdır. Bir system technically functional olabilir; ancak user, essential behavior’ını görme, ses veya dokunma olmadan tek tek anlayamıyor, navigate edemiyor, configure edemiyor veya operate edemiyorsa system o condition için reasonable access sağlamada başarısız olmuştur.

Bu specification her olası disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard veya specialized use case’i verify etmeye çalışmaz. Bunun yerine, üç primary accessibility senses öğesinden biri unavailable olduğunda users’ın system’ın essential portions bölümüne meaningfully access etmesi ve operate etmesi için required olan minimum accessibility foundation’ı tanımlar.

Daha basit ifadeyle, A11YSPEC üç primary question sorar:

1. Users essential system’ı görmeye güvenmeden anlayabilir mi?
2. Users essential system’ı sese güvenmeden anlayabilir mi?
3. Users essential system’ı dokunmaya güvenmeden operate edebilir mi?

> [!IMPORTANT]
>
> A11YSPEC verification için accessibility requirements tanımlar. Legal accessibility standards, platform certification requirements veya specialized assistive-technology review yerine geçmez. Bir system within A11YSPEC olabilir ve yine de diğer accessibility standards için additional review gerektirebilir.

<a id="table-of-contents"></a>

## İçindekiler

- [A11YSPEC](#a11yspec)
  - [Giriş](#introduction)
  - [İçindekiler](#table-of-contents)
  - [Conformance](#conformance)
  - [Primary Accessibility Senses](#primary-accessibility-senses)
    - [Görme](#sight)
    - [Ses](#sound)
    - [Dokunma](#touch)
    - [Ek Sensory Domains](#additional-sensory-domains)
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
  - [Görme Kullanılamadığında](#sight-unavailable)
  - [Ses Kullanılamadığında](#sound-unavailable)
  - [Dokunma Kullanılamadığında](#touch-unavailable)
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

Bir system, her required accessibility case için bu document tarafından tanımlanan requirements’ı karşıladığında A11YSPEC ile conformant kabul edilir.

Conforming system şunları yapmalıdır:

1. Görme unavailable olduğunda makul ölçüde usable kalmalıdır.
2. Ses unavailable olduğunda makul ölçüde usable kalmalıdır.
3. Dokunma unavailable olduğunda makul ölçüde usable kalmalıdır.
4. Her required accessibility case içinde essential functionality’ye access’i korumalıdır.
5. Her required accessibility case içinde tüm critical functionality’ye access’i korumalıdır.
6. Essential meaning veya operation unavailable sense’e bağlı olacaksa reasonable alternate access paths sağlamalıdır.
7. Reviewed system’a uygun stable accessibility mechanism kullanmalıdır.
8. Essential functionality için yalnızca bir primary sense’e güvenmekten kaçınmalıdır.

Bir system’ın her sensory path üzerinde identical experiences sağlaması gerekmez. Non-visual experience visual olandan daha yavaş olabilir. Sound-free experience captions, visual indicators veya haptic confirmation gerektirebilir. Touch-free experience keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction veya başka bir non-touch method gerektirebilir.

Verification identical presentation’dan çok essential functionality’ye practical access ile ilgilenir.

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

A11YSPEC için üç primary accessibility senses **görme**, **ses** ve **dokunma**dır.

Bu duyular primary kabul edilir, çünkü user-interface interaction içinde yer alan en yaygın sensory pathways bunlardır. Bir system output’u görme, ses veya dokunma yoluyla sağlayabilir; interaction’ı touch, motion, voice, keyboard input, pointer input, switch input veya başka bir available input path üzerinden alabilir.

<a id="sight"></a>

### Görme

Görme, user’ın visual output’u algıladığı visual sensory pathway’dir.

Görme şunları algılamada yer alabilir:

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

Essential meaning veya operation, user’ın bilgiyi visual olarak algılamasını gerektiriyorsa system görmeye bağlıdır.

<a id="sound"></a>

### Ses

Ses, user’ın audio output’u algıladığı auditory sensory pathway’dir.

Ses şunları algılamada yer alabilir:

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

Essential meaning veya operation, user’ın bilgiyi duymasını gerektiriyorsa system sese bağlıdır.

<a id="touch"></a>

### Dokunma

Dokunma, user’ın physical veya haptic output’u algıladığı tactile sensory pathway ve user’ın direct contact, pressure, gesture veya movement yoluyla controls’u operate edebildiği physical interaction pathway’dir.

Dokunma şunları algılamada veya gerçekleştirmede yer alabilir:

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

Essential meaning veya operation, reasonable alternate input veya output path olmadan tactile perception ya da touch-based interaction gerektiriyorsa system dokunmaya bağlıdır.

<a id="additional-sensory-domains"></a>

### Ek Sensory Domains

CatalystUI ayrıca **tat** ve **koku**yu sensory domains olarak tanır.

System tarafından meaningful olarak kullanıldıklarında tat ve koku accessibility review sırasında değerlendirilebilir. Bu duyular verification için inclusive kabul edilir; yani meaningful alternate access veya additional context sağladıklarında accessibility review’u güçlendirebilir veya destekleyebilirler.

Tat ve koku şu anda failure için exclusive değildir. Bir system taste-based veya smell-based interaction sağlamadığı için A11YSPEC’ten kalmaz.

A11YSPEC öncelikle system’ın görme, ses veya dokunma individually unavailable olduğunda reasonably usable kalıp kalmadığıyla ilgilenir.

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

Conforming system her required accessibility case’e göre reviewed olmalıdır.

| Kullanılamayan Duyu | Gerekli Accessibility Behavior |
| ------------------- | ------------------------------ |
| Görme               | System ses ve dokunma yoluyla makul ölçüde kullanılabilir kalmalıdır. |
| Ses                 | System görme ve dokunma yoluyla makul ölçüde kullanılabilir kalmalıdır. |
| Dokunma             | System görme ve ses yoluyla makul ölçüde kullanılabilir kalmalıdır. |

Her case ayrı ayrı reviewed edilir.

Reviewed scope içinde bulunmadıkça, bir system’ın birden fazla primary sense aynı anda unavailable olduğunda fully usable kalması required değildir.

Bir system’ın her possible accommodation’ı sağlaması required değildir. Her required accessibility case altında essential functionality için reasonable access sağlamalıdır.

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality, user’ın bir system’ın essential behavior’ını anlamak, navigate etmek, configure etmek veya operate etmek için makul olarak ihtiyaç duyduğu herhangi bir behavior, content, control, output, input, workflow veya configuration’dır.

Essential functionality şunları içerebilir:

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
* normal kullanım için required olan herhangi bir interaction

Bir system’ın her decorative, optional, redundant veya nonessential feature’ı her sensory path üzerinden eşit biçimde available yapması gerekmez. Ancak user, unavailable sense nedeniyle essential system’ı kullanmaktan blocked olmamalıdır.

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality, access kaybının meaningful use’u engelleyebileceği, serious error oluşturabileceği veya user’ın consequence’ı anlamadan önemli bir decision almasına neden olabileceği essential functionality’dir.

Critical functionality şunları içerebilir:

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

Critical functionality her required accessibility case içinde accessible kalmalıdır.

Critical functionality unavailable sense’e exclusively bağlıysa system A11YSPEC’ten kalabilir.

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality, user’ın bir system’ın essential behavior’ını anlamak, navigate etmek, configure etmek veya operate etmek için makul olarak ihtiyaç duymadığı functionality’dir.

Nonessential functionality şunları içerebilir:

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

Nonessential functionality bir veya daha fazla accessibility case altında inaccessible olabilir ve bu durum otomatik olarak failure oluşturmaz. Ancak nonessential functionality, support etmek inconvenient olduğu için essential functionality ile karıştırılmamalıdır.

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

Essential functionality her required accessibility case içinde reasonably understandable, navigable, configurable ve operable kaldığında system essential access requirement’ı karşılar.

Essential experience’ın tüm senses genelinde identical olması gerekmez.

Essential experience meaningfully usable kalmalıdır.

<a id="critical-access-requirement"></a>

### Critical Access Requirement

Tüm critical functionality her required accessibility case içinde accessible kaldığında system critical access requirement’ı karşılar.

Critical functionality tek bir required sensory pathway arkasına gizlenmemelidir.

Örneğin bir system ordinary use için accessible interface sağlarken account deletion warnings, payment confirmations, privacy decisions veya accessibility settings’i yalnızca görme, ses veya dokunmaya bağlı bırakmamalıdır.

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

Bir primary sense üzerinden sağlanan essential meaning veya operation, o sense unavailable olduğunda başka bir sensory veya interaction path üzerinden de makul şekilde available ise system alternate access requirement’ı karşılar.

Alternate access şu yollarla sağlanabilir:

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

Alternate path’in original path ile perfectly eşleşmesi gerekmez. Essential meaning ve operation’ı korumalıdır.

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

Bir system essential functionality’ye giden tek path olarak bir primary sense’i required kılmamalıdır.

Bir system görme, ses veya dokunmayı primary experience olarak kullanabilir. Ancak o sense unavailable olduğunda user, remaining sensory paths üzerinden essential system’ı anlamak ve operate etmek için reasonable way’e sahip olmalıdır.

Essential information veya interaction yalnızca şu yollarla available ise system review’dan kalabilir:

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

## Görme Kullanılamadığında

Görme unavailable olduğunda system ses ve dokunma yoluyla makul ölçüde usable kalmalıdır.

Bu, essential visual information’ın meaningful non-visual access path’e sahip olması gerektiği anlamına gelir.

Bir system bu requirement’ı şu yollarla karşılayabilir:

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

Bir system yalnızca şunlara güvenmemelidir:

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

essential functionality’yi anlamak veya operate etmek için bu information required olduğunda.

User essential system’ı görme olmadan makul şekilde navigate edemiyor, anlayamıyor veya operate edemiyorsa system bu case’ten kalabilir.

<a id="sound-unavailable"></a>

## Ses Kullanılamadığında

Ses unavailable olduğunda system görme ve dokunma yoluyla makul ölçüde usable kalmalıdır.

Bu, essential auditory information’ın meaningful non-auditory access path’e sahip olması gerektiği anlamına gelir.

Bir system bu requirement’ı şu yollarla karşılayabilir:

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

Bir system yalnızca şunlara güvenmemelidir:

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

essential functionality’yi anlamak veya operate etmek için bu information required olduğunda.

User essential system’ı ses olmadan makul şekilde navigate edemiyor, anlayamıyor veya operate edemiyorsa system bu case’ten kalabilir.

<a id="touch-unavailable"></a>

## Dokunma Kullanılamadığında

Dokunma unavailable olduğunda system görme ve ses yoluyla makul ölçüde usable kalmalıdır.

Bu, essential tactile information ve touch-based operation’ın meaningful non-touch access path’e sahip olması gerektiği anlamına gelir.

Bir system bu requirement’ı şu yollarla karşılayabilir:

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

Bir system yalnızca şunlara güvenmemelidir:

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

essential functionality’yi anlamak veya operate etmek için bu interaction required olduğunda.

User essential system’ı dokunma olmadan makul şekilde navigate edemiyor, anlayamıyor veya operate edemiyorsa system bu case’ten kalabilir.

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

Conforming system, reviewed edilen system’a uygun stable accessibility mechanism kullanmalıdır.

Stable accessibility mechanism, accessibility behavior’ın fragile veya undocumented behavior’a bağlı olmadan maintained, updated, reviewed ve extended edilebilmesine izin vermelidir.

Stable accessibility mechanism şunları içerebilir:

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

Bir system essential functionality’yi reasonable alternate access’i engelleyecek şekilde implement etmekten kaçınmalıdır.

<a id="semantic-structure"></a>

### Semantic Structure

Conforming system, meaningful content veya controls sunduğunda semantic structure sağlamalıdır.

Semantic structure şunları içerebilir:

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

Semantic structure özellikle görme unavailable olduğunda önemlidir, çünkü assistive technologies visual interfaces’i non-visual output yoluyla iletmek için semantic information’a sıklıkla güvenir.

Essential controls veya content, structure, labels veya relationships alternate access paths üzerinden unavailable olduğu için anlaşılamıyorsa system review’dan kalabilir.

<a id="alternate-output"></a>

### Alternate Output

Conforming system, essential meaning unavailable sense’e bağlı olacaksa reasonable alternate output sağlamalıdır.

Alternate output şunları içerebilir:

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

Alternate output essential meaning’i korumalıdır.

<a id="alternate-input"></a>

### Alternate Input

Conforming system, essential operation yalnızca touch’a bağlı olacaksa reasonable alternate input sağlamalıdır.

Alternate input şunları içerebilir:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input’in en hızlı veya en convenient input method olması gerekmez. Essential operation için yeterli olmalıdır.

<a id="accessible-feedback"></a>

### Accessible Feedback

Conforming system, essential actions için accessible feedback sağlamalıdır.

Accessible feedback şunları içerebilir:

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

Feedback ilgili accessibility case içinde unavailable sense’e exclusively bağlı olmamalıdır.

Örneğin, sound unavailable olduğunda sound-only success chime yeterli değildir. Sight unavailable olduğunda color-only error state yeterli değildir. Touch unavailable olduğunda vibration-only confirmation yeterli değildir.

<a id="accessible-configuration"></a>

### Accessible Configuration

Conforming system, users’ın required accessibility settings’e bu specification tarafından tanımlanan aynı accessibility requirements üzerinden ulaşmasına ve kullanmasına izin vermelidir.

Accessibility settings inaccessible path arkasına gizlenmemelidir.

Örneğin, user’ın screen-reader-compatible mode’u enable etmek için önce unlabeled visual-only menu içinde navigate etmesi gerekiyorsa bu mode yeterli değildir.

Accessibility configuration, desteklemeyi amaçladığı condition içinde ulaşılamıyor veya operate edilemiyorsa system review’dan kalabilir.

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

CatalystUI Team system’ı review edip A11YSPEC’i karşıladığını düşünmenin reasonable olduğu sonucuna vardığında system within spec kabul edilir.

Bir system şu durumlarda within spec olabilir:

* sight-unavailable use remains reasonably supported
* sound-unavailable use remains reasonably supported
* touch-unavailable use remains reasonably supported
* essential functionality remains accessible in each required case
* critical functionality remains accessible in each required case
* alternate access paths preserve essential meaning and operation
* accessibility settings, when present, can be reached and used accessibly
* the system does not trap essential functionality behind one required sense
* the system uses a stable accessibility mechanism appropriate to its design

Bir system, experiences tüm sensory paths genelinde identical olmasa bile within spec olabilir.

Bazı nonessential functionality her required accessibility case içinde eşit available olmasa bile system within spec olabilir.

<a id="warnings"></a>

### Warnings

Bir system A11YSPEC’i karşılıyor gibi görünse de documented olması gereken concerns içeriyorsa warning verilebilir.

Warnings şunları içerebilir:

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

Warnings verification’ı mutlaka engellemez.

<a id="failures"></a>

### Failures

Bir system A11YSPEC’in bir veya daha fazla required condition’ını karşılamadığında failure oluşur.

Failures şunları içerebilir:

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

Failures resolved edilene kadar verification’ı engeller.

<a id="verification-validity"></a>

### Verification Validity

A11YSPEC verification yalnızca verification verildiği anda system’ın reviewed state’i için geçerlidir.

System verified accessibility foundation’ı koruduğu sürece later updates boyunca verification’ı koruyabilir.

Minor wording changes, visual refinements, performance improvements, added accessibility features ve ordinary content updates verification’ı otomatik olarak invalidate etmez.

Yeni review şu durumlarda gerekebilir:

* removes alternate access paths
* breaks assistive-technology support
* substantially changes essential navigation
* removes required accessibility settings
* changes interaction behavior in a way that affects verified accessibility
* introduces new essential workflows without accessible alternatives
* makes previously accessible critical functionality inaccessible
* replaces accessible behavior with single-sense-dependent behavior

Başka bir deyişle, accessibility’yi geliştirmek genellikle uygundur.

Verified access model’ı bozmak review gerektirebilir.
