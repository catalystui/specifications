<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->
<!-- Supprimez ces lignes dans une pull request une fois la traduction vérifiée. -->

# FRELSPEC

<br/>

> **Spécification des relations fondamentales**<br/>
> Révision 2.1<br/>
> 24 novembre 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Tous droits réservés.<br/>
> <br/>
> Les définitions et concepts présentés ici décrivent des constructions mathématiques fondamentales et peuvent être reformulés librement.

## Introduction

La **Spécification des relations fondamentales (FRELSPEC)** établit les structures relationnelles centrales qui sous-tendent l’écosystème CatalystUI. Elle vise à fournir une compréhension unifiée des relations entre mémoire, collections, opérations et composites dans la documentation, les spécifications, les implémentations et les examens de vérification, afin d’assurer cohérence, clarté et alignement.

En définissant les relations entre concepts fondamentaux sous une forme précise et stable, FRELSPEC fournit un point de référence commun aux spécifications de niveau supérieur tout en permettant aux implémentations de définir leurs propres règles et comportements. Les développeurs, examinateurs et implémenteurs peuvent ainsi raisonner sur une base commune pour déterminer si un langage, un service, un framework ou un système peut représenter les constructions relationnelles requises pour être conforme à la spécification.

> [!IMPORTANT]
>
> Nous exprimons les définitions au moyen d’une forme dérivée de la notation de la [théorie des ensembles](https://en.wikipedia.org/wiki/Set_theory). Cette approche fournit des définitions précises et non ambiguës tout en préservant clarté et concision. Nous les structurons pour faciliter la consultation, l’interprétation claire et une hiérarchie conceptuelle cohérente.

## Table des matières

- [FRELSPEC](#frelspec)
  - [Introduction](#introduction)
  - [Table des matières](#table-des-matières)
  - [Révisions](#révisions)
    - [Révision 2.1](#révision-21)
    - [Révision 2](#révision-2)
  - [Mémoire](#mémoire)
    - [Word](#word)
    - [Address](#address)
      - [Address()](#address-1)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Collections](#collections)
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
  - [Opérations](#opérations)
    - [Instruction](#instruction)
    - [Procedure](#procedure)
      - [Procedure(k)](#procedurek)
    - [Function](#function)
      - [Function(k)](#functionk)
  - [Gestion des threads](#gestion-des-threads)
    - [Process](#process)
    - [Thread](#thread)
      - [Thread(p)](#threadp)
    - [Dispatcher](#dispatcher)
      - [Dispatcher(t)](#dispatchert)
  - [Composites](#composites)
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

## Révisions

### Révision 2.1

**24 novembre 2026**

Nous avons affiné la définition de File pour établir une résolution des données régie par les métadonnées et redéfini Stream comme un mécanisme indépendant de génération ou de récupération séquentielle des données. Ces changements permettent aux flux de représenter des séquences finies ou infinies sans imposer de contraintes supplémentaires aux autres collections.

### Révision 2

**21 novembre 2026**

Nous avons identifié des incohérences dans la représentation de la mémoire et des valeurs stockées par des octets et des tableaux d’octets. Nous avons établi Word comme représentation fondamentale de la mémoire, unifiant les relations entre Mémoire, Opérations et Composites.

Nous avons constaté des incohérences dans l’indexation des tableaux et les relations entre collections. Nous avons normalisé les indices finis et contigus et clarifié les relations entre Array, File et Stream.

Nous avons identifié des redondances et ambiguïtés dans les relations d’exécution et de composition. Nous avons affiné les procédures, fonctions, répartiteurs et relations entre objets pour les résoudre tout en préservant l’indépendance d’implémentation.

## Mémoire

### Word

Un mot est toute séquence de bits $w \in \mathrm{Bit}^n$ stockée en mémoire, telle que $n \in \mathbb{N}^+$.

### Address

Une adresse est tout mot $a \in A$, où $A$ est un ensemble de mots, tel que $a$ identifie de manière unique un emplacement dans une structure mémoire spécifiée.

#### Address()

> $\mathrm{Address}(b_0,\dots,b_{n-1}) = \sum_{i=0}^{n-1} b_i \cdot 2^{n-1-i} \in \{m \in \mathbb{Z} \mid 0 \leq m \leq 2^n-1\}$

### Pointer

Un pointeur est toute fonction $f_p : \{a\} \to B$ telle que $a \in A$ est une adresse et $B$ un ensemble de mots, chaque application de $f_p$ évaluant le mot stocké à l’emplacement mémoire identifié par $a$.

#### Pointer()

> Soit $f_m : A \to B$ une application mémoire.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Une variable est toute fonction $f_v : \{k\} \to B$ telle que $k$ est une clé et $B$ un ensemble de mots, la variable étendant un pointeur en liant une clé à une adresse et en évaluant le mot stocké à cette adresse.

#### Variable(k)

> Soit $f_b : \{k\} \to \{a\}$ la fonction de liaison de la variable.
>
> Soit $f_p : \{a\} \to B$ un pointeur.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constant

Une constante est toute variable $f_c : \{k\} \to B$ telle que $k$ est une clé et $B$ un ensemble de mots, le mot associé à $k$ ne pouvant être modifié après son affectation.

#### Constant(k)

> Soit $b_0 \in B$ le mot affecté à $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ après l’affectation de $b_0$.

## Collections

### Set

Un ensemble est toute collection finie et non ordonnée de mots distincts.

#### Set()

> Soit $B$ un ensemble de mots.
>
> $S \subseteq B, |S| \in \mathbb{N}_0$

### Map

Une application est toute fonction $f_m : K \to V$ telle que $K$ est un ensemble de clés et $V$ un ensemble de valeurs, chaque clé étant associée à exactement une valeur.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Array

Un tableau est toute fonction $f_a : I \to V$ telle que $I \subseteq \mathbb{N}$ est un ensemble fini et contigu d’indices entiers et $V$ un ensemble de mots, chaque indice identifiant exactement une valeur.

#### Array(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### File

Un fichier est tout tuple $(f_m,d)$ tel que $d$ est un tableau de mots et $f_m : I \times \{d\} \to \mathrm{Array}$ une fonction de métadonnées représentée par un tableau de mots, où $I$ est un ensemble fini et contigu d’indices entiers et $f_m$ détermine comment les données sont résolues à partir de $d$.

#### File(i)

> Soit $(f_m,d)$ un fichier.
>
> $\mathrm{File}(i) = f_m(i,d),\quad i \in I$

### Stream

Un flux est toute fonction $f_s$ telle que chaque application de $f_s$ produit le prochain fragment $c$ d’une séquence finie ou infinie, où $f_s$ établit un mécanisme de génération ou de récupération séquentielle des données.

#### Stream()

> Soit $f_c : K \to C$ une fonction de résolution des fragments, où $K \subseteq \mathbb{N}$ est un ensemble contigu d’indices entiers et $C$ un ensemble de fragments.
>
> Soit $k \in K$ l’indice du prochain fragment.
>
> $\mathrm{Stream}() = f_s() = f_c(k)$, en avançant $k$ après chaque application.

## Opérations

### Instruction

Une instruction est tout mot ou tuple fini de mots $i \in B$ tel que $B$ est un ensemble de mots ou de tuples finis de mots, chaque instruction représentant une unique opération de calcul à effectuer.

### Procedure

Une procédure est toute variable $f_{proc} : \{k\} \to B$ telle que $f_{proc}(k)$ représente un tableau d’instructions $f_a : I \to V$, l’exécution de la procédure effectuant chaque instruction dans l’ordre de ses indices.

#### Procedure(k)

> $\mathrm{Procedure}(k)$ est l’exécution de chaque $f_a(i)$ dans l’ordre croissant de $i \in I$.

### Function

Une fonction est toute procédure $f_{func} : \{k\} \to B$ telle que son exécution renvoie une adresse $a_r \in A$ identifiant le mot résultant ou le premier mot d’un tableau de mots représentant le résultat.

#### Function(k)

> Soit $f_m : A \to B$ une application mémoire, où $a_r \in A$ identifie le mot résultant $r \in B$.
>
> $\mathrm{Function}(k) = a_r, f_m(a_r) = r$

## Gestion des threads

### Process

Un processus est tout flux d’exécution borné qui accepte une entrée, exécute une ou plusieurs procédures ou fonctions et produit une sortie, le processus représentant une unité distincte de transformation au sein d’un système.

### Thread

Un thread est tout flux d’exécution contenu dans un processus, fournissant un chemin par lequel les procédures ou fonctions de ce processus peuvent être exécutées.

#### Thread(p)

> Soit $p$ un processus.
>
> Soit $(w_0, \dots, w_n)$ un tuple fini de procédures ou fonctions appartenant à $p$.
>
> $\mathrm{Thread}(p)$ est l’exécution de chaque $w_j$ dans l’ordre croissant de $j$ au sein de $p$.

### Dispatcher

Un répartiteur est tout tuple $(t,W,f_d)$ tel que $t$ est un thread, $W$ un ensemble de procédures ou fonctions acceptées comme travail et $f_d$ une règle de répartition sélectionnant du travail dans $W$, le répartiteur faisant exécuter le travail sélectionné sur $t$ selon cette règle.

#### Dispatcher(t)

> Soit $t$ un thread.
>
> Soit $W$ un ensemble de procédures ou fonctions acceptées par le répartiteur, où $\forall w \in W$, $w$ est une procédure ou fonction.
>
> Soit $f_d : \mathcal{P}^+(W) \to W$ une règle de répartition sélectionnant du travail dans un sous-ensemble non vide du travail accepté.
>
> $\mathrm{Dispatcher}(t)$ est l’exécution de chaque $f_d(W')$ sélectionné sur $t$, où $W' \subseteq W$, $W' \neq \varnothing$ et $f_d(W') \in W'$.

## Composites

### Member

Un membre est tout élément $m \in M$ tel que $M$ est un ensemble d’éléments et $f_o : K \to M$ l’application des membres d’un objet, où $m = f_o(k)$ pour une certaine clé $k \in K$.

### Object

Un objet est tout tuple $(a,K,f_o)$ tel que $a \in A$ est une adresse, $K$ un ensemble de clés et $f_o : K \to M$ une application des membres, où $M$ est un ensemble d’éléments, permettant à l’objet de représenter un composite adressable dont les membres sont associés aux clés par $f_o$.

#### Object(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Field

Un champ est tout tuple $(o,k,m)$ tel que $o = (a,K,f_o)$ est un objet, $k \in K$ une clé et $m = f_o(k)$ un membre, le champ représentant un membre identifié par une clé et résolu à partir de l’application des membres de l’objet.

#### Field(o,k)

> Soit $o = (a,K,f_o)$ un objet.
>
> $\mathrm{Field}(o,k) = (o,k,f_o(k)), k \in K$

### Method

Une méthode est tout champ $(o,k,m)$ tel que $m$ est une procédure ou une fonction, la méthode représentant un membre exécutable d’un objet identifié par une clé.

#### Method(o,k)

> Soit $(o,k,m)$ un champ.
>
> $\mathrm{Method}(o,k) = (o,k,m)$, où $m$ est une procédure ou une fonction.

### Property

Une propriété est tout champ $(o,k,m)$ tel que $m = (X,f_a)$ est une application d’accesseurs, $X = \{\mathrm{Get}, \mathrm{Set}\}$, et $f_a : X \to M$ associe chaque accesseur à un membre, où $f_a(\mathrm{Get})$ est une fonction et $f_a(\mathrm{Set})$ une procédure, permettant à la propriété de définir la récupération et l’affectation d’un membre identifié par une clé.

#### Property(o,k)

> Soit $(o,k,m)$ un champ, où $m = (X,f_a)$ est une application d’accesseurs.
>
> $\mathrm{Property}(o,k) = (o,k,m)$

#### Get(o,k)

> Soit $(o,k,(X,f_a))$ une propriété.
>
> $\mathrm{Get}(o,k)$ est l’application de $f_a(\mathrm{Get})$.

#### Set(o,k)

> Soit $(o,k,(X,f_a))$ une propriété.
>
> $\mathrm{Set}(o,k)$ est l’application de $f_a(\mathrm{Set})$.

### Structure

Une structure (souvent abrégée en `struct`) est tout objet $s = (a,K,f_s)$ tel que $K$ est un ensemble fini de clés et $f_s : K \to M$ une application des membres dont les clés ne peuvent être modifiées après l’affectation de la structure, celle-ci étant un objet spécialisé à disposition fixe de membres identifiés par des clés.

#### Structure(s,k)

> Soit $s = (a,K,f_s)$ une structure.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Class

Une classe est tout objet $c = (a_c,K_c,f_c)$ tel que $K_c$ est un ensemble fini de clés et $f_c : K_c \to M$ une application de définitions de membres, la classe étant un objet spécialisé dont les membres identifiés par des clés définissent la disposition des membres utilisée pour produire d’autres objets.

#### Class(c,a)

> Soit $c = (a_c,K_c,f_c)$ une classe.
>
> Soit $a \in A$ une adresse affectée à un objet produit à partir de $c$.
>
> Soit $f_o : K_c \to M$ une application des membres suivant les définitions de $f_c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_o)$

### Interface

Une interface est tout objet $r = (a_r,K_r,f_r)$ tel que $K_r$ est un ensemble fini de clés et $f_r : K_r \to M$ une application d’exigences de membres, l’interface étant un objet spécialisé dont les membres identifiés par des clés définissent ceux qu’un autre objet doit fournir.

#### Interface(r,o)

> Soit $r = (a_r,K_r,f_r)$ une interface.
>
> Soit $o = (a,K,f_o)$ un objet.
>
> Soit $f_v : M \times M \to \{0,1\}$ une règle de validation déterminant si un membre satisfait aux exigences d’un autre membre.
>
> $\mathrm{Interface}(r,o)$ est vérifié lorsque $K_r \subseteq K$ et $\forall k \in K_r,\ f_v(f_o(k),f_r(k)) = 1$.
