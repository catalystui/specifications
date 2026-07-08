<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->
<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

# Detail Peninjauan

## Python

### Ikhtisar

Bahasa pemrograman Python telah ditinjau terhadap spesifikasi FDEFSPEC (Rev. 1) dan FRELSPEC (Rev. 1) per 7 Juli 2026.

#### Pernyataan Peninjauan

Walaupun Python dapat merepresentasikan banyak konsep yang diperlukan melalui tipe bawaan, object, function, class, modul library standar, dan validasi khusus, mekanisme ini tidak cukup untuk memenuhi spesifikasi CatalystUI yang berlaku pada tingkat bahasa.

Python menyediakan dukungan kuat untuk text encoding, file, stream, object, function, class, property, process, thread, dan eksekusi ter-dispatch melalui perilaku bawaan dan library standarnya. Namun, Python tidak menyediakan tipe numerik scalar fixed-width yang diperlukan, tidak mendefinisikan constant sejati, dan bergantung pada perilaku runtime dinamis untuk beberapa konstruksi yang dapat diekspresikan lebih langsung oleh bahasa terverifikasi lainnya.

Karena hal ini, kami tidak percaya Python menyediakan fondasi yang cukup stabil untuk implementasi yang mematuhi CatalystUI tanpa infrastruktur tambahan yang signifikan.

Akibatnya, Python belum diberikan status CatalystUI Verified untuk Bahasa Pemrograman.

#### Asumsi Peninjauan

Peninjauan ini mengevaluasi Python itu sendiri dan library standar yang dibundel bersamanya.

Package pihak ketiga, extension implementation-specific, modul native opsional, type checker eksternal, transpiler, dan framework runtime khusus tidak diperlakukan sebagai dukungan tingkat bahasa.

### Peringatan

* Python menyediakan integer berpresisi tak terbatas, bukan primitive integer fixed-width.
* `float` Python biasanya presisi ganda, tetapi bukan keluarga fixed-width tersendiri.
* Beberapa perilaku memori tingkat rendah mungkin memerlukan `ctypes` atau perilaku implementation-specific.
* Type hint Python tidak diberlakukan saat runtime.
* Python mendukung property, tetapi perilaku setter dapat dihilangkan.
* Python dapat memodelkan beberapa structure melalui fitur library standar, tetapi bukan sebagai tipe structure native.

### Kegagalan

* Python tidak menyediakan sebagian besar tipe numerik scalar fixed-width yang diperlukan.
* Python tidak menyediakan tipe floating point scalar 32-bit khusus.
* Python tidak menyediakan constant sejati pada tingkat bahasa.
* Python tidak mendefinisikan procedure secara terpisah dari function.
* Python tidak menyediakan dukungan pointer native.
* Python tidak menyediakan dukungan interface native.

### Verifikasi FDEFSPEC

#### Numerik

| Ketentuan | Terverifikasi | Catatan                                |
| --------- | -------- | ------------------------------------ |
| Bit       | ❌        | Tidak ada tipe numerik 1-bit.               |
| Nibble    | ❌        | Tidak ada tipe numerik 4-bit.               |
| Byte      | ❌        | Tidak ada tipe integer scalar 8-bit.        |
| Short     | ❌        | Tidak ada tipe integer scalar 16-bit.       |
| Int       | ❌        | Tidak ada tipe integer scalar 32-bit.       |
| Long      | ❌        | Tidak ada tipe integer scalar 64-bit.       |
| Float     | ❌        | Tidak ada tipe float scalar 32-bit.         |
| Double    | ⚠️       | `float` is usually double precision. |
| Boolean   | ✅        | Didukung melalui `bool`.            |

#### Pengodean Teks

| Ketentuan | Terverifikasi | Catatan                            |
| --------- | -------- | -------------------------------- |
| Codepoint | ✅        | Strings use Unicode code points. |
| ASCII     | ✅        | Supported codec.                 |
| CP1252    | ✅        | Supported codec.                 |
| UTF-8     | ✅        | Supported codec.                 |
| UTF-16LE  | ✅        | Supported codec.                 |

#### Status Operasi

| Ketentuan | Terverifikasi | Catatan                       |
| --------- | -------- | --------------------------- |
| Status    | ⚠️       | Memerlukan validasi khusus. |
| Context   | ⚠️       | Memerlukan validasi khusus. |
| Operation | ⚠️       | Memerlukan validasi khusus. |
| Detail    | ⚠️       | Memerlukan validasi khusus. |
| Result    | ⚠️       | Memerlukan validasi khusus. |

### Verifikasi FRELSPEC

#### Koleksi

| Ketentuan | Terverifikasi | Catatan                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Didukung melalui `set`.       |
| Map       | ✅        | Didukung melalui `dict`.      |
| Array     | ✅        | Didukung melalui sequence.   |
| File      | ✅        | Didukung melalui API file.   |
| Stream    | ✅        | Didukung melalui API stream. |

#### Memori

| Ketentuan | Terverifikasi | Catatan                        |
| --------- | -------- | ---------------------------- |
| Address   | ⚠️       | Hanya identitas object.        |
| Pointer   | ❌        | Tidak ada dukungan pointer native.   |
| Variable  | ✅        | Name binding didukung. |
| Constant  | ❌        | Tidak ada constant sejati.           |

#### Operasi

| Provision   | Verified | Notes                             |
| ----------- | -------- | --------------------------------- |
| Instruction | ⚠️       | Bytecode berada pada tingkat implementasi. |
| Procedure   | ❌        | Function mengembalikan `None`.          |
| Function    | ✅        | Function didukung.          |

#### Threading

| Provision  | Verified | Notes                            |
| ---------- | -------- | -------------------------------- |
| Process    | ✅        | Didukung melalui API process.  |
| Thread     | ✅        | Didukung melalui `threading`.   |
| Dispatcher | ✅        | Didukung melalui API executor. |

#### Komposit

| Ketentuan | Terverifikasi | Catatan                            |
| --------- | -------- | -------------------------------- |
| Member    | ✅        | Member object didukung.    |
| Object    | ✅        | Object didukung.           |
| Field     | ✅        | Attribute dapat merepresentasikan field. |
| Method    | ✅        | Method didukung.           |
| Property  | ⚠️       | Dukungan getter/setter ada.    |
| Structure | ⚠️       | Hanya model library standar.    |
| Class     | ✅        | Class didukung.           |
| Interface | ❌        | Tidak ada dukungan interface native.     |
