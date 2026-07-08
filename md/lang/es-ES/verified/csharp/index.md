<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimine estas líneas en un pull request después de que la traducción haya sido verificada. -->

# Detalles de verificación

## C#

### Resumen

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


El lenguaje de programación C# ha sido verificado frente a las especificaciones FDEFSPEC (Rev. 1) y FRELSPEC (Rev. 1) a fecha de 7 de julio de 2026.

#### Declaración de buena fe

Creemos de buena fe que el lenguaje de programación C# puede representar razonablemente los conceptos y disposiciones definidos en las siguientes especificaciones, y que puede usarse para implementar sistemas que cumplan estas especificaciones.

#### Supuestos de revisión

Esta revisión asume compatibilidad con C# moderno y .NET cuando se indican funciones dependientes de la versión.

### Advertencias

* El soporte de CP1252 está disponible mediante el proveedor oficial de páginas de código de .NET, pero puede requerir registrar el proveedor o un paquete adicional según el entorno de ejecución de destino.
* El comportamiento de punteros unsafe puede requerir autorización unsafe explícita.

### Fallos

* No se encontraron fallos conocidos de FDEFSPEC o FRELSPEC durante esta verificación.

### Verificación de FDEFSPEC

#### Numéricos

| Provisión | Verificado | Notas                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | No hay numérico de 1 bit; ampliar.                |
| Nibble    | ⚠️       | No hay numérico de 4 bits; ampliar.                |
| Byte      | ✅        | Compatible mediante `byte` y `sbyte`.   |
| Short     | ✅        | Compatible mediante `short` y `ushort`. |
| Int       | ✅        | Compatible mediante `int` y `uint`.     |
| Long      | ✅        | Compatible mediante `long` y `ulong`.   |
| Float     | ✅        | Compatible mediante `float`.              |
| Double    | ✅        | Compatible mediante `double`.             |
| Boolean   | ✅        | Compatible mediante `bool`.               |

#### Codificación de texto

| Provisión | Verificado | Notas                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | Compatible mediante numerics and `Rune`. |
| ASCII     | ✅        | Compatible mediante `Encoding.ASCII`.    |
| CP1252    | ⚠️       | Requiere proveedor de páginas de código.          |
| UTF-8     | ✅        | Compatible mediante `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | Compatible mediante `Encoding.Unicode`.  |

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

| Provisión | Verificado | Notas                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Compatible mediante `HashSet<T>`.              |
| Map       | ✅        | Compatible mediante `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Native arrays are supported.                 |
| File      | ✅        | Compatible mediante API de archivos.                 |
| Stream    | ✅        | Compatible mediante `Stream`.                  |

#### Memoria

| Provisión | Verificado | Notas                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Compatible mediante references and pointers. |
| Pointer   | ✅        | Compatible mediante unsafe pointers.         |
| Variable  | ✅        | Las variables son compatibles.                   |
| Constant  | ✅        | Compatible mediante `const` and `readonly`.  |

#### Operaciones

| Provisión   | Verificado | Notas                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Representado mediante IL y operaciones. |
| Procedure   | ✅        | Compatible mediante `void` methods.      |
| Function    | ✅        | Compatible mediante métodos con retorno.   |

#### Hilos de ejecución

| Provisión  | Verificado | Notas                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Compatible mediante application and `Process` APIs. |
| Thread     | ✅        | Compatible mediante `Thread`.                       |
| Dispatcher | ✅        | Compatible mediante tasks and schedulers.           |

#### Compuestos

| Provisión | Verificado | Notas                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Type members are supported.        |
| Object    | ✅        | Los objetos son compatibles.             |
| Field     | ✅        | Los campos son compatibles.              |
| Method    | ✅        | Los métodos son compatibles.             |
| Property  | ✅        | Properties are natively supported. |
| Structure | ✅        | Structures are natively supported. |
| Class     | ✅        | Las clases son compatibles.             |
| Interface | ✅        | Interfaces are supported.          |
