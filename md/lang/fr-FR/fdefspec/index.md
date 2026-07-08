<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->
<!-- Supprimez ces lignes dans une pull request une fois la traduction vérifiée. -->

# FDEFSPEC

<br/>

> **Spécification des définitions fondamentales**<br/>
> Révision 1<br/>
> 23 mars 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Tous droits réservés.<br/>
> <br/>
> Les définitions et concepts présentés ici décrivent des constructions mathématiques fondamentales et peuvent être reformulés librement.

## Introduction

La **Foundational Definitions Specification (FDEFSPEC)** établit les concepts et la terminologie de base qui soutiennent l’écosystème CatalystUI. Son objectif est de fournir une compréhension unifiée de ces concepts dans la documentation, les spécifications, les implémentations et les examens de vérification, afin d’assurer cohérence, clarté et alignement.

En définissant les termes clés et leurs relations sous une forme précise et stable, FDEFSPEC fournit un point de référence commun pour les spécifications de plus haut niveau. Cela permet aux développeurs, examinateurs et implémenteurs de raisonner à partir de la même base lorsqu’ils déterminent si un langage, un service, un framework ou un système peut être considéré comme conforme à la spécification.

> [!IMPORTANT]
>
> Nous exprimons les définitions au moyen d’une forme dérivée de la notation de la [théorie des ensembles](https://en.wikipedia.org/wiki/Set_theory). Cette approche fournit des définitions précises et non ambiguës tout en conservant clarté et concision. Nous structurons ces définitions afin de faciliter la référence, l’interprétation et une hiérarchie conceptuelle cohérente.

## Table des matières

- [FDEFSPEC](#fdefspec)
  - [Introduction](#introduction)
  - [Table des matières](#table-of-contents)
  - [Numériques](#numerics)
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
  - [Encodage de texte](#text-encoding)
    - [Text Encoding](#text-encoding-1)
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
  - [État d’opération](#operation-status)
    - [Status Code](#status-code)
      - [Status Code()](#status-code-1)
      - [Status Code Level()](#status-code-level)
      - [Status Code Definition()](#status-code-definition)
        - [Success](#success)
        - [Warning](#warning)
        - [Error](#error)
        - [Fatal](#fatal)
    - [Context Code](#context-code)
      - [Context Code()](#context-code-1)
    - [Operation Code](#operation-code)
      - [Operation Code()](#operation-code-1)
    - [Detail Code](#detail-code)
      - [Detail Code()](#detail-code-1)
    - [Result](#result)
      - [Result()](#result-1)

## Numériques

### Bit

Un bit est tout $b \in \{0,1\}$.

### Nibble

Un nibble est tout $(b_0,\dots,b_3)$ tel que, pour tout $i \in \{0,\dots,3\}$, $b_i \in \mathrm{Bit}$.

#### Nibble()

> $\mathrm{Nibble}(b_0,\dots,b_3) = \sum_{i=0}^{3} b_i \cdot 2^{3-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^4 - 1 \,\}$

### Byte

Un octet est tout $(b_0,\dots,b_7)$ tel que, pour tout $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Byte()

> $\mathrm{Byte}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^8 - 1 \,\}$

#### SByte()

> $\mathrm{SByte}(b_0,\dots,b_7) = -b_0 \cdot 2^7 + \sum_{i=1}^{7} b_i \cdot  2^{7-i} \in \{\, n \in \mathbb{Z} : -2^7 \leq n \leq 2^7 - 1 \,\}$

### Short

Un short est tout $(b_0,\dots,b_{15})$ tel que, pour tout $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### Short()

> $\mathrm{Short}(b_0,\dots,b_{15}) = -b_0 \cdot  2^{15} + \sum_{i=1}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : -2^{15} \leq n \leq 2^{15} - 1 \,\}$

#### UShort()

> $\mathrm{UShort}(b_0,\dots,b_{15}) = \sum_{i=0}^{15} b_i \cdot 2^{15-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{16} - 1 \,\}$

### Int

Un entier est tout $(b_0,\dots,b_{31})$ tel que, pour tout $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Int()

> $\mathrm{Int}(b_0,\dots,b_{31}) = -b_0 \cdot 2^{31} + \sum_{i=1}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : -2^{31} \leq n \leq 2^{31} - 1 \,\}$

#### UInt()

> $\mathrm{UInt}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{32} - 1 \,\}$

### Long

Un long est tout $(b_0,\dots,b_{63})$ tel que, pour tout $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Long()

> $\mathrm{Long}(b_0,\dots,b_{63}) = -b_0 \cdot 2^{63} + \sum_{i=1}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : -2^{63} \leq n \leq 2^{63} - 1 \,\}$

#### ULong()

> $\mathrm{ULong}(b_0,\dots,b_{63}) = \sum_{i=0}^{63} b_i \cdot 2^{63-i} \in \{\, n \in \mathbb{Z} : 0 \leq n \leq 2^{64} - 1 \,\}$

### Single

Un single est tout $(b_0,\dots,b_{31})$ tel que, pour tout $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

#### Single()

La définition suivante est conforme à la norme IEEE 754 pour la représentation des nombres à virgule flottante en simple précision. Elle définit comment une séquence binaire de 32 bits est interprétée comme un nombre à virgule flottante, y compris les cas spéciaux zéro, infini et NaN (Not a Number).

> Soit $s = b_0$
>
> Soit $e = \sum_{i=1}^{8} b_i 2^{8-i}$
>
> Soit $f = \sum_{i=9}^{31} b_i 2^{31-i}$
>
> $\displaystyle \mathrm{Single}(b_0,\dots,b_{31}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{23}}\right) \cdot 2^{e-127} & 0 < e < 255 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{23}}\right) \cdot 2^{-126} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 255 \land f = 0 \\ \quad\mathrm{NaN} & e = 255 \land f \neq 0 \end{cases}$

### Double

Un double est tout $(b_0,\dots,b_{63})$ tel que, pour tout $i \in \{0,\dots,63\}$, $b_i \in \mathrm{Bit}$.

#### Double()

La définition suivante est conforme à la norme IEEE 754 pour la représentation des nombres à virgule flottante en double précision. Elle définit comment une séquence binaire de 64 bits est interprétée comme un nombre à virgule flottante, y compris les cas spéciaux zéro, infini et NaN (Not a Number).

> Soit $s = b_0$
>
> Soit $e = \sum_{i=1}^{11} b_i 2^{11-i}$
>
> Soit $f = \sum_{i=12}^{63} b_i 2^{63-i}$
>
> $\displaystyle \mathrm{Double}(b_0,\dots,b_{63}) = \begin{cases} \quad(-1)^s \cdot \left(1 + \dfrac{f}{2^{52}}\right) \cdot 2^{e-1023} & 0 < e < 2047 \\ \quad(-1)^s \cdot \left(\dfrac{f}{2^{52}}\right) \cdot 2^{-1022} & e = 0 \land f \neq 0 \\ \quad(-1)^s \cdot 0 & e = 0 \land f = 0 \\ \quad(-1)^s \cdot \infty & e = 2047 \land f = 0 \\ \quad\mathrm{NaN} & e = 2047 \land f \neq 0 \end{cases}$

### Boolean

Un booléen est tout $b \in \{0,1\}$.

#### Boolean()

> $\displaystyle \mathrm{Boolean}(b) = \begin{cases} \quad\mathrm{False} & b = 0 \\ \quad\mathrm{True} & b = 1 \end{cases} \quad \text{where } b \in \mathrm{Bit}$

## Encodage de texte

### Encodage de texte

Un encodage de texte est défini comme l’ensemble suivant :

$\displaystyle \quad\mathrm{Text\ Encoding} = \{\, \mathrm{Unknown}, \mathrm{ASCII}, \mathrm{CP1252}, \mathrm{UTF\text{-}8}, \mathrm{UTF\text{-}16LE} \,\}$

#### Encodage de texte()

> $\displaystyle \mathrm{Text\ Encoding}(e) = \begin{cases} \mathrm{Nibble}(0,0,0,0) & e = \mathrm{Unknown} \\ \mathrm{Nibble}(0,0,0,1) & e = \mathrm{ASCII} \\ \mathrm{Nibble}(0,0,1,0) & e = \mathrm{CP1252} \\ \mathrm{Nibble}(0,0,1,1) & e = \mathrm{UTF\text{-}8} \\ \mathrm{Nibble}(0,1,0,0) & e = \mathrm{UTF\text{-}16LE} \end{cases}$

### Codepoint

Un point de code Unicode est tout $e \in \mathbb{Z}$ tel que $0 \leq e \leq 0x10FFFF$.

#### Codepoint()

> $\mathrm{Codepoint}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$

### ASCII Code Unit

Une unité de code ASCII est tout $(b_0,\dots,b_6)$ tel que, pour tout $i \in \{0,\dots,6\}$, $b_i \in \mathrm{Bit}$.

#### ASCII Code Unit()

Il est courant de représenter une unité de code ASCII comme un octet en ajoutant un bit zéro en tête, pour des raisons de performance et de compatibilité. Dans ces cas, l’unité de code ASCII est représentée ainsi :

> $\mathrm{ASCII\ Code\ Unit}(0,b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Sinon :

> $\mathrm{ASCII\ Code\ Unit}(b_0,\dots,b_6) = \sum_{i=0}^{6} b_i \cdot 2^{6-i}$

Dans le cadre de ce théorème, les deux définitions sont des représentations acceptables d’une unité de code ASCII. Par cohérence, nous utiliserons la première définition lorsque les unités de code ASCII sont représentées comme des octets, et la seconde lorsqu’elles sont représentées comme des séquences de 7 bits.

#### ASCII()

ASCII est un tuple fini terminé par nul $(u_0, \dots, u_k, u_{k+1})$ tel que :

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is an ASCII code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{ASCII\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{ASCII\ Code\ Unit}(u_{k+1}) = 0$

On dit que la séquence est terminée par nul.

### CP1252 Code Unit

Une unité de code CP1252 est tout $(b_0,\dots,b_7)$ tel que, pour tout $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### CP1252 Code Unit()

> $\mathrm{CP1252\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### CP1252()

CP1252 est un tuple fini terminé par nul $(u_0, \dots, u_k, u_{k+1})$ tel que :

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a CP1252 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{CP1252\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{CP1252\ Code\ Unit}(u_{k+1}) = 0$

On dit que la séquence est terminée par nul.

### UTF-8 Code Unit

Une unité de code UTF-8 est tout $(b_0,\dots,b_7)$ tel que, pour tout $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### UTF-8 Code Unit()

> $\mathrm{UTF\text{-}8\ Code\ Unit}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### UTF-8()

UTF-8 est un tuple fini terminé par nul $(u_0, \dots, u_k, u_{k+1})$ tel que :

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-8 code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}8\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}8\ Code\ Unit}(u_{k+1}) = 0$

On dit que la séquence est terminée par nul.

### UTF-16LE Code Unit

Une unité de code UTF-16LE est tout $(b_0,\dots,b_{15})$ tel que, pour tout $i \in \{0,\dots,15\}$, $b_i \in \mathrm{Bit}$.

#### UTF-16LE Code Unit()

> $\mathrm{UTF\text{-}16LE\ Code\ Unit}(b_0,\dots,b_{15}) = \left( \sum_{i=0}^{7} b_i \cdot 2^{i} \right) + \left( \sum_{i=8}^{15} b_i \cdot 2^{i-8} \right) \cdot 2^{8}$

#### UTF-16LE()

UTF-16LE est un tuple fini terminé par nul $(u_0, \dots, u_k, u_{k+1})$ tel que :

- $\forall i \in \{0,\dots,k+1\}$, $u_i$ is a UTF-16LE code unit
- $\forall i \in \{0,\dots,k\}$, $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_i) \neq 0$
- $\mathrm{UTF\text{-}16LE\ Code\ Unit}(u_{k+1}) = 0$

On dit que la séquence est terminée par nul.

## État d’opération

### Code d’état

Un code d’état est tout $(b_0,\dots,b_7)$ tel que, pour tout $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

Un niveau de code d’état est défini comme l’ensemble suivant :

$\displaystyle \quad\mathrm{Status\ Code\ Level} = \{\, \mathrm{Success}, \mathrm{Warning}, \mathrm{Error}, \mathrm{Fatal} \,\}$

#### Code d’état()

> $\mathrm{Status\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

#### Niveau de code d’état()

L’ensemble des valeurs de code d’état est l’intervalle $[0, 255]$, partitionné en quatre niveaux :

> Soit $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
>
> $\displaystyle \mathrm{Status\ Code\ Level}(s) = \begin{cases} \quad\mathrm{Success} & 0 \leq s \leq 63 \\ \quad\mathrm{Warning} & 64 \leq s \leq 127 \\ \quad\mathrm{Error} & 128 \leq s \leq 191 \\ \quad\mathrm{Fatal} & 192 \leq s \leq 255 \end{cases}$

#### Définition de code d’état()

Tous les codes d’état ont des définitions explicites. Tout code d’état non inclus dans la liste suivante est réservé pour un usage futur, et son sens est indéfini. Le niveau d’un code d’état est déterminé par $\mathrm{Status\ Code\ Level}(s)$.

Dans la liste suivante, l’entrée $s$ est représentée sous forme hexadécimale pour faciliter la lecture. Chaque code d’état défini précise son niveau, sa catégorie, sa sous-catégorie, sa description et son détail correspondants, le cas échéant.

Cette liste peut être étendue à mesure que de nouveaux codes d’état sont définis. Tout nouveau code d’état défini ne doit pas entrer en conflit avec les codes existants et doit avoir un sens clairement documenté.

Pour transmettre des informations non représentées par un code d’état défini, il convient d’utiliser le code de contexte, le code d’opération ou le code de détail.

##### Succès

| Code | Niveau | Catégorie | Description | Détail |
| --- | --- | --- | --- | --- |
| `0x00` | SUCCESS | NONE | L’opération s’est terminée avec succès. | |
| `0x01` | SUCCESS | NOOP | L’opération s’est terminée avec succès sans effectuer d’action. | |

##### Avertissement

| Code | Niveau | Catégorie | Description | Détail |
| --- | --- | --- | --- | --- |
| `0x40` | WARNING | NONE | L’opération s’est terminée, mais le résultat peut être inattendu ou indésirable. | |
| `0x41` | WARNING | PARTIAL | L’opération s’est terminée, mais seulement partiellement. La sortie peut être incomplète. | |
| `0x42` | WARNING | DEPRECATED | L’opération s’est terminée, mais elle a utilisé une fonctionnalité ou un comportement obsolète. L’opération pourrait ne plus fonctionner à l’avenir. | |

##### Erreur

| Code | Niveau | Catégorie | Description | Détail |
| --- | --- | --- | --- | --- |
| `0x80` | ERROR | NONE | L’opération a échoué à cause d’une erreur récupérable. | |
| `0x81` | ERROR | INVALID_ARGUMENT | L’opération a échoué. Un argument était invalide ou hors plage. | L’indice de l’argument invalide, en commençant à 0 de gauche à droite dans la signature de la fonction. |
| `0x82` | ERROR | INVALID_STATE | L’opération a échoué. Le système est dans un état incohérent, corrompu ou autrement invalide. | |
| `0x83` | ERROR | MALFORMED_INPUT | L’opération a échoué. Une entrée requise était mal formée ou contenait des données invalides. | |
| `0x84` | ERROR | ACCESS_DENIED | L’opération a échoué parce qu’une ressource requise a refusé l’accès. | |
| `0x85` | ERROR | NOT_IMPLEMENTED | L’opération a échoué parce que la fonctionnalité ou le comportement demandé n’est pas encore implémenté. | |
| `0x86` | ERROR | SYSTEM_NOT_SUPPORTED | L’opération a échoué parce que le système ou la configuration cible ne prend pas en charge la fonctionnalité demandée. | |
| `0x87` | ERROR | TIMEOUT | L’opération a échoué parce qu’un délai d’expiration requis est survenu avant la fin. | |
| `0x88` | ERROR | NOT_FOUND | L’opération a échoué parce qu’une ressource requise n’existe pas. | |
| `0x89` | ERROR | INTERRUPTED | L’opération a échoué parce qu’un événement externe l’a interrompue. | |
| `0x8A` | ERROR | DEPENDENCY_FAILURE | L’opération a échoué parce qu’une dépendance requise a échoué. | La valeur `STATUS_CODE` de la dépendance. Les appelants sont encouragés, sans y être obligés, à identifier la dépendance en échec via le champ `OP_CODE`. |
| `0x90` | ERROR | BUFFER_OVERFLOW | L’opération a échoué. Un tampon était trop petit pour contenir les données requises. | |
| `0x91` | ERROR | ALLOCATION_FAILED | L’opération a échoué. Une demande d’allocation mémoire a échoué. | |
| `0xA0` | ERROR | IO_ERROR | L’opération a échoué. Une erreur d’E/S s’est produite pendant l’opération. | |

##### Fatal

| Code | Niveau | Catégorie | Description | Détail |
| --- | --- | --- | --- | --- |
| `0xC0` | FATAL | NONE | L’opération a échoué à cause d’une erreur irrécupérable. | |
| `0xC1` | FATAL | INVARIANT_VIOLATION | L’opération a échoué parce que le système a violé un invariant fondamental, indiquant une erreur logique critique ou une corruption de données. | |

### Code de contexte

A context code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Code de contexte()

Une valeur de code de contexte représente des informations contextuelles supplémentaires sur une opération terminée, telles que définies par l’opération associée ; elle doit valoir zéro lorsque le niveau du code d’état est $\mathrm{Success}$, et elle est sinon définie par l’implémentation.

> $\mathrm{Context\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Code d’opération

An operation code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Code d’opération()

Une valeur de code d’opération représente l’opération associée à un résultat. Son sens est défini par l’opération correspondante et sa documentation. Les valeurs non définies sont considérées comme inconnues.

> $\mathrm{Operation\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Code de détail

A detail code is any $(b_0,\dots,b_7)$ such that for all $i \in \{0,\dots,7\}$, $b_i \in \mathrm{Bit}$.

#### Code de détail()

Une valeur de code de détail représente des informations supplémentaires sur une opération terminée ; son sens est défini par le code d’état, de contexte ou d’opération associé (dans cet ordre), et il est sinon inconnu.

> $\mathrm{Detail\ Code}(b_0,\dots,b_7) = \sum_{i=0}^{7} b_i \cdot 2^{7-i}$

### Résultat

> [!TIP]
>
> Une valeur de résultat peut être représentée comme un entier de 32 bits. En ordre d’octets big-endian, la valeur apparaît sous la forme `0xSSCCOODD`, où `SS`, `CC`, `OO` et `DD` correspondent respectivement au code d’état, au code de contexte, au code d’opération et au code de détail. En ordre d’octets little-endian, la même valeur apparaît sous la forme `0xDDOOCCSS`. L’un ou l’autre ordre d’octets peut être utilisé, à condition d’être appliqué de façon cohérente et documentée.

Un résultat est tout $(b_0,\dots,b_{31})$ tel que, pour tout $i \in \{0,\dots,31\}$, $b_i \in \mathrm{Bit}$.

Un résultat est divisé en quatre octets ordonnés :

- $s = \mathrm{Status\ Code}(b_0,\dots,b_7)$
- $c = \mathrm{Context\ Code}(b_8,\dots,b_{15})$
- $o = \mathrm{Operation\ Code}(b_{16},\dots,b_{23})$
- $d = \mathrm{Detail\ Code}(b_{24},\dots,b_{31})$

où $s$, $c$, $o$ et $d$ sont les composants du résultat.

#### Résultat()

> $\mathrm{Result}(b_0,\dots,b_{31}) = \sum_{i=0}^{31} b_i \cdot 2^{31-i}$
