<!-- Questa traduzione è stata generata da ChatGPT e deve essere revisionata da un traduttore umano. -->
<!-- Rimuovere queste righe in una pull request dopo che la traduzione è stata verificata. -->

# FDEFSPEC

<br/>

> **Specifica delle definizioni fondamentali**<br/>
> Revisione 1<br/>
> 23 marzo 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Tutti i diritti riservati.<br/>
> <br/>
> Le definizioni e i concetti presentati qui descrivono costrutti matematici fondamentali e possono essere riespressi liberamente.

## Introduzione

La **Specifica delle definizioni fondamentali (FDEFSPEC)** stabilisce i concetti e la terminologia di base che sostengono l’ecosistema CatalystUI. Il suo scopo è fornire una comprensione unificata di questi concetti attraverso documentazione, specifiche, implementazioni ed esami di verifica, assicurando coerenza, chiarezza e allineamento.

Definendo termini e relazioni chiave in una forma precisa e stabile, FDEFSPEC fornisce un punto di riferimento comune per specifiche di livello superiore. Questo consente a sviluppatori, revisori e implementatori di ragionare dalla stessa base quando determinano se un linguaggio, servizio, framework o sistema possa essere considerato conforme alla specifica.

> [!IMPORTANT]
>
> Esprimiamo le definizioni usando una forma derivata della notazione della [teoria degli insiemi](https://en.wikipedia.org/wiki/Set_theory). Questo approccio fornisce definizioni precise e non ambigue mantenendo chiarezza e concisione. Strutturiamo queste definizioni per supportare un riferimento semplice, un’interpretazione chiara e una gerarchia concettuale coerente.

## Sommario

- [FDEFSPEC](#fdefspec)
  - [Introduction](#introduction)
  - [Sommario](#table-of-contents)
  - [Numerici](#numerics)
    - [Bit](#bit)
    - [Nibble](#nibble)
      - [Nibble()](#nibble-1)
    - [Byte](#byte)
      - [Byte()](#byte-1)
      - [SByte()](#sbyte)
    - [Short](#short)
      - [Short()](#short-1)
      - [UShort()](#ushort)
    - [Int](#int)
      - [Int()](#int-1)
      - [UInt()](#uint)
    - [Long](#long)
      - [Long()](#long-1)
      - [ULong()](#ulong)
    - [Single](#single)
      - [Single()](#single-1)
    - [Double](#double)
      - [Double()](#double-1)
    - [Boolean](#boolean)
      - [Boolean()](#boolean-1)
  - [Codifica del testo](#text-encoding)
    - [Codifica del testo](#text-encoding-1)
      - [Text Encoding()](#text-encoding-2)
    - [Codepoint](#codepoint)
      - [Codepoint()](#codepoint-1)
    - [ASCII Code Unit](#ascii-code-unit)
      - [ASCII Code Unit()](#ascii-code-unit-1)
      - [ASCII()](#ascii)
    - [CP1252 Code Unit](#cp1252-code-unit)
      - [CP1252 Code Unit()](#cp1252-code-unit-1)
      - [CP1252()](#cp1252)
    - [UTF-8 Code Unit](#utf-8-code-unit)
      - [UTF-8 Code Unit()](#utf-8-code-unit-1)
      - [UTF-8()](#utf-8)
    - [UTF-16LE Code Unit](#utf-16le-code-unit)
      - [UTF-16LE Code Unit()](#utf-16le-code-unit-1)
      - [UTF-16LE()](#utf-16le)
  - [Stato dell’operazione](#operation-status)
    - [Codice di stato](#status-code)
      - [Status Code()](#status-code-1)
      - [Status Code Level()](#status-code-level)
      - [Status Code Definition()](#status-code-definition)
        - [Successo](#success)
        - [Avviso](#warning)
        - [Errore](#error)
        - [Fatale](#fatal)
    - [Codice di contesto](#context-code)
      - [Context Code()](#context-code-1)
    - [Codice di operazione](#operation-code)
      - [Operation Code()](#operation-code-1)
    - [Codice di dettaglio](#detail-code)
      - [Detail Code()](#detail-code-1)
    - [Risultato](#result)
      - [Result()](#result-1)

## Numerici

### Bit

Un bit è qualsiasi $b \in \{0,1\}$.

### Nibble

Un nibble è qualsiasi $(b_0,\dots,b_3)$ tale che per ogni $i \in \{0,\dots,3\}$, $b_i \in \mathrm{Bit}$.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

Un byte è qualsiasi $(b_0,\dots,b_7)$ tale che per ogni $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

Uno short è qualsiasi $(b_0,\dots,b_{15})$ tale che per ogni $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

Un intero è qualsiasi $(b_0,\dots,b_{31})$ tale che per ogni $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

Un long è qualsiasi $(b_0,\dots,b_{63})$ tale che per ogni $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

Un single è qualsiasi $(b_0,\dots,b_{31})$ tale che per ogni $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Single()

La seguente definizione è conforme allo standard IEEE 754 per la rappresentazione in virgola mobile a precisione singola. Definisce come una sequenza binaria a 32 bit viene interpretata come numero in virgola mobile, inclusi i casi speciali per zero, infinito e NaN (Not a Number).

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Let $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

Un double è qualsiasi $(b_0,\dots,b_{63})$ tale che per ogni $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Double()

La seguente definizione è conforme allo standard IEEE 754 per la rappresentazione in virgola mobile a precisione doppia. Definisce come una sequenza binaria a 64 bit viene interpretata come numero in virgola mobile, inclusi i casi speciali per zero, infinito e NaN (Not a Number).

> Let $s = b_0$
>
> Let $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Let $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

Un booleano è qualsiasi $b \in \{0,1\}$.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## Codifica del testo

### Codifica del testo

Una codifica del testo è definita come il seguente insieme:

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Codifica del testo()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Un codepoint Unicode è qualsiasi $e \in \mathbb{Z}$ tale che $0 \leq e \leq 0x10FFFF$.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

Un’unità di codice ASCII è qualsiasi $(b_0,\dots,b_6)$ tale che per ogni $i \in \{0,\dots,6\}$, $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

È comune rappresentare un’unità di codice ASCII come byte aggiungendo un bit zero iniziale, per ragioni di prestazioni e compatibilità. In tali casi, l’unità di codice ASCII è rappresentata come:

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Altrimenti:

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Nel caso di questo teorema, entrambe le definizioni sono rappresentazioni accettabili di un’unità di codice ASCII. Per coerenza, useremo la prima definizione quando rappresentiamo unità di codice ASCII come byte, e la seconda definizione quando le rappresentiamo come sequenze a 7 bit.

#### ASCII()

ASCII è una tupla finita terminata da null $(u_0, \dots, u_k, u_{k+1})$ tale che:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is an ASCII code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

La sequenza si dice terminata da null.

### CP1252 Code Unit

Un’unità di codice CP1252 è qualsiasi $(b_0,\dots,b_7)$ tale che per ogni $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 è una tupla finita terminata da null $(u_0, \dots, u_k, u_{k+1})$ tale che:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a CP1252 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

La sequenza si dice terminata da null.

### UTF-8 Code Unit

Un’unità di codice UTF-8 è qualsiasi $(b_0,\dots,b_7)$ tale che per ogni $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 è una tupla finita terminata da null $(u_0, \dots, u_k, u_{k+1})$ tale che:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-8 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

La sequenza si dice terminata da null.

### UTF-16LE Code Unit

Un’unità di codice UTF-16LE è qualsiasi $(b_0,\dots,b_{15})$ tale che per ogni $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE è una tupla finita terminata da null $(u_0, \dots, u_k, u_{k+1})$ tale che:

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-16LE code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

La sequenza si dice terminata da null.

## Stato dell’operazione

### Codice di stato

Un codice di stato è qualsiasi $(b_0,\dots,b_7)$ tale che per ogni $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

Un livello di codice di stato è definito come il seguente insieme:

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Codice di stato()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Livello del codice di stato()

L’insieme dei valori del codice di stato è l’intervallo $[0, 255]$, suddiviso in quattro livelli:

> Let $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Definizione del codice di stato()

Tutti i codici di stato hanno definizioni esplicite. Qualsiasi codice di stato non incluso nell’elenco seguente è riservato per uso futuro e il suo significato è indefinito. Il livello di un codice di stato è determinato da $\mathrm{Status\ Code\ Level}(s)$.

Nell’elenco seguente, l’input $s$ è rappresentato come valore esadecimale per leggibilità. Ogni codice di stato definito specifica il livello, la categoria, la sottocategoria, la descrizione e il dettaglio corrispondenti, ove applicabile.

Questo elenco può essere esteso man mano che vengono definiti nuovi codici di stato. Qualsiasi nuovo codice di stato definito non deve entrare in conflitto con codici esistenti e deve avere un significato chiaramente documentato.

Per comunicare informazioni non rappresentate da un codice di stato definito, si dovrebbe usare il codice di contesto, il codice di operazione o il codice di dettaglio.

##### Successo

| Codice | Livello | Categoria | Descrizione | Dettaglio |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | L’operazione è stata completata correttamente. | |
| `0x01` | SUCCESS | NOOP | L’operazione è stata completata correttamente senza eseguire alcuna azione. | |

##### Avviso

| Codice | Livello | Categoria | Descrizione | Dettaglio |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | L’operazione è stata completata, ma il risultato potrebbe essere inatteso o indesiderato. | |
| `0x41` | WARNING | PARTIAL | L’operazione è stata completata, ma solo parzialmente. L’output potrebbe essere incompleto. | |
| `0x42` | WARNING | DEPRECATED | L’operazione è stata completata, ma ha usato una funzionalità o un comportamento deprecato. L’operazione potrebbe non funzionare più in futuro. | |

##### Errore

| Codice | Livello | Categoria | Descrizione | Dettaglio |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | L’operazione non è riuscita a causa di un errore recuperabile. | |
| `0x81` | ERROR | INVALID_ARGUMENT | L’operazione non è riuscita. Un argomento non era valido o era fuori intervallo. | L’indice dell’argomento non valido, a partire da 0 da sinistra a destra nella firma della funzione. |
| `0x82` | ERROR | INVALID_STATE | L’operazione non è riuscita. Il sistema si trova in uno stato incoerente, corrotto o altrimenti non valido. | |
| `0x83` | ERROR | MALFORMED_INPUT | L’operazione non è riuscita. Un input richiesto era malformato o conteneva dati non validi. | |
| `0x84` | ERROR | ACCESS_DENIED | L’operazione non è riuscita perché una risorsa richiesta ha negato l’accesso. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | L’operazione non è riuscita perché la funzionalità o il comportamento richiesto non è ancora implementato. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | L’operazione non è riuscita perché il sistema o la configurazione di destinazione non supporta la funzionalità richiesta. | |
| `0x87` | ERROR | TIMEOUT | L’operazione non è riuscita perché si è verificato un timeout richiesto prima del completamento. | |
| `0x88` | ERROR | NOT_FOUND | L’operazione non è riuscita perché una risorsa richiesta non esiste. | |
| `0x89` | ERROR | INTERRUPTED | L’operazione non è riuscita perché un evento esterno l’ha interrotta. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | L’operazione non è riuscita perché una dipendenza richiesta non è riuscita. | Il valore `STATUS_CODE` della dipendenza. I chiamanti sono incoraggiati, ma non obbligati, a identificare la dipendenza non riuscita tramite il campo `OP_CODE`. |
| `0x90` | ERROR | BUFFER_OVERFLOW | L’operazione non è riuscita. Un buffer era troppo piccolo per contenere i dati richiesti. | |
| `0x91` | ERROR | ALLOCATION_FAILED | L’operazione non è riuscita. Una richiesta di allocazione della memoria non ha avuto successo. | |
| `0xA0` | ERROR | IO_ERROR | L’operazione non è riuscita. Si è verificato un errore di I/O durante l’operazione. | |

##### Fatale

| Codice | Livello | Categoria | Descrizione | Dettaglio |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | L’operazione non è riuscita a causa di un errore non recuperabile. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | L’operazione non è riuscita perché il sistema ha violato un invariante fondamentale, indicando un errore logico critico o una corruzione dei dati. | |

### Codice di contesto

Un codice di contesto è qualsiasi $(b_0,\dots,b_7)$ tale che per ogni $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Codice di contesto()

Un valore di codice di contesto rappresenta informazioni contestuali aggiuntive su un’operazione completata, come definito dall’operazione associata; deve essere zero quando il livello del codice di stato è $\mathrm{Success}$, ed è altrimenti definito dall’implementazione.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Codice di operazione

Un codice di operazione è qualsiasi $(b_0,\dots,b_7)$ tale che per ogni $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Codice di operazione()

Un valore di codice di operazione rappresenta l’operazione associata a un risultato. Il suo significato è definito dall’operazione corrispondente e dalla sua documentazione. I valori indefiniti sono considerati sconosciuti.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Codice di dettaglio

Un codice di dettaglio è qualsiasi $(b_0,\dots,b_7)$ tale che per ogni $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Codice di dettaglio()

Un valore di codice di dettaglio rappresenta informazioni aggiuntive su un’operazione completata; il suo significato è definito dal codice di stato, contesto o operazione associato, in quest’ordine, ed è altrimenti sconosciuto.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Risultato

> [!TIP]
>
> Un valore di risultato può essere rappresentato come intero a 32 bit. In ordine di byte big-endian, il valore appare come `0xSSCCOODD`, dove `SS`, `CC`, `OO` e `DD` corrispondono rispettivamente al codice di stato, al codice di contesto, al codice di operazione e al codice di dettaglio. In ordine di byte little-endian, lo stesso valore appare come `0xDDOOCCSS`. Può essere usato qualunque ordine dei byte, purché sia applicato in modo coerente e documentato.

Un risultato è qualsiasi $(b_0,\dots,b_{31})$ tale che per ogni $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

Un risultato è suddiviso in quattro byte ordinati:

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

dove $s$, $c$, $o$ e $d$ sono i componenti del risultato.

#### Risultato()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
