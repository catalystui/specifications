<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->

<!-- Elimina estas líneas en un pull request después de que la traducción haya sido verificada. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Bienvenido a la documentación de verificación de CatalystUI para accesibilidad.

**CatalystUI Verified for Accessibility** indica que un servicio, framework, aplicación, biblioteca o sistema ha sido revisado por el Equipo de CatalystUI y se ha determinado que sigue siendo razonablemente usable cuando uno de los tres sentidos primarios involucrados en la interacción con interfaces de usuario no está disponible individualmente.

Para esta verificación, CatalystUI identifica los tres sentidos primarios de accesibilidad como **vista**, **sonido** y **tacto**. Un sistema verificado debe preservar un acceso razonable a su funcionalidad esencial cuando cualquiera de estos sentidos no esté disponible, apoyándose en los dominios sensoriales restantes que sí estén disponibles.

En términos más simples, esta verificación pregunta si un usuario todavía puede entender, navegar y operar de manera significativa las partes esenciales de un sistema si no puede depender individualmente de la vista, el sonido o el tacto.

## Propósito

La accesibilidad importa porque una interfaz de usuario no debería depender por completo de una sola vía sensorial cuando el mismo significado esencial puede comunicarse razonablemente por otra.

CatalystUI está diseñado en torno al movimiento fiel de los datos entre los sistemas y la percepción humana. Si la información importante solo es visible, solo es audible o solo está disponible mediante el tacto, entonces el sistema puede volverse inutilizable para usuarios que no pueden depender de ese sentido. La Verificación de Accesibilidad existe para identificar sistemas que preservan el acceso al permitir que la información esencial y la interacción continúen por rutas sensoriales alternativas.

El objetivo no es exigir todos los métodos de interacción posibles, todas las tecnologías de asistencia ni todas las adaptaciones especializadas. El objetivo es determinar si el sistema esencial sigue siendo significativamente usable cuando la vista, el sonido o el tacto no están disponibles individualmente.

## Qué significa la verificación

Un sistema se convierte en **CatalystUI Verified for Accessibility** cuando se revisa contra los requisitos enumerados en esta sección y se determina que está dentro de la especificación.

Para ser verificado, un sistema debe seguir siendo razonablemente usable en cada uno de los siguientes casos:

| Sentido no disponible | Comportamiento de accesibilidad requerido |
| ----------------- | ----------------------------------------------------------------- |
| Vista             | El sistema debe seguir siendo razonablemente usable mediante sonido y tacto. |
| Sonido            | El sistema debe seguir siendo razonablemente usable mediante vista y tacto. |
| Tacto             | El sistema debe seguir siendo razonablemente usable mediante vista y sonido. |

Un sistema no necesita ofrecer experiencias idénticas en todas las rutas sensoriales. Una experiencia no visual puede ser más lenta que una visual. Una experiencia sin sonido puede requerir subtítulos, indicadores visuales u otras sustituciones. Una experiencia sin tacto puede requerir controles alternativos, interacción por voz, navegación por teclado, navegación con puntero u otros métodos que no dependan del tacto.

Lo que importa es si la funcionalidad esencial sigue siendo accesible, comprensible y operable sin requerir el sentido no disponible.

## Funcionalidad esencial

Para la Verificación de Accesibilidad, **funcionalidad esencial** se refiere a las partes de un sistema que un usuario necesita razonablemente para entender, navegar, configurar y operar el sistema.

La funcionalidad esencial puede incluir:

* navegación principal
* flujos de trabajo centrales
* controles requeridos
* advertencias importantes
* errores importantes
* mensajes de confirmación requeridos
* acceso a cuenta o sesión
* ajustes y preferencias
* configuración de idioma o accesibilidad
* instrucciones esenciales
* información de estado orientada al usuario
* cualquier interacción requerida para el uso normal

Un sistema puede seguir estando dentro de la especificación si las funciones decorativas, redundantes, opcionales o no esenciales no están disponibles de la misma manera por todas las rutas sensoriales. Sin embargo, el usuario debe poder seguir usando el sistema esencial sin quedar bloqueado por el sentido ausente.

## Vista no disponible

Cuando la vista no está disponible, el sistema debería seguir siendo razonablemente usable mediante sonido y tacto.

Esto puede incluir salida hablada, estructura compatible con lectores de pantalla, orden de foco significativo, controles táctiles, acceso por teclado, confirmación háptica, descripciones de audio u otro método no visual razonable para comunicar información esencial.

Un sistema no debería depender exclusivamente de la posición visual, el color, la forma, la animación, los iconos o la disposición cuando esa información sea necesaria para entender u operar funcionalidad esencial.

## Sonido no disponible

Cuando el sonido no está disponible, el sistema debería seguir siendo razonablemente usable mediante vista y tacto.

Esto puede incluir subtítulos, transcripciones, alertas visuales, equivalentes de texto, indicadores de progreso, mensajes de estado visibles, retroalimentación háptica u otro método no auditivo razonable para comunicar información esencial.

Un sistema no debería depender exclusivamente de efectos de sonido, instrucciones habladas, alertas, alarmas, señales musicales o indicaciones solo de audio cuando esa información sea necesaria para entender u operar funcionalidad esencial.

## Tacto no disponible

Cuando el tacto no está disponible, el sistema debería seguir siendo razonablemente usable mediante vista y sonido.

Esto puede incluir control por voz, navegación por teclado, alternativas de puntero, controles remotos, interacción compatible con la mirada, interacción compatible con interruptores, indicaciones habladas, confirmación visual u otro método razonable que no requiera interacción basada en el tacto ni percepción táctil.

Un sistema no debería depender exclusivamente de gestos táctiles, retroalimentación háptica, textura física, vibración, fuerza, presión o controles solo táctiles cuando esas interacciones sean necesarias para entender u operar funcionalidad esencial.

## Dominios sensoriales adicionales

CatalystUI también reconoce **gusto** y **olfato** como dominios sensoriales. Estos dominios pueden considerarse durante la revisión de accesibilidad cuando el sistema los usa de manera significativa.

El gusto y el olfato son **inclusivos** para la verificación, lo que significa que pueden fortalecer o respaldar una revisión de accesibilidad cuando proporcionan acceso alternativo significativo o contexto adicional.

El gusto y el olfato no son actualmente **exclusivos** para el fallo, lo que significa que un sistema no falla la Verificación de Accesibilidad simplemente porque no proporcione interacción basada en el gusto o el olfato.

La Verificación de Accesibilidad de CatalystUI se ocupa principalmente de si el sistema sigue siendo razonablemente usable cuando la vista, el sonido o el tacto no están disponibles individualmente.

## Qué significa “dentro de la especificación”

Cuando se considera que un sistema está **dentro de la especificación**, significa que el Equipo de CatalystUI ha revisado manualmente el sistema y ha encontrado razonable concluir que satisface los requisitos de accesibilidad descritos por esta categoría de verificación.

Esto no requiere un único patrón rígido de implementación. Un sistema puede satisfacer los requisitos de accesibilidad mediante API nativas de accesibilidad de la plataforma, estructura semántica, métodos de entrada alternativos, métodos de salida alternativos, soporte para tecnologías de asistencia, ajustes de accesibilidad incorporados, integración a nivel de dispositivo u otro mecanismo estable adecuado para el sistema.

La verificación se ocupa de la capacidad práctica de los usuarios para acceder al sistema esencial cuando un sentido primario no está disponible, no de si el sistema usa una arquitectura específica de accesibilidad.

## Qué no significa la verificación

CatalystUI Verified for Accessibility no garantiza que se hayan revisado completamente todas las posibles discapacidades, dispositivos, tecnologías de asistencia, condiciones médicas, requisitos legales, estándares regionales o casos de uso especializados.

Tampoco verifica automáticamente la internacionalización, la calidad de la traducción, la tipografía, la localización, el cumplimiento regional ni la calidad general del diseño, salvo que esas cuestiones estén incluidas en el alcance de accesibilidad revisado.

Un sistema puede ser razonablemente accesible según el modelo de accesibilidad de CatalystUI y aun así requerir una revisión separada para cumplimiento legal, certificación de plataforma, soporte especializado para tecnologías de asistencia u otros estándares de accesibilidad.

## Por qué existe esta verificación

Una interfaz de usuario solo tiene éxito cuando los usuarios realmente pueden usarla.

Muchos sistemas tratan la accesibilidad como una idea secundaria, una lista de verificación o un requisito técnico estrecho en lugar de una parte fundamental de la interacción humano-computadora. CatalystUI adopta un enfoque más simple y directo: si un sistema depende de la percepción humana, entonces el sistema debería preservar el significado esencial cuando una vía sensorial primaria no está disponible.

La Verificación de Accesibilidad existe para identificar sistemas que toman esta responsabilidad en serio. Reconoce sistemas que proporcionan acceso alternativo significativo, preservan la funcionalidad esencial y evitan atrapar a los usuarios detrás de un único sentido requerido.

## Alcance de la verificación

La Verificación de CatalystUI para Accesibilidad se aplica al sistema, servicio, framework, aplicación, biblioteca o implementación revisado tal como existía en el momento en que se emitió la verificación.

Un sistema verificado proporciona accesibilidad razonable para su funcionalidad esencial bajo las condiciones revisadas. No garantiza que cada página, función, lanzamiento, plugin, extensión, integración de terceros, dispositivo o versión específica de plataforma futura esté automáticamente dentro de la especificación.

Productos, módulos, servicios, revisiones mayores o compilaciones específicas de plataforma separadas pueden requerir su propia revisión según la categoría de verificación solicitada.

## Validez de la verificación

La Verificación de CatalystUI se aplica únicamente al estado revisado del sistema en el momento en que se emite la verificación.

Un sistema puede conservar su verificación a través de actualizaciones posteriores siempre que preserve la base de accesibilidad verificada. Cambios menores de redacción, refinamientos visuales, mejoras de rendimiento y actualizaciones ordinarias de contenido no invalidan automáticamente la verificación.

Puede requerirse una nueva revisión si un sistema elimina rutas de acceso alternativas, rompe el soporte para tecnologías de asistencia, cambia sustancialmente la navegación esencial, elimina ajustes de accesibilidad requeridos o cambia el comportamiento de interacción de una manera que afecte la base de accesibilidad verificada.

En otras palabras, mejorar la accesibilidad suele estar bien. Romper el modelo de acceso verificado puede requerir revisión.

## Sistemas verificados

Los sistemas conocidos verificados para accesibilidad se enumeran por separado en la página apropiada de CatalystUI Verified.
