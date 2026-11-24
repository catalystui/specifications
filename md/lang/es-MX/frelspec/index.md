<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimine estas líneas en un pull request después de que la traducción haya sido verificada. -->

# FRELSPEC

<br/>

> **Especificación de relaciones fundamentales**<br/>
> Revisión 2.1<br/>
> 24 de noviembre de 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Todos los derechos reservados.<br/>
> <br/>
> Las definiciones y los conceptos aquí presentados describen construcciones matemáticas fundamentales y pueden reformularse libremente.

## Introducción

La **Especificación de relaciones fundamentales (FRELSPEC)** establece las estructuras relacionales centrales que sustentan el ecosistema CatalystUI. Su propósito es proporcionar una comprensión unificada de cómo se relacionan la memoria, las colecciones, las operaciones y los compuestos en la documentación, las especificaciones, las implementaciones y las revisiones de verificación, garantizando coherencia, claridad y alineación.

Al definir las relaciones entre conceptos fundamentales de forma precisa y estable, FRELSPEC proporciona un punto de referencia común para especificaciones de nivel superior, permitiendo que cada implementación establezca sus propias reglas y comportamientos. Así, desarrolladores, revisores e implementadores pueden razonar desde la misma base al determinar si un lenguaje, servicio, framework o sistema puede representar las construcciones relacionales necesarias para ajustarse a la especificación.

> [!IMPORTANT]
>
> Expresamos las definiciones mediante una forma derivada de la notación de [teoría de conjuntos](https://en.wikipedia.org/wiki/Set_theory). Este enfoque proporciona definiciones precisas e inequívocas sin perder claridad ni concisión. Las estructuramos para facilitar la consulta, una interpretación clara y una jerarquía conceptual coherente.

## Tabla de contenidos

- [FRELSPEC](#frelspec)
  - [Introducción](#introducción)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Revisiones](#revisiones)
    - [Revisión 2.1](#revisión-21)
    - [Revisión 2](#revisión-2)
  - [Memoria](#memoria)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Colecciones](#colecciones)
    - [Set](#set)
      - [Set()](#set-1)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [Operaciones](#operaciones)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [Hilos de ejecución](#hilos-de-ejecución)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Compuestos](#compuestos)
    - [Member](#member)
    - [Object](#object)
      - [Object(k)](#objectk)
    - [Field](#field)
      - [Field(o,k)](#fieldok)
    - [Method](#method)
      - [Method(o,k)](#methodok)
    - [Property](#property)
      - [Property(o,k)](#propertyok)
      - [Get(o,k)](#getok)
      - [Set(o,k)](#setok)
    - [Structure](#structure)
      - [Structure(s,k)](#structuresk)
    - [Class](#class)
      - [Class(c,a)](#classca)
    - [Interface](#interface)
      - [Interface(r,o)](#interfacero)

## Revisiones

### Revisión 2.1

**24 de noviembre de 2026**

Refinamos la definición de File para establecer la resolución de datos regida por metadatos y redefinimos Stream como un mecanismo independiente de generación o recuperación secuencial de datos. Estos cambios permiten que los flujos representen secuencias finitas o infinitas sin imponer restricciones adicionales a otras colecciones.

### Revisión 2

**21 de noviembre de 2026**

Identificamos incoherencias en la representación de la memoria y los valores almacenados mediante bytes y arreglos de bytes. Establecimos Word como representación fundamental de la memoria, unificando las relaciones entre Memoria, Operaciones y Compuestos.

Detectamos incoherencias en la indexación de arreglos y las relaciones entre colecciones. Estandarizamos los índices finitos y contiguos y aclaramos las relaciones entre Array, File y Stream.

Identificamos redundancias y ambigüedades en las relaciones de ejecución y composición. Refinamos los procedimientos, funciones, despachadores y relaciones entre objetos para resolverlas, preservando la independencia de implementación.

## Memoria

### Word

Una palabra es cualquier secuencia de bits $w \in \mathrm{Bit}^n$ almacenada en memoria, tal que $n \in \mathbb{N}^+$.

### Address

Una dirección es cualquier palabra $a \in A$, donde $A$ es un conjunto de palabras, tal que $a$ identifica de forma única una ubicación dentro de una estructura de memoria especificada.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

Un puntero es cualquier función $f_p : \{a\} \to B$ tal que $a \in A$ es una dirección y $B$ es un conjunto de palabras, donde cada aplicación de $f_p$ evalúa la palabra almacenada en la ubicación de memoria identificada por $a$.

#### Pointer()

> Sea $f_m : A \to B$ un mapa de memoria.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Una variable es cualquier función $f_v : \{k\} \to B$ tal que $k$ es una clave y $B$ es un conjunto de palabras, donde la variable extiende un puntero al vincular una clave a una dirección y evaluar la palabra almacenada en dicha dirección.

#### Variable(k)

> Sea $f_b : \{k\} \to \{a\}$ la función de vinculación de la variable.
>
> Sea $f_p : \{a\} \to B$ un puntero.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Una constante es cualquier variable $f_c : \{k\} \to B$ tal que $k$ es una clave y $B$ es un conjunto de palabras, donde la palabra asociada a $k$ no puede cambiarse después de asignarla.

#### Constant(k)

> Sea $b_0 \in B$ la palabra asignada a $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ después de asignar $b_0$.

## Colecciones

### Set

Un conjunto es cualquier colección finita y no ordenada de palabras distintas.

#### Set()

> Sea $B$ un conjunto de palabras.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

Un mapa es cualquier función $f_m : K \to V$ tal que $K$ es un conjunto de claves y $V$ es un conjunto de valores, donde cada clave se asocia exactamente a un valor.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Un arreglo es cualquier función $f_a : I \to V$ tal que $I \subseteq \mathbb{N}$ es un conjunto finito y contiguo de índices enteros y $V$ es un conjunto de palabras, donde cada índice identifica exactamente un valor.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Un archivo es cualquier tupla $(f_m,d)$ tal que $d$ es un arreglo de palabras y $f_m : I \times \{d\} \to \mathrm{Array}$ es una función de metadatos representada por un arreglo de palabras, donde $I$ es un conjunto finito y contiguo de índices enteros y $f_m$ determina cómo se resuelven los datos a partir de $d$.

#### File(i)

> Sea $(f_m,d)$ un archivo.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

Un flujo es cualquier función $f_s$ tal que cada aplicación de $f_s$ produce el siguiente fragmento $c$ de una secuencia finita o infinita, donde $f_s$ establece un mecanismo de generación o recuperación secuencial de datos.

#### Stream()

> Sea $f_c : K \to C$ una función de resolución de fragmentos, donde $K \subseteq \mathbb{N}$ es un conjunto contiguo de índices enteros y $C$ es un conjunto de fragmentos.
>
> Sea $k \in K$ el índice del siguiente fragmento.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$, avanzando $k$ después de cada aplicación.

## Operaciones

### Instruction

Una instrucción es cualquier palabra o tupla finita de palabras $i \in B$ tal que $B$ es un conjunto de palabras o tuplas finitas de palabras, donde cada instrucción representa una única operación computacional que debe realizarse.

### Procedure

Un procedimiento es cualquier variable $f_{proc} : \{k\} \to B$ tal que $f_{proc}(k)$ representa un arreglo de instrucciones $f_a : I \to V$, donde ejecutar el procedimiento realiza cada instrucción en su orden indexado.

#### Procedure(k)

> $\mathrm{Procedure}(k)$ es la ejecución de cada $f_a(i)$ en orden ascendente de $i \in I$.

### Function

Una función es cualquier procedimiento $f_{func} : \{k\} \to B$ tal que su ejecución devuelve una dirección $a_r \in A$ que identifica la palabra resultante o la primera palabra de un arreglo de palabras que representa el resultado.

#### Function(k)

> Sea $f_m : A \to B$ un mapa de memoria, donde $a_r \in A$ identifica la palabra resultante $r \in B$.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## Hilos de ejecución

### Process

Un proceso es cualquier flujo de ejecución acotado que acepta una entrada, ejecuta uno o más procedimientos o funciones y produce una salida, donde el proceso representa una unidad diferenciada de transformación dentro de un sistema.

### Thread

Un hilo es cualquier flujo de ejecución contenido en un proceso, donde el hilo proporciona una vía por la que pueden ejecutarse procedimientos o funciones pertenecientes a ese proceso.

#### Thread(p)

> Sea $p$ un proceso.
>
> Sea $(w_0, \dots, w_n)$ una tupla finita de procedimientos o funciones pertenecientes a $p$.
>
> $\mathrm{Thread}(p)$ es la ejecución de cada $w_j$ en orden ascendente de $j$ dentro de $p$.

### Dispatcher

Un despachador es cualquier tupla $(t,W,f_d)$ tal que $t$ es un hilo, $W$ es un conjunto de procedimientos o funciones aceptados como trabajo y $f_d$ es una regla de despacho que selecciona trabajo de $W$, donde el despachador hace que el trabajo seleccionado se ejecute en $t$ según la regla de despacho.

#### Dispatcher(t)

> Sea $t$ un hilo.
>
> Sea $W$ un conjunto de procedimientos o funciones aceptados por el despachador, donde $\forall w \in W$, $w$ es un procedimiento o función.
>
> Sea $f_d : \mathcal{P}^+(W) \to W$ una regla de despacho que selecciona trabajo de un subconjunto no vacío del trabajo aceptado.
>
> $\mathrm{Dispatcher}(t)$ es la ejecución de cada $f_d(W')$ seleccionado en $t$, donde $W' \subseteq W$, $W' \neq \varnothing$ y $f_d(W') \in W'$.

## Compuestos

### Member

Un miembro es cualquier elemento $m \in M$ tal que $M$ es un conjunto de elementos y $f_o : K \to M$ es el mapa de miembros de un objeto, donde $m = f_o(k)$ para alguna clave $k \in K$.

### Object

Un objeto es cualquier tupla $(a,K,f_o)$ tal que $a \in A$ es una dirección, $K$ es un conjunto de claves y $f_o : K \to M$ es un mapa de miembros, donde $M$ es un conjunto de elementos, permitiendo al objeto representar un compuesto direccionable cuyos miembros se asignan a claves mediante $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Un campo es cualquier tupla $(o,k,m)$ tal que $o = (a,K,f_o)$ es un objeto, $k \in K$ es una clave y $m = f_o(k)$ es un miembro, donde el campo representa un miembro identificado por clave y resuelto a partir del mapa de miembros del objeto.

#### Field(o,k)

> Sea $o = (a,K,f_o)$ un objeto.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

Un método es cualquier campo $(o,k,m)$ tal que $m$ es un procedimiento o función, donde el método representa un miembro ejecutable de un objeto identificado por clave.

#### Method(o,k)

> Sea $(o,k,m)$ un campo.
>
> $\mathrm{Method}(o,k) = (o,k,m)$, donde $m$ es un procedimiento o función.

### Property

Una propiedad es cualquier campo $(o,k,m)$ tal que $m = (X,f_a)$ es un mapa de accesores, $X = \{\mathrm{Get}, \mathrm{Set}\}$, y $f_a : X \to M$ asigna cada accesor a un miembro, donde $f_a(\mathrm{Get})$ es una función y $f_a(\mathrm{Set})$ es un procedimiento, permitiendo que la propiedad defina tanto la recuperación como la asignación de un miembro identificado por clave.

#### Property(o,k)

> Sea $(o,k,m)$ un campo, donde $m = (X,f_a)$ es un mapa de accesores.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> Sea $(o,k,(X,f_a))$ una propiedad.
>
> $\mathrm{Get}(o,k)$ es la aplicación de $f_a(\mathrm{Get})$.

#### Set(o,k)

> Sea $(o,k,(X,f_a))$ una propiedad.
>
> $\mathrm{Set}(o,k)$ es la aplicación de $f_a(\mathrm{Set})$.

### Structure

Una estructura (a menudo abreviada como `struct`) es cualquier objeto $s = (a,K,f_s)$ tal que $K$ es un conjunto finito de claves y $f_s : K \to M$ es un mapa de miembros cuyas claves no pueden cambiarse después de asignar la estructura, donde la estructura es un objeto especializado cuya disposición de miembros identificados por clave es fija.

#### Structure(s,k)

> Sea $s = (a,K,f_s)$ una estructura.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Una clase es cualquier objeto $c = (a_c,K_c,f_c)$ tal que $K_c$ es un conjunto finito de claves y $f_c : K_c \to M$ es un mapa de definiciones de miembros, donde la clase es un objeto especializado cuyos miembros identificados por clave definen la disposición de miembros utilizada para producir otros objetos.

#### Class(c,a)

> Sea $c = (a_c,K_c,f_c)$ una clase.
>
> Sea $a \in A$ una dirección asignada a un objeto producido a partir de $c$.
>
> Sea $f_o : K_c \to M$ un mapa de miembros que sigue las definiciones de $f_c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

Una interfaz es cualquier objeto $r = (a_r,K_r,f_r)$ tal que $K_r$ es un conjunto finito de claves y $f_r : K_r \to M$ es un mapa de requisitos de miembros, donde la interfaz es un objeto especializado cuyos miembros identificados por clave definen los miembros que otro objeto debe proporcionar.

#### Interface(r,o)

> Sea $r = (a_r,K_r,f_r)$ una interfaz.
>
> Sea $o = (a,K,f_o)$ un objeto.
>
> Sea $f_v : M \times M \to \{0,1\}$ una regla de validación que determina si un miembro satisface los requisitos de otro miembro.
>
> $\mathrm{Interface}(r,o)$ se cumple cuando $K_r \subseteq K$ y $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$.
