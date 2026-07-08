<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimine estas líneas en un pull request después de que la traducción haya sido verificada. -->

# Detalles de verificación

## C

### Resumen

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


El lenguaje de programación C ha sido verificado frente a las especificaciones FDEFSPEC (Rev. 1) y FRELSPEC (Rev. 1) a fecha de 7 de julio de 2026.

#### Declaración de buena fe

Creemos de buena fe que el lenguaje de programación C puede representar razonablemente los conceptos y disposiciones definidos en las siguientes especificaciones, y que puede usarse para implementar sistemas que cumplan estas especificaciones.

#### Declaración de revisión

C proporciona un fuerte soporte de bajo nivel para representación de datos fundamentales, acceso a memoria, archivos, flujos, procedimientos, funciones, estructuras e implementación directa orientada al sistema.

Aunque C no proporciona de forma nativa varias construcciones compuestas orientadas a objetos, estas limitaciones se aíslan a disposiciones compuestas específicas de FRELSPEC y se documentan a continuación. Estos fallos no impiden que C sea considerado dentro de la especificación en conjunto, pero deben entenderse al usar C para implementaciones compatibles con CatalystUI.

#### Supuestos de revisión

Esta revisión asume compatibilidad con C estándar moderno cuando se indican funciones dependientes de la versión. La compatibilidad con enteros de ancho exacto asume que la implementación proporciona los tipos correspondientes de `<stdint.h>`.

Esta revisión trata C como un lenguaje de representación de bajo nivel. Las codificaciones exactas por byte pueden representarse directamente mediante arrays de bytes, tablas de búsqueda y lógica de análisis explícita cuando no se proporciona un códec estándar con nombre.

### Advertencias

* Los tipos enteros de ancho exacto dependen del soporte de la implementación.
* CP1252 puede representarse byte por byte, pero no se proporciona ningún códec estándar con nombre.
* La serialización UTF-16LE requiere manejo explícito del orden de bytes.
* Algunas implementaciones de C pueden omitir los hilos estándar.
* Los patrones orientados a objetos pueden emularse manualmente, pero no son construcciones nativas del lenguaje.

### Fallos

* C no proporciona miembros de método nativos.
* C no proporciona propiedades nativas.
* C no proporciona clases nativas.
* C no proporciona interfaces nativas.

### Verificación de FDEFSPEC

#### Numéricos

| Provisión | Verificado | Notas                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | Compatible mediante `unsigned char`.          |
| Short     | ✅        | Compatible mediante `int16_t` and `uint16_t`. |
| Int       | ✅        | Compatible mediante `int32_t` and `uint32_t`. |
| Long      | ✅        | Compatible mediante `int64_t` and `uint64_t`. |
| Float     | ✅        | Compatible mediante `float`.                  |
| Double    | ✅        | Compatible mediante `double`.                 |
| Boolean   | ✅        | Compatible mediante `bool`; C99+.             |

#### Codificación de texto

| Provisión | Verificado | Notas                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | Compatible mediante `char32_t`; C11+.     |
| ASCII     | ✅        | Representable as byte values.           |
| CP1252    | ⚠️        | Requiere mapeo explícito de bytes.         |
| UTF-8     | ✅        | Compatible mediante UTF-8 literals; C11+. |
| UTF-16LE  | ⚠️        | Requiere manejo del orden de bytes.           |

#### Estado de operación

| Provisión | Verificado | Notas                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Can be represented by an enum.  |
| Context   | ✅        | Can be represented by a value.  |
| Operation | ✅        | Can be represented by a value.  |
| Detail    | ✅        | Can be represented by a value.  |
| Result    | ✅        | Can be represented by a struct. |

### Verificación de FRELSPEC

#### Colecciones

| Provisión | Verificado | Notas                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Can be represented by structs. |
| Map       | ✅        | Can be represented by structs. |
| Array     | ✅        | Native arrays are supported.   |
| File      | ✅        | Compatible mediante API de archivos.   |
| Stream    | ✅        | Compatible mediante API de flujos. |

#### Memoria

| Provisión | Verificado | Notas                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Addresses are supported.   |
| Pointer   | ✅        | Los punteros son compatibles.    |
| Variable  | ✅        | Las variables son compatibles.   |
| Constant  | ✅        | Compatible mediante `const`. |

#### Operaciones

| Provisión   | Verificado | Notas                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Representado mediante operaciones de máquina. |
| Procedure   | ✅        | Compatible mediante `void` functions.     |
| Function    | ✅        | Compatible mediante funciones con retorno.  |

#### Hilos de ejecución

| Provisión  | Verificado | Notas                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Compatible mediante entornos alojados. |
| Thread     | ⚠️        | Compatible mediante `<threads.h>`; C11+. |
| Dispatcher | ✅        | Can be represented directly.           |

#### Compuestos

| Provisión | Verificado | Notas                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Struct members are supported.            |
| Object    | ✅        | Los structs pueden formar compuestos direccionables. |
| Field     | ✅        | Struct fields are supported.             |
| Method    | ❌        | Sin miembros de método nativos.                |
| Property  | ❌        | Sin mapa explícito de accesores Get/Set.        |
| Structure | ✅        | Structures are natively supported.       |
| Class     | ❌        | Sin construcción nativa de clase.               |
| Interface | ❌        | Sin construcción nativa de interfaz.           |
