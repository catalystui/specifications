<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->

<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

# I18NSPEC

<br/>

> **Spesifikasi Internasionalisasi**<br/>
> Revisi 1<br/>
> 8 Juli 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Definisi, persyaratan, dan konsep yang disajikan di sini menjelaskan dukungan internasionalisasi praktis dan dapat diungkapkan kembali secara bebas.

<a id="introduction"></a>
## Pendahuluan

**Spesifikasi Internasionalisasi (I18NSPEC)** menetapkan konsep inti, terminologi, dan persyaratan yang digunakan untuk mengevaluasi dukungan multibahasa dalam ekosistem CatalystUI. Tujuannya adalah menyediakan standar yang jelas untuk menentukan apakah suatu sistem, layanan, framework, aplikasi, atau implementasi menyediakan dukungan bahasa yang memadai agar dapat dianggap within spec.

Internasionalisasi penting karena sebuah user interface tidak dapat berkomunikasi dengan jelas jika makna esensialnya hanya tersedia dalam satu bahasa. Suatu sistem mungkin berfungsi secara teknis, tetapi jika pengguna tidak dapat memahami label, instruksi, kontrol, pengaturan, peringatan, kesalahan, atau alur kerja intinya, maka sistem tersebut gagal menyediakan interface yang bermakna bagi pengguna tersebut.

Spesifikasi ini tidak berusaha mengukur kualitas terjemahan yang sempurna, gaya sastra, adaptasi budaya, kepatuhan hukum, atau lokalisasi regional yang lengkap. Sebaliknya, spesifikasi ini mendefinisikan fondasi multibahasa minimum yang diperlukan agar pengguna dapat secara bermakna mengakses dan mengoperasikan bagian-bagian esensial suatu sistem di seluruh kumpulan locale CatalystUI yang diwajibkan.

Dengan kata yang lebih sederhana, I18NSPEC mengajukan tiga pertanyaan utama:

1. Dapatkah pengguna mengakses bagian-bagian esensial sistem dalam setiap bahasa yang diwajibkan?
2. Dapatkah pengguna memilih bahasa yang mereka pahami secara wajar?
3. Apakah sistem mempertahankan cukup makna lintas bahasa agar tetap dapat digunakan?

> [!IMPORTANT]
>
> I18NSPEC mendefinisikan persyaratan internasionalisasi untuk verifikasi. Ini bukan spesifikasi terpisah untuk setiap bahasa. Setiap locale yang diwajibkan diperiksa terhadap spesifikasi yang sama.

<a id="table-of-contents"></a>
## Daftar Isi

* [I18NSPEC](#i18nspec)

  * [Pendahuluan](#introduction)
  * [Daftar Isi](#table-of-contents)
  * [Konformitas](#conformance)
  * [Kumpulan Locale yang Diwajibkan](#required-locale-set)
  * [Konten yang Ditujukan kepada Pengguna](#user-facing-content)

    * [Konten yang Ditujukan kepada Pengguna](#user-facing-content-1)
    * [Konten Esensial yang Ditujukan kepada Pengguna](#essential-user-facing-content)
    * [Konten Kritis yang Ditujukan kepada Pengguna](#critical-user-facing-content)
    * [Konten Nonesensial](#nonessential-content)
  * [Cakupan Terjemahan](#translation-coverage)

    * [Cakupan Terjemahan Esensial](#essential-translation-coverage)
    * [Persyaratan Cakupan](#coverage-requirement)
    * [Persyaratan Konten Kritis](#critical-content-requirement)
  * [Pemilihan Bahasa](#language-selection)

    * [Locale Aktif](#active-locale)
    * [Locale Bawaan](#default-locale)
    * [Mekanisme Pemilihan Bahasa](#language-selection-mechanism)
    * [Label Opsi Bahasa](#language-option-labels)
  * [Fallback dan Kesetaraan Locale](#fallbacks-and-locale-equivalence)

    * [Locale Fallback](#fallback-locale)
    * [Perilaku Fallback](#fallback-behavior)
    * [Kesetaraan Locale](#locale-equivalence)
  * [Persyaratan Implementasi](#implementation-requirements)

    * [Mekanisme Terjemahan yang Stabil](#stable-translation-mechanism)
    * [Pelestarian Makna](#preservation-of-meaning)
    * [Bahasa yang Sensitif terhadap Arah](#direction-sensitive-languages)
    * [Nilai yang Sensitif terhadap Locale](#locale-sensitive-values)
  * [Verifikasi](#verification)

    * [Within Spec](#within-spec)
    * [Peringatan](#warnings)
    * [Kegagalan](#failures)
    * [Validitas Verifikasi](#verification-validity)

<a id="conformance"></a>
## Konformitas

Suatu sistem dianggap konforman dengan I18NSPEC ketika sistem tersebut memenuhi persyaratan yang ditetapkan oleh dokumen ini untuk setiap locale dalam kumpulan locale yang diwajibkan.

Sistem yang konforman harus:

1. Mendukung setiap locale dalam kumpulan locale yang diwajibkan.
2. Menyediakan konten terjemahan untuk lebih dari 75% konten esensial yang ditujukan kepada pengguna dalam setiap locale yang diwajibkan.
3. Menyediakan konten terjemahan untuk seluruh konten kritis yang ditujukan kepada pengguna dalam setiap locale yang diwajibkan.
4. Menyediakan mekanisme pengguna akhir yang masuk akal untuk memilih locale aktif.
5. Menggunakan mekanisme terjemahan yang stabil dan sesuai dengan sistem.
6. Mempertahankan makna esensial dari konten terjemahan yang ditujukan kepada pengguna.
7. Menghindari ketergantungan pada konten fallback untuk mengklaim cakupan terjemahan, kecuali ketika kesetaraan locale diterima selama peninjauan.

Suatu sistem tidak perlu menggunakan satu pola implementasi tertentu untuk konforman dengan spesifikasi ini. Sistem dapat menggunakan berkas resource, tabel terjemahan, routing sadar-locale, resource bahasa terkompilasi, halaman lokal statis, paket bahasa runtime, terjemahan berbasis database, atau mekanisme stabil lain yang sesuai dengan sistem.

Verifikasi berfokus pada akses pengguna secara praktis dan makna esensial, bukan pada satu arsitektur teknis yang kaku.

<a id="required-locale-set"></a>
## Kumpulan Locale yang Diwajibkan

Kumpulan locale yang diwajibkan mendefinisikan bahasa dan varian regional yang harus ditinjau untuk CatalystUI Internationalization Verification.

Kumpulan locale yang diwajibkan saat ini mencakup locale berikut:

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

Suatu sistem harus menyediakan dukungan terjemahan esensial yang memadai untuk setiap locale yang tercantum agar dapat dianggap within spec.

Kumpulan locale yang diwajibkan tidak dimaksudkan untuk mewakili setiap bahasa, dialek, wilayah, atau aksara. Sebaliknya, kumpulan ini menetapkan dasar praktis untuk kegunaan internasional yang luas di banyak kelompok bahasa yang umum di dunia teknologi.

<a id="user-facing-content"></a>
## Konten yang Ditujukan kepada Pengguna

<a id="user-facing-content-1"></a>
### Konten yang Ditujukan kepada Pengguna

Konten yang ditujukan kepada pengguna adalah setiap konten yang dimaksudkan untuk dipersepsi, dibaca, didengar, dipilih, dipahami, atau ditindaklanjuti oleh pengguna akhir.

Konten yang ditujukan kepada pengguna dapat mencakup:

* navigasi
* label
* tombol
* menu
* kontrol
* heading
* dialog
* pengaturan
* instruksi
* prompt
* peringatan
* kesalahan
* konfirmasi
* pesan status
* teks onboarding
* teks bantuan yang diwajibkan
* kontrol pemilihan bahasa
* konten alur kerja inti

Konten yang ditujukan kepada pengguna tidak harus visual. Konten tersebut juga dapat mencakup konten auditori, taktil, simbolik, atau multisensori ketika konten itu mengomunikasikan makna kepada pengguna.

<a id="essential-user-facing-content"></a>
### Konten Esensial yang Ditujukan kepada Pengguna

Konten esensial yang ditujukan kepada pengguna adalah konten yang secara wajar dibutuhkan pengguna untuk memahami, menavigasi, mengonfigurasi, atau mengoperasikan perilaku esensial suatu sistem.

Konten esensial yang ditujukan kepada pengguna dapat mencakup:

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

Suatu sistem tidak perlu menerjemahkan setiap halaman opsional, pesan tersembunyi, label internal, atau teks nonesensial untuk memenuhi I18NSPEC. Namun, konten yang diperlukan untuk penggunaan esensial biasa harus diterjemahkan sesuai persyaratan spesifikasi ini.

<a id="critical-user-facing-content"></a>
### Konten Kritis yang Ditujukan kepada Pengguna

Konten kritis yang ditujukan kepada pengguna adalah konten esensial yang ditujukan kepada pengguna di mana salah paham dapat mencegah penggunaan yang bermakna, menimbulkan kesalahan serius, atau menyebabkan pengguna mengambil keputusan penting tanpa memahami akibatnya.

Konten kritis yang ditujukan kepada pengguna dapat mencakup:

* kontrol pemilihan bahasa
* peringatan tindakan destruktif
* peringatan penghapusan akun
* konfirmasi pembayaran
* konfirmasi pembelian
* pilihan privasi
* peringatan keamanan
* prompt persetujuan
* instruksi keselamatan yang diwajibkan
* instruksi penyiapan yang diwajibkan
* pesan kesalahan yang diwajibkan
* navigasi inti yang diperlukan untuk mencapai pengaturan bahasa

Konten kritis yang ditujukan kepada pengguna harus diterjemahkan untuk setiap locale yang diwajibkan.

Ambang cakupan terjemahan esensial 75% tidak boleh digunakan untuk membiarkan konten kritis tidak diterjemahkan.

<a id="nonessential-content"></a>
### Konten Nonesensial

Konten nonesensial adalah konten yang tidak secara wajar diperlukan agar pengguna memahami, menavigasi, mengonfigurasi, atau mengoperasikan perilaku esensial suatu sistem.

Konten nonesensial dapat mencakup:

* pengenal internal
* nama kode sumber
* string khusus debug
* detail implementasi yang ditujukan kepada pengembang
* teks diagnostik tersembunyi
* halaman pemasaran opsional
* halaman dukungan opsional
* teks hukum atau bisnis nonesensial di luar cakupan yang ditinjau
* konten pihak ketiga yang tidak dikendalikan oleh sistem yang ditinjau

Konten nonesensial boleh diterjemahkan, tetapi tidak diwajibkan untuk konformitas I18NSPEC kecuali konten itu menjadi perlu untuk pemahaman atau pengoperasian esensial oleh pengguna.

<a id="translation-coverage"></a>
## Cakupan Terjemahan

<a id="essential-translation-coverage"></a>
### Cakupan Terjemahan Esensial

Cakupan terjemahan esensial adalah jumlah konten esensial yang ditujukan kepada pengguna yang diterjemahkan untuk suatu locale tertentu.

Cakupan harus dievaluasi berdasarkan unit konten bermakna yang ditujukan kepada pengguna, bukan berdasarkan ukuran berkas, jumlah byte, jumlah baris, ukuran repositori, atau jumlah halaman.

Misalnya, satu tombol yang tidak diterjemahkan dan mengendalikan tindakan esensial dapat lebih penting daripada paragraf opsional besar yang tidak diterjemahkan tetapi tidak memengaruhi penggunaan biasa.

Cakupan terjemahan harus dinilai berdasarkan apakah pengguna dapat secara bermakna memahami dan mengoperasikan sistem esensial dalam locale yang ditinjau.

<a id="coverage-requirement"></a>
### Persyaratan Cakupan

Suatu sistem memenuhi persyaratan cakupan terjemahan untuk suatu locale ketika lebih dari 75% konten esensial yang ditujukan kepada pengguna diterjemahkan untuk locale tersebut.

Suatu sistem memenuhi persyaratan cakupan I18NSPEC ketika memenuhi ambang ini untuk setiap locale dalam kumpulan locale yang diwajibkan.

Dalam peninjauan praktis, hal ini dapat direpresentasikan sebagai:

| Locale  | Cakupan Terjemahan Esensial | Hasil |
| ------- | --------------------------- | ----- |
| `en-US` | 100%                        | Lulus |
| `es-ES` | 94%                         | Lulus |
| `ar-SA` | 78%                         | Lulus |
| `ja-JP` | 61%                         | Gagal |

Locale dengan cakupan 75% atau kurang tidak memenuhi persyaratan cakupan.

Locale dengan cakupan lebih dari 75% masih dapat gagal jika konten kritis yang ditujukan kepada pengguna belum diterjemahkan.

<a id="critical-content-requirement"></a>
### Persyaratan Konten Kritis

Seluruh konten kritis yang ditujukan kepada pengguna harus diterjemahkan untuk setiap locale yang diwajibkan.

Suatu sistem dapat gagal I18NSPEC bahkan ketika memenuhi ambang cakupan umum jika satu atau lebih item konten kritis yang ditujukan kepada pengguna hilang, tidak diterjemahkan, menyesatkan, atau tidak dapat dipahami secara bermakna.

Misalnya, suatu sistem tidak boleh dianggap within spec jika interface umum diterjemahkan tetapi peringatan penghapusan akun, konfirmasi pembelian, peringatan keamanan, atau pemilih bahasa tetap tidak diterjemahkan.

<a id="language-selection"></a>
## Pemilihan Bahasa

<a id="active-locale"></a>
### Locale Aktif

Locale aktif adalah locale yang saat ini dipilih untuk pengalaman pengguna.

Locale aktif menentukan konten terjemahan mana yang harus ditampilkan, disediakan, atau dengan cara lain dikomunikasikan kepada pengguna.

<a id="default-locale"></a>
### Locale Bawaan

Locale bawaan adalah locale yang digunakan ketika pengguna belum memilih locale aktif atau ketika tidak ada preferensi pengguna yang tersedia.

Suatu sistem harus mendefinisikan locale bawaan.

Locale bawaan harus didokumentasikan atau dapat disimpulkan secara wajar oleh peninjau.

<a id="language-selection-mechanism"></a>
### Mekanisme Pemilihan Bahasa

Sistem yang konforman harus menyediakan cara yang masuk akal bagi pengguna akhir untuk mengubah locale aktif.

Mekanisme pemilihan bahasa harus tersedia tanpa mengharuskan pengguna untuk:

* mengubah kode sumber
* menggunakan alat pengembang
* mengedit berkas konfigurasi yang tidak terdokumentasi
* memasang patch tidak resmi
* bergantung pada perilaku tersembunyi
* menghubungi dukungan untuk perubahan bahasa biasa

Mekanisme pemilihan bahasa dapat disediakan melalui:

* pengaturan aplikasi
* preferensi akun
* pemilih bahasa
* prompt awal
* pengaturan browser
* pengaturan operating system
* pengaturan perangkat
* mekanisme lain yang sesuai dan dapat diakses oleh pengguna akhir

Mekanisme tersebut tidak perlu mengikuti satu pola desain tertentu. Mekanisme itu harus secara wajar memungkinkan pengguna memilih bahasa yang didukung.

<a id="language-option-labels"></a>
### Label Opsi Bahasa

Saat menampilkan opsi bahasa, suatu sistem harus mengidentifikasi setiap bahasa dengan cara yang dapat dipahami oleh pengguna yang berbicara bahasa tersebut.

Opsi bahasa dapat mencakup:

* nama bahasa dalam bahasa tersebut
* nama bahasa dalam bahasa yang sedang aktif
* kode locale
* label regional
* label aksara

Misalnya:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Format yang tepat dapat bervariasi.

Maksudnya adalah agar pengguna dapat mengenali bahasa mereka sendiri, memahami nama bahasa yang sedang ditampilkan bila memungkinkan, dan mengidentifikasi kode locale terkait.

<a id="fallbacks-and-locale-equivalence"></a>
## Fallback dan Kesetaraan Locale

<a id="fallback-locale"></a>
### Locale Fallback

Locale fallback adalah locale yang digunakan ketika konten terjemahan tidak tersedia untuk locale aktif.

Locale fallback dapat membantu mempertahankan kegunaan, tetapi konten fallback tidak otomatis dianggap sebagai konten terjemahan untuk locale aktif.

Misalnya, jika suatu sistem diatur ke `es-MX` tetapi menampilkan teks `en-US` karena terjemahan bahasa Spanyol hilang, teks bahasa Inggris tersebut mungkin berguna sebagai fallback, tetapi tidak boleh dihitung sebagai cakupan terjemahan bahasa Spanyol.

<a id="fallback-behavior"></a>
### Perilaku Fallback

Sistem yang konforman dapat menggunakan perilaku fallback ketika konten terlokalisasi tidak tersedia.

Perilaku fallback harus menghindari output yang rusak, kosong, atau menyesatkan.

Perilaku fallback tidak boleh digunakan untuk mengklaim cakupan terjemahan secara palsu untuk locale yang diwajibkan.

Suatu sistem dapat menerima peringatan atau kegagalan jika perilaku fallback berlebihan, membingungkan, tidak terdokumentasi, atau menyebabkan konten esensial muncul tanpa terjemahan dalam locale yang diwajibkan.

<a id="locale-equivalence"></a>
### Kesetaraan Locale

Kesetaraan locale terjadi ketika satu terjemahan secara wajar dapat melayani lebih dari satu locale tanpa mencegah pemahaman atau pengoperasian esensial.

Misalnya, suatu sistem dapat menggunakan satu terjemahan bahasa Inggris untuk `en-US`, `en-GB`, dan `en-IN` jika makna esensial tetap jelas bagi pengguna dari setiap locale.

Kesetaraan locale dapat diterima selama peninjauan ketika perbedaan regional kecil dan tidak secara material memengaruhi kegunaan esensial.

Kesetaraan locale tidak boleh digunakan ketika locale yang hilang akan menimbulkan kebingungan bermakna, menghilangkan terminologi regional penting, merusak perilaku esensial, atau mencegah pengguna memahami sistem.

Misalnya, suatu sistem tidak boleh mengasumsikan bahwa bahasa yang tidak terkait adalah setara karena memiliki arah penulisan, wilayah geografis, keluarga aksara, atau kategori budaya yang luas yang sama.

Kesetaraan locale adalah penilaian peninjauan, bukan aturan otomatis.

<a id="implementation-requirements"></a>
## Persyaratan Implementasi

<a id="stable-translation-mechanism"></a>
### Mekanisme Terjemahan yang Stabil

Sistem yang konforman harus menggunakan mekanisme terjemahan yang stabil dan sesuai dengan sistem yang sedang ditinjau.

Mekanisme terjemahan yang stabil harus memungkinkan konten terjemahan dipelihara, diperbarui, ditinjau, dan diperluas tanpa bergantung pada perilaku yang rapuh atau tidak terdokumentasi.

Mekanisme terjemahan yang stabil dapat mencakup:

* berkas resource
* tabel terjemahan
* routing sadar-locale
* aset bahasa terkompilasi
* halaman lokal statis
* paket bahasa runtime
* terjemahan berbasis database
* struktur terjemahan terdokumentasi lainnya

Suatu sistem harus menghindari hardcoding konten esensial yang ditujukan kepada pengguna dengan cara yang mencegah dukungan terjemahan yang diwajibkan.

<a id="preservation-of-meaning"></a>
### Pelestarian Makna

Terjemahan mempertahankan makna ketika pengguna dapat secara wajar memahami instruksi, label, peringatan, kontrol, pengaturan, atau alur kerja esensial yang sama seperti pengguna bahasa sumber.

Terjemahan tidak perlu identik kata demi kata dengan konten sumber.

Terjemahan dapat mengubah urutan kata, tata bahasa, struktur kalimat, idiom, nada, atau frasa bila diperlukan untuk mengomunikasikan makna esensial yang sama dalam bahasa target.

Terjemahan dapat gagal dalam peninjauan jika menyesatkan, tidak lengkap, tidak masuk akal, rusak oleh mesin, atau berbeda secara bermakna dari konten sumber dengan cara yang memengaruhi penggunaan esensial.

<a id="direction-sensitive-languages"></a>
### Bahasa yang Sensitif terhadap Arah

Beberapa locale yang diwajibkan umumnya menggunakan arah teks kanan-ke-kiri.

Sistem yang konforman tidak boleh mencegah konten terjemahan esensial untuk dibaca, dipahami, dipilih, atau ditindaklanjuti karena locale aktif menggunakan arah teks yang berbeda.

Sistem harus mempertahankan urutan yang terbaca, perilaku tanda baca, dan asosiasi kontrol untuk bahasa yang sensitif terhadap arah.

Polesan visual penuh, kualitas tipografi, perilaku aksesibilitas, dan penyempurnaan tata letak mungkin memerlukan tinjauan terpisah. Namun, konten terjemahan esensial harus tetap dapat digunakan secara bermakna.

<a id="locale-sensitive-values"></a>
### Nilai yang Sensitif terhadap Locale

Nilai yang sensitif terhadap locale adalah nilai yang makna atau keterbacaannya dapat bervariasi berdasarkan bahasa, wilayah, aksara, atau budaya.

Nilai yang sensitif terhadap locale dapat mencakup:

* tanggal
* waktu
* angka
* mata uang
* ukuran
* bentuk jamak
* gender gramatikal
* urutan penyortiran
* format alamat
* format nomor telepon

I18NSPEC tidak mewajibkan lokalisasi lengkap untuk setiap nilai yang sensitif terhadap locale kecuali nilai tersebut esensial untuk memahami atau mengoperasikan sistem.

Ketika nilai yang sensitif terhadap locale bersifat esensial, sistem harus merepresentasikannya dengan cara yang dapat dipahami secara wajar oleh pengguna locale aktif.

<a id="verification"></a>
## Verifikasi

<a id="within-spec"></a>
### Within Spec

Suatu sistem dianggap within spec ketika Tim CatalystUI telah meninjau sistem tersebut dan menilai bahwa secara wajar sistem itu memenuhi I18NSPEC.

Suatu sistem dapat berada within spec ketika:

* setiap locale yang diwajibkan didukung
* lebih dari 75% konten esensial yang ditujukan kepada pengguna diterjemahkan untuk setiap locale yang diwajibkan
* seluruh konten kritis yang ditujukan kepada pengguna diterjemahkan untuk setiap locale yang diwajibkan
* pengguna dapat memilih locale aktif secara wajar
* perilaku fallback tidak mengklaim cakupan terjemahan secara palsu
* kesetaraan locale, jika digunakan, wajar dan terdokumentasi
* konten terjemahan mempertahankan makna esensial

Suatu sistem dapat berada within spec meskipun sebagian konten nonesensial tetap tidak diterjemahkan.

Suatu sistem dapat berada within spec meskipun terjemahan tidak sempurna, selama makna esensial dipertahankan dan persyaratan spesifikasi ini dipenuhi.

<a id="warnings"></a>
### Peringatan

Peringatan dapat dikeluarkan ketika suatu sistem tampak memenuhi I18NSPEC tetapi memiliki kekhawatiran yang harus didokumentasikan.

Peringatan dapat mencakup:

* konten nonesensial kecil yang belum diterjemahkan
* terminologi yang tidak konsisten antar-locale
* terjemahan yang tidak sempurna tetapi dapat dipahami
* kesetaraan locale yang dapat diterima tetapi harus didokumentasikan
* perilaku fallback yang terbatas
* halaman opsional yang diterjemahkan sebagian
* kekhawatiran tata letak yang sensitif terhadap arah tetapi tidak mencegah penggunaan esensial
* nilai yang sensitif terhadap locale yang dapat dipahami tetapi tidak ideal

Peringatan tidak selalu mencegah verifikasi.

<a id="failures"></a>
### Kegagalan

Kegagalan terjadi ketika suatu sistem tidak memenuhi satu atau lebih kondisi wajib I18NSPEC.

Kegagalan dapat mencakup:

* tidak adanya dukungan untuk locale yang diwajibkan
* cakupan terjemahan esensial pada atau di bawah 75% untuk locale yang diwajibkan
* konten kritis yang ditujukan kepada pengguna tidak diterjemahkan
* tidak ada mekanisme pemilihan bahasa yang masuk akal
* pemilihan bahasa yang mengharuskan modifikasi kode sumber
* pemilihan bahasa yang mengharuskan alat pengembang
* pemuatan terjemahan yang rusak
* klaim locale yang menyesatkan
* perilaku fallback yang berlebihan
* konten fallback dihitung sebagai konten terjemahan tanpa kesetaraan locale yang valid
* konten yang sensitif terhadap arah tidak terbaca atau tidak dapat digunakan
* alur kerja esensial tidak tersedia dalam satu atau lebih locale yang diwajibkan

Kegagalan mencegah verifikasi sampai diselesaikan.

<a id="verification-validity"></a>
### Validitas Verifikasi

Verifikasi I18NSPEC hanya berlaku untuk keadaan sistem yang ditinjau pada saat verifikasi diterbitkan.

Suatu sistem dapat mempertahankan verifikasi dalam pembaruan berikutnya selama mempertahankan fondasi internasionalisasi yang telah diverifikasi.

Perubahan kata kecil, tambahan terjemahan, peningkatan terjemahan, dan pembaruan konten biasa tidak secara otomatis membatalkan verifikasi.

Tinjauan baru mungkin diperlukan jika suatu sistem:

* menghapus dukungan locale yang diwajibkan
* merusak pemilihan bahasa
* secara substansial mengurangi cakupan terjemahan esensial
* membiarkan alur kerja esensial baru tidak diterjemahkan
* mengganti konten terjemahan dengan konten fallback
* mengubah arsitektur terjemahannya dengan cara yang memengaruhi perilaku yang diverifikasi
* memperkenalkan perubahan besar yang ditujukan kepada pengguna dan mengubah cakupan yang ditinjau

Dengan kata lain, meningkatkan dukungan terjemahan biasanya tidak masalah.

Merusak fondasi multibahasa yang telah diverifikasi mungkin memerlukan tinjauan.
