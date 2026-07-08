<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimine estas líneas en un pull request después de que la traducción haya sido verificada. -->

# Detalles de revisión

## JavaScript

### Resumen

El lenguaje de programación JavaScript ha sido revisado frente a las especificaciones FDEFSPEC (Rev. 1) y FRELSPEC (Rev. 1) a fecha de 7 de julio de 2026.

#### Declaración de revisión

Aunque JavaScript puede representar algunos conceptos requeridos mediante objetos, funciones, arrays y comportamiento incorporado del lenguaje, estos mecanismos no son suficientes para satisfacer las especificaciones aplicables de CatalystUI a nivel de lenguaje.

Esta revisión evalúa JavaScript en sí, no el ecosistema que lo rodea. Las API de navegador, API de Node.js, API de Deno, API de Bun, API web, TypeScript, WebAssembly, bibliotecas externas y validación personalizada no se tratan como soporte de nivel de lenguaje.

Debido a que JavaScript carece de muchos tipos numéricos escalares de ancho fijo requeridos, no proporciona las codificaciones de texto requeridas como funciones del lenguaje y no define varias construcciones requeridas de sistema, memoria, hilos y compuestos, no creemos que JavaScript proporcione una base lo suficientemente estable para una implementación compatible con CatalystUI sin infraestructura adicional significativa.

Como resultado, JavaScript no ha recibido el estado CatalystUI Verified para lenguajes de programación.

#### Supuestos de revisión

Esta revisión aplica un estándar estricto de nivel de lenguaje. Si una disposición no está explícitamente soportada por JavaScript en sí, se marca como no verificada.

Las API proporcionadas por el host, el comportamiento específico de implementación, las bibliotecas externas, los transpiladores, los sistemas de tipos y la validación personalizada en tiempo de ejecución quedan excluidos de la verificación.

### Advertencias

* JavaScript puede representar muchos valores numéricos mediante `Number`, pero `Number` es un tipo numérico de coma flotante de 64 bits.
* JavaScript proporciona `BigInt`, pero `BigInt` es de ancho arbitrario.
* Los arrays tipados proporcionan vistas de almacenamiento binario, no tipos escalares del lenguaje.
* Las cadenas de JavaScript usan unidades de código UTF-16, no valores explícitos de codificación de texto.
* `const` protege enlaces, no valores de objeto.

### Fallos

* JavaScript no proporciona la mayoría de los tipos numéricos escalares de ancho fijo requeridos.
* JavaScript no proporciona un tipo escalar dedicado de coma flotante de 32 bits.
* JavaScript no proporciona ASCII, CP1252, UTF-8 ni UTF-16LE como codificaciones de texto de nivel de lenguaje.
* JavaScript no proporciona construcciones de archivo o flujo a nivel de lenguaje.
* JavaScript no proporciona construcciones de dirección o puntero a nivel de lenguaje.
* JavaScript no proporciona construcciones de proceso, hilo o despachador a nivel de lenguaje.
* Las propiedades de JavaScript no proporcionan un miembro con clave explícita respaldado por un mapa de accesores Get/Set requerido.
* JavaScript no proporciona estructuras ni interfaces.

### Verificación de FDEFSPEC

#### Numéricos

| Provisión | Verificado | Notas                          |
| --------- | -------- | ------------------------------ |
| Bit       | ❌        | No hay tipo numérico de 1 bit.         |
| Nibble    | ❌        | No hay tipo numérico de 4 bits.         |
| Byte      | ❌        | No hay tipo entero escalar de 8 bits.  |
| Short     | ❌        | No hay tipo entero escalar de 16 bits. |
| Int       | ❌        | No hay tipo entero escalar de 32 bits. |
| Long      | ❌        | No hay tipo entero escalar de 64 bits. |
| Float     | ❌        | No hay tipo flotante escalar de 32 bits.   |
| Double    | ✅        | Compatible mediante `Number`.    |
| Boolean   | ✅        | Compatible mediante `boolean`.   |

#### Codificación de texto

| Provisión | Verificado | Notas                        |
| --------- | -------- | ---------------------------- |
| Codepoint | ❌        | No hay tipo dedicado de punto de código. |
| ASCII     | ❌        | No es de nivel de lenguaje.          |
| CP1252    | ❌        | No es de nivel de lenguaje.          |
| UTF-8     | ❌        | No es de nivel de lenguaje.          |
| UTF-16LE  | ❌        | No es de nivel de lenguaje.          |

#### Estado de operación

| Provisión | Verificado | Notas                           |
| --------- | -------- | ------------------------------- |
| Status    | ⚠️       | Representable, pero no exigible. |
| Context   | ⚠️       | Representable, pero no exigible. |
| Operation | ⚠️       | Representable, pero no exigible. |
| Detail    | ⚠️       | Representable, pero no exigible. |
| Result    | ⚠️       | Requiere validación en tiempo de ejecución.    |

### Verificación de FRELSPEC

#### Colecciones

| Provisión | Verificado | Notas                    |
| --------- | -------- | ------------------------ |
| Set       | ✅        | Compatible mediante `Set`. |
| Map       | ✅        | Compatible mediante `Map`. |
| Array     | ✅        | Los arrays son compatibles.    |
| File      | ❌        | No es de nivel de lenguaje.      |
| Stream    | ❌        | No es de nivel de lenguaje.      |

#### Memoria

| Provisión | Verificado | Notas                           |
| --------- | -------- | ------------------------------- |
| Address   | ❌        | Sin soporte de direcciones.             |
| Pointer   | ❌        | Sin soporte de punteros.             |
| Variable  | ✅        | Las variables son compatibles.        |
| Constant  | ⚠️       | `const` solo protege enlaces. |

#### Operaciones

| Provisión   | Verificado | Notas                            |
| ----------- | -------- | -------------------------------- |
| Instruction | ❌        | No hay tipo de instrucción definido.     |
| Procedure   | ❌        | Las funciones siempre devuelven un valor. |
| Function    | ✅        | Las funciones son compatibles.         |

#### Hilos de ejecución

| Provisión  | Verificado | Notas                       |
| ---------- | -------- | --------------------------- |
| Process    | ❌        | No es de nivel de lenguaje.         |
| Thread     | ⚠️        | Representado mediante agentes. |
| Dispatcher | ❌        | Requiere planificación del host.   |


#### Compuestos

| Provisión | Verificado | Notas                                 |
| --------- | -------- | ------------------------------------- |
| Member    | ✅        | Los miembros de objeto son compatibles.         |
| Object    | ✅        | Los objetos son compatibles.                |
| Field     | ✅        | Las propiedades de datos pueden representar campos. |
| Method    | ✅        | Los métodos son compatibles.                |
| Property  | ❌        | Sin mapa explícito de accesores.             |
| Structure | ❌        | Sin soporte de estructuras.                 |
| Class     | ✅        | La sintaxis de clases es compatible.            |
| Interface | ❌        | Sin soporte de interfaces.                 |
