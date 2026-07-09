<!-- Questa traduzione è stata generata da ChatGPT e deve essere revisionata da un traduttore umano. -->

<!-- Rimuovere queste righe in una pull request dopo che la traduzione è stata verificata. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Benvenuto nella documentazione di CatalystUI Verification per l’accessibilità.

**CatalystUI Verified for Accessibility** indica che un service, framework, application, library o system è stato esaminato dal CatalystUI Team ed è stato ritenuto ragionevolmente utilizzabile quando uno dei tre sensi primari coinvolti nell’interazione con l’interfaccia utente non è disponibile singolarmente.

Per questa verification, CatalystUI identifica i tre sensi primari di accessibilità come **sight**, **sound** e **touch**. Un system verificato deve preservare un accesso ragionevole alla sua essential functionality quando uno qualsiasi di questi sensi non è disponibile, facendo affidamento sui sensory domains rimanenti.

In termini più semplici, questa verification chiede se un user può ancora comprendere, navigare e utilizzare in modo significativo le parti essential di un system se non può fare affidamento su sight, sound o touch singolarmente.

## Scopo

L’accessibilità è importante perché una user interface non dovrebbe dipendere interamente da un solo sensory pathway quando lo stesso essential meaning può ragionevolmente essere comunicato attraverso un altro.

CatalystUI è progettato attorno al movimento fedele dei dati tra systems e human perception. Se un’informazione importante è solo visibile, solo udibile o disponibile solo tramite touch, allora il system può diventare inutilizzabile per gli user che non possono fare affidamento su quel senso. Accessibility Verification esiste per identificare systems che preservano l’accesso consentendo alle informazioni e alle interazioni essential di continuare attraverso percorsi sensoriali alternativi.

L’obiettivo non è richiedere ogni possibile metodo di interazione, ogni assistive technology o ogni accommodation specialistica. L’obiettivo è determinare se l’essential system resta meaningfully usable quando sight, sound o touch non è disponibile singolarmente.

## Cosa significa Verification

Un system diventa **CatalystUI Verified for Accessibility** quando viene esaminato rispetto ai requirements elencati in questa sezione e risulta within spec.

Per essere verificato, un system deve restare ragionevolmente utilizzabile in ciascuno dei seguenti casi:

| Unavailable Sense | Required Accessibility Behavior |
| ----------------- | ----------------------------------------------------------------- |
| Sight             | Il system deve restare ragionevolmente utilizzabile tramite sound e touch. |
| Sound             | Il system deve restare ragionevolmente utilizzabile tramite sight e touch. |
| Touch             | Il system deve restare ragionevolmente utilizzabile tramite sight e sound. |

Un system non deve fornire esperienze identiche in ogni sensory path. Un’esperienza non visuale può essere più lenta di una visuale. Un’esperienza senza sound può richiedere captions, visual indicators o altre sostituzioni. Un’esperienza senza touch può richiedere alternate controls, voice interaction, keyboard navigation, pointer navigation o altri metodi non-touch.

Ciò che conta è se la essential functionality resta accessible, understandable e operable senza richiedere il senso non disponibile.

## Essential Functionality

Per Accessibility Verification, **essential functionality** indica le parti di un system di cui un user ha ragionevolmente bisogno per comprendere, navigare, configurare e utilizzare il system.

Essential functionality può includere:

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
* qualsiasi interaction richiesta per l’uso normale

Un system può comunque essere within spec se funzionalità decorative, redundant, optional o nonessential non sono ugualmente disponibili attraverso ogni sensory path. Tuttavia, l’user deve comunque poter usare l’essential system senza essere bloccato dal senso mancante.

## Sight Unavailable

Quando sight non è disponibile, il system dovrebbe restare ragionevolmente utilizzabile tramite sound e touch.

Questo può includere spoken output, screen-reader-compatible structure, meaningful focus order, tactile controls, keyboard access, haptic confirmation, audio descriptions o un altro metodo non visuale ragionevole per comunicare essential information.

Un system non dovrebbe dipendere esclusivamente da visual position, color, shape, animation, icons o layout quando tali informazioni sono richieste per comprendere o utilizzare essential functionality.

## Sound Unavailable

Quando sound non è disponibile, il system dovrebbe restare ragionevolmente utilizzabile tramite sight e touch.

Questo può includere captions, transcripts, visual alerts, text equivalents, progress indicators, visible status messages, haptic feedback o un altro metodo non uditivo ragionevole per comunicare essential information.

Un system non dovrebbe dipendere esclusivamente da sound effects, spoken instructions, alerts, alarms, music cues o audio-only prompts quando tali informazioni sono richieste per comprendere o utilizzare essential functionality.

## Touch Unavailable

Quando touch non è disponibile, il system dovrebbe restare ragionevolmente utilizzabile tramite sight e sound.

Questo può includere voice control, keyboard navigation, pointer alternatives, remote controls, gaze-compatible interaction, switch-compatible interaction, spoken prompts, visual confirmation o un altro metodo ragionevole che non richieda touch-based interaction o tactile perception.

Un system non dovrebbe dipendere esclusivamente da touch gestures, haptic feedback, physical texture, vibration, force, pressure o touch-only controls quando tali interaction sono richieste per comprendere o utilizzare essential functionality.

## Additional Sensory Domains

CatalystUI riconosce anche **taste** e **smell** come sensory domains. Questi domains possono essere considerati durante l’accessibility review quando sono usati in modo significativo dal system.

Taste e smell sono **inclusive** per la verification, cioè possono rafforzare o supportare un’accessibility review quando forniscono meaningful alternate access o additional context.

Taste e smell attualmente non sono **exclusive** per il failure, cioè un system non fallisce Accessibility Verification semplicemente perché non fornisce interaction basate su taste o smell.

CatalystUI Accessibility Verification riguarda principalmente se il system resta ragionevolmente utilizzabile quando sight, sound o touch non è disponibile singolarmente.

## Cosa significa “Within Spec”

Quando un system è considerato **within spec**, significa che il CatalystUI Team ha esaminato manualmente il system e ha ritenuto ragionevole concludere che soddisfi gli accessibility requirements descritti da questa verification category.

Questo non richiede un unico rigid implementation pattern. Un system può soddisfare gli accessibility requirements tramite native platform accessibility APIs, semantic structure, alternate input methods, alternate output methods, assistive-technology support, built-in accessibility settings, device-level integration o un altro stable mechanism appropriato al system.

Verification riguarda la capacità pratica degli user di accedere all’essential system quando un primary sense non è disponibile, non il fatto che il system usi una specifica accessibility architecture.

## Cosa non significa Verification

CatalystUI Verified for Accessibility non garantisce che ogni possibile disability, device, assistive technology, medical condition, legal requirement, regional standard o specialized use case sia stato completamente esaminato.

Inoltre non verifica automaticamente internationalization, translation quality, typography, localization, regional compliance o general design quality, salvo che tali aspetti siano inclusi nel reviewed accessibility scope.

Un system può essere ragionevolmente accessible secondo il modello di accessibilità CatalystUI e richiedere comunque una review separata per legal compliance, platform certification, specialized assistive technology support o altri accessibility standards.

## Perché esiste questa Verification

Una user interface ha successo solo quando gli user possono davvero usarla.

Molti systems trattano accessibility come un afterthought, una checklist o un narrow technical requirement invece che come una parte fondamentale della human-computer interaction. CatalystUI adotta un approccio più semplice e diretto: se un system dipende dalla human perception, allora dovrebbe preservare l’essential meaning quando un primary sensory path non è disponibile.

Accessibility Verification esiste per identificare systems che prendono sul serio questa responsabilità. Riconosce systems che forniscono meaningful alternate access, preservano essential functionality ed evitano di intrappolare gli user dietro un solo senso richiesto.

## Verification Scope

CatalystUI Verification for Accessibility si applica al reviewed system, service, framework, application, library o implementation così com’era al momento in cui la verification è stata emessa.

Un system verificato fornisce accessibilità ragionevole per la sua essential functionality nelle condizioni esaminate. Non garantisce che ogni future page, feature, release, plugin, extension, third-party integration, device o platform-specific version sia automaticamente within spec.

Prodotti, modules, services, major revisions o platform-specific builds separati possono richiedere la propria review in base alla verification category richiesta.

## Verification Validity

CatalystUI Verification si applica solo allo stato esaminato del system nel momento in cui viene emessa.

Un system può conservare la verification negli update successivi finché preserva la verified accessibility foundation. Minor wording changes, visual refinements, performance improvements e ordinary content updates non invalidano automaticamente la verification.

Una nuova review può essere richiesta se un system rimuove alternate access paths, rompe assistive-technology support, cambia sostanzialmente essential navigation, rimuove required accessibility settings o cambia interaction behavior in modo da influire sulla verified accessibility foundation.

In altre parole, migliorare accessibility di solito va bene. Rompere il verified access model può richiedere review.

## Verified Systems

I systems noti verificati per accessibility sono elencati separatamente nella pagina CatalystUI Verified appropriata.
