<!-- Questa traduzione è stata generata da ChatGPT e deve essere revisionata da un traduttore umano. -->
<!-- Rimuovere queste righe in una pull request dopo che la traduzione è stata verificata. -->

# Dettagli di verifica

## Java

### Panoramica

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Il linguaggio di programmazione Java è stato verificato rispetto alle specifiche FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) al 7 luglio 2026.

#### Dichiarazione di buona fede

Riteniamo in buona fede che il linguaggio di programmazione Java possa rappresentare ragionevolmente una grande parte dei concetti e delle disposizioni definite nelle seguenti specifiche, e che possa essere usato per implementare sistemi conformi a tali specifiche.

#### Ipotesi dell’esame

Questo esame presume il supporto del linguaggio Java moderno dove sono annotate funzionalità dipendenti dalla versione. Funzionalità come inferenza delle variabili locali, record e accesso alla memoria esterna possono richiedere versioni Java successive.

### Avvisi

* Java non dispone di supporto nativo per tipi numerici unsigned, il che può richiedere widening o rappresentazioni alternative per alcune disposizioni.
* Direct memory address and pointer-style behavior may require Java 22+ Foreign Function and Memory API support.
* Java non dispone di sintassi nativa per le proprietà, richiedendo invece metodi getter e setter.

### Esiti non conformi

* Java non fornisce CP1252 come set di caratteri standard garantito, richiedendo supporto specifico dell’implementazione, librerie aggiuntive o gestione personalizzata per la piena conformità.
* Java properties do not provide an explicit keyed member backed by a required Get/Set accessor map.

### Verifica FDEFSPEC

#### Numerici

| Voce | Verificato | Note                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | Nessun numerico a 1 bit; ampliare.                         |
| Nibble    | ⚠️       | Nessun numerico a 4 bit; ampliare.                         |
| Byte      | ⚠️       | Signed 8-bit only; widen for unsigned.           |
| Short     | ⚠️       | Signed 16-bit only; widen for unsigned.          |
| Int       | ⚠️       | Signed 32-bit; unsigned helpers require Java 8+. |
| Long      | ⚠️       | Signed 64-bit; unsigned helpers require Java 8+. |
| Float     | ✅        | 32-bit floating point is supported.              |
| Double    | ✅        | 64-bit floating point is supported.              |
| Boolean   | ✅        | Boolean type is supported.                       |

#### Codifica del testo

| Voce | Verificato | Note                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Supportato tramite `int` e `Character`. |
| ASCII     | ✅        | Guaranteed standard charset.             |
| CP1252    | ❌        | Not guaranteed by `StandardCharsets`.    |
| UTF-8     | ✅        | Guaranteed standard charset.             |
| UTF-16LE  | ✅        | Guaranteed standard charset.             |

#### Stato dell’operazione

| Voce | Verificato | Note                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Può essere rappresentato da un tipo personalizzato.        |
| Context   | ✅        | Può essere rappresentato da un valore personalizzato.       |
| Operation | ✅        | Può essere rappresentato da un valore personalizzato.       |
| Detail    | ✅        | Può essere rappresentato da un valore personalizzato.       |
| Result    | ✅        | Può essere rappresentato da un tipo restituito personalizzato. |

### Verifica FRELSPEC

#### Collezioni

| Voce | Verificato | Note                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Supportato tramite `Set`.       |
| Map       | ✅        | Supportato tramite `Map`.       |
| Array     | ✅        | Gli array nativi sono supportati.   |
| File      | ✅        | Supportato tramite API file.   |
| Stream    | ✅        | Supportato tramite API stream. |

#### Memoria

| Voce | Verificato | Note                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses require Java 22+ FFM.                         |
| Pointer   | ⚠️       | Pointer-like access requires Java 22+ FFM.                     |
| Variable  | ✅        | Declarations and `var` are supported; `var` requires Java 10+. |
| Constant  | ✅        | Supportato tramite `final`.                                     |

#### Operazioni

| Voce   | Verificato | Note                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Rappresentato tramite bytecode e operazioni. |
| Procedure   | ✅        | Supportato tramite metodi `void`.            |
| Function    | ✅        | Supportato tramite metodi che restituiscono un valore.         |

#### Threading

| Voce  | Verificato | Note                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Supportato tramite API applicazione e `Process`. |
| Thread     | ✅        | Supportato tramite `Thread`.                       |
| Dispatcher | ✅        | Supportato tramite API `Executor`.                |

#### Compositi

| Voce | Verificato | Note                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | I membri di classe sono supportati.           |
| Object    | ✅        | Gli oggetti sono supportati.                 |
| Field     | ✅        | I campi sono supportati.                  |
| Method    | ✅        | I metodi sono supportati.                 |
| Property  | ❌        | Nessuna mappa di accessor esplicita.              |
| Structure | ✅        | Supportato tramite record; Java 16+.   |
| Class     | ✅        | Le classi sono supportate.                 |
| Interface | ✅        | Interfaces are supported.              |
