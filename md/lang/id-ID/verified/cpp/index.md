<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->
<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

# Detail Verifikasi

## C++

### Ikhtisar

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Bahasa pemrograman C++ telah diverifikasi terhadap spesifikasi FDEFSPEC (Rev. 1) dan FRELSPEC (Rev. 1) per 7 Juli 2026.

#### Pernyataan Itikad Baik

Kami percaya dengan itikad baik bahwa bahasa pemrograman C++ dapat secara wajar merepresentasikan konsep dan ketentuan yang didefinisikan dalam spesifikasi berikut, dan dapat digunakan untuk mengimplementasikan sistem yang mematuhi spesifikasi ini.

#### Asumsi Peninjauan

Peninjauan ini mengasumsikan dukungan C++ standar modern ketika fitur yang bergantung pada versi dicatat. Dukungan integer exact-width mengasumsikan tipe `<cstdint>` yang bersesuaian disediakan oleh implementasi.

Peninjauan ini memperlakukan C++ sebagai bahasa pemrograman sistem dengan dukungan langsung untuk representasi tingkat rendah, pemodelan object, kontrol memori, generic programming, dan eksekusi concurrent.

### Peringatan

* Tipe integer exact-width bergantung pada dukungan implementasi.
* CP1252 dapat direpresentasikan byte demi byte, tetapi tidak ada codec standar bernama yang disediakan.
* Serialisasi UTF-16LE memerlukan penanganan byte-order eksplisit.
* Beberapa fitur concurrency dan karakter memerlukan revisi C++ modern.

### Kegagalan

* Tidak ada kegagalan FDEFSPEC atau FRELSPEC yang diketahui ditemukan selama verifikasi ini.

### Verifikasi FDEFSPEC

#### Numerik

| Ketentuan | Terverifikasi | Catatan                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Gunakan bit-field atau mask.                    |
| Nibble    | ⚠️       | Gunakan bit-field atau mask.                    |
| Byte      | ✅        | Didukung melalui `std::byte`.              |
| Short     | ✅        | Didukung melalui `int16_t` dan `uint16_t`. |
| Int       | ✅        | Didukung melalui `int32_t` dan `uint32_t`. |
| Long      | ✅        | Didukung melalui `int64_t` dan `uint64_t`. |
| Float     | ✅        | Didukung melalui `float`.                  |
| Double    | ✅        | Didukung melalui `double`.                 |
| Boolean   | ✅        | Didukung melalui `bool`.                   |

#### Pengodean Teks

| Ketentuan | Terverifikasi | Catatan                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Didukung melalui `char32_t`.        |
| ASCII     | ✅        | Dapat direpresentasikan sebagai nilai byte.        |
| CP1252    | ⚠️        | Memerlukan mapping byte eksplisit.      |
| UTF-8     | ✅        | Didukung melalui `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Memerlukan penanganan byte-order.        |

#### Status Operasi

| Ketentuan | Terverifikasi | Catatan                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Dapat direpresentasikan oleh enum.           |
| Context   | ✅        | Dapat direpresentasikan oleh nilai.           |
| Operation | ✅        | Dapat direpresentasikan oleh nilai.           |
| Detail    | ✅        | Dapat direpresentasikan oleh nilai.           |
| Result    | ✅        | Dapat direpresentasikan oleh struct atau class. |

### Verifikasi FRELSPEC

#### Koleksi

| Ketentuan | Terverifikasi | Catatan                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Didukung melalui `std::set`.              |
| Map       | ✅        | Didukung melalui `std::map`.              |
| Array     | ✅        | Didukung melalui array dan `std::array`. |
| File      | ✅        | Didukung melalui file stream.            |
| Stream    | ✅        | Didukung melalui iostream.               |

#### Memori

| Ketentuan | Terverifikasi | Catatan                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Address didukung.                   |
| Pointer   | ✅        | Pointer didukung.                    |
| Variable  | ✅        | Variable didukung.                   |
| Constant  | ✅        | Didukung melalui `const` dan `constexpr`. |

#### Operasi

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Direpresentasikan melalui operasi mesin. |
| Procedure   | ✅        | Didukung melalui function `void`.     |
| Function    | ✅        | Didukung melalui function yang mengembalikan nilai.  |

#### Threading

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Didukung melalui eksekusi hosted.      |
| Thread     | ✅        | Didukung melalui `std::thread`; C++11+. |
| Dispatcher | ✅        | Didukung melalui async dan scheduler.  |

#### Komposit

| Ketentuan | Terverifikasi | Catatan                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Member class didukung.            |
| Object    | ✅        | Object didukung.                  |
| Field     | ✅        | Field didukung.                   |
| Method    | ✅        | Method didukung.                  |
| Property  | ✅        | Map Get/Set dapat direpresentasikan.        |
| Structure | ✅        | Structure didukung secara native.      |
| Class     | ✅        | Class didukung secara native.         |
| Interface | ✅        | Dapat direpresentasikan oleh abstract class. |
