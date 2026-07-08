<!-- یہ ترجمہ ChatGPT کے ذریعے تیار کیا گیا ہے اور اسے کسی انسانی مترجم سے نظرثانی کروانی چاہیے۔ -->

<!-- ترجمے کی تصدیق کے بعد pull request میں یہ سطریں ہٹا دیں۔ -->

# I18NSPEC

<br/>

> **Internationalization Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> یہاں پیش کی گئی definitions، requirements، اور concepts practical internationalization support کو بیان کرتے ہیں اور انہیں آزادانہ طور پر دوبارہ بیان کیا جا سکتا ہے۔

<a id="introduction"></a>
## تعارف

**Internationalization Specification (I18NSPEC)** CatalystUI ecosystem میں multilingual support کو evaluate کرنے کے لیے استعمال ہونے والے core concepts، terminology، اور requirements قائم کرتی ہے۔ اس کا purpose یہ ہے کہ یہ determine کرنے کے لیے clear standard فراہم کیا جائے کہ کوئی system، service، framework، application، یا implementation کافی language support فراہم کرتا ہے یا نہیں تاکہ اسے within spec سمجھا جا سکے۔

Internationalization اہم ہے کیونکہ user interface واضح communication نہیں کر سکتا اگر اس کا essential meaning صرف ایک language میں available ہو۔ System technically functional ہو سکتا ہے، مگر اگر users اس کے labels، instructions، controls، settings، warnings، errors، یا core workflows نہیں سمجھ سکتے، تو system نے ان users کے لیے meaningful interface فراہم نہیں کیا۔

یہ specification perfect translation quality، literary style، cultural adaptation، legal compliance، یا complete regional localization کو measure کرنے کی کوشش نہیں کرتی۔ اس کے بجائے یہ minimum multilingual foundation define کرتی ہے جو users کو required CatalystUI locale set میں system کے essential portions تک meaningfully access اور operate کرنے کے لیے required ہے۔

آسان الفاظ میں، I18NSPEC تین primary questions پوچھتی ہے:

1. کیا users ہر required language میں system کے essential parts تک access کر سکتے ہیں؟
2. کیا users reasonably وہ language select کر سکتے ہیں جو وہ سمجھتے ہیں؟
3. کیا system languages کے درمیان enough meaning preserve کرتا ہے تاکہ usable رہے؟

> [!IMPORTANT]
>
> I18NSPEC verification کے لیے internationalization requirements define کرتی ہے۔ یہ ہر language کے لیے separate specification نہیں ہے۔ ہر required locale کو اسی specification کے against check کیا جاتا ہے۔

<a id="table-of-contents"></a>
## Table of Contents

* [I18NSPEC](#i18nspec)

  * [تعارف](#introduction)
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

System کو I18NSPEC کے ساتھ conformant تب سمجھا جاتا ہے جب وہ required locale set کے ہر locale کے لیے اس document میں defined requirements satisfy کرے۔

Conforming system کو چاہیے کہ:

1. Required locale set کے ہر locale کو support کرے۔
2. ہر required locale میں essential user-facing content کے 75% سے زیادہ کے لیے translated content provide کرے۔
3. ہر required locale میں تمام critical user-facing content کے لیے translated content provide کرے۔
4. Active locale select کرنے کے لیے reasonable end-user mechanism provide کرے۔
5. System کے لیے appropriate stable translation mechanism use کرے۔
6. Translated user-facing content کا essential meaning preserve کرے۔
7. Translation coverage claim کرنے کے لیے fallback content پر rely کرنے سے avoid کرے، except جہاں review کے دوران locale equivalence accepted ہو۔

System کو اس specification کے ساتھ conform کرنے کے لیے one specific implementation pattern use کرنے کی ضرورت نہیں۔ یہ resource files، translation tables، locale-aware routing، compiled language resources، static localized pages، runtime language packs، database-backed translations، یا system کے لیے appropriate کوئی اور stable mechanism use کر سکتا ہے۔

Verification practical user access اور essential meaning سے concerned ہے، one rigid technical architecture سے نہیں۔

<a id="required-locale-set"></a>
## Required Locale Set

Required locale set وہ languages اور regional variants define کرتا ہے جن کا CatalystUI Internationalization Verification کے لیے review ہونا ضروری ہے۔

موجودہ required locale set میں درج ذیل locales شامل ہیں:

| Locale    | زبان                     |
| --------- | ------------------------ |
| `ar-SA`   | عربی (سعودی عرب)         |
| `bn-BD`   | بنگالی (بنگلہ دیش)       |
| `de-DE`   | جرمن (جرمنی)             |
| `en-GB`   | انگریزی (برطانیہ)        |
| `en-IN`   | انگریزی (بھارت)          |
| `en-US`   | انگریزی (ریاستہائے متحدہ) |
| `es-ES`   | ہسپانوی (اسپین)          |
| `es-MX`   | ہسپانوی (میکسیکو)        |
| `fa-IR`   | فارسی (ایران)            |
| `fr-FR`   | فرانسیسی (فرانس)         |
| `hi-IN`   | ہندی (بھارت)             |
| `id-ID`   | انڈونیشیائی (انڈونیشیا)  |
| `it-IT`   | اطالوی (اٹلی)            |
| `ja-JP`   | جاپانی (جاپان)           |
| `ko-KR`   | کوریائی (جنوبی کوریا)    |
| `nl-NL`   | ڈچ (نیدرلینڈز)           |
| `pl-PL`   | پولش (پولینڈ)            |
| `pt-BR`   | پرتگالی (برازیل)         |
| `ru-RU`   | روسی (روس)               |
| `tl-PH`   | ٹیگالاگ (فلپائن)         |
| `tr-TR`   | ترکی (ترکیہ)             |
| `uk-UA`   | یوکرینی (یوکرین)         |
| `ur-PK`   | اردو (پاکستان)           |
| `vi-VN`   | ویتنامی (ویتنام)         |
| `zh-CN`   | چینی (چین)               |
| `zh-Hans` | چینی (آسان رسم الخط)     |

System کو within spec سمجھنے کے لیے ہر listed locale کے لیے sufficient essential translation support provide کرنا چاہیے۔

Required locale set ہر language، dialect، region، یا script کی نمائندگی کے لیے نہیں ہے۔ اس کے بجائے یہ بہت سے common technology-facing language groups میں broad international usability کے لیے practical baseline قائم کرتا ہے۔

<a id="user-facing-content"></a>
## User-Facing Content

<a id="user-facing-content-1"></a>
### User-Facing Content

User-facing content وہ content ہے جو end-user کے perceive، read، hear، select، understand، یا act upon کرنے کے لیے intended ہو۔

User-facing content میں شامل ہو سکتے ہیں:

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

User-facing content کا visual ہونا ضروری نہیں۔ یہ auditory، tactile، symbolic، یا multisensory content بھی ہو سکتا ہے جب وہ content user کو meaning communicate کرے۔

<a id="essential-user-facing-content"></a>
### Essential User-Facing Content

Essential user-facing content وہ user-facing content ہے جس کی user کو system کے essential behavior کو understand، navigate، configure، یا operate کرنے کے لیے reasonably ضرورت ہو۔

Essential user-facing content میں شامل ہو سکتے ہیں:

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
* core workflows needed for normal use

System کو I18NSPEC satisfy کرنے کے لیے ہر optional page، hidden message، internal label، یا nonessential text translate کرنے کی ضرورت نہیں۔ تاہم ordinary essential use کے لیے required content کو اس specification کی requirements کے مطابق translated ہونا چاہیے۔

<a id="critical-user-facing-content"></a>
### Critical User-Facing Content

Critical user-facing content وہ essential user-facing content ہے جہاں misunderstanding meaningful use کو روک سکتی ہے، serious error پیدا کر سکتی ہے، یا user کو consequence سمجھے بغیر important decision کرنے پر مجبور کر سکتی ہے۔

Critical user-facing content میں شامل ہو سکتے ہیں:

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
* core navigation required to reach language settings

Critical user-facing content کو ہر required locale کے لیے translated ہونا چاہیے۔

75% essential translation coverage threshold کو critical content untranslated چھوڑنے کے لیے استعمال نہیں کیا جانا چاہیے۔

<a id="nonessential-content"></a>
### Nonessential Content

Nonessential content وہ content ہے جو user کو system کے essential behavior کو understand، navigate، configure، یا operate کرنے کے لیے reasonably required نہیں ہوتا۔

Nonessential content میں شامل ہو سکتے ہیں:

* internal identifiers
* source code names
* debug-only strings
* developer-facing implementation details
* hidden diagnostic text
* optional marketing pages
* optional support pages
* nonessential legal or business text outside the reviewed scope
* third-party content not controlled by the reviewed system

Nonessential content translate کیا جا سکتا ہے، مگر I18NSPEC conformance کے لیے required نہیں جب تک وہ essential user understanding یا operation کے لیے necessary نہ ہو جائے۔

<a id="translation-coverage"></a>
## Translation Coverage

<a id="essential-translation-coverage"></a>
### Essential Translation Coverage

Essential translation coverage کسی specific locale کے لیے translated essential user-facing content کی مقدار ہے۔

Coverage کو file size، byte count، line count، repository size، یا number of pages کے بجائے meaningful user-facing content units سے evaluate کیا جانا چاہیے۔

مثال کے طور پر، ایک untranslated button جو essential action control کرتا ہے، large untranslated optional paragraph سے زیادہ matter کر سکتا ہے جو ordinary use affect نہیں کرتا۔

Translation coverage کو اس بنیاد پر judge کرنا چاہیے کہ user reviewed locale میں essential system کو meaningfully understand اور operate کر سکتا ہے یا نہیں۔

<a id="coverage-requirement"></a>
### Coverage Requirement

System کسی locale کے لیے translation coverage requirement تب satisfy کرتا ہے جب اس locale کے لیے essential user-facing content کا 75% سے زیادہ translated ہو۔

System I18NSPEC coverage requirement تب satisfy کرتا ہے جب وہ required locale set کے ہر locale کے لیے یہ threshold meet کرے۔

Practical review میں اسے یوں represent کیا جا سکتا ہے:

| Locale  | Essential Translation Coverage | Result |
| ------- | ------------------------------ | ------ |
| `en-US` | 100%                           | Pass   |
| `es-ES` | 94%                            | Pass   |
| `ar-SA` | 78%                            | Pass   |
| `ja-JP` | 61%                            | Fail   |

75% coverage یا اس سے کم والا locale coverage requirement satisfy نہیں کرتا۔

75% سے زیادہ coverage والا locale بھی fail ہو سکتا ہے اگر critical user-facing content untranslated ہو۔

<a id="critical-content-requirement"></a>
### Critical Content Requirement

تمام critical user-facing content ہر required locale کے لیے translated ہونا چاہیے۔

System I18NSPEC fail کر سکتا ہے، even when it satisfies the general coverage threshold، اگر ایک یا زیادہ critical user-facing content items missing، untranslated، misleading، یا not meaningfully understandable ہوں۔

مثال کے طور پر، system کو within spec نہیں سمجھنا چاہیے اگر general interface translated ہو مگر account deletion warning، purchase confirmation، security warning، یا language selector untranslated رہے۔

<a id="language-selection"></a>
## Language Selection

<a id="active-locale"></a>
### Active Locale

Active locale وہ locale ہے جو user’s experience کے لیے currently selected ہے۔

Active locale determine کرتا ہے کہ کون سا translated content user کو displayed، provided، یا otherwise communicated ہونا چاہیے۔

<a id="default-locale"></a>
### Default Locale

Default locale وہ locale ہے جو تب use ہوتا ہے جب user نے active locale select نہ کیا ہو یا no user preference available ہو۔

System کو default locale define کرنا چاہیے۔

Default locale documented یا reviewer کے لیے reasonably inferable ہونا چاہیے۔

<a id="language-selection-mechanism"></a>
### Language Selection Mechanism

Conforming system کو end-user کے لیے active locale change کرنے کا reasonable way provide کرنا چاہیے۔

Language selection mechanism user سے یہ require کیے بغیر available ہونا چاہیے کہ وہ:

* modify source code
* use developer tools
* edit undocumented configuration files
* install unofficial patches
* rely on hidden behavior
* contact support for ordinary language changes

Language selection mechanism ان طریقوں سے provide کیا جا سکتا ہے:

* application settings
* account preferences
* a language selector
* a startup prompt
* browser settings
* operating system settings
* device settings
* another appropriate end-user-accessible mechanism

Mechanism کو one specific design pattern follow کرنے کی ضرورت نہیں۔ اسے user کو supported language select کرنے کی reasonable اجازت دینی چاہیے۔

<a id="language-option-labels"></a>
### Language Option Labels

Language options دکھاتے وقت system کو ہر language ایسے identify کرنی چاہیے جو اس language بولنے والے users کے لیے understandable ہو۔

Language option میں شامل ہو سکتا ہے:

* the language name in that language
* the language name in the currently active language
* the locale code
* a regional label
* a script label

For example:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Exact formatting may vary.

Intent یہ ہے کہ users اپنی language recognize کر سکیں، possible ہو تو currently displayed language name سمجھ سکیں، اور associated locale code identify کر سکیں۔

<a id="fallbacks-and-locale-equivalence"></a>
## Fallbacks and Locale Equivalence

<a id="fallback-locale"></a>
### Fallback Locale

Fallback locale وہ locale ہے جو active locale کے لیے translated content unavailable ہونے پر use کیا جاتا ہے۔

Fallback locales usability preserve کرنے میں مدد دے سکتے ہیں، مگر fallback content automatically active locale کے لیے translated content نہیں سمجھا جاتا۔

مثال کے طور پر، اگر system `es-MX` پر set ہے مگر Spanish translation missing ہونے کی وجہ سے `en-US` text display کرتا ہے، تو وہ English text fallback کے طور پر useful ہو سکتا ہے، مگر اسے Spanish translation coverage میں count نہیں کیا جانا چاہیے۔

<a id="fallback-behavior"></a>
### Fallback Behavior

Conforming system localized content unavailable ہونے پر fallback behavior use کر سکتا ہے۔

Fallback behavior کو broken، empty، یا misleading output سے avoid کرنا چاہیے۔

Fallback behavior کو required locale کے لیے falsely claim translation coverage کرنے میں استعمال نہیں کیا جانا چاہیے۔

System کو warning یا failure مل سکتی ہے اگر fallback behavior excessive، confusing، undocumented ہو، یا required locale میں essential content کو untranslated ظاہر کرے۔

<a id="locale-equivalence"></a>
### Locale Equivalence

Locale equivalence تب ہوتی ہے جب ایک translation reasonably ایک سے زیادہ locale کی خدمت کر سکے without preventing essential understanding or operation.

مثال کے طور پر، system `en-US`، `en-GB`، اور `en-IN` کے لیے one English translation use کر سکتا ہے اگر essential meaning ہر locale کے users کے لیے clear رہے۔

Locale equivalence review کے دوران accept ہو سکتی ہے جب regional differences minor ہوں اور essential usability پر materially affect نہ کریں۔

Locale equivalence اس وقت use نہیں ہونی چاہیے جب missing locale meaningful confusion پیدا کرے، important regional terminology omit کرے، essential behavior break کرے، یا users کو system سمجھنے سے prevent کرے۔

مثال کے طور پر، system کو یہ assume نہیں کرنا چاہیے کہ unrelated languages equivalent ہیں کیونکہ وہ writing direction، geographic region، script family، یا broad cultural category share کرتی ہیں۔

Locale equivalence review judgment ہے، automatic rule نہیں۔

<a id="implementation-requirements"></a>
## Implementation Requirements

<a id="stable-translation-mechanism"></a>
### Stable Translation Mechanism

Conforming system کو reviewed system کے لیے appropriate stable translation mechanism use کرنا چاہیے۔

Stable translation mechanism کو translated content maintain، update، review، اور extend کرنے دینا چاہیے without relying on fragile or undocumented behavior.

Stable translation mechanism میں شامل ہو سکتے ہیں:

* resource files
* translation tables
* locale-aware routing
* compiled language assets
* static localized pages
* runtime language packs
* database-backed translations
* another documented translation structure

System کو essential user-facing content کو اس طرح hardcode کرنے سے avoid کرنا چاہیے جو required translation support کو prevent کرے۔

<a id="preservation-of-meaning"></a>
### Preservation of Meaning

Translation meaning preserve کرتی ہے جب user وہی essential instruction، label، warning، control، setting، یا workflow reasonably understand کر سکے جو source language کے users سمجھتے ہیں۔

Translation کو source content کے ساتھ word-for-word identical ہونا ضروری نہیں۔

Translation target language میں same essential meaning communicate کرنے کے لیے word order، grammar، sentence structure، idiom، tone، یا phrasing change کر سکتی ہے۔

Translation review fail کر سکتی ہے اگر وہ misleading، incomplete، nonsensical، machine-corrupted، یا source content سے meaningfully different ہو اس طرح کہ essential use affect ہو۔

<a id="direction-sensitive-languages"></a>
### Direction-Sensitive Languages

کچھ required locales عام طور پر right-to-left text direction استعمال کرتے ہیں۔

Conforming system کو active locale کی different text direction کی وجہ سے essential translated content کو read، understand، select، یا act upon کرنے سے prevent نہیں کرنا چاہیے۔

System کو direction-sensitive languages کے لیے readable ordering، punctuation behavior، اور control association preserve کرنا چاہیے۔

Full visual polish، typography quality، accessibility behavior، اور layout refinement separate review require کر سکتے ہیں۔ تاہم essential translated content meaningfully usable رہنا چاہیے۔

<a id="locale-sensitive-values"></a>
### Locale-Sensitive Values

Locale-sensitive values وہ values ہیں جن کا meaning یا readability language، region، script، یا culture کے لحاظ سے vary کر سکتا ہے۔

Locale-sensitive values میں شامل ہو سکتے ہیں:

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

I18NSPEC ہر locale-sensitive value کی complete localization require نہیں کرتا جب تک وہ value system کو understand یا operate کرنے کے لیے essential نہ ہو۔

جب locale-sensitive values essential ہوں، system کو انہیں اس طرح represent کرنا چاہیے کہ active locale کے users reasonably understand کر سکیں۔

<a id="verification"></a>
## Verification

<a id="within-spec"></a>
### Within Spec

System within spec تب سمجھا جاتا ہے جب CatalystUI Team نے system کا review کیا ہو اور یہ conclude کرنا reasonable پایا ہو کہ وہ I18NSPEC satisfy کرتا ہے۔

System within spec ہو سکتا ہے جب:

* every required locale is supported
* more than 75% of essential user-facing content is translated for each required locale
* all critical user-facing content is translated for each required locale
* users can reasonably select the active locale
* fallback behavior does not falsely claim translation coverage
* locale equivalence, if used, is reasonable and documented
* translated content preserves essential meaning

System within spec ہو سکتا ہے even if کچھ nonessential content untranslated رہے۔

System within spec ہو سکتا ہے even if translations perfect نہ ہوں، بشرطیکہ essential meaning preserved ہو اور اس specification کی requirements satisfied ہوں۔

<a id="warnings"></a>
### Warnings

Warning اس وقت issue ہو سکتی ہے جب system I18NSPEC satisfy کرتا دکھائی دے مگر ایسے concerns رکھتا ہو جنہیں documented ہونا چاہیے۔

Warnings میں شامل ہو سکتے ہیں:

* minor untranslated nonessential content
* inconsistent terminology across locales
* imperfect but understandable translations
* acceptable locale equivalence that should be documented
* limited fallback behavior
* partially translated optional pages
* direction-sensitive layout concerns that do not prevent essential use
* locale-sensitive values that are understandable but not ideal

Warnings لازماً verification کو prevent نہیں کرتیں۔

<a id="failures"></a>
### Failures

Failure اس وقت ہوتی ہے جب system I18NSPEC کی ایک یا زیادہ required conditions satisfy نہ کرے۔

Failures میں شامل ہو سکتے ہیں:

* missing support for a required locale
* essential translation coverage at or below 75% for a required locale
* untranslated critical user-facing content
* no reasonable language selection mechanism
* language selection requiring source code modification
* language selection requiring developer tools
* broken translation loading
* misleading locale claims
* excessive fallback behavior
* fallback content counted as translated content without valid locale equivalence
* direction-sensitive content being unreadable or unusable
* essential workflows being unavailable in one or more required locales

Failures resolved ہونے تک verification prevent کرتی ہیں۔

<a id="verification-validity"></a>
### Verification Validity

I18NSPEC verification صرف system کی reviewed state پر apply ہوتی ہے، اس وقت جب verification issue کی جاتی ہے۔

System later updates میں verification retain کر سکتا ہے جب تک وہ verified internationalization foundation preserve کرے۔

Minor wording changes، added translations، improved translations، اور ordinary content updates verification کو automatically invalidate نہیں کرتے۔

New review required ہو سکتا ہے اگر system:

* removes required locale support
* breaks language selection
* substantially reduces essential translation coverage
* leaves new essential workflows untranslated
* replaces translated content with fallback content
* changes its translation architecture in a way that affects verified behavior
* introduces major user-facing changes that alter the reviewed scope

دوسرے الفاظ میں، translation support improve کرنا generally fine ہے۔

Verified multilingual foundation کو break کرنا review require کر سکتا ہے۔
