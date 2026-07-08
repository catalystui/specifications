<!-- Цей переклад було створено ChatGPT, і його має переглянути перекладач-людина. -->

<!-- Видаліть ці рядки у pull request після перевірки перекладу. -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified для інтернаціоналізації

Ласкаво просимо до документації CatalystUI Verification для інтернаціоналізації.

**CatalystUI Verified for Internationalization** означає, що система, сервіс, фреймворк, застосунок або implementation були розглянуті CatalystUI Team і визнані такими, що надають достатню багатомовну підтримку для required CatalystUI internationalization language set.

Ця verification не є загальним рейтингом якості перекладу, стилю письма, глибини локалізації або культурної адаптації. Натомість вона визначає, чи надає reviewed system стабільну й практичну основу, щоб користувачі могли отримувати доступ до essential functionality усіма required supported languages.

Простіше кажучи, ця verification запитує, чи можуть користувачі осмислено користуватися essential parts системи required languages, і чи надано їм розумний спосіб вибрати мову, яку вони розуміють.

<a id="purpose"></a>
## Мета

Інтернаціоналізація важлива, бо system не може вважатися broadly accessible, якщо її essential meaning заблоковано за однією мовою.

CatalystUI розроблено навколо clarity, consistency і faithful representation взаємодії людини з компʼютером. Мова є частиною цієї interaction. Якщо користувач не може зрозуміти labels, instructions, warnings, controls, settings або essential content системи, тоді система не змогла комунікувати ясно, навіть якщо underlying functionality технічно працює.

Internationalization Verification існує, щоб визначати системи, які надають достатню translated support для користувачів у межах required CatalystUI language set. Мета не в тому, щоб вимагати ідеального перекладу кожного optional word, hidden developer message або nonessential page. Мета — визначити, чи можуть люди кожною required language зрозуміти й використовувати essential parts системи.

<a id="what-verification-means"></a>
## Що означає Verification

Система стає **CatalystUI Verified for Internationalization**, коли її review виконано за вимогами, наведеними в цьому розділі, і її визнано within spec.

Щоб бути verified, система має надати переклади більш ніж для 75% essential user-facing parts системи кожною required language. Вона також має надати розумний end-user mechanism для зміни active language.

Система не повинна перекладати кожен internal identifier, developer-facing implementation detail, debug string, optional marketing page або nonessential support text. Однак user-facing portions, потрібні для розуміння й роботи з essential system, мають бути доступні кожною required language.

<a id="required-languages"></a>
## Обовʼязкові мови

Поточний CatalystUI internationalization language set було вибрано на основі практичного review мов, які часто потрібні в технологічних контекстах, зокрема з урахуванням global speaker reach, common online usage, multilingual software expectations і broad regional accessibility needs.

Цей language set не призначений представляти кожну мову, кожен діалект або кожен regional variant. Натомість він установлює практичний baseline для систем, які прагнуть broad international usability серед багатьох найпоширеніших technology-facing language groups світу.

Поточний CatalystUI internationalization language set включає такі locales:

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

Система має забезпечити достатню essential translation coverage для кожної зазначеної language group, щоб вважатися within spec.

Однак regional variants можуть розглядатися з розумною гнучкістю, коли відмінності між variant є незначними й не впливають суттєво на здатність користувача зрозуміти або використовувати систему. Наприклад, система все ще може бути eligible for verification, якщо вона надає один сильний англійський переклад, але не перекладає окремо кожен English regional variant, доки essential meaning, navigation, instructions, warnings і controls залишаються зрозумілими для користувачів missing variants.

Ця гнучкість не застосовується, коли missing variant створює meaningful confusion, пропускає regionally important terminology, порушує locale-sensitive behavior або заважає користувачам зрозуміти essential parts системи.

<a id="essential-translation-coverage"></a>
## Покриття essential translation

Для Internationalization Verification **essential translation coverage** означає частини system, які користувачу обґрунтовано потрібні, щоб зрозуміти, навігувати, налаштовувати й використовувати system.

Essential parts можуть включати:

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

Система вважається такою, що виконує translation coverage requirement, коли понад 75% її essential user-facing content доступні кожною required language.

Цей threshold існує тому, що internationalization work може бути великою, тривалою й залежною від контексту. Система все ще може бути within spec, навіть якщо частина nonessential або lower-priority content залишається неперекладеною. Однак essential experience має бути meaningfully available кожною required language.

<a id="language-selection"></a>
## Вибір мови

Verified system має надати розумний спосіб, щоб end-user міг змінити active language.

Language selection mechanism має бути легко знайти, легко зрозуміти, і він має бути доступним без потреби в технічних знаннях. Користувачам не має бути потрібно редагувати configuration files, змінювати source code, встановлювати developer tools або покладатися на undocumented behavior лише для зміни мови.

Під час показу language options system має визначати кожну мову так, щоб це було зрозуміло і користувачам, які говорять цією мовою, і користувачам, які зараз використовують іншу selected language.

Наприклад, language option може відображатися так:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Точне formatting може відрізнятися, але intent має залишатися тим самим: користувачі мають могти впізнати власну мову, за можливості зрозуміти назву мови, яка зараз відображається, і визначити associated locale code.

<a id="what-within-spec-means"></a>
## Що означає “Within Spec”

Коли система вважається **within spec**, це означає, що CatalystUI Team вручну review систему й визнала розумним висновок, що вона задовольняє internationalization requirements, описані цією verification category.

Це не вимагає одного rigid implementation pattern. Система може виконати requirement через resource files, translation tables, locale-aware routing, compiled language assets, database-backed translations, runtime language packs або інший stable mechanism, придатний для system.

Verification стосується практичної здатності користувачів отримувати доступ до essential system required languages, а не того, чи system використовує одну specific translation architecture.

<a id="what-verification-does-not-mean"></a>
## Чого Verification не означає

CatalystUI Verified for Internationalization не гарантує, що кожен переклад є ідеальним, літературним, ідіоматичним, культурно повним або юридично достатнім для кожного region.

Вона також не підтверджує автоматично accessibility, typography, right-to-left layout, locale-specific formatting, currency formatting, date formatting, legal compliance або regional business requirements, якщо ці питання не включені до reviewed internationalization scope.

Система може мати сильне translation coverage і все одно потребувати окремого review для accessibility, localization quality, regional compliance або інших specialized concerns.

<a id="why-this-verification-exists"></a>
## Чому ця Verification існує

User interface корисний лише тоді, коли користувач може зрозуміти, що він повідомляє.

Багато систем заявляють language support, перекладаючи лише невелику частину experience, приховуючи language selection, пропускаючи important messages або залишаючи essential workflows частково неперекладеними. Це створює confusion і заважає користувачам довіряти system.

Internationalization Verification існує, щоб установити чіткіший standard. Вона визначає systems, які роблять серйозні й практичні зусилля для підтримки користувачів у межах required CatalystUI language set і надають розумний спосіб вибрати потрібну мову.

<a id="verification-scope"></a>
## Scope Verification

CatalystUI Verification for Internationalization застосовується до reviewed system, service, framework, application або implementation у тому стані, у якому вони існували на момент issued verification.

Verified system надає достатню essential translation coverage для required languages. Це не гарантує, що кожна future page, feature, release, plugin, extension або third-party integration автоматично within spec.

Окремі products, modules, services, language packs або major revisions можуть вимагати власного review залежно від verification category, яку запитують.

<a id="verification-validity"></a>
## Чинність Verification

CatalystUI Verification застосовується лише до reviewed state системи на момент issued verification.

Система може зберігати verification після later updates, доки вона зберігає verified internationalization foundation. Minor wording changes, added translations і ordinary content updates не invalidates verification автоматично.

Новий review може знадобитися, якщо система видаляє required language support, ламає language selection, суттєво зменшує essential translation coverage або змінює internationalization architecture так, що це впливає на verified behavior.

Інакше кажучи, покращувати translation support зазвичай нормально. Ламання verified multilingual base може вимагати review.

<a id="verified-systems"></a>
## Verified Systems

Відомі systems, verified for internationalization, наведено окремо на відповідній сторінці CatalystUI Verified.
