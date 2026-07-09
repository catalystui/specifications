<!-- Terjemahan ini dibuat oleh ChatGPT dan harus ditinjau oleh penerjemah manusia. -->

<!-- Hapus baris-baris ini dalam pull request setelah terjemahan diverifikasi. -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Definisi, requirements, dan konsep yang disajikan di sini menjelaskan dukungan aksesibilitas praktis dan boleh diungkapkan kembali secara bebas.

<a id="introduction"></a>

## Introduction

**Accessibility Specification (A11YSPEC)** menetapkan core concepts, terminology, dan requirements yang digunakan untuk mengevaluasi accessibility support dalam ecosystem CatalystUI. Tujuannya adalah menyediakan standard yang jelas untuk menentukan apakah suatu system, service, framework, application, library, atau implementation tetap meaningfully usable ketika satu primary sensory pathway tidak tersedia.

Accessibility penting karena user interface tidak boleh sepenuhnya bergantung pada satu sense ketika essential meaning yang sama dapat dikomunikasikan secara wajar melalui sense lain. Suatu system mungkin technically functional, tetapi jika user tidak dapat memahami, menavigasi, mengonfigurasi, atau mengoperasikan essential behavior-nya tanpa sight, sound, atau touch secara terpisah, maka system tersebut gagal menyediakan reasonable access untuk kondisi tersebut.

Specification ini tidak berusaha memverifikasi setiap possible disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard, atau specialized use case. Sebaliknya, specification ini mendefinisikan minimum accessibility foundation yang diperlukan agar user dapat meaningfully access dan operate bagian essential dari suatu system ketika salah satu dari tiga primary accessibility senses tidak tersedia.

Secara sederhana, A11YSPEC mengajukan tiga pertanyaan utama:

1. Dapatkah user memahami essential system tanpa mengandalkan sight?
2. Dapatkah user memahami essential system tanpa mengandalkan sound?
3. Dapatkah user mengoperasikan essential system tanpa mengandalkan touch?

> [!IMPORTANT]
>
> A11YSPEC mendefinisikan accessibility requirements untuk verification. Ini bukan pengganti legal accessibility standards, platform certification requirements, atau specialized assistive-technology review. Suatu system dapat berada within A11YSPEC dan tetap memerlukan additional review untuk accessibility standards lain.

<a id="table-of-contents"></a>

## Table of Contents

- [A11YSPEC](#a11yspec)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Conformance](#conformance)
  - [Primary Accessibility Senses](#primary-accessibility-senses)
    - [Sight](#sight)
    - [Sound](#sound)
    - [Touch](#touch)
    - [Additional Sensory Domains](#additional-sensory-domains)
  - [Required Accessibility Cases](#required-accessibility-cases)
  - [Essential Functionality](#essential-functionality)
    - [Essential Functionality](#essential-functionality-1)
    - [Critical Functionality](#critical-functionality)
    - [Nonessential Functionality](#nonessential-functionality)
  - [Accessibility Requirements](#accessibility-requirements)
    - [Essential Access Requirement](#essential-access-requirement)
    - [Critical Access Requirement](#critical-access-requirement)
    - [Alternate Access Requirement](#alternate-access-requirement)
    - [No Single-Sense Dependency](#no-single-sense-dependency)
  - [Sight Unavailable](#sight-unavailable)
  - [Sound Unavailable](#sound-unavailable)
  - [Touch Unavailable](#touch-unavailable)
  - [Implementation Requirements](#implementation-requirements)
    - [Stable Accessibility Mechanism](#stable-accessibility-mechanism)
    - [Semantic Structure](#semantic-structure)
    - [Alternate Output](#alternate-output)
    - [Alternate Input](#alternate-input)
    - [Accessible Feedback](#accessible-feedback)
    - [Accessible Configuration](#accessible-configuration)
  - [Verification](#verification)
    - [Within Spec](#within-spec)
    - [Warnings](#warnings)
    - [Failures](#failures)
    - [Verification Validity](#verification-validity)

<a id="conformance"></a>

## Conformance

Suatu system dianggap conformant dengan A11YSPEC ketika memenuhi requirements yang didefinisikan oleh document ini untuk setiap required accessibility case.

Conforming system harus:

1. Tetap reasonably usable ketika sight tidak tersedia.
2. Tetap reasonably usable ketika sound tidak tersedia.
3. Tetap reasonably usable ketika touch tidak tersedia.
4. Mempertahankan access ke essential functionality dalam setiap required accessibility case.
5. Mempertahankan access ke semua critical functionality dalam setiap required accessibility case.
6. Menyediakan reasonable alternate access paths ketika essential meaning atau operation sebaliknya akan bergantung pada unavailable sense.
7. Menggunakan stable accessibility mechanism yang sesuai untuk reviewed system.
8. Menghindari ketergantungan eksklusif pada satu primary sense untuk essential functionality.

System tidak perlu memberikan pengalaman yang identik di setiap sensory path. Pengalaman non-visual dapat lebih lambat daripada visual. Pengalaman sound-free dapat memerlukan captions, visual indicators, atau haptic confirmation. Pengalaman touch-free dapat memerlukan keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction, atau metode non-touch lain.

Verification berfokus pada practical access ke essential functionality, bukan presentation yang identik.

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

Untuk A11YSPEC, tiga primary accessibility senses adalah **sight**, **sound**, dan **touch**.

Indra ini disebut primary karena merupakan sensory pathways yang paling umum terlibat dalam user-interface interaction. System dapat memberikan output melalui sight, sound, atau touch, dan dapat menerima interaction melalui touch, motion, voice, keyboard input, pointer input, switch input, atau input path lain yang tersedia.

<a id="sight"></a>

### Sight

Sight adalah visual sensory pathway yang digunakan user untuk perceive visual output.

Sight dapat terlibat dalam mempersepsi:

* text
* color
* shape
* position
* layout
* animation
* icons
* images
* video
* visual warnings
* visual status indicators
* visible controls

System bergantung pada sight ketika essential meaning atau operation mengharuskan user perceive information secara visual.

<a id="sound"></a>

### Sound

Sound adalah auditory sensory pathway yang digunakan user untuk perceive audio output.

Sound dapat terlibat dalam mempersepsi:

* spoken instructions
* alerts
* alarms
* music cues
* sound effects
* audio prompts
* audio descriptions
* auditory status indicators
* spoken confirmation
* spoken navigation

System bergantung pada sound ketika essential meaning atau operation mengharuskan user mendengar information.

<a id="touch"></a>

### Touch

Touch adalah tactile sensory pathway yang digunakan user untuk perceive physical atau haptic output, serta physical interaction pathway yang memungkinkan user mengoperasikan controls melalui direct contact, pressure, gesture, atau movement.

Touch dapat terlibat dalam mempersepsi atau melakukan:

* touch gestures
* haptic feedback
* vibration
* physical texture
* force
* pressure
* touch-only controls
* physical buttons
* direct manipulation
* touchscreen interaction
* drag actions
* swipe actions

System bergantung pada touch ketika essential meaning atau operation memerlukan tactile perception atau touch-based interaction tanpa reasonable alternate input atau output path.

<a id="additional-sensory-domains"></a>

### Additional Sensory Domains

CatalystUI juga mengenali **taste** dan **smell** sebagai sensory domains.

Taste dan smell dapat dipertimbangkan selama accessibility review ketika digunakan secara bermakna oleh system. Indra ini bersifat inclusive untuk verification, artinya dapat memperkuat atau mendukung accessibility review ketika memberikan meaningful alternate access atau additional context.

Taste dan smell saat ini tidak exclusive untuk failure. System tidak gagal A11YSPEC hanya karena tidak menyediakan taste-based atau smell-based interaction.

A11YSPEC terutama berkaitan dengan apakah system tetap reasonably usable ketika sight, sound, atau touch tidak tersedia secara terpisah.

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

Conforming system harus ditinjau terhadap setiap required accessibility case.

| Unavailable Sense | Required Accessibility Behavior |
| ----------------- | ----------------------------------------------------------------- |
| Sight             | System harus tetap reasonably usable melalui sound dan touch. |
| Sound             | System harus tetap reasonably usable melalui sight dan touch. |
| Touch             | System harus tetap reasonably usable melalui sight dan sound. |

Setiap case ditinjau secara individual.

System tidak diwajibkan tetap fully usable ketika multiple primary senses tidak tersedia pada saat yang sama kecuali kondisi tersebut termasuk dalam reviewed scope.

System tidak diwajibkan menyediakan setiap possible accommodation. System harus menyediakan reasonable access ke essential functionality di bawah setiap required accessibility case.

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality adalah behavior, content, control, output, input, workflow, atau configuration apa pun yang secara wajar dibutuhkan user untuk memahami, menavigasi, mengonfigurasi, atau mengoperasikan essential behavior dari suatu system.

Essential functionality dapat mencakup:

* primary navigation
* core workflows
* required controls
* important warnings
* important errors
* required confirmation messages
* account or session access
* settings and preferences
* language configuration
* accessibility configuration
* essential instructions
* user-facing status information
* interaksi apa pun yang diperlukan untuk penggunaan normal

System tidak perlu membuat setiap decorative, optional, redundant, atau nonessential feature tersedia secara setara melalui setiap sensory path. Namun, user tidak boleh terhalang menggunakan essential system oleh unavailable sense.

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality adalah essential functionality yang kehilangan access-nya dapat mencegah meaningful use, menciptakan serious error, atau menyebabkan user membuat important decision tanpa memahami konsekuensinya.

Critical functionality dapat mencakup:

* accessibility settings
* language settings
* destructive action warnings
* account deletion warnings
* payment confirmations
* purchase confirmations
* privacy choices
* security warnings
* consent prompts
* required safety instructions
* required setup instructions
* required error messages
* session access
* emergency stop or cancel behavior
* core navigation yang diperlukan untuk mencapai accessibility settings

Critical functionality harus tetap accessible dalam setiap required accessibility case.

System dapat gagal A11YSPEC jika critical functionality bergantung secara eksklusif pada unavailable sense.

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality adalah functionality yang tidak secara wajar diperlukan agar user memahami, menavigasi, mengonfigurasi, atau mengoperasikan essential behavior dari suatu system.

Nonessential functionality dapat mencakup:

* decorative animation
* optional effects
* cosmetic visual polish
* nonessential sound effects
* redundant haptic effects
* optional marketing content
* optional tutorial content
* hidden diagnostic behavior
* developer-facing controls
* experimental features di luar reviewed scope

Nonessential functionality dapat inaccessible dalam satu atau lebih accessibility cases tanpa otomatis menyebabkan failure. Namun, nonessential functionality tidak boleh disamakan dengan essential functionality hanya karena support-nya inconvenient.

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

System memenuhi essential access requirement ketika essential functionality tetap reasonably understandable, navigable, configurable, dan operable dalam setiap required accessibility case.

Essential experience tidak perlu identik di semua senses.

Essential experience harus tetap meaningfully usable.

<a id="critical-access-requirement"></a>

### Critical Access Requirement

System memenuhi critical access requirement ketika semua critical functionality tetap accessible dalam setiap required accessibility case.

Critical functionality tidak boleh disembunyikan di balik satu required sensory pathway.

Misalnya, system tidak boleh menyediakan accessible interface untuk ordinary use tetapi membiarkan account deletion warnings, payment confirmations, privacy decisions, atau accessibility settings bergantung pada sight, sound, atau touch saja.

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

System memenuhi alternate access requirement ketika essential meaning atau operation yang diberikan melalui satu primary sense juga reasonably available melalui sensory atau interaction path lain ketika sense tersebut unavailable.

Alternate access dapat disediakan melalui:

* text alternatives
* captions
* transcripts
* spoken output
* screen-reader-compatible structure
* keyboard navigation
* pointer alternatives
* switch-compatible interaction
* voice control
* visual alerts
* haptic feedback
* focus indicators
* semantic structure
* accessible platform APIs
* device-level accessibility integration
* stable mechanism lain yang sesuai untuk system

Alternate path tidak perlu cocok sempurna dengan original path. Path tersebut harus preserve essential meaning dan operation.

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

System tidak boleh mewajibkan satu primary sense sebagai satu-satunya path ke essential functionality.

System dapat menggunakan sight, sound, atau touch sebagai primary experience. Namun, ketika sense tersebut unavailable, user tetap harus memiliki cara yang wajar untuk memahami dan mengoperasikan essential system melalui sensory paths yang tersisa.

System dapat gagal review ketika essential information atau interaction hanya tersedia melalui:

* visual-only meaning
* audio-only meaning
* touch-only meaning
* gesture-only operation
* haptic-only confirmation
* color-only status
* sound-only alerts
* layout-only instructions
* physical texture-only guidance

<a id="sight-unavailable"></a>

## Sight Unavailable

Ketika sight tidak tersedia, system harus tetap reasonably usable melalui sound dan touch.

Ini berarti essential visual information harus memiliki meaningful non-visual access path.

System dapat memenuhi requirement ini melalui:

* spoken output
* screen-reader-compatible structure
* meaningful focus order
* keyboard access
* tactile controls
* haptic confirmation
* audio descriptions
* text-to-speech support
* semantic labels
* accessible names
* accessible roles
* accessible state information
* another reasonable non-visual mechanism

System tidak seharusnya bergantung secara eksklusif pada:

* visual position
* color
* shape
* animation
* icons
* layout
* images
* video
* visual-only warnings
* visual-only status indicators

ketika informasi tersebut diperlukan untuk memahami atau mengoperasikan essential functionality.

System dapat gagal case ini jika user tidak dapat secara wajar menavigasi, memahami, atau mengoperasikan essential system tanpa sight.

<a id="sound-unavailable"></a>

## Sound Unavailable

Ketika sound tidak tersedia, system harus tetap reasonably usable melalui sight dan touch.

Ini berarti essential auditory information harus memiliki meaningful non-auditory access path.

System dapat memenuhi requirement ini melalui:

* captions
* transcripts
* visual alerts
* text equivalents
* progress indicators
* visible status messages
* haptic feedback
* visual confirmation
* written instructions
* symbolic indicators
* another reasonable non-auditory mechanism

System tidak seharusnya bergantung secara eksklusif pada:

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

ketika informasi tersebut diperlukan untuk memahami atau mengoperasikan essential functionality.

System dapat gagal case ini jika user tidak dapat secara wajar menavigasi, memahami, atau mengoperasikan essential system tanpa sound.

<a id="touch-unavailable"></a>

## Touch Unavailable

Ketika touch tidak tersedia, system harus tetap reasonably usable melalui sight dan sound.

Ini berarti essential tactile information dan touch-based operation harus memiliki meaningful non-touch access path.

System dapat memenuhi requirement ini melalui:

* keyboard navigation
* pointer alternatives
* voice control
* remote controls
* gaze-compatible interaction
* switch-compatible interaction
* spoken prompts
* visual confirmation
* accessible shortcut systems
* command palettes
* focus-based interaction
* another reasonable non-touch mechanism

System tidak seharusnya bergantung secara eksklusif pada:

* touch gestures
* haptic feedback
* physical texture
* vibration
* force
* pressure
* touch-only controls
* drag-only behavior
* swipe-only behavior
* pinch-only behavior
* direct manipulation without alternatives

ketika interaction tersebut diperlukan untuk memahami atau mengoperasikan essential functionality.

System dapat gagal case ini jika user tidak dapat secara wajar menavigasi, memahami, atau mengoperasikan essential system tanpa touch.

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

Conforming system harus menggunakan stable accessibility mechanism yang sesuai dengan system yang ditinjau.

Stable accessibility mechanism seharusnya memungkinkan accessibility behavior dipertahankan, diperbarui, ditinjau, dan diperluas tanpa bergantung pada fragile atau undocumented behavior.

Stable accessibility mechanism dapat mencakup:

* native platform accessibility APIs
* semantic structure
* alternate input methods
* alternate output methods
* assistive-technology support
* built-in accessibility settings
* device-level integration
* documented keyboard interaction
* documented voice interaction
* documented non-visual interaction
* stable structure lain yang sesuai untuk system

System sebaiknya menghindari implementasi essential functionality dengan cara yang mencegah reasonable alternate access.

<a id="semantic-structure"></a>

### Semantic Structure

Conforming system seharusnya menyediakan semantic structure ketika system menyajikan meaningful content atau controls.

Semantic structure dapat mencakup:

* names
* roles
* states
* relationships
* ordering
* grouping
* labels
* descriptions
* focus behavior
* control purpose
* content hierarchy

Semantic structure sangat penting ketika sight tidak tersedia, karena assistive technologies sering bergantung pada semantic information untuk mengomunikasikan visual interfaces melalui non-visual output.

System dapat gagal review jika essential controls atau content tidak dapat dipahami karena structure, labels, atau relationships-nya tidak tersedia melalui alternate access paths.

<a id="alternate-output"></a>

### Alternate Output

Conforming system harus menyediakan reasonable alternate output ketika essential meaning sebaliknya akan bergantung pada unavailable sense.

Alternate output dapat mencakup:

* visual output untuk auditory information
* auditory output untuk visual information
* tactile output untuk visual atau auditory information
* text equivalents
* captions
* transcripts
* spoken descriptions
* visible status messages
* haptic confirmation
* another appropriate output path

Alternate output harus preserve essential meaning.

<a id="alternate-input"></a>

### Alternate Input

Conforming system harus menyediakan reasonable alternate input ketika essential operation sebaliknya bergantung pada touch saja.

Alternate input dapat mencakup:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input tidak perlu menjadi input method yang tercepat atau paling nyaman. Ia harus cukup untuk essential operation.

<a id="accessible-feedback"></a>

### Accessible Feedback

Conforming system harus menyediakan accessible feedback untuk essential actions.

Accessible feedback dapat mencakup:

* confirmation that an action occurred
* indication that an action failed
* progress information
* validation messages
* warning messages
* error messages
* completion status
* current selection
* current focus
* current mode
* current system state

Feedback tidak boleh bergantung secara eksklusif pada unavailable sense dalam related accessibility case.

Misalnya, sound-only success chime tidak cukup ketika sound unavailable. Color-only error state tidak cukup ketika sight unavailable. Vibration-only confirmation tidak cukup ketika touch unavailable.

<a id="accessible-configuration"></a>

### Accessible Configuration

Conforming system harus memungkinkan user mencapai dan menggunakan required accessibility settings melalui accessibility requirements yang sama seperti yang didefinisikan specification ini.

Accessibility settings tidak boleh disembunyikan di balik inaccessible path.

Misalnya, screen-reader-compatible mode tidak cukup jika user harus terlebih dahulu menavigasi unlabeled visual-only menu untuk mengaktifkannya.

System dapat gagal review jika accessibility configuration-nya tidak dapat dicapai atau dioperasikan dalam kondisi yang memang dimaksudkan untuk didukung.

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

System dianggap within spec ketika CatalystUI Team telah meninjau system dan menilai wajar untuk menyimpulkan bahwa system tersebut satisfies A11YSPEC.

System dapat within spec ketika:

* sight-unavailable use tetap reasonably supported
* sound-unavailable use tetap reasonably supported
* touch-unavailable use tetap reasonably supported
* essential functionality tetap accessible dalam setiap required case
* critical functionality tetap accessible dalam setiap required case
* alternate access paths preserve essential meaning dan operation
* accessibility settings, jika ada, dapat dicapai dan digunakan secara accessible
* system tidak menjebak essential functionality di balik satu required sense
* system menggunakan stable accessibility mechanism yang sesuai dengan design-nya

System dapat within spec meskipun experiences tidak identik di semua sensory paths.

System dapat within spec meskipun sebagian nonessential functionality tidak tersedia secara setara di setiap required accessibility case.

<a id="warnings"></a>

### Warnings

Warning dapat diterbitkan ketika system tampak memenuhi A11YSPEC tetapi memiliki concerns yang perlu didokumentasikan.

Warnings dapat mencakup:

* minor nonessential content unavailable in one accessibility case
* slower but usable alternate access paths
* imperfect but understandable captions or transcripts
* limited but functional keyboard navigation
* limited but functional screen-reader support
* minor focus-order concerns that do not block essential use
* redundant visual, auditory, or tactile cues missing from one path
* accessibility settings that are usable but difficult to find
* assistive-technology support that works but could be clearer
* optional workflows that are not equally accessible

Warnings tidak selalu mencegah verification.

<a id="failures"></a>

### Failures

Failure terjadi ketika system tidak memenuhi satu atau lebih required conditions A11YSPEC.

Failures dapat mencakup:

* essential functionality unavailable when sight is unavailable
* essential functionality unavailable when sound is unavailable
* essential functionality unavailable when touch is unavailable
* critical functionality unavailable in any required accessibility case
* no reasonable alternate access path for essential visual information
* no reasonable alternate access path for essential auditory information
* no reasonable alternate access path for essential touch-based operation
* accessibility settings unreachable under the condition they are meant to support
* controls without meaningful labels or structure when required for non-visual use
* sound-only warnings with no visual, tactile, or text equivalent
* color-only status with no non-visual equivalent
* gesture-only operation with no keyboard, pointer, voice, switch, or other alternative
* haptic-only confirmation with no visual or auditory equivalent
* broken assistive-technology support for essential workflows
* major navigation traps
* essential workflows that cannot be completed without the unavailable sense

Failures mencegah verification sampai diselesaikan.

<a id="verification-validity"></a>

### Verification Validity

A11YSPEC verification hanya berlaku untuk reviewed state system pada saat verification diterbitkan.

System dapat mempertahankan verification dalam update berikutnya selama mempertahankan verified accessibility foundation.

Minor wording changes, visual refinements, performance improvements, added accessibility features, dan ordinary content updates tidak otomatis membatalkan verification.

Review baru mungkin diperlukan jika system:

* removes alternate access paths
* breaks assistive-technology support
* substantially changes essential navigation
* removes required accessibility settings
* changes interaction behavior in a way that affects verified accessibility
* introduces new essential workflows without accessible alternatives
* makes previously accessible critical functionality inaccessible
* replaces accessible behavior with single-sense-dependent behavior

Dengan kata lain, meningkatkan accessibility biasanya baik-baik saja.

Merusak verified access model dapat memerlukan review.
