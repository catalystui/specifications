<!-- Ang saling ito ay ginawa ng ChatGPT at dapat suriin ng isang taong tagasalin. -->

<!-- Alisin ang mga linyang ito sa isang pull request pagkatapos ma-verify ang salin. -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Ang mga definition, requirement, at concept na ipinapakita rito ay naglalarawan ng practical accessibility support at maaaring malayang ipahayag muli.

<a id="introduction"></a>

## Panimula

Itinatatag ng **Accessibility Specification (A11YSPEC)** ang core concepts, terminology, at requirements na ginagamit upang suriin ang accessibility support sa loob ng CatalystUI ecosystem. Layunin nitong magbigay ng malinaw na standard para matukoy kung ang isang system, service, framework, application, library, o implementation ay nananatiling meaningfully usable kapag hindi available ang isang primary sensory pathway.

Mahalaga ang accessibility dahil hindi dapat lubos na umasa ang user interface sa isang pandama kapag ang parehong essential meaning ay makatwirang maipapahayag sa pamamagitan ng iba. Maaaring technically functional ang isang system, ngunit kung hindi kayang maunawaan, ma-navigate, ma-configure, o mapatakbo ng user ang essential behavior nito nang walang paningin, tunog, o haplos nang paisa-isa, bigo ang system na magbigay ng reasonable access para sa condition na iyon.

Hindi sinusubukan ng specification na ito na i-verify ang bawat posibleng disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard, o specialized use case. Sa halip, tinutukoy nito ang minimum accessibility foundation na kailangan upang makahulugang ma-access at mapatakbo ng users ang essential portions ng isang system kapag hindi available ang isa sa tatlong primary accessibility senses.

Sa mas simpleng salita, nagtatanong ang A11YSPEC ng tatlong pangunahing tanong:

1. Nauunawaan ba ng users ang essential system nang hindi umaasa sa paningin?
2. Nauunawaan ba ng users ang essential system nang hindi umaasa sa tunog?
3. Napapatakbo ba ng users ang essential system nang hindi umaasa sa haplos?

> [!IMPORTANT]
>
> Tinutukoy ng A11YSPEC ang accessibility requirements para sa verification. Hindi ito kapalit ng legal accessibility standards, platform certification requirements, o specialized assistive-technology review. Maaaring within A11YSPEC ang isang system at kailangan pa rin ng additional review para sa iba pang accessibility standards.

<a id="table-of-contents"></a>

## Talaan ng Nilalaman

- [A11YSPEC](#a11yspec)
  - [Panimula](#introduction)
  - [Talaan ng Nilalaman](#table-of-contents)
  - [Conformance](#conformance)
  - [Primary Accessibility Senses](#primary-accessibility-senses)
    - [Paningin](#sight)
    - [Tunog](#sound)
    - [Haplos](#touch)
    - [Karagdagang Sensory Domains](#additional-sensory-domains)
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
  - [Hindi Available ang Paningin](#sight-unavailable)
  - [Hindi Available ang Tunog](#sound-unavailable)
  - [Hindi Available ang Haplos](#touch-unavailable)
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

Itinuturing na conformant sa A11YSPEC ang isang system kapag natutugunan nito ang requirements na tinutukoy ng dokumentong ito para sa bawat required accessibility case.

Ang isang conforming system ay dapat:

1. Manatiling makatwirang nagagamit kapag hindi available ang paningin.
2. Manatiling makatwirang nagagamit kapag hindi available ang tunog.
3. Manatiling makatwirang nagagamit kapag hindi available ang haplos.
4. Panatilihin ang access sa essential functionality sa bawat required accessibility case.
5. Panatilihin ang access sa lahat ng critical functionality sa bawat required accessibility case.
6. Magbigay ng reasonable alternate access paths kapag ang essential meaning o operation ay kung hindi man ay dedepende sa unavailable sense.
7. Gumamit ng stable accessibility mechanism na angkop sa reviewed system.
8. Iwasang umasa nang eksklusibo sa isang primary sense para sa essential functionality.

Hindi kailangang magbigay ang system ng identical experiences sa bawat sensory path. Maaaring mas mabagal ang non-visual experience kaysa sa visual. Maaaring mangailangan ang sound-free experience ng captions, visual indicators, o haptic confirmation. Maaaring mangailangan ang touch-free experience ng keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction, o ibang non-touch method.

Nakatuon ang verification sa practical access sa essential functionality, hindi sa identical presentation.

<a id="primary-accessibility-senses"></a>

## Primary Accessibility Senses

Para sa A11YSPEC, ang tatlong primary accessibility senses ay **paningin**, **tunog**, at **haplos**.

Primary ang mga pandamang ito dahil sila ang pinakakaraniwang sensory pathways na kasangkot sa user-interface interaction. Maaaring magbigay ang system ng output sa pamamagitan ng paningin, tunog, o haplos, at maaaring tumanggap ito ng interaction sa pamamagitan ng touch, motion, voice, keyboard input, pointer input, switch input, o ibang available input path.

<a id="sight"></a>

### Paningin

Ang paningin ay ang visual sensory pathway kung saan nararamdaman o nauunawaan ng user ang visual output.

Maaaring kasangkot ang paningin sa pag-unawa sa:

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

Umaasa ang isang system sa paningin kapag ang essential meaning o operation ay nangangailangan na makita ng user ang impormasyon.

<a id="sound"></a>

### Tunog

Ang tunog ay ang auditory sensory pathway kung saan naririnig ng user ang audio output.

Maaaring kasangkot ang tunog sa pag-unawa sa:

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

Umaasa ang isang system sa tunog kapag ang essential meaning o operation ay nangangailangan na marinig ng user ang impormasyon.

<a id="touch"></a>

### Haplos

Ang haplos ay ang tactile sensory pathway kung saan nararamdaman ng user ang physical o haptic output, at ang physical interaction pathway kung saan maaaring magpatakbo ang user ng controls sa pamamagitan ng direct contact, pressure, gesture, o movement.

Maaaring kasangkot ang haplos sa pagdama o paggawa ng:

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

Umaasa ang isang system sa haplos kapag ang essential meaning o operation ay nangangailangan ng tactile perception o touch-based interaction nang walang reasonable alternate input o output path.

<a id="additional-sensory-domains"></a>

### Karagdagang Sensory Domains

Kinikilala rin ng CatalystUI ang **panlasa** at **pang-amoy** bilang sensory domains.

Maaaring isaalang-alang ang panlasa at pang-amoy sa accessibility review kapag meaningful ang paggamit ng system sa kanila. Inclusive ang mga pandamang ito para sa verification, ibig sabihin maaari nilang palakasin o suportahan ang accessibility review kapag nagbibigay sila ng meaningful alternate access o karagdagang context.

Hindi kasalukuyang exclusive para sa failure ang panlasa at pang-amoy. Hindi bumabagsak ang isang system sa A11YSPEC dahil lamang hindi ito nagbibigay ng taste-based o smell-based interaction.

Pangunahing inaalam ng A11YSPEC kung nananatiling makatwirang nagagamit ang system kapag ang paningin, tunog, o haplos ay hindi available nang paisa-isa.

<a id="required-accessibility-cases"></a>

## Required Accessibility Cases

Dapat marepaso ang isang conforming system laban sa bawat required accessibility case.

| Hindi Available na Pandama | Kinakailangang Accessibility Behavior |
| -------------------------- | ------------------------------------- |
| Paningin                   | Dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng tunog at haplos. |
| Tunog                      | Dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng paningin at haplos. |
| Haplos                     | Dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng paningin at tunog. |

Indibidwal na nire-review ang bawat case.

Hindi kinakailangang manatiling ganap na usable ang system kapag maraming primary senses ang hindi available nang sabay-sabay maliban kung kasama ang condition na iyon sa reviewed scope.

Hindi kinakailangang ibigay ng system ang bawat posibleng accommodation. Dapat itong magbigay ng reasonable access sa essential functionality sa ilalim ng bawat required accessibility case.

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Ang essential functionality ay anumang behavior, content, control, output, input, workflow, o configuration na makatwirang kailangan ng user upang maunawaan, ma-navigate, ma-configure, o mapatakbo ang essential behavior ng isang system.

Maaaring kabilang sa essential functionality ang:

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
* anumang interaction na kailangan para sa normal na paggamit

Hindi kailangang gawing pantay na available ng system ang bawat decorative, optional, redundant, o nonessential feature sa bawat sensory path. Gayunpaman, hindi dapat ma-block ang user sa paggamit ng essential system dahil sa unavailable sense.

<a id="critical-functionality"></a>

### Critical Functionality

Ang critical functionality ay essential functionality kung saan ang pagkawala ng access ay maaaring pumigil sa meaningful use, lumikha ng seryosong error, o magdulot na gumawa ang user ng mahalagang desisyon nang hindi nauunawaan ang consequence.

Maaaring kabilang sa critical functionality ang:

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
* core navigation required to reach accessibility settings

Dapat manatiling accessible ang critical functionality sa bawat required accessibility case.

Maaaring bumagsak ang isang system sa A11YSPEC kung ang critical functionality ay eksklusibong nakadepende sa unavailable sense.

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Ang nonessential functionality ay functionality na hindi makatwirang kailangan ng user upang maunawaan, ma-navigate, ma-configure, o mapatakbo ang essential behavior ng isang system.

Maaaring kabilang sa nonessential functionality ang:

* decorative animation
* optional effects
* cosmetic visual polish
* nonessential sound effects
* redundant haptic effects
* optional marketing content
* optional tutorial content
* hidden diagnostic behavior
* developer-facing controls
* experimental features outside the reviewed scope

Maaaring maging inaccessible ang nonessential functionality sa isa o higit pang accessibility cases nang hindi awtomatikong nagdudulot ng failure. Gayunpaman, hindi dapat ipagkamali ang nonessential functionality bilang essential functionality dahil lamang inconvenient itong suportahan.

<a id="accessibility-requirements"></a>

## Accessibility Requirements

<a id="essential-access-requirement"></a>

### Essential Access Requirement

Natutugunan ng isang system ang essential access requirement kapag ang essential functionality ay nananatiling reasonably understandable, navigable, configurable, at operable sa bawat required accessibility case.

Hindi kailangang maging identical ang essential experience sa lahat ng senses.

Dapat manatiling meaningfully usable ang essential experience.

<a id="critical-access-requirement"></a>

### Critical Access Requirement

Natutugunan ng isang system ang critical access requirement kapag ang lahat ng critical functionality ay nananatiling accessible sa bawat required accessibility case.

Hindi dapat maitago ang critical functionality sa likod ng isang required sensory pathway.

Halimbawa, hindi dapat magbigay ang isang system ng accessible interface para sa ordinaryong paggamit habang iniiwan ang account deletion warnings, payment confirmations, privacy decisions, o accessibility settings na nakadepende lamang sa paningin, tunog, o haplos.

<a id="alternate-access-requirement"></a>

### Alternate Access Requirement

Natutugunan ng isang system ang alternate access requirement kapag ang essential meaning o operation na ibinibigay sa pamamagitan ng isang primary sense ay makatwirang available din sa pamamagitan ng ibang sensory o interaction path kapag hindi available ang sense na iyon.

Maaaring ibigay ang alternate access sa pamamagitan ng:

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
* another stable mechanism appropriate to the system

Hindi kailangang perpektong tumugma ang alternate path sa original path. Dapat nitong panatilihin ang essential meaning at operation.

<a id="no-single-sense-dependency"></a>

### No Single-Sense Dependency

Hindi dapat i-require ng isang system ang isang primary sense bilang tanging path patungo sa essential functionality.

Maaaring gamitin ng system ang paningin, tunog, o haplos bilang primary experience. Gayunpaman, kapag hindi available ang sense na iyon, dapat mayroon pa ring reasonable way ang user upang maunawaan at mapatakbo ang essential system sa pamamagitan ng natitirang sensory paths.

Maaaring bumagsak ang system sa review kapag ang essential information o interaction ay available lamang sa pamamagitan ng:

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

## Hindi Available ang Paningin

Kapag hindi available ang paningin, dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng tunog at haplos.

Ibig sabihin nito, ang essential visual information ay dapat magkaroon ng meaningful non-visual access path.

Maaaring matugunan ng system ang requirement na ito sa pamamagitan ng:

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

Hindi dapat umasa nang eksklusibo ang isang system sa:

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

kapag kailangan ang impormasyong iyon upang maunawaan o mapatakbo ang essential functionality.

Maaaring bumagsak ang system sa case na ito kung hindi makatwirang maka-navigate, makaunawa, o makapagpatakbo ang user ng essential system nang walang paningin.

<a id="sound-unavailable"></a>

## Hindi Available ang Tunog

Kapag hindi available ang tunog, dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng paningin at haplos.

Ibig sabihin nito, ang essential auditory information ay dapat magkaroon ng meaningful non-auditory access path.

Maaaring matugunan ng system ang requirement na ito sa pamamagitan ng:

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

Hindi dapat umasa nang eksklusibo ang system sa:

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

kapag kailangan ang impormasyong iyon upang maunawaan o mapatakbo ang essential functionality.

Maaaring bumagsak ang system sa case na ito kung hindi makatwirang maka-navigate, makaunawa, o makapagpatakbo ang user ng essential system nang walang tunog.

<a id="touch-unavailable"></a>

## Hindi Available ang Haplos

Kapag hindi available ang haplos, dapat manatiling makatwirang nagagamit ang system sa pamamagitan ng paningin at tunog.

Ibig sabihin nito, ang essential tactile information at touch-based operation ay dapat magkaroon ng meaningful non-touch access path.

Maaaring matugunan ng system ang requirement na ito sa pamamagitan ng:

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

Hindi dapat umasa nang eksklusibo ang system sa:

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

kapag kailangan ang interaction na iyon upang maunawaan o mapatakbo ang essential functionality.

Maaaring bumagsak ang system sa case na ito kung hindi makatwirang maka-navigate, makaunawa, o makapagpatakbo ang user ng essential system nang walang haplos.

<a id="implementation-requirements"></a>

## Implementation Requirements

<a id="stable-accessibility-mechanism"></a>

### Stable Accessibility Mechanism

Dapat gumamit ang conforming system ng stable accessibility mechanism na angkop sa system na nire-review.

Dapat pahintulutan ng stable accessibility mechanism na mapanatili, ma-update, ma-review, at mapalawak ang accessibility behavior nang hindi umaasa sa fragile o undocumented behavior.

Maaaring kabilang sa stable accessibility mechanism ang:

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
* another stable structure appropriate to the system

Dapat iwasan ng system ang implementation ng essential functionality sa paraang humahadlang sa reasonable alternate access.

<a id="semantic-structure"></a>

### Semantic Structure

Dapat magbigay ang conforming system ng semantic structure kapag nagpapakita ang system ng meaningful content o controls.

Maaaring kabilang sa semantic structure ang:

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

Lalong mahalaga ang semantic structure kapag hindi available ang paningin, dahil madalas umaasa ang assistive technologies sa semantic information upang maipahayag ang visual interfaces sa pamamagitan ng non-visual output.

Maaaring bumagsak ang system sa review kung hindi mauunawaan ang essential controls o content dahil ang kanilang structure, labels, o relationships ay hindi available sa alternate access paths.

<a id="alternate-output"></a>

### Alternate Output

Dapat magbigay ang conforming system ng reasonable alternate output kapag ang essential meaning ay kung hindi man ay dedepende sa unavailable sense.

Maaaring kabilang sa alternate output ang:

* visual output for auditory information
* auditory output for visual information
* tactile output for visual or auditory information
* text equivalents
* captions
* transcripts
* spoken descriptions
* visible status messages
* haptic confirmation
* another appropriate output path

Dapat panatilihin ng alternate output ang essential meaning.

<a id="alternate-input"></a>

### Alternate Input

Dapat magbigay ang conforming system ng reasonable alternate input kapag ang essential operation ay kung hindi man ay dedepende lamang sa touch.

Maaaring kabilang sa alternate input ang:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Hindi kailangang ang alternate input ang pinakamabilis o pinakakomportableng input method. Dapat itong sapat para sa essential operation.

<a id="accessible-feedback"></a>

### Accessible Feedback

Dapat magbigay ang conforming system ng accessible feedback para sa essential actions.

Maaaring kabilang sa accessible feedback ang:

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

Hindi dapat umasa nang eksklusibo ang feedback sa unavailable sense sa kaugnay na accessibility case.

Halimbawa, hindi sapat ang sound-only success chime kapag hindi available ang tunog. Hindi sapat ang color-only error state kapag hindi available ang paningin. Hindi sapat ang vibration-only confirmation kapag hindi available ang haplos.

<a id="accessible-configuration"></a>

### Accessible Configuration

Dapat payagan ng conforming system ang users na maabot at magamit ang required accessibility settings sa pamamagitan ng parehong accessibility requirements na tinutukoy ng specification na ito.

Hindi dapat maitago ang accessibility settings sa likod ng inaccessible path.

Halimbawa, hindi sapat ang screen-reader-compatible mode kung kailangan munang mag-navigate ang user sa unlabeled visual-only menu upang i-enable ito.

Maaaring bumagsak ang system sa review kung ang accessibility configuration nito ay hindi maabot o mapatakbo sa condition na nilalayon nitong suportahan.

<a id="verification"></a>

## Verification

<a id="within-spec"></a>

### Within Spec

Itinuturing na within spec ang isang system kapag nirepaso ito ng CatalystUI Team at napatunayang makatwirang ipalagay na natutugunan nito ang A11YSPEC.

Maaaring within spec ang isang system kapag:

* sight-unavailable use remains reasonably supported
* sound-unavailable use remains reasonably supported
* touch-unavailable use remains reasonably supported
* essential functionality remains accessible in each required case
* critical functionality remains accessible in each required case
* alternate access paths preserve essential meaning and operation
* accessibility settings, when present, can be reached and used accessibly
* the system does not trap essential functionality behind one required sense
* the system uses a stable accessibility mechanism appropriate to its design

Maaaring within spec ang isang system kahit hindi identical ang experiences sa lahat ng sensory paths.

Maaaring within spec ang isang system kahit ang ilang nonessential functionality ay hindi pantay na available sa bawat required accessibility case.

<a id="warnings"></a>

### Warnings

Maaaring maglabas ng warning kapag mukhang natutugunan ng system ang A11YSPEC ngunit may concerns na dapat i-document.

Maaaring kabilang sa warnings ang:

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

Hindi kinakailangang pigilan ng warnings ang verification.

<a id="failures"></a>

### Failures

Nagkakaroon ng failure kapag hindi natutugunan ng system ang isa o higit pang required conditions ng A11YSPEC.

Maaaring kabilang sa failures ang:

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

Pinipigilan ng failures ang verification hanggang maresolba.

<a id="verification-validity"></a>

### Verification Validity

Nalalapat lamang ang A11YSPEC verification sa reviewed state ng system sa oras na inilabas ang verification.

Maaaring panatilihin ng isang system ang verification sa mga susunod na updates hangga't pinapanatili nito ang verified accessibility foundation.

Hindi awtomatikong nagpapawalang-bisa sa verification ang minor wording changes, visual refinements, performance improvements, added accessibility features, at ordinary content updates.

Maaaring kailanganin ang bagong review kung ang isang system ay:

* removes alternate access paths
* breaks assistive-technology support
* substantially changes essential navigation
* removes required accessibility settings
* changes interaction behavior in a way that affects verified accessibility
* introduces new essential workflows without accessible alternatives
* makes previously accessible critical functionality inaccessible
* replaces accessible behavior with single-sense-dependent behavior

Sa madaling salita, karaniwang ayos lang ang pagpapahusay ng accessibility.

Ang pagsira sa verified access model ay maaaring mangailangan ng review.
