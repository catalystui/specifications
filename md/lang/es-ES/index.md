<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimine estas líneas en un pull request después de que la traducción haya sido verificada. -->

![CatalystUI Verified for Programming Languages](/images/verification/verified-logo-languages.png)

# CatalystUI Verified para lenguajes de programación

Bienvenido a la documentación de verificación de CatalystUI para lenguajes de programación.

**CatalystUI Verified para lenguajes de programación** indica que un lenguaje de programación ha sido revisado por el equipo de CatalystUI y que se ha determinado que proporciona las representaciones de datos fundamentales y las estructuras relacionales necesarias para expresar sistemas compatibles con CatalystUI.

Esta verificación no es una clasificación general de lenguajes de programación. No decide si un lenguaje es mejor, más rápido, más sencillo, más nuevo, más popular o más agradable que otro. En su lugar, identifica si el lenguaje proporciona una base estable y práctica para las especificaciones requeridas por la verificación de CatalystUI.

En términos más sencillos, esta verificación pregunta si un lenguaje de programación puede representar fielmente los datos básicos y las relaciones de las que depende CatalystUI.

## Propósito

Los lenguajes de programación forman la base representacional bajo toda implementación de CatalystUI. Antes de que un framework, biblioteca, entorno de ejecución, aplicación o servicio pueda seguir el stack de CatalystUI, el lenguaje usado para construirlo debe ser capaz de expresar los conceptos fundamentales de los que depende el modelo.

Para los lenguajes de programación, esto significa principalmente dos cosas:

1. El lenguaje debe ser capaz de representar datos fundamentales.
2. El lenguaje debe ser capaz de representar relaciones fundamentales entre datos.

Estas cuestiones se definen mediante las especificaciones fundamentales de CatalystUI. FDEFSPEC define las representaciones de datos fundamentales esperadas. FRELSPEC define las relaciones fundamentales esperadas entre esas representaciones, incluidas las colecciones, las relaciones de memoria, las operaciones, las relaciones de hilos de ejecución y los compuestos.

Un lenguaje de programación verificado ofrece a los desarrolladores suficiente claridad y control para construir sistemas compatibles con CatalystUI sin depender de soluciones frágiles, confusas o inestables para los conceptos básicos que CatalystUI requiere.

## Qué significa la verificación

Un lenguaje de programación se convierte en **CatalystUI Verified** cuando se revisa frente a las especificaciones enumeradas en esta sección y se determina que está dentro de la especificación.

En la verificación de lenguajes de programación, la revisión se centra en si el lenguaje puede expresar los requisitos fundamentales definidos por las especificaciones aplicables. Esto no significa que el propio lenguaje sea una implementación de CatalystUI. Significa que el lenguaje proporciona una base adecuada desde la cual pueden construirse implementaciones compatibles con CatalystUI.

Un lenguaje no necesita satisfacer estos requisitos de la misma manera que otro. Los distintos lenguajes usan distinta sintaxis, sistemas de tipos, bibliotecas estándar, compiladores, entornos de ejecución y patrones de diseño. La verificación de CatalystUI permite esas diferencias siempre que los conceptos requeridos puedan expresarse de forma clara, fiable y coherente.

## Qué significa “Within Spec”

Cuando un lenguaje de programación se considera **within spec**, significa que el equipo de CatalystUI ha revisado manualmente el lenguaje y ha considerado razonable concluir que el comportamiento requerido descrito por las especificaciones aplicables puede expresarse dentro de ese lenguaje.

Esto no exige un patrón de implementación rígido. Un lenguaje puede satisfacer un requisito mediante primitivos incorporados, funciones de la biblioteca estándar, comportamiento del compilador, comportamiento del entorno de ejecución, garantías documentadas u otro mecanismo estable apropiado para ese lenguaje.

La verificación se ocupa de la capacidad práctica de representar y preservar el significado de la especificación, no de si el lenguaje usa exactamente los mismos nombres, estructuras, sintaxis o diseño interno que el texto de la especificación.

## Por qué existe esta verificación

CatalystUI está diseñado en torno a la claridad, la coherencia y la representación fiel de cómo interactúan los humanos y los ordenadores. Los lenguajes de programación importan porque determinan lo que los desarrolladores pueden expresar de forma realista, con qué seguridad pueden modelarse esos sistemas y con qué claridad pueden construirse implementaciones de nivel superior.

Si un lenguaje no puede proporcionar los conceptos fundamentales requeridos de forma estable, entonces las implementaciones de CatalystUI de nivel superior se vuelven más difíciles de confiar. Los desarrolladores pueden verse empujados hacia abstracciones poco claras, comportamientos impredecibles, dependencias frágiles o reescrituras innecesarias solo para expresar ideas que deberían ser fiables desde el principio.

La verificación de lenguajes de programación existe para identificar qué lenguajes proporcionan una base suficientemente sólida para el trabajo con CatalystUI. Da a desarrolladores, diseñadores de lenguajes y organizaciones una comprensión más clara de si un lenguaje es adecuado para construir sistemas compatibles con CatalystUI.

## Cómo se verifica un lenguaje

Para convertirse en **CatalystUI Verified para lenguajes de programación**, un lenguaje debe revisarse frente a las especificaciones enumeradas en esta sección.

El proceso general es:

1. Se identifican las especificaciones aplicables de CatalystUI.
2. El lenguaje se revisa frente a cada especificación requerida.
3. El equipo de CatalystUI determina si el lenguaje satisface la intención y los requisitos de las especificaciones.
4. Si se determina que el lenguaje está dentro de la especificación, puede concedérsele la verificación de CatalystUI.
5. Una vez verificado, el lenguaje puede aparecer en la página de [Lenguajes verificados](/verified/).

La revisión puede considerar documentación oficial del lenguaje, comportamiento de la biblioteca estándar, comportamiento del compilador, comportamiento del entorno de ejecución, ejemplos de implementación, casos de prueba y otras evidencias necesarias para determinar si el lenguaje cumple los requisitos.

El comportamiento del compilador y del entorno de ejecución puede considerarse durante la revisión cuando ese comportamiento forma parte de cómo se usa el lenguaje común y oficialmente. Sin embargo, verificar un lenguaje de programación no verifica automáticamente todos los compiladores, entornos de ejecución, paquetes, frameworks, bibliotecas, aplicaciones o herramientas del ecosistema de ese lenguaje.

## Especificaciones aplicables

Las especificaciones enumeradas en esta sección definen los requisitos usados para la verificación de lenguajes de programación.

Para los lenguajes de programación, la base activa se centra actualmente en las siguientes categorías de especificación:

* **FDEFSPEC**, que define representaciones de datos fundamentales.
* **FRELSPEC**, que define relaciones fundamentales entre representaciones de datos.

Juntas, estas especificaciones establecen la base mínima requerida para que un lenguaje de programación represente sistemas compatibles con CatalystUI.

Más adelante pueden introducirse especificaciones adicionales para categorías de verificación más especializadas. Esas especificaciones pueden definir requisitos de implementación de nivel superior, plataforma, accesibilidad, internacionalización, framework, servicio o entorno de ejecución. Sin embargo, esas especificaciones posteriores se construyen sobre la base en lugar de reemplazarla.

Un lenguaje de programación se verifica satisfaciendo las especificaciones requeridas para esta categoría. No se espera que satisfaga requisitos específicos de implementación no relacionados salvo que esos requisitos se añadan a la verificación de lenguajes de programación.

## Alcance de la verificación

La verificación de CatalystUI para lenguajes de programación se aplica al lenguaje de programación tal como fue revisado.

Un lenguaje verificado proporciona una base adecuada para el desarrollo compatible con CatalystUI. No garantiza que todo proyecto escrito en ese lenguaje siga CatalystUI correctamente, ni verifica automáticamente el ecosistema que lo rodea.

Herramientas, bibliotecas, frameworks, entornos de ejecución, aplicaciones, servicios o implementaciones independientes pueden requerir su propia revisión según la categoría de verificación solicitada.

Por tanto, la verificación de lenguajes de programación debe entenderse como una comprobación de base. Confirma que el lenguaje puede representar los conceptos requeridos. No confirma que cada uso del lenguaje aplique esos conceptos correctamente.

## Validez de la verificación

La verificación de CatalystUI se aplica solo al estado revisado de un lenguaje de programación en el momento en que se emite la verificación.

Los lenguajes de programación se tratan como un caso especial porque muchos lenguajes conservan la compatibilidad a través de múltiples versiones. Un lenguaje puede conservar su verificación en versiones posteriores siempre que preserve la compatibilidad con versiones anteriores respecto a las funciones, primitivos, representaciones y comportamientos de los que dependía la revisión original.

Las nuevas funciones del lenguaje por sí solas no invalidan la verificación. Una versión futura puede requerir una nueva revisión solo si elimina, rompe o cambia sustancialmente la base verificada.

En otras palabras, ampliar un lenguaje suele estar bien. Romper la base verificada puede requerir revisión.

## Lenguajes verificados

Los lenguajes de programación verificados conocidos se enumeran por separado en la página de [Lenguajes verificados](/verified/).
