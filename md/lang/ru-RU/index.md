<!-- Этот перевод был создан ChatGPT и должен быть проверен человеком-переводчиком. -->

<!-- Удалите эти строки в pull request после проверки перевода. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Добро пожаловать в документацию CatalystUI Verification по доступности.

**CatalystUI Verified for Accessibility** означает, что service, framework, application, library или system был рассмотрен CatalystUI Team и признан разумно пригодным к использованию, когда один из трех основных чувств, участвующих в user-interface interaction, индивидуально недоступен.

Для этой проверки CatalystUI определяет три primary accessibility senses как **зрение**, **звук** и **осязание**. Проверенная system должна сохранять разумный доступ к своей essential functionality, когда любой из этих senses недоступен, опираясь на оставшиеся доступные sensory domains.

Проще говоря, эта verification спрашивает, может ли пользователь по-прежнему осмысленно понимать, перемещаться по системе и использовать essential parts системы, если он не может отдельно полагаться на зрение, звук или осязание.

## Назначение

Доступность важна, потому что user interface не должен полностью зависеть от одной sensory pathway, если то же essential meaning можно разумно передать через другую.

CatalystUI построен вокруг точного движения data между системами и человеческим восприятием. Если важная information только видима, только слышима или доступна только через touch, система может стать непригодной для пользователей, которые не могут полагаться на этот sense. Accessibility Verification существует для выявления systems, которые сохраняют access, позволяя essential information и interaction продолжаться через alternate sensory routes.

Цель состоит не в том, чтобы требовать каждый возможный interaction method, каждую assistive technology или каждое specialized accommodation. Цель — определить, остается ли essential system meaningfully usable, когда зрение, звук или осязание индивидуально недоступны.

## Что означает проверка

System становится **CatalystUI Verified for Accessibility**, когда она рассмотрена по requirements, перечисленным в этой секции, и признана within spec.

Для verification система должна оставаться разумно пригодной к использованию в каждом из следующих случаев:

| Недоступное чувство | Требуемое поведение доступности |
| ------------------- | ----------------------------------------------------------------- |
| Зрение              | Система должна оставаться разумно пригодной к использованию через звук и осязание. |
| Звук                | Система должна оставаться разумно пригодной к использованию через зрение и осязание. |
| Осязание            | Система должна оставаться разумно пригодной к использованию через зрение и звук. |

Система не обязана предоставлять identical experiences по каждому sensory path. Non-visual experience может быть медленнее visual. Sound-free experience может требовать captions, visual indicators или других substitutions. Touch-free experience может требовать alternate controls, voice interaction, keyboard navigation, pointer navigation или других non-touch methods.

Важно, остается ли essential functionality accessible, understandable и operable без требования unavailable sense.

## Essential Functionality

Для Accessibility Verification **essential functionality** означает части системы, которые пользователю разумно нужны, чтобы понимать, навигировать, настраивать и использовать систему.

Essential functionality может включать:

* primary navigation
* core workflows
* required controls
* важные предупреждения
* важные ошибки
* required confirmation messages
* account or session access
* settings and preferences
* language or accessibility configuration
* essential instructions
* user-facing status information
* любое interaction, required for normal use

Система может оставаться within spec, если decorative, redundant, optional или nonessential features не одинаково доступны через каждый sensory path. Однако пользователь все равно должен иметь возможность использовать essential system без блокировки из-за отсутствующего sense.

## Недоступно зрение

Когда зрение недоступно, система должна оставаться разумно пригодной к использованию через звук и осязание.

Это может включать spoken output, screen-reader-compatible structure, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions или другой разумный non-visual method передачи essential information.

Система не должна полагаться исключительно на visual position, color, shape, animation, icons или layout, когда эта information нужна для понимания или использования essential functionality.

## Недоступен звук

Когда звук недоступен, система должна оставаться разумно пригодной к использованию через зрение и осязание.

Это может включать captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback или другой разумный non-auditory method передачи essential information.

Система не должна полагаться исключительно на sound effects, spoken instructions, alerts, alarms, music cues или audio-only prompts, когда эта information нужна для понимания или использования essential functionality.

## Недоступно осязание

Когда осязание недоступно, система должна оставаться разумно пригодной к использованию через зрение и звук.

Это может включать voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation или другой разумный method, не требующий touch-based interaction или tactile perception.

Система не должна полагаться исключительно на touch gestures, haptic feedback, physical texture, vibration, force, pressure или touch-only controls, когда эти interactions нужны для понимания или использования essential functionality.

## Дополнительные сенсорные домены

CatalystUI также признает **вкус** и **запах** как sensory domains. Эти domains могут учитываться при accessibility review, когда system использует их осмысленно.

Вкус и запах являются **inclusive** для verification: они могут усилить или поддержать accessibility review, когда предоставляют meaningful alternate access или дополнительный context.

Вкус и запах в настоящее время не являются **exclusive** для failure: system не проваливает Accessibility Verification только потому, что не предоставляет taste-based или smell-based interaction.

CatalystUI Accessibility Verification прежде всего рассматривает, остается ли system разумно пригодной к использованию, когда зрение, звук или осязание индивидуально недоступны.

## Что означает “Within Spec”

Когда system считается **within spec**, это означает, что CatalystUI Team вручную рассмотрела system и сочла разумным заключить, что она удовлетворяет accessibility requirements, описанным этой verification category.

Это не требует одного жесткого implementation pattern. System может удовлетворять accessibility requirements через native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration или другой stable mechanism, подходящий для system.

Verification касается практической способности users получить access к essential system, когда один primary sense недоступен, а не того, использует ли system конкретную accessibility architecture.

## Чего проверка не означает

CatalystUI Verified for Accessibility не гарантирует, что каждая возможная disability, device, assistive technology, medical condition, legal requirement, regional standard или specialized use case была полностью рассмотрена.

Она также не проверяет автоматически internationalization, translation quality, typography, localization, regional compliance или general design quality, если эти вопросы не включены в reviewed accessibility scope.

System может быть reasonably accessible в рамках модели accessibility CatalystUI и при этом требовать отдельного review для legal compliance, platform certification, specialized assistive technology support или других accessibility standards.

## Почему эта проверка существует

User interface успешен только тогда, когда users действительно могут им пользоваться.

Многие systems относятся к accessibility как к второстепенной мысли, checklist или узкому technical requirement, а не как к fundamental part human-computer interaction. CatalystUI применяет более простой и прямой подход: если system зависит от human perception, она должна сохранять essential meaning, когда одна primary sensory path недоступна.

Accessibility Verification существует, чтобы выявлять systems, которые серьезно относятся к этой ответственности. Она признает systems, которые предоставляют meaningful alternate access, сохраняют essential functionality и не запирают users за одним required sense.

## Область проверки

CatalystUI Verification for Accessibility применяется к reviewed system, service, framework, application, library или implementation в том состоянии, в котором они существовали на момент выдачи verification.

Verified system предоставляет reasonable accessibility для своей essential functionality в reviewed conditions. Это не гарантирует, что каждая будущая page, feature, release, plugin, extension, third-party integration, device или platform-specific version автоматически будет within spec.

Отдельные products, modules, services, major revisions или platform-specific builds могут требовать собственного review в зависимости от requested verification category.

## Действительность проверки

CatalystUI Verification применяется только к reviewed state системы на момент выдачи verification.

System может сохранить verification при последующих updates, пока сохраняет verified accessibility foundation. Minor wording changes, visual refinements, performance improvements и ordinary content updates не аннулируют verification автоматически.

Новый review может потребоваться, если system удаляет alternate access paths, ломает assistive-technology support, существенно меняет essential navigation, удаляет required accessibility settings или меняет interaction behavior способом, который влияет на verified accessibility foundation.

Иными словами, улучшение accessibility обычно допустимо. Нарушение verified access model может требовать review.

## Проверенные системы

Известные systems, verified for accessibility, перечислены отдельно на соответствующей странице CatalystUI Verified.
