# I18NSPEC

<br/>

> **Internationalization Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> The definitions, requirements, and concepts presented herein describe practical internationalization support and may be freely re-expressed.

## Introduction

The **Internationalization Specification (I18NSPEC)** establishes the core concepts, terminology, and requirements used to evaluate multilingual support within the CatalystUI ecosystem. Its purpose is to provide a clear standard for determining whether a system, service, framework, application, or implementation provides sufficient language support to be considered within spec.

Internationalization matters because a user interface cannot communicate clearly if its essential meaning is available in only one language. A system may be technically functional, but if users cannot understand its labels, instructions, controls, settings, warnings, errors, or core workflows, then the system has failed to provide a meaningful interface for those users.

This specification does not attempt to measure perfect translation quality, literary style, cultural adaptation, legal compliance, or complete regional localization. Instead, it defines the minimum multilingual foundation required for users to meaningfully access and operate the essential portions of a system across the required CatalystUI locale set.

In simpler terms, I18NSPEC asks three primary questions:

1. Can users access the essential parts of the system in each required language?
2. Can users reasonably select the language they understand?
3. Does the system preserve enough meaning across languages to remain usable?

> [!IMPORTANT]
>
> I18NSPEC defines internationalization requirements for verification. It is not a separate specification for each language. Each required locale is checked against the same specification.

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

## Conformance

A system is considered conformant with I18NSPEC when it satisfies the requirements defined by this document for each locale in the required locale set.

A conforming system must:

1. Support each locale in the required locale set.
2. Provide translated content for more than 75% of essential user-facing content in each required locale.
3. Provide translated content for all critical user-facing content in each required locale.
4. Provide a reasonable end-user mechanism for selecting the active locale.
5. Use a stable translation mechanism appropriate to the system.
6. Preserve the essential meaning of translated user-facing content.
7. Avoid relying on fallback content to claim translation coverage, except where locale equivalence is accepted during review.

A system does not need to use one specific implementation pattern to conform to this specification. It may use resource files, translation tables, locale-aware routing, compiled language resources, static localized pages, runtime language packs, database-backed translations, or another stable mechanism appropriate to the system.

Verification is concerned with practical user access and essential meaning, not one rigid technical architecture.

## Required Locale Set

The required locale set defines the languages and regional variants that must be reviewed for CatalystUI Internationalization Verification.

The current required locale set includes the following locales:

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

A system must provide sufficient essential translation support for each listed locale to be considered within spec.

The required locale set is not intended to represent every language, dialect, region, or script. Instead, it establishes a practical baseline for broad international usability across many common technology-facing language groups.

## User-Facing Content

### User-Facing Content

User-facing content is any content intended to be perceived, read, heard, selected, understood, or acted upon by an end-user.

User-facing content may include:

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

User-facing content does not need to be visual. It may also include auditory, tactile, symbolic, or multisensory content when that content communicates meaning to the user.

### Essential User-Facing Content

Essential user-facing content is user-facing content that a user reasonably needs in order to understand, navigate, configure, or operate the essential behavior of a system.

Essential user-facing content may include:

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

A system does not need to translate every optional page, hidden message, internal label, or nonessential text to satisfy I18NSPEC. However, the content required for ordinary essential use must be translated according to the requirements of this specification.

### Critical User-Facing Content

Critical user-facing content is essential user-facing content where misunderstanding may prevent meaningful use, create a serious error, or cause the user to make an important decision without understanding the consequence.

Critical user-facing content may include:

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

Critical user-facing content must be translated for each required locale.

The 75% essential translation coverage threshold must not be used to leave critical content untranslated.

### Nonessential Content

Nonessential content is content that is not reasonably required for a user to understand, navigate, configure, or operate the essential behavior of a system.

Nonessential content may include:

* internal identifiers
* source code names
* debug-only strings
* developer-facing implementation details
* hidden diagnostic text
* optional marketing pages
* optional support pages
* nonessential legal or business text outside the reviewed scope
* third-party content not controlled by the reviewed system

Nonessential content may be translated, but it is not required for I18NSPEC conformance unless it becomes necessary for essential user understanding or operation.

## Translation Coverage

### Essential Translation Coverage

Essential translation coverage is the amount of essential user-facing content translated for a specific locale.

Coverage should be evaluated by meaningful user-facing content units rather than by file size, byte count, line count, repository size, or number of pages.

For example, one untranslated button that controls an essential action may matter more than a large untranslated optional paragraph that does not affect ordinary use.

Translation coverage should be judged by whether the user can meaningfully understand and operate the essential system in the reviewed locale.

### Coverage Requirement

A system satisfies the translation coverage requirement for a locale when more than 75% of essential user-facing content is translated for that locale.

A system satisfies the I18NSPEC coverage requirement when it meets this threshold for every locale in the required locale set.

In practical review, this may be represented as:

| Locale  | Essential Translation Coverage | Result |
| ------- | ------------------------------ | ------ |
| `en-US` | 100%                           | Pass   |
| `es-ES` | 94%                            | Pass   |
| `ar-SA` | 78%                            | Pass   |
| `ja-JP` | 61%                            | Fail   |

A locale with 75% coverage or less does not satisfy the coverage requirement.

A locale with more than 75% coverage may still fail if critical user-facing content is untranslated.

### Critical Content Requirement

All critical user-facing content must be translated for each required locale.

A system may fail I18NSPEC even when it satisfies the general coverage threshold if one or more critical user-facing content items are missing, untranslated, misleading, or not meaningfully understandable.

For example, a system should not be considered within spec if the general interface is translated but the account deletion warning, purchase confirmation, security warning, or language selector remains untranslated.

## Language Selection

### Active Locale

The active locale is the locale currently selected for the user’s experience.

The active locale determines which translated content should be displayed, provided, or otherwise communicated to the user.

### Default Locale

The default locale is the locale used when the user has not selected an active locale or when no user preference is available.

A system must define a default locale.

The default locale should be documented or reasonably inferable by the reviewer.

### Language Selection Mechanism

A conforming system must provide a reasonable way for the end-user to change the active locale.

The language selection mechanism must be available without requiring the user to:

* modify source code
* use developer tools
* edit undocumented configuration files
* install unofficial patches
* rely on hidden behavior
* contact support for ordinary language changes

A language selection mechanism may be provided through:

* application settings
* account preferences
* a language selector
* a startup prompt
* browser settings
* operating system settings
* device settings
* another appropriate end-user-accessible mechanism

The mechanism does not need to follow one specific design pattern. It must reasonably allow the user to select a supported language.

### Language Option Labels

When displaying language options, a system should identify each language in a way that is understandable to users who speak that language.

A language option may include:

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

The exact formatting may vary.

The intent is that users should be able to recognize their own language, understand the currently displayed language name when possible, and identify the associated locale code.

## Fallbacks and Locale Equivalence

### Fallback Locale

A fallback locale is a locale used when translated content is unavailable for the active locale.

Fallback locales may help preserve usability, but fallback content is not automatically considered translated content for the active locale.

For example, if a system is set to `es-MX` but displays `en-US` text because the Spanish translation is missing, that English text may be useful as a fallback, but it should not be counted as Spanish translation coverage.

### Fallback Behavior

A conforming system may use fallback behavior when localized content is unavailable.

Fallback behavior should avoid broken, empty, or misleading output.

Fallback behavior must not be used to falsely claim translation coverage for a required locale.

A system may receive a warning or failure if fallback behavior is excessive, confusing, undocumented, or causes essential content to appear untranslated in a required locale.

### Locale Equivalence

Locale equivalence occurs when one translation can reasonably serve more than one locale without preventing essential understanding or operation.

For example, a system may use one English translation for `en-US`, `en-GB`, and `en-IN` if the essential meaning remains clear for users of each locale.

Locale equivalence may be accepted during review when regional differences are minor and do not materially affect essential usability.

Locale equivalence must not be used when a missing locale would create meaningful confusion, omit important regional terminology, break essential behavior, or prevent users from understanding the system.

For example, a system should not assume that unrelated languages are equivalent because they share a writing direction, geographic region, script family, or broad cultural category.

Locale equivalence is a review judgment, not an automatic rule.

## Implementation Requirements

### Stable Translation Mechanism

A conforming system must use a stable translation mechanism appropriate to the system being reviewed.

A stable translation mechanism should allow translated content to be maintained, updated, reviewed, and extended without relying on fragile or undocumented behavior.

A stable translation mechanism may include:

* resource files
* translation tables
* locale-aware routing
* compiled language assets
* static localized pages
* runtime language packs
* database-backed translations
* another documented translation structure

A system should avoid hardcoding essential user-facing content in a way that prevents required translation support.

### Preservation of Meaning

A translation preserves meaning when the user can reasonably understand the same essential instruction, label, warning, control, setting, or workflow as users of the source language.

A translation does not need to be word-for-word identical to the source content.

A translation may change word order, grammar, sentence structure, idiom, tone, or phrasing when necessary to communicate the same essential meaning in the target language.

A translation may fail review if it is misleading, incomplete, nonsensical, machine-corrupted, or meaningfully different from the source content in a way that affects essential use.

### Direction-Sensitive Languages

Some required locales commonly use right-to-left text direction.

A conforming system must not prevent essential translated content from being read, understood, selected, or acted upon because the active locale uses a different text direction.

The system should preserve readable ordering, punctuation behavior, and control association for direction-sensitive languages.

Full visual polish, typography quality, accessibility behavior, and layout refinement may require separate review. However, essential translated content must remain meaningfully usable.

### Locale-Sensitive Values

Locale-sensitive values are values whose meaning or readability may vary by language, region, script, or culture.

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

## Verification

### Within Spec

A system is considered within spec when the CatalystUI Team has reviewed the system and found it reasonable to conclude that it satisfies I18NSPEC.

A system may be within spec when:

* every required locale is supported
* more than 75% of essential user-facing content is translated for each required locale
* all critical user-facing content is translated for each required locale
* users can reasonably select the active locale
* fallback behavior does not falsely claim translation coverage
* locale equivalence, if used, is reasonable and documented
* translated content preserves essential meaning

A system may be within spec even if some nonessential content remains untranslated.

A system may be within spec even if translations are not perfect, provided the essential meaning is preserved and the requirements of this specification are satisfied.

### Warnings

A warning may be issued when a system appears to satisfy I18NSPEC but contains concerns that should be documented.

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

### Failures

A failure occurs when a system does not satisfy one or more required conditions of I18NSPEC.

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
