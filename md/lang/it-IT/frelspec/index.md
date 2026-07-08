<!-- Questa traduzione è stata generata da ChatGPT e deve essere revisionata da un traduttore umano. -->
<!-- Rimuovere queste righe in una pull request dopo che la traduzione è stata verificata. -->

# FRELSPEC

<br/>

> **Specifica delle relazioni fondamentali**<br/>
> Revisione 1<br/>
> 7 luglio 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Tutti i diritti riservati.<br/>
> <br/>
> Le definizioni e i concetti presentati qui descrivono costrutti matematici fondamentali e possono essere riespressi liberamente.

## Introduzione

La **Specifica delle relazioni fondamentali (FRELSPEC)** stabilisce le strutture relazionali di base che sostengono l’ecosistema CatalystUI. Il suo scopo è fornire una comprensione unificata di come valori, memoria, operazioni e compositi siano associati attraverso documentazione, specifiche, implementazioni ed esami di verifica, assicurando coerenza, chiarezza e allineamento.

Definendo le relazioni tra concetti fondamentali in una forma precisa e stabile, FRELSPEC fornisce un punto di riferimento comune per specifiche di livello superiore. Questo consente a sviluppatori, revisori e implementatori di ragionare dalla stessa base quando determinano se un linguaggio, servizio, framework o sistema possa rappresentare i costrutti relazionali richiesti per essere considerato conforme alla specifica.

> [!IMPORTANT]
>
> Esprimiamo le definizioni usando una forma derivata della notazione della [teoria degli insiemi](https://en.wikipedia.org/wiki/Set_theory). Questo approccio fornisce definizioni precise e non ambigue mantenendo chiarezza e concisione. Strutturiamo queste definizioni per supportare un riferimento semplice, un’interpretazione chiara e una gerarchia concettuale coerente.

## Sommario

- [FRELSPEC](#frelspec)
  - [Introduction](#introduction)
  - [Sommario](#table-of-contents)
  - [Collezioni](#collections)
    - [Insieme](#set)
    - [Mappa](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [Memoria](#memory)
    - [Indirizzo](#address)
    - [Puntatore](#pointer)
      - [Pointer()](#pointer-1)
    - [Variabile](#variable)
      - [Variable(k)](#variablek)
    - [Costante](#constant)
      - [Constant(k)](#constantk)
  - [Operazioni](#operations)
    - [Istruzione](#instruction)
    - [Procedura](#procedure)
      - [Procedure(k)](#procedurek)
    - [Funzione](#function)
      - [Function(k)](#functionk)
  - [Threading](#threading)
    - [Processo](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Compositi](#composites)
    - [Membro](#member)
    - [Oggetto](#object)
      - [Object(k)](#objectk)
    - [Campo](#field)
      - [Field(k)](#fieldk)
    - [Metodo](#method)
      - [Method(k)](#methodk)
    - [Proprietà](#property)
      - [Property(k)](#propertyk)
      - [Get(k)](#getk)
      - [Set(k)](#setk)
    - [Struttura](#structure)
      - [Structure(k)](#structurek)
    - [Classe](#class)
      - [Class(a)](#classa)
    - [Interfaccia](#interface)
      - [Interface(o)](#interfaceo)

## Collezioni

### Insieme

Un insieme è qualsiasi collezione di elementi distinti.

### Mappa

Una mappa è qualsiasi funzione $f_m : K \to V$ tale che $K$ sia un insieme di chiavi e $V$ sia un insieme di valori.

#### Mappa(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Un array è qualsiasi funzione $f_a : I \to V$ tale che $I \subset \mathbb{N}$, $I$ sia un insieme finito e contiguo di interi, e $V$ sia un insieme di valori.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Un file è qualsiasi funzione $f_f : I \to B$ tale che $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ sia un insieme finito e contiguo di interi e $b$ sia un insieme di byte, dove $f_f$ ha origine da un meccanismo di archiviazione persistente dei dati.

#### File(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Stream

Uno stream è qualsiasi funzione $f_s$ tale che ogni applicazione di $f_s$ produca il chunk successivo $f_c : I \to B$ in una sequenza di byte, dove $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ è un insieme finito e contiguo di interi, $B$ è un insieme di byte e $f_s$ ha origine da un meccanismo di generazione o recupero sequenziale dei dati.

#### Stream()

> Sia $c_k : I_k \to B$ il chunk restituito dalla $k$-esima applicazione di $f_s$.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ alla $k$-esima applicazione.

## Memoria

### Indirizzo

Un indirizzo è qualsiasi elemento $a \in A$ tale che $A$ sia un insieme di indirizzi, dove ogni indirizzo $a$ identifica univocamente una posizione in una struttura di memoria.

### Puntatore

Un puntatore è qualsiasi funzione $f_p : \{a\} \to B$ tale che $a \in A$ sia un indirizzo e $B$ sia un insieme di array di byte, dove ogni applicazione di $f_p$ valuta l’array di byte archiviato nella posizione di memoria identificata dal suo indirizzo associato.

#### Puntatore()

> Sia $f_m : A \to B$ una mappa di memoria.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variabile

Una variabile è qualsiasi funzione $f_v : \{k\} \to B$ tale che $k$ sia una chiave e $B$ sia un insieme di array di byte, dove la variabile estende un puntatore associando una chiave a un indirizzo e valutando l’array di byte archiviato nella posizione di memoria identificata da quell’indirizzo.

#### Variabile(k)

> Sia $f_b : \{k\} \to \{a\}$ la funzione di associazione della variabile.
>
> Sia $f_p : \{a\} \to B$ un puntatore.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Costante

Una costante è qualsiasi variabile $f_c : \{k\} \to B$ tale che $k$ sia una chiave e $B$ sia un insieme di array di byte, dove l’array di byte associato a $k$ non può essere modificato dopo l’assegnazione.

#### Costante(k)

> Sia $b_0 \in B$ l’array di byte assegnato a $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ dopo che $b_0$ è stato assegnato.


## Operazioni

### Istruzione

Un’istruzione è qualsiasi array di byte $i \in B$ tale che $B$ sia un insieme di array di byte, dove ogni istruzione rappresenta una singola operazione computazionale da eseguire.

### Procedura

Una procedura è qualsiasi variabile $f_{proc} : \{k\} \to B$ tale che $k$ sia una chiave e $B$ sia un insieme di array di byte, dove ogni applicazione della procedura valuta l’array di byte associato a $k$ come una sequenza finita e ordinata di istruzioni ed esegue tali istruzioni nell’ordine rappresentato senza definire un valore restituito.

#### Procedura(k)

> Sia $b \in B$ tale che $f_{proc}(k) = b$.
>
> Sia $(i_0,\dots,i_n)$ la sequenza finita e ordinata di istruzioni rappresentata da $b$, dove $\forall j \in \{0,\dots,n\}, i_j$ è un’istruzione.
>
> $\mathrm{Procedure}(k)$ è l’esecuzione di ciascun $i_j$ in ordine crescente di $j$.

### Funzione

Una funzione è qualsiasi procedura $f_{func} : \{k\} \to B$ tale che $k$ sia una chiave e $B$ sia un insieme di array di byte, dove ogni applicazione della funzione valuta l’array di byte associato a $k$ come una sequenza finita e ordinata di istruzioni, esegue tali istruzioni nell’ordine rappresentato e, dopo il completamento dell’esecuzione, assegna un array di byte risultante a un indirizzo in memoria che può essere valutato come valore restituito dalla funzione.

#### Funzione(k)

> Sia $b \in B$ tale che $f_{func}(k) = b$.
>
> Sia $(i_0,\dots,i_n)$ la sequenza finita e ordinata di istruzioni rappresentata da $b$, dove $\forall j \in \{0,\dots,n\}, i_j$ è un’istruzione.
>
> Sia $a_r \in A$ un indirizzo assegnato dopo il completamento dell’esecuzione.
>
> Sia $f_m : A \to B$ una mappa di memoria.
>
> $\mathrm{Function}(k)$ è l’esecuzione di ciascun $i_j$ in ordine crescente di $j$, dove $\exists b_r \in B : f_m(a_r) = b_r$ dopo il completamento dell’esecuzione.
>
> $\mathrm{Function}(k) = b_r$

## Threading

### Processo

Un processo è qualsiasi flusso di esecuzione delimitato che accetta input, esegue una o più istruzioni e produce output, dove il processo rappresenta un’unità distinta di trasformazione all’interno di un sistema.

### Thread

Un thread è qualsiasi flusso di esecuzione contenuto all’interno di un processo, dove il thread fornisce un percorso tramite il quale possono essere eseguite sequenze ordinate di istruzioni appartenenti a quel processo.

#### Thread(p)

> Sia $p$ un processo.
>
> Sia $(i_0,\dots,i_n)$ una sequenza finita e ordinata di istruzioni appartenenti a $p$.
>
> $\mathrm{Thread}(p)$ è l’esecuzione di ciascun $i_j$ in ordine crescente di $j$ all’interno di $p$.

### Dispatcher

Un dispatcher è qualsiasi tupla $(t,W,f_d)$ tale che $t$ sia un thread, $W$ sia un insieme di procedure o funzioni accettate come lavoro e $f_d$ sia una regola di dispatch che seleziona lavoro da $W$, dove il dispatcher fa eseguire il lavoro selezionato su $t$ secondo la regola di dispatch.

#### Dispatcher(t)

> Sia $t$ un thread.
>
> Sia $W$ un insieme di procedure o funzioni accettate dal dispatcher, dove $\forall w \in W$, $w$ è una procedura o una funzione.
>
> Sia $f_d : \mathcal{P}(W) \to W$ una regola di dispatch che seleziona lavoro da un sottoinsieme non vuoto del lavoro accettato.
>
> $\mathrm{Dispatcher}(t)$ è l’esecuzione di ciascun $f_d(W')$ selezionato su $t$, dove $W' \subseteq W$ e $W' \neq \varnothing$.

## Compositi

### Membro

Un membro è qualsiasi elemento $m \in M$ tale che $M$ sia un insieme di membri, dove un membro è un valore che può essere assegnato a una chiave all’interno della mappa dei membri di un oggetto.

### Oggetto

Un oggetto è qualsiasi tupla $(a,K,f_o)$ tale che $a \in A$ sia un indirizzo, $K$ sia un insieme di chiavi e $f_o : K \to M$ sia una mappa dei membri, dove $M$ è un insieme di membri, consentendo all’oggetto di rappresentare un composito indirizzabile i cui membri sono assegnati a chiavi tramite $f_o$.

#### Oggetto(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Campo

Un campo è qualsiasi tupla $(o,k,m)$ tale che $o = (a,K,f_o)$ sia un oggetto, $k \in K$ sia una chiave, $m \in M$ sia un membro e $f_o(k) = m$, dove il campo rappresenta un membro con chiave risolto dalla mappa dei membri di un oggetto.

#### Campo(k)

> Sia $o = (a,K,f_o)$ un oggetto.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Metodo

Un metodo è qualsiasi campo $(o,k,m)$ tale che $m$ sia una procedura o una funzione, dove il metodo rappresenta un membro eseguibile con chiave di un oggetto.

#### Metodo(k)

> Sia $o = (a,K,f_o)$ un oggetto.
>
> Sia $k \in K$ una chiave.
>
> Sia $m \in M$ un membro tale che $f_o(k) = m$.
>
> $\mathrm{Method}(o,k) = (o,k,m)$ quando $m$ è una procedura o una funzione.

### Proprietà

Una proprietà è qualsiasi campo $(o,k,m)$ tale che $m = (A,f_a)$ sia una mappa di accessor, $A = \{ \mathrm{Get}, \mathrm{Set} \}$, e $f_a : A \to M$ mappi ogni accessor a un membro, dove $f_a(\mathrm{Get})$ è una funzione e $f_a(\mathrm{Set})$ è una procedura, consentendo alla proprietà di definire sia il comportamento di recupero sia quello di assegnazione di un membro con chiave.

#### Proprietà(k)

> Sia $(o,k,m)$ un campo.
>
> Sia $m = (A,f_a)$ una mappa di accessor.
>
> Sia $A = \{ \mathrm{Get}, \mathrm{Set} \}$.
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$, dove $g$ è una funzione.
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$, dove $s$ è una procedura.
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> Sia $(o,k,(A,f_a))$ una proprietà.
>
> Sia $g = f_a(\mathrm{Get})$.
>
> $\mathrm{Get}(k)$ è l’applicazione di $g$.

#### Insieme(k)

> Sia $(o,k,(A,f_a))$ una proprietà.
>
> Sia $s = f_a(\mathrm{Set})$.
>
> $\mathrm{Set}(k)$ è l’applicazione di $s$.

### Struttura

Una struttura (spesso abbreviata in `struct`) è qualsiasi oggetto $s = (a,K,f_s)$ tale che $K$ sia un insieme finito di chiavi e $f_s : K \to M$ sia una mappa dei membri che non può essere modificata dopo l’assegnazione della struct, dove la struct è un oggetto specializzato il cui layout dei membri con chiave è fisso.

#### Struttura(k)

> Sia $s = (a,K,f_s)$ una struttura.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Classe

Una classe è qualsiasi oggetto $c = (a_c,K_c,f_c)$ tale che $K_c$ sia un insieme finito di chiavi e $f_c : K_c \to M$ sia una mappa di definizione dei membri, dove la classe è un oggetto specializzato i cui membri con chiave definiscono il layout dei membri usato per produrre altri oggetti.

#### Classe(a)

> Sia $c = (a_c,K_c,f_c)$ una classe.
>
> Sia $a \in A$ un indirizzo assegnato a un oggetto prodotto da $c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interfaccia

Un’interfaccia è qualsiasi oggetto $r = (a_r,K_r,f_r)$ tale che $K_r$ sia un insieme finito di chiavi e $f_r : K_r \to M$ sia una mappa dei requisiti dei membri, dove l’interfaccia è un oggetto specializzato i cui membri con chiave definiscono i membri che devono essere forniti da un altro oggetto.

#### Interfaccia(o)

> Sia $r = (a_r,K_r,f_r)$ un’interfaccia.
>
> Sia $o = (a,K,f_o)$ un oggetto.
>
> $\mathrm{Interface}(r,o)$ holds when $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
