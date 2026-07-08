<!-- Esta traducción fue generada por ChatGPT y debe ser revisada por un traductor humano. -->
<!-- Elimine estas líneas en un pull request después de que la traducción haya sido verificada. -->

# FRELSPEC

<br/>

> **Especificación de relaciones fundamentales**<br/>
> Revisión 1<br/>
> 7 de julio de 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Todos los derechos reservados.<br/>
> <br/>
> Las definiciones y conceptos presentados aquí describen construcciones matemáticas fundamentales y pueden ser reformulados libremente.

## Introducción

La **Especificación de relaciones fundamentales (FRELSPEC)** establece las estructuras relacionales centrales que sustentan el ecosistema CatalystUI. Su propósito es proporcionar una comprensión unificada de cómo se asocian valores, memoria, operaciones y compuestos en la documentación, las especificaciones, las implementaciones y las revisiones de verificación, asegurando coherencia, claridad y alineación.

Al definir relaciones entre conceptos fundamentales en una forma precisa y estable, FRELSPEC proporciona un punto de referencia común para especificaciones de nivel superior. Esto permite que desarrolladores, revisores e implementadores razonen desde la misma base al determinar si un lenguaje, servicio, framework o sistema puede representar las construcciones relacionales requeridas para considerarse dentro de la especificación.

> [!IMPORTANT]
>
> Expresamos las definiciones mediante una forma derivada de la notación de [teoría de conjuntos](https://en.wikipedia.org/wiki/Set_theory). Este enfoque proporciona definiciones precisas e inequívocas mientras mantiene claridad y concisión. Estructuramos estas definiciones para facilitar la consulta, una interpretación clara y una jerarquía conceptual coherente.

## Tabla de contenidos

- [FRELSPEC](#frelspec)
  - [Introducción](#introducción)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Colecciones](#colecciones)
    - [Set](#set)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [Memoria](#memoria)
    - [Address](#address)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
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
      - [Field(k)](#fieldk)
    - [Method](#method)
      - [Method(k)](#methodk)
    - [Property](#property)
      - [Property(k)](#propertyk)
      - [Get(k)](#getk)
      - [Set(k)](#setk)
    - [Structure](#structure)
      - [Structure(k)](#structurek)
    - [Class](#class)
      - [Class(a)](#classa)
    - [Interface](#interface)
      - [Interface(o)](#interfaceo)

## Colecciones

### Conjunto

Un conjunto es cualquier colección de elementos distintos.

### Mapa

Un mapa es cualquier función $f_m : K \to V$ tal que $K$ es un conjunto de claves y $V$ es un conjunto de valores.

#### Mapa(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Un array es cualquier función $f_a : I \to V$ tal que $I \subset \mathbb{N}$, $I$ es un conjunto finito y contiguo de enteros, y $V$ es un conjunto de valores.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### Archivo

Un archivo es cualquier función $f_f : I \to B$ tal que $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ es un conjunto finito y contiguo de enteros, y $B$ es un conjunto de bytes, donde $f_f$ se origina a partir de un mecanismo de almacenamiento persistente de datos.

#### Archivo(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Flujo

Un flujo es cualquier función $f_s$ tal que cada aplicación de $f_s$ produce el siguiente fragmento $f_c : I \to B$ en una secuencia de bytes, donde $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ es un conjunto finito y contiguo de enteros, $B$ es un conjunto de bytes, y $f_s$ se origina a partir de un mecanismo de generación o recuperación secuencial de datos.

#### Flujo()

> Sea $c_k : I_k \to B$ el fragmento devuelto por la $k$-ésima aplicación de $f_s$.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ en la $k$-ésima aplicación.

## Memoria

### Dirección

Una dirección es cualquier elemento $a \in A$ tal que $A$ es un conjunto de direcciones, donde cada dirección $a$ identifica de forma única una ubicación en una estructura de memoria.

### Puntero

Un puntero es cualquier función $f_p : \{a\} \to B$ tal que $a \in A$ es una dirección y $B$ es un conjunto de arrays de bytes, donde cada aplicación de $f_p$ evalúa el array de bytes almacenado en la ubicación de memoria identificada por su dirección enlazada.

#### Puntero()

> Sea $f_m : A \to B$ un mapa de memoria.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Una variable es cualquier función $f_v : \{k\} \to B$ tal que $k$ es una clave y $B$ es un conjunto de arrays de bytes, donde la variable extiende un puntero al enlazar una clave con una dirección y evaluar el array de bytes almacenado en la ubicación de memoria identificada por esa dirección.

#### Variable(k)

> Sea $f_b : \{k\} \to \{a\}$ la función de enlace de la variable.
>
> Sea $f_p : \{a\} \to B$ un puntero.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constante

Una constante es cualquier variable $f_c : \{k\} \to B$ tal que $k$ es una clave y $B$ es un conjunto de arrays de bytes, donde el array de bytes asociado con $k$ no puede cambiarse después de ser asignado.

#### Constante(k)

> Sea $b_0 \in B$ el array de bytes asignado a $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ después de que se asigne $b_0$.


## Operaciones

### Instrucción

Una instrucción es cualquier array de bytes $i \in B$ tal que $B$ es un conjunto de arrays de bytes, donde cada instrucción representa una única operación computacional que debe realizarse.

### Procedimiento

Un procedimiento es cualquier variable $f_{proc} : \{k\} \to B$ tal que $k$ es una clave y $B$ es un conjunto de arrays de bytes, donde cada aplicación del procedimiento evalúa el array de bytes asociado con $k$ como una secuencia ordenada finita de instrucciones y ejecuta esas instrucciones en su orden representado sin definir un valor devuelto.

#### Procedimiento(k)

> Sea $b \in B$ tal que $f_{proc}(k) = b$.
>
> Sea $(i_0,\dots,i_n)$ la secuencia ordenada finita de instrucciones representada por $b$, donde $\forall j \in \{0,\dots,n\}, i_j$ es una instrucción.
>
> $\mathrm{Procedure}(k)$ es la ejecución de cada $i_j$ en orden ascendente de $j$.

### Función

Una función es cualquier procedimiento $f_{func} : \{k\} \to B$ tal que $k$ es una clave y $B$ es un conjunto de arrays de bytes, donde cada aplicación de la función evalúa el array de bytes asociado con $k$ como una secuencia ordenada finita de instrucciones, ejecuta esas instrucciones en su orden representado y, una vez completada la ejecución, asigna un array de bytes resultante a alguna dirección de memoria que puede evaluarse como el valor devuelto por la función.

#### Función(k)

> Sea $b \in B$ tal que $f_{func}(k) = b$.
>
> Sea $(i_0,\dots,i_n)$ la secuencia ordenada finita de instrucciones representada por $b$, donde $\forall j \in \{0,\dots,n\}, i_j$ es una instrucción.
>
> Sea $a_r \in A$ una dirección asignada después de completarse la ejecución.
>
> Sea $f_m : A \to B$ un mapa de memoria.
>
> $\mathrm{Function}(k)$ es la ejecución de cada $i_j$ en orden ascendente de $j$, donde $\exists b_r \in B : f_m(a_r) = b_r$ después de completarse la ejecución.
>
> $\mathrm{Function}(k) = b_r$

## Hilos de ejecución

### Proceso

Un proceso es cualquier flujo acotado de ejecución que acepta entrada, ejecuta una o más instrucciones y produce salida, donde el proceso representa una unidad distinta de transformación dentro de un sistema.

### Hilo

Un hilo es cualquier flujo de ejecución contenido dentro de un proceso, donde el hilo proporciona un camino por el que pueden ejecutarse secuencias ordenadas de instrucciones pertenecientes a ese proceso.

#### Hilo(p)

> Sea $p$ un proceso.
>
> Sea $(i_0,\dots,i_n)$ una secuencia ordenada finita de instrucciones pertenecientes a $p$.
>
> $\mathrm{Thread}(p)$ es la ejecución de cada $i_j$ en orden ascendente de $j$ dentro de $p$.

### Despachador

Un despachador es cualquier tupla $(t,W,f_d)$ tal que $t$ es un hilo, $W$ es un conjunto de procedimientos o funciones aceptados como trabajo, y $f_d$ es una regla de despacho que selecciona trabajo de $W$, donde el despachador hace que el trabajo seleccionado se ejecute en $t$ según la regla de despacho.

#### Despachador(t)

> Sea $t$ un hilo.
>
> Sea $W$ un conjunto de procedimientos o funciones aceptados por el despachador, donde $\forall w \in W$, $w$ es un procedimiento o una función.
>
> Sea $f_d : \mathcal{P}(W) \to W$ una regla de despacho que selecciona trabajo de un subconjunto no vacío de trabajo aceptado.
>
> $\mathrm{Dispatcher}(t)$ es la ejecución de cada $f_d(W')$ seleccionado en $t$, donde $W' \subseteq W$ y $W' \neq \varnothing$.

## Compuestos

### Miembro

Un miembro es cualquier elemento $m \in M$ tal que $M$ es un conjunto de miembros, donde un miembro es un valor que puede asignarse a una clave dentro del mapa de miembros de un objeto.

### Objeto

Un objeto es cualquier tupla $(a,K,f_o)$ tal que $a \in A$ es una dirección, $K$ es un conjunto de claves y $f_o : K \to M$ es un mapa de miembros, donde $M$ es un conjunto de miembros, lo que permite que el objeto represente un compuesto direccionable cuyos miembros se asignan a claves mediante $f_o$.

#### Objeto(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Campo

Un campo es cualquier tupla $(o,k,m)$ tal que $o = (a,K,f_o)$ es un objeto, $k \in K$ es una clave, $m \in M$ es un miembro y $f_o(k) = m$, donde el campo representa un miembro con clave resuelto desde el mapa de miembros de un objeto.

#### Campo(k)

> Sea $o = (a,K,f_o)$ un objeto.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Método

Un método es cualquier campo $(o,k,m)$ tal que $m$ es un procedimiento o una función, donde el método representa un miembro ejecutable con clave de un objeto.

#### Método(k)

> Sea $o = (a,K,f_o)$ un objeto.
>
> Sea $k \in K$ una clave.
>
> Sea $m \in M$ un miembro tal que $f_o(k) = m$.
>
> $\mathrm{Method}(o,k) = (o,k,m)$ cuando $m$ es un procedimiento o una función.

### Propiedad

Una propiedad es cualquier campo $(o,k,m)$ tal que $m = (A,f_a)$ es un mapa de accesores, $A = \{ \mathrm{Get}, \mathrm{Set} \}$, y $f_a : A \to M$ asigna cada accesor a un miembro, donde $f_a(\mathrm{Get})$ es una función y $f_a(\mathrm{Set})$ es un procedimiento, lo que permite que la propiedad defina tanto el comportamiento de recuperación como el de asignación de un miembro con clave.

#### Propiedad(k)

> Sea $(o,k,m)$ un campo.
>
> Sea $m = (A,f_a)$ un mapa de accesores.
>
> Sea $A = \{ \mathrm{Get}, \mathrm{Set} \}$.
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$, donde $g$ es una función.
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$, donde $s$ es un procedimiento.
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> Sea $(o,k,(A,f_a))$ una propiedad.
>
> Sea $g = f_a(\mathrm{Get})$.
>
> $\mathrm{Get}(k)$ es la aplicación de $g$.

#### Conjunto(k)

> Sea $(o,k,(A,f_a))$ una propiedad.
>
> Sea $s = f_a(\mathrm{Set})$.
>
> $\mathrm{Set}(k)$ es la aplicación de $s$.

### Estructura

Una estructura (a menudo abreviada como `struct`) es cualquier objeto $s = (a,K,f_s)$ tal que $K$ es un conjunto finito de claves y $f_s : K \to M$ es un mapa de miembros que no puede cambiarse después de asignarse el struct, donde el struct es un objeto especializado cuyo diseño de miembros con clave es fijo.

#### Estructura(k)

> Sea $s = (a,K,f_s)$ una estructura.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Clase

Una clase es cualquier objeto $c = (a_c,K_c,f_c)$ tal que $K_c$ es un conjunto finito de claves y $f_c : K_c \to M$ es un mapa de definición de miembros, donde la clase es un objeto especializado cuyos miembros con clave definen el diseño de miembros usado para producir otros objetos.

#### Clase(a)

> Sea $c = (a_c,K_c,f_c)$ una clase.
>
> Sea $a \in A$ una dirección asignada a un objeto producido a partir de $c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interfaz

Una interfaz es cualquier objeto $r = (a_r,K_r,f_r)$ tal que $K_r$ es un conjunto finito de claves y $f_r : K_r \to M$ es un mapa de requisitos de miembros, donde la interfaz es un objeto especializado cuyos miembros con clave definen los miembros que otro objeto debe proporcionar.

#### Interfaz(o)

> Sea $r = (a_r,K_r,f_r)$ una interfaz.
>
> Sea $o = (a,K,f_o)$ un objeto.
>
> $\mathrm{Interface}(r,o)$ holds when $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
