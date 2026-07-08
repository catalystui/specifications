<!-- Цей переклад було створено ChatGPT, і його має перевірити людина-перекладач. -->
<!-- Видаліть ці рядки в pull request після перевірки перекладу. -->

# CatalystUI Verified для мов програмування

Ласкаво просимо до документації CatalystUI Verification для мов програмування.

**CatalystUI Verified для мов програмування** означає, що мову програмування було розглянуто командою CatalystUI і визнано такою, що надає фундаментальні представлення даних та реляційні структури, необхідні для вираження систем, сумісних із CatalystUI.

Ця верифікація не є загальним рейтингом мов програмування. Вона не визначає, чи є одна мова кращою, швидшою, простішою, новішою, популярнішою або приємнішою за іншу. Натомість вона визначає, чи надає мова стабільну й практичну основу для специфікацій, потрібних CatalystUI Verification.

Простіше кажучи, ця верифікація ставить питання, чи може мова програмування достовірно представляти базові дані та зв'язки, від яких залежить CatalystUI.

## Призначення

Мови програмування формують представницьку основу під кожною реалізацією CatalystUI. Перш ніж framework, бібліотека, runtime, застосунок або сервіс зможе слідувати CatalystUI Stack, мова, використана для його створення, має бути здатною виражати фундаментальні поняття, від яких залежить модель.

Для мов програмування це насамперед означає дві речі:

1. Мова має бути здатною представляти фундаментальні дані.
2. Мова має бути здатною представляти фундаментальні зв'язки між даними.

Ці питання визначаються через фундаментальні специфікації CatalystUI. FDEFSPEC визначає очікувані фундаментальні представлення даних. FRELSPEC визначає очікувані фундаментальні зв'язки між цими представленнями, включно з колекціями, зв'язками пам'яті, операціями, зв'язками потоків і композитами.

Верифікована мова програмування дає розробникам достатньо ясності й контролю, щоб будувати системи, сумісні з CatalystUI, не покладаючись на крихкі, неясні або нестабільні обхідні рішення для базових понять, яких потребує CatalystUI.

## Що означає верифікація

Мова програмування стає **CatalystUI Verified**, коли її розглянуто відповідно до специфікацій, перелічених у цьому розділі, і визнано within spec.

Для Programming Language Verification розгляд зосереджений на тому, чи може мова виразити фундаментальні вимоги, визначені застосовними специфікаціями. Це не означає, що сама мова є реалізацією CatalystUI. Це означає, що мова надає придатну основу, на якій можуть будуватися реалізації, сумісні з CatalystUI.

Мові не потрібно задовольняти ці вимоги так само, як іншій мові. Різні мови використовують різний синтаксис, системи типів, стандартні бібліотеки, компілятори, runtime-и та шаблони проєктування. CatalystUI Verification допускає ці відмінності, якщо потрібні поняття можна виразити чітко, надійно й послідовно.

## Що означає “Within Spec”

Коли мову програмування вважають **within spec**, це означає, що команда CatalystUI вручну розглянула мову й дійшла обґрунтованого висновку, що потрібну поведінку, описану застосовними специфікаціями, можна виразити в цій мові.

Це не вимагає одного жорсткого шаблону реалізації. Мова може задовольнити вимогу через вбудовані примітиви, можливості стандартної бібліотеки, поведінку компілятора, поведінку runtime, задокументовані гарантії або інший стабільний механізм, доречний для цієї мови.

Верифікація стосується практичної здатності представляти й зберігати зміст специфікації, а не того, чи використовує мова ті самі назви, структури, синтаксис або внутрішній дизайн, що й текст специфікації.

## Чому ця верифікація існує

CatalystUI спроєктовано навколо ясності, послідовності та достовірного представлення того, як люди й комп'ютери взаємодіють. Мови програмування важливі, бо вони визначають, що розробники можуть реально виразити, наскільки безпечно ці системи можна моделювати та наскільки чітко можна будувати реалізації вищого рівня.

Якщо мова не може стабільно надати потрібні фундаментальні поняття, реалізаціям CatalystUI вищого рівня стає важче довіряти. Розробників може підштовхувати до неясних абстракцій, непередбачуваної поведінки, крихких залежностей або непотрібного переписування лише для того, щоб виразити ідеї, які мали б бути надійними від початку.

Programming Language Verification існує, щоб визначити, які мови надають достатньо міцну основу для роботи CatalystUI. Вона дає розробникам, проєктувальникам мов і організаціям чіткіше розуміння того, чи придатна мова для побудови систем, сумісних із CatalystUI.

## How a Language Becomes Verified

To become **CatalystUI Verified for Programming Languages**, a language must be reviewed against the specifications listed in this section.

The general process is:

1. The applicable CatalystUI specifications are identified.
2. The language is reviewed against each required specification.
3. The CatalystUI Team determines whether the language satisfies the intent and requirements of the specifications.
4. If the language is found to be within spec, it may be granted CatalystUI Verification.
5. Once verified, the language may be listed on the [Verified Languages](/verified/) page.

The review may consider official language documentation, standard library behavior, compiler behavior, runtime behavior, implementation examples, test cases, and other evidence needed to determine whether the language meets the requirements.

Compiler and runtime behavior may be considered during review when that behavior is part of how the language is commonly and officially used. However, verifying a programming language does not automatically verify every compiler, runtime, package, framework, library, application, or tool in that language’s ecosystem.

## Applicable Specifications

The specifications listed in this section define the requirements used for Programming Language Verification.

For programming languages, the active foundation is currently centered on the following specification categories:

* **FDEFSPEC**, which defines foundational data representations.
* **FRELSPEC**, which defines foundational relations between data representations.

Together, these specifications establish the minimum foundation required for a programming language to represent CatalystUI-compatible systems.

Additional specifications may be introduced later for more specialized verification categories. Those specifications may define higher-level implementation, platform, accessibility, internationalization, framework, service, or runtime requirements. However, those later specifications build on the foundation rather than replacing it.

A programming language becomes verified by satisfying the required specifications for this category. It is not expected to satisfy unrelated implementation-specific requirements unless those requirements are added to Programming Language Verification.

## Обсяг верифікації

CatalystUI Verification for Programming Languages applies to the programming language as reviewed.

A verified language provides a suitable foundation for CatalystUI-compatible development. It does not guarantee that every project written in that language follows CatalystUI correctly, nor does it automatically verify the surrounding ecosystem.

Separate tools, libraries, frameworks, runtimes, applications, services, or implementations may require their own review depending on the verification category being requested.

Programming Language Verification should therefore be understood as a foundation check. It confirms that the language can represent the required concepts. It does not confirm that every use of the language applies those concepts correctly.

## Verification Validity

CatalystUI Verification applies only to the reviewed state of a programming language at the time verification is issued.

Programming languages are treated as a special case because many languages preserve compatibility across multiple versions. A language may retain its verification across later versions so long as it preserves backward compatibility with the features, primitives, representations, and behavior the original review depended on.

New language features alone do not invalidate verification. A future version may require a new review only if it removes, breaks, or substantially changes the verified foundation.

In other words, extending a language is usually fine. Breaking the verified base may require review.

## Верифіковані мови

Known verified programming languages are listed separately on the [Verified Languages](/verified/) page.
