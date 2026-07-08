<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->
<!-- Supprimez ces lignes dans une pull request une fois la traduction vérifiée. -->

# FRELSPEC

<br/>

> **Spécification des relations fondamentales**<br/>
> Révision 1<br/>
> 7 juillet 2026<br/>
> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Tous droits réservés.<br/>
> <br/>
> Les définitions et concepts présentés ici décrivent des constructions mathématiques fondamentales et peuvent être reformulés librement.

## Introduction

La **Foundational Relations Specification (FRELSPEC)** établit les structures relationnelles de base qui soutiennent l’écosystème CatalystUI. Son objectif est de fournir une compréhension unifiée de la manière dont les valeurs, la mémoire, les opérations et les composites sont associés dans la documentation, les spécifications, les implémentations et les examens de vérification, afin d’assurer cohérence, clarté et alignement.

En définissant les relations entre les concepts fondamentaux sous une forme précise et stable, FRELSPEC fournit un point de référence commun pour les spécifications de plus haut niveau. Cela permet aux développeurs, examinateurs et implémenteurs de raisonner à partir de la même base lorsqu’ils déterminent si un langage, un service, un framework ou un système peut représenter les constructions relationnelles nécessaires pour être considéré comme conforme à la spécification.

> [!IMPORTANT]
>
> Nous exprimons les définitions au moyen d’une forme dérivée de la notation de la [théorie des ensembles](https://en.wikipedia.org/wiki/Set_theory). Cette approche fournit des définitions précises et non ambiguës tout en conservant clarté et concision. Nous structurons ces définitions afin de faciliter la référence, l’interprétation et une hiérarchie conceptuelle cohérente.

## Table des matières

- [FRELSPEC](#frelspec)
  - [Introduction](#introduction)
  - [Table des matières](#table-of-contents)
  - [Collections](#collections)
    - [Set](#set)
    - [Map](#map)
      - [Map(k)](#mapk)
    - [Array](#array)
      - [Array(i)](#arrayi)
    - [File](#file)
      - [File(i)](#filei)
    - [Stream](#stream)
      - [Stream()](#stream-1)
  - [Mémoire](#memory)
    - [Address](#address)
    - [Pointer](#pointer)
      - [Pointer()](#pointer-1)
    - [Variable](#variable)
      - [Variable(k)](#variablek)
    - [Constant](#constant)
      - [Constant(k)](#constantk)
  - [Opérations](#operations)
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
  - [Composites](#composites)
    - [Member](#member)
    - [Object](#object)
      - [Object(k)](#objectk)
    - [Field](#field)
      - [Field(k)](#fieldk)
    - [Method](#method)
      - [Method(k)](#methodk)
    - [Property](#property)
      - [Property(k)](#propertyk)
      - [Get(k)](#getk)
      - [Set(k)](#setk)
    - [Structure](#structure)
      - [Structure(k)](#structurek)
    - [Class](#class)
      - [Class(a)](#classa)
    - [Interface](#interface)
      - [Interface(o)](#interfaceo)

## Collections

### Ensemble

Un ensemble est toute collection d’éléments distincts.

### Map

Une map est toute fonction $f_m : K \to V$ telle que $K$ est un ensemble de clés et $V$ est un ensemble de valeurs.

#### Map(k)

> $\forall k \in K, \exists v \in V : f_m(k) = v$

### Tableau

Un tableau est toute fonction $f_a : I \to V$ telle que $I \subset \mathbb{N}$, $I$ est un ensemble fini et contigu d’entiers, et $V$ est un ensemble de valeurs.

#### Tableau(i)

> $\forall i \in I, \exists v \in V : f_a(i) = v$

### Fichier

Un fichier est toute fonction $f_f : I \to B$ telle que $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ est un ensemble fini et contigu d’entiers et $B$ est un ensemble d’octets, où $f_f$ provient d’un mécanisme de stockage persistant des données.

#### Fichier(i)

$\forall i \in I, \exists b \in B : f_f(i) = b$

### Flux

Un flux est toute fonction $f_s$ telle que chaque application de $f_s$ produit le fragment suivant $f_c : I \to B$ dans une séquence d’octets, où $I = \{ x \in \mathbb{Z} : m \leq x \leq n \}$ est un ensemble fini et contigu d’entiers, $B$ est un ensemble d’octets, et $f_s$ provient d’un mécanisme de génération ou de récupération séquentielle de données.

#### Flux()

> Soit $c_k : I_k \to B$ le fragment renvoyé par la $k$-ième application de $f_s$.
>
> $\forall k \in \mathbb{N}, f_s() = c_k$ lors de la $k$-ième application.

## Mémoire

### Adresse

Une adresse est tout élément $a \in A$ tel que $A$ est un ensemble d’adresses, où chaque adresse $a$ identifie de manière unique un emplacement dans une structure de mémoire.

### Pointeur

Un pointeur est toute fonction $f_p : \{a\} \to B$ telle que $a \in A$ est une adresse et $B$ est un ensemble de tableaux d’octets, où chaque application de $f_p$ évalue le tableau d’octets stocké à l’emplacement mémoire identifié par son adresse liée.

#### Pointeur()

> Soit $f_m : A \to B$ une map mémoire.
>
> $\exists b \in B : f_p(a) = f_m(a) = b$

### Variable

Une variable est toute fonction $f_v : \{k\} \to B$ telle que $k$ est une clé et $B$ est un ensemble de tableaux d’octets, où la variable étend un pointeur en liant une clé à une adresse et en évaluant le tableau d’octets stocké à l’emplacement mémoire identifié par cette adresse.

#### Variable(k)

> Soit $f_b : \{k\} \to \{a\}$ la fonction de liaison de la variable.
>
> Soit $f_p : \{a\} \to B$ un pointeur.
>
> $\exists b \in B : f_v(k) = f_p(f_b(k)) = b$

### Constante

Une constante est toute variable $f_c : \{k\} \to B$ telle que $k$ est une clé et $B$ est un ensemble de tableaux d’octets, où le tableau d’octets associé à $k$ ne peut pas être modifié après son affectation.

#### Constante(k)

> Soit $b_0 \in B$ le tableau d’octets affecté à $k$.
>
> $\forall b \in B,\ f_c(k) = b \implies b = b_0$ après l’affectation de $b_0$.


## Opérations

### Instruction

Une instruction est tout tableau d’octets $i \in B$ tel que $B$ est un ensemble de tableaux d’octets, où chaque instruction représente une opération de calcul unique à exécuter.

### Procédure

Une procédure est toute variable $f_{proc} : \{k\} \to B$ telle que $k$ est une clé et $B$ est un ensemble de tableaux d’octets, où chaque application de la procédure évalue le tableau d’octets associé à $k$ comme une séquence finie ordonnée d’instructions et exécute ces instructions dans l’ordre représenté sans définir de valeur renvoyée.

#### Procédure(k)

> Soit $b \in B$ tel que $f_{proc}(k) = b$.
>
> Soit $(i_0,\dots,i_n)$ la séquence finie ordonnée d’instructions représentée par $b$, où $\forall j \in \{0,\dots,n\}, i_j$ est une instruction.
>
> $\mathrm{Procedure}(k)$ est l’exécution de chaque $i_j$ dans l’ordre croissant de $j$.

### Fonction

Une fonction est toute procédure $f_{func} : \{k\} \to B$ telle que $k$ est une clé et $B$ est un ensemble de tableaux d’octets, où chaque application de la fonction évalue le tableau d’octets associé à $k$ comme une séquence finie ordonnée d’instructions, exécute ces instructions dans l’ordre représenté puis, une fois l’exécution terminée, affecte un tableau d’octets résultant à une adresse en mémoire pouvant être évaluée comme la valeur renvoyée par la fonction.

#### Fonction(k)

> Soit $b \in B$ tel que $f_{func}(k) = b$.
>
> Soit $(i_0,\dots,i_n)$ la séquence finie ordonnée d’instructions représentée par $b$, où $\forall j \in \{0,\dots,n\}, i_j$ est une instruction.
>
> Soit $a_r \in A$ une adresse affectée après la fin de l’exécution.
>
> Soit $f_m : A \to B$ une map mémoire.
>
> $\mathrm{Function}(k)$ est l’exécution de chaque $i_j$ dans l’ordre croissant de $j$, où $\exists b_r \in B : f_m(a_r) = b_r$ après la fin de l’exécution.
>
> $\mathrm{Function}(k) = b_r$

## Threading

### Processus

Un processus est tout flux d’exécution borné qui accepte une entrée, exécute une ou plusieurs instructions et produit une sortie, où le processus représente une unité distincte de transformation au sein d’un système.

### Thread

Un thread est tout flux d’exécution contenu dans un processus, où le thread fournit un chemin par lequel les séquences ordonnées d’instructions appartenant à ce processus peuvent être exécutées.

#### Thread(p)

> Soit $p$ un processus.
>
> Soit $(i_0,\dots,i_n)$ une séquence finie ordonnée d’instructions appartenant à $p$.
>
> $\mathrm{Thread}(p)$ est l’exécution de chaque $i_j$ dans l’ordre croissant de $j$ au sein de $p$.

### Répartiteur

Un répartiteur est tout tuple $(t,W,f_d)$ tel que $t$ est un thread, $W$ est un ensemble de procédures ou de fonctions acceptées comme travail, et $f_d$ est une règle de répartition qui sélectionne du travail dans $W$, où le répartiteur fait exécuter le travail sélectionné sur $t$ selon la règle de répartition.

#### Répartiteur(t)

> Soit $t$ un thread.
>
> Soit $W$ un ensemble de procédures ou de fonctions acceptées par le répartiteur, où $\forall w \in W$, $w$ est une procédure ou une fonction.
>
> Soit $f_d : \mathcal{P}(W) \to W$ une règle de répartition qui sélectionne du travail dans un sous-ensemble non vide de travail accepté.
>
> $\mathrm{Dispatcher}(t)$ est l’exécution de chaque $f_d(W')$ sélectionné sur $t$, où $W' \subseteq W$ et $W' \neq \varnothing$.

## Composites

### Membre

Un membre est tout élément $m \in M$ tel que $M$ est un ensemble de membres, où un membre est une valeur pouvant être affectée à une clé dans la map de membres d’un objet.

### Objet

Un objet est tout tuple $(a,K,f_o)$ tel que $a \in A$ est une adresse, $K$ est un ensemble de clés, et $f_o : K \to M$ est une map de membres, où $M$ est un ensemble de membres, ce qui permet à l’objet de représenter un composite adressable dont les membres sont affectés à des clés via $f_o$.

#### Objet(k)

> $\forall k \in K,\ \exists m \in M : f_o(k) = m$

### Champ

Un champ est tout tuple $(o,k,m)$ tel que $o = (a,K,f_o)$ est un objet, $k \in K$ est une clé, $m \in M$ est un membre, et $f_o(k) = m$, où le champ représente un membre à clé résolu à partir de la map de membres d’un objet.

#### Champ(k)

> Soit $o = (a,K,f_o)$ un objet.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Field}(o,k) = (o,k,f_o(k)) = (o,k,m)$

### Méthode

Une méthode est tout champ $(o,k,m)$ tel que $m$ est une procédure ou une fonction, où la méthode représente un membre exécutable à clé d’un objet.

#### Méthode(k)

> Soit $o = (a,K,f_o)$ un objet.
>
> Soit $k \in K$ une clé.
>
> Soit $m \in M$ un membre tel que $f_o(k) = m$.
>
> $\mathrm{Method}(o,k) = (o,k,m)$ lorsque $m$ est une procédure ou une fonction.

### Propriété

Une propriété est tout champ $(o,k,m)$ tel que $m = (A,f_a)$ est une map d’accesseurs, $A = \{ \mathrm{Get}, \mathrm{Set} \}$, et $f_a : A \to M$ associe chaque accesseur à un membre, où $f_a(\mathrm{Get})$ est une fonction et $f_a(\mathrm{Set})$ est une procédure, permettant à la propriété de définir à la fois le comportement de récupération et d’affectation d’un membre à clé.

#### Propriété(k)

> Soit $(o,k,m)$ un champ.
>
> Soit $m = (A,f_a)$ une map d’accesseurs.
>
> Soit $A = \{ \mathrm{Get}, \mathrm{Set} \}$.
>
> $\exists g \in M : f_a(\mathrm{Get}) = g$, où $g$ est une fonction.
>
> $\exists s \in M : f_a(\mathrm{Set}) = s$, où $s$ est une procédure.
>
> $\mathrm{Property}(o,k) = (o,k,(A,f_a))$

#### Get(k)

> Soit $(o,k,(A,f_a))$ une propriété.
>
> Soit $g = f_a(\mathrm{Get})$.
>
> $\mathrm{Get}(k)$ est l’application de $g$.

#### Set(k)

> Soit $(o,k,(A,f_a))$ une propriété.
>
> Soit $s = f_a(\mathrm{Set})$.
>
> $\mathrm{Set}(k)$ est l’application de $s$.

### Structure

Une structure (souvent abrégée en `struct`) est tout objet $s = (a,K,f_s)$ tel que $K$ est un ensemble fini de clés et $f_s : K \to M$ est une map de membres qui ne peut pas être modifiée après l’affectation de la struct, où la struct est un objet spécialisé dont la disposition des membres à clé est fixe.

#### Structure(k)

> Soit $s = (a,K,f_s)$ une structure.
>
> $\forall k \in K,\ \exists m \in M : \mathrm{Structure}(s,k) = f_s(k) = m$

### Classe

Une classe est tout objet $c = (a_c,K_c,f_c)$ tel que $K_c$ est un ensemble fini de clés et $f_c : K_c \to M$ est une map de définition de membres, où la classe est un objet spécialisé dont les membres à clé définissent la disposition de membres utilisée pour produire d’autres objets.

#### Classe(a)

> Soit $c = (a_c,K_c,f_c)$ une classe.
>
> Soit $a \in A$ une adresse affectée à un objet produit à partir de $c$.
>
> $\mathrm{Class}(c,a) = (a,K_c,f_c)$

### Interface

Une interface est tout objet $r = (a_r,K_r,f_r)$ tel que $K_r$ est un ensemble fini de clés et $f_r : K_r \to M$ est une map d’exigences de membres, où l’interface est un objet spécialisé dont les membres à clé définissent les membres devant être fournis par un autre objet.

#### Interface(o)

> Soit $r = (a_r,K_r,f_r)$ une interface.
>
> Soit $o = (a,K,f_o)$ un objet.
>
> $\mathrm{Interface}(r,o)$ est vraie lorsque $\forall k \in K_r,\ \exists m \in M : f_o(k) = m$
