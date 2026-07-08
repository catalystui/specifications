<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimine estas líneas en un pull request después de que la traducción haya sido verificada. -->

# Detalles de verificación

## C++

### Resumen

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


El lenguaje de programación C++ ha sido verificado frente a las especificaciones FDEFSPEC (Rev. 1) y FRELSPEC (Rev. 1) a fecha de 7 de julio de 2026.

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
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | Compatible mediante `std::byte`.              |
| Short     | ✅        | Compatible mediante `int16_t` and `uint16_t`. |
| Int       | ✅        | Compatible mediante `int32_t` and `uint32_t`. |
| Long      | ✅        | Compatible mediante `int64_t` and `uint64_t`. |
| Float     | ✅        | Compatible mediante `float`.                  |
| Double    | ✅        | Compatible mediante `double`.                 |
| Boolean   | ✅        | Compatible mediante `bool`.                   |

#### Codificación de texto

| Provisión | Verificado | Notas                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Compatible mediante `char32_t`.        |
| ASCII     | ✅        | Representable as byte values.        |
| CP1252    | ⚠️        | Requiere mapeo explícito de bytes.      |
| UTF-8     | ✅        | Compatible mediante `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Requiere manejo del orden de bytes.        |

#### Estado de operación

| Provisión | Verificado | Notas                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Can be represented by an enum.           |
| Context   | ✅        | Can be represented by a value.           |
| Operation | ✅        | Can be represented by a value.           |
| Detail    | ✅        | Can be represented by a value.           |
| Result    | ✅        | Can be represented by a struct or class. |

### Verificación de FRELSPEC

#### Colecciones

| Provisión | Verificado | Notas                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Compatible mediante `std::set`.              |
| Map       | ✅        | Compatible mediante `std::map`.              |
| Array     | ✅        | Compatible mediante arrays and `std::array`. |
| File      | ✅        | Compatible mediante file streams.            |
| Stream    | ✅        | Compatible mediante iostreams.               |

#### Memoria

| Provisión | Verificado | Notas                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Addresses are supported.                   |
| Pointer   | ✅        | Los punteros son compatibles.                    |
| Variable  | ✅        | Las variables son compatibles.                   |
| Constant  | ✅        | Compatible mediante `const` and `constexpr`. |

#### Operaciones

| Provisión   | Verificado | Notas                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Representado mediante operaciones de máquina. |
| Procedure   | ✅        | Compatible mediante `void` functions.     |
| Function    | ✅        | Compatible mediante funciones con retorno.  |

#### Hilos de ejecución

| Provisión  | Verificado | Notas                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Compatible mediante ejecución alojada.      |
| Thread     | ✅        | Compatible mediante `std::thread`; C++11+. |
| Dispatcher | ✅        | Compatible mediante async and schedulers.  |

#### Compuestos

| Provisión | Verificado | Notas                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Class members are supported.            |
| Object    | ✅        | Los objetos son compatibles.                  |
| Field     | ✅        | Los campos son compatibles.                   |
| Method    | ✅        | Los métodos son compatibles.                  |
| Property  | ✅        | Get/Set maps can be represented.        |
| Structure | ✅        | Structures are natively supported.      |
| Class     | ✅        | Las clases son compatibles de forma nativa.         |
| Interface | ✅        | Can be represented by abstract classes. |
