<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->
<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

# Detail Verifikasi

## Java

### Ikhtisar

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Bahasa pemrograman Java telah diverifikasi terhadap spesifikasi FDEFSPEC (Rev. 1) dan FRELSPEC (Rev. 1) per 7 Juli 2026.

#### Pernyataan Itikad Baik

Kami percaya dengan itikad baik bahwa bahasa pemrograman Java dapat secara wajar merepresentasikan sebagian besar konsep dan ketentuan yang didefinisikan dalam spesifikasi berikut, dan dapat digunakan untuk mengimplementasikan sistem yang mematuhi spesifikasi ini.

#### Asumsi Peninjauan

Peninjauan ini mengasumsikan dukungan bahasa Java modern ketika fitur yang bergantung pada versi dicatat. Fitur seperti local variable inference, records, dan foreign memory access mungkin memerlukan versi Java yang lebih baru.

### Peringatan

* Java tidak memiliki dukungan native untuk tipe numerik unsigned, sehingga mungkin memerlukan widening atau representasi alternatif untuk beberapa ketentuan.
* Perilaku address memori langsung dan gaya pointer mungkin memerlukan dukungan Java 22+ Foreign Function and Memory API.
* Java tidak memiliki sintaks property native, sehingga memerlukan method getter dan setter sebagai gantinya.

### Kegagalan

* Java tidak menyediakan CP1252 sebagai charset standar yang dijamin, sehingga memerlukan dukungan implementation-specific, library tambahan, atau penanganan khusus untuk kepatuhan penuh.
* Property Java tidak menyediakan keyed member eksplisit yang didukung oleh accessor map Get/Set yang diperlukan.

### Verifikasi FDEFSPEC

#### Numerik

| Ketentuan | Terverifikasi | Catatan                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | Tidak ada numerik 1-bit; perlu widening.                         |
| Nibble    | ⚠️       | Tidak ada numerik 4-bit; perlu widening.                         |
| Byte      | ⚠️       | Hanya signed 8-bit; gunakan widening untuk unsigned.           |
| Short     | ⚠️       | Hanya signed 16-bit; gunakan widening untuk unsigned.          |
| Int       | ⚠️       | Signed 32-bit; helper unsigned memerlukan Java 8+. |
| Long      | ⚠️       | Signed 64-bit; helper unsigned memerlukan Java 8+. |
| Float     | ✅        | 32-bit floating point is supported.              |
| Double    | ✅        | 64-bit floating point is supported.              |
| Boolean   | ✅        | Tipe Boolean didukung.                       |

#### Pengodean Teks

| Ketentuan | Terverifikasi | Catatan                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Didukung melalui `int` dan `Character`. |
| ASCII     | ✅        | Charset standar yang dijamin.             |
| CP1252    | ❌        | Tidak dijamin oleh `StandardCharsets`.    |
| UTF-8     | ✅        | Charset standar yang dijamin.             |
| UTF-16LE  | ✅        | Charset standar yang dijamin.             |

#### Status Operasi

| Ketentuan | Terverifikasi | Catatan                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Dapat direpresentasikan oleh tipe khusus.        |
| Context   | ✅        | Dapat direpresentasikan oleh nilai khusus.       |
| Operation | ✅        | Dapat direpresentasikan oleh nilai khusus.       |
| Detail    | ✅        | Dapat direpresentasikan oleh nilai khusus.       |
| Result    | ✅        | Dapat direpresentasikan oleh tipe return khusus. |

### Verifikasi FRELSPEC

#### Koleksi

| Ketentuan | Terverifikasi | Catatan                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Didukung melalui `Set`.       |
| Map       | ✅        | Didukung melalui `Map`.       |
| Array     | ✅        | Array native didukung.   |
| File      | ✅        | Didukung melalui API file.   |
| Stream    | ✅        | Didukung melalui API stream. |

#### Memori

| Ketentuan | Terverifikasi | Catatan                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Address langsung memerlukan Java 22+ FFM.                         |
| Pointer   | ⚠️       | Akses bergaya pointer memerlukan Java 22+ FFM.                     |
| Variable  | ✅        | Deklarasi dan `var` didukung; `var` memerlukan Java 10+. |
| Constant  | ✅        | Didukung melalui `final`.                                     |

#### Operasi

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Direpresentasikan melalui bytecode dan operasi. |
| Procedure   | ✅        | Didukung melalui method `void`.            |
| Function    | ✅        | Didukung melalui method yang mengembalikan nilai.         |

#### Threading

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Didukung melalui aplikasi dan API `Process`. |
| Thread     | ✅        | Didukung melalui `Thread`.                       |
| Dispatcher | ✅        | Didukung melalui API `Executor`.                |

#### Komposit

| Ketentuan | Terverifikasi | Catatan                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Member class didukung.           |
| Object    | ✅        | Object didukung.                 |
| Field     | ✅        | Field didukung.                  |
| Method    | ✅        | Method didukung.                 |
| Property  | ❌        | Tidak ada accessor map eksplisit.              |
| Structure | ✅        | Didukung melalui record; Java 16+.   |
| Class     | ✅        | Class didukung.                 |
| Interface | ✅        | Interface didukung.              |
