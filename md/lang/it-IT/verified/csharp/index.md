<!-- Questa traduzione è stata generata da ChatGPT e deve essere revisionata da un traduttore umano. -->
<!-- Rimuovere queste righe in una pull request dopo che la traduzione è stata verificata. -->

# Dettagli di verifica

## C#

### Panoramica

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Il linguaggio di programmazione C# è stato verificato rispetto alle specifiche FDEFSPEC (Rev. 1) e FRELSPEC (Rev. 1) al 7 luglio 2026.

#### Dichiarazione di buona fede

Riteniamo in buona fede che il linguaggio di programmazione C# possa rappresentare ragionevolmente i concetti e le disposizioni definite nelle seguenti specifiche, e che possa essere usato per implementare sistemi conformi a tali specifiche.

#### Ipotesi dell’esame

Questo esame presume il supporto moderno di C# e .NET dove sono annotate funzionalità dipendenti dalla versione.

### Avvisi

* Il supporto CP1252 è disponibile tramite il provider ufficiale delle code page di .NET, ma può richiedere la registrazione del provider o un pacchetto aggiuntivo a seconda del runtime di destinazione.
* Il comportamento dei puntatori unsafe può richiedere autorizzazione unsafe esplicita.

### Esiti non conformi

* Durante questa verifica non sono stati trovati esiti non conformi noti per FDEFSPEC o FRELSPEC.

### Verifica FDEFSPEC

#### Numerici

| Voce | Verificato | Note                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | Nessun numerico a 1 bit; ampliare.                |
| Nibble    | ⚠️       | Nessun numerico a 4 bit; ampliare.                |
| Byte      | ✅        | Supportato tramite `byte` e `sbyte`.   |
| Short     | ✅        | Supportato tramite `short` e `ushort`. |
| Int       | ✅        | Supportato tramite `int` e `uint`.     |
| Long      | ✅        | Supportato tramite `long` e `ulong`.   |
| Float     | ✅        | Supportato tramite `float`.              |
| Double    | ✅        | Supportato tramite `double`.             |
| Boolean   | ✅        | Supportato tramite `bool`.               |

#### Codifica del testo

| Voce | Verificato | Note                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | Supportato tramite numerici e `Rune`. |
| ASCII     | ✅        | Supportato tramite `Encoding.ASCII`.    |
| CP1252    | ⚠️       | Richiede il provider delle code page.          |
| UTF-8     | ✅        | Supportato tramite `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | Supportato tramite `Encoding.Unicode`.  |

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

| Voce | Verificato | Note                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Supportato tramite `HashSet<T>`.              |
| Map       | ✅        | Supportato tramite `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Gli array nativi sono supportati.                 |
| File      | ✅        | Supportato tramite API file.                 |
| Stream    | ✅        | Supportato tramite `Stream`.                  |

#### Memoria

| Voce | Verificato | Note                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Supportato tramite riferimenti e puntatori. |
| Pointer   | ✅        | Supportato tramite puntatori unsafe.         |
| Variable  | ✅        | Le variabili sono supportate.                   |
| Constant  | ✅        | Supportato tramite `const` e `readonly`.  |

#### Operazioni

| Voce   | Verificato | Note                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Rappresentato tramite IL e operazioni. |
| Procedure   | ✅        | Supportato tramite metodi `void`.      |
| Function    | ✅        | Supportato tramite metodi che restituiscono un valore.   |

#### Threading

| Voce  | Verificato | Note                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Supportato tramite API applicazione e `Process`. |
| Thread     | ✅        | Supportato tramite `Thread`.                       |
| Dispatcher | ✅        | Supportato tramite task e scheduler.           |

#### Compositi

| Voce | Verificato | Note                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | I membri di tipo sono supportati.        |
| Object    | ✅        | Gli oggetti sono supportati.             |
| Field     | ✅        | I campi sono supportati.              |
| Method    | ✅        | I metodi sono supportati.             |
| Property  | ✅        | Le proprietà sono supportate nativamente. |
| Structure | ✅        | Le strutture sono supportate nativamente. |
| Class     | ✅        | Le classi sono supportate.             |
| Interface | ✅        | Interfaces are supported.          |
