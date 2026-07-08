<!-- Questa traduzione è stata generata da ChatGPT e deve essere revisionata da un traduttore umano. -->
<!-- Rimuovere queste righe in una pull request dopo che la traduzione è stata verificata. -->

# Dettagli di verifica

## C

### Panoramica

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Il linguaggio di programmazione C è stato verificato rispetto alle specifiche FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) al 7 luglio 2026.

#### Dichiarazione di buona fede

Riteniamo in buona fede che il linguaggio di programmazione C possa rappresentare ragionevolmente i concetti e le disposizioni definite nelle seguenti specifiche, e che possa essere usato per implementare sistemi conformi a tali specifiche.

#### Dichiarazione di esame

C fornisce un forte supporto di basso livello per la rappresentazione fondamentale dei dati, l’accesso alla memoria, file, stream, procedure, funzioni, strutture e implementazione diretta orientata al sistema.

Sebbene C non fornisca nativamente diversi costrutti compositi orientati agli oggetti, queste limitazioni sono isolate a specifiche disposizioni composite di FRELSPEC e sono documentate di seguito. Questi esiti non conformi non impediscono a C di essere considerato complessivamente conforme alla specifica, ma dovrebbero essere compresi quando si usa C per implementazioni compatibili con CatalystUI.

#### Ipotesi dell’esame

Questo esame presume il supporto del C standard moderno dove sono annotate funzionalità dipendenti dalla versione. Il supporto degli interi a larghezza esatta presume che i tipi `<stdint.h>` corrispondenti siano forniti dall’implementazione.

Questo esame tratta C come linguaggio di rappresentazione di basso livello. Le codifiche esatte a livello di byte possono essere rappresentate direttamente tramite array di byte, tabelle di lookup e logica di parsing esplicita quando non è fornito alcun codec standard nominato.

### Avvisi

* I tipi interi a larghezza esatta dipendono dal supporto dell’implementazione.
* CP1252 può essere rappresentato byte per byte, ma non viene fornito alcun codec standard nominato.
* La serializzazione UTF-16LE richiede la gestione esplicita dell’ordine dei byte.
* I thread standard possono essere omessi da alcune implementazioni C.
* I pattern orientati agli oggetti possono essere emulati manualmente, ma non sono costrutti nativi del linguaggio.

### Esiti non conformi

* C non fornisce membri metodo nativi.
* C non fornisce proprietà native.
* C non fornisce classi native.
* C non fornisce interfacce native.

### Verifica FDEFSPEC

#### Numerici

| Voce | Verificato | Note                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Usare bit-field o maschere.                    |
| Nibble    | ⚠️       | Usare bit-field o maschere.                    |
| Byte      | ✅        | Supportato tramite `unsigned char`.          |
| Short     | ✅        | Supportato tramite `int16_t` e `uint16_t`. |
| Int       | ✅        | Supportato tramite `int32_t` e `uint32_t`. |
| Long      | ✅        | Supportato tramite `int64_t` e `uint64_t`. |
| Float     | ✅        | Supportato tramite `float`.                  |
| Double    | ✅        | Supportato tramite `double`.                 |
| Boolean   | ✅        | Supportato tramite `bool`; C99+.             |

#### Codifica del testo

| Voce | Verificato | Note                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | Supportato tramite `char32_t`; C11+.     |
| ASCII     | ✅        | Rappresentabile come valori byte.           |
| CP1252    | ⚠️        | Richiede mapping esplicito dei byte.         |
| UTF-8     | ✅        | Supportato tramite letterali UTF-8; C11+. |
| UTF-16LE  | ⚠️        | Richiede la gestione dell’ordine dei byte.           |

#### Stato dell’operazione

| Voce | Verificato | Note                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Può essere rappresentato da un enum.  |
| Context   | ✅        | Può essere rappresentato da un valore.  |
| Operation | ✅        | Può essere rappresentato da un valore.  |
| Detail    | ✅        | Può essere rappresentato da un valore.  |
| Result    | ✅        | Può essere rappresentato da una struct. |

### Verifica FRELSPEC

#### Collezioni

| Voce | Verificato | Note                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Può essere rappresentato da struct. |
| Map       | ✅        | Può essere rappresentato da struct. |
| Array     | ✅        | Gli array nativi sono supportati.   |
| File      | ✅        | Supportato tramite API file.   |
| Stream    | ✅        | Supportato tramite API stream. |

#### Memoria

| Voce | Verificato | Note                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Gli indirizzi sono supportati.   |
| Pointer   | ✅        | I puntatori sono supportati.    |
| Variable  | ✅        | Le variabili sono supportate.   |
| Constant  | ✅        | Supportato tramite `const`. |

#### Operazioni

| Voce   | Verificato | Note                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Rappresentato tramite operazioni macchina. |
| Procedure   | ✅        | Supportato tramite funzioni `void`.     |
| Function    | ✅        | Supportato tramite funzioni che restituiscono un valore.  |

#### Threading

| Voce  | Verificato | Note                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Supportato tramite ambienti hosted. |
| Thread     | ⚠️        | Supportato tramite `<threads.h>`; C11+. |
| Dispatcher | ✅        | Può essere rappresentato direttamente.           |

#### Compositi

| Voce | Verificato | Note                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | I membri struct sono supportati.            |
| Object    | ✅        | Le struct possono formare compositi indirizzabili. |
| Field     | ✅        | I campi struct sono supportati.             |
| Method    | ❌        | Nessun membro metodo nativo.                |
| Property  | ❌        | Nessuna mappa esplicita di accessor Get/Set.        |
| Structure | ✅        | Le strutture sono supportate nativamente.       |
| Class     | ❌        | Nessun costrutto classe nativo.               |
| Interface | ❌        | Nessun costrutto interfaccia nativo.           |
