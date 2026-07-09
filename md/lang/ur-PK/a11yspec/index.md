<!-- یہ ترجمہ ChatGPT نے تیار کیا ہے اور کسی انسانی مترجم کو اس کا جائزہ لینا چاہیے۔ -->

<!-- ترجمہ تصدیق ہونے کے بعد pull request میں یہ سطریں ہٹا دیں۔ -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> یہاں پیش کی گئی definitions، requirements، اور concepts practical accessibility support کو بیان کرتے ہیں اور انہیں آزادانہ طور پر دوبارہ بیان کیا جا سکتا ہے۔

<a id="introduction"></a>

## تعارف

**Accessibility Specification (A11YSPEC)** CatalystUI ecosystem میں accessibility support evaluate کرنے کے لیے استعمال ہونے والے core concepts، terminology، اور requirements establish کرتی ہے۔ اس کا مقصد یہ determine کرنے کے لیے clear standard فراہم کرنا ہے کہ کوئی system، service، framework، application، library، یا implementation ایک primary sensory pathway unavailable ہونے پر بھی meaningfully usable رہتا ہے یا نہیں۔

Accessibility اس لیے important ہے کیونکہ user interface کو ایک sense پر entirely depend نہیں کرنا چاہیے جب وہی essential meaning reasonable طور پر another sense کے ذریعے communicate کیا جا سکتا ہو۔ System technically functional ہو سکتا ہے، لیکن اگر user sight، sound، یا touch کے بغیر individually اس کے essential behavior کو understand، navigate، configure، یا operate نہیں کر سکتا، تو system نے اس condition کے لیے reasonable access provide کرنے میں failure کیا ہے۔

یہ specification ہر possible disability، device، assistive technology، medical condition، legal requirement، regional accessibility standard، یا specialized use case کو verify کرنے کی کوشش نہیں کرتی۔ Instead، یہ وہ minimum accessibility foundation define کرتی ہے جو users کو system کے essential portions کو meaningfully access اور operate کرنے کے لیے required ہے جب تین primary accessibility senses میں سے ایک unavailable ہو۔

آسان الفاظ میں، A11YSPEC تین primary questions پوچھتی ہے:

1. کیا users sight پر rely کیے بغیر essential system کو understand کر سکتے ہیں؟
2. کیا users sound پر rely کیے بغیر essential system کو understand کر سکتے ہیں؟
3. کیا users touch پر rely کیے بغیر essential system کو operate کر سکتے ہیں؟

> [!IMPORTANT]
>
> A11YSPEC verification کے لیے accessibility requirements define کرتی ہے۔ یہ legal accessibility standards، platform certification requirements، یا specialized assistive-technology review کا replacement نہیں ہے۔ کوئی system A11YSPEC کے within ہو سکتا ہے اور پھر بھی other accessibility standards کے لیے additional review require کر سکتا ہے۔

<a id="table-of-contents"></a>

## فہرستِ مضامین

- [A11YSPEC](#a11yspec)
  - [تعارف](#introduction)
  - [فہرستِ مضامین](#table-of-contents)
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

کوئی system A11YSPEC کے ساتھ conformant سمجھا جاتا ہے جب وہ ہر required accessibility case کے لیے اس document میں defined requirements satisfy کرتا ہے۔

Conforming system کو لازماً:

1. Sight unavailable ہونے پر reasonably usable رہنا چاہیے۔
2. Sound unavailable ہونے پر reasonably usable رہنا چاہیے۔
3. Touch unavailable ہونے پر reasonably usable رہنا چاہیے۔
4. ہر required accessibility case میں essential functionality تک access preserve کرنی چاہیے۔
5. ہر required accessibility case میں all critical functionality تک access preserve کرنی چاہیے۔
6. جب essential meaning یا operation unavailable sense پر otherwise depend کرے تو reasonable alternate access paths provide کرنے چاہئیں۔
7. Reviewed system کے لیے appropriate stable accessibility mechanism استعمال کرنا چاہیے۔
8. Essential functionality کے لیے one primary sense پر exclusively rely کرنے سے avoid کرنا چاہیے۔

System کو ہر sensory path میں identical experiences provide کرنے کی ضرورت نہیں۔ Non-visual experience visual experience سے slower ہو سکتا ہے۔ Sound-free experience کو captions، visual indicators، یا haptic confirmation کی ضرورت ہو سکتی ہے۔ Touch-free experience کو keyboard navigation، pointer alternatives، voice interaction، switch-compatible interaction، یا another non-touch method کی ضرورت ہو سکتی ہے۔

Verification practical access to essential functionality سے concerned ہے، identical presentation سے نہیں۔

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

A11YSPEC کے لیے تین primary accessibility senses **sight**، **sound**، اور **touch** ہیں۔

یہ senses primary ہیں کیونکہ user-interface interaction میں شامل most common sensory pathways یہی ہیں۔ کوئی system sight، sound، یا touch کے ذریعے output provide کر سکتا ہے، اور touch، motion، voice، keyboard input، pointer input، switch input، یا another available input path کے ذریعے interaction receive کر سکتا ہے۔

<a id="sight"></a>

### Sight

Sight وہ visual sensory pathway ہے جس کے ذریعے user visual output perceive کرتا ہے۔

Sight مندرجہ ذیل perceive کرنے میں involved ہو سکتی ہے:

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

System sight پر depend کرتا ہے جب essential meaning یا operation user سے visually information perceive کرنے کا require کرے۔

<a id="sound"></a>

### Sound

Sound وہ auditory sensory pathway ہے جس کے ذریعے user audio output perceive کرتا ہے۔

Sound مندرجہ ذیل perceive کرنے میں involved ہو سکتی ہے:

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

System sound پر depend کرتا ہے جب essential meaning یا operation user سے information سننے کا require کرے۔

<a id="touch"></a>

### Touch

Touch وہ tactile sensory pathway ہے جس کے ذریعے user physical یا haptic output perceive کرتا ہے، اور وہ physical interaction pathway بھی ہے جس کے ذریعے user direct contact، pressure، gesture، یا movement سے controls operate کر سکتا ہے۔

Touch مندرجہ ذیل perceive یا perform کرنے میں involved ہو سکتی ہے:

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

System touch پر depend کرتا ہے جب essential meaning یا operation tactile perception یا touch-based interaction require کرے، بغیر کسی reasonable alternate input یا output path کے۔

<a id="additional-sensory-domains"></a>

### Additional Sensory Domains

CatalystUI **taste** اور **smell** کو بھی sensory domains کے طور پر recognize کرتا ہے۔

Taste اور smell کو accessibility review کے دوران consider کیا جا سکتا ہے جب system انہیں meaningfully use کرتا ہو۔ یہ senses verification کے لیے inclusive ہیں، یعنی یہ meaningful alternate access یا additional context provide کر کے accessibility review کو strengthen یا support کر سکتے ہیں۔

Taste اور smell currently failure کے لیے exclusive نہیں ہیں۔ System صرف اس لیے A11YSPEC fail نہیں کرتا کہ وہ taste-based یا smell-based interaction provide نہیں کرتا۔

A11YSPEC بنیادی طور پر اس بات سے concerned ہے کہ sight، sound، یا touch individually unavailable ہونے پر system reasonably usable رہتا ہے یا نہیں۔

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

Conforming system کو ہر required accessibility case کے خلاف review کیا جانا چاہیے۔

| Unavailable Sense | Required Accessibility Behavior |
| ----------------- | -------------------------------- |
| Sight             | System کو sound اور touch کے ذریعے reasonably usable رہنا چاہیے۔ |
| Sound             | System کو sight اور touch کے ذریعے reasonably usable رہنا چاہیے۔ |
| Touch             | System کو sight اور sound کے ذریعے reasonably usable رہنا چاہیے۔ |

ہر case individually review کیا جاتا ہے۔

System کو same time پر multiple primary senses unavailable ہونے پر fully usable رہنے کی ضرورت نہیں، جب تک وہ condition reviewed scope میں included نہ ہو۔

System کو every possible accommodation provide کرنے کی ضرورت نہیں۔ اسے ہر required accessibility case کے تحت essential functionality تک reasonable access provide کرنی چاہیے۔

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality کوئی بھی behavior، content، control، output، input، workflow، یا configuration ہے جس کی user کو system کے essential behavior کو understand، navigate، configure، یا operate کرنے کے لیے reasonable ضرورت ہو۔

Essential functionality میں شامل ہو سکتے ہیں:

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
* normal use کے لیے required کوئی بھی interaction

System کو ہر decorative، optional، redundant، یا nonessential feature کو ہر sensory path کے ذریعے equally available بنانے کی ضرورت نہیں۔ تاہم user unavailable sense کی وجہ سے essential system استعمال کرنے سے blocked نہیں ہونا چاہیے۔

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality وہ essential functionality ہے جس تک access کا loss meaningful use کو prevent کر سکتا ہے، serious error create کر سکتا ہے، یا user کو consequence understand کیے بغیر important decision لینے پر مجبور کر سکتا ہے۔

Critical functionality میں شامل ہو سکتے ہیں:

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
* accessibility settings تک پہنچنے کے لیے required core navigation

Critical functionality ہر required accessibility case میں accessible رہنی چاہیے۔

اگر critical functionality unavailable sense پر exclusively depend کرے تو system A11YSPEC fail کر سکتا ہے۔

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality وہ functionality ہے جو user کو system کے essential behavior کو understand، navigate، configure، یا operate کرنے کے لیے reasonably required نہیں ہوتی۔

Nonessential functionality میں شامل ہو سکتے ہیں:

* decorative animation
* optional effects
* cosmetic visual polish
* nonessential sound effects
* redundant haptic effects
* optional marketing content
* optional tutorial content
* hidden diagnostic behavior
* developer-facing controls
* reviewed scope سے باہر experimental features

Nonessential functionality ایک یا زیادہ accessibility cases میں inaccessible ہو سکتی ہے بغیر automatic failure کے۔ تاہم nonessential functionality کو essential functionality کے ساتھ confuse نہیں کرنا چاہیے صرف اس لیے کہ اسے support کرنا inconvenient ہے۔

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

System essential access requirement اس وقت satisfy کرتا ہے جب essential functionality ہر required accessibility case میں reasonably understandable، navigable، configurable، اور operable رہے۔

Essential experience کو all senses کے across identical ہونے کی ضرورت نہیں۔

Essential experience کو meaningfully usable رہنا چاہیے۔

<a id="critical-access-requirement"></a>

### Critical Access Requirement

System critical access requirement اس وقت satisfy کرتا ہے جب all critical functionality ہر required accessibility case میں accessible رہے۔

Critical functionality کو one required sensory pathway کے پیچھے hidden نہیں ہونا چاہیے۔

مثال کے طور پر، system کو ordinary use کے لیے accessible interface provide کرتے ہوئے account deletion warnings، payment confirmations، privacy decisions، یا accessibility settings کو sight، sound، یا touch alone پر dependent نہیں چھوڑنا چاہیے۔

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

System alternate access requirement اس وقت satisfy کرتا ہے جب one primary sense کے ذریعے provided essential meaning یا operation، اس sense unavailable ہونے پر another sensory یا interaction path کے ذریعے reasonably available ہو۔

Alternate access مندرجہ ذیل کے ذریعے provide ہو سکتا ہے:

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
* system کے لیے appropriate another stable mechanism

Alternate path کو original path کے ساتھ perfectly match کرنے کی ضرورت نہیں۔ اسے essential meaning اور operation preserve کرنا چاہیے۔

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

System کو essential functionality کے only path کے طور پر one primary sense require نہیں کرنا چاہیے۔

System sight، sound، یا touch کو primary experience کے طور پر use کر سکتا ہے۔ تاہم جب وہ sense unavailable ہو، user کے پاس remaining sensory paths کے ذریعے essential system کو understand اور operate کرنے کا reasonable way ہونا چاہیے۔

System review fail کر سکتا ہے جب essential information یا interaction صرف درج ذیل کے ذریعے available ہو:

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

جب sight unavailable ہو، system کو sound اور touch کے ذریعے reasonably usable رہنا چاہیے۔

اس کا مطلب ہے کہ essential visual information کے لیے meaningful non-visual access path ہونا چاہیے۔

System یہ requirement درج ذیل کے ذریعے satisfy کر سکتا ہے:

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

System کو exclusively درج ذیل پر rely نہیں کرنا چاہیے:

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

جب وہ information essential functionality کو understand یا operate کرنے کے لیے required ہو۔

اگر user sight کے بغیر essential system کو reasonably navigate، understand، یا operate نہیں کر سکتا تو system اس case میں fail کر سکتا ہے۔

<a id="sound-unavailable"></a>

## Sound Unavailable

جب sound unavailable ہو، system کو sight اور touch کے ذریعے reasonably usable رہنا چاہیے۔

اس کا مطلب ہے کہ essential auditory information کے لیے meaningful non-auditory access path ہونا چاہیے۔

System یہ requirement درج ذیل کے ذریعے satisfy کر سکتا ہے:

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

System کو exclusively درج ذیل پر rely نہیں کرنا چاہیے:

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

جب وہ information essential functionality کو understand یا operate کرنے کے لیے required ہو۔

اگر user sound کے بغیر essential system کو reasonably navigate، understand، یا operate نہیں کر سکتا تو system اس case میں fail کر سکتا ہے۔

<a id="touch-unavailable"></a>

## Touch Unavailable

جب touch unavailable ہو، system کو sight اور sound کے ذریعے reasonably usable رہنا چاہیے۔

اس کا مطلب ہے کہ essential tactile information اور touch-based operation کے لیے meaningful non-touch access path ہونا چاہیے۔

System یہ requirement درج ذیل کے ذریعے satisfy کر سکتا ہے:

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

System کو exclusively درج ذیل پر rely نہیں کرنا چاہیے:

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

جب وہ interaction essential functionality کو understand یا operate کرنے کے لیے required ہو۔

اگر user touch کے بغیر essential system کو reasonably navigate، understand، یا operate نہیں کر سکتا تو system اس case میں fail کر سکتا ہے۔

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

Conforming system کو reviewed system کے لیے appropriate stable accessibility mechanism استعمال کرنا چاہیے۔

Stable accessibility mechanism کو accessibility behavior کو maintain، update، review، اور extend کرنے کی اجازت دینی چاہیے بغیر fragile یا undocumented behavior پر rely کیے۔

Stable accessibility mechanism میں شامل ہو سکتے ہیں:

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
* system کے لیے appropriate another stable structure

System کو essential functionality اس طرح implement کرنے سے avoid کرنا چاہیے جو reasonable alternate access کو prevent کرے۔

<a id="semantic-structure"></a>

### Semantic Structure

Conforming system کو meaningful content یا controls present کرتے وقت semantic structure provide کرنی چاہیے۔

Semantic structure میں شامل ہو سکتے ہیں:

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

Semantic structure خاص طور پر sight unavailable ہونے پر important ہے، کیونکہ assistive technologies اکثر visual interfaces کو non-visual output کے ذریعے communicate کرنے کے لیے semantic information پر rely کرتی ہیں۔

اگر essential controls یا content alternate access paths کے ذریعے unavailable structure، labels، یا relationships کی وجہ سے understood نہیں ہو سکتے تو system review fail کر سکتا ہے۔

<a id="alternate-output"></a>

### Alternate Output

Conforming system کو reasonable alternate output provide کرنا چاہیے جب essential meaning otherwise unavailable sense پر depend کرے۔

Alternate output میں شامل ہو سکتے ہیں:

* auditory information کے لیے visual output
* visual information کے لیے auditory output
* visual یا auditory information کے لیے tactile output
* text equivalents
* captions
* transcripts
* spoken descriptions
* visible status messages
* haptic confirmation
* another appropriate output path

Alternate output کو essential meaning preserve کرنا چاہیے۔

<a id="alternate-input"></a>

### Alternate Input

Conforming system کو reasonable alternate input provide کرنا چاہیے جب essential operation otherwise touch alone پر depend کرے۔

Alternate input میں شامل ہو سکتے ہیں:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input کو fastest یا most convenient input method ہونے کی ضرورت نہیں۔ اسے essential operation کے لیے sufficient ہونا چاہیے۔

<a id="accessible-feedback"></a>

### Accessible Feedback

Conforming system کو essential actions کے لیے accessible feedback provide کرنا چاہیے۔

Accessible feedback میں شامل ہو سکتے ہیں:

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

Related accessibility case میں feedback کو unavailable sense پر exclusively rely نہیں کرنا چاہیے۔

مثال کے طور پر، sound unavailable ہونے پر sound-only success chime sufficient نہیں۔ Sight unavailable ہونے پر color-only error state sufficient نہیں۔ Touch unavailable ہونے پر vibration-only confirmation sufficient نہیں۔

<a id="accessible-configuration"></a>

### Accessible Configuration

Conforming system کو users کو required accessibility settings تک پہنچنے اور انہیں use کرنے کی اجازت اسی accessibility requirements کے ذریعے دینی چاہیے جو اس specification میں defined ہیں۔

Accessibility settings کو inaccessible path کے پیچھے hidden نہیں ہونا چاہیے۔

مثال کے طور پر، screen-reader-compatible mode sufficient نہیں اگر user کو پہلے اسے enable کرنے کے لیے unlabeled visual-only menu navigate کرنا پڑے۔

اگر system کی accessibility configuration اس condition میں reached یا operated نہیں ہو سکتی جسے support کرنا مقصود ہے، تو system review fail کر سکتا ہے۔

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

System within spec اس وقت سمجھا جاتا ہے جب CatalystUI Team نے system review کیا ہو اور reasonable طور پر conclude کیا ہو کہ یہ A11YSPEC satisfy کرتا ہے۔

System within spec ہو سکتا ہے جب:

* sight-unavailable use reasonably supported رہے
* sound-unavailable use reasonably supported رہے
* touch-unavailable use reasonably supported رہے
* essential functionality ہر required case میں accessible رہے
* critical functionality ہر required case میں accessible رہے
* alternate access paths essential meaning اور operation preserve کریں
* accessibility settings، جب present ہوں، accessibly reached اور used ہو سکیں
* system essential functionality کو one required sense کے پیچھے trap نہ کرے
* system اپنی design کے لیے appropriate stable accessibility mechanism استعمال کرے

System within spec ہو سکتا ہے چاہے experiences all sensory paths میں identical نہ ہوں۔

System within spec ہو سکتا ہے چاہے کچھ nonessential functionality ہر required accessibility case میں equally available نہ ہو۔

<a id="warnings"></a>

### Warnings

Warning اس وقت issue ہو سکتی ہے جب system A11YSPEC satisfy کرتا دکھائی دے مگر ایسی concerns ہوں جنہیں documented ہونا چاہیے۔

Warnings میں شامل ہو سکتے ہیں:

* one accessibility case میں minor nonessential content unavailable
* slower but usable alternate access paths
* imperfect but understandable captions or transcripts
* limited but functional keyboard navigation
* limited but functional screen-reader support
* minor focus-order concerns جو essential use کو block نہیں کرتے
* redundant visual، auditory، یا tactile cues کا one path سے missing ہونا
* accessibility settings جو usable ہیں مگر find کرنا difficult ہے
* assistive-technology support جو work کرتا ہے مگر clearer ہو سکتا ہے
* optional workflows جو equally accessible نہیں ہیں

Warnings necessarily verification کو prevent نہیں کرتے۔

<a id="failures"></a>

### Failures

Failure اس وقت occurs ہوتا ہے جب system A11YSPEC کی one or more required conditions satisfy نہیں کرتا۔

Failures میں شامل ہو سکتے ہیں:

* sight unavailable ہونے پر essential functionality unavailable
* sound unavailable ہونے پر essential functionality unavailable
* touch unavailable ہونے پر essential functionality unavailable
* کسی required accessibility case میں critical functionality unavailable
* essential visual information کے لیے no reasonable alternate access path
* essential auditory information کے لیے no reasonable alternate access path
* essential touch-based operation کے لیے no reasonable alternate access path
* accessibility settings اس condition کے تحت unreachable جسے وہ support کرنے کے لیے meant ہیں
* non-visual use کے لیے required controls without meaningful labels or structure
* visual، tactile، یا text equivalent کے بغیر sound-only warnings
* non-visual equivalent کے بغیر color-only status
* keyboard، pointer، voice، switch، یا other alternative کے بغیر gesture-only operation
* visual یا auditory equivalent کے بغیر haptic-only confirmation
* essential workflows کے لیے broken assistive-technology support
* major navigation traps
* essential workflows جو unavailable sense کے بغیر complete نہیں ہو سکتے

Failures resolved ہونے تک verification prevent کرتے ہیں۔

<a id="verification-validity"></a>

### Verification Validity

A11YSPEC verification صرف system کی reviewed state پر apply کرتی ہے at the time verification is issued۔

System later updates میں verification retain کر سکتا ہے جب تک وہ verified accessibility foundation preserve کرے۔

Minor wording changes، visual refinements، performance improvements، added accessibility features، اور ordinary content updates automatically verification invalidate نہیں کرتے۔

New review required ہو سکتی ہے اگر system:

* alternate access paths remove کرے
* assistive-technology support break کرے
* essential navigation substantially change کرے
* required accessibility settings remove کرے
* interaction behavior اس طرح change کرے جو verified accessibility کو affect کرے
* accessible alternatives کے بغیر new essential workflows introduce کرے
* previously accessible critical functionality کو inaccessible بنائے
* accessible behavior کو single-sense-dependent behavior سے replace کرے

دوسرے الفاظ میں، accessibility improve کرنا usually fine ہے۔

Verified access model کو break کرنا review require کر سکتا ہے۔
