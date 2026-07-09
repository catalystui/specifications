<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza-człowieka. -->

<!-- Usuń te wiersze w pull request po zweryfikowaniu tłumaczenia. -->

# A11YSPEC

<br/>

> **Accessibility Specification**<br/>
> Revision 1<br/>
> July 8th, 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Definicje, wymagania i koncepcje przedstawione tutaj opisują praktyczne wsparcie dostępności i mogą być swobodnie wyrażane na nowo.

<a id="introduction"></a>

## Wprowadzenie

**Accessibility Specification (A11YSPEC)** ustanawia core concepts, terminology i requirements używane do oceny accessibility support w ekosystemie CatalystUI. Jej celem jest zapewnienie jasnego standardu do ustalenia, czy system, service, framework, application, library lub implementation pozostaje meaningfully usable, gdy jedna primary sensory pathway jest niedostępna.

Dostępność ma znaczenie, ponieważ user interface nie powinien całkowicie zależeć od jednego zmysłu, gdy to samo essential meaning można rozsądnie przekazać przez inny. System może być technically functional, ale jeśli użytkownik nie może indywidualnie bez wzroku, dźwięku albo dotyku zrozumieć, nawigować, skonfigurować albo obsłużyć jego essential behavior, system nie zapewnił reasonable access dla tego condition.

Ta specification nie próbuje weryfikować każdej możliwej disability, device, assistive technology, medical condition, legal requirement, regional accessibility standard ani specialized use case. Zamiast tego definiuje minimalną accessibility foundation wymaganą, aby użytkownicy mogli sensownie uzyskać dostęp do essential portions systemu i je obsługiwać, gdy jeden z trzech primary accessibility senses jest niedostępny.

Prościej mówiąc, A11YSPEC zadaje trzy główne pytania:

1. Czy użytkownicy mogą zrozumieć essential system bez polegania na wzroku?
2. Czy użytkownicy mogą zrozumieć essential system bez polegania na dźwięku?
3. Czy użytkownicy mogą obsługiwać essential system bez polegania na dotyku?

> [!IMPORTANT]
>
> A11YSPEC definiuje accessibility requirements dla verification. Nie zastępuje legal accessibility standards, platform certification requirements ani specialized assistive-technology review. System może być within A11YSPEC, a mimo to wymagać additional review dla innych accessibility standards.

<a id="table-of-contents"></a>

## Spis treści

- [A11YSPEC](#a11yspec)
  - [Wprowadzenie](#introduction)
  - [Spis treści](#table-of-contents)
  - [Zgodność](#conformance)
  - [Podstawowe zmysły dostępności](#primary-accessibility-senses)
    - [Wzrok](#sight)
    - [Dźwięk](#sound)
    - [Dotyk](#touch)
    - [Dodatkowe domeny sensoryczne](#additional-sensory-domains)
  - [Wymagane przypadki dostępności](#required-accessibility-cases)
  - [Essential Functionality](#essential-functionality)
    - [Essential Functionality](#essential-functionality-1)
    - [Critical Functionality](#critical-functionality)
    - [Nonessential Functionality](#nonessential-functionality)
  - [Wymagania dostępności](#accessibility-requirements)
    - [Wymaganie essential access](#essential-access-requirement)
    - [Wymaganie critical access](#critical-access-requirement)
    - [Wymaganie alternate access](#alternate-access-requirement)
    - [Brak zależności od jednego zmysłu](#no-single-sense-dependency)
  - [Niedostępny wzrok](#sight-unavailable)
  - [Niedostępny dźwięk](#sound-unavailable)
  - [Niedostępny dotyk](#touch-unavailable)
  - [Wymagania implementacyjne](#implementation-requirements)
    - [Stabilny mechanizm dostępności](#stable-accessibility-mechanism)
    - [Struktura semantyczna](#semantic-structure)
    - [Alternate Output](#alternate-output)
    - [Alternate Input](#alternate-input)
    - [Accessible Feedback](#accessible-feedback)
    - [Accessible Configuration](#accessible-configuration)
  - [Weryfikacja](#verification)
    - [Within Spec](#within-spec)
    - [Ostrzeżenia](#warnings)
    - [Niepowodzenia](#failures)
    - [Ważność weryfikacji](#verification-validity)

<a id="conformance"></a>

## Zgodność

System jest uznawany za zgodny z A11YSPEC, gdy spełnia requirements zdefiniowane przez ten dokument dla każdego required accessibility case.

Zgodny system musi:

1. Pozostawać rozsądnie używalny, gdy wzrok jest niedostępny.
2. Pozostawać rozsądnie używalny, gdy dźwięk jest niedostępny.
3. Pozostawać rozsądnie używalny, gdy dotyk jest niedostępny.
4. Zachowywać dostęp do essential functionality w każdym required accessibility case.
5. Zachowywać dostęp do całej critical functionality w każdym required accessibility case.
6. Zapewniać rozsądne alternate access paths, gdy essential meaning albo operation w przeciwnym razie zależałyby od niedostępnego zmysłu.
7. Używać stable accessibility mechanism właściwego dla reviewed system.
8. Unikać wyłącznego polegania na jednym primary sense dla essential functionality.

System nie musi zapewniać identycznych experiences we wszystkich sensory paths. Non-visual experience może być wolniejsze niż visual. Sound-free experience może wymagać captions, visual indicators lub haptic confirmation. Touch-free experience może wymagać keyboard navigation, pointer alternatives, voice interaction, switch-compatible interaction lub innej non-touch method.

Verification dotyczy praktycznego dostępu do essential functionality, a nie identycznej prezentacji.

<a id="primary-accessibility-senses"></a>

## Podstawowe zmysły dostępności

Dla A11YSPEC trzema podstawowymi accessibility senses są **wzrok**, **dźwięk** i **dotyk**.

Te zmysły są podstawowe, ponieważ są najczęstszymi sensory pathways uczestniczącymi w user-interface interaction. System może dostarczać output przez wzrok, dźwięk albo dotyk oraz może odbierać interaction przez dotyk, ruch, głos, keyboard input, pointer input, switch input lub inną dostępną input path.

<a id="sight"></a>

### Wzrok

Wzrok jest visual sensory pathway, przez którą użytkownik odbiera visual output.

Wzrok może uczestniczyć w odbiorze:

* tekstu
* koloru
* kształtu
* położenia
* layout
* animacji
* icons
* images
* video
* visual warnings
* visual status indicators
* visible controls

System zależy od wzroku, gdy essential meaning albo operation wymaga od użytkownika wizualnego postrzeżenia informacji.

<a id="sound"></a>

### Dźwięk

Dźwięk jest auditory sensory pathway, przez którą użytkownik odbiera audio output.

Dźwięk może uczestniczyć w odbiorze:

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

System zależy od dźwięku, gdy essential meaning albo operation wymaga od użytkownika usłyszenia informacji.

<a id="touch"></a>

### Dotyk

Dotyk jest tactile sensory pathway, przez którą użytkownik odbiera physical lub haptic output, oraz physical interaction pathway, przez którą użytkownik może obsługiwać controls przez bezpośredni kontakt, nacisk, gesture lub ruch.

Dotyk może uczestniczyć w odbiorze albo wykonywaniu:

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

System zależy od dotyku, gdy essential meaning albo operation wymaga tactile perception lub touch-based interaction bez rozsądnej alternate input or output path.

<a id="additional-sensory-domains"></a>

### Dodatkowe domeny sensoryczne

CatalystUI rozpoznaje także **smak** i **węch** jako sensory domains.

Smak i węch mogą być brane pod uwagę podczas accessibility review, gdy system używa ich w znaczący sposób. Te zmysły są inclusive dla verification, co oznacza, że mogą wzmacniać albo wspierać accessibility review, gdy zapewniają meaningful alternate access lub dodatkowy kontekst.

Smak i węch nie są obecnie exclusive dla failure. System nie oblewa A11YSPEC tylko dlatego, że nie zapewnia taste-based lub smell-based interaction.

A11YSPEC dotyczy przede wszystkim tego, czy system pozostaje rozsądnie używalny, gdy wzrok, dźwięk albo dotyk jest indywidualnie niedostępny.

<a id="required-accessibility-cases"></a>

## Wymagane przypadki dostępności

Zgodny system musi zostać sprawdzony względem każdego required accessibility case.

| Niedostępny zmysł | Wymagane zachowanie dostępności |
| ----------------- | ----------------------------------------------------------------- |
| Wzrok             | System musi pozostawać rozsądnie używalny przez dźwięk i dotyk. |
| Dźwięk            | System musi pozostawać rozsądnie używalny przez wzrok i dotyk. |
| Dotyk             | System musi pozostawać rozsądnie używalny przez wzrok i dźwięk. |

Każdy przypadek jest sprawdzany indywidualnie.

System nie musi pozostawać w pełni używalny, gdy wiele primary senses jest niedostępnych jednocześnie, chyba że ten condition jest uwzględniony w reviewed scope.

System nie musi zapewniać every possible accommodation. Musi zapewniać reasonable access do essential functionality w każdym required accessibility case.

<a id="essential-functionality"></a>

## Essential Functionality

<a id="essential-functionality-1"></a>

### Essential Functionality

Essential functionality to każde behavior, content, control, output, input, workflow lub configuration, którego użytkownik rozsądnie potrzebuje, aby zrozumieć, nawigować, skonfigurować albo obsługiwać essential behavior systemu.

Essential functionality może obejmować:

* primary navigation
* core workflows
* required controls
* ważne ostrzeżenia
* ważne błędy
* required confirmation messages
* account or session access
* settings and preferences
* language configuration
* accessibility configuration
* essential instructions
* user-facing status information
* any interaction required for normal use

System nie musi czynić każdej decorative, optional, redundant albo nonessential feature jednakowo dostępnej przez każdą sensory path. Użytkownik nie może jednak zostać zablokowany przed użyciem essential system przez unavailable sense.

<a id="critical-functionality"></a>

### Critical Functionality

Critical functionality to essential functionality, której utrata dostępu może uniemożliwić meaningful use, stworzyć serious error albo spowodować, że użytkownik podejmie ważną decyzję bez zrozumienia consequence.

Critical functionality może obejmować:

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

Critical functionality musi pozostawać dostępna w każdym required accessibility case.

System może nie spełnić A11YSPEC, jeśli critical functionality zależy wyłącznie od unavailable sense.

<a id="nonessential-functionality"></a>

### Nonessential Functionality

Nonessential functionality to functionality, która nie jest rozsądnie wymagana, aby użytkownik rozumiał, nawigował, konfigurował albo obsługiwał essential behavior systemu.

Nonessential functionality może obejmować:

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

Nonessential functionality może być inaccessible w jednym lub wielu accessibility cases bez automatycznego failure. Nie należy jednak mylić nonessential functionality z essential functionality tylko dlatego, że jej wsparcie jest niewygodne.

<a id="accessibility-requirements"></a>

## Wymagania dostępności

<a id="essential-access-requirement"></a>

### Wymaganie essential access

System spełnia essential access requirement, gdy essential functionality pozostaje rozsądnie understandable, navigable, configurable i operable w każdym required accessibility case.

Essential experience nie musi być identyczne we wszystkich zmysłach.

Essential experience musi pozostawać meaningfully usable.

<a id="critical-access-requirement"></a>

### Wymaganie critical access

System spełnia critical access requirement, gdy cała critical functionality pozostaje accessible w każdym required accessibility case.

Critical functionality nie może być ukryta za jedną wymaganą sensory pathway.

Na przykład system nie powinien zapewniać accessible interface do zwykłego użycia, a jednocześnie zostawiać account deletion warnings, payment confirmations, privacy decisions lub accessibility settings zależnych wyłącznie od wzroku, dźwięku albo dotyku.

<a id="alternate-access-requirement"></a>

### Wymaganie alternate access

System spełnia alternate access requirement, gdy essential meaning albo operation zapewnione przez jeden primary sense jest także rozsądnie dostępne przez inną sensory or interaction path, gdy ten zmysł jest niedostępny.

Alternate access może być zapewniony przez:

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

Alternate path nie musi idealnie odpowiadać original path. Musi zachowywać essential meaning i operation.

<a id="no-single-sense-dependency"></a>

### Brak zależności od jednego zmysłu

System nie może wymagać jednego primary sense jako jedynej ścieżki do essential functionality.

System może używać wzroku, dźwięku albo dotyku jako primary experience. Jednak gdy ten zmysł jest unavailable, użytkownik nadal musi mieć rozsądny sposób zrozumienia i obsługi essential system przez pozostałe sensory paths.

System może nie przejść review, gdy essential information albo interaction jest dostępna wyłącznie przez:

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

## Niedostępny wzrok

Gdy wzrok jest niedostępny, system musi pozostawać rozsądnie używalny przez dźwięk i dotyk.

Oznacza to, że essential visual information musi mieć meaningful non-visual access path.

System może spełnić to wymaganie przez:

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

System nie powinien polegać wyłącznie na:

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

kiedy ta informacja jest wymagana do zrozumienia albo obsługi essential functionality.

System może nie przejść tego case, jeśli użytkownik nie może rozsądnie nawigować, rozumieć albo obsługiwać essential system bez wzroku.

<a id="sound-unavailable"></a>

## Niedostępny dźwięk

Gdy dźwięk jest niedostępny, system musi pozostawać rozsądnie używalny przez wzrok i dotyk.

Oznacza to, że essential auditory information musi mieć meaningful non-auditory access path.

System może spełnić to wymaganie przez:

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

System nie powinien polegać wyłącznie na:

* sound effects
* spoken instructions
* alerts
* alarms
* music cues
* audio-only prompts
* spoken confirmation
* audio-only warnings
* audio-only status indicators

kiedy ta informacja jest wymagana do zrozumienia albo obsługi essential functionality.

System może nie przejść tego case, jeśli użytkownik nie może rozsądnie nawigować, rozumieć albo obsługiwać essential system bez dźwięku.

<a id="touch-unavailable"></a>

## Niedostępny dotyk

Gdy dotyk jest niedostępny, system musi pozostawać rozsądnie używalny przez wzrok i dźwięk.

Oznacza to, że essential tactile information i touch-based operation muszą mieć meaningful non-touch access path.

System może spełnić to wymaganie przez:

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

System nie powinien polegać wyłącznie na:

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

kiedy ta interaction jest wymagana do zrozumienia albo obsługi essential functionality.

System może nie przejść tego case, jeśli użytkownik nie może rozsądnie nawigować, rozumieć albo obsługiwać essential system bez dotyku.

<a id="implementation-requirements"></a>

## Wymagania implementacyjne

<a id="stable-accessibility-mechanism"></a>

### Stabilny mechanizm dostępności

Zgodny system musi używać stable accessibility mechanism odpowiedniego dla sprawdzanego systemu.

Stable accessibility mechanism powinien pozwalać utrzymywać, aktualizować, sprawdzać i rozszerzać accessibility behavior bez polegania na fragile albo undocumented behavior.

Stable accessibility mechanism może obejmować:

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

System powinien unikać implementowania essential functionality w sposób, który uniemożliwia reasonable alternate access.

<a id="semantic-structure"></a>

### Struktura semantyczna

Zgodny system powinien zapewniać semantic structure, gdy przedstawia meaningful content lub controls.

Semantic structure może obejmować:

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

Semantic structure jest szczególnie ważna, gdy wzrok jest niedostępny, ponieważ assistive technologies często polegają na semantic information, aby przekazywać visual interfaces przez non-visual output.

System może nie przejść review, jeśli essential controls albo content nie mogą zostać zrozumiane, ponieważ ich structure, labels albo relationships są niedostępne przez alternate access paths.

<a id="alternate-output"></a>

### Alternate Output

Zgodny system musi zapewniać reasonable alternate output, gdy essential meaning w przeciwnym razie zależałoby od unavailable sense.

Alternate output może obejmować:

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

Alternate output musi zachowywać essential meaning.

<a id="alternate-input"></a>

### Alternate Input

Zgodny system musi zapewniać reasonable alternate input, gdy essential operation w przeciwnym razie zależałoby wyłącznie od dotyku.

Alternate input może obejmować:

* keyboard input
* pointer input
* voice input
* switch input
* remote input
* gaze-compatible input
* command input
* another appropriate input path

Alternate input nie musi być najszybszą ani najwygodniejszą metodą input. Musi wystarczać dla essential operation.

<a id="accessible-feedback"></a>

### Accessible Feedback

Zgodny system musi zapewniać accessible feedback dla essential actions.

Accessible feedback może obejmować:

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

Feedback nie może polegać wyłącznie na unavailable sense w powiązanym accessibility case.

Na przykład sound-only success chime nie wystarcza, gdy dźwięk jest niedostępny. Color-only error state nie wystarcza, gdy wzrok jest niedostępny. Vibration-only confirmation nie wystarcza, gdy dotyk jest niedostępny.

<a id="accessible-configuration"></a>

### Accessible Configuration

Zgodny system musi pozwalać użytkownikom dotrzeć do required accessibility settings i używać ich zgodnie z tymi samymi accessibility requirements zdefiniowanymi przez tę specification.

Accessibility settings nie mogą być ukryte za inaccessible path.

Na przykład screen-reader-compatible mode nie wystarcza, jeśli użytkownik musi najpierw przejść przez nieopisane visual-only menu, aby go włączyć.

System może nie przejść review, jeśli jego accessibility configuration nie może zostać osiągnięta albo obsłużona w condition, które ma wspierać.

<a id="verification"></a>

## Weryfikacja

<a id="within-spec"></a>

### Within Spec

System jest uznawany za within spec, gdy CatalystUI Team sprawdził system i uznał za rozsądne stwierdzić, że spełnia A11YSPEC.

System może być within spec, gdy:

* sight-unavailable use remains reasonably supported
* sound-unavailable use remains reasonably supported
* touch-unavailable use remains reasonably supported
* essential functionality remains accessible in each required case
* critical functionality remains accessible in each required case
* alternate access paths preserve essential meaning and operation
* accessibility settings, when present, can be reached and used accessibly
* the system does not trap essential functionality behind one required sense
* the system uses a stable accessibility mechanism appropriate to its design

System może być within spec, nawet jeśli experiences nie są identyczne we wszystkich sensory paths.

System może być within spec, nawet jeśli część nonessential functionality nie jest jednakowo dostępna w każdym required accessibility case.

<a id="warnings"></a>

### Ostrzeżenia

Warning może zostać wydany, gdy system wydaje się spełniać A11YSPEC, ale zawiera concerns, które powinny zostać udokumentowane.

Warnings mogą obejmować:

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

Warnings niekoniecznie uniemożliwiają verification.

<a id="failures"></a>

### Niepowodzenia

Failure występuje, gdy system nie spełnia jednego lub więcej wymaganych warunków A11YSPEC.

Failures mogą obejmować:

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

Failures uniemożliwiają verification, dopóki nie zostaną rozwiązane.

<a id="verification-validity"></a>

### Ważność weryfikacji

A11YSPEC verification dotyczy tylko reviewed state systemu w chwili wydania verification.

System może zachować verification przy późniejszych updates, o ile zachowuje verified accessibility foundation.

Minor wording changes, visual refinements, performance improvements, added accessibility features i ordinary content updates nie unieważniają automatycznie verification.

Nowy review może być wymagany, jeśli system:

* removes alternate access paths
* breaks assistive-technology support
* substantially changes essential navigation
* removes required accessibility settings
* changes interaction behavior in a way that affects verified accessibility
* introduces new essential workflows without accessible alternatives
* makes previously accessible critical functionality inaccessible
* replaces accessible behavior with single-sense-dependent behavior

Innymi słowy, poprawianie accessibility zwykle jest w porządku.

Zepsucie verified access model może wymagać review.
