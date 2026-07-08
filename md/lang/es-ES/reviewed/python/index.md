<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimine estas líneas en un pull request después de que la traducción haya sido verificada. -->

# Detalles de revisión

## Python

### Resumen

El lenguaje de programación Python ha sido revisado frente a las especificaciones FDEFSPEC (Rev. 1) y FRELSPEC (Rev. 1) a fecha de 7 de julio de 2026.

#### Declaración de revisión

Aunque Python puede representar muchos conceptos requeridos mediante tipos incorporados, objetos, funciones, clases, módulos de la biblioteca estándar y validación personalizada, estos mecanismos no son suficientes para satisfacer las especificaciones aplicables de CatalystUI a nivel de lenguaje.

Python proporciona un fuerte soporte para codificación de texto, archivos, flujos, objetos, funciones, clases, propiedades, procesos, hilos y ejecución despachada mediante su comportamiento incorporado y su biblioteca estándar. Sin embargo, Python no proporciona los tipos numéricos escalares de ancho fijo requeridos, no define constantes verdaderas y depende del comportamiento dinámico en tiempo de ejecución para varias construcciones que otros lenguajes verificados pueden expresar de forma más directa.

Debido a esto, no creemos que Python proporcione una base lo suficientemente estable para una implementación compatible con CatalystUI sin infraestructura adicional significativa.

Como resultado, Python no ha recibido el estado CatalystUI Verified para lenguajes de programación.

#### Supuestos de revisión

Esta revisión evalúa Python en sí y su biblioteca estándar incluida.

Los paquetes de terceros, las extensiones específicas de implementación, los módulos nativos opcionales, los verificadores de tipos externos, los transpiladores y los frameworks personalizados de tiempo de ejecución no se tratan como soporte de nivel de lenguaje.

### Advertencias

* Python proporciona enteros de precisión ilimitada, no primitivos enteros de ancho fijo.
* El `float` de Python suele ser de doble precisión, pero no forma una familia diferenciada de ancho fijo.
* Cierto comportamiento de memoria de bajo nivel puede requerir `ctypes` o comportamiento específico de la implementación.
* Las anotaciones de tipo de Python no se aplican en tiempo de ejecución.
* Python admite propiedades, pero el comportamiento de setter puede omitirse.
* Python puede modelar varias estructuras mediante funciones de la biblioteca estándar, pero no como un tipo de estructura nativo.

### Fallos

* Python no proporciona la mayoría de los tipos numéricos escalares de ancho fijo requeridos.
* Python no proporciona un tipo escalar dedicado de coma flotante de 32 bits.
* Python no proporciona constantes verdaderas a nivel de lenguaje.
* Python no define procedimientos separados de las funciones.
* Python no proporciona soporte nativo de punteros.
* Python no proporciona soporte nativo de interfaces.

### Verificación de FDEFSPEC

#### Numéricos

| Provisión | Verificado | Notas                                |
| --------- | -------- | ------------------------------------ |
| Bit       | ❌        | No hay tipo numérico de 1 bit.               |
| Nibble    | ❌        | No hay tipo numérico de 4 bits.               |
| Byte      | ❌        | No hay tipo entero escalar de 8 bits.        |
| Short     | ❌        | No hay tipo entero escalar de 16 bits.       |
| Int       | ❌        | No hay tipo entero escalar de 32 bits.       |
| Long      | ❌        | No hay tipo entero escalar de 64 bits.       |
| Float     | ❌        | No hay tipo flotante escalar de 32 bits.         |
| Double    | ⚠️       | `float` suele ser de doble precisión. |
| Boolean   | ✅        | Compatible mediante `bool`.            |

#### Codificación de texto

| Provisión | Verificado | Notas                            |
| --------- | -------- | -------------------------------- |
| Codepoint | ✅        | Las cadenas usan puntos de código Unicode. |
| ASCII     | ✅        | Códec compatible.                 |
| CP1252    | ✅        | Códec compatible.                 |
| UTF-8     | ✅        | Códec compatible.                 |
| UTF-16LE  | ✅        | Códec compatible.                 |

#### Estado de operación

| Provisión | Verificado | Notas                       |
| --------- | -------- | --------------------------- |
| Status    | ⚠️       | Requiere validación personalizada. |
| Context   | ⚠️       | Requiere validación personalizada. |
| Operation | ⚠️       | Requiere validación personalizada. |
| Detail    | ⚠️       | Requiere validación personalizada. |
| Result    | ⚠️       | Requiere validación personalizada. |

### Verificación de FRELSPEC

#### Colecciones

| Provisión | Verificado | Notas                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Compatible mediante `set`.       |
| Map       | ✅        | Compatible mediante `dict`.      |
| Array     | ✅        | Compatible mediante secuencias.   |
| File      | ✅        | Compatible mediante API de archivos.   |
| Stream    | ✅        | Compatible mediante API de flujos. |

#### Memoria

| Provisión | Verificado | Notas                        |
| --------- | -------- | ---------------------------- |
| Address   | ⚠️       | Solo identidad de objeto.        |
| Pointer   | ❌        | Sin soporte nativo de punteros.   |
| Variable  | ✅        | Los enlaces de nombres son compatibles. |
| Constant  | ❌        | No hay constantes verdaderas.           |

#### Operaciones

| Provisión   | Verificado | Notas                             |
| ----------- | -------- | --------------------------------- |
| Instruction | ⚠️       | El bytecode es de nivel de implementación. |
| Procedure   | ❌        | Las funciones devuelven `None`.          |
| Function    | ✅        | Las funciones son compatibles.          |

#### Hilos de ejecución

| Provisión  | Verificado | Notas                            |
| ---------- | -------- | -------------------------------- |
| Process    | ✅        | Compatible mediante API de procesos.  |
| Thread     | ✅        | Compatible mediante `threading`.   |
| Dispatcher | ✅        | Compatible mediante API de ejecutores. |

#### Compuestos

| Provisión | Verificado | Notas                            |
| --------- | -------- | -------------------------------- |
| Member    | ✅        | Los miembros de objeto son compatibles.    |
| Object    | ✅        | Los objetos son compatibles.           |
| Field     | ✅        | Los atributos pueden representar campos. |
| Method    | ✅        | Los métodos son compatibles.           |
| Property  | ⚠️       | Existe soporte para getter/setter.    |
| Structure | ⚠️       | Solo modelos de la biblioteca estándar.    |
| Class     | ✅        | Las clases son compatibles.           |
| Interface | ❌        | Sin soporte nativo de interfaces.     |
