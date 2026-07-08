<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->
<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

# Detail Peninjauan

## JavaScript

### Ikhtisar

Bahasa pemrograman JavaScript telah ditinjau terhadap spesifikasi FDEFSPEC (Rev. 1) dan FRELSPEC (Rev. 1) per 7 Juli 2026.

#### Pernyataan Peninjauan

Walaupun JavaScript dapat merepresentasikan beberapa konsep yang diperlukan melalui object, function, array, dan perilaku bahasa bawaan, mekanisme ini tidak cukup untuk memenuhi spesifikasi CatalystUI yang berlaku pada tingkat bahasa.

Peninjauan ini mengevaluasi JavaScript itu sendiri, bukan ekosistem JavaScript di sekitarnya. Browser API, Node.js API, Deno API, Bun API, Web API, TypeScript, WebAssembly, library eksternal, dan validasi khusus tidak diperlakukan sebagai dukungan tingkat bahasa.

Karena JavaScript tidak memiliki banyak tipe numerik scalar fixed-width yang diperlukan, tidak menyediakan text encoding yang diperlukan sebagai fitur bahasa, dan tidak mendefinisikan beberapa konstruksi sistem, memori, threading, dan komposit yang diperlukan, kami tidak percaya JavaScript menyediakan fondasi yang cukup stabil untuk implementasi yang mematuhi CatalystUI tanpa infrastruktur tambahan yang signifikan.

Akibatnya, JavaScript belum diberikan status CatalystUI Verified untuk Bahasa Pemrograman.

#### Asumsi Peninjauan

Peninjauan ini menerapkan standar tingkat bahasa yang ketat. Jika suatu ketentuan tidak secara eksplisit didukung oleh JavaScript itu sendiri, ketentuan tersebut ditandai sebagai tidak terverifikasi.

API yang disediakan host, perilaku implementation-specific, library eksternal, transpiler, sistem tipe, dan validasi runtime khusus dikecualikan dari verifikasi.

### Peringatan

* JavaScript dapat merepresentasikan banyak nilai numerik melalui `Number`, tetapi `Number` adalah tipe numerik floating point 64-bit.
* JavaScript menyediakan `BigInt`, tetapi `BigInt` bersifat arbitrary-width.
* Typed array menyediakan tampilan penyimpanan biner, bukan tipe bahasa scalar.
* String JavaScript menggunakan unit kode UTF-16, bukan nilai text encoding eksplisit.
* `const` melindungi binding, bukan nilai object.

### Kegagalan

* JavaScript tidak menyediakan sebagian besar tipe numerik scalar fixed-width yang diperlukan.
* JavaScript tidak menyediakan tipe floating point scalar 32-bit khusus.
* JavaScript tidak menyediakan ASCII, CP1252, UTF-8, atau UTF-16LE sebagai text encoding tingkat bahasa.
* JavaScript tidak menyediakan konstruksi file atau stream tingkat bahasa.
* JavaScript tidak menyediakan konstruksi address atau pointer tingkat bahasa.
* JavaScript tidak menyediakan konstruksi process, thread, atau dispatcher tingkat bahasa.
* Property JavaScript tidak menyediakan keyed member eksplisit yang didukung oleh accessor map Get/Set yang diperlukan.
* JavaScript tidak menyediakan structure atau interface.

### Verifikasi FDEFSPEC

#### Numerik

| Ketentuan | Terverifikasi | Catatan                          |
| --------- | -------- | ------------------------------ |
| Bit       | ❌        | Tidak ada tipe numerik 1-bit.         |
| Nibble    | ❌        | Tidak ada tipe numerik 4-bit.         |
| Byte      | ❌        | Tidak ada tipe integer scalar 8-bit.  |
| Short     | ❌        | Tidak ada tipe integer scalar 16-bit. |
| Int       | ❌        | Tidak ada tipe integer scalar 32-bit. |
| Long      | ❌        | Tidak ada tipe integer scalar 64-bit. |
| Float     | ❌        | Tidak ada tipe float scalar 32-bit.   |
| Double    | ✅        | Didukung melalui `Number`.    |
| Boolean   | ✅        | Didukung melalui `boolean`.   |

#### Pengodean Teks

| Ketentuan | Terverifikasi | Catatan                        |
| --------- | -------- | ---------------------------- |
| Codepoint | ❌        | Tidak ada tipe codepoint khusus. |
| ASCII     | ❌        | Bukan tingkat bahasa.          |
| CP1252    | ❌        | Bukan tingkat bahasa.          |
| UTF-8     | ❌        | Bukan tingkat bahasa.          |
| UTF-16LE  | ❌        | Bukan tingkat bahasa.          |

#### Status Operasi

| Ketentuan | Terverifikasi | Catatan                           |
| --------- | -------- | ------------------------------- |
| Status    | ⚠️       | Dapat direpresentasikan, tetapi tidak dapat diberlakukan. |
| Context   | ⚠️       | Dapat direpresentasikan, tetapi tidak dapat diberlakukan. |
| Operation | ⚠️       | Dapat direpresentasikan, tetapi tidak dapat diberlakukan. |
| Detail    | ⚠️       | Dapat direpresentasikan, tetapi tidak dapat diberlakukan. |
| Result    | ⚠️       | Memerlukan validasi runtime.    |

### Verifikasi FRELSPEC

#### Koleksi

| Ketentuan | Terverifikasi | Catatan                    |
| --------- | -------- | ------------------------ |
| Set       | ✅        | Didukung melalui `Set`. |
| Map       | ✅        | Didukung melalui `Map`. |
| Array     | ✅        | Array didukung.    |
| File      | ❌        | Bukan tingkat bahasa.      |
| Stream    | ❌        | Bukan tingkat bahasa.      |

#### Memori

| Ketentuan | Terverifikasi | Catatan                           |
| --------- | -------- | ------------------------------- |
| Address   | ❌        | Tidak ada dukungan address.             |
| Pointer   | ❌        | Tidak ada dukungan pointer.             |
| Variable  | ✅        | Variable didukung.        |
| Constant  | ⚠️       | `const` hanya melindungi binding. |

#### Operasi

| Provision   | Verified | Notes                            |
| ----------- | -------- | -------------------------------- |
| Instruction | ❌        | Tidak ada tipe instruction yang didefinisikan.     |
| Procedure   | ❌        | Function selalu mengembalikan nilai. |
| Function    | ✅        | Function didukung.         |

#### Threading

| Provision  | Verified | Notes                       |
| ---------- | -------- | --------------------------- |
| Process    | ❌        | Bukan tingkat bahasa.         |
| Thread     | ⚠️        | Direpresentasikan melalui agent. |
| Dispatcher | ❌        | Memerlukan scheduling host.   |


#### Komposit

| Ketentuan | Terverifikasi | Catatan                                 |
| --------- | -------- | ------------------------------------- |
| Member    | ✅        | Member object didukung.         |
| Object    | ✅        | Object didukung.                |
| Field     | ✅        | Property data dapat merepresentasikan field. |
| Method    | ✅        | Method didukung.                |
| Property  | ❌        | Tidak ada accessor map eksplisit.             |
| Structure | ❌        | Tidak ada dukungan structure.                 |
| Class     | ✅        | Sintaks class didukung.            |
| Interface | ❌        | Tidak ada dukungan interface.                 |
