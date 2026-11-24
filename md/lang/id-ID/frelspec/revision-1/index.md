<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->
<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

# FRELSPEC

<br/>

> **Spesifikasi Relasi Dasar**<br/>
> Revisi 1<br/>
> 7 Juli 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Hak cipta dilindungi undang-undang.<br/>
> <br/>
> Definisi dan konsep yang disajikan di sini menjelaskan konstruksi matematis dasar dan dapat diungkapkan kembali secara bebas.

## Pendahuluan

**Foundational Relations Specification (FRELSPEC)** menetapkan struktur relasional inti yang menopang ekosistem CatalystUI. Tujuannya adalah memberikan pemahaman terpadu tentang bagaimana nilai, memori, operasi, dan komposit dikaitkan di seluruh dokumentasi, spesifikasi, implementasi, dan peninjauan verifikasi, sehingga konsistensi, kejelasan, dan keselarasan tetap terjaga.

Dengan mendefinisikan hubungan antara konsep-konsep dasar dalam bentuk yang presisi dan stabil, FRELSPEC menyediakan titik acuan bersama bagi spesifikasi tingkat lebih tinggi. Hal ini memungkinkan pengembang, peninjau, dan implementer berpikir dari fondasi yang sama ketika menentukan apakah suatu bahasa, service, framework, atau sistem dapat merepresentasikan konstruksi relasional yang diperlukan agar dianggap within spec.

> [!IMPORTANT]
>
> Kami mengekspresikan definisi menggunakan bentuk turunan dari notasi [teori himpunan](https://en.wikipedia.org/wiki/Set_theory). Pendekatan ini menyediakan definisi yang presisi dan tidak ambigu sambil tetap menjaga kejelasan dan keringkasan. Kami menyusun definisi ini agar mendukung referensi yang mudah, interpretasi yang jelas, dan hierarki konseptual yang konsisten.

## Daftar Isi

- [FRELSPEC](#frelspec)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Collections](#collections)
    - [Set](#set)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [Memory](#memory)
    - [Address](#address)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Operations](#operations)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [Threading](#threading)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Composites](#composites)
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

## Koleksi

### Set

Set adalah koleksi apa pun dari elemen-elemen yang berbeda.

### Map

Map adalah setiap fungsi $f_m : K \to V$ sedemikian sehingga $K$ adalah set kunci dan $V$ adalah set nilai.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Array adalah setiap fungsi $f_a : I \to V$ sedemikian sehingga $I \subset \mathbb{N}$, $I$ adalah set integer yang finite dan contiguous, dan $V$ adalah set nilai.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

File adalah setiap fungsi $f_f : I \to B$ sedemikian sehingga $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ adalah set integer yang finite dan contiguous, dan $b$ adalah set byte, di mana $f_f$ berasal dari mekanisme penyimpanan data persisten.

#### File(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Stream

Stream adalah setiap fungsi $f_s$ sedemikian sehingga setiap penerapan $f_s$ menghasilkan chunk berikutnya $f_c : I \to B$ dalam urutan byte, di mana $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ adalah set integer yang finite dan contiguous, $B$ adalah set byte, dan $f_s$ berasal dari mekanisme pembuatan atau pengambilan data berurutan.

#### Stream()

> Misalkan $c_k : I_k \to B$ adalah chunk yang dikembalikan oleh penerapan ke-$k$ dari $f_s$.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ pada penerapan ke-$k$.

## Memori

### Address

Address adalah setiap elemen $a \in A$ sedemikian sehingga $A$ adalah set address, di mana setiap address $a$ mengidentifikasi secara unik suatu lokasi dalam struktur memori.

### Pointer

Pointer adalah setiap fungsi $f_p : \{a\} \to B$ sedemikian sehingga $a \in A$ adalah address dan $B$ adalah set byte array, di mana setiap penerapan $f_p$ mengevaluasi byte array yang disimpan pada lokasi memori yang diidentifikasi oleh address yang terikat padanya.

#### Pointer()

> Misalkan $f_m : A \to B$ adalah memory map.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Variable adalah setiap fungsi $f_v : \{k\} \to B$ sedemikian sehingga $k$ adalah key dan $B$ adalah set byte array, di mana variable memperluas pointer dengan mengikat satu key ke satu address dan mengevaluasi byte array yang disimpan pada lokasi memori yang diidentifikasi oleh address tersebut.

#### Variable(k)

> Misalkan $f_b : \{k\} \to \{a\}$ adalah fungsi binding milik variable.
>
> Misalkan $f_p : \{a\} \to B$ adalah pointer.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Constant adalah setiap variable $f_c : \{k\} \to B$ sedemikian sehingga $k$ adalah key dan $B$ adalah set byte array, di mana byte array yang terkait dengan $k$ tidak dapat diubah setelah ditetapkan.

#### Constant(k)

> Misalkan $b_0 \in B$ adalah byte array yang ditetapkan ke $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ setelah $b_0$ ditetapkan.


## Operasi

### Instruction

Instruction adalah setiap array byte $i \in B$ sedemikian sehingga $B$ adalah set byte array, di mana setiap instruction merepresentasikan satu operasi komputasional yang akan dilakukan.

### Procedure

Procedure adalah setiap variable $f_{proc} : \{k\} \to B$ sedemikian sehingga $k$ adalah key dan $B$ adalah set byte array, di mana setiap penerapan procedure mengevaluasi byte array yang terkait dengan $k$ sebagai urutan instruction yang finite dan ordered, lalu menjalankan instruction tersebut sesuai urutan representasinya tanpa mendefinisikan nilai return.

#### Procedure(k)

> Misalkan $b \in B$ sedemikian sehingga $f_{proc}(k) = b$.
>
> Misalkan $(i_0,\dots,i_n)$ adalah urutan instruction yang finite dan ordered yang direpresentasikan oleh $b$, di mana $\forall j \in \{0,\dots,n\}, i_j$ adalah instruction.
>
> $\mathrm{Procedure}(k)$ adalah eksekusi setiap $i_j$ dalam urutan naik berdasarkan $j$.

### Function

Function adalah setiap procedure $f_{func} : \{k\} \to B$ sedemikian sehingga $k$ adalah key dan $B$ adalah set byte array, di mana setiap penerapan function mengevaluasi byte array yang terkait dengan $k$ sebagai urutan instruction yang finite dan ordered, menjalankan instruction tersebut sesuai urutan representasinya, dan setelah eksekusi selesai, menetapkan byte array hasil ke suatu address dalam memori yang dapat dievaluasi sebagai nilai return function.

#### Function(k)

> Misalkan $b \in B$ sedemikian sehingga $f_{func}(k) = b$.
>
> Misalkan $(i_0,\dots,i_n)$ adalah urutan instruction yang finite dan ordered yang direpresentasikan oleh $b$, di mana $\forall j \in \{0,\dots,n\}, i_j$ adalah instruction.
>
> Misalkan $a_r \in A$ adalah address yang ditetapkan setelah eksekusi selesai.
>
> Misalkan $f_m : A \to B$ adalah memory map.
>
> $\mathrm{Function}(k)$ adalah eksekusi setiap $i_j$ dalam urutan naik berdasarkan $j$, di mana $\exists b_r \in B : f_m(a_r) = b_r$ setelah eksekusi selesai.
>
> $\mathrm{Function}(k) = b_r$

## Threading

### Process

Process adalah alur eksekusi berbatas yang menerima input, menjalankan satu atau lebih instruction, dan menghasilkan output, di mana process merepresentasikan unit transformasi yang berbeda di dalam sistem.

### Thread

Thread adalah alur eksekusi apa pun yang berada di dalam process, di mana thread menyediakan satu jalur untuk mengeksekusi urutan instruction milik process tersebut.

#### Thread(p)

> Misalkan $p$ adalah process.
>
> Misalkan $(i_0,\dots,i_n)$ adalah urutan instruction yang finite dan ordered milik $p$.
>
> $\mathrm{Thread}(p)$ adalah eksekusi setiap $i_j$ dalam urutan naik berdasarkan $j$ di dalam $p$.

### Dispatcher

Dispatcher adalah setiap tuple $(t,W,f_d)$ sedemikian sehingga $t$ adalah thread, $W$ adalah set procedure atau function yang diterima sebagai work, dan $f_d$ adalah aturan dispatch yang memilih work dari $W$, di mana dispatcher menyebabkan work yang dipilih dieksekusi pada $t$ sesuai aturan dispatch.

#### Dispatcher(t)

> Misalkan $t$ adalah thread.
>
> Misalkan $W$ adalah set procedure atau function yang diterima oleh dispatcher, di mana $\forall w \in W$, $w$ adalah procedure atau function.
>
> Misalkan $f_d : \mathcal{P}(W) \to W$ adalah aturan dispatch yang memilih work dari subset tidak kosong dari work yang diterima.
>
> $\mathrm{Dispatcher}(t)$ adalah eksekusi dari setiap $f_d(W')$ pada $t$, di mana $W' \subseteq W$ dan $W' \neq \varnothing$.

## Komposit

### Member

Member adalah setiap elemen $m \in M$ sedemikian sehingga $M$ adalah set member, di mana member adalah nilai yang dapat ditetapkan ke key di dalam member map suatu object.

### Object

Object adalah setiap tuple $(a,K,f_o)$ sedemikian sehingga $a \in A$ adalah address, $K$ adalah set key, dan $f_o : K \to M$ adalah member map, di mana $M$ adalah set member, sehingga object dapat merepresentasikan komposit addressable yang member-nya ditetapkan ke key melalui $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Field adalah setiap tuple $(o,k,m)$ sedemikian sehingga $o = (a,K,f_o)$ adalah object, $k \in K$ adalah key, $m \in M$ adalah member, dan $f_o(k) = m$, di mana field merepresentasikan satu keyed member yang diselesaikan dari member map suatu object.

#### Field(k)

> Misalkan $o = (a,K,f_o)$ adalah object.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Method

Method adalah setiap field $(o,k,m)$ sedemikian sehingga $m$ adalah procedure atau function, di mana method merepresentasikan executable member berkunci milik object.

#### Method(k)

> Misalkan $o = (a,K,f_o)$ adalah object.
>
> Misalkan $k \in K$ adalah key.
>
> Misalkan $m \in M$ adalah member sedemikian sehingga $f_o(k) = m$.
>
> $\mathrm{Method}(o,k) = (o,k,m)$ ketika $m$ adalah procedure atau function.

### Property

Property adalah setiap field $(o,k,m)$ sedemikian sehingga $m = (A,f_a)$ adalah accessor map, $A = \{ \mathrm{Get}, \mathrm{Set} \}$, dan $f_a : A \to M$ memetakan setiap accessor ke member, di mana $f_a(\mathrm{Get})$ adalah function dan $f_a(\mathrm{Set})$ adalah procedure, sehingga property dapat mendefinisikan perilaku pengambilan dan penetapan dari keyed member.

#### Property(k)

> Misalkan $(o,k,m)$ adalah field.
>
> Misalkan $m = (A,f_a)$ adalah accessor map.
>
> Misalkan $A = \{ \mathrm{Get}, \mathrm{Set} \}$.
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$, di mana $g$ adalah function.
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$, di mana $s$ adalah procedure.
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> Misalkan $(o,k,(A,f_a))$ adalah property.
>
> Misalkan $g = f_a(\mathrm{Get})$.
>
> $\mathrm{Get}(k)$ adalah penerapan $g$.

#### Set(k)

> Misalkan $(o,k,(A,f_a))$ adalah property.
>
> Misalkan $s = f_a(\mathrm{Set})$.
>
> $\mathrm{Set}(k)$ adalah penerapan $s$.

### Structure

Structure (sering disingkat `struct`) adalah setiap object $s = (a,K,f_s)$ sedemikian sehingga $K$ adalah set key yang finite dan $f_s : K \to M$ adalah member map yang tidak dapat diubah setelah struct ditetapkan, di mana struct adalah object khusus dengan layout keyed member yang tetap.

#### Structure(k)

> Misalkan $s = (a,K,f_s)$ adalah structure.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Class adalah setiap object $c = (a_c,K_c,f_c)$ sedemikian sehingga $K_c$ adalah set key yang finite dan $f_c : K_c \to M$ adalah member-definition map, di mana class adalah object khusus yang keyed member-nya mendefinisikan layout member yang digunakan untuk menghasilkan object lain.

#### Class(a)

> Misalkan $c = (a_c,K_c,f_c)$ adalah class.
>
> Misalkan $a \in A$ adalah address yang ditetapkan kepada object yang dihasilkan dari $c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interface

Interface adalah setiap object $r = (a_r,K_r,f_r)$ sedemikian sehingga $K_r$ adalah set key yang finite dan $f_r : K_r \to M$ adalah member-requirement map, di mana interface adalah object khusus yang keyed member-nya mendefinisikan member yang harus disediakan oleh object lain.

#### Interface(o)

> Misalkan $r = (a_r,K_r,f_r)$ adalah interface.
>
> Misalkan $o = (a,K,f_o)$ adalah object.
>
> $\mathrm{Interface}(r,o)$ holds when $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
