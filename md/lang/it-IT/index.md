<!-- Questa traduzione è stata generata da ChatGPT e deve essere rivista da un traduttore umano. -->

<!-- Rimuovi queste righe in una pull request dopo che la traduzione è stata verificata. -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified for Internationalization

Benvenuto nella documentazione CatalystUI Verification per l’internazionalizzazione.

**CatalystUI Verified for Internationalization** indica che un sistema, servizio, framework, applicazione o implementazione è stato esaminato dal Team CatalystUI ed è risultato in grado di fornire supporto multilingue sufficiente per l’insieme di lingue di internazionalizzazione richiesto da CatalystUI.

Questa verifica non è una classifica generale della qualità della traduzione, dello stile di scrittura, della profondità della localizzazione o dell’adattamento culturale. Identifica invece se il sistema esaminato fornisce una base stabile e pratica perché gli utenti possano accedere alle sue funzionalità essenziali nelle lingue supportate richieste.

In termini più semplici, questa verifica chiede se gli utenti possano usare in modo significativo le parti essenziali di un sistema nelle lingue richieste, e se venga loro dato un modo ragionevole per scegliere la lingua che comprendono.

<a id="purpose"></a>
## Scopo

L’internazionalizzazione è importante perché un sistema non può essere considerato ampiamente accessibile se il suo significato essenziale è bloccato dietro una sola lingua.

CatalystUI è progettato attorno alla chiarezza, alla coerenza e alla rappresentazione fedele dell’interazione uomo-computer. La lingua fa parte di questa interazione. Se un utente non può comprendere etichette, istruzioni, avvisi, controlli, impostazioni o contenuti essenziali di un sistema, allora il sistema non ha comunicato chiaramente, anche se la funzionalità sottostante tecnicamente funziona.

Internationalization Verification esiste per identificare i sistemi che forniscono sufficiente supporto tradotto agli utenti nell’intero insieme di lingue richiesto da CatalystUI. L’obiettivo non è pretendere la traduzione perfetta di ogni parola opzionale, messaggio nascosto per sviluppatori o pagina non essenziale. L’obiettivo è determinare se le parti essenziali del sistema possano essere comprese e utilizzate dalle persone in ogni lingua richiesta.

<a id="what-verification-means"></a>
## Cosa significa la verifica

Un sistema diventa **CatalystUI Verified for Internationalization** quando viene esaminato rispetto ai requisiti elencati in questa sezione e viene ritenuto within spec.

Per essere verificato, un sistema deve fornire traduzioni per più del 75% delle parti essenziali rivolte all’utente in ogni lingua richiesta. Deve inoltre fornire un meccanismo ragionevole per consentire all’utente finale di cambiare la lingua attiva.

Un sistema non deve tradurre ogni identificatore interno, dettaglio di implementazione rivolto agli sviluppatori, stringa di debug, pagina di marketing opzionale o testo di supporto non essenziale. Tuttavia, le parti rivolte all’utente necessarie per comprendere e utilizzare il sistema essenziale devono essere disponibili in ogni lingua richiesta.

<a id="required-languages"></a>
## Lingue richieste

L’attuale insieme di lingue di internazionalizzazione CatalystUI è stato selezionato attraverso una revisione pratica delle lingue comunemente necessarie nei contesti tecnologici, includendo la portata globale dei parlanti, l’uso comune online, le aspettative verso software multilingue e le ampie esigenze di accessibilità regionale.

Questo insieme di lingue non intende rappresentare ogni lingua, ogni dialetto o ogni variante regionale. Stabilisce invece una base pratica per i sistemi che cercano ampia usabilità internazionale in molti dei gruppi linguistici più comuni nel mondo della tecnologia.

L’attuale insieme di lingue di internazionalizzazione CatalystUI include le seguenti locale:

| Locale    | Lingua                  |
| --------- | ----------------------- |
| `ar-SA`   | Arabo (Arabia Saudita)  |
| `bn-BD`   | Bengalese (Bangladesh)  |
| `de-DE`   | Tedesco (Germania)      |
| `en-GB`   | Inglese (Regno Unito)   |
| `en-IN`   | Inglese (India)         |
| `en-US`   | Inglese (Stati Uniti)   |
| `es-ES`   | Spagnolo (Spagna)       |
| `es-MX`   | Spagnolo (Messico)      |
| `fa-IR`   | Persiano (Iran)         |
| `fr-FR`   | Francese (Francia)      |
| `hi-IN`   | Hindi (India)           |
| `id-ID`   | Indonesiano (Indonesia) |
| `it-IT`   | Italiano (Italia)       |
| `ja-JP`   | Giapponese (Giappone)   |
| `ko-KR`   | Coreano (Corea del Sud) |
| `nl-NL`   | Olandese (Paesi Bassi)  |
| `pl-PL`   | Polacco (Polonia)       |
| `pt-BR`   | Portoghese (Brasile)    |
| `ru-RU`   | Russo (Russia)          |
| `tl-PH`   | Tagalog (Filippine)     |
| `tr-TR`   | Turco (Turchia)         |
| `uk-UA`   | Ucraino (Ucraina)       |
| `ur-PK`   | Urdu (Pakistan)         |
| `vi-VN`   | Vietnamita (Vietnam)    |
| `zh-CN`   | Cinese (Cina)           |
| `zh-Hans` | Cinese (semplificato)   |

Un sistema deve fornire una copertura di traduzione essenziale sufficiente per ogni gruppo linguistico elencato per essere considerato within spec.

Tuttavia, le varianti regionali possono essere esaminate con ragionevole flessibilità quando le differenze tra varianti sono minori e non influenzano materialmente la capacità dell’utente di comprendere o utilizzare il sistema. Per esempio, un sistema può ancora essere idoneo alla verifica se fornisce una sola solida traduzione inglese ma non traduce separatamente ogni variante regionale dell’inglese, purché significato essenziale, navigazione, istruzioni, avvisi e controlli rimangano chiari per gli utenti delle varianti mancanti.

Questa flessibilità non si applica quando una variante mancante creerebbe confusione significativa, ometterebbe terminologia regionale importante, interromperebbe un comportamento sensibile alla locale, o impedirebbe agli utenti di comprendere parti essenziali del sistema.

<a id="essential-translation-coverage"></a>
## Copertura di traduzione essenziale

Per Internationalization Verification, **copertura di traduzione essenziale** indica le parti di un sistema di cui un utente ha ragionevolmente bisogno per comprendere, navigare, configurare e utilizzare il sistema.

Le parti essenziali possono includere:

* navigazione principale
* schermate e viste principali
* impostazioni e preferenze
* etichette rivolte all’utente
* controlli rivolti all’utente
* istruzioni richieste
* avvisi importanti
* errori importanti
* prompt essenziali
* messaggi di conferma richiesti
* controlli di selezione della lingua
* flussi di lavoro principali necessari per l’uso normale

Un sistema è considerato conforme al requisito di copertura della traduzione quando più del 75% del suo contenuto essenziale rivolto all’utente è disponibile in ogni lingua richiesta.

Questa soglia esiste perché il lavoro di internazionalizzazione può essere ampio, continuo e dipendente dal contesto. Un sistema può ancora essere within spec anche se alcuni contenuti non essenziali o a priorità inferiore rimangono non tradotti. Tuttavia, l’esperienza essenziale deve essere significativamente disponibile in ogni lingua richiesta.

<a id="language-selection"></a>
## Selezione della lingua

Un sistema verificato deve fornire un modo ragionevole perché l’utente finale cambi la lingua attiva.

Il meccanismo di selezione della lingua dovrebbe essere facile da trovare, comprensibile e disponibile senza richiedere conoscenze tecniche. Gli utenti non dovrebbero dover modificare file di configurazione, cambiare codice sorgente, installare strumenti per sviluppatori o affidarsi a comportamenti non documentati solo per cambiare lingua.

Quando mostra le opzioni di lingua, il sistema dovrebbe identificare ogni lingua in un modo comprensibile sia agli utenti che parlano quella lingua sia agli utenti che stanno usando un’altra lingua selezionata.

Per esempio, un’opzione di lingua può essere mostrata così:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

La formattazione esatta può variare, ma l’intento dovrebbe rimanere lo stesso: gli utenti dovrebbero poter riconoscere la propria lingua, comprendere quando possibile il nome della lingua attualmente mostrato e identificare il codice locale associato.

<a id="what-within-spec-means"></a>
## Cosa significa “Within Spec”

Quando un sistema è considerato **within spec**, significa che il Team CatalystUI ha esaminato manualmente il sistema e ha ritenuto ragionevole concludere che soddisfi i requisiti di internazionalizzazione descritti da questa categoria di verifica.

Ciò non richiede un unico modello di implementazione rigido. Un sistema può soddisfare il requisito attraverso file di risorse, tabelle di traduzione, routing consapevole della locale, asset linguistici compilati, traduzioni supportate da database, language pack runtime o un altro meccanismo stabile appropriato al sistema.

La verifica riguarda la capacità pratica degli utenti di accedere al sistema essenziale nelle lingue richieste, non il fatto che il sistema usi una specifica architettura di traduzione.

<a id="what-verification-does-not-mean"></a>
## Cosa non significa la verifica

CatalystUI Verified for Internationalization non garantisce che ogni traduzione sia perfetta, letteraria, idiomatica, culturalmente completa o legalmente sufficiente per ogni regione.

Inoltre non verifica automaticamente accessibilità, tipografia, layout da destra a sinistra, formattazione specifica della locale, formattazione delle valute, formattazione delle date, conformità legale o requisiti commerciali regionali, salvo quando tali aspetti sono inclusi nell’ambito di internazionalizzazione esaminato.

Un sistema può fornire una forte copertura di traduzione e richiedere comunque una revisione separata per accessibilità, qualità della localizzazione, conformità regionale o altre aree specializzate.

<a id="why-this-verification-exists"></a>
## Perché esiste questa verifica

Una user interface è utile solo quando l’utente può comprendere ciò che comunica.

Molti sistemi dichiarano supporto linguistico mentre traducono solo una piccola parte dell’esperienza, nascondono la selezione della lingua, omettono messaggi importanti o lasciano flussi di lavoro essenziali parzialmente non tradotti. Questo crea confusione e impedisce agli utenti di fidarsi del sistema.

Internationalization Verification esiste per stabilire uno standard più chiaro. Identifica i sistemi che compiono uno sforzo serio e pratico per supportare gli utenti nell’insieme di lingue richiesto da CatalystUI e che forniscono un modo ragionevole perché gli utenti scelgano la lingua di cui hanno bisogno.

<a id="verification-scope"></a>
## Ambito della verifica

CatalystUI Verification for Internationalization si applica al sistema, servizio, framework, applicazione o implementazione esaminato come esisteva al momento dell’emissione della verifica.

Un sistema verificato fornisce una copertura di traduzione essenziale sufficiente per le lingue richieste. Non garantisce che ogni futura pagina, funzionalità, release, plugin, estensione o integrazione di terze parti sia automaticamente within spec.

Prodotti, moduli, servizi, language pack o revisioni maggiori separati possono richiedere una propria revisione a seconda della categoria di verifica richiesta.

<a id="verification-validity"></a>
## Validità della verifica

CatalystUI Verification si applica solo allo stato esaminato del sistema al momento dell’emissione della verifica.

Un sistema può mantenere la propria verifica negli aggiornamenti successivi finché preserva la base di internazionalizzazione verificata. Piccoli cambiamenti di formulazione, traduzioni aggiunte e normali aggiornamenti di contenuto non invalidano automaticamente la verifica.

Una nuova revisione può essere richiesta se un sistema rimuove il supporto linguistico richiesto, rompe la selezione della lingua, riduce sostanzialmente la copertura di traduzione essenziale o cambia la propria architettura di internazionalizzazione in un modo che influisce sul comportamento verificato.

In altre parole, migliorare il supporto di traduzione di solito va bene. Rompere la base multilingue verificata può richiedere una revisione.

<a id="verified-systems"></a>
## Sistemi verificati

I sistemi noti verificati per l’internazionalizzazione sono elencati separatamente nella pagina CatalystUI Verified appropriata.
