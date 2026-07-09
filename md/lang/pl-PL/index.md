<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza-człowieka. -->

<!-- Usuń te wiersze w pull request po zweryfikowaniu tłumaczenia. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Witamy w dokumentacji CatalystUI Verification dotyczącej dostępności.

**CatalystUI Verified for Accessibility** oznacza, że service, framework, application, library lub system został sprawdzony przez CatalystUI Team i uznany za nadal rozsądnie używalny, gdy jeden z trzech podstawowych zmysłów uczestniczących w user-interface interaction jest indywidualnie niedostępny.

Dla tej weryfikacji CatalystUI określa trzy podstawowe accessibility senses jako **wzrok**, **dźwięk** i **dotyk**. Zweryfikowany system musi zachować rozsądny dostęp do swojej essential functionality, gdy którykolwiek z tych zmysłów jest niedostępny, polegając na pozostałych dostępnych sensory domains.

Prościej mówiąc, ta weryfikacja pyta, czy użytkownik nadal może sensownie rozumieć, nawigować i obsługiwać essential parts systemu, jeśli nie może indywidualnie polegać na wzroku, dźwięku albo dotyku.

## Cel

Dostępność ma znaczenie, ponieważ user interface nie powinien całkowicie zależeć od jednej sensory pathway, gdy to samo essential meaning można rozsądnie przekazać przez inną.

CatalystUI jest zaprojektowany wokół wiernego przepływu data między systemami a ludzką percepcją. Jeśli ważna informacja jest wyłącznie widoczna, wyłącznie słyszalna albo dostępna wyłącznie przez dotyk, system może stać się nieużywalny dla użytkowników, którzy nie mogą polegać na tym zmyśle. Accessibility Verification istnieje po to, aby wskazywać systemy, które zachowują dostęp, pozwalając essential information i interaction trwać przez alternatywne sensory routes.

Celem nie jest wymaganie każdej możliwej metody interakcji, każdej assistive technology ani każdego specjalistycznego dostosowania. Celem jest ustalenie, czy essential system pozostaje meaningfully usable, gdy wzrok, dźwięk albo dotyk jest indywidualnie niedostępny.

## Co oznacza weryfikacja

System staje się **CatalystUI Verified for Accessibility**, gdy zostanie sprawdzony względem requirements wymienionych w tej sekcji i uznany za within spec.

Aby zostać zweryfikowanym, system musi pozostawać rozsądnie używalny w każdym z poniższych przypadków:

| Niedostępny zmysł | Wymagane zachowanie dostępności |
| ----------------- | ----------------------------------------------------------------- |
| Wzrok             | System musi pozostawać rozsądnie używalny przez dźwięk i dotyk. |
| Dźwięk            | System musi pozostawać rozsądnie używalny przez wzrok i dotyk. |
| Dotyk             | System musi pozostawać rozsądnie używalny przez wzrok i dźwięk. |

System nie musi zapewniać identycznych experiences przez każdą sensory path. Doświadczenie non-visual może być wolniejsze niż visual. Doświadczenie sound-free może wymagać napisów, visual indicators lub innych substitutions. Doświadczenie touch-free może wymagać alternate controls, voice interaction, keyboard navigation, pointer navigation lub innych non-touch methods.

Liczy się to, czy essential functionality pozostaje accessible, understandable i operable bez wymagania niedostępnego zmysłu.

## Essential Functionality

W Accessibility Verification **essential functionality** oznacza części systemu, których użytkownik rozsądnie potrzebuje, aby system rozumieć, nawigować, konfigurować i obsługiwać.

Essential functionality może obejmować:

* primary navigation
* core workflows
* required controls
* ważne ostrzeżenia
* ważne błędy
* wymagane confirmation messages
* dostęp do konta lub sesji
* settings and preferences
* language or accessibility configuration
* essential instructions
* user-facing status information
* każdą interakcję wymaganą do normalnego użycia

System może nadal być within spec, jeśli funkcje dekoracyjne, redundantne, opcjonalne lub nonessential nie są jednakowo dostępne przez każdą sensory path. Użytkownik musi jednak nadal móc używać essential system bez blokady spowodowanej brakującym zmysłem.

## Niedostępny wzrok

Gdy wzrok jest niedostępny, system powinien pozostawać rozsądnie używalny przez dźwięk i dotyk.

Może to obejmować spoken output, strukturę compatible ze screen readerem, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions lub inną rozsądną non-visual method przekazywania essential information.

System nie powinien polegać wyłącznie na visual position, color, shape, animation, icons lub layout, gdy ta informacja jest wymagana do rozumienia albo obsługi essential functionality.

## Niedostępny dźwięk

Gdy dźwięk jest niedostępny, system powinien pozostawać rozsądnie używalny przez wzrok i dotyk.

Może to obejmować captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback lub inną rozsądną non-auditory method przekazywania essential information.

System nie powinien polegać wyłącznie na sound effects, spoken instructions, alerts, alarms, music cues lub audio-only prompts, gdy ta informacja jest wymagana do rozumienia albo obsługi essential functionality.

## Niedostępny dotyk

Gdy dotyk jest niedostępny, system powinien pozostawać rozsądnie używalny przez wzrok i dźwięk.

Może to obejmować voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation lub inną rozsądną metodę, która nie wymaga touch-based interaction ani tactile perception.

System nie powinien polegać wyłącznie na touch gestures, haptic feedback, physical texture, vibration, force, pressure lub touch-only controls, gdy te interakcje są wymagane do rozumienia albo obsługi essential functionality.

## Dodatkowe domeny sensoryczne

CatalystUI rozpoznaje także **smak** i **węch** jako sensory domains. Te domeny mogą być brane pod uwagę podczas accessibility review, gdy system używa ich w znaczący sposób.

Smak i węch są **inclusive** dla verification, co oznacza, że mogą wzmacniać albo wspierać accessibility review, gdy zapewniają meaningful alternate access lub dodatkowy kontekst.

Smak i węch nie są obecnie **exclusive** dla failure, co oznacza, że system nie oblewa Accessibility Verification tylko dlatego, że nie zapewnia taste-based lub smell-based interaction.

CatalystUI Accessibility Verification dotyczy przede wszystkim tego, czy system pozostaje rozsądnie używalny, gdy wzrok, dźwięk albo dotyk jest indywidualnie niedostępny.

## Co oznacza „Within Spec”

Gdy system jest uznany za **within spec**, oznacza to, że CatalystUI Team ręcznie sprawdził system i uznał za rozsądne stwierdzić, że spełnia accessibility requirements opisane przez tę verification category.

Nie wymaga to jednego sztywnego implementation pattern. System może spełniać accessibility requirements przez native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration albo inny stable mechanism właściwy dla systemu.

Weryfikacja dotyczy praktycznej możliwości dostępu użytkowników do essential system, gdy jeden primary sense jest niedostępny, a nie tego, czy system używa jednej konkretnej accessibility architecture.

## Czego weryfikacja nie oznacza

CatalystUI Verified for Accessibility nie gwarantuje, że każda możliwa disability, device, assistive technology, medical condition, legal requirement, regional standard lub specialized use case została w pełni sprawdzona.

Nie weryfikuje też automatycznie internationalization, translation quality, typography, localization, regional compliance ani general design quality, chyba że te kwestie są objęte reviewed accessibility scope.

System może być rozsądnie accessible według modelu dostępności CatalystUI i nadal wymagać osobnego przeglądu pod kątem legal compliance, platform certification, specialized assistive technology support lub innych accessibility standards.

## Dlaczego ta weryfikacja istnieje

User interface odnosi sukces tylko wtedy, gdy użytkownicy faktycznie mogą z niego korzystać.

Wiele systemów traktuje accessibility jako dopisek, checklistę albo wąski technical requirement, zamiast jako fundamentalną część human-computer interaction. CatalystUI przyjmuje prostsze i bardziej bezpośrednie podejście: jeśli system zależy od ludzkiej percepcji, powinien zachować essential meaning, gdy jedna primary sensory path jest niedostępna.

Accessibility Verification istnieje, aby identyfikować systemy, które traktują tę odpowiedzialność poważnie. Uznaje systemy, które zapewniają meaningful alternate access, zachowują essential functionality i nie zamykają użytkowników za jednym wymaganym zmysłem.

## Zakres weryfikacji

CatalystUI Verification for Accessibility dotyczy reviewed system, service, framework, application, library lub implementation w stanie, w jakim istniał w chwili wydania verification.

Zweryfikowany system zapewnia reasonable accessibility dla swojej essential functionality w reviewed conditions. Nie gwarantuje to, że każda przyszła page, feature, release, plugin, extension, third-party integration, device lub platform-specific version automatycznie będzie within spec.

Oddzielne products, modules, services, major revisions lub platform-specific builds mogą wymagać własnego review zależnie od requested verification category.

## Ważność weryfikacji

CatalystUI Verification stosuje się tylko do reviewed state systemu w chwili wydania verification.

System może zachować verification przy późniejszych updates, o ile zachowuje verified accessibility foundation. Minor wording changes, visual refinements, performance improvements i ordinary content updates nie unieważniają automatycznie verification.

Nowy review może być wymagany, jeśli system usuwa alternate access paths, psuje assistive-technology support, znacząco zmienia essential navigation, usuwa wymagane accessibility settings albo zmienia interaction behavior w sposób wpływający na verified accessibility foundation.

Innymi słowy, poprawianie accessibility zwykle jest w porządku. Zepsucie verified access model może wymagać review.

## Zweryfikowane systemy

Znane systemy zweryfikowane pod kątem dostępności są wymienione osobno na odpowiedniej stronie CatalystUI Verified.
