<!-- Цей переклад створено ChatGPT, і його має перевірити людина-перекладач. -->

<!-- Видаліть ці рядки в pull request після перевірки перекладу. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Ласкаво просимо до документації CatalystUI Verification щодо accessibility.

**CatalystUI Verified for Accessibility** означає, що service, framework, application, library або system було переглянуто CatalystUI Team і визнано таким, що залишається reasonably usable, коли один із трьох primary senses, залучених до user-interface interaction, окремо недоступний.

Для цієї verification CatalystUI визначає три primary accessibility senses як **зір**, **звук** і **дотик**. Verified system має зберігати reasonable access до своєї essential functionality, коли будь-яке одне з цих чуттів недоступне, спираючись на решту available sensory domains.

Простіше кажучи, ця verification запитує, чи може user і далі meaningful understand, navigate і operate essential parts системи, якщо він окремо не може покладатися на зір, звук або дотик.

## Мета

Accessibility важлива, тому що user interface не має повністю залежати від одного sensory pathway, коли той самий essential meaning можна розумно передати іншим шляхом.

CatalystUI спроєктовано навколо точного руху data між systems і human perception. Якщо важлива інформація лише видима, лише чутна або доступна лише через дотик, system може стати unusable для users, які не можуть покладатися на це чуття. Accessibility Verification існує, щоб визначати systems, які зберігають access, дозволяючи essential information та interaction продовжуватися через alternate sensory routes.

Мета полягає не в тому, щоб вимагати кожен можливий interaction method, кожну assistive technology або кожне specialized accommodation. Мета — визначити, чи essential system залишається meaningfully usable, коли зір, звук або дотик окремо unavailable.

## Що означає Verification

System стає **CatalystUI Verified for Accessibility**, коли її переглянуто відповідно до requirements, перелічених у цьому розділі, і визнано within spec.

Щоб бути verified, system має залишатися reasonably usable у кожному з таких випадків:

| Недоступне чуття | Обов’язкова Accessibility Behavior |
| ---------------- | ---------------------------------- |
| Зір              | System має залишатися reasonably usable через звук і дотик. |
| Звук             | System має залишатися reasonably usable через зір і дотик. |
| Дотик            | System має залишатися reasonably usable через зір і звук. |

System не зобов’язана надавати identical experiences через кожен sensory path. Non-visual experience може бути повільнішим за visual. Sound-free experience може потребувати captions, visual indicators або інших substitutions. Touch-free experience може потребувати alternate controls, voice interaction, keyboard navigation, pointer navigation або інших non-touch methods.

Важливо те, чи essential functionality залишається accessible, understandable і operable без вимоги unavailable sense.

## Essential Functionality

Для Accessibility Verification **essential functionality** означає частини system, які user розумно потребує, щоб understand, navigate, configure і operate system.

Essential functionality може включати:

* primary navigation
* core workflows
* required controls
* important warnings
* important errors
* required confirmation messages
* account or session access
* settings and preferences
* language or accessibility configuration
* essential instructions
* user-facing status information
* будь-яку interaction, required для нормального використання

System може й надалі бути within spec, якщо decorative, redundant, optional або nonessential features не однаково available через кожен sensory path. Однак user все одно має мати змогу використовувати essential system без блокування через missing sense.

## Коли зір недоступний

Коли зір unavailable, system має залишатися reasonably usable через звук і дотик.

Це може включати spoken output, screen-reader-compatible structure, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions або інший reasonable non-visual method передавання essential information.

System не має покладатися виключно на visual position, color, shape, animation, icons або layout, коли ця information required для understanding або operation essential functionality.

## Коли звук недоступний

Коли звук unavailable, system має залишатися reasonably usable через зір і дотик.

Це може включати captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback або інший reasonable non-auditory method передавання essential information.

System не має покладатися виключно на sound effects, spoken instructions, alerts, alarms, music cues або audio-only prompts, коли ця information required для understanding або operation essential functionality.

## Коли дотик недоступний

Коли дотик unavailable, system має залишатися reasonably usable через зір і звук.

Це може включати voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation або інший reasonable method, що не потребує touch-based interaction чи tactile perception.

System не має покладатися виключно на touch gestures, haptic feedback, physical texture, vibration, force, pressure або touch-only controls, коли ці interactions required для understanding або operation essential functionality.

## Додаткові Sensory Domains

CatalystUI також визнає **смак** і **нюх** як sensory domains. Ці domains можуть розглядатися під час accessibility review, коли system використовує їх meaningful.

Смак і нюх є **inclusive** для verification, тобто вони можуть посилювати або підтримувати accessibility review, коли надають meaningful alternate access або додатковий context.

Смак і нюх наразі не є **exclusive** для failure, тобто system не провалює Accessibility Verification лише тому, що не надає taste-based або smell-based interaction.

CatalystUI Accessibility Verification насамперед стосується того, чи system залишається reasonably usable, коли зір, звук або дотик окремо unavailable.

## Що означає “Within Spec”

Коли system вважається **within spec**, це означає, що CatalystUI Team вручну переглянула system і визнала reasonable зробити висновок, що вона задовольняє accessibility requirements, описані цією verification category.

Це не вимагає одного жорсткого implementation pattern. System може задовольняти accessibility requirements через native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration або інший stable mechanism, appropriate to the system.

Verification стосується практичної здатності users отримувати access до essential system, коли один primary sense unavailable, а не того, чи system використовує одну specific accessibility architecture.

## Чого Verification не означає

CatalystUI Verified for Accessibility не гарантує, що кожну можливу disability, device, assistive technology, medical condition, legal requirement, regional standard або specialized use case було повністю reviewed.

Вона також автоматично не verify internationalization, translation quality, typography, localization, regional compliance або general design quality, якщо ці concerns не входять до reviewed accessibility scope.

System може бути reasonably accessible за accessibility model CatalystUI і все одно потребувати separate review для legal compliance, platform certification, specialized assistive technology support або інших accessibility standards.

## Чому ця Verification існує

User interface успішний лише тоді, коли users справді можуть ним користуватися.

Багато systems ставляться до accessibility як до afterthought, checklist або вузького technical requirement, а не як до fundamental частини human-computer interaction. CatalystUI застосовує простіший і пряміший approach: якщо system залежить від human perception, вона має зберігати essential meaning, коли один primary sensory path unavailable.

Accessibility Verification існує, щоб визначати systems, які серйозно ставляться до цієї responsibility. Вона визнає systems, які надають meaningful alternate access, зберігають essential functionality і не замикають users за одним required sense.

## Verification Scope

CatalystUI Verification for Accessibility застосовується до reviewed system, service, framework, application, library або implementation у тому стані, в якому вона існувала на момент видання verification.

Verified system надає reasonable accessibility для своєї essential functionality у reviewed conditions. Це не гарантує, що кожна future page, feature, release, plugin, extension, third-party integration, device або platform-specific version автоматично within spec.

Separate products, modules, services, major revisions або platform-specific builds можуть потребувати власного review залежно від requested verification category.

## Verification Validity

CatalystUI Verification застосовується лише до reviewed state system на момент видання verification.

System може зберігати verification під час later updates, доки вона зберігає verified accessibility foundation. Minor wording changes, visual refinements, performance improvements і ordinary content updates не invalidates verification automatically.

Новий review може бути required, якщо system removes alternate access paths, breaks assistive-technology support, substantially changes essential navigation, removes required accessibility settings або changes interaction behavior у спосіб, що affects verified accessibility foundation.

Іншими словами, improving accessibility зазвичай нормально. Breaking the verified access model може require review.

## Verified Systems

Known systems, verified for accessibility, listed separately on the appropriate CatalystUI Verified page.
