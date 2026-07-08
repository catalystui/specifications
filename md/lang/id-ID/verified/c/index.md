<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->
<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

# Detail Verifikasi

## C

### Ikhtisar

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Bahasa pemrograman C telah diverifikasi terhadap spesifikasi FDEFSPEC (Rev. 1) dan FRELSPEC (Rev. 1) per 7 Juli 2026.

#### Pernyataan Itikad Baik

Kami percaya dengan itikad baik bahwa bahasa pemrograman C dapat secara wajar merepresentasikan konsep dan ketentuan yang didefinisikan dalam spesifikasi berikut, dan dapat digunakan untuk mengimplementasikan sistem yang mematuhi spesifikasi ini.

#### Pernyataan Peninjauan

C provides strong low-level support for foundational data representation, memory access, files, streams, procedures, functions, structures, and direct system-oriented implementation.

Walaupun C tidak menyediakan beberapa konstruksi komposit object-oriented secara native, keterbatasan ini terisolasi pada ketentuan komposit FRELSPEC tertentu dan didokumentasikan di bawah. Kegagalan ini tidak mencegah C dianggap within spec secara keseluruhan, tetapi perlu dipahami saat menggunakan C untuk implementasi yang kompatibel dengan CatalystUI.

#### Asumsi Peninjauan

Peninjauan ini mengasumsikan dukungan C standar modern ketika fitur yang bergantung pada versi dicatat. Dukungan integer exact-width mengasumsikan tipe `<stdint.h>` yang bersesuaian disediakan oleh implementasi.

Peninjauan ini memperlakukan C sebagai bahasa representasi tingkat rendah. Encoding byte-exact dapat direpresentasikan langsung melalui byte array, lookup table, dan logika parsing eksplisit ketika tidak ada codec standar bernama yang disediakan.

### Peringatan

* Tipe integer exact-width bergantung pada dukungan implementasi.
* CP1252 dapat direpresentasikan byte demi byte, tetapi tidak ada codec standar bernama yang disediakan.
* Serialisasi UTF-16LE memerlukan penanganan byte-order eksplisit.
* Standard threads may be omitted by some C implementations.
* Object-oriented patterns may be manually emulated, but are not native language constructs.

### Kegagalan

* C tidak menyediakan member method native.
* C tidak menyediakan property native.
* C tidak menyediakan class native.
* C tidak menyediakan interface native.

### Verifikasi FDEFSPEC

#### Numerik

| Ketentuan | Terverifikasi | Catatan                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Gunakan bit-field atau mask.                    |
| Nibble    | ⚠️       | Gunakan bit-field atau mask.                    |
| Byte      | ✅        | Didukung melalui `unsigned char`.          |
| Short     | ✅        | Didukung melalui `int16_t` dan `uint16_t`. |
| Int       | ✅        | Didukung melalui `int32_t` dan `uint32_t`. |
| Long      | ✅        | Didukung melalui `int64_t` dan `uint64_t`. |
| Float     | ✅        | Didukung melalui `float`.                  |
| Double    | ✅        | Didukung melalui `double`.                 |
| Boolean   | ✅        | Didukung melalui `bool`; C99+.             |

#### Pengodean Teks

| Ketentuan | Terverifikasi | Catatan                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | Didukung melalui `char32_t`; C11+.     |
| ASCII     | ✅        | Dapat direpresentasikan sebagai nilai byte.           |
| CP1252    | ⚠️        | Memerlukan mapping byte eksplisit.         |
| UTF-8     | ✅        | Didukung melalui literal UTF-8; C11+. |
| UTF-16LE  | ⚠️        | Memerlukan penanganan byte-order.           |

#### Status Operasi

| Ketentuan | Terverifikasi | Catatan                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Dapat direpresentasikan oleh enum.  |
| Context   | ✅        | Dapat direpresentasikan oleh nilai.  |
| Operation | ✅        | Dapat direpresentasikan oleh nilai.  |
| Detail    | ✅        | Dapat direpresentasikan oleh nilai.  |
| Result    | ✅        | Dapat direpresentasikan oleh struct. |

### Verifikasi FRELSPEC

#### Koleksi

| Ketentuan | Terverifikasi | Catatan                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Dapat direpresentasikan oleh struct. |
| Map       | ✅        | Dapat direpresentasikan oleh struct. |
| Array     | ✅        | Array native didukung.   |
| File      | ✅        | Didukung melalui API file.   |
| Stream    | ✅        | Didukung melalui API stream. |

#### Memori

| Ketentuan | Terverifikasi | Catatan                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Address didukung.   |
| Pointer   | ✅        | Pointer didukung.    |
| Variable  | ✅        | Variable didukung.   |
| Constant  | ✅        | Didukung melalui `const`. |

#### Operasi

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Direpresentasikan melalui operasi mesin. |
| Procedure   | ✅        | Didukung melalui function `void`.     |
| Function    | ✅        | Didukung melalui function yang mengembalikan nilai.  |

#### Threading

| Provision  | Verified | Notes                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Didukung melalui hosted environment. |
| Thread     | ⚠️        | Didukung melalui `<threads.h>`; C11+. |
| Dispatcher | ✅        | Dapat direpresentasikan secara langsung.           |

#### Komposit

| Ketentuan | Terverifikasi | Catatan                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Member struct didukung.            |
| Object    | ✅        | Struct dapat membentuk komposit addressable. |
| Field     | ✅        | Field struct didukung.             |
| Method    | ❌        | Tidak ada member method native.                |
| Property  | ❌        | Tidak ada accessor map Get/Set eksplisit.        |
| Structure | ✅        | Structure didukung secara native.       |
| Class     | ❌        | Tidak ada konstruksi class native.               |
| Interface | ❌        | Tidak ada konstruksi interface native.           |
