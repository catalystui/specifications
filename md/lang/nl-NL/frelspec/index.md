<!-- Deze vertaling is gegenereerd door ChatGPT en moet door een menselijke vertaler worden nagekeken. -->
<!-- Verwijder deze regels in een pull request nadat de vertaling is geverifieerd. -->

# FRELSPEC

<br/>

> **Specificatie van fundamentele relaties**<br/>
> Revisie 2.1<br/>
> 24 november 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Alle rechten voorbehouden.<br/>
> <br/>
> De hier gepresenteerde definities en concepten beschrijven fundamentele wiskundige constructies en mogen vrij worden geherformuleerd.

## Inleiding

De **Specificatie van fundamentele relaties (FRELSPEC)** legt de centrale relationele structuren vast die ten grondslag liggen aan het CatalystUI-ecosysteem. Het doel is een uniform begrip te bieden van de relaties tussen geheugen, collecties, bewerkingen en samengestelde structuren in documentatie, specificaties, implementaties en verificatiebeoordelingen, zodat consistentie, duidelijkheid en afstemming gewaarborgd zijn.

Door relaties tussen fundamentele concepten nauwkeurig en stabiel te definiëren biedt FRELSPEC een gemeenschappelijk referentiepunt voor specificaties op een hoger niveau, terwijl afzonderlijke implementaties hun eigen regels en gedrag kunnen bepalen. Ontwikkelaars, beoordelaars en implementeerders kunnen zo vanuit dezelfde basis bepalen of een taal, dienst, framework of systeem de relationele constructies kan weergeven die nodig zijn om aan de specificatie te voldoen.

> [!IMPORTANT]
>
> We drukken definities uit met een afgeleide vorm van de notatie van de [verzamelingenleer](https://en.wikipedia.org/wiki/Set_theory). Deze benadering levert precieze, ondubbelzinnige definities met behoud van duidelijkheid en beknoptheid. We structureren ze voor gemakkelijke raadpleging, heldere interpretatie en een consistente conceptuele hiërarchie.

## Inhoudsopgave

- [FRELSPEC](#frelspec)
  - [Inleiding](#inleiding)
  - [Inhoudsopgave](#inhoudsopgave)
  - [Revisies](#revisies)
    - [Revisie 2.1](#revisie-21)
    - [Revisie 2](#revisie-2)
  - [Geheugen](#geheugen)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Collecties](#collecties)
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
  - [Bewerkingen](#bewerkingen)
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
  - [Samengestelde structuren](#samengestelde-structuren)
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

## Revisies

### Revisie 2.1

**24 november 2026**

We hebben de definitie van File verfijnd om door metadata gestuurde gegevensresolutie vast te leggen en Stream opnieuw gedefinieerd als een onafhankelijk mechanisme voor sequentiële gegevensgeneratie of -opvraging. Hierdoor kunnen streams eindige of oneindige reeksen weergeven zonder andere collecties extra beperkingen op te leggen.

### Revisie 2

**21 november 2026**

We hebben inconsistenties vastgesteld in de weergave van geheugen en opgeslagen waarden met bytes en byte-arrays. We hebben Word vastgesteld als fundamentele geheugenrepresentatie en de relaties tussen Geheugen, Bewerkingen en Samengestelde structuren verenigd.

We hebben inconsistenties vastgesteld in array-indexering en de relaties tussen collecties. We hebben eindige, aaneengesloten indices gestandaardiseerd en de relaties tussen Array, File en Stream verduidelijkt.

We hebben redundanties en dubbelzinnigheden in uitvoerings- en compositierelaties vastgesteld. We hebben procedures, functies, dispatchers en objectrelaties verfijnd om deze op te lossen met behoud van implementatieonafhankelijkheid.

## Geheugen

### Word

Een woord is elke in het geheugen opgeslagen reeks bits $w \in \mathrm{Bit}^n$, zodanig dat $n \in \mathbb{N}^+$.

### Address

Een adres is elk woord $a \in A$, waarbij $A$ een verzameling woorden is, zodanig dat $a$ een locatie binnen een gespecificeerde geheugenstructuur uniek identificeert.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

Een pointer is elke functie $f_p : \{a\} \to B$ zodanig dat $a \in A$ een adres is en $B$ een verzameling woorden is, waarbij elke toepassing van $f_p$ het woord evalueert dat is opgeslagen op de door $a$ geïdentificeerde geheugenlocatie.

#### Pointer()

> Laat $f_m : A \to B$ een geheugenafbeelding zijn.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Een variabele is elke functie $f_v : \{k\} \to B$ zodanig dat $k$ een sleutel is en $B$ een verzameling woorden is, waarbij de variabele een pointer uitbreidt door een sleutel aan een adres te binden en het daar opgeslagen woord te evalueren.

#### Variable(k)

> Laat $f_b : \{k\} \to \{a\}$ de bindingsfunctie van de variabele zijn.
>
> Laat $f_p : \{a\} \to B$ een pointer zijn.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Een constante is elke variabele $f_c : \{k\} \to B$ zodanig dat $k$ een sleutel is en $B$ een verzameling woorden is, waarbij het aan $k$ gekoppelde woord na toewijzing niet kan worden gewijzigd.

#### Constant(k)

> Laat $b_0 \in B$ het aan $k$ toegewezen woord zijn.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ nadat $b_0$ is toegewezen.

## Collecties

### Set

Een verzameling is elke eindige, ongeordende collectie van verschillende woorden.

#### Set()

> Laat $B$ een verzameling woorden zijn.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

Een map is elke functie $f_m : K \to V$ zodanig dat $K$ een verzameling sleutels is en $V$ een verzameling waarden is, waarbij elke sleutel aan precies één waarde gekoppeld is.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Een array is elke functie $f_a : I \to V$ zodanig dat $I \subseteq \mathbb{N}$ een eindige, aaneengesloten verzameling gehele indices is en $V$ een verzameling woorden is, waarbij elke index precies één waarde identificeert.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Een bestand is elk tupel $(f_m,d)$ zodanig dat $d$ een array van woorden is en $f_m : I \times \{d\} \to \mathrm{Array}$ een metadatafunctie is die door een array van woorden wordt weergegeven, waarbij $I$ een eindige, aaneengesloten verzameling gehele indices is en $f_m$ bepaalt hoe gegevens uit $d$ worden opgelost.

#### File(i)

> Laat $(f_m,d)$ een bestand zijn.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

Een stream is elke functie $f_s$ zodanig dat elke toepassing van $f_s$ het volgende fragment $c$ in een eindige of oneindige reeks oplevert, waarbij $f_s$ een mechanisme voor sequentiële gegevensgeneratie of -opvraging vastlegt.

#### Stream()

> Laat $f_c : K \to C$ een fragmentresolutiefunctie zijn, waarbij $K \subseteq \mathbb{N}$ een aaneengesloten verzameling gehele indices is en $C$ een verzameling fragmenten is.
>
> Laat $k \in K$ de index van het volgende fragment zijn.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$, waarbij $k$ na elke toepassing wordt verhoogd.

## Bewerkingen

### Instruction

Een instructie is elk woord of eindig tupel van woorden $i \in B$ zodanig dat $B$ een verzameling woorden of eindige tupels van woorden is, waarbij elke instructie één uit te voeren computationele bewerking vertegenwoordigt.

### Procedure

Een procedure is elke variabele $f_{proc} : \{k\} \to B$ zodanig dat $f_{proc}(k)$ een array van instructies $f_a : I \to V$ vertegenwoordigt, waarbij uitvoering van de procedure elke instructie in indexvolgorde uitvoert.

#### Procedure(k)

> $\mathrm{Procedure}(k)$ is de uitvoering van elke $f_a(i)$ in oplopende volgorde van $i \in I$.

### Function

Een functie is elke procedure $f_{func} : \{k\} \to B$ waarvan de uitvoering een adres $a_r \in A$ retourneert dat het resulterende woord of het eerste woord van een array van woorden die het resultaat vertegenwoordigt identificeert.

#### Function(k)

> Laat $f_m : A \to B$ een geheugenafbeelding zijn, waarbij $a_r \in A$ het resulterende woord $r \in B$ identificeert.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## Threading

### Process

Een proces is elke begrensde uitvoeringsstroom die invoer aanneemt, een of meer procedures of functies uitvoert en uitvoer produceert, waarbij het proces een afzonderlijke transformatie-eenheid binnen een systeem vormt.

### Thread

Een thread is elke uitvoeringsstroom binnen een proces, die één pad biedt waarlangs procedures of functies van dat proces kunnen worden uitgevoerd.

#### Thread(p)

> Laat $p$ een proces zijn.
>
> Laat $(w_0, \dots, w_n)$ een eindig tupel zijn van procedures of functies die tot $p$ behoren.
>
> $\mathrm{Thread}(p)$ is de uitvoering van elke $w_j$ in oplopende volgorde van $j$ binnen $p$.

### Dispatcher

Een dispatcher is elk tupel $(t,W,f_d)$ zodanig dat $t$ een thread is, $W$ een verzameling als werk geaccepteerde procedures of functies is en $f_d$ een dispatchregel is die werk uit $W$ selecteert, waarbij de dispatcher geselecteerd werk op $t$ laat uitvoeren volgens die regel.

#### Dispatcher(t)

> Laat $t$ een thread zijn.
>
> Laat $W$ een verzameling door de dispatcher geaccepteerde procedures of functies zijn, waarbij $\forall w \in W$, $w$ een procedure of functie is.
>
> Laat $f_d : \mathcal{P}^+(W) \to W$ een dispatchregel zijn die werk selecteert uit een niet-lege deelverzameling van het geaccepteerde werk.
>
> $\mathrm{Dispatcher}(t)$ is de uitvoering van elke geselecteerde $f_d(W')$ op $t$, waarbij $W' \subseteq W$, $W' \neq \varnothing$ en $f_d(W') \in W'$.

## Samengestelde structuren

### Member

Een lid is elk element $m \in M$ zodanig dat $M$ een verzameling elementen is en $f_o : K \to M$ de ledenafbeelding van een object is, waarbij $m = f_o(k)$ voor een sleutel $k \in K$.

### Object

Een object is elk tupel $(a,K,f_o)$ zodanig dat $a \in A$ een adres is, $K$ een verzameling sleutels is en $f_o : K \to M$ een ledenafbeelding is, waarbij $M$ een verzameling elementen is, zodat het object een adresseerbare samengestelde structuur kan vertegenwoordigen waarvan de leden via $f_o$ aan sleutels worden toegewezen.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Een veld is elk tupel $(o,k,m)$ zodanig dat $o = (a,K,f_o)$ een object is, $k \in K$ een sleutel is en $m = f_o(k)$ een lid is, waarbij het veld één via een sleutel geïdentificeerd lid uit de ledenafbeelding van het object vertegenwoordigt.

#### Field(o,k)

> Laat $o = (a,K,f_o)$ een object zijn.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

Een methode is elk veld $(o,k,m)$ zodanig dat $m$ een procedure of functie is, waarbij de methode een uitvoerbaar lid van een object vertegenwoordigt dat via een sleutel geïdentificeerd is.

#### Method(o,k)

> Laat $(o,k,m)$ een veld zijn.
>
> $\mathrm{Method}(o,k) = (o,k,m)$, waarbij $m$ een procedure of functie is.

### Property

Een eigenschap is elk veld $(o,k,m)$ zodanig dat $m = (X,f_a)$ een accessorafbeelding is, $X = \{\mathrm{Get}, \mathrm{Set}\}$, en $f_a : X \to M$ elke accessor aan een lid koppelt, waarbij $f_a(\mathrm{Get})$ een functie en $f_a(\mathrm{Set})$ een procedure is, zodat de eigenschap zowel het opvraag- als toewijzingsgedrag van een via een sleutel geïdentificeerd lid kan definiëren.

#### Property(o,k)

> Laat $(o,k,m)$ een veld zijn, waarbij $m = (X,f_a)$ een accessorafbeelding is.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> Laat $(o,k,(X,f_a))$ een eigenschap zijn.
>
> $\mathrm{Get}(o,k)$ is de toepassing van $f_a(\mathrm{Get})$.

#### Set(o,k)

> Laat $(o,k,(X,f_a))$ een eigenschap zijn.
>
> $\mathrm{Set}(o,k)$ is de toepassing van $f_a(\mathrm{Set})$.

### Structure

Een structuur (vaak afgekort tot `struct`) is elk object $s = (a,K,f_s)$ zodanig dat $K$ een eindige verzameling sleutels is en $f_s : K \to M$ een ledenafbeelding is waarvan de sleutels na toewijzing van de structuur niet kunnen veranderen, waarbij de structuur een gespecialiseerd object is met een vaste indeling van via sleutels geïdentificeerde leden.

#### Structure(s,k)

> Laat $s = (a,K,f_s)$ een structuur zijn.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Een klasse is elk object $c = (a_c,K_c,f_c)$ zodanig dat $K_c$ een eindige verzameling sleutels is en $f_c : K_c \to M$ een afbeelding van ledendefinities is, waarbij de klasse een gespecialiseerd object is waarvan de via sleutels geïdentificeerde leden de ledenindeling voor het produceren van andere objecten definiëren.

#### Class(c,a)

> Laat $c = (a_c,K_c,f_c)$ een klasse zijn.
>
> Laat $a \in A$ een adres zijn dat is toegewezen aan een uit $c$ geproduceerd object.
>
> Laat $f_o : K_c \to M$ een ledenafbeelding zijn volgens de definities van $f_c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

Een interface is elk object $r = (a_r,K_r,f_r)$ zodanig dat $K_r$ een eindige verzameling sleutels is en $f_r : K_r \to M$ een afbeelding van ledenvereisten is, waarbij de interface een gespecialiseerd object is waarvan de via sleutels geïdentificeerde leden bepalen welke leden een ander object moet bieden.

#### Interface(r,o)

> Laat $r = (a_r,K_r,f_r)$ een interface zijn.
>
> Laat $o = (a,K,f_o)$ een object zijn.
>
> Laat $f_v : M \times M \to \{0,1\}$ een validatieregel zijn die bepaalt of een lid aan de vereisten van een ander lid voldoet.
>
> $\mathrm{Interface}(r,o)$ geldt wanneer $K_r \subseteq K$ en $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$.
