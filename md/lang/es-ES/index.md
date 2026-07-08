<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->

<!-- Elimine estas líneas en una solicitud de incorporación de cambios después de que la traducción haya sido verificada. -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified for Internationalization

Bienvenido a la documentación de verificación de CatalystUI para internacionalización.

**CatalystUI Verified for Internationalization** indica que un sistema, servicio, framework, aplicación o implementación ha sido revisado por el Equipo de CatalystUI y se ha determinado que proporciona compatibilidad multilingüe suficiente para el conjunto de idiomas de internacionalización requerido por CatalystUI.

Esta verificación no es una clasificación general de la calidad de la traducción, el estilo de redacción, la profundidad de localización o la adaptación cultural. En cambio, identifica si el sistema revisado proporciona una base estable y práctica para que los usuarios accedan a su funcionalidad esencial en los idiomas admitidos requeridos.

Dicho de forma más sencilla, esta verificación pregunta si los usuarios pueden utilizar de manera significativa las partes esenciales de un sistema en los idiomas requeridos, y si se les ofrece una forma razonable de elegir el idioma que entienden.

<a id="purpose"></a>
## Propósito

La internacionalización importa porque un sistema no puede considerarse ampliamente accesible si su significado esencial queda encerrado detrás de un único idioma.

CatalystUI está diseñado en torno a la claridad, la consistencia y la representación fiel de la interacción entre humanos y ordenadores. El idioma forma parte de esa interacción. Si un usuario no puede entender las etiquetas, instrucciones, advertencias, controles, ajustes o contenido esencial de un sistema, entonces el sistema no ha comunicado con claridad, incluso si la funcionalidad subyacente técnicamente funciona.

La Verificación de Internacionalización existe para identificar sistemas que proporcionan suficiente soporte traducido para usuarios en todo el conjunto de idiomas requerido por CatalystUI. El objetivo no es exigir una traducción perfecta de cada palabra opcional, mensaje oculto para desarrolladores o página no esencial. El objetivo es determinar si las partes esenciales del sistema pueden ser entendidas y usadas por personas en cada idioma requerido.

<a id="what-verification-means"></a>
## Qué significa la verificación

Un sistema se convierte en **CatalystUI Verified for Internationalization** cuando se revisa frente a los requisitos indicados en esta sección y se determina que está dentro de la especificación.

Para ser verificado, un sistema debe proporcionar traducciones para más del 75 % de las partes esenciales orientadas al usuario del sistema en cada idioma requerido. También debe proporcionar un mecanismo razonable para que el usuario final cambie el idioma activo.

Un sistema no necesita traducir cada identificador interno, detalle de implementación orientado a desarrolladores, cadena de depuración, página de marketing opcional o texto de soporte no esencial. Sin embargo, las partes orientadas al usuario necesarias para entender y operar el sistema esencial deben estar disponibles en cada idioma requerido.

<a id="required-languages"></a>
## Idiomas requeridos

El conjunto actual de idiomas de internacionalización de CatalystUI se seleccionó a partir de una revisión práctica de los idiomas que suelen necesitarse en contextos tecnológicos, incluyendo el alcance global de hablantes, el uso común en línea, las expectativas de software multilingüe y las necesidades amplias de accesibilidad regional.

Este conjunto de idiomas no pretende representar todos los idiomas, dialectos o variantes regionales. En cambio, establece una base práctica para sistemas que buscan una amplia usabilidad internacional entre muchos de los grupos lingüísticos orientados a la tecnología más comunes del mundo.

El conjunto actual de idiomas de internacionalización de CatalystUI incluye las siguientes locales:

| Locale    | Idioma                   |
| --------- | ------------------------ |
| `ar-SA`   | Árabe (Arabia Saudí)     |
| `bn-BD`   | Bengalí (Bangladés)      |
| `de-DE`   | Alemán (Alemania)        |
| `en-GB`   | Inglés (Reino Unido)     |
| `en-IN`   | Inglés (India)           |
| `en-US`   | Inglés (Estados Unidos)  |
| `es-ES`   | Español (España)         |
| `es-MX`   | Español (México)         |
| `fa-IR`   | Persa (Irán)             |
| `fr-FR`   | Francés (Francia)        |
| `hi-IN`   | Hindi (India)            |
| `id-ID`   | Indonesio (Indonesia)    |
| `it-IT`   | Italiano (Italia)        |
| `ja-JP`   | Japonés (Japón)          |
| `ko-KR`   | Coreano (Corea del Sur)  |
| `nl-NL`   | Neerlandés (Países Bajos) |
| `pl-PL`   | Polaco (Polonia)         |
| `pt-BR`   | Portugués (Brasil)       |
| `ru-RU`   | Ruso (Rusia)             |
| `tl-PH`   | Tagalo (Filipinas)       |
| `tr-TR`   | Turco (Turquía)          |
| `uk-UA`   | Ucraniano (Ucrania)      |
| `ur-PK`   | Urdu (Pakistán)          |
| `vi-VN`   | Vietnamita (Vietnam)     |
| `zh-CN`   | Chino (China)            |
| `zh-Hans` | Chino (simplificado)     |

Un sistema debe proporcionar cobertura de traducción esencial suficiente para cada grupo lingüístico enumerado a fin de considerarse dentro de la especificación.

Sin embargo, las variantes regionales pueden revisarse con flexibilidad razonable cuando las diferencias entre variantes son menores y no afectan de forma material a la capacidad del usuario para entender u operar el sistema. Por ejemplo, un sistema aún puede ser elegible para verificación si proporciona una traducción sólida al inglés pero no traduce por separado cada variante regional del inglés, siempre que el significado esencial, la navegación, las instrucciones, las advertencias y los controles sigan siendo claros para los usuarios de las variantes ausentes.

Esta flexibilidad no se aplica cuando una variante ausente crearía confusión significativa, omitiría terminología importante a nivel regional, rompería un comportamiento sensible a la locale o impediría que los usuarios entendieran partes esenciales del sistema.

<a id="essential-translation-coverage"></a>
## Cobertura de traducción esencial

Para la Verificación de Internacionalización, **cobertura de traducción esencial** se refiere a las partes de un sistema que un usuario necesita razonablemente para entender, navegar, configurar y operar el sistema.

Las partes esenciales pueden incluir:

* navegación principal
* pantallas y vistas principales
* ajustes y preferencias
* etiquetas orientadas al usuario
* controles orientados al usuario
* instrucciones requeridas
* advertencias importantes
* errores importantes
* indicaciones esenciales
* mensajes de confirmación requeridos
* controles de selección de idioma
* flujos de trabajo principales necesarios para el uso normal

Se considera que un sistema cumple el requisito de cobertura de traducción cuando más del 75 % de su contenido esencial orientado al usuario está disponible en cada idioma requerido.

Este umbral existe porque el trabajo de internacionalización puede ser amplio, continuo y dependiente del contexto. Un sistema aún puede estar dentro de la especificación aunque parte del contenido no esencial o de menor prioridad siga sin traducirse. Sin embargo, la experiencia esencial debe estar disponible de manera significativa en cada idioma requerido.

<a id="language-selection"></a>
## Selección de idioma

Un sistema verificado debe proporcionar una forma razonable para que el usuario final cambie el idioma activo.

El mecanismo de selección de idioma debe ser fácil de encontrar, comprensible y estar disponible sin requerir conocimientos técnicos. Los usuarios no deberían necesitar editar archivos de configuración, modificar código fuente, instalar herramientas de desarrollo ni depender de comportamientos no documentados solo para cambiar el idioma.

Al mostrar opciones de idioma, el sistema debe identificar cada idioma de una forma comprensible tanto para los usuarios que hablan ese idioma como para los usuarios que actualmente están usando otro idioma seleccionado.

Por ejemplo, una opción de idioma puede mostrarse usando:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

El formato exacto puede variar, pero la intención debe seguir siendo la misma: los usuarios deben poder reconocer su propio idioma, entender cuando sea posible el nombre del idioma mostrado actualmente e identificar el código de locale asociado.

<a id="what-within-spec-means"></a>
## Qué significa “Within Spec”

Cuando un sistema se considera **within spec**, significa que el Equipo de CatalystUI ha revisado manualmente el sistema y ha considerado razonable concluir que satisface los requisitos de internacionalización descritos por esta categoría de verificación.

Esto no exige un único patrón rígido de implementación. Un sistema puede satisfacer el requisito mediante archivos de recursos, tablas de traducción, enrutamiento consciente de la locale, recursos de idioma compilados, traducciones respaldadas por base de datos, paquetes de idioma en tiempo de ejecución u otro mecanismo estable apropiado para el sistema.

La verificación se ocupa de la capacidad práctica de los usuarios para acceder al sistema esencial en los idiomas requeridos, no de si el sistema usa una arquitectura de traducción específica.

<a id="what-verification-does-not-mean"></a>
## Qué no significa la verificación

CatalystUI Verified for Internationalization no garantiza que cada traducción sea perfecta, literaria, idiomática, culturalmente completa o legalmente suficiente para cada región.

Tampoco verifica automáticamente la accesibilidad, la tipografía, el diseño de derecha a izquierda, el formato sensible a la locale, el formato de moneda, el formato de fechas, el cumplimiento legal o los requisitos empresariales regionales, salvo que esas preocupaciones estén incluidas en el alcance de internacionalización revisado.

Un sistema puede proporcionar una sólida cobertura de traducción y aun así requerir una revisión separada de accesibilidad, calidad de localización, cumplimiento regional u otras preocupaciones especializadas.

<a id="why-this-verification-exists"></a>
## Por qué existe esta verificación

Una interfaz de usuario solo es útil cuando el usuario puede entender lo que comunica.

Muchos sistemas afirman tener soporte de idiomas mientras solo traducen una pequeña parte de la experiencia, ocultan la selección de idioma, omiten mensajes importantes o dejan flujos de trabajo esenciales parcialmente sin traducir. Esto crea confusión e impide que los usuarios confíen en el sistema.

La Verificación de Internacionalización existe para establecer un estándar más claro. Identifica sistemas que hacen un esfuerzo serio y práctico para apoyar a los usuarios en todo el conjunto de idiomas requerido por CatalystUI y que proporcionan una forma razonable para que los usuarios seleccionen el idioma que necesitan.

<a id="verification-scope"></a>
## Alcance de la verificación

CatalystUI Verification for Internationalization se aplica al sistema, servicio, framework, aplicación o implementación revisado tal como existía en el momento en que se emitió la verificación.

Un sistema verificado proporciona cobertura de traducción esencial suficiente para los idiomas requeridos. No garantiza que cada página, función, versión, plugin, extensión o integración de terceros futura esté automáticamente dentro de la especificación.

Los productos, módulos, servicios, paquetes de idioma o revisiones importantes separados pueden requerir su propia revisión según la categoría de verificación solicitada.

<a id="verification-validity"></a>
## Validez de la verificación

La Verificación de CatalystUI se aplica solo al estado revisado del sistema en el momento en que se emite la verificación.

Un sistema puede conservar su verificación en actualizaciones posteriores siempre que preserve la base de internacionalización verificada. Los cambios menores de redacción, las traducciones añadidas y las actualizaciones ordinarias de contenido no invalidan automáticamente la verificación.

Puede requerirse una nueva revisión si un sistema elimina soporte para idiomas requeridos, rompe la selección de idioma, reduce sustancialmente la cobertura de traducción esencial o cambia su arquitectura de internacionalización de una forma que afecte al comportamiento verificado.

En otras palabras, mejorar el soporte de traducción suele estar bien. Romper la base multilingüe verificada puede requerir revisión.

<a id="verified-systems"></a>
## Sistemas verificados

Los sistemas conocidos verificados para internacionalización se enumeran por separado en la página correspondiente de CatalystUI Verified.
