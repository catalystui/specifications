<!-- এই অনুবাদটি ChatGPT দ্বারা তৈরি করা হয়েছে এবং একজন মানব অনুবাদক দ্বারা পর্যালোচনা করা উচিত। -->

<!-- অনুবাদ যাচাই হয়ে গেলে pull request-এ এই লাইনগুলো সরিয়ে ফেলুন। -->

# I18NSPEC

<br/>

> **Internationalization Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> এখানে উপস্থাপিত definitions, requirements, এবং concepts ব্যবহারিক internationalization support বর্ণনা করে এবং সেগুলি স্বাধীনভাবে পুনরায় প্রকাশ করা যেতে পারে।

<a id="introduction"></a>
## ভূমিকা

**Internationalization Specification (I18NSPEC)** CatalystUI ecosystem-এর মধ্যে multilingual support মূল্যায়নের জন্য ব্যবহৃত core concepts, terminology, এবং requirements প্রতিষ্ঠা করে। এর উদ্দেশ্য হলো কোনো system, service, framework, application, অথবা implementation within spec বিবেচিত হওয়ার মতো যথেষ্ট language support দেয় কি না তা নির্ধারণের জন্য একটি clear standard প্রদান করা।

Internationalization গুরুত্বপূর্ণ, কারণ user interface যদি তার essential meaning কেবল এক ভাষায় দেয়, তবে সেটি স্পষ্টভাবে communicate করতে পারে না। কোনো system technically functional হতে পারে, কিন্তু users যদি তার labels, instructions, controls, settings, warnings, errors, অথবা core workflows বুঝতে না পারে, তবে systemটি সেই users-দের জন্য meaningful interface দিতে ব্যর্থ হয়েছে।

এই specification perfect translation quality, literary style, cultural adaptation, legal compliance, অথবা complete regional localization পরিমাপ করার চেষ্টা করে না। এর পরিবর্তে, এটি required CatalystUI locale set জুড়ে users যেন system-এর essential portions meaningfully access ও operate করতে পারে, সেই minimum multilingual foundation সংজ্ঞায়িত করে।

সহজভাবে বললে, I18NSPEC তিনটি primary question করে:

1. Users কি প্রতিটি required language-এ system-এর essential parts access করতে পারে?
2. Users কি তারা যে language বোঝে সেটি reasonably select করতে পারে?
3. System কি languages জুড়ে যথেষ্ট meaning preserve করে যাতে usable থাকে?

> [!IMPORTANT]
>
> I18NSPEC verification-এর জন্য internationalization requirements সংজ্ঞায়িত করে। এটি প্রতিটি language-এর জন্য আলাদা specification নয়। প্রতিটি required locale একই specification-এর বিরুদ্ধে check করা হয়।

<a id="table-of-contents"></a>
## বিষয়সূচি

* [I18NSPEC](#i18nspec)

  * [ভূমিকা](#introduction)
  * [বিষয়সূচি](#table-of-contents)
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

একটি system I18NSPEC-এর সঙ্গে conformant বিবেচিত হয় যখন এটি required locale set-এর প্রতিটি locale-এর জন্য এই document-এ সংজ্ঞায়িত requirements পূরণ করে।

একটি conforming system-কে অবশ্যই:

1. required locale set-এর প্রতিটি locale support করতে হবে।
2. প্রতিটি required locale-এ essential user-facing content-এর 75%-এর বেশি translated content প্রদান করতে হবে।
3. প্রতিটি required locale-এ সমস্ত critical user-facing content-এর translated content প্রদান করতে হবে।
4. active locale select করার জন্য reasonable end-user mechanism প্রদান করতে হবে।
5. system-এর জন্য appropriate stable translation mechanism ব্যবহার করতে হবে।
6. translated user-facing content-এর essential meaning preserve করতে হবে।
7. translation coverage দাবি করার জন্য fallback content-এর ওপর নির্ভর করা এড়াতে হবে, review-এর সময় locale equivalence accepted হওয়া ব্যতিক্রম।

এই specification-এর সঙ্গে conform করতে system-এর এক নির্দিষ্ট implementation pattern ব্যবহার করার প্রয়োজন নেই। এটি resource files, translation tables, locale-aware routing, compiled language resources, static localized pages, runtime language packs, database-backed translations, অথবা system-এর জন্য appropriate অন্য কোনো stable mechanism ব্যবহার করতে পারে।

Verification practical user access এবং essential meaning নিয়ে concerned; এক rigid technical architecture নিয়ে নয়।

<a id="required-locale-set"></a>
## Required Locale Set

Required locale set সেই languages এবং regional variants সংজ্ঞায়িত করে যেগুলি CatalystUI Internationalization Verification-এর জন্য review করতে হবে।

বর্তমান required locale set-এ নিম্নলিখিত locales অন্তর্ভুক্ত:

| Locale    | Language                 |
| --------- | ------------------------ |
| `ar-SA`   | Arabic (Saudi Arabia)    |
| `bn-BD`   | Bengali (Bangladesh)     |
| `de-DE`   | German (Germany)         |
| `en-GB`   | English (United Kingdom) |
| `en-IN`   | English (India)          |
| `en-US`   | English (United States)  |
| `es-ES`   | Spanish (Spain)          |
| `es-MX`   | Spanish (Mexico)         |
| `fa-IR`   | Persian (Iran)           |
| `fr-FR`   | French (France)          |
| `hi-IN`   | Hindi (India)            |
| `id-ID`   | Indonesian (Indonesia)   |
| `it-IT`   | Italian (Italy)          |
| `ja-JP`   | Japanese (Japan)         |
| `ko-KR`   | Korean (South Korea)     |
| `nl-NL`   | Dutch (Netherlands)      |
| `pl-PL`   | Polish (Poland)          |
| `pt-BR`   | Portuguese (Brazil)      |
| `ru-RU`   | Russian (Russia)         |
| `tl-PH`   | Tagalog (Philippines)    |
| `tr-TR`   | Turkish (Turkey)         |
| `uk-UA`   | Ukrainian (Ukraine)      |
| `ur-PK`   | Urdu (Pakistan)          |
| `vi-VN`   | Vietnamese (Vietnam)     |
| `zh-CN`   | Chinese (China)          |
| `zh-Hans` | Chinese (Simplified)     |

within spec বিবেচিত হতে system-কে প্রতিটি listed locale-এর জন্য sufficient essential translation support প্রদান করতে হবে।

Required locale set প্রতিটি language, dialect, region, অথবা script উপস্থাপন করার উদ্দেশ্যে নয়। এর পরিবর্তে, এটি অনেক common technology-facing language group জুড়ে broad international usability-এর জন্য একটি practical baseline স্থাপন করে।

<a id="user-facing-content"></a>
## User-Facing Content

<a id="user-facing-content-1"></a>
### User-Facing Content

User-facing content হলো এমন content যা end-user দ্বারা perceive, read, hear, select, understand, অথবা acted upon হওয়ার উদ্দেশ্যে তৈরি।

User-facing content-এর মধ্যে থাকতে পারে:

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

User-facing content visual হতে হবে এমন নয়। এটি auditory, tactile, symbolic, অথবা multisensory content-ও হতে পারে, যখন সেই content user-এর কাছে meaning communicate করে।

<a id="essential-user-facing-content"></a>
### Essential User-Facing Content

Essential user-facing content হলো এমন user-facing content যা user system-এর essential behavior বুঝতে, navigate করতে, configure করতে, অথবা operate করতে reasonably needs করে।

Essential user-facing content-এর মধ্যে থাকতে পারে:

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

I18NSPEC satisfy করতে system-এর প্রতিটি optional page, hidden message, internal label, অথবা nonessential text অনুবাদ করার প্রয়োজন নেই। তবে ordinary essential use-এর জন্য required content এই specification-এর requirements অনুযায়ী translated হতে হবে।

<a id="critical-user-facing-content"></a>
### Critical User-Facing Content

Critical user-facing content হলো essential user-facing content যেখানে misunderstanding meaningful use আটকাতে পারে, serious error তৈরি করতে পারে, অথবা user-কে consequence না বুঝে important decision নিতে বাধ্য করতে পারে।

Critical user-facing content-এর মধ্যে থাকতে পারে:

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

Critical user-facing content প্রতিটি required locale-এর জন্য translated হতে হবে।

75% essential translation coverage threshold critical content untranslated রাখার জন্য ব্যবহার করা যাবে না।

<a id="nonessential-content"></a>
### Nonessential Content

Nonessential content হলো এমন content যা user system-এর essential behavior বুঝতে, navigate করতে, configure করতে, অথবা operate করতে reasonably required নয়।

Nonessential content-এর মধ্যে থাকতে পারে:

* internal identifiers
* source code names
* debug-only strings
* developer-facing implementation details
* hidden diagnostic text
* optional marketing pages
* optional support pages
* reviewed scope-এর বাইরে nonessential legal or business text
* reviewed system-এর control-এর বাইরে third-party content

Nonessential content translated হতে পারে, কিন্তু essential user understanding বা operation-এর জন্য necessary না হলে I18NSPEC conformance-এর জন্য required নয়।

<a id="translation-coverage"></a>
## Translation Coverage

<a id="essential-translation-coverage"></a>
### Essential Translation Coverage

Essential translation coverage হলো specific locale-এর জন্য translated essential user-facing content-এর পরিমাণ।

Coverage file size, byte count, line count, repository size, অথবা number of pages দ্বারা নয়, meaningful user-facing content units দ্বারা evaluate করা উচিত।

উদাহরণস্বরূপ, essential action control করা একটি untranslated button, ordinary use affect না করা একটি বড় untranslated optional paragraph-এর চেয়ে বেশি গুরুত্বপূর্ণ হতে পারে।

Translation coverage বিচার করা উচিত user reviewed locale-এ essential system meaningfully understand এবং operate করতে পারে কি না তার ওপর।

<a id="coverage-requirement"></a>
### Coverage Requirement

কোনো locale-এর জন্য essential user-facing content-এর 75%-এর বেশি translated থাকলে system সেই locale-এর translation coverage requirement satisfy করে।

required locale set-এর প্রতিটি locale-এর জন্য এই threshold পূরণ করলে system I18NSPEC coverage requirement satisfy করে।

Practical review-এ এটি এভাবে represent করা যেতে পারে:

| Locale  | Essential Translation Coverage | Result |
| ------- | ------------------------------ | ------ |
| `en-US` | 100%                           | Pass   |
| `es-ES` | 94%                            | Pass   |
| `ar-SA` | 78%                            | Pass   |
| `ja-JP` | 61%                            | Fail   |

75% coverage বা তার কম থাকা locale coverage requirement satisfy করে না।

75%-এর বেশি coverage থাকা locale-ও fail করতে পারে যদি critical user-facing content untranslated থাকে।

<a id="critical-content-requirement"></a>
### Critical Content Requirement

সমস্ত critical user-facing content প্রতিটি required locale-এর জন্য translated হতে হবে।

এক বা একাধিক critical user-facing content item missing, untranslated, misleading, অথবা meaningfully understandable না হলে, general coverage threshold satisfy করলেও system I18NSPEC fail করতে পারে।

উদাহরণস্বরূপ, general interface translated হলেও account deletion warning, purchase confirmation, security warning, অথবা language selector untranslated থাকলে system within spec বিবেচিত হওয়া উচিত নয়।

<a id="language-selection"></a>
## Language Selection

<a id="active-locale"></a>
### Active Locale

Active locale হলো user experience-এর জন্য বর্তমানে selected locale।

Active locale নির্ধারণ করে কোন translated content user-এর কাছে displayed, provided, অথবা otherwise communicated হওয়া উচিত।

<a id="default-locale"></a>
### Default Locale

Default locale হলো user active locale select না করলে অথবা user preference unavailable থাকলে ব্যবহৃত locale।

একটি system-কে default locale define করতে হবে।

Default locale reviewer-এর কাছে documented অথবা reasonably inferable হওয়া উচিত।

<a id="language-selection-mechanism"></a>
### Language Selection Mechanism

একটি conforming system-কে end-user-এর active locale পরিবর্তনের জন্য reasonable way প্রদান করতে হবে।

Language selection mechanism এমনভাবে available হতে হবে যাতে user-কে এসব করতে না হয়:

* source code modify করা
* developer tools ব্যবহার করা
* undocumented configuration files edit করা
* unofficial patches install করা
* hidden behavior-এর ওপর rely করা
* ordinary language changes-এর জন্য support contact করা

Language selection mechanism প্রদান করা যেতে পারে:

* application settings
* account preferences
* language selector
* startup prompt
* browser settings
* operating system settings
* device settings
* অন্য কোনো appropriate end-user-accessible mechanism

Mechanism-টির এক নির্দিষ্ট design pattern follow করার প্রয়োজন নেই। এটি user-কে supported language select করতে reasonably allow করতে হবে।

<a id="language-option-labels"></a>
### Language Option Labels

Language options display করার সময়, system-এর উচিত প্রতিটি language এমনভাবে identify করা যা সেই language-ভাষী users-দের কাছে understandable।

একটি language option অন্তর্ভুক্ত করতে পারে:

* সেই language-এ language name
* currently active language-এ language name
* locale code
* regional label
* script label

উদাহরণস্বরূপ:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

নির্দিষ্ট formatting ভিন্ন হতে পারে।

Intent হলো users যেন নিজের language recognize করতে পারে, সম্ভব হলে currently displayed language name বুঝতে পারে, এবং associated locale code identify করতে পারে।

<a id="fallbacks-and-locale-equivalence"></a>
## Fallbacks and Locale Equivalence

<a id="fallback-locale"></a>
### Fallback Locale

Fallback locale হলো এমন locale যা active locale-এর জন্য translated content unavailable হলে ব্যবহৃত হয়।

Fallback locales usability preserve করতে সাহায্য করতে পারে, কিন্তু fallback content automatically active locale-এর translated content বিবেচিত হয় না।

উদাহরণস্বরূপ, যদি কোনো system `es-MX`-এ set করা থাকে কিন্তু Spanish translation missing হওয়ায় `en-US` text display করে, সেই English text fallback হিসেবে useful হতে পারে, কিন্তু সেটি Spanish translation coverage হিসেবে counted হওয়া উচিত নয়।

<a id="fallback-behavior"></a>
### Fallback Behavior

Localized content unavailable হলে conforming system fallback behavior ব্যবহার করতে পারে।

Fallback behavior broken, empty, অথবা misleading output এড়ানো উচিত।

Required locale-এর translation coverage falsely claim করতে fallback behavior ব্যবহার করা যাবে না।

Fallback behavior excessive, confusing, undocumented হলে, অথবা required locale-এ essential content untranslated দেখালে system warning বা failure পেতে পারে।

<a id="locale-equivalence"></a>
### Locale Equivalence

Locale equivalence ঘটে যখন একটি translation essential understanding বা operation আটকানো ছাড়াই একাধিক locale reasonably serve করতে পারে।

উদাহরণস্বরূপ, essential meaning প্রতিটি locale-এর users-এর কাছে clear থাকলে system `en-US`, `en-GB`, এবং `en-IN`-এর জন্য একটি English translation ব্যবহার করতে পারে।

Regional differences minor হলে এবং essential usability materially affect না করলে review-এর সময় locale equivalence accepted হতে পারে।

Missing locale meaningful confusion তৈরি করলে, important regional terminology omit করলে, essential behavior break করলে, অথবা users-দের system understand করা থেকে আটকালে locale equivalence ব্যবহার করা যাবে না।

উদাহরণস্বরূপ, writing direction, geographic region, script family, অথবা broad cultural category share করে বলে unrelated languages equivalent ধরে নেওয়া system-এর উচিত নয়।

Locale equivalence একটি review judgment, automatic rule নয়।

<a id="implementation-requirements"></a>
## Implementation Requirements

<a id="stable-translation-mechanism"></a>
### Stable Translation Mechanism

একটি conforming system-কে reviewed system-এর জন্য appropriate stable translation mechanism ব্যবহার করতে হবে।

Stable translation mechanism translated content maintain, update, review, এবং extend করার সুযোগ দেওয়া উচিত, fragile বা undocumented behavior-এর ওপর নির্ভর না করে।

Stable translation mechanism অন্তর্ভুক্ত করতে পারে:

* resource files
* translation tables
* locale-aware routing
* compiled language assets
* static localized pages
* runtime language packs
* database-backed translations
* অন্য কোনো documented translation structure

Required translation support বাধাগ্রস্ত করে এমনভাবে essential user-facing content hardcode করা system-এর এড়ানো উচিত।

<a id="preservation-of-meaning"></a>
### Preservation of Meaning

একটি translation meaning preserve করে যখন user source language-এর users-এর মতো একই essential instruction, label, warning, control, setting, অথবা workflow reasonably understand করতে পারে।

Translation source content-এর word-for-word identical হতে হবে এমন নয়।

Target language-এ একই essential meaning communicate করার জন্য প্রয়োজন হলে translation word order, grammar, sentence structure, idiom, tone, অথবা phrasing পরিবর্তন করতে পারে।

Translation misleading, incomplete, nonsensical, machine-corrupted, অথবা essential use affect করে এমনভাবে source content থেকে meaningfully different হলে review fail করতে পারে।

<a id="direction-sensitive-languages"></a>
### Direction-Sensitive Languages

কিছু required locales সাধারণত right-to-left text direction ব্যবহার করে।

Active locale ভিন্ন text direction ব্যবহার করে বলে conforming system essential translated content পড়া, বোঝা, select করা, অথবা acted upon হওয়া আটকাতে পারবে না।

Direction-sensitive languages-এর জন্য system readable ordering, punctuation behavior, এবং control association preserve করা উচিত।

Full visual polish, typography quality, accessibility behavior, এবং layout refinement separate review প্রয়োজন করতে পারে। তবে essential translated content meaningfully usable থাকতে হবে।

<a id="locale-sensitive-values"></a>
### Locale-Sensitive Values

Locale-sensitive values হলো এমন values যাদের meaning বা readability language, region, script, অথবা culture অনুযায়ী vary করতে পারে।

Locale-sensitive values-এর মধ্যে থাকতে পারে:

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

I18NSPEC প্রতিটি locale-sensitive value-এর complete localization require করে না, যদি না valueটি system বুঝতে বা operate করতে essential হয়।

Locale-sensitive values essential হলে system-এর উচিত সেগুলি এমনভাবে represent করা যাতে active locale-এর users reasonably understand করতে পারে।

<a id="verification"></a>
## Verification

<a id="within-spec"></a>
### Within Spec

CatalystUI Team system review করে এবং I18NSPEC satisfy করে বলে reasonable conclusion পেলে system within spec বিবেচিত হয়।

একটি system within spec হতে পারে যখন:

* প্রতিটি required locale supported
* প্রতিটি required locale-এর জন্য essential user-facing content-এর 75%-এর বেশি translated
* প্রতিটি required locale-এর জন্য all critical user-facing content translated
* users active locale reasonably select করতে পারে
* fallback behavior translation coverage falsely claim করে না
* locale equivalence, ব্যবহার করা হলে, reasonable এবং documented
* translated content essential meaning preserve করে

কিছু nonessential content untranslated থাকলেও system within spec হতে পারে।

Translations perfect না হলেও system within spec হতে পারে, provided essential meaning preserved থাকে এবং এই specification-এর requirements satisfied হয়।

<a id="warnings"></a>
### Warnings

কোনো system I18NSPEC satisfy করছে বলে মনে হলেও document করা উচিত এমন concerns থাকলে warning issue করা যেতে পারে।

Warnings অন্তর্ভুক্ত করতে পারে:

* minor untranslated nonessential content
* locales জুড়ে inconsistent terminology
* imperfect but understandable translations
* acceptable locale equivalence that should be documented
* limited fallback behavior
* partially translated optional pages
* direction-sensitive layout concerns that do not prevent essential use
* locale-sensitive values that are understandable but not ideal

Warnings necessarily verification prevent করে না।

<a id="failures"></a>
### Failures

System I18NSPEC-এর এক বা একাধিক required condition satisfy না করলে failure ঘটে।

Failures অন্তর্ভুক্ত করতে পারে:

* required locale-এর support missing
* required locale-এর essential translation coverage 75% বা তার নিচে
* untranslated critical user-facing content
* reasonable language selection mechanism নেই
* language selection-এর জন্য source code modification required
* language selection-এর জন্য developer tools required
* broken translation loading
* misleading locale claims
* excessive fallback behavior
* valid locale equivalence ছাড়া fallback content translated content হিসেবে counted
* direction-sensitive content unreadable বা unusable
* এক বা একাধিক required locale-এ essential workflows unavailable

Failures resolved না হওয়া পর্যন্ত verification prevent করে।

<a id="verification-validity"></a>
### Verification Validity

I18NSPEC verification কেবল system-এর reviewed state-এ প্রযোজ্য, verification issued হওয়ার সময়।

Verified internationalization foundation preserve করলে system later updates জুড়ে verification retain করতে পারে।

Minor wording changes, added translations, improved translations, এবং ordinary content updates automatically verification invalidate করে না।

নতুন review প্রয়োজন হতে পারে যদি system:

* required locale support সরিয়ে দেয়
* language selection ভেঙে দেয়
* essential translation coverage উল্লেখযোগ্যভাবে কমিয়ে দেয়
* new essential workflows untranslated রেখে দেয়
* translated content fallback content দিয়ে replace করে
* verified behavior affect করে এমনভাবে translation architecture পরিবর্তন করে
* reviewed scope alter করে এমন major user-facing changes introduce করে

অন্যভাবে বললে, translation support উন্নত করা সাধারণত ঠিক আছে।

Verified multilingual foundation ভেঙে দিলে review প্রয়োজন হতে পারে।
