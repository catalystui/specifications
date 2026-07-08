<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimine estas líneas en un pull request después de que la traducción haya sido verificada. -->

# FDEFSPEC

<br/>

> **Especificación de definiciones fundamentales**<br/>
> Revisión 1<br/>
> 23 de marzo de 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Todos los derechos reservados.<br/>
> <br/>
> Las definiciones y conceptos presentados aquí describen construcciones matemáticas fundamentales y pueden ser reformulados libremente.

## Introducción

La **Especificación de definiciones fundamentales (FDEFSPEC)** establece los conceptos centrales y la terminología que sustentan el ecosistema CatalystUI. Su propósito es proporcionar una comprensión unificada de estos conceptos en la documentación, las especificaciones, las implementaciones y las revisiones de verificación, asegurando coherencia, claridad y alineación.

Al definir términos clave y relaciones en una forma precisa y estable, FDEFSPEC proporciona un punto de referencia común para especificaciones de nivel superior. Esto permite que desarrolladores, revisores e implementadores razonen desde la misma base al determinar si un lenguaje, servicio, framework o sistema puede considerarse dentro de la especificación.

> [!IMPORTANT]
>
> Expresamos las definiciones mediante una forma derivada de la notación de [teoría de conjuntos](https://en.wikipedia.org/wiki/Set_theory). Este enfoque proporciona definiciones precisas e inequívocas mientras mantiene claridad y concisión. Estructuramos estas definiciones para facilitar la consulta, una interpretación clara y una jerarquía conceptual coherente.

## Tabla de contenidos

- [FDEFSPEC](#fdefspec)
  - [Introducción](#introducción)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Numéricos](#numéricos)
    - [Bit](#bit)
    - [Nibble](#nibble)
      - [Nibble()](#nibble-1)
    - [Byte](#byte)
      - [Byte()](#byte-1)
      - [SByte()](#sbyte)
    - [Short](#short)
      - [Short()](#short-1)
      - [UShort()](#ushort)
    - [Int](#int)
      - [Int()](#int-1)
      - [UInt()](#uint)
    - [Long](#long)
      - [Long()](#long-1)
      - [ULong()](#ulong)
    - [Single](#single)
      - [Single()](#single-1)
    - [Double](#double)
      - [Double()](#double-1)
    - [Boolean](#boolean)
      - [Boolean()](#boolean-1)
  - [Codificación de texto](#codificación-de-texto)
    - [Text Encoding](#text-encoding-1)
      - [Text Encoding()](#text-encoding-2)
    - [Codepoint](#codepoint)
      - [Codepoint()](#codepoint-1)
    - [ASCII Code Unit](#ascii-code-unit)
      - [ASCII Code Unit()](#ascii-code-unit-1)
      - [ASCII()](#ascii)
    - [CP1252 Code Unit](#cp1252-code-unit)
      - [CP1252 Code Unit()](#cp1252-code-unit-1)
      - [CP1252()](#cp1252)
    - [UTF-8 Code Unit](#utf-8-code-unit)
      - [UTF-8 Code Unit()](#utf-8-code-unit-1)
      - [UTF-8()](#utf-8)
    - [UTF-16LE Code Unit](#utf-16le-code-unit)
      - [UTF-16LE Code Unit()](#utf-16le-code-unit-1)
      - [UTF-16LE()](#utf-16le)
  - [Estado de operación](#estado-de-operación)
    - [Status Code](#status-code)
      - [Status Code()](#status-code-1)
      - [Status Code Level()](#status-code-level)
      - [Status Code Definition()](#status-code-definition)
        - [Success](#success)
        - [Warning](#warning)
        - [Error](#error)
        - [Fatal](#fatal)
    - [Context Code](#context-code)
      - [Context Code()](#context-code-1)
    - [Operation Code](#operation-code)
      - [Operation Code()](#operation-code-1)
    - [Detail Code](#detail-code)
      - [Detail Code()](#detail-code-1)
    - [Result](#result)
      - [Result()](#result-1)

## Numéricos

### Bit

Un bit es cualquier $b \in \{0,1\}$.

### Nibble

Un nibble es cualquier $(b_0,\dots,b_3)$ tal que, para todo $i \in \{0,\dots,3\}$, $b_i \in \mathrm{Bit}$.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

Un byte es cualquier $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

Un short es cualquier $(b_0,\dots,b_{15})$ tal que, para todo $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

Un entero es cualquier $(b_0,\dots,b_{31})$ tal que, para todo $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

Un long es cualquier $(b_0,\dots,b_{63})$ tal que, para todo $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

Un single es cualquier $(b_0,\dots,b_{31})$ tal que, para todo $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Single()

La siguiente definición se ajusta al estándar IEEE 754 para la representación de coma flotante de precisión simple. Define cómo se interpreta una secuencia binaria de 32 bits como un número de coma flotante, incluidos los casos especiales de cero, infinito y NaN (Not a Number).

> Sea $s = b_0$
>
> Sea $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Sea $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

Un double es cualquier $(b_0,\dots,b_{63})$ tal que, para todo $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Double()

La siguiente definición se ajusta al estándar IEEE 754 para la representación de coma flotante de doble precisión. Define cómo se interpreta una secuencia binaria de 64 bits como un número de coma flotante, incluidos los casos especiales de cero, infinito y NaN (Not a Number).

> Sea $s = b_0$
>
> Sea $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Sea $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

Un booleano es cualquier $b \in \{0,1\}$.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## Codificación de texto

### Codificación de texto

Una codificación de texto se define como el siguiente conjunto:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Codificación de texto()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Un punto de código Unicode es cualquier $e \in \mathbb{Z}$ tal que $0 \leq e \leq 0x10FFFF$.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

Una unidad de código ASCII es cualquier $(b_0,\dots,b_6)$ tal que, para todo $i \in \{0,\dots,6\}$, $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

Es habitual representar una unidad de código ASCII como un byte añadiendo un bit cero inicial, por razones de rendimiento y compatibilidad. En esos casos, la unidad de código ASCII se representa como:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

En caso contrario:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

En el caso de este teorema, ambas definiciones son representaciones aceptables de una unidad de código ASCII. Por coherencia, usaremos la primera definición al representar unidades de código ASCII como bytes, y la segunda al representarlas como secuencias de 7 bits.

#### ASCII()

ASCII es una tupla finita terminada en nulo $(u_0, \dots, u_k, u_{k+1})$ tal que:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is an ASCII code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

Se dice que la secuencia está terminada en nulo.

### CP1252 Code Unit

Una unidad de código CP1252 es cualquier $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 es una tupla finita terminada en nulo $(u_0, \dots, u_k, u_{k+1})$ tal que:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a CP1252 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

Se dice que la secuencia está terminada en nulo.

### UTF-8 Code Unit

Una unidad de código UTF-8 es cualquier $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 es una tupla finita terminada en nulo $(u_0, \dots, u_k, u_{k+1})$ tal que:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-8 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

Se dice que la secuencia está terminada en nulo.

### UTF-16LE Code Unit

Una unidad de código UTF-16LE es cualquier $(b_0,\dots,b_{15})$ tal que, para todo $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE es una tupla finita terminada en nulo $(u_0, \dots, u_k, u_{k+1})$ tal que:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-16LE code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

Se dice que la secuencia está terminada en nulo.

## Estado de operación

### Código de estado

Un código de estado es cualquier $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

Un nivel de código de estado se define como el siguiente conjunto:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Código de estado()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Nivel de código de estado()

El conjunto de valores de código de estado es el rango $[0, 255]$, que se divide en cuatro niveles:

> Let $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Definición de código de estado()

Todos los códigos de estado tienen definiciones explícitas. Cualquier código de estado no incluido en la siguiente lista queda reservado para uso futuro y su significado no está definido. El nivel de un código de estado se determina mediante $\mathrm{Status\ Code\ Level}(s)$.

En la siguiente lista, la entrada $s$ se representa como un valor hexadecimal para facilitar la lectura. Cada código de estado definido especifica su nivel, categoría, subcategoría, descripción y detalle correspondientes, cuando corresponda.

Esta lista puede ampliarse a medida que se definan nuevos códigos de estado. Cualquier código de estado nuevo no debe entrar en conflicto con códigos existentes y debe tener un significado claramente documentado.

Para transmitir información no representada por un código de estado definido, debe utilizarse el código de contexto, el código de operación o el código de detalle.

##### Éxito

| Código | Nivel | Categoría | Descripción | Detalle |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | La operación se completó correctamente. | |
| `0x01` | SUCCESS | NOOP | La operación se completó correctamente sin realizar ninguna acción. | |

##### Advertencia

| Código | Nivel | Categoría | Descripción | Detalle |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | La operación se completó, pero el resultado puede ser inesperado o no deseado. | |
| `0x41` | WARNING | PARTIAL | La operación se completó, pero solo parcialmente. La salida puede estar incompleta. | |
| `0x42` | WARNING | DEPRECATED | La operación se completó, pero usó una función o comportamiento obsoleto. La operación puede dejar de funcionar en el futuro. | |

##### Error

| Código | Nivel | Categoría | Descripción | Detalle |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | La operación falló debido a un error recuperable. | |
| `0x81` | ERROR | INVALID_ARGUMENT | La operación falló. Un argumento no era válido o estaba fuera de rango. | El índice del argumento no válido, empezando en 0 de izquierda a derecha en la firma de la función. |
| `0x82` | ERROR | INVALID_STATE | La operación falló. El sistema está en un estado incoherente, corrupto o de otro modo no válido. | |
| `0x83` | ERROR | MALFORMED_INPUT | La operación falló. Una entrada requerida estaba mal formada o contenía datos no válidos. | |
| `0x84` | ERROR | ACCESS_DENIED | La operación falló porque un recurso requerido denegó el acceso. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | La operación falló porque la función o el comportamiento solicitado aún no está implementado. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | La operación falló porque el sistema o la configuración de destino no admite la función solicitada. | |
| `0x87` | ERROR | TIMEOUT | La operación falló porque se produjo un timeout requerido antes de completarse. | |
| `0x88` | ERROR | NOT_FOUND | La operación falló porque un recurso requerido no existe. | |
| `0x89` | ERROR | INTERRUPTED | La operación falló porque un evento externo la interrumpió. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | La operación falló porque falló una dependencia requerida. | El valor `STATUS_CODE` de la dependencia. Se anima a los llamadores (aunque no es obligatorio) a identificar la dependencia que falla mediante el campo `OP_CODE`. |
| `0x90` | ERROR | BUFFER_OVERFLOW | La operación falló. Un búfer era demasiado pequeño para contener los datos requeridos. | |
| `0x91` | ERROR | ALLOCATION_FAILED | La operación falló. Una solicitud de asignación de memoria no tuvo éxito. | |
| `0xA0` | ERROR | IO_ERROR | La operación falló. Se produjo un error de E/S durante la operación. | |

##### Fatal

| Código | Nivel | Categoría | Descripción | Detalle |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | La operación falló debido a un error irrecuperable. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | La operación falló porque el sistema violó una invariante fundamental, lo que indica un error lógico crítico o corrupción de datos. | |

### Código de contexto

Un código de contexto es cualquier $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Código de contexto()

Un valor de código de contexto representa información contextual adicional sobre una operación completada, según lo definido por la operación asociada; debe ser cero cuando el nivel del código de estado es $\mathrm{Success}$ y, en caso contrario, queda definido por la implementación.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Código de operación

Un código de operación es cualquier $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Código de operación()

Un valor de código de operación representa la operación asociada con un resultado. Su significado lo definen la operación correspondiente y su documentación. Los valores no definidos se consideran desconocidos.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Código de detalle

Un código de detalle es cualquier $(b_0,\dots,b_7)$ tal que, para todo $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Código de detalle()

Un valor de código de detalle representa información adicional sobre una operación completada; su significado se define por el código de estado, contexto u operación asociado (en ese orden), y en caso contrario es desconocido.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Resultado

> [!TIP]
>
> Un valor de resultado puede representarse como un entero de 32 bits. En orden de bytes big-endian, el valor aparece como `0xSSCCOODD`, donde `SS`, `CC`, `OO` y `DD` corresponden al código de estado, código de contexto, código de operación y código de detalle, respectivamente. En orden de bytes little-endian, el mismo valor aparece como `0xDDOOCCSS`. Puede usarse cualquiera de los dos órdenes de bytes, siempre que se aplique de forma coherente y se documente.

Un resultado es cualquier $(b_0,\dots,b_{31})$ tal que, para todo $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

Un resultado se divide en cuatro bytes ordenados:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

donde $s$, $c$, $o$ y $d$ son los componentes del resultado.

#### Resultadoado()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
