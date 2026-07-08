<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->

<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified for Internationalization

Selamat datang di dokumentasi CatalystUI Verification untuk internasionalisasi.

**CatalystUI Verified for Internationalization** menunjukkan bahwa suatu sistem, layanan, framework, aplikasi, atau implementasi telah ditinjau oleh Tim CatalystUI dan dinilai menyediakan dukungan multibahasa yang memadai untuk kumpulan bahasa internasionalisasi CatalystUI yang diwajibkan.

Verifikasi ini bukan peringkat umum atas kualitas terjemahan, gaya penulisan, kedalaman lokalisasi, atau adaptasi budaya. Sebaliknya, verifikasi ini mengidentifikasi apakah sistem yang ditinjau menyediakan fondasi yang stabil dan praktis agar pengguna dapat mengakses fungsionalitas esensialnya dalam bahasa-bahasa yang diwajibkan.

Dengan kata yang lebih sederhana, verifikasi ini menanyakan apakah pengguna dapat menggunakan bagian-bagian esensial dari suatu sistem secara bermakna dalam bahasa yang diwajibkan, dan apakah mereka diberi cara yang masuk akal untuk memilih bahasa yang mereka pahami.

<a id="purpose"></a>
## Tujuan

Internasionalisasi penting karena suatu sistem tidak dapat dianggap dapat diakses secara luas jika makna esensialnya terkunci di balik satu bahasa saja.

CatalystUI dirancang di sekitar kejelasan, konsistensi, dan representasi yang setia atas interaksi manusia-komputer. Bahasa adalah bagian dari interaksi itu. Jika pengguna tidak dapat memahami label, instruksi, peringatan, kontrol, pengaturan, atau konten esensial dari suatu sistem, maka sistem tersebut gagal berkomunikasi dengan jelas, sekalipun fungsionalitas dasarnya secara teknis bekerja.

Internationalization Verification ada untuk mengidentifikasi sistem yang menyediakan dukungan terjemahan yang cukup bagi pengguna di seluruh kumpulan bahasa CatalystUI yang diwajibkan. Tujuannya bukan menuntut terjemahan sempurna untuk setiap kata opsional, pesan tersembunyi bagi pengembang, atau halaman nonesensial. Tujuannya adalah menentukan apakah bagian-bagian esensial dari sistem dapat dipahami dan digunakan oleh orang-orang dalam setiap bahasa yang diwajibkan.

<a id="what-verification-means"></a>
## Arti Verifikasi

Suatu sistem menjadi **CatalystUI Verified for Internationalization** ketika sistem tersebut ditinjau berdasarkan persyaratan yang tercantum dalam bagian ini dan dinyatakan within spec.

Agar dapat diverifikasi, suatu sistem harus menyediakan terjemahan untuk lebih dari 75% bagian esensial yang ditujukan kepada pengguna dalam setiap bahasa yang diwajibkan. Sistem tersebut juga harus menyediakan mekanisme yang masuk akal bagi pengguna akhir untuk mengubah bahasa aktif.

Suatu sistem tidak perlu menerjemahkan setiap pengenal internal, detail implementasi yang ditujukan kepada pengembang, string debug, halaman pemasaran opsional, atau teks dukungan nonesensial. Namun, bagian yang ditujukan kepada pengguna dan diperlukan untuk memahami serta mengoperasikan sistem esensial harus tersedia dalam setiap bahasa yang diwajibkan.

<a id="required-languages"></a>
## Bahasa yang Diwajibkan

Kumpulan bahasa internasionalisasi CatalystUI saat ini dipilih melalui tinjauan praktis terhadap bahasa yang umum dibutuhkan dalam konteks teknologi, termasuk jangkauan penutur global, penggunaan daring yang umum, ekspektasi perangkat lunak multibahasa, dan kebutuhan aksesibilitas regional yang luas.

Kumpulan bahasa ini tidak dimaksudkan untuk mewakili setiap bahasa, setiap dialek, atau setiap varian regional. Sebaliknya, kumpulan ini menetapkan dasar praktis bagi sistem yang mencari kegunaan internasional yang luas di banyak kelompok bahasa paling umum di dunia teknologi.

Kumpulan bahasa internasionalisasi CatalystUI saat ini mencakup locale berikut:

| Locale    | Bahasa                   |
| --------- | ------------------------ |
| `ar-SA`   | Arab (Arab Saudi)        |
| `bn-BD`   | Bengali (Bangladesh)     |
| `de-DE`   | Jerman (Jerman)          |
| `en-GB`   | Inggris (Britania Raya)  |
| `en-IN`   | Inggris (India)          |
| `en-US`   | Inggris (Amerika Serikat) |
| `es-ES`   | Spanyol (Spanyol)        |
| `es-MX`   | Spanyol (Meksiko)        |
| `fa-IR`   | Persia (Iran)            |
| `fr-FR`   | Prancis (Prancis)        |
| `hi-IN`   | Hindi (India)            |
| `id-ID`   | Indonesia (Indonesia)    |
| `it-IT`   | Italia (Italia)          |
| `ja-JP`   | Jepang (Jepang)          |
| `ko-KR`   | Korea (Korea Selatan)    |
| `nl-NL`   | Belanda (Belanda)        |
| `pl-PL`   | Polandia (Polandia)      |
| `pt-BR`   | Portugis (Brasil)        |
| `ru-RU`   | Rusia (Rusia)            |
| `tl-PH`   | Tagalog (Filipina)       |
| `tr-TR`   | Turki (Turki)            |
| `uk-UA`   | Ukraina (Ukraina)        |
| `ur-PK`   | Urdu (Pakistan)          |
| `vi-VN`   | Vietnam (Vietnam)        |
| `zh-CN`   | Tionghoa (Tiongkok)      |
| `zh-Hans` | Tionghoa (Sederhana)     |

Suatu sistem harus menyediakan cakupan terjemahan esensial yang memadai untuk setiap kelompok bahasa yang tercantum agar dapat dianggap within spec.

Namun, varian regional dapat ditinjau dengan fleksibilitas yang wajar ketika perbedaan antarvarian kecil dan tidak secara material memengaruhi kemampuan pengguna untuk memahami atau mengoperasikan sistem. Misalnya, suatu sistem masih dapat memenuhi syarat untuk verifikasi jika menyediakan satu terjemahan bahasa Inggris yang kuat tetapi tidak menerjemahkan setiap varian regional bahasa Inggris secara terpisah, selama makna esensial, navigasi, instruksi, peringatan, dan kontrol tetap jelas bagi pengguna varian yang belum tersedia.

Fleksibilitas ini tidak berlaku ketika varian yang hilang akan menimbulkan kebingungan bermakna, menghilangkan terminologi regional yang penting, merusak perilaku yang sensitif terhadap locale, atau mencegah pengguna memahami bagian esensial dari sistem.

<a id="essential-translation-coverage"></a>
## Cakupan Terjemahan Esensial

Untuk Internationalization Verification, **cakupan terjemahan esensial** merujuk pada bagian-bagian sistem yang secara wajar dibutuhkan pengguna untuk memahami, menavigasi, mengonfigurasi, dan mengoperasikan sistem.

Bagian esensial dapat mencakup:

* navigasi utama
* layar dan tampilan inti
* pengaturan dan preferensi
* label yang ditujukan kepada pengguna
* kontrol yang ditujukan kepada pengguna
* instruksi yang diwajibkan
* peringatan penting
* kesalahan penting
* prompt esensial
* pesan konfirmasi yang diwajibkan
* kontrol pemilihan bahasa
* alur kerja inti yang dibutuhkan untuk penggunaan normal

Suatu sistem dianggap memenuhi persyaratan cakupan terjemahan ketika lebih dari 75% konten esensial yang ditujukan kepada pengguna tersedia dalam setiap bahasa yang diwajibkan.

Ambang ini ada karena pekerjaan internasionalisasi dapat besar, berkelanjutan, dan bergantung pada konteks. Suatu sistem masih dapat berada within spec meskipun sebagian konten nonesensial atau berprioritas lebih rendah belum diterjemahkan. Namun, pengalaman esensial harus tersedia secara bermakna dalam setiap bahasa yang diwajibkan.

<a id="language-selection"></a>
## Pemilihan Bahasa

Sistem yang diverifikasi harus menyediakan cara yang masuk akal bagi pengguna akhir untuk mengubah bahasa aktif.

Mekanisme pemilihan bahasa harus mudah ditemukan, dapat dipahami, dan tersedia tanpa memerlukan pengetahuan teknis. Pengguna seharusnya tidak perlu mengedit berkas konfigurasi, mengubah kode sumber, memasang alat pengembang, atau bergantung pada perilaku yang tidak terdokumentasi hanya untuk mengubah bahasa.

Saat menampilkan opsi bahasa, sistem harus mengidentifikasi setiap bahasa dengan cara yang dapat dipahami baik oleh pengguna yang berbicara bahasa tersebut maupun pengguna yang sedang memakai bahasa lain yang dipilih.

Misalnya, opsi bahasa dapat ditampilkan menggunakan:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Format yang tepat dapat bervariasi, tetapi maksudnya harus tetap sama: pengguna harus dapat mengenali bahasa mereka sendiri, memahami nama bahasa yang sedang ditampilkan bila memungkinkan, dan mengidentifikasi kode locale terkait.

<a id="what-within-spec-means"></a>
## Arti “Within Spec”

Ketika suatu sistem dianggap **within spec**, artinya Tim CatalystUI telah meninjau sistem tersebut secara manual dan menilai bahwa secara wajar sistem itu memenuhi persyaratan internasionalisasi yang dijelaskan oleh kategori verifikasi ini.

Hal ini tidak mengharuskan satu pola implementasi yang kaku. Suatu sistem dapat memenuhi persyaratan melalui berkas resource, tabel terjemahan, routing sadar-locale, aset bahasa terkompilasi, terjemahan berbasis database, paket bahasa runtime, atau mekanisme stabil lain yang sesuai dengan sistem.

Verifikasi berfokus pada kemampuan praktis pengguna untuk mengakses sistem esensial dalam bahasa yang diwajibkan, bukan pada apakah sistem menggunakan satu arsitektur terjemahan tertentu.

<a id="what-verification-does-not-mean"></a>
## Hal yang Tidak Dimaksud oleh Verifikasi

CatalystUI Verified for Internationalization tidak menjamin bahwa setiap terjemahan sempurna, sastrawi, idiomatis, lengkap secara budaya, atau cukup secara hukum untuk setiap wilayah.

Verifikasi ini juga tidak secara otomatis memverifikasi aksesibilitas, tipografi, tata letak kanan-ke-kiri, pemformatan khusus locale, pemformatan mata uang, pemformatan tanggal, kepatuhan hukum, atau persyaratan bisnis regional kecuali hal-hal tersebut termasuk dalam cakupan internasionalisasi yang ditinjau.

Suatu sistem dapat menyediakan cakupan terjemahan yang kuat dan tetap memerlukan tinjauan terpisah untuk aksesibilitas, kualitas lokalisasi, kepatuhan regional, atau perhatian khusus lainnya.

<a id="why-this-verification-exists"></a>
## Mengapa Verifikasi Ini Ada

User interface hanya berguna ketika pengguna dapat memahami apa yang dikomunikasikannya.

Banyak sistem mengklaim dukungan bahasa sementara hanya menerjemahkan sebagian kecil dari pengalaman, menyembunyikan pemilihan bahasa, menghilangkan pesan penting, atau membiarkan alur kerja esensial hanya diterjemahkan sebagian. Ini menciptakan kebingungan dan mencegah pengguna memercayai sistem.

Internationalization Verification ada untuk menetapkan standar yang lebih jelas. Verifikasi ini mengidentifikasi sistem yang melakukan upaya serius dan praktis untuk mendukung pengguna di seluruh kumpulan bahasa CatalystUI yang diwajibkan dan yang menyediakan cara yang masuk akal bagi pengguna untuk memilih bahasa yang mereka butuhkan.

<a id="verification-scope"></a>
## Cakupan Verifikasi

CatalystUI Verification for Internationalization berlaku untuk sistem, layanan, framework, aplikasi, atau implementasi yang ditinjau sebagaimana adanya pada saat verifikasi diterbitkan.

Sistem yang diverifikasi menyediakan cakupan terjemahan esensial yang memadai untuk bahasa-bahasa yang diwajibkan. Hal ini tidak menjamin bahwa setiap halaman, fitur, rilis, plugin, ekstensi, atau integrasi pihak ketiga di masa mendatang otomatis berada within spec.

Produk, modul, layanan, paket bahasa, atau revisi besar yang terpisah mungkin memerlukan tinjauan mereka sendiri tergantung pada kategori verifikasi yang diminta.

<a id="verification-validity"></a>
## Validitas Verifikasi

CatalystUI Verification hanya berlaku untuk keadaan sistem yang ditinjau pada saat verifikasi diterbitkan.

Suatu sistem dapat mempertahankan verifikasinya dalam pembaruan berikutnya selama mempertahankan fondasi internasionalisasi yang telah diverifikasi. Perubahan kata kecil, tambahan terjemahan, dan pembaruan konten biasa tidak secara otomatis membatalkan verifikasi.

Tinjauan baru mungkin diperlukan jika suatu sistem menghapus dukungan bahasa yang diwajibkan, merusak pemilihan bahasa, secara substansial mengurangi cakupan terjemahan esensial, atau mengubah arsitektur internasionalisasinya dengan cara yang memengaruhi perilaku yang telah diverifikasi.

Dengan kata lain, meningkatkan dukungan terjemahan biasanya tidak masalah. Merusak dasar multibahasa yang telah diverifikasi mungkin memerlukan tinjauan.

<a id="verified-systems"></a>
## Sistem Terverifikasi

Sistem yang diketahui telah diverifikasi untuk internasionalisasi dicantumkan secara terpisah pada halaman CatalystUI Verified yang sesuai.
