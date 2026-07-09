<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->

<!-- Elimina estas líneas en un pull request después de que la traducción haya sido verificada. -->

# A11YSPEC

<br/>

> **Especificación de Accesibilidad**<br/>
> Revisión 1<br/>
> 8 de julio de 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Todos los derechos reservados.<br/> <br/>
> Las definiciones, requisitos y conceptos presentados aquí describen soporte práctico de accesibilidad y pueden expresarse libremente con otras palabras.

<a id="introduction"></a>

## Introducción

La **Especificación de Accesibilidad (A11YSPEC)** establece los conceptos, la terminología y los requisitos centrales utilizados para evaluar el soporte de accesibilidad dentro del ecosistema CatalystUI. Su propósito es proporcionar un estándar claro para determinar si un sistema, servicio, framework, aplicación, biblioteca o implementación sigue siendo significativamente usable cuando una vía sensorial primaria no está disponible.

La accesibilidad importa porque una interfaz de usuario no debería depender por completo de un solo sentido cuando el mismo significado esencial puede comunicarse razonablemente por otro. Un sistema puede funcionar técnicamente, pero si un usuario no puede entender, navegar, configurar u operar su comportamiento esencial sin vista, sonido o tacto individualmente, entonces el sistema no ha proporcionado acceso razonable para esa condición.

Esta especificación no intenta verificar todas las discapacidades, dispositivos, tecnologías de asistencia, condiciones médicas, requisitos legales, estándares regionales de accesibilidad ni casos de uso especializados posibles. En su lugar, define la base mínima de accesibilidad requerida para que los usuarios puedan acceder y operar de manera significativa las partes esenciales de un sistema cuando uno de los tres sentidos primarios de accesibilidad no esté disponible.

En términos más simples, A11YSPEC hace tres preguntas principales:

1. ¿Pueden los usuarios entender el sistema esencial sin depender de la vista?
2. ¿Pueden los usuarios entender el sistema esencial sin depender del sonido?
3. ¿Pueden los usuarios operar el sistema esencial sin depender del tacto?

> [!IMPORTANT]
>
> A11YSPEC define requisitos de accesibilidad para verificación. No sustituye a los estándares legales de accesibilidad, los requisitos de certificación de plataformas ni la revisión especializada de tecnologías de asistencia. Un sistema puede estar dentro de A11YSPEC y aun así requerir revisión adicional para otros estándares de accesibilidad.

<a id="table-of-contents"></a>

## Tabla de contenido

- [A11YSPEC](#a11yspec)
  - [Introducción](#introduction)
  - [Tabla de contenido](#table-of-contents)
  - [Conformidad](#conformance)
  - [Sentidos primarios de accesibilidad](#primary-accessibility-senses)
    - [Vista](#sight)
    - [Sonido](#sound)
    - [Tacto](#touch)
    - [Dominios sensoriales adicionales](#additional-sensory-domains)
  - [Casos de accesibilidad requeridos](#required-accessibility-cases)
  - [Funcionalidad esencial](#essential-functionality)
    - [Funcionalidad esencial](#essential-functionality-1)
    - [Funcionalidad crítica](#critical-functionality)
    - [Funcionalidad no esencial](#nonessential-functionality)
  - [Requisitos de accesibilidad](#accessibility-requirements)
    - [Requisito de acceso esencial](#essential-access-requirement)
    - [Requisito de acceso crítico](#critical-access-requirement)
    - [Requisito de acceso alternativo](#alternate-access-requirement)
    - [Sin dependencia de un solo sentido](#no-single-sense-dependency)
  - [Vista no disponible](#sight-unavailable)
  - [Sonido no disponible](#sound-unavailable)
  - [Tacto no disponible](#touch-unavailable)
  - [Requisitos de implementación](#implementation-requirements)
    - [Mecanismo de accesibilidad estable](#stable-accessibility-mechanism)
    - [Estructura semántica](#semantic-structure)
    - [Salida alternativa](#alternate-output)
    - [Entrada alternativa](#alternate-input)
    - [Retroalimentación accesible](#accessible-feedback)
    - [Configuración accesible](#accessible-configuration)
  - [Verificación](#verification)
    - [Dentro de la especificación](#within-spec)
    - [Advertencias](#warnings)
    - [Fallos](#failures)
    - [Validez de la verificación](#verification-validity)

<a id="conformance"></a>

## Conformidad

Un sistema se considera conforme con A11YSPEC cuando satisface los requisitos definidos por este documento para cada caso de accesibilidad requerido.

Un sistema conforme debe:

1. Seguir siendo razonablemente usable cuando la vista no esté disponible.
2. Seguir siendo razonablemente usable cuando el sonido no esté disponible.
3. Seguir siendo razonablemente usable cuando el tacto no esté disponible.
4. Preservar el acceso a la funcionalidad esencial en cada caso de accesibilidad requerido.
5. Preservar el acceso a toda la funcionalidad crítica en cada caso de accesibilidad requerido.
6. Proporcionar rutas razonables de acceso alternativo cuando el significado esencial o la operación dependan de otro modo del sentido no disponible.
7. Usar un mecanismo de accesibilidad estable adecuado para el sistema revisado.
8. Evitar depender exclusivamente de un sentido primario para la funcionalidad esencial.

Un sistema no necesita proporcionar experiencias idénticas en todas las rutas sensoriales. Una experiencia no visual puede ser más lenta que una visual. Una experiencia sin sonido puede requerir subtítulos, indicadores visuales o confirmación háptica. Una experiencia sin tacto puede requerir navegación por teclado, alternativas de puntero, interacción por voz, interacción compatible con interruptores u otro método que no dependa del tacto.

La verificación se ocupa del acceso práctico a la funcionalidad esencial, no de una presentación idéntica.

<a id="primary-accessibility-senses"></a>

## Sentidos primarios de accesibilidad

Para A11YSPEC, los tres sentidos primarios de accesibilidad son **vista**, **sonido** y **tacto**.

Estos sentidos son primarios porque son las vías sensoriales más comunes involucradas en la interacción con interfaces de usuario. Un sistema puede proporcionar salida mediante vista, sonido o tacto, y puede recibir interacción mediante tacto, movimiento, voz, entrada de teclado, entrada de puntero, entrada por interruptor u otra ruta de entrada disponible.

<a id="sight"></a>

### Vista

La vista es la vía sensorial visual por la cual un usuario percibe la salida visual.

La vista puede estar involucrada en percibir:

* texto
* color
* forma
* posición
* disposición
* animación
* iconos
* imágenes
* video
* advertencias visuales
* indicadores visuales de estado
* controles visibles

Un sistema depende de la vista cuando el significado esencial o la operación requiere que el usuario perciba visualmente la información.

<a id="sound"></a>

### Sonido

El sonido es la vía sensorial auditiva por la cual un usuario percibe la salida de audio.

El sonido puede estar involucrado en percibir:

* instrucciones habladas
* alertas
* alarmas
* señales musicales
* efectos de sonido
* indicaciones de audio
* descripciones de audio
* indicadores auditivos de estado
* confirmación hablada
* navegación hablada

Un sistema depende del sonido cuando el significado esencial o la operación requiere que el usuario escuche información.

<a id="touch"></a>

### Tacto

El tacto es la vía sensorial táctil por la cual un usuario percibe salida física o háptica, y la vía de interacción física por la cual un usuario puede operar controles mediante contacto directo, presión, gesto o movimiento.

El tacto puede estar involucrado en percibir o realizar:

* gestos táctiles
* retroalimentación háptica
* vibración
* textura física
* fuerza
* presión
* controles solo táctiles
* botones físicos
* manipulación directa
* interacción con pantalla táctil
* acciones de arrastre
* acciones de deslizamiento

Un sistema depende del tacto cuando el significado esencial o la operación requiere percepción táctil o interacción basada en el tacto sin una ruta razonable de entrada o salida alternativa.

<a id="additional-sensory-domains"></a>

### Dominios sensoriales adicionales

CatalystUI también reconoce **gusto** y **olfato** como dominios sensoriales.

El gusto y el olfato pueden considerarse durante la revisión de accesibilidad cuando el sistema los utiliza de manera significativa. Estos sentidos son inclusivos para la verificación, lo que significa que pueden fortalecer o respaldar una revisión de accesibilidad cuando proporcionan acceso alternativo significativo o contexto adicional.

El gusto y el olfato no son actualmente exclusivos para el fallo. Un sistema no falla A11YSPEC simplemente porque no proporcione interacción basada en el gusto o el olfato.

A11YSPEC se ocupa principalmente de si el sistema sigue siendo razonablemente usable cuando la vista, el sonido o el tacto no están disponibles individualmente.

<a id="required-accessibility-cases"></a>

## Casos de accesibilidad requeridos

Un sistema conforme debe revisarse contra cada caso de accesibilidad requerido.

| Sentido no disponible | Comportamiento de accesibilidad requerido |
| ----------------- | ----------------------------------------------------------------- |
| Vista             | El sistema debe seguir siendo razonablemente usable mediante sonido y tacto. |
| Sonido            | El sistema debe seguir siendo razonablemente usable mediante vista y tacto. |
| Tacto             | El sistema debe seguir siendo razonablemente usable mediante vista y sonido. |

Cada caso se revisa individualmente.

Un sistema no está obligado a seguir siendo plenamente usable cuando varios sentidos primarios no están disponibles al mismo tiempo, salvo que esa condición esté incluida en el alcance revisado.

Un sistema no está obligado a proporcionar todas las adaptaciones posibles. Debe proporcionar acceso razonable a la funcionalidad esencial en cada caso de accesibilidad requerido.

<a id="essential-functionality"></a>

## Funcionalidad esencial

<a id="essential-functionality-1"></a>

### Funcionalidad esencial

La funcionalidad esencial es cualquier comportamiento, contenido, control, salida, entrada, flujo de trabajo o configuración que un usuario necesita razonablemente para entender, navegar, configurar u operar el comportamiento esencial de un sistema.

La funcionalidad esencial puede incluir:

* navegación principal
* flujos de trabajo centrales
* controles requeridos
* advertencias importantes
* errores importantes
* mensajes de confirmación requeridos
* acceso a cuenta o sesión
* ajustes y preferencias
* configuración de idioma
* configuración de accesibilidad
* instrucciones esenciales
* información de estado orientada al usuario
* cualquier interacción requerida para el uso normal

Un sistema no necesita hacer que todas las funciones decorativas, opcionales, redundantes o no esenciales estén disponibles de la misma manera por todas las rutas sensoriales. Sin embargo, el usuario no debe quedar bloqueado de usar el sistema esencial por el sentido no disponible.

<a id="critical-functionality"></a>

### Funcionalidad crítica

La funcionalidad crítica es funcionalidad esencial cuya pérdida de acceso puede impedir el uso significativo, crear un error grave o hacer que el usuario tome una decisión importante sin entender la consecuencia.

La funcionalidad crítica puede incluir:

* ajustes de accesibilidad
* ajustes de idioma
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
* acceso a la sesión
* comportamiento de parada o cancelación de emergencia
* navegación central requerida para llegar a los ajustes de accesibilidad

La funcionalidad crítica debe permanecer accesible en cada caso de accesibilidad requerido.

Un sistema puede fallar A11YSPEC si la funcionalidad crítica depende exclusivamente del sentido no disponible.

<a id="nonessential-functionality"></a>

### Funcionalidad no esencial

La funcionalidad no esencial es funcionalidad que no se requiere razonablemente para que un usuario entienda, navegue, configure u opere el comportamiento esencial de un sistema.

La funcionalidad no esencial puede incluir:

* animación decorativa
* efectos opcionales
* pulido visual cosmético
* efectos de sonido no esenciales
* efectos hápticos redundantes
* contenido de marketing opcional
* contenido tutorial opcional
* comportamiento de diagnóstico oculto
* controles orientados a desarrolladores
* funciones experimentales fuera del alcance revisado

La funcionalidad no esencial puede ser inaccesible en uno o más casos de accesibilidad sin causar automáticamente un fallo. Sin embargo, la funcionalidad no esencial no debe confundirse con funcionalidad esencial solo porque sea incómodo darle soporte.

<a id="accessibility-requirements"></a>

## Requisitos de accesibilidad

<a id="essential-access-requirement"></a>

### Requisito de acceso esencial

Un sistema satisface el requisito de acceso esencial cuando la funcionalidad esencial sigue siendo razonablemente comprensible, navegable, configurable y operable en cada caso de accesibilidad requerido.

La experiencia esencial no necesita ser idéntica en todos los sentidos.

La experiencia esencial debe seguir siendo significativamente usable.

<a id="critical-access-requirement"></a>

### Requisito de acceso crítico

Un sistema satisface el requisito de acceso crítico cuando toda la funcionalidad crítica permanece accesible en cada caso de accesibilidad requerido.

La funcionalidad crítica no debe quedar oculta detrás de una vía sensorial requerida.

Por ejemplo, un sistema no debería proporcionar una interfaz accesible para el uso ordinario mientras deja advertencias de eliminación de cuenta, confirmaciones de pago, decisiones de privacidad o ajustes de accesibilidad dependientes únicamente de la vista, el sonido o el tacto.

<a id="alternate-access-requirement"></a>

### Requisito de acceso alternativo

Un sistema satisface el requisito de acceso alternativo cuando el significado esencial o la operación proporcionados mediante un sentido primario también están razonablemente disponibles mediante otra ruta sensorial o de interacción cuando ese sentido no está disponible.

El acceso alternativo puede proporcionarse mediante:

* alternativas de texto
* subtítulos
* transcripciones
* salida hablada
* estructura compatible con lectores de pantalla
* navegación por teclado
* alternativas de puntero
* interacción compatible con interruptores
* control por voz
* alertas visuales
* retroalimentación háptica
* indicadores de foco
* estructura semántica
* API de plataforma accesibles
* integración de accesibilidad a nivel de dispositivo
* otro mecanismo estable adecuado para el sistema

La ruta alternativa no necesita coincidir perfectamente con la ruta original. Debe preservar el significado y la operación esenciales.

<a id="no-single-sense-dependency"></a>

### Sin dependencia de un solo sentido

Un sistema no debe requerir un sentido primario como única ruta hacia la funcionalidad esencial.

Un sistema puede usar la vista, el sonido o el tacto como experiencia primaria. Sin embargo, cuando ese sentido no esté disponible, el usuario debe seguir teniendo una forma razonable de entender y operar el sistema esencial mediante las rutas sensoriales restantes.

Un sistema puede fallar la revisión cuando la información o interacción esencial está disponible solo mediante:

* significado solo visual
* significado solo auditivo
* significado solo táctil
* operación solo por gestos
* confirmación solo háptica
* estado indicado solo por color
* alertas solo sonoras
* instrucciones solo por disposición visual
* guía solo por textura física

<a id="sight-unavailable"></a>

## Vista no disponible

Cuando la vista no está disponible, el sistema debe seguir siendo razonablemente usable mediante sonido y tacto.

Esto significa que la información visual esencial debe tener una ruta de acceso no visual significativa.

Un sistema puede satisfacer este requisito mediante:

* salida hablada
* estructura compatible con lectores de pantalla
* orden de foco significativo
* acceso por teclado
* controles táctiles
* confirmación háptica
* descripciones de audio
* soporte de texto a voz
* etiquetas semánticas
* nombres accesibles
* roles accesibles
* información de estado accesible
* otro mecanismo no visual razonable

Un sistema no debería depender exclusivamente de:

* posición visual
* color
* forma
* animación
* iconos
* disposición
* imágenes
* video
* advertencias solo visuales
* indicadores de estado solo visuales

cuando esa información sea necesaria para entender u operar funcionalidad esencial.

Un sistema puede fallar este caso si un usuario no puede navegar, entender u operar razonablemente el sistema esencial sin vista.

<a id="sound-unavailable"></a>

## Sonido no disponible

Cuando el sonido no está disponible, el sistema debe seguir siendo razonablemente usable mediante vista y tacto.

Esto significa que la información auditiva esencial debe tener una ruta de acceso no auditiva significativa.

Un sistema puede satisfacer este requisito mediante:

* subtítulos
* transcripciones
* alertas visuales
* equivalentes de texto
* indicadores de progreso
* mensajes de estado visibles
* retroalimentación háptica
* confirmación visual
* instrucciones escritas
* indicadores simbólicos
* otro mecanismo no auditivo razonable

Un sistema no debería depender exclusivamente de:

* efectos de sonido
* instrucciones habladas
* alertas
* alarmas
* señales musicales
* indicaciones solo de audio
* confirmación hablada
* advertencias solo de audio
* indicadores de estado solo de audio

cuando esa información sea necesaria para entender u operar funcionalidad esencial.

Un sistema puede fallar este caso si un usuario no puede navegar, entender u operar razonablemente el sistema esencial sin sonido.

<a id="touch-unavailable"></a>

## Tacto no disponible

Cuando el tacto no está disponible, el sistema debe seguir siendo razonablemente usable mediante vista y sonido.

Esto significa que la información táctil esencial y la operación basada en el tacto deben tener una ruta de acceso no táctil significativa.

Un sistema puede satisfacer este requisito mediante:

* navegación por teclado
* alternativas de puntero
* control por voz
* controles remotos
* interacción compatible con la mirada
* interacción compatible con interruptores
* indicaciones habladas
* confirmación visual
* sistemas accesibles de atajos
* paletas de comandos
* interacción basada en foco
* otro mecanismo no táctil razonable

Un sistema no debería depender exclusivamente de:

* gestos táctiles
* retroalimentación háptica
* textura física
* vibración
* fuerza
* presión
* controles solo táctiles
* comportamiento solo de arrastre
* comportamiento solo de deslizamiento
* comportamiento solo de pellizco
* manipulación directa sin alternativas

cuando esa interacción sea necesaria para entender u operar funcionalidad esencial.

Un sistema puede fallar este caso si un usuario no puede navegar, entender u operar razonablemente el sistema esencial sin tacto.

<a id="implementation-requirements"></a>

## Requisitos de implementación

<a id="stable-accessibility-mechanism"></a>

### Mecanismo de accesibilidad estable

Un sistema conforme debe usar un mecanismo de accesibilidad estable adecuado para el sistema que se está revisando.

Un mecanismo de accesibilidad estable debería permitir que el comportamiento de accesibilidad se mantenga, actualice, revise y amplíe sin depender de comportamiento frágil o no documentado.

Un mecanismo de accesibilidad estable puede incluir:

* API nativas de accesibilidad de la plataforma
* estructura semántica
* métodos de entrada alternativos
* métodos de salida alternativos
* soporte para tecnologías de asistencia
* ajustes de accesibilidad incorporados
* integración a nivel de dispositivo
* interacción documentada por teclado
* interacción documentada por voz
* interacción no visual documentada
* otra estructura estable adecuada para el sistema

Un sistema debería evitar implementar funcionalidad esencial de una forma que impida un acceso alternativo razonable.

<a id="semantic-structure"></a>

### Estructura semántica

Un sistema conforme debería proporcionar estructura semántica cuando el sistema presenta contenido o controles significativos.

La estructura semántica puede incluir:

* nombres
* roles
* estados
* relaciones
* ordenación
* agrupación
* etiquetas
* descripciones
* comportamiento de foco
* propósito de control
* jerarquía de contenido

La estructura semántica es especialmente importante cuando la vista no está disponible, porque las tecnologías de asistencia a menudo dependen de la información semántica para comunicar interfaces visuales mediante salida no visual.

Un sistema puede fallar la revisión si los controles o contenidos esenciales no pueden entenderse porque su estructura, etiquetas o relaciones no están disponibles mediante rutas de acceso alternativas.

<a id="alternate-output"></a>

### Salida alternativa

Un sistema conforme debe proporcionar salida alternativa razonable cuando el significado esencial dependería de otro modo del sentido no disponible.

La salida alternativa puede incluir:

* salida visual para información auditiva
* salida auditiva para información visual
* salida táctil para información visual o auditiva
* equivalentes de texto
* subtítulos
* transcripciones
* descripciones habladas
* mensajes de estado visibles
* confirmación háptica
* otra ruta de salida adecuada

La salida alternativa debe preservar el significado esencial.

<a id="alternate-input"></a>

### Entrada alternativa

Un sistema conforme debe proporcionar entrada alternativa razonable cuando la operación esencial dependería de otro modo solo del tacto.

La entrada alternativa puede incluir:

* entrada por teclado
* entrada por puntero
* entrada por voz
* entrada por interruptor
* entrada remota
* entrada compatible con la mirada
* entrada por comandos
* otra ruta de entrada adecuada

La entrada alternativa no necesita ser el método de entrada más rápido ni el más conveniente. Debe ser suficiente para la operación esencial.

<a id="accessible-feedback"></a>

### Retroalimentación accesible

Un sistema conforme debe proporcionar retroalimentación accesible para las acciones esenciales.

La retroalimentación accesible puede incluir:

* confirmación de que ocurrió una acción
* indicación de que una acción falló
* información de progreso
* mensajes de validación
* mensajes de advertencia
* mensajes de error
* estado de finalización
* selección actual
* foco actual
* modo actual
* estado actual del sistema

La retroalimentación no debe depender exclusivamente del sentido no disponible en el caso de accesibilidad correspondiente.

Por ejemplo, un sonido de éxito únicamente sonoro no es suficiente cuando el sonido no está disponible. Un estado de error indicado solo por color no es suficiente cuando la vista no está disponible. Una confirmación solo por vibración no es suficiente cuando el tacto no está disponible.

<a id="accessible-configuration"></a>

### Configuración accesible

Un sistema conforme debe permitir que los usuarios lleguen a los ajustes de accesibilidad requeridos y los usen mediante los mismos requisitos de accesibilidad definidos por esta especificación.

Los ajustes de accesibilidad no deben estar ocultos detrás de una ruta inaccesible.

Por ejemplo, un modo compatible con lectores de pantalla no es suficiente si el usuario primero debe navegar por un menú solo visual y sin etiquetas para habilitarlo.

Un sistema puede fallar la revisión si su configuración de accesibilidad no puede alcanzarse u operarse en la condición que pretende apoyar.

<a id="verification"></a>

## Verificación

<a id="within-spec"></a>

### Dentro de la especificación

Un sistema se considera dentro de la especificación cuando el Equipo de CatalystUI ha revisado el sistema y ha encontrado razonable concluir que satisface A11YSPEC.

Un sistema puede estar dentro de la especificación cuando:

* el uso con vista no disponible sigue estando razonablemente soportado
* el uso con sonido no disponible sigue estando razonablemente soportado
* el uso con tacto no disponible sigue estando razonablemente soportado
* la funcionalidad esencial sigue siendo accesible en cada caso requerido
* la funcionalidad crítica sigue siendo accesible en cada caso requerido
* las rutas de acceso alternativas preservan el significado y la operación esenciales
* los ajustes de accesibilidad, cuando existen, pueden alcanzarse y usarse de forma accesible
* el sistema no atrapa la funcionalidad esencial detrás de un sentido requerido
* el sistema usa un mecanismo de accesibilidad estable adecuado para su diseño

Un sistema puede estar dentro de la especificación aunque las experiencias no sean idénticas en todas las rutas sensoriales.

Un sistema puede estar dentro de la especificación aunque alguna funcionalidad no esencial no esté igualmente disponible en todos los casos de accesibilidad requeridos.

<a id="warnings"></a>

### Advertencias

Puede emitirse una advertencia cuando un sistema parece satisfacer A11YSPEC pero contiene preocupaciones que deberían documentarse.

Las advertencias pueden incluir:

* contenido menor no esencial no disponible en un caso de accesibilidad
* rutas de acceso alternativas más lentas pero usables
* subtítulos o transcripciones imperfectos pero comprensibles
* navegación por teclado limitada pero funcional
* soporte limitado pero funcional para lectores de pantalla
* preocupaciones menores sobre el orden de foco que no bloquean el uso esencial
* señales visuales, auditivas o táctiles redundantes ausentes en una ruta
* ajustes de accesibilidad que son usables pero difíciles de encontrar
* soporte para tecnologías de asistencia que funciona pero podría ser más claro
* flujos de trabajo opcionales que no son igualmente accesibles

Las advertencias no impiden necesariamente la verificación.

<a id="failures"></a>

### Fallos

Un fallo ocurre cuando un sistema no satisface una o más condiciones requeridas de A11YSPEC.

Los fallos pueden incluir:

* funcionalidad esencial no disponible cuando la vista no está disponible
* funcionalidad esencial no disponible cuando el sonido no está disponible
* funcionalidad esencial no disponible cuando el tacto no está disponible
* funcionalidad crítica no disponible en cualquier caso de accesibilidad requerido
* ninguna ruta razonable de acceso alternativo para información visual esencial
* ninguna ruta razonable de acceso alternativo para información auditiva esencial
* ninguna ruta razonable de acceso alternativo para operación esencial basada en el tacto
* ajustes de accesibilidad inalcanzables bajo la condición que deben apoyar
* controles sin etiquetas o estructura significativas cuando se requieren para uso no visual
* advertencias solo sonoras sin equivalente visual, táctil o textual
* estado indicado solo por color sin equivalente no visual
* operación solo por gestos sin alternativa de teclado, puntero, voz, interruptor u otra
* confirmación solo háptica sin equivalente visual o auditivo
* soporte roto de tecnologías de asistencia para flujos de trabajo esenciales
* trampas mayores de navegación
* flujos de trabajo esenciales que no pueden completarse sin el sentido no disponible

Los fallos impiden la verificación hasta que se resuelvan.

<a id="verification-validity"></a>

### Validez de la verificación

La verificación A11YSPEC se aplica únicamente al estado revisado del sistema en el momento en que se emite la verificación.

Un sistema puede conservar la verificación a través de actualizaciones posteriores siempre que preserve la base de accesibilidad verificada.

Cambios menores de redacción, refinamientos visuales, mejoras de rendimiento, funciones de accesibilidad añadidas y actualizaciones ordinarias de contenido no invalidan automáticamente la verificación.

Puede requerirse una nueva revisión si un sistema:

* elimina rutas de acceso alternativas
* rompe el soporte para tecnologías de asistencia
* cambia sustancialmente la navegación esencial
* elimina ajustes de accesibilidad requeridos
* cambia el comportamiento de interacción de una manera que afecta la accesibilidad verificada
* introduce nuevos flujos de trabajo esenciales sin alternativas accesibles
* vuelve inaccesible funcionalidad crítica que antes era accesible
* reemplaza comportamiento accesible con comportamiento dependiente de un solo sentido

En otras palabras, mejorar la accesibilidad suele estar bien.

Romper el modelo de acceso verificado puede requerir revisión.
