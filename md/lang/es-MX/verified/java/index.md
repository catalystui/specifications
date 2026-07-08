<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimina estas líneas en un pull request después de verificar la traducción. -->

# Detalles de verificación

## Java

### Resumen

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


El lenguaje de programación Java ha sido verificado frente a las especificaciones FDEFSPEC (Rev. 1) y FRELSPEC (Rev. 1) con fecha del 7 de julio de 2026.

#### Declaración de buena fe

Creemos de buena fe que el lenguaje de programación Java puede representar razonablemente una gran parte de los conceptos y disposiciones definidos en las siguientes especificaciones, y que puede usarse para implementar sistemas que cumplan estas especificaciones.

#### Supuestos de revisión

Esta revisión asume compatibilidad con Java moderno cuando se indican funciones dependientes de la versión. Funciones como la inferencia de variables locales, los records y el acceso a memoria extranjera pueden requerir versiones posteriores de Java.

### Advertencias

* Java no tiene soporte nativo para tipos numéricos sin signo, lo que puede requerir ampliación o representaciones alternativas para ciertas disposiciones.
* El comportamiento de direcciones de memoria directas y estilo puntero puede requerir soporte de la Foreign Function and Memory API de Java 22+.
* Java no tiene sintaxis nativa de propiedades, por lo que requiere métodos getter y setter.

### Fallos

* Java no proporciona CP1252 como conjunto de caracteres estándar garantizado, por lo que requiere soporte específico de la implementación, bibliotecas adicionales o manejo personalizado para el cumplimiento completo.
* Las propiedades de Java no proporcionan un miembro con clave explícita respaldado por un mapa de accesores Get/Set requerido.

### Verificación de FDEFSPEC

#### Numéricos

| Provisión | Verificado | Notas                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | No hay numérico de 1 bit; ampliar.                         |
| Nibble    | ⚠️       | No hay numérico de 4 bits; ampliar.                         |
| Byte      | ⚠️       | Solo 8 bits con signo; ampliar para valores sin signo.           |
| Short     | ⚠️       | Solo 16 bits con signo; ampliar para valores sin signo.          |
| Int       | ⚠️       | 32 bits con signo; los auxiliares sin signo requieren Java 8+. |
| Long      | ⚠️       | 64 bits con signo; los auxiliares sin signo requieren Java 8+. |
| Float     | ✅        | La coma flotante de 32 bits es compatible.              |
| Double    | ✅        | La coma flotante de 64 bits es compatible.              |
| Boolean   | ✅        | El tipo booleano es compatible.                       |

#### Codificación de texto

| Provisión | Verificado | Notas                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Compatible mediante `int` y `Character`. |
| ASCII     | ✅        | Conjunto de caracteres estándar garantizado.             |
| CP1252    | ❌        | No está garantizado por `StandardCharsets`.    |
| UTF-8     | ✅        | Conjunto de caracteres estándar garantizado.             |
| UTF-16LE  | ✅        | Conjunto de caracteres estándar garantizado.             |

#### Estado de operación

| Provisión | Verificado | Notas                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Puede representarse mediante un tipo personalizado.        |
| Context   | ✅        | Puede representarse mediante un valor personalizado.       |
| Operation | ✅        | Puede representarse mediante un valor personalizado.       |
| Detail    | ✅        | Puede representarse mediante un valor personalizado.       |
| Result    | ✅        | Puede representarse mediante un tipo de retorno personalizado. |

### Verificación de FRELSPEC

#### Colecciones

| Provisión | Verificado | Notas                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Compatible mediante `Set`.       |
| Map       | ✅        | Compatible mediante `Map`.       |
| Array     | ✅        | Los arrays nativos son compatibles.   |
| File      | ✅        | Compatible mediante API de archivos.   |
| Stream    | ✅        | Compatible mediante API de flujos. |

#### Memoria

| Provisión | Verificado | Notas                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses require Java 22+ FFM.                         |
| Pointer   | ⚠️       | El acceso similar a punteros requiere Java 22+ FFM.                     |
| Variable  | ✅        | Las declaraciones y `var` son compatibles; `var` requiere Java 10+. |
| Constant  | ✅        | Compatible mediante `final`.                                     |

#### Operaciones

| Provisión   | Verificado | Notas                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Representado mediante bytecode y operaciones. |
| Procedure   | ✅        | Compatible mediante métodos `void`.            |
| Function    | ✅        | Compatible mediante métodos con retorno.         |

#### Hilos de ejecución

| Provisión  | Verificado | Notas                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Compatible mediante la aplicación y las API de `Process`. |
| Thread     | ✅        | Compatible mediante `Thread`.                       |
| Dispatcher | ✅        | Compatible mediante `Executor` APIs.                |

#### Compuestos

| Provisión | Verificado | Notas                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Los miembros de clase son compatibles.           |
| Object    | ✅        | Los objetos son compatibles.                 |
| Field     | ✅        | Los campos son compatibles.                  |
| Method    | ✅        | Los métodos son compatibles.                 |
| Property  | ❌        | Sin mapa explícito de accesores.              |
| Structure | ✅        | Compatible mediante records; Java 16+.   |
| Class     | ✅        | Las clases son compatibles.                 |
| Interface | ✅        | Las interfaces son compatibles.              |
