<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->
<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

# Detail Verifikasi

## C#

### Ikhtisar

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Bahasa pemrograman C# telah diverifikasi terhadap spesifikasi FDEFSPEC (Rev. 1) dan FRELSPEC (Rev. 1) per 7 Juli 2026.

#### Pernyataan Itikad Baik

Kami percaya dengan itikad baik bahwa bahasa pemrograman C# dapat secara wajar merepresentasikan konsep dan ketentuan yang didefinisikan dalam spesifikasi berikut, dan dapat digunakan untuk mengimplementasikan sistem yang mematuhi spesifikasi ini.

#### Asumsi Peninjauan

Peninjauan ini mengasumsikan dukungan C# dan .NET modern ketika fitur yang bergantung pada versi dicatat.

### Peringatan

* Dukungan CP1252 tersedia melalui provider code pages resmi .NET, tetapi mungkin memerlukan registrasi provider atau package tambahan bergantung pada runtime target.
* Perilaku pointer unsafe mungkin memerlukan otorisasi unsafe secara eksplisit.

### Kegagalan

* Tidak ada kegagalan FDEFSPEC atau FRELSPEC yang diketahui ditemukan selama verifikasi ini.

### Verifikasi FDEFSPEC

#### Numerik

| Ketentuan | Terverifikasi | Catatan                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | Tidak ada numerik 1-bit; perlu widening.                |
| Nibble    | ⚠️       | Tidak ada numerik 4-bit; perlu widening.                |
| Byte      | ✅        | Didukung melalui `byte` dan `sbyte`.   |
| Short     | ✅        | Didukung melalui `short` dan `ushort`. |
| Int       | ✅        | Didukung melalui `int` dan `uint`.     |
| Long      | ✅        | Didukung melalui `long` dan `ulong`.   |
| Float     | ✅        | Didukung melalui `float`.              |
| Double    | ✅        | Didukung melalui `double`.             |
| Boolean   | ✅        | Didukung melalui `bool`.               |

#### Pengodean Teks

| Ketentuan | Terverifikasi | Catatan                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | Didukung melalui numerik dan `Rune`. |
| ASCII     | ✅        | Didukung melalui `Encoding.ASCII`.    |
| CP1252    | ⚠️       | Memerlukan provider code pages.          |
| UTF-8     | ✅        | Didukung melalui `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | Didukung melalui `Encoding.Unicode`.  |

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

| Ketentuan | Terverifikasi | Catatan                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Didukung melalui `HashSet<T>`.              |
| Map       | ✅        | Didukung melalui `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Array native didukung.                 |
| File      | ✅        | Didukung melalui API file.                 |
| Stream    | ✅        | Didukung melalui `Stream`.                  |

#### Memori

| Ketentuan | Terverifikasi | Catatan                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Didukung melalui reference dan pointer. |
| Pointer   | ✅        | Didukung melalui unsafe pointer.         |
| Variable  | ✅        | Variable didukung.                   |
| Constant  | ✅        | Didukung melalui `const` dan `readonly`.  |

#### Operasi

| Provision   | Verified | Notes                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Direpresentasikan melalui IL dan operasi. |
| Procedure   | ✅        | Didukung melalui method `void`.      |
| Function    | ✅        | Didukung melalui method yang mengembalikan nilai.   |

#### Threading

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Didukung melalui aplikasi dan API `Process`. |
| Thread     | ✅        | Didukung melalui `Thread`.                       |
| Dispatcher | ✅        | Didukung melalui task dan scheduler.           |

#### Komposit

| Ketentuan | Terverifikasi | Catatan                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Member type didukung.        |
| Object    | ✅        | Object didukung.             |
| Field     | ✅        | Field didukung.              |
| Method    | ✅        | Method didukung.             |
| Property  | ✅        | Property didukung secara native. |
| Structure | ✅        | Structure didukung secara native. |
| Class     | ✅        | Class didukung.             |
| Interface | ✅        | Interface didukung.          |
