<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimina estas líneas en un pull request después de verificar la traducción. -->

# Detalles de verificación

## C#

### Resumen

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


El lenguaje de programación C# ha sido verificado frente a las especificaciones FDEFSPEC (Rev. 1) y FRELSPEC (Rev. 1) con fecha del 7 de julio de 2026.

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
| Codepoint | ✅        | Compatible mediante numéricos y `Rune`. |
| ASCII     | ✅        | Compatible mediante `Encoding.ASCII`.    |
| CP1252    | ⚠️       | Requiere proveedor de páginas de código.          |
| UTF-8     | ✅        | Compatible mediante `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | Compatible mediante `Encoding.Unicode`.  |

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

| Provisión | Verificado | Notas                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Compatible mediante `HashSet<T>`.              |
| Map       | ✅        | Compatible mediante `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Los arrays nativos son compatibles.                 |
| File      | ✅        | Compatible mediante API de archivos.                 |
| Stream    | ✅        | Compatible mediante `Stream`.                  |

#### Memoria

| Provisión | Verificado | Notas                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Compatible mediante referencias y punteros. |
| Pointer   | ✅        | Compatible mediante punteros unsafe.         |
| Variable  | ✅        | Las variables son compatibles.                   |
| Constant  | ✅        | Compatible mediante `const` y `readonly`.  |

#### Operaciones

| Provisión   | Verificado | Notas                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Representado mediante IL y operaciones. |
| Procedure   | ✅        | Compatible mediante métodos `void`.      |
| Function    | ✅        | Compatible mediante métodos con retorno.   |

#### Hilos de ejecución

| Provisión  | Verificado | Notas                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Compatible mediante la aplicación y las API de `Process`. |
| Thread     | ✅        | Compatible mediante `Thread`.                       |
| Dispatcher | ✅        | Compatible mediante tareas y planificadores.           |

#### Compuestos

| Provisión | Verificado | Notas                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Los miembros de tipo son compatibles.        |
| Object    | ✅        | Los objetos son compatibles.             |
| Field     | ✅        | Los campos son compatibles.              |
| Method    | ✅        | Los métodos son compatibles.             |
| Property  | ✅        | Las propiedades son compatibles de forma nativa. |
| Structure | ✅        | Las estructuras son compatibles de forma nativa. |
| Class     | ✅        | Las clases son compatibles.             |
| Interface | ✅        | Las interfaces son compatibles.          |
