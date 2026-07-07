# CatalystUI Verified for Internationalization

Welcome to the CatalystUI Verification documentation for internationalization.

**CatalystUI Verified for Internationalization** indicates that a system, service, framework, application, or implementation has been reviewed by the CatalystUI Team and found to provide sufficient multilingual support for the required CatalystUI internationalization language set.

This verification is not a general ranking of translation quality, writing style, localization depth, or cultural adaptation. Instead, it identifies whether the reviewed system provides a stable and practical foundation for users to access its essential functionality across the required supported languages.

In simpler terms, this verification asks whether users can meaningfully use the essential parts of a system in the required languages, and whether they are given a reasonable way to choose the language they understand.

## Purpose

Internationalization matters because a system cannot be considered broadly accessible if its essential meaning is locked behind one language.

CatalystUI is designed around clarity, consistency, and the faithful representation of human-computer interaction. Language is part of that interaction. If a user cannot understand the labels, instructions, warnings, controls, settings, or essential content of a system, then the system has failed to communicate clearly, even if the underlying functionality technically works.

Internationalization Verification exists to identify systems that provide enough translated support for users across the required CatalystUI language set. The goal is not to demand perfect translation of every optional word, hidden developer message, or nonessential page. The goal is to determine whether the essential parts of the system can be understood and used by people in each required language.

## What Verification Means

A system becomes **CatalystUI Verified for Internationalization** when it is reviewed against the requirements listed in this section and found to be within spec.

To be verified, a system must provide translations for more than 75% of the essential user-facing parts of the system in each required language. It must also provide a reasonable end-user mechanism for changing the active language.

A system does not need to translate every internal identifier, developer-facing implementation detail, debug string, optional marketing page, or nonessential support text. However, the user-facing portions required to understand and operate the essential system must be available in each required language.

## Required Languages

The current CatalystUI internationalization language set was selected from a practical review of languages commonly needed in technology contexts, including global speaker reach, common online usage, multilingual software expectations, and broad regional accessibility needs.

This language set is not intended to represent every language, every dialect, or every regional variant. Instead, it establishes a practical baseline for systems seeking broad international usability across many of the world’s most common technology-facing language groups.

The current CatalystUI internationalization language set includes the following locales:

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

A system must provide sufficient essential translation coverage for each listed language group to be considered within spec.

However, regional variants may be reviewed with reasonable flexibility when the differences between variants are minor and do not materially affect the user’s ability to understand or operate the system. For example, a system may still be eligible for verification if it provides one strong English translation but does not separately translate every English regional variant, so long as essential meaning, navigation, instructions, warnings, and controls remain clear to users of the missing variants.

This flexibility does not apply when a missing variant would create meaningful confusion, omit regionally important terminology, break locale-sensitive behavior, or prevent users from understanding essential parts of the system.

## Essential Translation Coverage

For Internationalization Verification, **essential translation coverage** refers to the parts of a system that a user reasonably needs in order to understand, navigate, configure, and operate the system.

Essential parts may include:

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

A system is considered to meet the translation coverage requirement when more than 75% of its essential user-facing content is available in each required language.

This threshold exists because internationalization work can be large, ongoing, and context-dependent. A system may still be within spec even if some nonessential or lower-priority content remains untranslated. However, the essential experience must be meaningfully available in every required language.

## Language Selection

A verified system must provide a reasonable way for the end-user to change the active language.

The language selection mechanism should be easy to find, understandable, and available without requiring technical knowledge. Users should not need to edit configuration files, modify source code, install developer tools, or rely on undocumented behavior simply to change the language.

When displaying language options, the system should identify each language in a way that is understandable both to users who speak that language and users who are currently using another selected language.

For example, a language option may be displayed using:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

The exact formatting may vary, but the intent should remain the same: users should be able to recognize their own language, understand the currently displayed language name when possible, and identify the associated locale code.

## What “Within Spec” Means

When a system is considered **within spec**, it means the CatalystUI Team has manually reviewed the system and found it reasonable to conclude that it satisfies the internationalization requirements described by this verification category.

This does not require one rigid implementation pattern. A system may satisfy the requirement through resource files, translation tables, locale-aware routing, compiled language assets, database-backed translations, runtime language packs, or another stable mechanism appropriate to the system.

Verification is concerned with the practical ability of users to access the essential system in the required languages, not whether the system uses one specific translation architecture.

## What Verification Does Not Mean

CatalystUI Verified for Internationalization does not guarantee that every translation is perfect, literary, idiomatic, culturally complete, or legally sufficient for every region.

It also does not automatically verify accessibility, typography, right-to-left layout, locale-specific formatting, currency formatting, date formatting, legal compliance, or regional business requirements unless those concerns are included in the reviewed internationalization scope.

A system may provide strong translation coverage and still require separate review for accessibility, localization quality, regional compliance, or other specialized concerns.

## Why This Verification Exists

A user interface is only useful when the user can understand what it is communicating.

Many systems claim language support while only translating a small portion of the experience, hiding language selection, omitting important messages, or leaving essential workflows partially untranslated. This creates confusion and prevents users from trusting the system.

Internationalization Verification exists to set a clearer standard. It identifies systems that make a serious, practical effort to support users across the required CatalystUI language set and that provide a reasonable way for users to select the language they need.

## Verification Scope

CatalystUI Verification for Internationalization applies to the reviewed system, service, framework, application, or implementation as it existed at the time verification was issued.

A verified system provides sufficient essential translation coverage for the required languages. It does not guarantee that every future page, feature, release, plugin, extension, or third-party integration is automatically within spec.

Separate products, modules, services, language packs, or major revisions may require their own review depending on the verification category being requested.

## Verification Validity

CatalystUI Verification applies only to the reviewed state of the system at the time verification is issued.

A system may retain its verification across later updates so long as it preserves the verified internationalization foundation. Minor wording changes, added translations, and ordinary content updates do not automatically invalidate verification.

A new review may be required if a system removes required language support, breaks language selection, substantially reduces essential translation coverage, or changes its internationalization architecture in a way that affects the verified behavior.

In other words, improving translation support is usually fine. Breaking the verified multilingual base may require review.

## Verified Systems

Known systems verified for internationalization are listed separately on the appropriate CatalystUI Verified page.
