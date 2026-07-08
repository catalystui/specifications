<!-- Цей переклад було створено ChatGPT, і його має переглянути перекладач-людина. -->

<!-- Видаліть ці рядки у pull request після перевірки перекладу. -->

# I18NSPEC

<br/>

> **Специфікація інтернаціоналізації**<br/>
> Ревізія 1<br/>
> 8 липня 2026 року<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Подані тут визначення, вимоги й концепції описують практичну підтримку інтернаціоналізації та можуть бути вільно переказані.

<a id="introduction"></a>
## Вступ

**Internationalization Specification (I18NSPEC)** встановлює core concepts, terminology і requirements, які використовуються для оцінки multilingual support в екосистемі CatalystUI. Її мета — надати clear standard для визначення, чи system, service, framework, application або implementation забезпечує достатню language support, щоб вважатися within spec.

Internationalization важлива, бо user interface не може clearly communicate, якщо його essential meaning доступний лише однією мовою. System може бути technically functional, але якщо users не можуть зрозуміти labels, instructions, controls, settings, warnings, errors або core workflows, тоді system не надав meaningful interface для цих users.

Ця specification не намагається вимірювати perfect translation quality, literary style, cultural adaptation, legal compliance або complete regional localization. Натомість вона визначає minimum multilingual foundation, потрібний для того, щоб users могли meaningfully access and operate essential portions system у всьому required CatalystUI locale set.

Простіше кажучи, I18NSPEC ставить три основні questions:

1. Чи можуть users access essential parts system кожною required language?
2. Чи можуть users reasonably select language, яку вони розуміють?
3. Чи system preserve enough meaning across languages, щоб залишатися usable?

> [!IMPORTANT]
>
> I18NSPEC визначає internationalization requirements for verification. Це не окрема specification для кожної language. Кожен required locale перевіряється за тією самою specification.

<a id="table-of-contents"></a>
## Зміст

* [I18NSPEC](#i18nspec)

  * [Вступ](#introduction)
  * [Зміст](#table-of-contents)
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

System вважається conformant з I18NSPEC, коли вона задовольняє requirements, визначені цим document, для кожного locale у required locale set.

Conforming system повинна:

1. Support кожен locale у required locale set.
2. Provide translated content для понад 75% essential user-facing content у кожному required locale.
3. Provide translated content для всього critical user-facing content у кожному required locale.
4. Provide reasonable end-user mechanism для selecting active locale.
5. Use stable translation mechanism, appropriate to the system.
6. Preserve essential meaning of translated user-facing content.
7. Avoid relying on fallback content to claim translation coverage, except where locale equivalence is accepted during review.

System не повинна використовувати один specific implementation pattern, щоб conform to this specification. Вона може використовувати resource files, translation tables, locale-aware routing, compiled language resources, static localized pages, runtime language packs, database-backed translations або інший stable mechanism, appropriate to the system.

Verification стосується practical user access і essential meaning, а не однієї rigid technical architecture.

<a id="required-locale-set"></a>
## Required Locale Set

Required locale set визначає languages і regional variants, які мають бути reviewed для CatalystUI Internationalization Verification.

Поточний required locale set включає такі locales:

| Locale    | Мова                     |
| --------- | ------------------------ |
| `ar-SA`   | Арабська (Саудівська Аравія) |
| `bn-BD`   | Бенгальська (Бангладеш)  |
| `de-DE`   | Німецька (Німеччина)     |
| `en-GB`   | Англійська (Велика Британія) |
| `en-IN`   | Англійська (Індія)       |
| `en-US`   | Англійська (США)         |
| `es-ES`   | Іспанська (Іспанія)      |
| `es-MX`   | Іспанська (Мексика)      |
| `fa-IR`   | Перська (Іран)           |
| `fr-FR`   | Французька (Франція)     |
| `hi-IN`   | Гінді (Індія)            |
| `id-ID`   | Індонезійська (Індонезія) |
| `it-IT`   | Італійська (Італія)      |
| `ja-JP`   | Японська (Японія)        |
| `ko-KR`   | Корейська (Південна Корея) |
| `nl-NL`   | Нідерландська (Нідерланди) |
| `pl-PL`   | Польська (Польща)        |
| `pt-BR`   | Португальська (Бразилія) |
| `ru-RU`   | Російська (Росія)        |
| `tl-PH`   | Тагальська (Філіппіни)   |
| `tr-TR`   | Турецька (Туреччина)     |
| `uk-UA`   | Українська (Україна)     |
| `ur-PK`   | Урду (Пакистан)          |
| `vi-VN`   | Вʼєтнамська (Вʼєтнам)    |
| `zh-CN`   | Китайська (Китай)        |
| `zh-Hans` | Китайська (спрощена)     |

System має надати sufficient essential translation support для кожного listed locale, щоб вважатися within spec.

Required locale set не призначений представляти every language, dialect, region або script. Натомість він established practical baseline для broad international usability серед багатьох common technology-facing language groups.

<a id="user-facing-content"></a>
## User-Facing Content

<a id="user-facing-content-1"></a>
### User-Facing Content

User-facing content — це будь-який content, intended to be perceived, read, heard, selected, understood або acted upon by an end-user.

User-facing content може включати:

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

User-facing content не обовʼязково має бути visual. Він також може включати auditory, tactile, symbolic або multisensory content, коли цей content communicates meaning to the user.

<a id="essential-user-facing-content"></a>
### Essential User-Facing Content

Essential user-facing content — це user-facing content, який user reasonably needs, щоб understand, navigate, configure або operate essential behavior of a system.

Essential user-facing content може включати:

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

System не повинна translate every optional page, hidden message, internal label або nonessential text, щоб satisfy I18NSPEC. Однак content, required for ordinary essential use, має бути translated according to the requirements of this specification.

<a id="critical-user-facing-content"></a>
### Critical User-Facing Content

Critical user-facing content — це essential user-facing content, де misunderstanding може prevent meaningful use, create a serious error або cause the user to make an important decision without understanding the consequence.

Critical user-facing content може включати:

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

Critical user-facing content має бути translated для кожного required locale.

75% essential translation coverage threshold не можна використовувати, щоб leave critical content untranslated.

<a id="nonessential-content"></a>
### Nonessential Content

Nonessential content — це content, який не є reasonably required для user, щоб understand, navigate, configure або operate essential behavior of a system.

Nonessential content може включати:

* internal identifiers
* source code names
* debug-only strings
* developer-facing implementation details
* hidden diagnostic text
* optional marketing pages
* optional support pages
* nonessential legal or business text outside the reviewed scope
* third-party content not controlled by the reviewed system

Nonessential content може бути translated, але він не required для I18NSPEC conformance, unless it becomes necessary for essential user understanding or operation.

<a id="translation-coverage"></a>
## Translation Coverage

<a id="essential-translation-coverage"></a>
### Essential Translation Coverage

Essential translation coverage — це amount of essential user-facing content translated for a specific locale.

Coverage should be evaluated by meaningful user-facing content units rather than by file size, byte count, line count, repository size або number of pages.

Наприклад, одна untranslated button, що controls an essential action, може бути важливішою, ніж large untranslated optional paragraph, який не affects ordinary use.

Translation coverage should be judged by whether the user can meaningfully understand and operate the essential system in the reviewed locale.

<a id="coverage-requirement"></a>
### Coverage Requirement

System satisfies the translation coverage requirement for a locale, коли понад 75% essential user-facing content translated for that locale.

System satisfies the I18NSPEC coverage requirement, коли вона meets this threshold для every locale in the required locale set.

У practical review це може бути represented as:

| Locale  | Essential Translation Coverage | Result |
| ------- | ------------------------------ | ------ |
| `en-US` | 100%                           | Pass   |
| `es-ES` | 94%                            | Pass   |
| `ar-SA` | 78%                            | Pass   |
| `ja-JP` | 61%                            | Fail   |

Locale з 75% coverage або менше не satisfies the coverage requirement.

Locale з more than 75% coverage все ще може fail, якщо critical user-facing content untranslated.

<a id="critical-content-requirement"></a>
### Critical Content Requirement

All critical user-facing content має бути translated для кожного required locale.

System може fail I18NSPEC, навіть коли satisfies the general coverage threshold, якщо один або більше critical user-facing content items missing, untranslated, misleading або not meaningfully understandable.

Наприклад, system не має вважатися within spec, якщо general interface translated, але account deletion warning, purchase confirmation, security warning або language selector remains untranslated.

<a id="language-selection"></a>
## Language Selection

<a id="active-locale"></a>
### Active Locale

Active locale — це locale, currently selected для user’s experience.

Active locale determines, which translated content should be displayed, provided або otherwise communicated to the user.

<a id="default-locale"></a>
### Default Locale

Default locale — це locale, used when the user has not selected an active locale або when no user preference is available.

System must define a default locale.

Default locale should be documented або reasonably inferable by the reviewer.

<a id="language-selection-mechanism"></a>
### Language Selection Mechanism

Conforming system must provide a reasonable way for the end-user to change the active locale.

Language selection mechanism must be available without requiring the user to:

* modify source code
* use developer tools
* edit undocumented configuration files
* install unofficial patches
* rely on hidden behavior
* contact support for ordinary language changes

Language selection mechanism may be provided through:

* application settings
* account preferences
* a language selector
* a startup prompt
* browser settings
* operating system settings
* device settings
* another appropriate end-user-accessible mechanism

Mechanism не повинен follow one specific design pattern. Він must reasonably allow the user to select a supported language.

<a id="language-option-labels"></a>
### Language Option Labels

When displaying language options, system should identify each language in a way that is understandable to users who speak that language.

Language option може включати:

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

Intent полягає в тому, що users should be able to recognize their own language, understand the currently displayed language name when possible, and identify the associated locale code.

<a id="fallbacks-and-locale-equivalence"></a>
## Fallbacks and Locale Equivalence

<a id="fallback-locale"></a>
### Fallback Locale

Fallback locale — це locale, used when translated content is unavailable for the active locale.

Fallback locales можуть help preserve usability, але fallback content не automatically considered translated content for the active locale.

Наприклад, якщо system set to `es-MX`, але displays `en-US` text because the Spanish translation is missing, that English text may be useful as a fallback, but it should not be counted as Spanish translation coverage.

<a id="fallback-behavior"></a>
### Fallback Behavior

Conforming system may use fallback behavior when localized content is unavailable.

Fallback behavior should avoid broken, empty, or misleading output.

Fallback behavior must not be used to falsely claim translation coverage for a required locale.

System may receive a warning or failure, if fallback behavior is excessive, confusing, undocumented, or causes essential content to appear untranslated in a required locale.

<a id="locale-equivalence"></a>
### Locale Equivalence

Locale equivalence occurs when one translation can reasonably serve more than one locale without preventing essential understanding or operation.

Наприклад, system may use one English translation for `en-US`, `en-GB`, and `en-IN`, if the essential meaning remains clear for users of each locale.

Locale equivalence may be accepted during review when regional differences are minor and do not materially affect essential usability.

Locale equivalence must not be used when a missing locale would create meaningful confusion, omit important regional terminology, break essential behavior, or prevent users from understanding the system.

Наприклад, system should not assume that unrelated languages are equivalent because they share a writing direction, geographic region, script family, or broad cultural category.

Locale equivalence is a review judgment, not an automatic rule.

<a id="implementation-requirements"></a>
## Implementation Requirements

<a id="stable-translation-mechanism"></a>
### Stable Translation Mechanism

Conforming system must use a stable translation mechanism appropriate to the system being reviewed.

Stable translation mechanism should allow translated content to be maintained, updated, reviewed, and extended without relying on fragile or undocumented behavior.

Stable translation mechanism may include:

* resource files
* translation tables
* locale-aware routing
* compiled language assets
* static localized pages
* runtime language packs
* database-backed translations
* another documented translation structure

System should avoid hardcoding essential user-facing content in a way that prevents required translation support.

<a id="preservation-of-meaning"></a>
### Preservation of Meaning

Translation preserves meaning when the user can reasonably understand the same essential instruction, label, warning, control, setting, or workflow as users of the source language.

Translation does not need to be word-for-word identical to the source content.

Translation may change word order, grammar, sentence structure, idiom, tone, or phrasing when necessary to communicate the same essential meaning in the target language.

Translation may fail review if it is misleading, incomplete, nonsensical, machine-corrupted, or meaningfully different from the source content in a way that affects essential use.

<a id="direction-sensitive-languages"></a>
### Direction-Sensitive Languages

Some required locales commonly use right-to-left text direction.

Conforming system must not prevent essential translated content from being read, understood, selected, or acted upon because the active locale uses a different text direction.

System should preserve readable ordering, punctuation behavior, and control association for direction-sensitive languages.

Full visual polish, typography quality, accessibility behavior, and layout refinement may require separate review. However, essential translated content must remain meaningfully usable.

<a id="locale-sensitive-values"></a>
### Locale-Sensitive Values

Locale-sensitive values — це values, whose meaning or readability may vary by language, region, script, or culture.

Locale-sensitive values may include:

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

I18NSPEC does not require complete localization of every locale-sensitive value unless that value is essential to understanding or operating the system.

When locale-sensitive values are essential, the system should represent them in a way that users of the active locale can reasonably understand.

<a id="verification"></a>
## Verification

<a id="within-spec"></a>
### Within Spec

System is considered within spec when the CatalystUI Team has reviewed the system and found it reasonable to conclude that it satisfies I18NSPEC.

System may be within spec when:

* every required locale is supported
* more than 75% of essential user-facing content is translated for each required locale
* all critical user-facing content is translated for each required locale
* users can reasonably select the active locale
* fallback behavior does not falsely claim translation coverage
* locale equivalence, if used, is reasonable and documented
* translated content preserves essential meaning

System may be within spec even if some nonessential content remains untranslated.

System may be within spec even if translations are not perfect, provided the essential meaning is preserved and the requirements of this specification are satisfied.

<a id="warnings"></a>
### Warnings

Warning may be issued when a system appears to satisfy I18NSPEC but contains concerns that should be documented.

Warnings may include:

* minor untranslated nonessential content
* inconsistent terminology across locales
* imperfect but understandable translations
* acceptable locale equivalence that should be documented
* limited fallback behavior
* partially translated optional pages
* direction-sensitive layout concerns that do not prevent essential use
* locale-sensitive values that are understandable but not ideal

Warnings do not necessarily prevent verification.

<a id="failures"></a>
### Failures

Failure occurs when a system does not satisfy one or more required conditions of I18NSPEC.

Failures may include:

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

Failures prevent verification until resolved.

<a id="verification-validity"></a>
### Verification Validity

I18NSPEC verification applies only to the reviewed state of the system at the time verification is issued.

A system may retain verification across later updates so long as it preserves the verified internationalization foundation.

Minor wording changes, added translations, improved translations, and ordinary content updates do not automatically invalidate verification.

A new review may be required if a system:

* removes required locale support
* breaks language selection
* substantially reduces essential translation coverage
* leaves new essential workflows untranslated
* replaces translated content with fallback content
* changes its translation architecture in a way that affects verified behavior
* introduces major user-facing changes that alter the reviewed scope

In other words, improving translation support is usually fine.

Breaking the verified multilingual foundation may require review.
