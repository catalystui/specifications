<!-- यह अनुवाद ChatGPT द्वारा बनाया गया था और किसी मानव अनुवादक द्वारा इसकी समीक्षा की जानी चाहिए। -->

<!-- अनुवाद सत्यापित होने के बाद pull request में इन पंक्तियों को हटा दें। -->

# I18NSPEC

<br/>

> **Internationalization Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> यहाँ प्रस्तुत definitions, requirements, और concepts practical internationalization support को describe करते हैं और इन्हें freely re-expressed किया जा सकता है।

<a id="introduction"></a>
## Introduction

**Internationalization Specification (I18NSPEC)** CatalystUI ecosystem के भीतर multilingual support evaluate करने के लिए उपयोग होने वाले core concepts, terminology, और requirements स्थापित करता है। इसका उद्देश्य यह निर्धारित करने के लिए clear standard देना है कि कोई system, service, framework, application, या implementation within spec माने जाने के लिए पर्याप्त language support देता है या नहीं।

Internationalization महत्वपूर्ण है क्योंकि user interface clearly communicate नहीं कर सकता यदि उसका essential meaning केवल एक भाषा में available हो। कोई system technically functional हो सकता है, लेकिन यदि users उसके labels, instructions, controls, settings, warnings, errors, या core workflows नहीं समझ सकते, तो system उन users के लिए meaningful interface देने में fail हुआ है।

यह specification perfect translation quality, literary style, cultural adaptation, legal compliance, या complete regional localization को measure करने की कोशिश नहीं करता। इसके बजाय, यह required CatalystUI locale set में users को system के essential portions तक meaningfully access और operate करने के लिए required minimum multilingual foundation define करता है।

सरल शब्दों में, I18NSPEC तीन primary questions पूछता है:

1. क्या users हर required language में system के essential parts access कर सकते हैं?
2. क्या users अपनी समझ की language reasonably select कर सकते हैं?
3. क्या system languages के बीच enough meaning preserve करता है ताकि वह usable रहे?

> [!IMPORTANT]
>
> I18NSPEC verification के लिए internationalization requirements define करता है। यह हर language के लिए अलग specification नहीं है। हर required locale को उसी specification के against check किया जाता है।

<a id="table-of-contents"></a>
## Table of Contents

* [I18NSPEC](#i18nspec)

  * [Introduction](#introduction)
  * [Table of Contents](#table-of-contents)
  * [Conformance](#conformance)
  * [Required Locale Set](#required-locale-set)
  * [User-Facing Content](#user-facing-content)

    * [User-Facing Content](#user-facing-content-1)
    * [Essential User-Facing Content](#essential-user-facing-content)
    * [Critical User-Facing Content](#critical-user-facing-content)
    * [Nonessential Content](#nonessential-content)
  * [Translation Coverage](#translation-coverage)

    * [Essential Translation Coverage](#essential-translation-coverage)
    * [Coverage Requirement](#coverage-requirement)
    * [Critical Content Requirement](#critical-content-requirement)
  * [Language Selection](#language-selection)

    * [Active Locale](#active-locale)
    * [Default Locale](#default-locale)
    * [Language Selection Mechanism](#language-selection-mechanism)
    * [Language Option Labels](#language-option-labels)
  * [Fallbacks and Locale Equivalence](#fallbacks-and-locale-equivalence)

    * [Fallback Locale](#fallback-locale)
    * [Fallback Behavior](#fallback-behavior)
    * [Locale Equivalence](#locale-equivalence)
  * [Implementation Requirements](#implementation-requirements)

    * [Stable Translation Mechanism](#stable-translation-mechanism)
    * [Preservation of Meaning](#preservation-of-meaning)
    * [Direction-Sensitive Languages](#direction-sensitive-languages)
    * [Locale-Sensitive Values](#locale-sensitive-values)
  * [Verification](#verification)

    * [Within Spec](#within-spec)
    * [Warnings](#warnings)
    * [Failures](#failures)
    * [Verification Validity](#verification-validity)

<a id="conformance"></a>
## Conformance

किसी system को I18NSPEC के अनुरूप तब माना जाता है जब वह required locale set की हर locale के लिए इस document में defined requirements satisfy करता है।

Conforming system को:

1. required locale set की हर locale support करनी होगी।
2. हर required locale में essential user-facing content के 75% से अधिक के लिए translated content देना होगा।
3. हर required locale में सभी critical user-facing content के लिए translated content देना होगा।
4. active locale select करने के लिए reasonable end-user mechanism देना होगा।
5. system के लिए appropriate stable translation mechanism का उपयोग करना होगा।
6. translated user-facing content का essential meaning preserve करना होगा।
7. translation coverage claim करने के लिए fallback content पर rely करने से बचना होगा, सिवाय वहाँ जहाँ review के दौरान locale equivalence accepted हो।

इस specification के अनुरूप होने के लिए system को एक specific implementation pattern उपयोग करने की आवश्यकता नहीं है। वह resource files, translation tables, locale-aware routing, compiled language resources, static localized pages, runtime language packs, database-backed translations, या system के लिए appropriate किसी अन्य stable mechanism का उपयोग कर सकता है।

Verification practical user access और essential meaning से संबंधित है, किसी एक rigid technical architecture से नहीं।

<a id="required-locale-set"></a>
## Required Locale Set

Required locale set उन languages और regional variants को define करता है जिन्हें CatalystUI Internationalization Verification के लिए review किया जाना चाहिए।

वर्तमान required locale set में निम्न locales शामिल हैं:

| Locale    | भाषा                     |
| --------- | ------------------------ |
| `ar-SA`   | अरबी (सऊदी अरब)          |
| `bn-BD`   | बंगाली (बांग्लादेश)      |
| `de-DE`   | जर्मन (जर्मनी)           |
| `en-GB`   | अंग्रेज़ी (यूनाइटेड किंगडम) |
| `en-IN`   | अंग्रेज़ी (भारत)         |
| `en-US`   | अंग्रेज़ी (संयुक्त राज्य) |
| `es-ES`   | स्पेनिश (स्पेन)          |
| `es-MX`   | स्पेनिश (मेक्सिको)       |
| `fa-IR`   | फ़ारसी (ईरान)            |
| `fr-FR`   | फ़्रेंच (फ़्रांस)        |
| `hi-IN`   | हिंदी (भारत)             |
| `id-ID`   | इंडोनेशियाई (इंडोनेशिया) |
| `it-IT`   | इतालवी (इटली)            |
| `ja-JP`   | जापानी (जापान)           |
| `ko-KR`   | कोरियाई (दक्षिण कोरिया)  |
| `nl-NL`   | डच (नीदरलैंड)            |
| `pl-PL`   | पोलिश (पोलैंड)           |
| `pt-BR`   | पुर्तगाली (ब्राज़ील)     |
| `ru-RU`   | रूसी (रूस)               |
| `tl-PH`   | तागालोग (फ़िलिपींस)     |
| `tr-TR`   | तुर्की (तुर्किये)        |
| `uk-UA`   | यूक्रेनी (यूक्रेन)       |
| `ur-PK`   | उर्दू (पाकिस्तान)        |
| `vi-VN`   | वियतनामी (वियतनाम)       |
| `zh-CN`   | चीनी (चीन)               |
| `zh-Hans` | चीनी (सरलीकृत)           |

Within spec माने जाने के लिए system को हर listed locale के लिए पर्याप्त essential translation support देना होगा।

Required locale set हर language, dialect, region, या script को represent करने के लिए नहीं है। इसके बजाय, यह कई common technology-facing language groups में broad international usability के लिए practical baseline स्थापित करता है।

<a id="user-facing-content"></a>
## User-Facing Content

<a id="user-facing-content-1"></a>
### User-Facing Content

User-facing content वह कोई भी content है जिसे end-user द्वारा perceive, read, hear, select, understand, या act upon किया जाना intended हो।

User-facing content में शामिल हो सकते हैं:

* navigation
* labels
* buttons
* menus
* controls
* headings
* dialogs
* settings
* instructions
* prompts
* warnings
* errors
* confirmations
* status messages
* onboarding text
* required help text
* language selection controls
* core workflow content

User-facing content visual होना आवश्यक नहीं है। यह auditory, tactile, symbolic, या multisensory content भी हो सकता है, जब वह content user को meaning communicate करता है।

<a id="essential-user-facing-content"></a>
### Essential User-Facing Content

Essential user-facing content वह user-facing content है जिसकी user को system के essential behavior को understand, navigate, configure, या operate करने के लिए reasonably आवश्यकता होती है।

Essential user-facing content में शामिल हो सकते हैं:

* primary navigation
* core screens and views
* settings and preferences
* user-facing labels
* user-facing controls
* required instructions
* important warnings
* important errors
* essential prompts
* required confirmation messages
* language selection controls
* normal use के लिए needed core workflows

I18NSPEC satisfy करने के लिए system को हर optional page, hidden message, internal label, या nonessential text translate करने की आवश्यकता नहीं है। फिर भी, ordinary essential use के लिए required content को इस specification की requirements के अनुसार translate किया जाना चाहिए।

<a id="critical-user-facing-content"></a>
### Critical User-Facing Content

Critical user-facing content वह essential user-facing content है जिसकी गलत समझ meaningful use को रोक सकती है, serious error पैदा कर सकती है, या user को consequence समझे बिना important decision लेने का कारण बन सकती है।

Critical user-facing content में शामिल हो सकते हैं:

* language selection controls
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
* language settings तक पहुँचने के लिए required core navigation

Critical user-facing content हर required locale के लिए translated होना चाहिए।

75% essential translation coverage threshold का उपयोग critical content untranslated छोड़ने के लिए नहीं किया जाना चाहिए।

<a id="nonessential-content"></a>
### Nonessential Content

Nonessential content वह content है जो user को system के essential behavior को understand, navigate, configure, या operate करने के लिए reasonably required नहीं है।

Nonessential content में शामिल हो सकते हैं:

* internal identifiers
* source code names
* debug-only strings
* developer-facing implementation details
* hidden diagnostic text
* optional marketing pages
* optional support pages
* reviewed scope के बाहर nonessential legal या business text
* reviewed system द्वारा controlled न किया गया third-party content

Nonessential content translate किया जा सकता है, लेकिन I18NSPEC conformance के लिए required नहीं है, जब तक वह essential user understanding या operation के लिए necessary न बन जाए।

<a id="translation-coverage"></a>
## Translation Coverage

<a id="essential-translation-coverage"></a>
### Essential Translation Coverage

Essential translation coverage किसी specific locale के लिए translated essential user-facing content की amount है।

Coverage को file size, byte count, line count, repository size, या pages की संख्या के बजाय meaningful user-facing content units से evaluate किया जाना चाहिए।

उदाहरण के लिए, essential action control करने वाला एक untranslated button, ordinary use को affect न करने वाले बड़े untranslated optional paragraph से अधिक महत्वपूर्ण हो सकता है।

Translation coverage को इस आधार पर judge किया जाना चाहिए कि user reviewed locale में essential system को meaningfully understand और operate कर सकता है या नहीं।

<a id="coverage-requirement"></a>
### Coverage Requirement

किसी system की locale के लिए translation coverage requirement तब satisfied होती है जब उस locale के लिए essential user-facing content का 75% से अधिक translated हो।

System I18NSPEC coverage requirement तब satisfy करता है जब वह required locale set की हर locale के लिए यह threshold meet करता है।

Practical review में इसे इस तरह represent किया जा सकता है:

| Locale  | Essential Translation Coverage | Result |
| ------- | ------------------------------ | ------ |
| `en-US` | 100%                           | Pass   |
| `es-ES` | 94%                            | Pass   |
| `ar-SA` | 78%                            | Pass   |
| `ja-JP` | 61%                            | Fail   |

75% या उससे कम coverage वाली locale coverage requirement satisfy नहीं करती।

75% से अधिक coverage वाली locale भी fail हो सकती है यदि critical user-facing content untranslated हो।

<a id="critical-content-requirement"></a>
### Critical Content Requirement

सभी critical user-facing content हर required locale के लिए translated होना चाहिए।

System general coverage threshold satisfy करने पर भी I18NSPEC fail कर सकता है यदि एक या अधिक critical user-facing content items missing, untranslated, misleading, या meaningfully understandable नहीं हैं।

उदाहरण के लिए, यदि general interface translated है लेकिन account deletion warning, purchase confirmation, security warning, या language selector untranslated रहता है, तो system को within spec नहीं माना जाना चाहिए।

<a id="language-selection"></a>
## Language Selection

<a id="active-locale"></a>
### Active Locale

Active locale वह locale है जो अभी user experience के लिए selected है।

Active locale तय करती है कि कौन-सा translated content user को displayed, provided, या otherwise communicated होना चाहिए।

<a id="default-locale"></a>
### Default Locale

Default locale वह locale है जो तब उपयोग की जाती है जब user ने active locale select नहीं की हो या कोई user preference available न हो।

System को default locale define करनी होगी।

Default locale reviewer के लिए documented या reasonably inferable होनी चाहिए।

<a id="language-selection-mechanism"></a>
### Language Selection Mechanism

Conforming system को end-user को active locale बदलने का reasonable तरीका देना होगा।

Language selection mechanism user को इनकी आवश्यकता के बिना available होना चाहिए:

* source code modify करना
* developer tools उपयोग करना
* undocumented configuration files edit करना
* unofficial patches install करना
* hidden behavior पर rely करना
* ordinary language changes के लिए support से contact करना

Language selection mechanism इन माध्यमों से provided हो सकता है:

* application settings
* account preferences
* language selector
* startup prompt
* browser settings
* operating system settings
* device settings
* कोई अन्य appropriate end-user-accessible mechanism

Mechanism को कोई एक specific design pattern follow करने की आवश्यकता नहीं है। उसे user को supported language select करने की reasonable अनुमति देनी होगी।

<a id="language-option-labels"></a>
### Language Option Labels

Language options display करते समय, system को हर language को इस तरह identify करना चाहिए जो उस language को बोलने वाले users के लिए understandable हो।

Language option में शामिल हो सकते हैं:

* उस language में language name
* currently active language में language name
* locale code
* regional label
* script label

उदाहरण:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Exact formatting अलग हो सकती है।

Intent यह है कि users अपनी language पहचान सकें, जब संभव हो currently displayed language name समझ सकें, और associated locale code identify कर सकें।

<a id="fallbacks-and-locale-equivalence"></a>
## Fallbacks and Locale Equivalence

<a id="fallback-locale"></a>
### Fallback Locale

Fallback locale वह locale है जिसका उपयोग तब होता है जब active locale के लिए translated content unavailable हो।

Fallback locales usability preserve करने में मदद कर सकती हैं, लेकिन fallback content automatic रूप से active locale के लिए translated content नहीं माना जाता।

उदाहरण के लिए, यदि system `es-MX` पर set है लेकिन Spanish translation missing होने के कारण `en-US` text दिखाता है, तो वह English text fallback के रूप में useful हो सकता है, लेकिन उसे Spanish translation coverage में count नहीं किया जाना चाहिए।

<a id="fallback-behavior"></a>
### Fallback Behavior

Conforming system localized content unavailable होने पर fallback behavior उपयोग कर सकता है।

Fallback behavior को broken, empty, या misleading output से बचना चाहिए।

Fallback behavior का उपयोग required locale के लिए translation coverage falsely claim करने के लिए नहीं किया जाना चाहिए।

यदि fallback behavior excessive, confusing, undocumented है, या required locale में essential content untranslated दिखाई देता है, तो system को warning या failure मिल सकता है।

<a id="locale-equivalence"></a>
### Locale Equivalence

Locale equivalence तब होती है जब एक translation essential understanding या operation को रोके बिना reasonably एक से अधिक locale की सेवा कर सकती है।

उदाहरण के लिए, यदि essential meaning हर locale के users के लिए clear रहता है, तो system `en-US`, `en-GB`, और `en-IN` के लिए एक English translation उपयोग कर सकता है।

Review के दौरान locale equivalence accepted हो सकती है जब regional differences minor हों और essential usability पर materially असर न डालें।

Locale equivalence का उपयोग तब नहीं किया जाना चाहिए जब missing locale meaningful confusion पैदा करे, important regional terminology omit करे, essential behavior तोड़े, या users को system समझने से रोक दे।

उदाहरण के लिए, system को यह assume नहीं करना चाहिए कि unrelated languages equivalent हैं क्योंकि वे writing direction, geographic region, script family, या broad cultural category share करती हैं।

Locale equivalence review judgment है, automatic rule नहीं।

<a id="implementation-requirements"></a>
## Implementation Requirements

<a id="stable-translation-mechanism"></a>
### Stable Translation Mechanism

Conforming system को reviewed system के लिए appropriate stable translation mechanism का उपयोग करना होगा।

Stable translation mechanism को translated content maintain, update, review, और extend करने देना चाहिए, fragile या undocumented behavior पर rely किए बिना।

Stable translation mechanism में शामिल हो सकते हैं:

* resource files
* translation tables
* locale-aware routing
* compiled language assets
* static localized pages
* runtime language packs
* database-backed translations
* कोई अन्य documented translation structure

System को essential user-facing content को इस तरह hardcode करने से बचना चाहिए जो required translation support रोक दे।

<a id="preservation-of-meaning"></a>
### Preservation of Meaning

Translation meaning तब preserve करती है जब user source language के users जैसी same essential instruction, label, warning, control, setting, या workflow reasonably समझ सकता है।

Translation को source content से word-for-word identical होना आवश्यक नहीं है।

Translation target language में same essential meaning communicate करने के लिए word order, grammar, sentence structure, idiom, tone, या phrasing बदल सकती है।

Translation review fail कर सकती है यदि वह misleading, incomplete, nonsensical, machine-corrupted, या source content से meaningfully different हो और essential use को affect करे।

<a id="direction-sensitive-languages"></a>
### Direction-Sensitive Languages

कुछ required locales commonly right-to-left text direction उपयोग करती हैं।

Conforming system को essential translated content को read, understand, select, या act upon करने से रोकना नहीं चाहिए केवल इसलिए कि active locale अलग text direction उपयोग करती है।

System को direction-sensitive languages के लिए readable ordering, punctuation behavior, और control association preserve करनी चाहिए।

Full visual polish, typography quality, accessibility behavior, और layout refinement को separate review की आवश्यकता हो सकती है। फिर भी, essential translated content meaningfully usable रहना चाहिए।

<a id="locale-sensitive-values"></a>
### Locale-Sensitive Values

Locale-sensitive values वे values हैं जिनका meaning या readability language, region, script, या culture के अनुसार vary कर सकता है।

Locale-sensitive values में शामिल हो सकते हैं:

* dates
* times
* numbers
* currencies
* measurements
* plural forms
* grammatical gender
* sorting order
* address formats
* phone number formats

I18NSPEC हर locale-sensitive value की complete localization require नहीं करता, जब तक वह value system को understand या operate करने के लिए essential न हो।

जब locale-sensitive values essential हों, तो system को उन्हें इस तरह represent करना चाहिए कि active locale के users उन्हें reasonably समझ सकें।

<a id="verification"></a>
## Verification

<a id="within-spec"></a>
### Within Spec

System within spec तब माना जाता है जब CatalystUI Team ने system review किया हो और यह conclude करना reasonable पाया हो कि वह I18NSPEC satisfy करता है।

System within spec हो सकता है जब:

* हर required locale supported हो
* हर required locale के लिए essential user-facing content का 75% से अधिक translated हो
* हर required locale के लिए all critical user-facing content translated हो
* users active locale reasonably select कर सकें
* fallback behavior translation coverage falsely claim न करे
* locale equivalence, यदि उपयोग की गई हो, reasonable और documented हो
* translated content essential meaning preserve करे

System within spec हो सकता है भले ही कुछ nonessential content untranslated रहे।

System within spec हो सकता है भले translations perfect न हों, बशर्ते essential meaning preserved हो और इस specification की requirements satisfied हों।

<a id="warnings"></a>
### Warnings

Warning तब issue हो सकती है जब system I18NSPEC satisfy करता हुआ दिखे लेकिन उसमें ऐसी concerns हों जिन्हें document किया जाना चाहिए।

Warnings में शामिल हो सकते हैं:

* minor untranslated nonessential content
* locales के बीच inconsistent terminology
* imperfect but understandable translations
* acceptable locale equivalence जिसे document किया जाना चाहिए
* limited fallback behavior
* partially translated optional pages
* direction-sensitive layout concerns जो essential use को नहीं रोकतीं
* locale-sensitive values जो understandable हैं लेकिन ideal नहीं

Warnings necessarily verification को prevent नहीं करतीं।

<a id="failures"></a>
### Failures

Failure तब होती है जब system I18NSPEC की एक या अधिक required conditions satisfy नहीं करता।

Failures में शामिल हो सकते हैं:

* required locale के लिए missing support
* required locale के लिए essential translation coverage 75% या उससे कम होना
* untranslated critical user-facing content
* reasonable language selection mechanism का न होना
* language selection के लिए source code modification required होना
* language selection के लिए developer tools required होना
* broken translation loading
* misleading locale claims
* excessive fallback behavior
* valid locale equivalence के बिना fallback content को translated content count करना
* direction-sensitive content unreadable या unusable होना
* एक या अधिक required locales में essential workflows unavailable होना

Failures resolved होने तक verification रोकती हैं।

<a id="verification-validity"></a>
### Verification Validity

I18NSPEC verification केवल system की reviewed state पर लागू होती है, उसी समय जब verification जारी की जाती है।

System बाद के updates में verification बनाए रख सकता है, जब तक वह verified internationalization foundation preserve करता है।

Minor wording changes, added translations, improved translations, और ordinary content updates automatic रूप से verification invalidate नहीं करते।

नई review required हो सकती है यदि system:

* required locale support हटाता है
* language selection तोड़ता है
* essential translation coverage substantially कम करता है
* new essential workflows untranslated छोड़ता है
* translated content को fallback content से replace करता है
* translation architecture को इस तरह बदलता है जिससे verified behavior affect हो
* major user-facing changes introduce करता है जो reviewed scope बदलते हैं

दूसरे शब्दों में, translation support सुधारना सामान्यतः ठीक है।

Verified multilingual foundation तोड़ना review की आवश्यकता पैदा कर सकता है।
