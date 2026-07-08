<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->

<!-- Elimine estas líneas en una solicitud de incorporación de cambios después de que la traducción haya sido verificada. -->

# I18NSPEC

<br/>

> **Especificación de Internacionalización**<br/>
> Revisión 1<br/>
> 8 de julio de 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Las definiciones, requisitos y conceptos presentados aquí describen soporte práctico de internacionalización y pueden reexpresarse libremente.

<a id="introduction"></a>
## Introducción

La **Especificación de Internacionalización (I18NSPEC)** establece los conceptos, la terminología y los requisitos principales utilizados para evaluar el soporte multilingüe dentro del ecosistema CatalystUI. Su propósito es proporcionar un estándar claro para determinar si un sistema, servicio, framework, aplicación o implementación ofrece suficiente soporte de idiomas para considerarse dentro de la especificación.

La internacionalización importa porque una interfaz de usuario no puede comunicar con claridad si su significado esencial está disponible en un solo idioma. Un sistema puede ser técnicamente funcional, pero si los usuarios no pueden entender sus etiquetas, instrucciones, controles, ajustes, advertencias, errores o flujos de trabajo principales, entonces el sistema no ha proporcionado una interfaz significativa para esos usuarios.

Esta especificación no intenta medir la calidad perfecta de la traducción, el estilo literario, la adaptación cultural, el cumplimiento legal o la localización regional completa. En cambio, define la base multilingüe mínima necesaria para que los usuarios puedan acceder y operar de manera significativa las partes esenciales de un sistema en todo el conjunto de locales requerido por CatalystUI.

En términos más sencillos, I18NSPEC plantea tres preguntas principales:

1. ¿Pueden los usuarios acceder a las partes esenciales del sistema en cada idioma requerido?
2. ¿Pueden los usuarios seleccionar razonablemente el idioma que entienden?
3. ¿Preserva el sistema suficiente significado entre idiomas para seguir siendo utilizable?

> [!IMPORTANT]
>
> I18NSPEC define requisitos de internacionalización para verificación. No es una especificación separada para cada idioma. Cada locale requerida se comprueba contra la misma especificación.

<a id="table-of-contents"></a>
## Tabla de contenidos

* [I18NSPEC](#i18nspec)

  * [Introducción](#introduction)
  * [Tabla de contenidos](#table-of-contents)
  * [Conformidad](#conformance)
  * [Conjunto de locales requerido](#required-locale-set)
  * [Contenido orientado al usuario](#user-facing-content)

    * [Contenido orientado al usuario](#user-facing-content-1)
    * [Contenido esencial orientado al usuario](#essential-user-facing-content)
    * [Contenido crítico orientado al usuario](#critical-user-facing-content)
    * [Contenido no esencial](#nonessential-content)
  * [Cobertura de traducción](#translation-coverage)

    * [Cobertura de traducción esencial](#essential-translation-coverage)
    * [Requisito de cobertura](#coverage-requirement)
    * [Requisito de contenido crítico](#critical-content-requirement)
  * [Selección de idioma](#language-selection)

    * [Locale activa](#active-locale)
    * [Locale predeterminada](#default-locale)
    * [Mecanismo de selección de idioma](#language-selection-mechanism)
    * [Etiquetas de opciones de idioma](#language-option-labels)
  * [Fallbacks y equivalencia de locales](#fallbacks-and-locale-equivalence)

    * [Locale de fallback](#fallback-locale)
    * [Comportamiento de fallback](#fallback-behavior)
    * [Equivalencia de locales](#locale-equivalence)
  * [Requisitos de implementación](#implementation-requirements)

    * [Mecanismo de traducción estable](#stable-translation-mechanism)
    * [Preservación del significado](#preservation-of-meaning)
    * [Idiomas sensibles a la dirección](#direction-sensitive-languages)
    * [Valores sensibles a la locale](#locale-sensitive-values)
  * [Verificación](#verification)

    * [Dentro de la especificación](#within-spec)
    * [Advertencias](#warnings)
    * [Fallos](#failures)
    * [Validez de la verificación](#verification-validity)

<a id="conformance"></a>
## Conformidad

Un sistema se considera conforme con I18NSPEC cuando satisface los requisitos definidos por este documento para cada locale del conjunto de locales requerido.

Un sistema conforme debe:

1. Admitir cada locale del conjunto de locales requerido.
2. Proporcionar contenido traducido para más del 75 % del contenido esencial orientado al usuario en cada locale requerida.
3. Proporcionar contenido traducido para todo el contenido crítico orientado al usuario en cada locale requerida.
4. Proporcionar un mecanismo razonable para que el usuario final seleccione la locale activa.
5. Usar un mecanismo de traducción estable apropiado para el sistema.
6. Preservar el significado esencial del contenido traducido orientado al usuario.
7. Evitar depender de contenido de fallback para afirmar cobertura de traducción, salvo cuando se acepte la equivalencia de locales durante la revisión.

Un sistema no necesita usar un patrón de implementación específico para cumplir esta especificación. Puede usar archivos de recursos, tablas de traducción, enrutamiento consciente de la locale, recursos de idioma compilados, páginas localizadas estáticas, paquetes de idioma en tiempo de ejecución, traducciones respaldadas por base de datos u otro mecanismo estable apropiado para el sistema.

La verificación se ocupa del acceso práctico del usuario y del significado esencial, no de una arquitectura técnica rígida.

<a id="required-locale-set"></a>
## Conjunto de locales requerido

El conjunto de locales requerido define los idiomas y variantes regionales que deben revisarse para la Verificación de Internacionalización de CatalystUI.

El conjunto actual de locales requeridas incluye las siguientes locales:

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

Un sistema debe proporcionar soporte de traducción esencial suficiente para cada locale enumerada a fin de considerarse dentro de la especificación.

El conjunto de locales requerido no pretende representar todos los idiomas, dialectos, regiones o escrituras. En cambio, establece una base práctica para una amplia usabilidad internacional en muchos grupos lingüísticos comunes orientados a la tecnología.

<a id="user-facing-content"></a>
## Contenido orientado al usuario

<a id="user-facing-content-1"></a>
### Contenido orientado al usuario

El contenido orientado al usuario es cualquier contenido destinado a ser percibido, leído, oído, seleccionado, entendido o utilizado por un usuario final.

El contenido orientado al usuario puede incluir:

* navegación
* etiquetas
* botones
* menús
* controles
* encabezados
* diálogos
* ajustes
* instrucciones
* indicaciones
* advertencias
* errores
* confirmaciones
* mensajes de estado
* texto de incorporación inicial
* texto de ayuda requerido
* controles de selección de idioma
* contenido de flujos de trabajo principales

El contenido orientado al usuario no necesita ser visual. También puede incluir contenido auditivo, táctil, simbólico o multisensorial cuando ese contenido comunica significado al usuario.

<a id="essential-user-facing-content"></a>
### Contenido esencial orientado al usuario

El contenido esencial orientado al usuario es contenido orientado al usuario que una persona necesita razonablemente para entender, navegar, configurar u operar el comportamiento esencial de un sistema.

El contenido esencial orientado al usuario puede incluir:

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

Un sistema no necesita traducir cada página opcional, mensaje oculto, etiqueta interna o texto no esencial para satisfacer I18NSPEC. Sin embargo, el contenido requerido para el uso esencial ordinario debe traducirse de acuerdo con los requisitos de esta especificación.

<a id="critical-user-facing-content"></a>
### Contenido crítico orientado al usuario

El contenido crítico orientado al usuario es contenido esencial orientado al usuario donde un malentendido puede impedir el uso significativo, crear un error grave o hacer que el usuario tome una decisión importante sin entender la consecuencia.

El contenido crítico orientado al usuario puede incluir:

* controles de selección de idioma
* advertencias de acciones destructivas
* advertencias de eliminación de cuenta
* confirmaciones de pago
* confirmaciones de compra
* opciones de privacidad
* advertencias de seguridad
* solicitudes de consentimiento
* instrucciones de seguridad requeridas
* instrucciones de configuración requeridas
* mensajes de error requeridos
* navegación principal requerida para llegar a los ajustes de idioma

El contenido crítico orientado al usuario debe traducirse para cada locale requerida.

El umbral del 75 % de cobertura de traducción esencial no debe usarse para dejar sin traducir contenido crítico.

<a id="nonessential-content"></a>
### Contenido no esencial

El contenido no esencial es contenido que no se requiere razonablemente para que un usuario entienda, navegue, configure u opere el comportamiento esencial de un sistema.

El contenido no esencial puede incluir:

* identificadores internos
* nombres de código fuente
* cadenas solo de depuración
* detalles de implementación orientados a desarrolladores
* texto de diagnóstico oculto
* páginas opcionales de marketing
* páginas opcionales de soporte
* texto legal o empresarial no esencial fuera del alcance revisado
* contenido de terceros no controlado por el sistema revisado

El contenido no esencial puede traducirse, pero no es requerido para la conformidad con I18NSPEC salvo que llegue a ser necesario para la comprensión u operación esencial por parte del usuario.

<a id="translation-coverage"></a>
## Cobertura de traducción

<a id="essential-translation-coverage"></a>
### Cobertura de traducción esencial

La cobertura de traducción esencial es la cantidad de contenido esencial orientado al usuario que se ha traducido para una locale específica.

La cobertura debe evaluarse por unidades significativas de contenido orientado al usuario, no por tamaño de archivo, número de bytes, número de líneas, tamaño del repositorio o número de páginas.

Por ejemplo, un botón sin traducir que controla una acción esencial puede importar más que un gran párrafo opcional sin traducir que no afecta al uso ordinario.

La cobertura de traducción debe juzgarse según si el usuario puede entender y operar de manera significativa el sistema esencial en la locale revisada.

<a id="coverage-requirement"></a>
### Requisito de cobertura

Un sistema satisface el requisito de cobertura de traducción para una locale cuando más del 75 % del contenido esencial orientado al usuario está traducido para esa locale.

Un sistema satisface el requisito de cobertura de I18NSPEC cuando cumple este umbral para cada locale del conjunto de locales requerido.

En una revisión práctica, esto puede representarse así:

| Locale  | Cobertura de traducción esencial | Resultado |
| ------- | -------------------------------- | --------- |
| `en-US` | 100%                             | Aprobado  |
| `es-ES` | 94%                              | Aprobado  |
| `ar-SA` | 78%                              | Aprobado  |
| `ja-JP` | 61%                              | No aprobado |

Una locale con una cobertura del 75 % o inferior no satisface el requisito de cobertura.

Una locale con más del 75 % de cobertura aún puede fallar si el contenido crítico orientado al usuario está sin traducir.

<a id="critical-content-requirement"></a>
### Requisito de contenido crítico

Todo el contenido crítico orientado al usuario debe traducirse para cada locale requerida.

Un sistema puede fallar I18NSPEC incluso cuando satisface el umbral general de cobertura si uno o más elementos de contenido crítico orientado al usuario faltan, no están traducidos, son engañosos o no son significativamente comprensibles.

Por ejemplo, un sistema no debe considerarse dentro de la especificación si la interfaz general está traducida pero la advertencia de eliminación de cuenta, la confirmación de compra, la advertencia de seguridad o el selector de idioma permanecen sin traducir.

<a id="language-selection"></a>
## Selección de idioma

<a id="active-locale"></a>
### Locale activa

La locale activa es la locale seleccionada actualmente para la experiencia del usuario.

La locale activa determina qué contenido traducido debe mostrarse, proporcionarse o comunicarse de otro modo al usuario.

<a id="default-locale"></a>
### Locale predeterminada

La locale predeterminada es la locale usada cuando el usuario no ha seleccionado una locale activa o cuando no hay ninguna preferencia de usuario disponible.

Un sistema debe definir una locale predeterminada.

La locale predeterminada debe estar documentada o ser razonablemente deducible por el revisor.

<a id="language-selection-mechanism"></a>
### Mecanismo de selección de idioma

Un sistema conforme debe proporcionar una forma razonable para que el usuario final cambie la locale activa.

El mecanismo de selección de idioma debe estar disponible sin requerir que el usuario:

* modifique código fuente
* use herramientas de desarrollo
* edite archivos de configuración no documentados
* instale parches no oficiales
* dependa de comportamiento oculto
* contacte con soporte para cambios ordinarios de idioma

Un mecanismo de selección de idioma puede proporcionarse mediante:

* ajustes de la aplicación
* preferencias de la cuenta
* un selector de idioma
* una indicación de inicio
* ajustes del navegador
* ajustes del sistema operativo
* ajustes del dispositivo
* otro mecanismo apropiado accesible para el usuario final

El mecanismo no necesita seguir un patrón de diseño específico. Debe permitir razonablemente que el usuario seleccione un idioma admitido.

<a id="language-option-labels"></a>
### Etiquetas de opciones de idioma

Al mostrar opciones de idioma, un sistema debe identificar cada idioma de una forma que sea comprensible para los usuarios que hablan ese idioma.

Una opción de idioma puede incluir:

* el nombre del idioma en ese idioma
* el nombre del idioma en el idioma actualmente activo
* el código de locale
* una etiqueta regional
* una etiqueta de escritura

Por ejemplo:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

El formato exacto puede variar.

La intención es que los usuarios puedan reconocer su propio idioma, entender cuando sea posible el nombre del idioma mostrado actualmente e identificar el código de locale asociado.

<a id="fallbacks-and-locale-equivalence"></a>
## Fallbacks y equivalencia de locales

<a id="fallback-locale"></a>
### Locale de fallback

Una locale de fallback es una locale usada cuando el contenido traducido no está disponible para la locale activa.

Las locales de fallback pueden ayudar a preservar la usabilidad, pero el contenido de fallback no se considera automáticamente contenido traducido para la locale activa.

Por ejemplo, si un sistema está configurado en `es-MX` pero muestra texto `en-US` porque falta la traducción al español, ese texto en inglés puede ser útil como fallback, pero no debe contarse como cobertura de traducción al español.

<a id="fallback-behavior"></a>
### Comportamiento de fallback

Un sistema conforme puede usar comportamiento de fallback cuando el contenido localizado no está disponible.

El comportamiento de fallback debe evitar salidas rotas, vacías o engañosas.

El comportamiento de fallback no debe usarse para afirmar falsamente cobertura de traducción para una locale requerida.

Un sistema puede recibir una advertencia o un fallo si el comportamiento de fallback es excesivo, confuso, no documentado o hace que contenido esencial aparezca sin traducir en una locale requerida.

<a id="locale-equivalence"></a>
### Equivalencia de locales

La equivalencia de locales ocurre cuando una traducción puede servir razonablemente para más de una locale sin impedir la comprensión u operación esencial.

Por ejemplo, un sistema puede usar una traducción al inglés para `en-US`, `en-GB` y `en-IN` si el significado esencial sigue siendo claro para los usuarios de cada locale.

La equivalencia de locales puede aceptarse durante la revisión cuando las diferencias regionales son menores y no afectan de forma material a la usabilidad esencial.

La equivalencia de locales no debe usarse cuando una locale ausente crearía confusión significativa, omitiría terminología regional importante, rompería comportamiento esencial o impediría que los usuarios entendieran el sistema.

Por ejemplo, un sistema no debe asumir que idiomas no relacionados son equivalentes porque comparten una dirección de escritura, región geográfica, familia de escritura o categoría cultural amplia.

La equivalencia de locales es un juicio de revisión, no una regla automática.

<a id="implementation-requirements"></a>
## Requisitos de implementación

<a id="stable-translation-mechanism"></a>
### Mecanismo de traducción estable

Un sistema conforme debe usar un mecanismo de traducción estable apropiado para el sistema que se revisa.

Un mecanismo de traducción estable debe permitir mantener, actualizar, revisar y ampliar el contenido traducido sin depender de comportamiento frágil o no documentado.

Un mecanismo de traducción estable puede incluir:

* archivos de recursos
* tablas de traducción
* enrutamiento consciente de la locale
* recursos de idioma compilados
* páginas localizadas estáticas
* paquetes de idioma en tiempo de ejecución
* traducciones respaldadas por base de datos
* otra estructura de traducción documentada

Un sistema debe evitar codificar de forma rígida contenido esencial orientado al usuario de una manera que impida el soporte de traducción requerido.

<a id="preservation-of-meaning"></a>
### Preservación del significado

Una traducción preserva el significado cuando el usuario puede entender razonablemente la misma instrucción, etiqueta, advertencia, control, ajuste o flujo de trabajo esencial que los usuarios del idioma de origen.

Una traducción no necesita ser idéntica palabra por palabra al contenido de origen.

Una traducción puede cambiar el orden de palabras, la gramática, la estructura de la oración, el modismo, el tono o la formulación cuando sea necesario para comunicar el mismo significado esencial en el idioma de destino.

Una traducción puede fallar la revisión si es engañosa, incompleta, absurda, está dañada por traducción automática o difiere significativamente del contenido de origen de una forma que afecte al uso esencial.

<a id="direction-sensitive-languages"></a>
### Idiomas sensibles a la dirección

Algunas locales requeridas usan comúnmente dirección de texto de derecha a izquierda.

Un sistema conforme no debe impedir que el contenido esencial traducido sea leído, entendido, seleccionado o utilizado porque la locale activa use una dirección de texto diferente.

El sistema debe preservar el orden legible, el comportamiento de puntuación y la asociación de controles para los idiomas sensibles a la dirección.

El pulido visual completo, la calidad tipográfica, el comportamiento de accesibilidad y el refinamiento del diseño pueden requerir una revisión separada. Sin embargo, el contenido esencial traducido debe seguir siendo significativamente utilizable.

<a id="locale-sensitive-values"></a>
### Valores sensibles a la locale

Los valores sensibles a la locale son valores cuyo significado o legibilidad puede variar según idioma, región, escritura o cultura.

Los valores sensibles a la locale pueden incluir:

* fechas
* horas
* números
* monedas
* medidas
* formas plurales
* género gramatical
* orden de clasificación
* formatos de dirección
* formatos de número de teléfono

I18NSPEC no requiere localización completa de cada valor sensible a la locale salvo que ese valor sea esencial para entender u operar el sistema.

Cuando los valores sensibles a la locale son esenciales, el sistema debe representarlos de una forma que los usuarios de la locale activa puedan entender razonablemente.

<a id="verification"></a>
## Verificación

<a id="within-spec"></a>
### Dentro de la especificación

Un sistema se considera dentro de la especificación cuando el Equipo de CatalystUI ha revisado el sistema y ha considerado razonable concluir que satisface I18NSPEC.

Un sistema puede estar dentro de la especificación cuando:

* cada locale requerida está admitida
* más del 75 % del contenido esencial orientado al usuario está traducido para cada locale requerida
* todo el contenido crítico orientado al usuario está traducido para cada locale requerida
* los usuarios pueden seleccionar razonablemente la locale activa
* el comportamiento de fallback no afirma falsamente cobertura de traducción
* la equivalencia de locales, si se usa, es razonable y está documentada
* el contenido traducido preserva el significado esencial

Un sistema puede estar dentro de la especificación aunque parte del contenido no esencial siga sin traducirse.

Un sistema puede estar dentro de la especificación aunque las traducciones no sean perfectas, siempre que se preserve el significado esencial y se satisfagan los requisitos de esta especificación.

<a id="warnings"></a>
### Advertencias

Puede emitirse una advertencia cuando un sistema parece satisfacer I18NSPEC pero contiene preocupaciones que deben documentarse.

Las advertencias pueden incluir:

* contenido no esencial menor sin traducir
* terminología inconsistente entre locales
* traducciones imperfectas pero comprensibles
* equivalencia de locales aceptable que debe documentarse
* comportamiento de fallback limitado
* páginas opcionales parcialmente traducidas
* preocupaciones de diseño sensibles a la dirección que no impiden el uso esencial
* valores sensibles a la locale que son comprensibles pero no ideales

Las advertencias no impiden necesariamente la verificación.

<a id="failures"></a>
### Fallos

Un fallo ocurre cuando un sistema no satisface una o más condiciones requeridas de I18NSPEC.

Los fallos pueden incluir:

* falta de soporte para una locale requerida
* cobertura de traducción esencial igual o inferior al 75 % para una locale requerida
* contenido crítico orientado al usuario sin traducir
* ausencia de un mecanismo razonable de selección de idioma
* selección de idioma que requiere modificación del código fuente
* selección de idioma que requiere herramientas de desarrollo
* carga de traducciones rota
* afirmaciones engañosas sobre locales
* comportamiento de fallback excesivo
* contenido de fallback contado como contenido traducido sin equivalencia de locales válida
* contenido sensible a la dirección ilegible o inutilizable
* flujos de trabajo esenciales no disponibles en una o más locales requeridas

Los fallos impiden la verificación hasta que se resuelvan.

<a id="verification-validity"></a>
### Validez de la verificación

La verificación de I18NSPEC se aplica solo al estado revisado del sistema en el momento en que se emite la verificación.

Un sistema puede conservar la verificación en actualizaciones posteriores siempre que preserve la base de internacionalización verificada.

Los cambios menores de redacción, las traducciones añadidas, las traducciones mejoradas y las actualizaciones ordinarias de contenido no invalidan automáticamente la verificación.

Puede requerirse una nueva revisión si un sistema:

* elimina soporte para una locale requerida
* rompe la selección de idioma
* reduce sustancialmente la cobertura de traducción esencial
* deja nuevos flujos de trabajo esenciales sin traducir
* reemplaza contenido traducido por contenido de fallback
* cambia su arquitectura de traducción de una forma que afecta al comportamiento verificado
* introduce cambios importantes orientados al usuario que alteran el alcance revisado

En otras palabras, mejorar el soporte de traducción suele estar bien.

Romper la base multilingüe verificada puede requerir revisión.
