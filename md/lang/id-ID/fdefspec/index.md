<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->
<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

# FDEFSPEC

<br/>

> **Spesifikasi Definisi Dasar**<br/>
> Revisi 1<br/>
> 23 Maret 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Hak cipta dilindungi undang-undang.<br/>
> <br/>
> Definisi dan konsep yang disajikan di sini menjelaskan konstruksi matematis dasar dan dapat diungkapkan kembali secara bebas.

## Pendahuluan

**Foundational Definitions Specification (FDEFSPEC)** menetapkan konsep inti dan terminologi yang menopang ekosistem CatalystUI. Tujuannya adalah memberikan pemahaman terpadu tentang konsep-konsep ini di seluruh dokumentasi, spesifikasi, implementasi, dan peninjauan verifikasi, sehingga konsistensi, kejelasan, dan keselarasan tetap terjaga.

Dengan mendefinisikan istilah kunci dan hubungan dalam bentuk yang presisi dan stabil, FDEFSPEC menyediakan titik acuan bersama bagi spesifikasi tingkat lebih tinggi. Hal ini memungkinkan pengembang, peninjau, dan implementer berpikir dari fondasi yang sama ketika menentukan apakah suatu bahasa, service, framework, atau sistem dapat dianggap within spec.

> [!IMPORTANT]
>
> Kami mengekspresikan definisi menggunakan bentuk turunan dari notasi [teori himpunan](https://en.wikipedia.org/wiki/Set_theory). Pendekatan ini menyediakan definisi yang presisi dan tidak ambigu sambil tetap menjaga kejelasan dan keringkasan. Kami menyusun definisi ini agar mendukung referensi yang mudah, interpretasi yang jelas, dan hierarki konseptual yang konsisten.

## Daftar Isi

- [FDEFSPEC](#fdefspec)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Numerics](#numerics)
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
  - [Text Encoding](#text-encoding)
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
  - [Operation Status](#operation-status)
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

## Numerik

### Bit

Bit adalah setiap $b \in \{0,1\}$.

### Nibble

Nibble adalah setiap $(b_0,\dots,b_3)$ sedemikian sehingga untuk semua $i \in \{0,\dots,3\}$, $b_i \in \mathrm{Bit}$.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

Byte adalah setiap $(b_0,\dots,b_7)$ sedemikian sehingga untuk semua $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

Short adalah setiap $(b_0,\dots,b_{15})$ sedemikian sehingga untuk semua $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

Integer adalah setiap $(b_0,\dots,b_{31})$ sedemikian sehingga untuk semua $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

Long adalah setiap $(b_0,\dots,b_{63})$ sedemikian sehingga untuk semua $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

Single adalah setiap $(b_0,\dots,b_{31})$ sedemikian sehingga untuk semua $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Single()

Definisi berikut sesuai dengan standar IEEE 754 untuk representasi floating-point presisi tunggal. Definisi ini menjelaskan bagaimana urutan biner 32-bit diinterpretasikan sebagai angka floating-point, termasuk kasus khusus untuk nol, tak hingga, dan NaN (Not a Number).

> Misalkan $s = b_0$
>
> Misalkan $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Misalkan $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

Double adalah setiap $(b_0,\dots,b_{63})$ sedemikian sehingga untuk semua $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Double()

Definisi berikut sesuai dengan standar IEEE 754 untuk representasi floating-point presisi ganda. Definisi ini menjelaskan bagaimana urutan biner 64-bit diinterpretasikan sebagai angka floating-point, termasuk kasus khusus untuk nol, tak hingga, dan NaN (Not a Number).

> Misalkan $s = b_0$
>
> Misalkan $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Misalkan $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

Boolean adalah setiap $b \in \{0,1\}$.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{di mana } b \in \mathrm{Bit}$

## Pengodean Teks

### Pengodean Teks

Pengodean teks didefinisikan sebagai set berikut:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Pengodean Teks()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Codepoint Unicode adalah setiap $e \in \mathbb{Z}$ sedemikian sehingga $0 \leq e \leq 0x10FFFF$.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

Unit kode ASCII adalah setiap $(b_0,\dots,b_6)$ sedemikian sehingga untuk semua $i \in \{0,\dots,6\}$, $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

Demi alasan performa dan kompatibilitas, unit kode ASCII lazim direpresentasikan sebagai byte dengan menambahkan bit nol di depan. Dalam kasus seperti itu, unit kode ASCII direpresentasikan sebagai:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Jika tidak:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Dalam teorema ini, kedua definisi merupakan representasi unit kode ASCII yang dapat diterima. Demi konsistensi, kita akan menggunakan definisi pertama ketika merepresentasikan unit kode ASCII sebagai byte, dan definisi kedua ketika merepresentasikannya sebagai urutan 7-bit.

#### ASCII()

ASCII adalah tuple hingga yang null-terminated $(u_0, \dots, u_k, u_{k+1})$ sedemikian sehingga:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ adalah unit kode ASCII
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

Urutan tersebut disebut null-terminated.

### CP1252 Code Unit

Unit kode CP1252 adalah setiap $(b_0,\dots,b_7)$ sedemikian sehingga untuk semua $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 adalah tuple hingga yang null-terminated $(u_0, \dots, u_k, u_{k+1})$ sedemikian sehingga:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ adalah unit kode CP1252
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

Urutan tersebut disebut null-terminated.

### UTF-8 Code Unit

Unit kode UTF-8 adalah setiap $(b_0,\dots,b_7)$ sedemikian sehingga untuk semua $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 adalah tuple hingga yang null-terminated $(u_0, \dots, u_k, u_{k+1})$ sedemikian sehingga:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ adalah unit kode UTF-8
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

Urutan tersebut disebut null-terminated.

### UTF-16LE Code Unit

Unit kode UTF-16LE adalah setiap $(b_0,\dots,b_{15})$ sedemikian sehingga untuk semua $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE adalah tuple hingga yang null-terminated $(u_0, \dots, u_k, u_{k+1})$ sedemikian sehingga:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ adalah unit kode UTF-16LE
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

Urutan tersebut disebut null-terminated.

## Status Operasi

### Kode Status

Kode status adalah setiap $(b_0,\dots,b_7)$ sedemikian sehingga untuk semua $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

Tingkat kode status didefinisikan sebagai set berikut:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Kode Status()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Kode Status Level()

Set nilai kode status adalah rentang $[0, 255]$, yang dipartisi menjadi empat tingkat:

> Misalkan $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Kode Status Definition()

Semua kode status memiliki definisi eksplisit. Kode status apa pun yang tidak termasuk dalam daftar berikut dicadangkan untuk penggunaan di masa depan, dan maknanya belum didefinisikan. Tingkat kode status ditentukan oleh $\mathrm{Status\ Code\ Level}(s)$.

Dalam daftar berikut, input $s$ direpresentasikan sebagai nilai heksadesimal agar mudah dibaca. Setiap kode status yang didefinisikan menentukan tingkat, kategori, subkategori, deskripsi, dan detail yang terkait, jika berlaku.

Daftar ini dapat diperluas ketika kode status baru didefinisikan. Kode status baru apa pun tidak boleh bertentangan dengan kode yang sudah ada dan harus memiliki makna yang terdokumentasi dengan jelas.

Untuk menyampaikan informasi yang tidak direpresentasikan oleh kode status yang telah didefinisikan, kode konteks, kode operasi, atau kode detail harus digunakan.

##### Sukses

| Kode | Tingkat | Kategori | Deskripsi | Detail |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | Operasi selesai dengan sukses. | |
| `0x01` | SUCCESS | NOOP | Operasi selesai dengan sukses tanpa melakukan tindakan apa pun. | |

##### Peringatan

| Kode | Tingkat | Kategori | Deskripsi | Detail |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | Operasi selesai, tetapi hasilnya mungkin tidak terduga atau tidak diinginkan. | |
| `0x41` | WARNING | PARTIAL | Operasi selesai, tetapi hanya sebagian. Output mungkin tidak lengkap. | |
| `0x42` | WARNING | DEPRECATED | Operasi selesai, tetapi menggunakan fitur atau perilaku yang deprecated. Operasi tersebut mungkin tidak lagi bekerja di masa depan. | |

##### Error

| Kode | Tingkat | Kategori | Deskripsi | Detail |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | Operasi gagal karena error yang dapat dipulihkan. | |
| `0x81` | ERROR | INVALID_ARGUMENT | Operasi gagal. Sebuah argumen tidak valid atau berada di luar rentang. | Indeks argumen yang tidak valid, dimulai dari 0 dari kiri ke kanan dalam signature fungsi. |
| `0x82` | ERROR | INVALID_STATE | Operasi gagal. Sistem berada dalam keadaan tidak konsisten, rusak, atau tidak valid. | |
| `0x83` | ERROR | MALFORMED_INPUT | Operasi gagal. Input yang diperlukan malformed atau berisi data tidak valid. | |
| `0x84` | ERROR | ACCESS_DENIED | Operasi gagal karena resource yang diperlukan menolak akses. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | Operasi gagal karena fitur atau perilaku yang diminta belum diimplementasikan. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | Operasi gagal karena sistem target atau konfigurasi tidak mendukung fitur yang diminta. | |
| `0x87` | ERROR | TIMEOUT | Operasi gagal karena timeout yang diperlukan terjadi sebelum selesai. | |
| `0x88` | ERROR | NOT_FOUND | Operasi gagal karena resource yang diperlukan tidak ada. | |
| `0x89` | ERROR | INTERRUPTED | Operasi gagal karena event eksternal menginterupsinya. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | Operasi gagal karena dependency yang diperlukan gagal. | Nilai `STATUS_CODE` milik dependency tersebut. Caller dianjurkan (tetapi tidak diwajibkan) untuk mengidentifikasi dependency yang gagal melalui field `OP_CODE`. |
| `0x90` | ERROR | BUFFER_OVERFLOW | Operasi gagal. Buffer terlalu kecil untuk menampung data yang diperlukan. | |
| `0x91` | ERROR | ALLOCATION_FAILED | Operasi gagal. Permintaan alokasi memori tidak berhasil. | |
| `0xA0` | ERROR | IO_ERROR | Operasi gagal. Error I/O terjadi selama operasi. | |

##### Fatal

| Kode | Tingkat | Kategori | Deskripsi | Detail |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | Operasi gagal karena error yang tidak dapat dipulihkan. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | Operasi gagal karena sistem melanggar invariant dasar, yang menunjukkan error logika kritis atau korupsi data. | |

### Kode Konteks

Kode konteks adalah setiap $(b_0,\dots,b_7)$ sedemikian sehingga untuk semua $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Kode Konteks()

Nilai kode konteks merepresentasikan informasi kontekstual tambahan tentang operasi yang telah selesai, sebagaimana didefinisikan oleh operasi terkait; nilainya harus nol ketika tingkat kode status adalah $\mathrm{Success}$, dan selain itu bersifat implementation-defined.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Kode Operasi

Kode operasi adalah setiap $(b_0,\dots,b_7)$ sedemikian sehingga untuk semua $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Kode Operasi()

Nilai kode operasi merepresentasikan operasi yang terkait dengan suatu result. Maknanya didefinisikan oleh operasi yang bersesuaian dan dokumentasinya. Nilai yang tidak didefinisikan dianggap unknown.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Kode Detail

Kode detail adalah setiap $(b_0,\dots,b_7)$ sedemikian sehingga untuk semua $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Kode Detail()

Nilai kode detail merepresentasikan informasi tambahan tentang operasi yang telah selesai; maknanya didefinisikan oleh status, konteks, atau kode operasi terkait (dalam urutan tersebut), dan selain itu unknown.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Result

> [!TIP]
>
> Nilai result dapat direpresentasikan sebagai integer 32-bit. Dalam urutan byte big-endian, nilainya muncul sebagai `0xSSCCOODD`, di mana `SS`, `CC`, `OO`, dan `DD` masing-masing berkaitan dengan kode status, kode konteks, kode operasi, dan kode detail. Dalam urutan byte little-endian, nilai yang sama muncul sebagai `0xDDOOCCSS`. Urutan byte mana pun dapat digunakan selama diterapkan secara konsisten dan didokumentasikan.

Result adalah setiap $(b_0,\dots,b_{31})$ sedemikian sehingga untuk semua $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

Result dipartisi menjadi empat byte berurutan:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

di mana $s$, $c$, $o$, dan $d$ adalah komponen result tersebut.

#### Result()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
