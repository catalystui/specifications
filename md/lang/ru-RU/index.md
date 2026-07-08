<!-- Этот перевод был создан ChatGPT и должен быть проверен человеком-переводчиком. -->
<!-- Удалите эти строки в pull request после проверки перевода. -->

# CatalystUI Verified для языков программирования

Добро пожаловать в документацию CatalystUI Verification для языков программирования.

**CatalystUI Verified для языков программирования** означает, что язык программирования был рассмотрен командой CatalystUI и признан обеспечивающим базовые представления данных и реляционные структуры, необходимые для выражения систем, совместимых с CatalystUI.

Эта проверка не является общим рейтингом языков программирования. Она не решает, является ли один язык лучше, быстрее, проще, новее, популярнее или приятнее другого. Вместо этого она определяет, предоставляет ли язык стабильную и практичную основу для спецификаций, требуемых CatalystUI Verification.

Проще говоря, эта проверка отвечает на вопрос, может ли язык программирования достоверно представлять базовые данные и отношения, от которых зависит CatalystUI.

## Назначение

Языки программирования образуют представительную основу под каждой реализацией CatalystUI. Прежде чем фреймворк, библиотека, среда выполнения, приложение или служба смогут следовать стеку CatalystUI, язык, используемый для их создания, должен быть способен выражать фундаментальные понятия, от которых зависит модель.

Для языков программирования это прежде всего означает две вещи:

1. Язык должен быть способен представлять фундаментальные данные.
2. Язык должен быть способен представлять фундаментальные отношения между данными.

Эти вопросы определяются через фундаментальные спецификации CatalystUI. FDEFSPEC определяет ожидаемые фундаментальные представления данных. FRELSPEC определяет ожидаемые фундаментальные отношения между этими представлениями, включая коллекции, отношения памяти, операции, отношения потоков и составные конструкции.

Проверенный язык программирования дает разработчикам достаточно ясности и контроля для создания систем, совместимых с CatalystUI, без опоры на хрупкие, неясные или нестабильные обходные пути для базовых понятий, необходимых CatalystUI.

## Что означает проверка

Язык программирования становится **CatalystUI Verified**, когда он рассматривается по спецификациям, перечисленным в этом разделе, и признается соответствующим спецификации.

Для проверки языков программирования обзор сосредоточен на том, может ли язык выражать фундаментальные требования, определенные применимыми спецификациями. Это не означает, что сам язык является реализацией CatalystUI. Это означает, что язык предоставляет подходящую основу, на которой могут строиться реализации, совместимые с CatalystUI.

Язык не обязан удовлетворять этим требованиям тем же способом, что и другой язык. Разные языки используют разный синтаксис, системы типов, стандартные библиотеки, компиляторы, среды выполнения и шаблоны проектирования. CatalystUI Verification допускает эти различия, пока требуемые понятия можно выражать ясно, надежно и последовательно.

## Что означает «в пределах спецификации»

Когда язык программирования считается **within spec**, это означает, что команда CatalystUI вручную рассмотрела язык и сочла разумным заключить, что требуемое поведение, описанное применимыми спецификациями, может быть выражено в этом языке.

Это не требует одного жесткого шаблона реализации. Язык может удовлетворять требованию через встроенные примитивы, возможности стандартной библиотеки, поведение компилятора, поведение среды выполнения, документированные гарантии или другой стабильный механизм, подходящий для этого языка.

Проверка касается практической способности представлять и сохранять смысл спецификации, а не того, использует ли язык точно такие же имена, структуры, синтаксис или внутренний дизайн, как текст спецификации.

## Зачем существует эта проверка

CatalystUI построен вокруг ясности, последовательности и достоверного представления того, как люди и компьютеры взаимодействуют. Языки программирования важны, потому что они определяют, что разработчики могут реалистично выразить, насколько безопасно эти системы можно моделировать и насколько ясно можно строить реализации более высокого уровня.

Если язык не может стабильно предоставить требуемые фундаментальные понятия, реализации CatalystUI более высокого уровня становится труднее считать надежными. Разработчиков может тянуть к неясным абстракциям, непредсказуемому поведению, хрупким зависимостям или ненужным переписываниям лишь для выражения идей, которые должны быть надежными с самого начала.

Проверка языков программирования существует для определения того, какие языки дают достаточно прочную основу для работы с CatalystUI. Она дает разработчикам, проектировщикам языков и организациям более ясное понимание того, подходит ли язык для создания систем, совместимых с CatalystUI.

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

## Область проверки

CatalystUI Verification for Programming Languages applies to the programming language as reviewed.

A verified language provides a suitable foundation for CatalystUI-compatible development. It does not guarantee that every project written in that language follows CatalystUI correctly, nor does it automatically verify the surrounding ecosystem.

Separate tools, libraries, frameworks, runtimes, applications, services, or implementations may require their own review depending on the verification category being requested.

Programming Language Verification should therefore be understood as a foundation check. It confirms that the language can represent the required concepts. It does not confirm that every use of the language applies those concepts correctly.

## Verification Validity

CatalystUI Verification applies only to the reviewed state of a programming language at the time verification is issued.

Programming languages are treated as a special case because many languages preserve compatibility across multiple versions. A language may retain its verification across later versions so long as it preserves backward compatibility with the features, primitives, representations, and behavior the original review depended on.

New language features alone do not invalidate verification. A future version may require a new review only if it removes, breaks, or substantially changes the verified foundation.

In other words, extending a language is usually fine. Breaking the verified base may require review.

## Проверенные языки

Known verified programming languages are listed separately on the [Verified Languages](/verified/) page.
