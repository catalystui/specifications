<!-- Questa traduzione è stata generata da ChatGPT e deve essere revisionata da un traduttore umano. -->
<!-- Rimuovere queste righe in una pull request dopo che la traduzione è stata verificata. -->

# Dettagli di esame

## JavaScript

### Panoramica

Il linguaggio di programmazione JavaScript è stato esaminato rispetto alle specifiche FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) al 7 luglio 2026.

#### Dichiarazione di esame

Sebbene JavaScript possa rappresentare alcuni concetti richiesti tramite oggetti, funzioni, array e comportamento integrato del linguaggio, questi meccanismi non sono sufficienti a soddisfare le specifiche CatalystUI applicabili a livello di linguaggio.

Questo esame valuta JavaScript stesso, non l’ecosistema JavaScript circostante. Le API del browser, le API Node.js, le API Deno, le API Bun, le Web API, TypeScript, WebAssembly, librerie esterne e validazione personalizzata non sono trattate come supporto a livello di linguaggio.

Poiché JavaScript manca di molti tipi numerici scalari a larghezza fissa richiesti, non fornisce le codifiche del testo richieste come funzionalità del linguaggio e non definisce diversi costrutti richiesti di sistema, memoria, threading e compositi, non riteniamo che JavaScript fornisca una base abbastanza stabile per un’implementazione conforme a CatalystUI senza un’infrastruttura aggiuntiva significativa.

Di conseguenza, a JavaScript non è stato concesso lo stato CatalystUI Verified per i linguaggi di programmazione.

#### Ipotesi dell’esame

Questo esame applica uno standard rigoroso a livello di linguaggio. Se una disposizione non è esplicitamente supportata da JavaScript stesso, viene contrassegnata come non verificata.

Le API fornite dall’host, il comportamento specifico dell’implementazione, le librerie esterne, i transpiler, i sistemi di tipi e la validazione runtime personalizzata sono esclusi dalla verifica.

### Avvisi

* JavaScript può rappresentare molti valori numerici tramite `Number`, ma `Number` è un tipo numerico in virgola mobile a 64 bit.
* JavaScript fornisce `BigInt`, ma `BigInt` è a larghezza arbitraria.
* Gli array tipizzati forniscono viste di archiviazione binaria, non tipi scalari del linguaggio.
* Le stringhe JavaScript usano unità di codice UTF-16, non valori espliciti di codifica del testo.
* `const` protegge le associazioni, non i valori degli oggetti.

### Esiti non conformi

* JavaScript non fornisce la maggior parte dei tipi numerici scalari a larghezza fissa richiesti.
* JavaScript non fornisce un tipo scalare dedicato in virgola mobile a 32 bit.
* JavaScript non fornisce ASCII, CP1252, UTF-8 o UTF-16LE come codifiche del testo a livello di linguaggio.
* JavaScript non fornisce costrutti file o stream a livello di linguaggio.
* JavaScript non fornisce costrutti indirizzo o puntatore a livello di linguaggio.
* JavaScript non fornisce costrutti processo, thread o dispatcher a livello di linguaggio.
* Le proprietà JavaScript non forniscono un membro esplicito con chiave sostenuto da una mappa di accessor Get/Set richiesta.
* JavaScript non fornisce strutture o interfacce.

### Verifica FDEFSPEC

#### Numerici

| Voce | Verificato | Note                          |
| --------- | -------- | ------------------------------ |
| Bit       | ❌        | Nessun tipo numerico a 1 bit.         |
| Nibble    | ❌        | Nessun tipo numerico a 4 bit.         |
| Byte      | ❌        | Nessun tipo intero scalare a 8 bit.  |
| Short     | ❌        | Nessun tipo intero scalare a 16 bit. |
| Int       | ❌        | Nessun tipo intero scalare a 32 bit. |
| Long      | ❌        | Nessun tipo intero scalare a 64 bit. |
| Float     | ❌        | Nessun tipo float scalare a 32 bit.   |
| Double    | ✅        | Supportato tramite `Number`.    |
| Boolean   | ✅        | Supportato tramite `boolean`.   |

#### Codifica del testo

| Voce | Verificato | Note                        |
| --------- | -------- | ---------------------------- |
| Codepoint | ❌        | Nessun tipo codepoint dedicato. |
| ASCII     | ❌        | Non a livello di linguaggio.          |
| CP1252    | ❌        | Non a livello di linguaggio.          |
| UTF-8     | ❌        | Non a livello di linguaggio.          |
| UTF-16LE  | ❌        | Non a livello di linguaggio.          |

#### Stato dell’operazione

| Voce | Verificato | Note                           |
| --------- | -------- | ------------------------------- |
| Status    | ⚠️       | Rappresentabile, non imponibile. |
| Context   | ⚠️       | Rappresentabile, non imponibile. |
| Operation | ⚠️       | Rappresentabile, non imponibile. |
| Detail    | ⚠️       | Rappresentabile, non imponibile. |
| Result    | ⚠️       | Richiede validazione a runtime.    |

### Verifica FRELSPEC

#### Collezioni

| Voce | Verificato | Note                    |
| --------- | -------- | ------------------------ |
| Set       | ✅        | Supportato tramite `Set`. |
| Map       | ✅        | Supportato tramite `Map`. |
| Array     | ✅        | Gli array sono supportati.    |
| File      | ❌        | Non a livello di linguaggio.      |
| Stream    | ❌        | Non a livello di linguaggio.      |

#### Memoria

| Voce | Verificato | Note                           |
| --------- | -------- | ------------------------------- |
| Address   | ❌        | Nessun supporto per indirizzi.             |
| Pointer   | ❌        | Nessun supporto per puntatori.             |
| Variable  | ✅        | Le variabili sono supportate.        |
| Constant  | ⚠️       | `const` protegge solo le associazioni. |

#### Operazioni

| Voce   | Verificato | Note                            |
| ----------- | -------- | -------------------------------- |
| Instruction | ❌        | Nessun tipo istruzione definito.     |
| Procedure   | ❌        | Le funzioni restituiscono sempre un valore. |
| Function    | ✅        | Le funzioni sono supportate.         |

#### Threading

| Voce  | Verificato | Note                       |
| ---------- | -------- | --------------------------- |
| Process    | ❌        | Non a livello di linguaggio.         |
| Thread     | ⚠️        | Rappresentato tramite agenti. |
| Dispatcher | ❌        | Richiede scheduling dell’host.   |


#### Compositi

| Voce | Verificato | Note                                 |
| --------- | -------- | ------------------------------------- |
| Member    | ✅        | I membri oggetto sono supportati.         |
| Object    | ✅        | Gli oggetti sono supportati.                |
| Field     | ✅        | Le proprietà dati possono rappresentare campi. |
| Method    | ✅        | I metodi sono supportati.                |
| Property  | ❌        | Nessuna mappa di accessor esplicita.             |
| Structure | ❌        | Nessun supporto per strutture.                 |
| Class     | ✅        | La sintassi delle classi è supportata.            |
| Interface | ❌        | Nessun supporto per interfacce.                 |
