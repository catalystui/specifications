<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->

<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Selamat datang di dokumentasi CatalystUI Verification untuk aksesibilitas.

**CatalystUI Verified for Accessibility** menunjukkan bahwa suatu service, framework, application, library, atau system telah ditinjau oleh CatalystUI Team dan dinilai tetap cukup dapat digunakan ketika salah satu dari tiga indra utama yang terlibat dalam interaksi antarmuka pengguna tidak tersedia secara terpisah.

Untuk verifikasi ini, CatalystUI mengidentifikasi tiga indra aksesibilitas utama sebagai **sight**, **sound**, dan **touch**. System yang terverifikasi harus mempertahankan akses yang wajar ke essential functionality ketika salah satu indra ini tidak tersedia, dengan mengandalkan sensory domains lain yang masih tersedia.

Secara sederhana, verifikasi ini menanyakan apakah user masih dapat memahami, menavigasi, dan mengoperasikan bagian-bagian essential dari suatu system secara bermakna ketika mereka tidak dapat mengandalkan sight, sound, atau touch secara terpisah.

## Tujuan

Aksesibilitas penting karena user interface tidak seharusnya bergantung sepenuhnya pada satu sensory pathway ketika makna essential yang sama dapat dikomunikasikan secara wajar melalui pathway lain.

CatalystUI dirancang di sekitar perpindahan data yang setia antara system dan persepsi manusia. Jika informasi penting hanya terlihat, hanya terdengar, atau hanya tersedia melalui touch, maka system dapat menjadi tidak dapat digunakan oleh user yang tidak dapat mengandalkan indra tersebut. Accessibility Verification ada untuk mengidentifikasi system yang mempertahankan akses dengan memungkinkan informasi dan interaksi essential tetap berlanjut melalui rute sensory alternatif.

Tujuannya bukan untuk mewajibkan setiap kemungkinan metode interaksi, setiap assistive technology, atau setiap akomodasi khusus. Tujuannya adalah menentukan apakah essential system tetap meaningfully usable ketika sight, sound, atau touch tidak tersedia secara terpisah.

## Arti Verification

Suatu system menjadi **CatalystUI Verified for Accessibility** ketika ditinjau terhadap requirements yang tercantum di bagian ini dan dinyatakan within spec.

Agar terverifikasi, suatu system harus tetap cukup dapat digunakan dalam setiap kasus berikut:

| Unavailable Sense | Required Accessibility Behavior |
| ----------------- | ----------------------------------------------------------------- |
| Sight             | System harus tetap cukup dapat digunakan melalui sound dan touch. |
| Sound             | System harus tetap cukup dapat digunakan melalui sight dan touch. |
| Touch             | System harus tetap cukup dapat digunakan melalui sight dan sound. |

System tidak perlu memberikan pengalaman yang identik di setiap sensory path. Pengalaman non-visual dapat lebih lambat daripada pengalaman visual. Pengalaman tanpa sound dapat memerlukan captions, visual indicators, atau substitusi lain. Pengalaman tanpa touch dapat memerlukan alternate controls, voice interaction, keyboard navigation, pointer navigation, atau metode non-touch lain.

Yang penting adalah apakah essential functionality tetap accessible, understandable, dan operable tanpa mewajibkan indra yang tidak tersedia.

## Essential Functionality

Untuk Accessibility Verification, **essential functionality** merujuk pada bagian-bagian system yang secara wajar dibutuhkan user untuk memahami, menavigasi, mengonfigurasi, dan mengoperasikan system.

Essential functionality dapat mencakup:

* primary navigation
* core workflows
* required controls
* important warnings
* important errors
* required confirmation messages
* account or session access
* settings and preferences
* language or accessibility configuration
* essential instructions
* user-facing status information
* interaksi apa pun yang diperlukan untuk penggunaan normal

System masih dapat within spec jika fitur dekoratif, redundant, optional, atau nonessential tidak tersedia secara setara melalui setiap sensory path. Namun, user tetap harus dapat menggunakan essential system tanpa terhalang oleh indra yang hilang.

## Sight Unavailable

Ketika sight tidak tersedia, system harus tetap cukup dapat digunakan melalui sound dan touch.

Ini dapat mencakup spoken output, screen-reader-compatible structure, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions, atau metode non-visual lain yang wajar untuk mengomunikasikan essential information.

System tidak seharusnya bergantung secara eksklusif pada visual position, color, shape, animation, icons, atau layout ketika informasi tersebut diperlukan untuk memahami atau mengoperasikan essential functionality.

## Sound Unavailable

Ketika sound tidak tersedia, system harus tetap cukup dapat digunakan melalui sight dan touch.

Ini dapat mencakup captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback, atau metode non-auditory lain yang wajar untuk mengomunikasikan essential information.

System tidak seharusnya bergantung secara eksklusif pada sound effects, spoken instructions, alerts, alarms, music cues, atau audio-only prompts ketika informasi tersebut diperlukan untuk memahami atau mengoperasikan essential functionality.

## Touch Unavailable

Ketika touch tidak tersedia, system harus tetap cukup dapat digunakan melalui sight dan sound.

Ini dapat mencakup voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation, atau metode wajar lain yang tidak memerlukan touch-based interaction atau tactile perception.

System tidak seharusnya bergantung secara eksklusif pada touch gestures, haptic feedback, physical texture, vibration, force, pressure, atau touch-only controls ketika interaksi tersebut diperlukan untuk memahami atau mengoperasikan essential functionality.

## Additional Sensory Domains

CatalystUI juga mengenali **taste** dan **smell** sebagai sensory domains. Domain ini dapat dipertimbangkan selama accessibility review ketika digunakan secara bermakna oleh system.

Taste dan smell bersifat **inclusive** untuk verification, artinya keduanya dapat memperkuat atau mendukung accessibility review ketika menyediakan alternate access yang bermakna atau additional context.

Taste dan smell saat ini tidak bersifat **exclusive** untuk failure, artinya system tidak gagal Accessibility Verification hanya karena tidak menyediakan interaksi berbasis taste atau smell.

CatalystUI Accessibility Verification terutama berkaitan dengan apakah system tetap cukup dapat digunakan ketika sight, sound, atau touch tidak tersedia secara terpisah.

## Arti “Within Spec”

Ketika suatu system dianggap **within spec**, artinya CatalystUI Team telah meninjau system secara manual dan menilai wajar untuk menyimpulkan bahwa system tersebut memenuhi accessibility requirements yang dijelaskan oleh kategori verification ini.

Ini tidak memerlukan satu pola implementasi yang kaku. System dapat memenuhi accessibility requirements melalui native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration, atau stable mechanism lain yang sesuai untuk system tersebut.

Verification berkaitan dengan kemampuan praktis user untuk mengakses essential system ketika satu primary sense tidak tersedia, bukan apakah system menggunakan satu arsitektur aksesibilitas tertentu.

## Yang Tidak Dimaksud oleh Verification

CatalystUI Verified for Accessibility tidak menjamin bahwa setiap kemungkinan disability, device, assistive technology, medical condition, legal requirement, regional standard, atau specialized use case telah ditinjau sepenuhnya.

Ini juga tidak secara otomatis memverifikasi internationalization, translation quality, typography, localization, regional compliance, atau general design quality kecuali hal-hal tersebut termasuk dalam reviewed accessibility scope.

System dapat cukup accessible menurut accessibility model CatalystUI dan tetap memerlukan review terpisah untuk legal compliance, platform certification, specialized assistive technology support, atau accessibility standards lain.

## Mengapa Verification Ini Ada

User interface hanya berhasil ketika user benar-benar dapat menggunakannya.

Banyak system memperlakukan accessibility sebagai afterthought, checklist, atau technical requirement yang sempit, bukan sebagai bagian fundamental dari human-computer interaction. CatalystUI mengambil pendekatan yang lebih sederhana dan langsung: jika system bergantung pada human perception, maka system harus mempertahankan essential meaning ketika satu primary sensory path tidak tersedia.

Accessibility Verification ada untuk mengidentifikasi system yang menjalankan tanggung jawab ini dengan serius. Ini mengenali system yang menyediakan alternate access yang bermakna, mempertahankan essential functionality, dan menghindari menjebak user di balik satu indra yang wajib.

## Verification Scope

CatalystUI Verification for Accessibility berlaku untuk system, service, framework, application, library, atau implementation yang ditinjau sebagaimana adanya pada saat verification diterbitkan.

System yang terverifikasi menyediakan aksesibilitas yang wajar untuk essential functionality-nya dalam kondisi yang ditinjau. Ini tidak menjamin bahwa setiap future page, feature, release, plugin, extension, third-party integration, device, atau platform-specific version otomatis within spec.

Produk, modules, services, major revisions, atau platform-specific builds yang terpisah dapat memerlukan review sendiri tergantung kategori verification yang diminta.

## Verification Validity

CatalystUI Verification hanya berlaku untuk reviewed state system pada saat verification diterbitkan.

System dapat mempertahankan verification-nya dalam update berikutnya selama mempertahankan verified accessibility foundation. Perubahan wording kecil, visual refinements, performance improvements, dan ordinary content updates tidak otomatis membatalkan verification.

Review baru dapat diperlukan jika system menghapus alternate access paths, merusak assistive-technology support, mengubah essential navigation secara substansial, menghapus required accessibility settings, atau mengubah interaction behavior dengan cara yang memengaruhi verified accessibility foundation.

Dengan kata lain, meningkatkan aksesibilitas biasanya baik-baik saja. Merusak verified access model dapat memerlukan review.

## Verified Systems

System yang diketahui verified for accessibility dicantumkan secara terpisah pada halaman CatalystUI Verified yang sesuai.
