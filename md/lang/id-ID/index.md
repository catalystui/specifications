<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->
<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

![CatalystUI Verified for Programming Languages](/images/verification/verified-logo-languages.png)

# CatalystUI Verified untuk Bahasa Pemrograman

Selamat datang di dokumentasi CatalystUI Verification untuk bahasa pemrograman.

**CatalystUI Verified untuk Bahasa Pemrograman** menunjukkan bahwa suatu bahasa pemrograman telah ditinjau oleh CatalystUI Team dan dinilai menyediakan representasi data dasar serta struktur relasional yang diperlukan untuk mengekspresikan sistem yang kompatibel dengan CatalystUI.

Verifikasi ini bukan pemeringkatan umum bahasa pemrograman. Verifikasi ini tidak menentukan apakah suatu bahasa lebih baik, lebih cepat, lebih mudah, lebih baru, lebih populer, atau lebih menyenangkan dibanding bahasa lain. Sebaliknya, verifikasi ini mengidentifikasi apakah bahasa tersebut menyediakan fondasi yang stabil dan praktis untuk spesifikasi yang diperlukan oleh CatalystUI Verification.

Dengan kata yang lebih sederhana, verifikasi ini menanyakan apakah suatu bahasa pemrograman dapat merepresentasikan data dasar dan hubungan dasar yang menjadi sandaran CatalystUI secara setia.

## Tujuan

Bahasa pemrograman membentuk fondasi representasional di bawah setiap implementasi CatalystUI. Sebelum sebuah framework, library, runtime, aplikasi, atau service dapat mengikuti CatalystUI Stack, bahasa yang digunakan untuk membangunnya harus mampu mengekspresikan konsep-konsep dasar yang menjadi sandaran model tersebut.

Untuk bahasa pemrograman, hal ini terutama berarti dua hal:

1. Bahasa tersebut harus mampu merepresentasikan data dasar.
2. Bahasa tersebut harus mampu merepresentasikan hubungan dasar antar-data.

Hal-hal ini didefinisikan melalui spesifikasi dasar CatalystUI. FDEFSPEC mendefinisikan representasi data dasar yang diharapkan. FRELSPEC mendefinisikan relasi dasar yang diharapkan di antara representasi tersebut, termasuk koleksi, hubungan memori, operasi, hubungan threading, dan komposit.

Bahasa pemrograman yang terverifikasi memberi pengembang kejelasan dan kendali yang cukup untuk membangun sistem yang kompatibel dengan CatalystUI tanpa bergantung pada workaround yang rapuh, tidak jelas, atau tidak stabil untuk konsep-konsep dasar yang dibutuhkan CatalystUI.

## Arti Verifikasi

Sebuah bahasa pemrograman menjadi **CatalystUI Verified** ketika bahasa tersebut ditinjau terhadap spesifikasi yang tercantum dalam bagian ini dan dinilai berada within spec.

Untuk Programming Language Verification, peninjauan difokuskan pada apakah bahasa tersebut dapat mengekspresikan persyaratan dasar yang didefinisikan oleh spesifikasi yang berlaku. Ini tidak berarti bahasa itu sendiri merupakan implementasi CatalystUI. Artinya, bahasa tersebut menyediakan fondasi yang sesuai untuk membangun implementasi yang kompatibel dengan CatalystUI.

Sebuah bahasa tidak perlu memenuhi persyaratan ini dengan cara yang sama seperti bahasa lain. Bahasa yang berbeda menggunakan sintaks, sistem tipe, library standar, compiler, runtime, dan pola desain yang berbeda. CatalystUI Verification mengizinkan perbedaan tersebut selama konsep yang diperlukan dapat diekspresikan dengan jelas, andal, dan konsisten.

## Arti “Within Spec”

Ketika sebuah bahasa pemrograman dianggap **within spec**, artinya CatalystUI Team telah meninjau bahasa tersebut secara manual dan menilai bahwa perilaku yang diperlukan sebagaimana dijelaskan oleh spesifikasi yang berlaku dapat diekspresikan di dalam bahasa tersebut.

Ini tidak memerlukan satu pola implementasi yang kaku. Sebuah bahasa dapat memenuhi persyaratan melalui primitive bawaan, fitur library standar, perilaku compiler, perilaku runtime, jaminan yang terdokumentasi, atau mekanisme stabil lain yang sesuai untuk bahasa tersebut.

Verifikasi berkaitan dengan kemampuan praktis untuk merepresentasikan dan mempertahankan makna spesifikasi, bukan apakah bahasa tersebut menggunakan nama, struktur, sintaks, atau desain internal yang persis sama seperti teks spesifikasi.

## Mengapa Verifikasi Ini Ada

CatalystUI dirancang berdasarkan kejelasan, konsistensi, dan representasi yang setia atas cara manusia dan komputer berinteraksi. Bahasa pemrograman penting karena bahasa menentukan apa yang secara realistis dapat diekspresikan oleh pengembang, seberapa aman sistem tersebut dapat dimodelkan, dan seberapa jelas implementasi tingkat lebih tinggi dapat dibangun.

Jika suatu bahasa tidak dapat menyediakan konsep dasar yang diperlukan secara stabil, implementasi CatalystUI tingkat lebih tinggi menjadi lebih sulit dipercaya. Pengembang dapat terdorong ke arah abstraksi yang tidak jelas, perilaku yang tidak dapat diprediksi, dependensi yang rapuh, atau penulisan ulang yang tidak perlu hanya untuk mengekspresikan ide yang seharusnya dapat diandalkan sejak awal.

Programming Language Verification ada untuk mengidentifikasi bahasa mana yang menyediakan fondasi yang cukup kuat bagi pekerjaan CatalystUI. Ini memberi pengembang, perancang bahasa, dan organisasi pemahaman yang lebih jelas tentang apakah suatu bahasa cocok untuk membangun sistem yang kompatibel dengan CatalystUI.

## Bagaimana Sebuah Bahasa Menjadi Terverifikasi

Untuk menjadi **CatalystUI Verified untuk Bahasa Pemrograman**, sebuah bahasa harus ditinjau terhadap spesifikasi yang tercantum dalam bagian ini.

Proses umumnya adalah:

1. Spesifikasi CatalystUI yang berlaku diidentifikasi.
2. Bahasa ditinjau terhadap setiap spesifikasi yang diperlukan.
3. CatalystUI Team menentukan apakah bahasa tersebut memenuhi maksud dan persyaratan spesifikasi.
4. Jika bahasa dinilai berada within spec, bahasa tersebut dapat diberikan CatalystUI Verification.
5. Setelah terverifikasi, bahasa tersebut dapat dicantumkan pada halaman [Verified Languages](/verified/).

Peninjauan dapat mempertimbangkan dokumentasi resmi bahasa, perilaku library standar, perilaku compiler, perilaku runtime, contoh implementasi, test case, dan bukti lain yang diperlukan untuk menentukan apakah bahasa memenuhi persyaratan.

Perilaku compiler dan runtime dapat dipertimbangkan selama peninjauan ketika perilaku tersebut merupakan bagian dari cara bahasa digunakan secara umum dan resmi. Namun, memverifikasi bahasa pemrograman tidak secara otomatis memverifikasi setiap compiler, runtime, package, framework, library, aplikasi, atau tool dalam ekosistem bahasa tersebut.

## Spesifikasi yang Berlaku

Spesifikasi yang tercantum dalam bagian ini mendefinisikan persyaratan yang digunakan untuk Programming Language Verification.

Untuk bahasa pemrograman, fondasi aktif saat ini berpusat pada kategori spesifikasi berikut:

* **FDEFSPEC**, yang mendefinisikan representasi data dasar.
* **FRELSPEC**, yang mendefinisikan relasi dasar antar-representasi data.

Bersama-sama, spesifikasi ini menetapkan fondasi minimum yang diperlukan agar suatu bahasa pemrograman dapat merepresentasikan sistem yang kompatibel dengan CatalystUI.

Spesifikasi tambahan dapat diperkenalkan kemudian untuk kategori verifikasi yang lebih khusus. Spesifikasi tersebut dapat mendefinisikan persyaratan implementasi tingkat lebih tinggi, platform, aksesibilitas, internasionalisasi, framework, service, atau runtime. Namun, spesifikasi yang lebih baru tersebut dibangun di atas fondasi ini, bukan menggantikannya.

Sebuah bahasa pemrograman menjadi terverifikasi dengan memenuhi spesifikasi yang diperlukan untuk kategori ini. Bahasa tersebut tidak diharapkan memenuhi persyaratan khusus implementasi yang tidak terkait kecuali persyaratan tersebut ditambahkan ke Programming Language Verification.

## Cakupan Verifikasi

CatalystUI Verification untuk Bahasa Pemrograman berlaku pada bahasa pemrograman sebagaimana telah ditinjau.

Bahasa yang terverifikasi menyediakan fondasi yang sesuai untuk pengembangan yang kompatibel dengan CatalystUI. Ini tidak menjamin bahwa setiap project yang ditulis dalam bahasa tersebut mengikuti CatalystUI dengan benar, dan juga tidak secara otomatis memverifikasi ekosistem di sekitarnya.

Tool, library, framework, runtime, aplikasi, service, atau implementasi terpisah mungkin memerlukan peninjauan sendiri bergantung pada kategori verifikasi yang diminta.

Karena itu, Programming Language Verification harus dipahami sebagai pemeriksaan fondasi. Verifikasi ini mengonfirmasi bahwa bahasa dapat merepresentasikan konsep yang diperlukan. Verifikasi ini tidak mengonfirmasi bahwa setiap penggunaan bahasa menerapkan konsep tersebut dengan benar.

## Masa Berlaku Verifikasi

CatalystUI Verification hanya berlaku pada keadaan bahasa pemrograman yang ditinjau pada saat verifikasi diterbitkan.

Bahasa pemrograman diperlakukan sebagai kasus khusus karena banyak bahasa menjaga kompatibilitas di berbagai versi. Sebuah bahasa dapat mempertahankan verifikasinya di versi-versi berikutnya selama bahasa tersebut menjaga backward compatibility dengan fitur, primitive, representasi, dan perilaku yang menjadi dasar peninjauan awal.

Fitur bahasa baru saja tidak membatalkan verifikasi. Versi masa depan mungkin memerlukan peninjauan baru hanya jika versi tersebut menghapus, merusak, atau mengubah secara substansial fondasi yang telah terverifikasi.

Dengan kata lain, memperluas sebuah bahasa biasanya tidak masalah. Merusak basis yang telah terverifikasi dapat memerlukan peninjauan.

## Bahasa Terverifikasi

Bahasa pemrograman terverifikasi yang diketahui dicantumkan secara terpisah pada halaman [Verified Languages](/verified/).
