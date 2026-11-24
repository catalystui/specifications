<!-- Terjemahan ini dihasilkan oleh ChatGPT dan perlu ditinjau oleh penerjemah manusia. -->
<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

# FRELSPEC

<br/>

> **Spesifikasi Relasi Fundamental**<br/>
> Revisi 2.1<br/>
> 24 November 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Seluruh hak dilindungi.<br/>
> <br/>
> Definisi dan konsep yang disajikan di sini menjelaskan konstruksi matematika fundamental dan dapat diungkapkan kembali secara bebas.

## Pendahuluan

**Spesifikasi Relasi Fundamental (FRELSPEC)** menetapkan struktur relasional inti yang mendasari ekosistem CatalystUI. Tujuannya adalah memberikan pemahaman terpadu tentang hubungan antara memori, koleksi, operasi, dan komposit di seluruh dokumentasi, spesifikasi, implementasi, dan tinjauan verifikasi, dengan memastikan konsistensi, kejelasan, dan keselarasan.

Dengan mendefinisikan hubungan antar konsep fundamental secara tepat dan stabil, FRELSPEC menyediakan acuan bersama untuk spesifikasi tingkat lebih tinggi sekaligus memungkinkan tiap implementasi menetapkan aturan dan perilakunya sendiri. Pengembang, peninjau, dan pelaksana implementasi dapat bertolak dari dasar yang sama dalam menentukan apakah suatu bahasa, layanan, kerangka kerja, atau sistem dapat merepresentasikan konstruksi relasional yang diperlukan untuk memenuhi spesifikasi.

> [!IMPORTANT]
>
> Kami menyatakan definisi menggunakan bentuk turunan dari notasi [teori himpunan](https://en.wikipedia.org/wiki/Set_theory). Pendekatan ini memberikan definisi yang tepat dan tidak ambigu dengan tetap menjaga kejelasan dan keringkasan. Definisi disusun agar mudah dirujuk, ditafsirkan dengan jelas, dan memiliki hierarki konseptual yang konsisten.

## Daftar isi

- [FRELSPEC](#frelspec)
  - [Pendahuluan](#pendahuluan)
  - [Daftar isi](#daftar-isi)
  - [Revisi](#revisi)
    - [Revisi 2.1](#revisi-21)
    - [Revisi 2](#revisi-2)
  - [Memori](#memori)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Koleksi](#koleksi)
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
  - [Operasi](#operasi)
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
  - [Komposit](#komposit)
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

## Revisi

### Revisi 2.1

**24 November 2026**

Kami menyempurnakan definisi File untuk menetapkan resolusi data yang diatur oleh metadata dan mendefinisikan ulang Stream sebagai mekanisme independen untuk menghasilkan atau mengambil data secara berurutan. Perubahan ini memungkinkan stream merepresentasikan urutan berhingga atau tak berhingga tanpa memberi batasan tambahan pada koleksi lain.

### Revisi 2

**21 November 2026**

Kami menemukan inkonsistensi dalam representasi memori dan nilai tersimpan menggunakan byte dan array byte. Kami menetapkan Word sebagai representasi memori fundamental, menyatukan hubungan di antara Memori, Operasi, dan Komposit.

Kami menemukan inkonsistensi dalam pengindeksan array dan hubungan antarkoleksi. Kami menstandarkan indeks berhingga dan berurutan tanpa celah serta memperjelas hubungan antara Array, File, dan Stream.

Kami menemukan redundansi dan ambiguitas dalam hubungan eksekusi dan komposisi. Kami menyempurnakan prosedur, fungsi, dispatcher, dan hubungan objek untuk mengatasi masalah tersebut dengan mempertahankan independensi implementasi.

## Memori

### Word

Word adalah sembarang urutan bit $w \in \mathrm{Bit}^n$ yang disimpan dalam memori, sedemikian sehingga $n \in \mathbb{N}^+$.

### Address

Alamat adalah sembarang word $a \in A$, dengan $A$ merupakan himpunan word, sedemikian sehingga $a$ mengidentifikasi secara unik suatu lokasi dalam struktur memori tertentu.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

Pointer adalah sembarang fungsi $f_p : \{a\} \to B$ dengan $a \in A$ merupakan alamat dan $B$ merupakan himpunan word, di mana setiap penerapan $f_p$ mengevaluasi word yang disimpan di lokasi memori yang diidentifikasi oleh $a$.

#### Pointer()

> Misalkan $f_m : A \to B$ adalah peta memori.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Variabel adalah sembarang fungsi $f_v : \{k\} \to B$ dengan $k$ merupakan kunci dan $B$ merupakan himpunan word, di mana variabel memperluas pointer dengan mengikat kunci pada alamat dan mengevaluasi word yang tersimpan pada alamat tersebut.

#### Variable(k)

> Misalkan $f_b : \{k\} \to \{a\}$ adalah fungsi pengikatan variabel.
>
> Misalkan $f_p : \{a\} \to B$ adalah pointer.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Konstanta adalah sembarang variabel $f_c : \{k\} \to B$ dengan $k$ merupakan kunci dan $B$ merupakan himpunan word, di mana word yang terkait dengan $k$ tidak dapat diubah setelah ditetapkan.

#### Constant(k)

> Misalkan $b_0 \in B$ adalah word yang ditetapkan pada $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ setelah $b_0$ ditetapkan.

## Koleksi

### Set

Himpunan adalah sembarang koleksi berhingga dan tidak berurutan yang terdiri atas word berbeda.

#### Set()

> Misalkan $B$ adalah himpunan word.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

Map adalah sembarang fungsi $f_m : K \to V$ dengan $K$ merupakan himpunan kunci dan $V$ merupakan himpunan nilai, di mana setiap kunci terkait dengan tepat satu nilai.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Array adalah sembarang fungsi $f_a : I \to V$ dengan $I \subseteq \mathbb{N}$ merupakan himpunan indeks bilangan bulat berhingga dan berurutan tanpa celah, dan $V$ merupakan himpunan word, di mana setiap indeks mengidentifikasi tepat satu nilai.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

File adalah sembarang tupel $(f_m,d)$ dengan $d$ merupakan array word dan $f_m : I \times \{d\} \to \mathrm{Array}$ merupakan fungsi metadata yang direpresentasikan oleh array word, di mana $I$ merupakan himpunan indeks bilangan bulat berhingga dan berurutan tanpa celah, dan $f_m$ menentukan cara data diresolusi dari $d$.

#### File(i)

> Misalkan $(f_m,d)$ adalah file.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

Stream adalah sembarang fungsi $f_s$ sedemikian sehingga setiap penerapan $f_s$ menghasilkan potongan berikutnya $c$ dalam urutan berhingga atau tak berhingga, di mana $f_s$ menetapkan mekanisme pembangkitan atau pengambilan data secara berurutan.

#### Stream()

> Misalkan $f_c : K \to C$ adalah fungsi resolusi potongan, dengan $K \subseteq \mathbb{N}$ merupakan himpunan indeks bilangan bulat berurutan tanpa celah dan $C$ merupakan himpunan potongan.
>
> Misalkan $k \in K$ adalah indeks potongan berikutnya.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$, dengan memajukan $k$ setelah setiap penerapan.

## Operasi

### Instruction

Instruksi adalah sembarang word atau tupel berhingga word $i \in B$ dengan $B$ merupakan himpunan word atau tupel berhingga word, di mana setiap instruksi merepresentasikan satu operasi komputasi yang akan dilakukan.

### Procedure

Prosedur adalah sembarang variabel $f_{proc} : \{k\} \to B$ dengan $f_{proc}(k)$ merepresentasikan array instruksi $f_a : I \to V$, di mana eksekusi prosedur menjalankan setiap instruksi sesuai urutan indeksnya.

#### Procedure(k)

> $\mathrm{Procedure}(k)$ adalah eksekusi setiap $f_a(i)$ dalam urutan menaik $i \in I$.

### Function

Fungsi adalah sembarang prosedur $f_{func} : \{k\} \to B$ yang jika dieksekusi mengembalikan alamat $a_r \in A$ yang mengidentifikasi word hasil atau word pertama dari array word yang merepresentasikan hasil.

#### Function(k)

> Misalkan $f_m : A \to B$ adalah peta memori, dengan $a_r \in A$ mengidentifikasi word hasil $r \in B$.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## Threading

### Process

Proses adalah sembarang aliran eksekusi terbatas yang menerima masukan, mengeksekusi satu atau lebih prosedur atau fungsi, dan menghasilkan keluaran, di mana proses merepresentasikan unit transformasi tersendiri dalam suatu sistem.

### Thread

Thread adalah sembarang aliran eksekusi yang terdapat dalam suatu proses, menyediakan satu jalur bagi eksekusi prosedur atau fungsi milik proses tersebut.

#### Thread(p)

> Misalkan $p$ adalah proses.
>
> Misalkan $(w_0, \dots, w_n)$ adalah tupel berhingga prosedur atau fungsi milik $p$.
>
> $\mathrm{Thread}(p)$ adalah eksekusi setiap $w_j$ dalam urutan menaik $j$ di dalam $p$.

### Dispatcher

Dispatcher adalah sembarang tupel $(t,W,f_d)$ dengan $t$ merupakan thread, $W$ merupakan himpunan prosedur atau fungsi yang diterima sebagai pekerjaan, dan $f_d$ merupakan aturan dispatch yang memilih pekerjaan dari $W$, di mana dispatcher menyebabkan pekerjaan terpilih dieksekusi pada $t$ menurut aturan tersebut.

#### Dispatcher(t)

> Misalkan $t$ adalah thread.
>
> Misalkan $W$ adalah himpunan prosedur atau fungsi yang diterima dispatcher, dengan $\forall w \in W$, $w$ merupakan prosedur atau fungsi.
>
> Misalkan $f_d : \mathcal{P}^+(W) \to W$ adalah aturan dispatch yang memilih pekerjaan dari subset tidak kosong pekerjaan yang diterima.
>
> $\mathrm{Dispatcher}(t)$ adalah eksekusi setiap $f_d(W')$ yang dipilih pada $t$, dengan $W' \subseteq W$, $W' \neq \varnothing$, dan $f_d(W') \in W'$.

## Komposit

### Member

Anggota adalah sembarang elemen $m \in M$ dengan $M$ merupakan himpunan elemen dan $f_o : K \to M$ merupakan map anggota objek, di mana $m = f_o(k)$ untuk suatu kunci $k \in K$.

### Object

Objek adalah sembarang tupel $(a,K,f_o)$ dengan $a \in A$ merupakan alamat, $K$ merupakan himpunan kunci, dan $f_o : K \to M$ merupakan map anggota, di mana $M$ merupakan himpunan elemen, sehingga objek dapat merepresentasikan komposit yang dapat dialamati dan anggotanya ditetapkan pada kunci melalui $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Field adalah sembarang tupel $(o,k,m)$ dengan $o = (a,K,f_o)$ merupakan objek, $k \in K$ merupakan kunci, dan $m = f_o(k)$ merupakan anggota, di mana field merepresentasikan satu anggota berkunci yang diresolusi dari map anggota objek.

#### Field(o,k)

> Misalkan $o = (a,K,f_o)$ adalah objek.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

Metode adalah sembarang field $(o,k,m)$ dengan $m$ merupakan prosedur atau fungsi, di mana metode merepresentasikan anggota objek berkunci yang dapat dieksekusi.

#### Method(o,k)

> Misalkan $(o,k,m)$ adalah field.
>
> $\mathrm{Method}(o,k) = (o,k,m)$, dengan $m$ merupakan prosedur atau fungsi.

### Property

Properti adalah sembarang field $(o,k,m)$ dengan $m = (X,f_a)$ merupakan map aksesor, $X = \{\mathrm{Get}, \mathrm{Set}\}$, dan $f_a : X \to M$ memetakan setiap aksesor ke anggota, dengan $f_a(\mathrm{Get})$ merupakan fungsi dan $f_a(\mathrm{Set})$ merupakan prosedur, sehingga properti dapat menentukan perilaku pengambilan maupun penetapan anggota berkunci.

#### Property(o,k)

> Misalkan $(o,k,m)$ adalah field, dengan $m = (X,f_a)$ merupakan map aksesor.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> Misalkan $(o,k,(X,f_a))$ adalah properti.
>
> $\mathrm{Get}(o,k)$ adalah penerapan $f_a(\mathrm{Get})$.

#### Set(o,k)

> Misalkan $(o,k,(X,f_a))$ adalah properti.
>
> $\mathrm{Set}(o,k)$ adalah penerapan $f_a(\mathrm{Set})$.

### Structure

Struktur (sering disingkat `struct`) adalah sembarang objek $s = (a,K,f_s)$ dengan $K$ merupakan himpunan kunci berhingga dan $f_s : K \to M$ merupakan map anggota yang kuncinya tidak dapat diubah setelah struktur ditetapkan, di mana struktur merupakan objek khusus dengan susunan anggota berkunci yang tetap.

#### Structure(s,k)

> Misalkan $s = (a,K,f_s)$ adalah struktur.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Kelas adalah sembarang objek $c = (a_c,K_c,f_c)$ dengan $K_c$ merupakan himpunan kunci berhingga dan $f_c : K_c \to M$ merupakan map definisi anggota, di mana kelas merupakan objek khusus dengan anggota berkunci yang menentukan susunan anggota untuk menghasilkan objek lain.

#### Class(c,a)

> Misalkan $c = (a_c,K_c,f_c)$ adalah kelas.
>
> Misalkan $a \in A$ adalah alamat yang ditetapkan pada objek yang dihasilkan dari $c$.
>
> Misalkan $f_o : K_c \to M$ adalah map anggota yang mengikuti definisi $f_c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

Antarmuka adalah sembarang objek $r = (a_r,K_r,f_r)$ dengan $K_r$ merupakan himpunan kunci berhingga dan $f_r : K_r \to M$ merupakan map persyaratan anggota, di mana antarmuka merupakan objek khusus dengan anggota berkunci yang menentukan anggota yang harus disediakan oleh objek lain.

#### Interface(r,o)

> Misalkan $r = (a_r,K_r,f_r)$ adalah antarmuka.
>
> Misalkan $o = (a,K,f_o)$ adalah objek.
>
> Misalkan $f_v : M \times M \to \{0,1\}$ adalah aturan validasi yang menentukan apakah suatu anggota memenuhi persyaratan anggota lain.
>
> $\mathrm{Interface}(r,o)$ berlaku ketika $K_r \subseteq K$ dan $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$.
