<!-- यह अनुवाद ChatGPT द्वारा तैयार किया गया है और किसी मानव अनुवादक द्वारा इसकी समीक्षा की जानी चाहिए। -->

<!-- अनुवाद सत्यापित हो जाने के बाद pull request में इन पंक्तियों को हटा दें। -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> यहाँ प्रस्तुत definitions, requirements, और concepts practical accessibility support का वर्णन करते हैं और इन्हें स्वतंत्र रूप से पुनः अभिव्यक्त किया जा सकता है।

<a id="introduction"></a>

## Introduction

**Accessibility Specification (A11YSPEC)** CatalystUI ecosystem के भीतर accessibility support को evaluate करने के लिए उपयोग किए जाने वाले core concepts, terminology, और requirements स्थापित करता है। इसका उद्देश्य यह निर्धारित करने के लिए clear standard देना है कि कोई system, service, framework, application, library, या implementation तब भी meaningfully usable रहता है या नहीं जब एक primary sensory pathway unavailable हो।

Accessibility इसलिए महत्त्वपूर्ण है क्योंकि user interface को पूरी तरह किसी एक sense पर निर्भर नहीं होना चाहिए, जब वही essential meaning किसी दूसरे sense के माध्यम से reasonably communicate किया जा सकता हो। कोई system technically functional हो सकता है, लेकिन यदि user sight, sound, या touch में से किसी एक के बिना उसके essential behavior को understand, navigate, configure, या operate नहीं कर सकता, तो उस condition के लिए system reasonable access देने में fail हुआ है।

यह specification हर possible disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard, या specialized use case को verify करने का प्रयास नहीं करती। इसके बजाय, यह वह minimum accessibility foundation define करती है जो users को system के essential portions तक meaningfully access और operation देने के लिए required है, जब तीन primary accessibility senses में से कोई एक unavailable हो।

सरल शब्दों में, A11YSPEC तीन primary questions पूछता है:

1. क्या users sight पर निर्भर हुए बिना essential system को समझ सकते हैं?
2. क्या users sound पर निर्भर हुए बिना essential system को समझ सकते हैं?
3. क्या users touch पर निर्भर हुए बिना essential system को operate कर सकते हैं?

> [!IMPORTANT]
>
> A11YSPEC verification के लिए accessibility requirements define करता है। यह legal accessibility standards, platform certification requirements, या specialized assistive-technology review का replacement नहीं है। कोई system A11YSPEC के भीतर हो सकता है और फिर भी अन्य accessibility standards के लिए additional review require कर सकता है।

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

कोई system A11YSPEC के conformant माना जाता है जब वह प्रत्येक required accessibility case के लिए इस document में defined requirements को satisfy करता है।

Conforming system को:

1. sight unavailable होने पर reasonably usable रहना चाहिए।
2. sound unavailable होने पर reasonably usable रहना चाहिए।
3. touch unavailable होने पर reasonably usable रहना चाहिए।
4. प्रत्येक required accessibility case में essential functionality तक access preserve करना चाहिए।
5. प्रत्येक required accessibility case में all critical functionality तक access preserve करना चाहिए।
6. जब essential meaning या operation otherwise unavailable sense पर depend करे, तब reasonable alternate access paths प्रदान करने चाहिए।
7. Reviewed system के लिए appropriate stable accessibility mechanism उपयोग करना चाहिए।
8. Essential functionality के लिए किसी एक primary sense पर exclusively depend करने से बचना चाहिए।

किसी system को हर sensory path में identical experiences देने की आवश्यकता नहीं है। Non-visual experience visual experience से धीमा हो सकता है। Sound-free experience में captions, visual indicators, या haptic confirmation की आवश्यकता हो सकती है। Touch-free experience में keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction, या कोई other non-touch method required हो सकता है।

Verification identical presentation नहीं, बल्कि essential functionality तक practical access से concerned है।

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

A11YSPEC के लिए, तीन primary accessibility senses **sight**, **sound**, और **touch** हैं।

ये senses primary हैं क्योंकि user-interface interaction में ये सबसे common sensory pathways हैं। कोई system sight, sound, या touch के माध्यम से output provide कर सकता है, और touch, motion, voice, keyboard input, pointer input, switch input, या किसी अन्य available input path के माध्यम से interaction receive कर सकता है।

<a id="sight"></a>

### Sight

Sight वह visual sensory pathway है जिसके द्वारा user visual output perceive करता है।

Sight निम्न चीज़ों को perceive करने में शामिल हो सकता है:

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

कोई system sight पर depend करता है जब essential meaning या operation user से information को visually perceive करने की requirement रखता है।

<a id="sound"></a>

### Sound

Sound वह auditory sensory pathway है जिसके द्वारा user audio output perceive करता है।

Sound निम्न चीज़ों को perceive करने में शामिल हो सकता है:

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

कोई system sound पर depend करता है जब essential meaning या operation user से information सुनने की requirement रखता है।

<a id="touch"></a>

### Touch

Touch वह tactile sensory pathway है जिसके द्वारा user physical या haptic output perceive करता है, और वह physical interaction pathway भी है जिसके द्वारा user direct contact, pressure, gesture, या movement से controls operate कर सकता है।

Touch निम्न चीज़ों को perceive या perform करने में शामिल हो सकता है:

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

कोई system touch पर depend करता है जब essential meaning या operation reasonable alternate input या output path के बिना tactile perception या touch-based interaction require करता है।

<a id="additional-sensory-domains"></a>

### Additional Sensory Domains

CatalystUI **taste** और **smell** को भी sensory domains के रूप में recognize करता है।

जब system इन्हें meaningfully use करता है, तब accessibility review के दौरान taste और smell consider किए जा सकते हैं। ये senses verification के लिए inclusive हैं, अर्थात meaningful alternate access या additional context देते समय ये accessibility review को strengthen या support कर सकते हैं।

Taste और smell फिलहाल failure के लिए exclusive नहीं हैं। कोई system A11YSPEC में केवल इसलिए fail नहीं होता क्योंकि वह taste-based या smell-based interaction provide नहीं करता।

A11YSPEC मुख्य रूप से इस बात से concerned है कि sight, sound, या touch में से कोई एक अलग से unavailable होने पर system reasonably usable रहता है या नहीं।

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

Conforming system को प्रत्येक required accessibility case के विरुद्ध review किया जाना चाहिए।

| Unavailable Sense | Required Accessibility Behavior                                   |
| ----------------- | ----------------------------------------------------------------- |
| Sight             | System को sound और touch के माध्यम से reasonably usable रहना चाहिए। |
| Sound             | System को sight और touch के माध्यम से reasonably usable रहना चाहिए। |
| Touch             | System को sight और sound के माध्यम से reasonably usable रहना चाहिए। |

प्रत्येक case को individually review किया जाता है।

जब तक वह condition reviewed scope में included न हो, system को multiple primary senses एक ही समय में unavailable होने पर fully usable रहना required नहीं है।

System को हर possible accommodation provide करने की आवश्यकता नहीं है। उसे प्रत्येक required accessibility case में essential functionality तक reasonable access provide करना चाहिए।

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality कोई भी behavior, content, control, output, input, workflow, या configuration है जिसकी user को system के essential behavior को understand, navigate, configure, या operate करने के लिए reasonably आवश्यकता होती है।

Essential functionality में शामिल हो सकते हैं:

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
* normal use के लिए required कोई भी interaction

System को हर decorative, optional, redundant, या nonessential feature हर sensory path से equally available कराने की आवश्यकता नहीं है। फिर भी user unavailable sense के कारण essential system का उपयोग करने से blocked नहीं होना चाहिए।

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality ऐसी essential functionality है जिसमें access खोने से meaningful use रुक सकता है, serious error पैदा हो सकता है, या user consequence को समझे बिना important decision ले सकता है।

Critical functionality में शामिल हो सकते हैं:

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
* accessibility settings तक पहुँचने के लिए required core navigation

Critical functionality प्रत्येक required accessibility case में accessible रहनी चाहिए।

यदि critical functionality unavailable sense पर exclusively depend करती है, तो system A11YSPEC में fail हो सकता है।

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality वह functionality है जो user को system के essential behavior को understand, navigate, configure, या operate करने के लिए reasonably required नहीं है।

Nonessential functionality में शामिल हो सकते हैं:

* decorative animation
* optional effects
* cosmetic visual polish
* nonessential sound effects
* redundant haptic effects
* optional marketing content
* optional tutorial content
* hidden diagnostic behavior
* developer-facing controls
* reviewed scope के बाहर experimental features

Nonessential functionality एक या अधिक accessibility cases में inaccessible हो सकती है और इससे automatically failure नहीं होता। फिर भी केवल support करना inconvenient है इसलिए nonessential functionality को essential functionality से confused नहीं करना चाहिए।

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

System essential access requirement तब satisfy करता है जब essential functionality प्रत्येक required accessibility case में reasonably understandable, navigable, configurable, और operable रहती है।

Essential experience सभी senses में identical होना आवश्यक नहीं है।

Essential experience meaningfully usable रहना चाहिए।

<a id="critical-access-requirement"></a>

### Critical Access Requirement

System critical access requirement तब satisfy करता है जब all critical functionality प्रत्येक required accessibility case में accessible रहती है।

Critical functionality किसी एक required sensory pathway के पीछे hidden नहीं होनी चाहिए।

उदाहरण के लिए, system ordinary use के लिए accessible interface provide करते हुए account deletion warnings, payment confirmations, privacy decisions, या accessibility settings को केवल sight, sound, या touch पर dependent नहीं छोड़ना चाहिए।

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

System alternate access requirement तब satisfy करता है जब किसी एक primary sense के माध्यम से दिया गया essential meaning या operation उस sense के unavailable होने पर किसी दूसरे sensory या interaction path से reasonably available रहता है।

Alternate access निम्न माध्यमों से provide किया जा सकता है:

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
* system के लिए appropriate कोई अन्य stable mechanism

Alternate path को original path से perfectly match करने की आवश्यकता नहीं है। उसे essential meaning और operation preserve करना चाहिए।

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

System को essential functionality के लिए किसी एक primary sense को only path के रूप में require नहीं करना चाहिए।

System sight, sound, या touch को primary experience के रूप में use कर सकता है। परंतु जब वह sense unavailable हो, तो user के पास remaining sensory paths के माध्यम से essential system को understand और operate करने का reasonable way होना चाहिए।

System review में fail हो सकता है जब essential information या interaction केवल इनसे available हो:

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

जब sight unavailable हो, तो system को sound और touch के माध्यम से reasonably usable रहना चाहिए।

इसका अर्थ है कि essential visual information के लिए meaningful non-visual access path होना चाहिए।

System इस requirement को निम्न माध्यमों से satisfy कर सकता है:

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

System को इन पर exclusively rely नहीं करना चाहिए:

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

जब वह information essential functionality को understand या operate करने के लिए required हो।

यदि user sight के बिना essential system को reasonably navigate, understand, या operate नहीं कर सकता, तो system इस case में fail हो सकता है।

<a id="sound-unavailable"></a>

## Sound Unavailable

जब sound unavailable हो, तो system को sight और touch के माध्यम से reasonably usable रहना चाहिए।

इसका अर्थ है कि essential auditory information के लिए meaningful non-auditory access path होना चाहिए।

System इस requirement को निम्न माध्यमों से satisfy कर सकता है:

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

System को इन पर exclusively rely नहीं करना चाहिए:

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

जब वह information essential functionality को understand या operate करने के लिए required हो।

यदि user sound के बिना essential system को reasonably navigate, understand, या operate नहीं कर सकता, तो system इस case में fail हो सकता है।

<a id="touch-unavailable"></a>

## Touch Unavailable

जब touch unavailable हो, तो system को sight और sound के माध्यम से reasonably usable रहना चाहिए।

इसका अर्थ है कि essential tactile information और touch-based operation के लिए meaningful non-touch access path होना चाहिए।

System इस requirement को निम्न माध्यमों से satisfy कर सकता है:

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

System को इन पर exclusively rely नहीं करना चाहिए:

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

जब वह interaction essential functionality को understand या operate करने के लिए required हो।

यदि user touch के बिना essential system को reasonably navigate, understand, या operate नहीं कर सकता, तो system इस case में fail हो सकता है।

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

Conforming system को reviewed system के लिए appropriate stable accessibility mechanism use करना चाहिए।

Stable accessibility mechanism accessibility behavior को fragile या undocumented behavior पर निर्भर हुए बिना maintain, update, review, और extend करने की अनुमति देना चाहिए।

Stable accessibility mechanism में शामिल हो सकते हैं:

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
* system के लिए appropriate कोई अन्य stable structure

System को essential functionality को ऐसे implement करने से बचना चाहिए जिससे reasonable alternate access रुक जाए।

<a id="semantic-structure"></a>

### Semantic Structure

Conforming system को meaningful content या controls present करने पर semantic structure provide करना चाहिए।

Semantic structure में शामिल हो सकते हैं:

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

Semantic structure विशेष रूप से sight unavailable होने पर महत्त्वपूर्ण है, क्योंकि assistive technologies visual interfaces को non-visual output के माध्यम से communicate करने के लिए अक्सर semantic information पर rely करती हैं।

यदि essential controls या content को समझा नहीं जा सकता क्योंकि उनकी structure, labels, या relationships alternate access paths से unavailable हैं, तो system review में fail हो सकता है।

<a id="alternate-output"></a>

### Alternate Output

Conforming system को reasonable alternate output provide करना चाहिए जब essential meaning otherwise unavailable sense पर depend करे।

Alternate output में शामिल हो सकते हैं:

* auditory information के लिए visual output
* visual information के लिए auditory output
* visual या auditory information के लिए tactile output
* text equivalents
* captions
* transcripts
* spoken descriptions
* visible status messages
* haptic confirmation
* another appropriate output path

Alternate output को essential meaning preserve करना चाहिए।

<a id="alternate-input"></a>

### Alternate Input

Conforming system को reasonable alternate input provide करना चाहिए जब essential operation otherwise touch alone पर depend करे।

Alternate input में शामिल हो सकते हैं:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input को fastest या most convenient input method होना आवश्यक नहीं है। Essential operation के लिए sufficient होना चाहिए।

<a id="accessible-feedback"></a>

### Accessible Feedback

Conforming system को essential actions के लिए accessible feedback provide करना चाहिए।

Accessible feedback में शामिल हो सकते हैं:

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

Related accessibility case में feedback unavailable sense पर exclusively rely नहीं करना चाहिए।

उदाहरण के लिए, sound unavailable होने पर sound-only success chime sufficient नहीं है। Sight unavailable होने पर color-only error state sufficient नहीं है। Touch unavailable होने पर vibration-only confirmation sufficient नहीं है।

<a id="accessible-configuration"></a>

### Accessible Configuration

Conforming system को users को इस specification द्वारा defined वही accessibility requirements के माध्यम से required accessibility settings तक पहुँचने और उन्हें use करने देना चाहिए।

Accessibility settings inaccessible path के पीछे hidden नहीं होनी चाहिए।

उदाहरण के लिए, screen-reader-compatible mode sufficient नहीं है यदि user को उसे enable करने के लिए पहले unlabeled visual-only menu navigate करना पड़े।

यदि system की accessibility configuration उस condition में reach या operate नहीं की जा सकती जिसे support करने के लिए वह intended है, तो system review में fail हो सकता है।

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

System within spec तब माना जाता है जब CatalystUI Team ने system की review की हो और यह conclude करना reasonable पाया हो कि वह A11YSPEC satisfy करता है।

System within spec हो सकता है जब:

* sight-unavailable use reasonably supported रहे
* sound-unavailable use reasonably supported रहे
* touch-unavailable use reasonably supported रहे
* essential functionality प्रत्येक required case में accessible रहे
* critical functionality प्रत्येक required case में accessible रहे
* alternate access paths essential meaning और operation preserve करें
* accessibility settings, जब present हों, accessibly reached और used की जा सकें
* system essential functionality को किसी एक required sense के पीछे trap न करे
* system अपने design के लिए appropriate stable accessibility mechanism use करे

System within spec हो सकता है भले ही experiences सभी sensory paths में identical न हों।

System within spec हो सकता है भले ही कुछ nonessential functionality हर required accessibility case में equally available न हो।

<a id="warnings"></a>

### Warnings

Warning तब issue की जा सकती है जब system A11YSPEC satisfy करता हुआ दिखता है लेकिन उसमें ऐसे concerns हैं जिन्हें documented किया जाना चाहिए।

Warnings में शामिल हो सकते हैं:

* किसी एक accessibility case में minor nonessential content unavailable होना
* slower but usable alternate access paths
* imperfect but understandable captions or transcripts
* limited but functional keyboard navigation
* limited but functional screen-reader support
* minor focus-order concerns that do not block essential use
* redundant visual, auditory, or tactile cues missing from one path
* accessibility settings that are usable but difficult to find
* assistive-technology support that works but could be clearer
* optional workflows that are not equally accessible

Warnings necessarily verification को prevent नहीं करतीं।

<a id="failures"></a>

### Failures

Failure तब होता है जब कोई system A11YSPEC की एक या अधिक required conditions satisfy नहीं करता।

Failures में शामिल हो सकते हैं:

* sight unavailable होने पर essential functionality unavailable होना
* sound unavailable होने पर essential functionality unavailable होना
* touch unavailable होने पर essential functionality unavailable होना
* किसी भी required accessibility case में critical functionality unavailable होना
* essential visual information के लिए कोई reasonable alternate access path न होना
* essential auditory information के लिए कोई reasonable alternate access path न होना
* essential touch-based operation के लिए कोई reasonable alternate access path न होना
* accessibility settings उस condition में unreachable होना जिसे support करने के लिए वे meant हैं
* non-visual use के लिए required होने पर meaningful labels या structure के बिना controls
* visual, tactile, या text equivalent के बिना sound-only warnings
* non-visual equivalent के बिना color-only status
* keyboard, pointer, voice, switch, या other alternative के बिना gesture-only operation
* visual या auditory equivalent के बिना haptic-only confirmation
* essential workflows के लिए broken assistive-technology support
* major navigation traps
* essential workflows जिन्हें unavailable sense के बिना complete नहीं किया जा सकता

Failures resolve होने तक verification को prevent करती हैं।

<a id="verification-validity"></a>

### Verification Validity

A11YSPEC verification केवल verification जारी होने के समय system की reviewed state पर लागू होती है।

System later updates में verification बनाए रख सकता है यदि वह verified accessibility foundation को preserve करता रहे।

Minor wording changes, visual refinements, performance improvements, added accessibility features, और ordinary content updates verification को automatically invalidate नहीं करते।

नई review की आवश्यकता हो सकती है यदि कोई system:

* alternate access paths हटाता है
* assistive-technology support तोड़ता है
* essential navigation को substantially बदलता है
* required accessibility settings हटाता है
* interaction behavior को ऐसे बदलता है जिससे verified accessibility प्रभावित होती है
* accessible alternatives के बिना new essential workflows introduce करता है
* previously accessible critical functionality को inaccessible बनाता है
* accessible behavior को single-sense-dependent behavior से replace करता है

दूसरे शब्दों में, accessibility improve करना आमतौर पर ठीक है।

Verified access model को break करना review require कर सकता है।
