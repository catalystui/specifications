<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimina estas líneas en un pull request después de verificar la traducción. -->

# Detalles de verificación

## C++

### Resumen

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


El lenguaje de programación C++ ha sido verificado frente a las especificaciones FDEFSPEC (Rev. 1) y FRELSPEC (Rev. 1) con fecha del 7 de julio de 2026.

#### Declaración de buena fe

Creemos de buena fe que el lenguaje de programación C++ puede representar razonablemente los conceptos y disposiciones definidos en las siguientes especificaciones, y que puede usarse para implementar sistemas que cumplan estas especificaciones.

#### Supuestos de revisión

Esta revisión asume compatibilidad con C++ estándar moderno cuando se indican funciones dependientes de la versión. La compatibilidad con enteros de ancho exacto asume que la implementación proporciona los tipos correspondientes de `<cstdint>`.

Esta revisión trata C++ como un lenguaje de programación de sistemas con soporte directo para representación de bajo nivel, modelado de objetos, control de memoria, programación genérica y ejecución concurrente.

### Advertencias

* Los tipos enteros de ancho exacto dependen del soporte de la implementación.
* CP1252 puede representarse byte por byte, pero no se proporciona ningún códec estándar con nombre.
* La serialización UTF-16LE requiere manejo explícito del orden de bytes.
* Algunas funciones de concurrencia y caracteres requieren revisiones modernas de C++.

### Fallos

* No se encontraron fallos conocidos de FDEFSPEC o FRELSPEC durante esta verificación.

### Verificación de FDEFSPEC

#### Numéricos

| Provisión | Verificado | Notas                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Usa campos de bits o máscaras.                    |
| Nibble    | ⚠️       | Usa campos de bits o máscaras.                    |
| Byte      | ✅        | Compatible mediante `std::byte`.              |
| Short     | ✅        | Compatible mediante `int16_t` y `uint16_t`. |
| Int       | ✅        | Compatible mediante `int32_t` y `uint32_t`. |
| Long      | ✅        | Compatible mediante `int64_t` y `uint64_t`. |
| Float     | ✅        | Compatible mediante `float`.                  |
| Double    | ✅        | Compatible mediante `double`.                 |
| Boolean   | ✅        | Compatible mediante `bool`.                   |

#### Codificación de texto

| Provisión | Verificado | Notas                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Compatible mediante `char32_t`.        |
| ASCII     | ✅        | Representable como valores de byte.        |
| CP1252    | ⚠️        | Requiere mapeo explícito de bytes.      |
| UTF-8     | ✅        | Compatible mediante `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Requiere manejo del orden de bytes.        |

#### Estado de operación

| Provisión | Verificado | Notas                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Puede representarse mediante un enum.           |
| Context   | ✅        | Puede representarse mediante un valor.           |
| Operation | ✅        | Puede representarse mediante un valor.           |
| Detail    | ✅        | Puede representarse mediante un valor.           |
| Result    | ✅        | Puede representarse mediante un struct o una clase. |

### Verificación de FRELSPEC

#### Colecciones

| Provisión | Verificado | Notas                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Compatible mediante `std::set`.              |
| Map       | ✅        | Compatible mediante `std::map`.              |
| Array     | ✅        | Compatible mediante arrays y `std::array`. |
| File      | ✅        | Compatible mediante flujos de archivos.            |
| Stream    | ✅        | Compatible mediante iostreams.               |

#### Memoria

| Provisión | Verificado | Notas                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Las direcciones son compatibles.                   |
| Pointer   | ✅        | Los punteros son compatibles.                    |
| Variable  | ✅        | Las variables son compatibles.                   |
| Constant  | ✅        | Compatible mediante `const` y `constexpr`. |

#### Operaciones

| Provisión   | Verificado | Notas                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Representado mediante operaciones de máquina. |
| Procedure   | ✅        | Compatible mediante funciones `void`.     |
| Function    | ✅        | Compatible mediante funciones con retorno.  |

#### Hilos de ejecución

| Provisión  | Verificado | Notas                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Compatible mediante ejecución alojada.      |
| Thread     | ✅        | Compatible mediante `std::thread`; C++11+. |
| Dispatcher | ✅        | Compatible mediante async y planificadores.  |

#### Compuestos

| Provisión | Verificado | Notas                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Los miembros de clase son compatibles.            |
| Object    | ✅        | Los objetos son compatibles.                  |
| Field     | ✅        | Los campos son compatibles.                   |
| Method    | ✅        | Los métodos son compatibles.                  |
| Property  | ✅        | Get/Set maps can be represented.        |
| Structure | ✅        | Las estructuras son compatibles de forma nativa.      |
| Class     | ✅        | Las clases son compatibles de forma nativa.         |
| Interface | ✅        | Puede representarse mediante clases abstractas. |
