<!-- Questa traduzione è stata generata da ChatGPT e dovrebbe essere revisionata da un traduttore umano. -->
<!-- Rimuovere queste righe in una pull request dopo la verifica della traduzione. -->

# FRELSPEC

<br/>

> **Specifica delle relazioni fondamentali**<br/>
> Revisione 2.1<br/>
> 24 novembre 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Tutti i diritti riservati.<br/>
> <br/>
> Le definizioni e i concetti qui presentati descrivono costrutti matematici fondamentali e possono essere riformulati liberamente.

## Introduzione

La **Specifica delle relazioni fondamentali (FRELSPEC)** stabilisce le strutture relazionali centrali alla base dell'ecosistema CatalystUI. Il suo scopo è fornire una comprensione unificata delle relazioni tra memoria, collezioni, operazioni e compositi nella documentazione, nelle specifiche, nelle implementazioni e nelle revisioni di verifica, garantendo coerenza, chiarezza e allineamento.

Definendo le relazioni tra concetti fondamentali in forma precisa e stabile, FRELSPEC fornisce un riferimento comune per le specifiche di livello superiore, consentendo alle singole implementazioni di stabilire regole e comportamenti propri. Sviluppatori, revisori e implementatori possono così ragionare sulla stessa base per determinare se un linguaggio, servizio, framework o sistema possa rappresentare i costrutti relazionali richiesti per la conformità alla specifica.

> [!IMPORTANT]
>
> Esprimiamo le definizioni mediante una forma derivata della notazione della [teoria degli insiemi](https://en.wikipedia.org/wiki/Set_theory). Questo approccio fornisce definizioni precise e inequivocabili, mantenendo chiarezza e concisione. Le strutturiamo per facilitarne la consultazione, l'interpretazione chiara e una gerarchia concettuale coerente.

## Indice

- [FRELSPEC](#frelspec)
  - [Introduzione](#introduzione)
  - [Indice](#indice)
  - [Revisioni](#revisioni)
    - [Revisione 2.1](#revisione-21)
    - [Revisione 2](#revisione-2)
  - [Memoria](#memoria)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Collezioni](#collezioni)
    - [Set](#set)
      - [Set()](#set-1)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [Operazioni](#operazioni)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [Threading](#threading)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Compositi](#compositi)
    - [Member](#member)
    - [Object](#object)
      - [Object(k)](#objectk)
    - [Field](#field)
      - [Field(o,k)](#fieldok)
    - [Method](#method)
      - [Method(o,k)](#methodok)
    - [Property](#property)
      - [Property(o,k)](#propertyok)
      - [Get(o,k)](#getok)
      - [Set(o,k)](#setok)
    - [Structure](#structure)
      - [Structure(s,k)](#structuresk)
    - [Class](#class)
      - [Class(c,a)](#classca)
    - [Interface](#interface)
      - [Interface(r,o)](#interfacero)

## Revisioni

### Revisione 2.1

**24 novembre 2026**

Abbiamo affinato la definizione di File per stabilire la risoluzione dei dati governata dai metadati e ridefinito Stream come meccanismo indipendente di generazione o recupero sequenziale dei dati. Queste modifiche consentono ai flussi di rappresentare sequenze finite o infinite senza imporre ulteriori vincoli alle altre collezioni.

### Revisione 2

**21 novembre 2026**

Abbiamo individuato incoerenze nella rappresentazione della memoria e dei valori memorizzati mediante byte e array di byte. Abbiamo stabilito Word come rappresentazione fondamentale della memoria, unificando le relazioni tra Memoria, Operazioni e Compositi.

Abbiamo riscontrato incoerenze nell'indicizzazione degli array e nelle relazioni tra collezioni. Abbiamo standardizzato gli indici finiti e contigui e chiarito le relazioni tra Array, File e Stream.

Abbiamo individuato ridondanze e ambiguità nelle relazioni di esecuzione e composizione. Abbiamo affinato procedure, funzioni, dispatcher e relazioni tra oggetti per risolverle preservando l'indipendenza dall'implementazione.

## Memoria

### Word

Una parola è qualsiasi sequenza di bit $w \in \mathrm{Bit}^n$ memorizzata in memoria, tale che $n \in \mathbb{N}^+$.

### Address

Un indirizzo è qualsiasi parola $a \in A$, dove $A$ è un insieme di parole, tale che $a$ identifica univocamente una posizione in una struttura di memoria specificata.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

Un puntatore è qualsiasi funzione $f_p : \{a\} \to B$ tale che $a \in A$ è un indirizzo e $B$ è un insieme di parole, dove ogni applicazione di $f_p$ valuta la parola memorizzata nella posizione di memoria identificata da $a$.

#### Pointer()

> Sia $f_m : A \to B$ una mappa di memoria.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Una variabile è qualsiasi funzione $f_v : \{k\} \to B$ tale che $k$ è una chiave e $B$ è un insieme di parole, dove la variabile estende un puntatore associando una chiave a un indirizzo e valutando la parola memorizzata a tale indirizzo.

#### Variable(k)

> Sia $f_b : \{k\} \to \{a\}$ la funzione di associazione della variabile.
>
> Sia $f_p : \{a\} \to B$ un puntatore.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Una costante è qualsiasi variabile $f_c : \{k\} \to B$ tale che $k$ è una chiave e $B$ è un insieme di parole, dove la parola associata a $k$ non può essere modificata dopo l'assegnazione.

#### Constant(k)

> Sia $b_0 \in B$ la parola assegnata a $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ dopo l'assegnazione di $b_0$.

## Collezioni

### Set

Un insieme è qualsiasi collezione finita e non ordinata di parole distinte.

#### Set()

> Sia $B$ un insieme di parole.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

Una mappa è qualsiasi funzione $f_m : K \to V$ tale che $K$ è un insieme di chiavi e $V$ è un insieme di valori, dove ogni chiave è associata a esattamente un valore.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Un array è qualsiasi funzione $f_a : I \to V$ tale che $I \subseteq \mathbb{N}$ è un insieme finito e contiguo di indici interi e $V$ è un insieme di parole, dove ogni indice identifica esattamente un valore.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Un file è qualsiasi tupla $(f_m,d)$ tale che $d$ è un array di parole e $f_m : I \times \{d\} \to \mathrm{Array}$ è una funzione di metadati rappresentata da un array di parole, dove $I$ è un insieme finito e contiguo di indici interi e $f_m$ determina come vengono risolti i dati da $d$.

#### File(i)

> Sia $(f_m,d)$ un file.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

Un flusso è qualsiasi funzione $f_s$ tale che ogni applicazione di $f_s$ produce il frammento successivo $c$ in una sequenza finita o infinita, dove $f_s$ stabilisce un meccanismo di generazione o recupero sequenziale dei dati.

#### Stream()

> Sia $f_c : K \to C$ una funzione di risoluzione dei frammenti, dove $K \subseteq \mathbb{N}$ è un insieme contiguo di indici interi e $C$ è un insieme di frammenti.
>
> Sia $k \in K$ l'indice del frammento successivo.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$, avanzando $k$ dopo ogni applicazione.

## Operazioni

### Instruction

Un'istruzione è qualsiasi parola o tupla finita di parole $i \in B$ tale che $B$ è un insieme di parole o tuple finite di parole, dove ogni istruzione rappresenta una singola operazione computazionale da eseguire.

### Procedure

Una procedura è qualsiasi variabile $f_{proc} : \{k\} \to B$ tale che $f_{proc}(k)$ rappresenta un array di istruzioni $f_a : I \to V$, dove l'esecuzione della procedura esegue ogni istruzione nell'ordine degli indici.

#### Procedure(k)

> $\mathrm{Procedure}(k)$ è l'esecuzione di ogni $f_a(i)$ in ordine crescente di $i \in I$.

### Function

Una funzione è qualsiasi procedura $f_{func} : \{k\} \to B$ tale che la sua esecuzione restituisce un indirizzo $a_r \in A$ che identifica la parola risultante o la prima parola di un array di parole che rappresenta il risultato.

#### Function(k)

> Sia $f_m : A \to B$ una mappa di memoria, dove $a_r \in A$ identifica la parola risultante $r \in B$.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## Threading

### Process

Un processo è qualsiasi flusso di esecuzione delimitato che accetta input, esegue una o più procedure o funzioni e produce output, rappresentando un'unità distinta di trasformazione all'interno di un sistema.

### Thread

Un thread è qualsiasi flusso di esecuzione contenuto in un processo, che fornisce un percorso attraverso il quale possono essere eseguite procedure o funzioni appartenenti a quel processo.

#### Thread(p)

> Sia $p$ un processo.
>
> Sia $(w_0, \dots, w_n)$ una tupla finita di procedure o funzioni appartenenti a $p$.
>
> $\mathrm{Thread}(p)$ è l'esecuzione di ogni $w_j$ in ordine crescente di $j$ all'interno di $p$.

### Dispatcher

Un dispatcher è qualsiasi tupla $(t,W,f_d)$ tale che $t$ è un thread, $W$ è un insieme di procedure o funzioni accettate come lavoro e $f_d$ è una regola di dispatch che seleziona lavoro da $W$, dove il dispatcher fa eseguire il lavoro selezionato su $t$ secondo tale regola.

#### Dispatcher(t)

> Sia $t$ un thread.
>
> Sia $W$ un insieme di procedure o funzioni accettate dal dispatcher, dove $\forall w \in W$, $w$ è una procedura o funzione.
>
> Sia $f_d : \mathcal{P}^+(W) \to W$ una regola di dispatch che seleziona lavoro da un sottoinsieme non vuoto del lavoro accettato.
>
> $\mathrm{Dispatcher}(t)$ è l'esecuzione di ogni $f_d(W')$ selezionato su $t$, dove $W' \subseteq W$, $W' \neq \varnothing$ e $f_d(W') \in W'$.

## Compositi

### Member

Un membro è qualsiasi elemento $m \in M$ tale che $M$ è un insieme di elementi e $f_o : K \to M$ è la mappa dei membri di un oggetto, dove $m = f_o(k)$ per una chiave $k \in K$.

### Object

Un oggetto è qualsiasi tupla $(a,K,f_o)$ tale che $a \in A$ è un indirizzo, $K$ è un insieme di chiavi e $f_o : K \to M$ è una mappa dei membri, dove $M$ è un insieme di elementi, consentendo all'oggetto di rappresentare un composito indirizzabile i cui membri sono assegnati a chiavi tramite $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Un campo è qualsiasi tupla $(o,k,m)$ tale che $o = (a,K,f_o)$ è un oggetto, $k \in K$ è una chiave e $m = f_o(k)$ è un membro, dove il campo rappresenta un membro identificato da una chiave e risolto dalla mappa dei membri dell'oggetto.

#### Field(o,k)

> Sia $o = (a,K,f_o)$ un oggetto.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

Un metodo è qualsiasi campo $(o,k,m)$ tale che $m$ è una procedura o funzione, dove il metodo rappresenta un membro eseguibile di un oggetto identificato da una chiave.

#### Method(o,k)

> Sia $(o,k,m)$ un campo.
>
> $\mathrm{Method}(o,k) = (o,k,m)$, dove $m$ è una procedura o funzione.

### Property

Una proprietà è qualsiasi campo $(o,k,m)$ tale che $m = (X,f_a)$ è una mappa di accessori, $X = \{\mathrm{Get}, \mathrm{Set}\}$, e $f_a : X \to M$ associa ogni accessore a un membro, dove $f_a(\mathrm{Get})$ è una funzione e $f_a(\mathrm{Set})$ è una procedura, consentendo alla proprietà di definire sia il recupero sia l'assegnazione di un membro identificato da una chiave.

#### Property(o,k)

> Sia $(o,k,m)$ un campo, dove $m = (X,f_a)$ è una mappa di accessori.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> Sia $(o,k,(X,f_a))$ una proprietà.
>
> $\mathrm{Get}(o,k)$ è l'applicazione di $f_a(\mathrm{Get})$.

#### Set(o,k)

> Sia $(o,k,(X,f_a))$ una proprietà.
>
> $\mathrm{Set}(o,k)$ è l'applicazione di $f_a(\mathrm{Set})$.

### Structure

Una struttura (spesso abbreviata in `struct`) è qualsiasi oggetto $s = (a,K,f_s)$ tale che $K$ è un insieme finito di chiavi e $f_s : K \to M$ è una mappa dei membri le cui chiavi non possono essere modificate dopo l'assegnazione della struttura, che è un oggetto specializzato con disposizione fissa dei membri identificati da chiavi.

#### Structure(s,k)

> Sia $s = (a,K,f_s)$ una struttura.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Una classe è qualsiasi oggetto $c = (a_c,K_c,f_c)$ tale che $K_c$ è un insieme finito di chiavi e $f_c : K_c \to M$ è una mappa delle definizioni dei membri, dove la classe è un oggetto specializzato i cui membri identificati da chiavi definiscono la disposizione dei membri usata per produrre altri oggetti.

#### Class(c,a)

> Sia $c = (a_c,K_c,f_c)$ una classe.
>
> Sia $a \in A$ un indirizzo assegnato a un oggetto prodotto da $c$.
>
> Sia $f_o : K_c \to M$ una mappa dei membri conforme alle definizioni di $f_c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

Un'interfaccia è qualsiasi oggetto $r = (a_r,K_r,f_r)$ tale che $K_r$ è un insieme finito di chiavi e $f_r : K_r \to M$ è una mappa dei requisiti dei membri, dove l'interfaccia è un oggetto specializzato i cui membri identificati da chiavi definiscono i membri che un altro oggetto deve fornire.

#### Interface(r,o)

> Sia $r = (a_r,K_r,f_r)$ un'interfaccia.
>
> Sia $o = (a,K,f_o)$ un oggetto.
>
> Sia $f_v : M \times M \to \{0,1\}$ una regola di validazione che determina se un membro soddisfa i requisiti di un altro membro.
>
> $\mathrm{Interface}(r,o)$ vale quando $K_r \subseteq K$ e $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$.
