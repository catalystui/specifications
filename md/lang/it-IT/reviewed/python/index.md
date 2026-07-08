<!-- Questa traduzione è stata generata da ChatGPT e deve essere revisionata da un traduttore umano. -->
<!-- Rimuovere queste righe in una pull request dopo che la traduzione è stata verificata. -->

# Dettagli di esame

## Python

### Panoramica

Il linguaggio di programmazione Python è stato esaminato rispetto alle specifiche FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) al 7 luglio 2026.

#### Dichiarazione di esame

Sebbene Python possa rappresentare molti concetti richiesti tramite tipi integrati, oggetti, funzioni, classi, moduli della libreria standard e validazione personalizzata, questi meccanismi non sono sufficienti a soddisfare le specifiche CatalystUI applicabili a livello di linguaggio.

Python fornisce un forte supporto per codifica del testo, file, stream, oggetti, funzioni, classi, proprietà, processi, thread ed esecuzione dispatchata tramite il suo comportamento integrato e la libreria standard. Tuttavia, Python non fornisce i tipi numerici scalari a larghezza fissa richiesti, non definisce vere costanti e si affida al comportamento dinamico del runtime per diversi costrutti che altri linguaggi verificati possono esprimere più direttamente.

Per questo motivo, non riteniamo che Python fornisca una base abbastanza stabile per un’implementazione conforme a CatalystUI senza un’infrastruttura aggiuntiva significativa.

Di conseguenza, a Python non è stato concesso lo stato CatalystUI Verified per i linguaggi di programmazione.

#### Ipotesi dell’esame

Questo esame valuta Python stesso e la sua libreria standard inclusa.

Pacchetti di terze parti, estensioni specifiche dell’implementazione, moduli nativi opzionali, type checker esterni, transpiler e framework runtime personalizzati non sono trattati come supporto a livello di linguaggio.

### Avvisi

* Python fornisce interi a precisione illimitata, non primitive intere a larghezza fissa.
* `float` di Python è solitamente a precisione doppia, ma non è una famiglia distinta a larghezza fissa.
* Alcuni comportamenti di memoria di basso livello possono richiedere `ctypes` o comportamento specifico dell’implementazione.
* I type hint di Python non sono applicati a runtime.
* Python supporta le proprietà, ma il comportamento setter può essere omesso.
* Python può modellare diverse strutture tramite funzionalità della libreria standard, ma non come tipo struttura nativo.

### Esiti non conformi

* Python non fornisce la maggior parte dei tipi numerici scalari a larghezza fissa richiesti.
* Python non fornisce un tipo scalare dedicato in virgola mobile a 32 bit.
* Python non fornisce vere costanti a livello di linguaggio.
* Python non definisce procedure separatamente dalle funzioni.
* Python non fornisce supporto nativo per i puntatori.
* Python non fornisce supporto nativo per le interfacce.

### Verifica FDEFSPEC

#### Numerici

| Voce | Verificato | Note                                |
| --------- | -------- | ------------------------------------ |
| Bit       | ❌        | Nessun tipo numerico a 1 bit.               |
| Nibble    | ❌        | Nessun tipo numerico a 4 bit.               |
| Byte      | ❌        | Nessun tipo intero scalare a 8 bit.        |
| Short     | ❌        | Nessun tipo intero scalare a 16 bit.       |
| Int       | ❌        | Nessun tipo intero scalare a 32 bit.       |
| Long      | ❌        | Nessun tipo intero scalare a 64 bit.       |
| Float     | ❌        | Nessun tipo float scalare a 32 bit.         |
| Double    | ⚠️       | `float` è solitamente a precisione doppia. |
| Boolean   | ✅        | Supportato tramite `bool`.            |

#### Codifica del testo

| Voce | Verificato | Note                            |
| --------- | -------- | -------------------------------- |
| Codepoint | ✅        | Le stringhe usano code point Unicode. |
| ASCII     | ✅        | Codec supportato.                 |
| CP1252    | ✅        | Codec supportato.                 |
| UTF-8     | ✅        | Codec supportato.                 |
| UTF-16LE  | ✅        | Codec supportato.                 |

#### Stato dell’operazione

| Voce | Verificato | Note                       |
| --------- | -------- | --------------------------- |
| Status    | ⚠️       | Richiede validazione personalizzata. |
| Context   | ⚠️       | Richiede validazione personalizzata. |
| Operation | ⚠️       | Richiede validazione personalizzata. |
| Detail    | ⚠️       | Richiede validazione personalizzata. |
| Result    | ⚠️       | Richiede validazione personalizzata. |

### Verifica FRELSPEC

#### Collezioni

| Voce | Verificato | Note                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Supportato tramite `set`.       |
| Map       | ✅        | Supportato tramite `dict`.      |
| Array     | ✅        | Supportato tramite sequenze.   |
| File      | ✅        | Supportato tramite API file.   |
| Stream    | ✅        | Supportato tramite API stream. |

#### Memoria

| Voce | Verificato | Note                        |
| --------- | -------- | ---------------------------- |
| Address   | ⚠️       | Solo identità dell’oggetto.        |
| Pointer   | ❌        | Nessun supporto nativo per puntatori.   |
| Variable  | ✅        | Le associazioni di nomi sono supportate. |
| Constant  | ❌        | Nessuna vera costante.           |

#### Operazioni

| Voce   | Verificato | Note                             |
| ----------- | -------- | --------------------------------- |
| Instruction | ⚠️       | Il bytecode è a livello di implementazione. |
| Procedure   | ❌        | Le funzioni restituiscono `None`.          |
| Function    | ✅        | Le funzioni sono supportate.          |

#### Threading

| Voce  | Verificato | Note                            |
| ---------- | -------- | -------------------------------- |
| Process    | ✅        | Supportato tramite API di processo.  |
| Thread     | ✅        | Supportato tramite `threading`.   |
| Dispatcher | ✅        | Supportato tramite API executor. |

#### Compositi

| Voce | Verificato | Note                            |
| --------- | -------- | -------------------------------- |
| Member    | ✅        | I membri oggetto sono supportati.    |
| Object    | ✅        | Gli oggetti sono supportati.           |
| Field     | ✅        | Gli attributi possono rappresentare campi. |
| Method    | ✅        | I metodi sono supportati.           |
| Property  | ⚠️       | Esiste supporto getter/setter.    |
| Structure | ⚠️       | Solo modelli della libreria standard.    |
| Class     | ✅        | Le classi sono supportate.           |
| Interface | ❌        | Nessun supporto nativo per interfacce.     |
