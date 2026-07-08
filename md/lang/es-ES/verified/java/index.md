<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimine estas líneas en un pull request después de que la traducción haya sido verificada. -->

# Detalles de verificación

## Java

### Resumen

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


El lenguaje de programación Java ha sido verificado frente a las especificaciones FDEFSPEC (Rev. 1) y FRELSPEC (Rev. 1) a fecha de 7 de julio de 2026.

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
| Byte      | ⚠️       | Signed 8-bit only; widen for unsigned.           |
| Short     | ⚠️       | Signed 16-bit only; widen for unsigned.          |
| Int       | ⚠️       | Signed 32-bit; unsigned helpers require Java 8+. |
| Long      | ⚠️       | Signed 64-bit; unsigned helpers require Java 8+. |
| Float     | ✅        | La coma flotante de 32 bits es compatible.              |
| Double    | ✅        | La coma flotante de 64 bits es compatible.              |
| Boolean   | ✅        | El tipo booleano es compatible.                       |

#### Codificación de texto

| Provisión | Verificado | Notas                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Compatible mediante `int` and `Character`. |
| ASCII     | ✅        | Guaranteed standard charset.             |
| CP1252    | ❌        | No está garantizado por `StandardCharsets`.    |
| UTF-8     | ✅        | Guaranteed standard charset.             |
| UTF-16LE  | ✅        | Guaranteed standard charset.             |

#### Estado de operación

| Provisión | Verificado | Notas                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Puede representarse mediante un tipo personalizado.        |
| Context   | ✅        | Can be represented by a custom value.       |
| Operation | ✅        | Can be represented by a custom value.       |
| Detail    | ✅        | Can be represented by a custom value.       |
| Result    | ✅        | Puede representarse mediante un tipo de retorno personalizado. |

### Verificación de FRELSPEC

#### Colecciones

| Provisión | Verificado | Notas                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Compatible mediante `Set`.       |
| Map       | ✅        | Compatible mediante `Map`.       |
| Array     | ✅        | Native arrays are supported.   |
| File      | ✅        | Compatible mediante API de archivos.   |
| Stream    | ✅        | Compatible mediante API de flujos. |

#### Memoria

| Provisión | Verificado | Notas                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses require Java 22+ FFM.                         |
| Pointer   | ⚠️       | Pointer-like access requires Java 22+ FFM.                     |
| Variable  | ✅        | Declarations and `var` are supported; `var` requires Java 10+. |
| Constant  | ✅        | Compatible mediante `final`.                                     |

#### Operaciones

| Provisión   | Verificado | Notas                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Representado mediante bytecode y operaciones. |
| Procedure   | ✅        | Compatible mediante `void` methods.            |
| Function    | ✅        | Compatible mediante métodos con retorno.         |

#### Hilos de ejecución

| Provisión  | Verificado | Notas                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Compatible mediante application and `Process` APIs. |
| Thread     | ✅        | Compatible mediante `Thread`.                       |
| Dispatcher | ✅        | Compatible mediante `Executor` APIs.                |

#### Compuestos

| Provisión | Verificado | Notas                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Class members are supported.           |
| Object    | ✅        | Los objetos son compatibles.                 |
| Field     | ✅        | Los campos son compatibles.                  |
| Method    | ✅        | Los métodos son compatibles.                 |
| Property  | ❌        | Sin mapa explícito de accesores.              |
| Structure | ✅        | Compatible mediante records; Java 16+.   |
| Class     | ✅        | Las clases son compatibles.                 |
| Interface | ✅        | Interfaces are supported.              |
