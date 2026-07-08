<!-- Questa traduzione è stata generata da ChatGPT e deve essere revisionata da un traduttore umano. -->
<!-- Rimuovere queste righe in una pull request dopo che la traduzione è stata verificata. -->

# Dettagli di verifica

## C++

### Panoramica

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Il linguaggio di programmazione C++ è stato verificato rispetto alle specifiche FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) al 7 luglio 2026.

#### Dichiarazione di buona fede

Riteniamo in buona fede che il linguaggio di programmazione C++ possa rappresentare ragionevolmente i concetti e le disposizioni definite nelle seguenti specifiche, e che possa essere usato per implementare sistemi conformi a tali specifiche.

#### Ipotesi dell’esame

Questo esame presume il supporto del C++ standard moderno dove sono annotate funzionalità dipendenti dalla versione. Il supporto degli interi a larghezza esatta presume che i tipi `<cstdint>` corrispondenti siano forniti dall’implementazione.

Questo esame tratta C++ come linguaggio di programmazione di sistema con supporto diretto per rappresentazione di basso livello, modellazione degli oggetti, controllo della memoria, programmazione generica ed esecuzione concorrente.

### Avvisi

* I tipi interi a larghezza esatta dipendono dal supporto dell’implementazione.
* CP1252 può essere rappresentato byte per byte, ma non viene fornito alcun codec standard nominato.
* La serializzazione UTF-16LE richiede la gestione esplicita dell’ordine dei byte.
* Alcune funzionalità di concorrenza e caratteri richiedono revisioni moderne di C++.

### Esiti non conformi

* Durante questa verifica non sono stati trovati esiti non conformi noti per FDEFSPEC o FRELSPEC.

### Verifica FDEFSPEC

#### Numerici

| Voce | Verificato | Note                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Usare bit-field o maschere.                    |
| Nibble    | ⚠️       | Usare bit-field o maschere.                    |
| Byte      | ✅        | Supportato tramite `std::byte`.              |
| Short     | ✅        | Supportato tramite `int16_t` e `uint16_t`. |
| Int       | ✅        | Supportato tramite `int32_t` e `uint32_t`. |
| Long      | ✅        | Supportato tramite `int64_t` e `uint64_t`. |
| Float     | ✅        | Supportato tramite `float`.                  |
| Double    | ✅        | Supportato tramite `double`.                 |
| Boolean   | ✅        | Supportato tramite `bool`.                   |

#### Codifica del testo

| Voce | Verificato | Note                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Supportato tramite `char32_t`.        |
| ASCII     | ✅        | Rappresentabile come valori byte.        |
| CP1252    | ⚠️        | Richiede mapping esplicito dei byte.      |
| UTF-8     | ✅        | Supportato tramite `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Richiede la gestione dell’ordine dei byte.        |

#### Stato dell’operazione

| Voce | Verificato | Note                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Può essere rappresentato da un enum.           |
| Context   | ✅        | Può essere rappresentato da un valore.           |
| Operation | ✅        | Può essere rappresentato da un valore.           |
| Detail    | ✅        | Può essere rappresentato da un valore.           |
| Result    | ✅        | Può essere rappresentato da una struct o una classe. |

### Verifica FRELSPEC

#### Collezioni

| Voce | Verificato | Note                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Supportato tramite `std::set`.              |
| Map       | ✅        | Supportato tramite `std::map`.              |
| Array     | ✅        | Supportato tramite array e `std::array`. |
| File      | ✅        | Supportato tramite file stream.            |
| Stream    | ✅        | Supportato tramite iostream.               |

#### Memoria

| Voce | Verificato | Note                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Gli indirizzi sono supportati.                   |
| Pointer   | ✅        | I puntatori sono supportati.                    |
| Variable  | ✅        | Le variabili sono supportate.                   |
| Constant  | ✅        | Supportato tramite `const` e `constexpr`. |

#### Operazioni

| Voce   | Verificato | Note                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Rappresentato tramite operazioni macchina. |
| Procedure   | ✅        | Supportato tramite funzioni `void`.     |
| Function    | ✅        | Supportato tramite funzioni che restituiscono un valore.  |

#### Threading

| Voce  | Verificato | Note                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Supportato tramite esecuzione hosted.      |
| Thread     | ✅        | Supportato tramite `std::thread`; C++11+. |
| Dispatcher | ✅        | Supportato tramite async e scheduler.  |

#### Compositi

| Voce | Verificato | Note                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | I membri di classe sono supportati.            |
| Object    | ✅        | Gli oggetti sono supportati.                  |
| Field     | ✅        | I campi sono supportati.                   |
| Method    | ✅        | I metodi sono supportati.                  |
| Property  | ✅        | Le mappe Get/Set possono essere rappresentate.        |
| Structure | ✅        | Le strutture sono supportate nativamente.      |
| Class     | ✅        | Le classi sono supportate nativamente.         |
| Interface | ✅        | Può essere rappresentato da classi astratte. |
