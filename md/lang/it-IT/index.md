<!-- Questa traduzione è stata generata da ChatGPT e deve essere revisionata da un traduttore umano. -->
<!-- Rimuovere queste righe in una pull request dopo che la traduzione è stata verificata. -->

# CatalystUI Verified per linguaggi di programmazione

Benvenuto nella documentazione di verifica CatalystUI per i linguaggi di programmazione.

**CatalystUI Verified per linguaggi di programmazione** indica che un linguaggio di programmazione è stato esaminato dal Team CatalystUI ed è risultato in grado di fornire le rappresentazioni fondamentali dei dati e le strutture relazionali richieste per esprimere sistemi compatibili con CatalystUI.

Questa verifica non è una classifica generale dei linguaggi di programmazione. Non decide se un linguaggio sia migliore, più veloce, più semplice, più recente, più popolare o più piacevole di un altro. Identifica invece se il linguaggio fornisce una base stabile e pratica per le specifiche richieste dalla Verifica CatalystUI.

In termini più semplici, questa verifica chiede se un linguaggio di programmazione può rappresentare fedelmente i dati di base e le relazioni da cui CatalystUI dipende.

## Scopo

I linguaggi di programmazione formano la base rappresentazionale sotto ogni implementazione CatalystUI. Prima che un framework, una libreria, un runtime, un’applicazione o un servizio possa seguire lo Stack CatalystUI, il linguaggio usato per costruirlo deve essere capace di esprimere i concetti fondamentali da cui il modello dipende.

Per i linguaggi di programmazione, questo significa principalmente due cose:

1. Il linguaggio deve essere capace di rappresentare dati fondamentali.
2. Il linguaggio deve essere capace di rappresentare relazioni fondamentali tra dati.

Questi aspetti sono definiti tramite le specifiche fondamentali CatalystUI. FDEFSPEC definisce le rappresentazioni fondamentali dei dati previste. FRELSPEC definisce le relazioni fondamentali previste tra tali rappresentazioni, incluse collezioni, relazioni di memoria, operazioni, relazioni di threading e compositi.

Un linguaggio di programmazione verificato offre agli sviluppatori sufficiente chiarezza e controllo per costruire sistemi compatibili con CatalystUI senza dipendere da soluzioni alternative fragili, poco chiare o instabili per i concetti di base richiesti da CatalystUI.

## Cosa significa verifica

Un linguaggio di programmazione diventa **CatalystUI Verified** quando viene esaminato rispetto alle specifiche elencate in questa sezione e risulta conforme alla specifica.

Per la Verifica dei linguaggi di programmazione, l’esame si concentra sulla capacità del linguaggio di esprimere i requisiti fondamentali definiti dalle specifiche applicabili. Questo non significa che il linguaggio stesso sia un’implementazione di CatalystUI. Significa che il linguaggio fornisce una base adeguata da cui possono essere costruite implementazioni compatibili con CatalystUI.

Un linguaggio non deve soddisfare questi requisiti nello stesso modo di un altro linguaggio. Linguaggi diversi usano sintassi, sistemi di tipi, librerie standard, compilatori, runtime e modelli di progettazione diversi. La Verifica CatalystUI consente queste differenze purché i concetti richiesti possano essere espressi in modo chiaro, affidabile e coerente.

## Cosa significa “Within Spec”

Quando un linguaggio di programmazione è considerato **within spec**, significa che il Team CatalystUI ha esaminato manualmente il linguaggio e ha ritenuto ragionevole concludere che il comportamento richiesto descritto dalle specifiche applicabili possa essere espresso all’interno di quel linguaggio.

Questo non richiede un unico modello di implementazione rigido. Un linguaggio può soddisfare un requisito tramite primitive integrate, funzionalità della libreria standard, comportamento del compilatore, comportamento del runtime, garanzie documentate o un altro meccanismo stabile appropriato per quel linguaggio.

La verifica riguarda la capacità pratica di rappresentare e preservare il significato della specifica, non il fatto che il linguaggio usi esattamente gli stessi nomi, strutture, sintassi o design interno del testo della specifica.

## Perché esiste questa verifica

CatalystUI è progettato intorno a chiarezza, coerenza e rappresentazione fedele di come esseri umani e computer interagiscono. I linguaggi di programmazione sono importanti perché determinano ciò che gli sviluppatori possono realisticamente esprimere, quanto in sicurezza tali sistemi possono essere modellati e quanto chiaramente possono essere costruite implementazioni di livello superiore.

Se un linguaggio non può fornire i concetti fondamentali richiesti in modo stabile, allora le implementazioni CatalystUI di livello superiore diventano più difficili da considerare affidabili. Gli sviluppatori possono essere spinti verso astrazioni poco chiare, comportamenti imprevedibili, dipendenze fragili o riscritture non necessarie solo per esprimere idee che dovrebbero essere affidabili fin dall’inizio.

La Verifica dei linguaggi di programmazione esiste per identificare quali linguaggi forniscono una base abbastanza solida per il lavoro CatalystUI. Offre a sviluppatori, progettisti di linguaggi e organizzazioni una comprensione più chiara dell’idoneità di un linguaggio alla costruzione di sistemi compatibili con CatalystUI.

## Come un linguaggio diventa verificato

Per diventare **CatalystUI Verified per linguaggi di programmazione**, un linguaggio deve essere esaminato rispetto alle specifiche elencate in questa sezione.

Il processo generale è il seguente:

1. Vengono identificate le specifiche CatalystUI applicabili.
2. Il linguaggio viene esaminato rispetto a ogni specifica richiesta.
3. Il Team CatalystUI determina se il linguaggio soddisfa l’intento e i requisiti delle specifiche.
4. Se il linguaggio risulta conforme alla specifica, può ricevere la Verifica CatalystUI.
5. Una volta verificato, il linguaggio può essere elencato nella pagina dei [Linguaggi verificati](/verified/).

L’esame può prendere in considerazione la documentazione ufficiale del linguaggio, il comportamento della libreria standard, il comportamento del compilatore, il comportamento del runtime, esempi di implementazione, casi di test e altre prove necessarie per determinare se il linguaggio soddisfa i requisiti.

Il comportamento del compilatore e del runtime può essere considerato durante l’esame quando tale comportamento fa parte dell’uso comune e ufficiale del linguaggio. Tuttavia, verificare un linguaggio di programmazione non verifica automaticamente ogni compilatore, runtime, pacchetto, framework, libreria, applicazione o strumento nell’ecosistema di quel linguaggio.

## Specifiche applicabili

Le specifiche elencate in questa sezione definiscono i requisiti usati per la Verifica dei linguaggi di programmazione.

Per i linguaggi di programmazione, la base attiva è attualmente centrata sulle seguenti categorie di specifiche:

* **FDEFSPEC**, che definisce le rappresentazioni fondamentali dei dati.
* **FRELSPEC**, che definisce le relazioni fondamentali tra rappresentazioni di dati.

Insieme, queste specifiche stabiliscono la base minima richiesta affinché un linguaggio di programmazione possa rappresentare sistemi compatibili con CatalystUI.

Ulteriori specifiche potranno essere introdotte in seguito per categorie di verifica più specializzate. Tali specifiche potranno definire requisiti di implementazione di livello superiore, piattaforma, accessibilità, internazionalizzazione, framework, servizio o runtime. Tuttavia, quelle specifiche successive si basano sulla fondazione invece di sostituirla.

Un linguaggio di programmazione diventa verificato soddisfacendo le specifiche richieste per questa categoria. Non ci si aspetta che soddisfi requisiti specifici di implementazione non correlati, salvo che tali requisiti vengano aggiunti alla Verifica dei linguaggi di programmazione.

## Ambito della verifica

La Verifica CatalystUI per linguaggi di programmazione si applica al linguaggio di programmazione così come è stato esaminato.

Un linguaggio verificato fornisce una base adatta allo sviluppo compatibile con CatalystUI. Non garantisce che ogni progetto scritto in quel linguaggio segua correttamente CatalystUI, né verifica automaticamente l’ecosistema circostante.

Strumenti, librerie, framework, runtime, applicazioni, servizi o implementazioni separati possono richiedere il proprio esame a seconda della categoria di verifica richiesta.

La Verifica dei linguaggi di programmazione deve quindi essere intesa come un controllo di base. Conferma che il linguaggio può rappresentare i concetti richiesti. Non conferma che ogni uso del linguaggio applichi correttamente tali concetti.

## Validità della verifica

La Verifica CatalystUI si applica soltanto allo stato esaminato di un linguaggio di programmazione nel momento in cui la verifica viene emessa.

I linguaggi di programmazione sono trattati come un caso particolare perché molti linguaggi preservano la compatibilità tra più versioni. Un linguaggio può mantenere la propria verifica nelle versioni successive purché preservi la compatibilità all’indietro con le funzionalità, primitive, rappresentazioni e comportamenti da cui dipendeva l’esame originale.

Le nuove funzionalità di un linguaggio, da sole, non invalidano la verifica. Una versione futura può richiedere un nuovo esame solo se rimuove, rompe o modifica sostanzialmente la base verificata.

In altre parole, estendere un linguaggio di solito va bene. Rompere la base verificata può richiedere un esame.

## Linguaggi verificati

I linguaggi di programmazione verificati noti sono elencati separatamente nella pagina dei [Linguaggi verificati](/verified/).
