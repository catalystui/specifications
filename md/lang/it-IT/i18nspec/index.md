<!-- Questa traduzione è stata generata da ChatGPT e deve essere rivista da un traduttore umano. -->

<!-- Rimuovi queste righe in una pull request dopo che la traduzione è stata verificata. -->

# I18NSPEC

<br/>

> **Specifica di internazionalizzazione**<br/>
> Revisione 1<br/>
> 8 luglio 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Le definizioni, i requisiti e i concetti presentati qui descrivono il supporto pratico all’internazionalizzazione e possono essere riformulati liberamente.

<a id="introduction"></a>
## Introduzione

La **Specifica di internazionalizzazione (I18NSPEC)** stabilisce i concetti fondamentali, la terminologia e i requisiti usati per valutare il supporto multilingue nell’ecosistema CatalystUI. Il suo scopo è fornire uno standard chiaro per determinare se un sistema, servizio, framework, applicazione o implementazione fornisca supporto linguistico sufficiente per essere considerato within spec.

L’internazionalizzazione è importante perché una user interface non può comunicare chiaramente se il suo significato essenziale è disponibile in una sola lingua. Un sistema può essere tecnicamente funzionante, ma se gli utenti non possono comprenderne etichette, istruzioni, controlli, impostazioni, avvisi, errori o flussi di lavoro principali, allora il sistema non ha fornito un’interfaccia significativa per quegli utenti.

Questa specifica non tenta di misurare la qualità perfetta della traduzione, lo stile letterario, l’adattamento culturale, la conformità legale o la localizzazione regionale completa. Definisce invece la base multilingue minima necessaria perché gli utenti possano accedere e utilizzare in modo significativo le parti essenziali di un sistema nell’insieme di locale richiesto da CatalystUI.

In termini più semplici, I18NSPEC pone tre domande principali:

1. Gli utenti possono accedere alle parti essenziali del sistema in ogni lingua richiesta?
2. Gli utenti possono selezionare ragionevolmente la lingua che comprendono?
3. Il sistema preserva abbastanza significato tra le lingue da rimanere utilizzabile?

> [!IMPORTANT]
>
> I18NSPEC definisce i requisiti di internazionalizzazione per la verifica. Non è una specifica separata per ogni lingua. Ogni locale richiesta viene controllata rispetto alla stessa specifica.

<a id="table-of-contents"></a>
## Indice

* [I18NSPEC](#i18nspec)

  * [Introduzione](#introduction)
  * [Indice](#table-of-contents)
  * [Conformità](#conformance)
  * [Insieme di locale richiesto](#required-locale-set)
  * [Contenuto rivolto all’utente](#user-facing-content)

    * [Contenuto rivolto all’utente](#user-facing-content-1)
    * [Contenuto essenziale rivolto all’utente](#essential-user-facing-content)
    * [Contenuto critico rivolto all’utente](#critical-user-facing-content)
    * [Contenuto non essenziale](#nonessential-content)
  * [Copertura della traduzione](#translation-coverage)

    * [Copertura della traduzione essenziale](#essential-translation-coverage)
    * [Requisito di copertura](#coverage-requirement)
    * [Requisito del contenuto critico](#critical-content-requirement)
  * [Selezione della lingua](#language-selection)

    * [Locale attiva](#active-locale)
    * [Locale predefinita](#default-locale)
    * [Meccanismo di selezione della lingua](#language-selection-mechanism)
    * [Etichette delle opzioni di lingua](#language-option-labels)
  * [Fallback ed equivalenza delle locale](#fallbacks-and-locale-equivalence)

    * [Locale di fallback](#fallback-locale)
    * [Comportamento di fallback](#fallback-behavior)
    * [Equivalenza delle locale](#locale-equivalence)
  * [Requisiti di implementazione](#implementation-requirements)

    * [Meccanismo di traduzione stabile](#stable-translation-mechanism)
    * [Preservazione del significato](#preservation-of-meaning)
    * [Lingue sensibili alla direzione](#direction-sensitive-languages)
    * [Valori sensibili alla locale](#locale-sensitive-values)
  * [Verifica](#verification)

    * [Within Spec](#within-spec)
    * [Avvisi](#warnings)
    * [Fallimenti](#failures)
    * [Validità della verifica](#verification-validity)

<a id="conformance"></a>
## Conformità

Un sistema è considerato conforme a I18NSPEC quando soddisfa i requisiti definiti da questo documento per ogni locale nell’insieme di locale richiesto.

Un sistema conforme deve:

1. Supportare ogni locale nell’insieme di locale richiesto.
2. Fornire contenuto tradotto per più del 75% del contenuto essenziale rivolto all’utente in ogni locale richiesta.
3. Fornire contenuto tradotto per tutto il contenuto critico rivolto all’utente in ogni locale richiesta.
4. Fornire un meccanismo ragionevole per l’utente finale per selezionare la locale attiva.
5. Usare un meccanismo di traduzione stabile appropriato al sistema.
6. Preservare il significato essenziale del contenuto tradotto rivolto all’utente.
7. Evitare di fare affidamento su contenuto di fallback per rivendicare copertura della traduzione, tranne quando l’equivalenza delle locale è accettata durante la revisione.

Un sistema non deve usare uno specifico modello di implementazione per essere conforme a questa specifica. Può usare file di risorse, tabelle di traduzione, routing consapevole della locale, risorse linguistiche compilate, pagine localizzate statiche, language pack runtime, traduzioni supportate da database o un altro meccanismo stabile appropriato al sistema.

La verifica riguarda l’accesso pratico dell’utente e il significato essenziale, non una rigida architettura tecnica.

<a id="required-locale-set"></a>
## Insieme di locale richiesto

L’insieme di locale richiesto definisce le lingue e le varianti regionali che devono essere esaminate per CatalystUI Internationalization Verification.

L’attuale insieme di locale richiesto include le seguenti locale:

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

Un sistema deve fornire supporto di traduzione essenziale sufficiente per ogni locale elencata per essere considerato within spec.

L’insieme di locale richiesto non intende rappresentare ogni lingua, dialetto, regione o scrittura. Stabilisce invece una base pratica per un’ampia usabilità internazionale in molti gruppi linguistici comuni nei contesti tecnologici.

<a id="user-facing-content"></a>
## Contenuto rivolto all’utente

<a id="user-facing-content-1"></a>
### Contenuto rivolto all’utente

Il contenuto rivolto all’utente è qualsiasi contenuto destinato a essere percepito, letto, ascoltato, selezionato, compreso o usato come base per un’azione da parte di un utente finale.

Il contenuto rivolto all’utente può includere:

* navigazione
* etichette
* pulsanti
* menu
* controlli
* intestazioni
* finestre di dialogo
* impostazioni
* istruzioni
* prompt
* avvisi
* errori
* conferme
* messaggi di stato
* testo di onboarding
* testo di aiuto richiesto
* controlli di selezione della lingua
* contenuto dei flussi di lavoro principali

Il contenuto rivolto all’utente non deve essere necessariamente visivo. Può anche includere contenuto uditivo, tattile, simbolico o multisensoriale quando quel contenuto comunica significato all’utente.

<a id="essential-user-facing-content"></a>
### Contenuto essenziale rivolto all’utente

Il contenuto essenziale rivolto all’utente è contenuto rivolto all’utente di cui un utente ha ragionevolmente bisogno per comprendere, navigare, configurare o utilizzare il comportamento essenziale di un sistema.

Il contenuto essenziale rivolto all’utente può includere:

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

Un sistema non deve tradurre ogni pagina opzionale, messaggio nascosto, etichetta interna o testo non essenziale per soddisfare I18NSPEC. Tuttavia, il contenuto richiesto per il normale uso essenziale deve essere tradotto secondo i requisiti di questa specifica.

<a id="critical-user-facing-content"></a>
### Contenuto critico rivolto all’utente

Il contenuto critico rivolto all’utente è contenuto essenziale rivolto all’utente in cui un fraintendimento può impedire l’uso significativo, creare un errore serio o portare l’utente a prendere una decisione importante senza comprenderne la conseguenza.

Il contenuto critico rivolto all’utente può includere:

* controlli di selezione della lingua
* avvisi per azioni distruttive
* avvisi di eliminazione dell’account
* conferme di pagamento
* conferme di acquisto
* scelte sulla privacy
* avvisi di sicurezza
* prompt di consenso
* istruzioni di sicurezza richieste
* istruzioni di configurazione richieste
* messaggi di errore richiesti
* navigazione principale necessaria per raggiungere le impostazioni della lingua

Il contenuto critico rivolto all’utente deve essere tradotto per ogni locale richiesta.

La soglia del 75% di copertura della traduzione essenziale non deve essere usata per lasciare non tradotto il contenuto critico.

<a id="nonessential-content"></a>
### Contenuto non essenziale

Il contenuto non essenziale è contenuto che non è ragionevolmente richiesto perché un utente comprenda, navighi, configuri o utilizzi il comportamento essenziale di un sistema.

Il contenuto non essenziale può includere:

* identificatori interni
* nomi del codice sorgente
* stringhe solo di debug
* dettagli di implementazione rivolti agli sviluppatori
* testo diagnostico nascosto
* pagine di marketing opzionali
* pagine di supporto opzionali
* testo legale o commerciale non essenziale fuori dall’ambito esaminato
* contenuto di terze parti non controllato dal sistema esaminato

Il contenuto non essenziale può essere tradotto, ma non è richiesto per la conformità a I18NSPEC salvo quando diventa necessario per la comprensione o l’uso essenziale da parte dell’utente.

<a id="translation-coverage"></a>
## Copertura della traduzione

<a id="essential-translation-coverage"></a>
### Copertura della traduzione essenziale

La copertura della traduzione essenziale è la quantità di contenuto essenziale rivolto all’utente tradotta per una locale specifica.

La copertura dovrebbe essere valutata in base a unità significative di contenuto rivolto all’utente, non in base alla dimensione dei file, al numero di byte, al numero di righe, alla dimensione del repository o al numero di pagine.

Per esempio, un solo pulsante non tradotto che controlla un’azione essenziale può contare più di un grande paragrafo opzionale non tradotto che non influisce sull’uso ordinario.

La copertura della traduzione dovrebbe essere giudicata in base al fatto che l’utente possa comprendere e utilizzare in modo significativo il sistema essenziale nella locale esaminata.

<a id="coverage-requirement"></a>
### Requisito di copertura

Un sistema soddisfa il requisito di copertura della traduzione per una locale quando più del 75% del contenuto essenziale rivolto all’utente è tradotto per quella locale.

Un sistema soddisfa il requisito di copertura I18NSPEC quando raggiunge questa soglia per ogni locale nell’insieme di locale richiesto.

Nella revisione pratica, ciò può essere rappresentato così:

| Locale  | Copertura della traduzione essenziale | Risultato |
| ------- | ------------------------------------- | --------- |
| `en-US` | 100%                                  | Pass      |
| `es-ES` | 94%                                   | Pass      |
| `ar-SA` | 78%                                   | Pass      |
| `ja-JP` | 61%                                   | Fail      |

Una locale con copertura del 75% o inferiore non soddisfa il requisito di copertura.

Una locale con copertura superiore al 75% può comunque fallire se contenuto critico rivolto all’utente non è tradotto.

<a id="critical-content-requirement"></a>
### Requisito del contenuto critico

Tutto il contenuto critico rivolto all’utente deve essere tradotto per ogni locale richiesta.

Un sistema può fallire I18NSPEC anche quando soddisfa la soglia generale di copertura se uno o più elementi di contenuto critico rivolto all’utente sono mancanti, non tradotti, fuorvianti o non significativamente comprensibili.

Per esempio, un sistema non dovrebbe essere considerato within spec se l’interfaccia generale è tradotta ma l’avviso di eliminazione dell’account, la conferma di acquisto, l’avviso di sicurezza o il selettore della lingua restano non tradotti.

<a id="language-selection"></a>
## Selezione della lingua

<a id="active-locale"></a>
### Locale attiva

La locale attiva è la locale attualmente selezionata per l’esperienza dell’utente.

La locale attiva determina quale contenuto tradotto debba essere mostrato, fornito o altrimenti comunicato all’utente.

<a id="default-locale"></a>
### Locale predefinita

La locale predefinita è la locale usata quando l’utente non ha selezionato una locale attiva o quando non è disponibile alcuna preferenza dell’utente.

Un sistema deve definire una locale predefinita.

La locale predefinita dovrebbe essere documentata o ragionevolmente deducibile dal revisore.

<a id="language-selection-mechanism"></a>
### Meccanismo di selezione della lingua

Un sistema conforme deve fornire un modo ragionevole perché l’utente finale cambi la locale attiva.

Il meccanismo di selezione della lingua deve essere disponibile senza richiedere all’utente di:

* modificare il codice sorgente
* usare strumenti per sviluppatori
* modificare file di configurazione non documentati
* installare patch non ufficiali
* affidarsi a comportamento nascosto
* contattare il supporto per cambiamenti ordinari della lingua

Un meccanismo di selezione della lingua può essere fornito tramite:

* impostazioni dell’applicazione
* preferenze dell’account
* un selettore della lingua
* un prompt di avvio
* impostazioni del browser
* impostazioni dell’operating system
* impostazioni del dispositivo
* un altro meccanismo appropriato accessibile all’utente finale

Il meccanismo non deve seguire uno specifico modello di progettazione. Deve consentire ragionevolmente all’utente di selezionare una lingua supportata.

<a id="language-option-labels"></a>
### Etichette delle opzioni di lingua

Quando mostra le opzioni di lingua, un sistema dovrebbe identificare ogni lingua in un modo comprensibile agli utenti che parlano quella lingua.

Un’opzione di lingua può includere:

* il nome della lingua in quella lingua
* il nome della lingua nella lingua attualmente attiva
* il codice locale
* un’etichetta regionale
* un’etichetta di scrittura

Per esempio:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

La formattazione esatta può variare.

L’intento è che gli utenti possano riconoscere la propria lingua, comprendere quando possibile il nome della lingua attualmente mostrato e identificare il codice locale associato.

<a id="fallbacks-and-locale-equivalence"></a>
## Fallback ed equivalenza delle locale

<a id="fallback-locale"></a>
### Locale di fallback

Una locale di fallback è una locale usata quando il contenuto tradotto non è disponibile per la locale attiva.

Le locale di fallback possono aiutare a preservare l’usabilità, ma il contenuto di fallback non è automaticamente considerato contenuto tradotto per la locale attiva.

Per esempio, se un sistema è impostato su `es-MX` ma mostra testo `en-US` perché manca la traduzione spagnola, quel testo inglese può essere utile come fallback, ma non dovrebbe essere conteggiato come copertura della traduzione spagnola.

<a id="fallback-behavior"></a>
### Comportamento di fallback

Un sistema conforme può usare comportamento di fallback quando il contenuto localizzato non è disponibile.

Il comportamento di fallback dovrebbe evitare output rotti, vuoti o fuorvianti.

Il comportamento di fallback non deve essere usato per rivendicare falsamente copertura della traduzione per una locale richiesta.

Un sistema può ricevere un avviso o un fallimento se il comportamento di fallback è eccessivo, confuso, non documentato o fa apparire non tradotto contenuto essenziale in una locale richiesta.

<a id="locale-equivalence"></a>
### Equivalenza delle locale

L’equivalenza delle locale si verifica quando una traduzione può servire ragionevolmente più di una locale senza impedire la comprensione o l’uso essenziale.

Per esempio, un sistema può usare una sola traduzione inglese per `en-US`, `en-GB` e `en-IN` se il significato essenziale rimane chiaro per gli utenti di ogni locale.

L’equivalenza delle locale può essere accettata durante la revisione quando le differenze regionali sono minori e non influenzano materialmente l’usabilità essenziale.

L’equivalenza delle locale non deve essere usata quando una locale mancante creerebbe confusione significativa, ometterebbe terminologia regionale importante, interromperebbe comportamento essenziale o impedirebbe agli utenti di comprendere il sistema.

Per esempio, un sistema non dovrebbe presumere che lingue non correlate siano equivalenti perché condividono una direzione di scrittura, una regione geografica, una famiglia di scritture o un’ampia categoria culturale.

L’equivalenza delle locale è un giudizio di revisione, non una regola automatica.

<a id="implementation-requirements"></a>
## Requisiti di implementazione

<a id="stable-translation-mechanism"></a>
### Meccanismo di traduzione stabile

Un sistema conforme deve usare un meccanismo di traduzione stabile appropriato al sistema esaminato.

Un meccanismo di traduzione stabile dovrebbe consentire al contenuto tradotto di essere mantenuto, aggiornato, revisionato ed esteso senza fare affidamento su comportamento fragile o non documentato.

Un meccanismo di traduzione stabile può includere:

* file di risorse
* tabelle di traduzione
* routing consapevole della locale
* asset linguistici compilati
* pagine localizzate statiche
* language pack runtime
* traduzioni supportate da database
* un’altra struttura di traduzione documentata

Un sistema dovrebbe evitare di inserire direttamente nel codice contenuto essenziale rivolto all’utente in un modo che impedisca il supporto di traduzione richiesto.

<a id="preservation-of-meaning"></a>
### Preservazione del significato

Una traduzione preserva il significato quando l’utente può ragionevolmente comprendere la stessa istruzione, etichetta, avviso, controllo, impostazione o flusso di lavoro essenziale degli utenti della lingua sorgente.

Una traduzione non deve essere identica parola per parola al contenuto sorgente.

Una traduzione può cambiare ordine delle parole, grammatica, struttura della frase, idioma, tono o formulazione quando necessario per comunicare lo stesso significato essenziale nella lingua di destinazione.

Una traduzione può fallire la revisione se è fuorviante, incompleta, priva di senso, corrotta da macchina o significativamente diversa dal contenuto sorgente in un modo che influisce sull’uso essenziale.

<a id="direction-sensitive-languages"></a>
### Lingue sensibili alla direzione

Alcune locale richieste usano comunemente direzione del testo da destra a sinistra.

Un sistema conforme non deve impedire al contenuto tradotto essenziale di essere letto, compreso, selezionato o usato come base per un’azione perché la locale attiva usa una direzione del testo diversa.

Il sistema dovrebbe preservare ordine leggibile, comportamento della punteggiatura e associazione dei controlli per lingue sensibili alla direzione.

La piena rifinitura visiva, la qualità tipografica, il comportamento di accessibilità e il perfezionamento del layout possono richiedere revisione separata. Tuttavia, il contenuto tradotto essenziale deve rimanere significativamente utilizzabile.

<a id="locale-sensitive-values"></a>
### Valori sensibili alla locale

I valori sensibili alla locale sono valori il cui significato o la cui leggibilità può variare in base a lingua, regione, scrittura o cultura.

I valori sensibili alla locale possono includere:

* date
* orari
* numeri
* valute
* misure
* forme plurali
* genere grammaticale
* ordine di ordinamento
* formati degli indirizzi
* formati dei numeri di telefono

I18NSPEC non richiede la localizzazione completa di ogni valore sensibile alla locale salvo quando quel valore è essenziale per comprendere o utilizzare il sistema.

Quando i valori sensibili alla locale sono essenziali, il sistema dovrebbe rappresentarli in un modo che gli utenti della locale attiva possano ragionevolmente comprendere.

<a id="verification"></a>
## Verifica

<a id="within-spec"></a>
### Within Spec

Un sistema è considerato within spec quando il Team CatalystUI ha esaminato il sistema e ha ritenuto ragionevole concludere che soddisfi I18NSPEC.

Un sistema può essere within spec quando:

* ogni locale richiesta è supportata
* più del 75% del contenuto essenziale rivolto all’utente è tradotto per ogni locale richiesta
* tutto il contenuto critico rivolto all’utente è tradotto per ogni locale richiesta
* gli utenti possono selezionare ragionevolmente la locale attiva
* il comportamento di fallback non rivendica falsamente copertura della traduzione
* l’equivalenza delle locale, se usata, è ragionevole e documentata
* il contenuto tradotto preserva il significato essenziale

Un sistema può essere within spec anche se parte del contenuto non essenziale rimane non tradotto.

Un sistema può essere within spec anche se le traduzioni non sono perfette, purché il significato essenziale sia preservato e i requisiti di questa specifica siano soddisfatti.

<a id="warnings"></a>
### Avvisi

Un avviso può essere emesso quando un sistema sembra soddisfare I18NSPEC ma contiene preoccupazioni che dovrebbero essere documentate.

Gli avvisi possono includere:

* contenuto non essenziale minore non tradotto
* terminologia incoerente tra locale
* traduzioni imperfette ma comprensibili
* equivalenza delle locale accettabile che dovrebbe essere documentata
* comportamento di fallback limitato
* pagine opzionali parzialmente tradotte
* preoccupazioni di layout sensibili alla direzione che non impediscono l’uso essenziale
* valori sensibili alla locale comprensibili ma non ideali

Gli avvisi non impediscono necessariamente la verifica.

<a id="failures"></a>
### Fallimenti

Un fallimento si verifica quando un sistema non soddisfa una o più condizioni richieste da I18NSPEC.

I fallimenti possono includere:

* supporto mancante per una locale richiesta
* copertura della traduzione essenziale pari o inferiore al 75% per una locale richiesta
* contenuto critico rivolto all’utente non tradotto
* nessun meccanismo ragionevole di selezione della lingua
* selezione della lingua che richiede modifica del codice sorgente
* selezione della lingua che richiede strumenti per sviluppatori
* caricamento della traduzione rotto
* dichiarazioni di locale fuorvianti
* comportamento di fallback eccessivo
* contenuto di fallback conteggiato come contenuto tradotto senza valida equivalenza delle locale
* contenuto sensibile alla direzione illeggibile o inutilizzabile
* flussi di lavoro essenziali non disponibili in una o più locale richieste

I fallimenti impediscono la verifica finché non vengono risolti.

<a id="verification-validity"></a>
### Validità della verifica

La verifica I18NSPEC si applica solo allo stato esaminato del sistema al momento dell’emissione della verifica.

Un sistema può mantenere la verifica negli aggiornamenti successivi finché preserva la base di internazionalizzazione verificata.

Piccoli cambiamenti di formulazione, traduzioni aggiunte, traduzioni migliorate e normali aggiornamenti di contenuto non invalidano automaticamente la verifica.

Una nuova revisione può essere richiesta se un sistema:

* rimuove il supporto per locale richieste
* rompe la selezione della lingua
* riduce sostanzialmente la copertura della traduzione essenziale
* lascia non tradotti nuovi flussi di lavoro essenziali
* sostituisce contenuto tradotto con contenuto di fallback
* cambia la propria architettura di traduzione in un modo che influisce sul comportamento verificato
* introduce cambiamenti maggiori rivolti all’utente che alterano l’ambito esaminato

In altre parole, migliorare il supporto di traduzione di solito va bene.

Rompere la base multilingue verificata può richiedere una revisione.
