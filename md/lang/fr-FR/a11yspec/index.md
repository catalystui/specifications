<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->

<!-- Supprimez ces lignes dans une pull request après vérification de la traduction. -->

# A11YSPEC

<br/>

> **Spécification d’accessibilité**<br/>
> Révision 1<br/>
> 8 juillet 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> Tous droits réservés.<br/> <br/>
> Les définitions, exigences et concepts présentés ici décrivent une prise en charge pratique de l’accessibilité et peuvent être librement reformulés.

<a id="introduction"></a>

## Introduction

La **Spécification d’accessibilité (A11YSPEC)** établit les concepts, la terminologie et les exigences de base utilisés pour évaluer la prise en charge de l’accessibilité dans l’écosystème CatalystUI. Son objectif est de fournir une norme claire permettant de déterminer si un système, service, framework, application, bibliothèque ou implémentation demeure utilisable de manière significative lorsqu’une voie sensorielle primaire est indisponible.

L’accessibilité est importante parce qu’une interface utilisateur ne devrait pas dépendre entièrement d’un seul sens lorsque le même sens essentiel peut raisonnablement être communiqué par un autre. Un système peut être techniquement fonctionnel, mais si un utilisateur ne peut pas comprendre, parcourir, configurer ou utiliser son comportement essentiel sans la vue, le son ou le toucher individuellement, alors le système n’a pas fourni un accès raisonnable pour cette condition.

Cette spécification ne tente pas de vérifier chaque handicap possible, appareil, technologie d’assistance, condition médicale, exigence légale, norme régionale d’accessibilité ou cas d’usage spécialisé. Elle définit plutôt la base minimale d’accessibilité requise pour que les utilisateurs puissent accéder et utiliser de manière significative les parties essentielles d’un système lorsque l’un des trois sens primaires d’accessibilité est indisponible.

En termes plus simples, A11YSPEC pose trois questions principales :

1. Les utilisateurs peuvent-ils comprendre le système essentiel sans s’appuyer sur la vue ?
2. Les utilisateurs peuvent-ils comprendre le système essentiel sans s’appuyer sur le son ?
3. Les utilisateurs peuvent-ils utiliser le système essentiel sans s’appuyer sur le toucher ?

> [!IMPORTANT]
>
> A11YSPEC définit des exigences d’accessibilité pour la vérification. Elle ne remplace pas les normes légales d’accessibilité, les exigences de certification des plateformes ni les examens spécialisés des technologies d’assistance. Un système peut être conforme à A11YSPEC et nécessiter tout de même un examen supplémentaire pour d’autres normes d’accessibilité.

<a id="table-of-contents"></a>

## Table des matières

- [A11YSPEC](#a11yspec)
  - [Introduction](#introduction)
  - [Table des matières](#table-of-contents)
  - [Conformité](#conformance)
  - [Sens primaires d’accessibilité](#primary-accessibility-senses)
    - [Vue](#sight)
    - [Son](#sound)
    - [Toucher](#touch)
    - [Domaines sensoriels supplémentaires](#additional-sensory-domains)
  - [Cas d’accessibilité requis](#required-accessibility-cases)
  - [Fonctionnalité essentielle](#essential-functionality)
    - [Fonctionnalité essentielle](#essential-functionality-1)
    - [Fonctionnalité critique](#critical-functionality)
    - [Fonctionnalité non essentielle](#nonessential-functionality)
  - [Exigences d’accessibilité](#accessibility-requirements)
    - [Exigence d’accès essentiel](#essential-access-requirement)
    - [Exigence d’accès critique](#critical-access-requirement)
    - [Exigence d’accès alternatif](#alternate-access-requirement)
    - [Aucune dépendance à un seul sens](#no-single-sense-dependency)
  - [Vue indisponible](#sight-unavailable)
  - [Son indisponible](#sound-unavailable)
  - [Toucher indisponible](#touch-unavailable)
  - [Exigences d’implémentation](#implementation-requirements)
    - [Mécanisme d’accessibilité stable](#stable-accessibility-mechanism)
    - [Structure sémantique](#semantic-structure)
    - [Sortie alternative](#alternate-output)
    - [Entrée alternative](#alternate-input)
    - [Retour accessible](#accessible-feedback)
    - [Configuration accessible](#accessible-configuration)
  - [Vérification](#verification)
    - [Conforme à la spécification](#within-spec)
    - [Avertissements](#warnings)
    - [Échecs](#failures)
    - [Validité de la vérification](#verification-validity)

<a id="conformance"></a>

## Conformité

Un système est considéré comme conforme à A11YSPEC lorsqu’il satisfait aux exigences définies par ce document pour chaque cas d’accessibilité requis.

Un système conforme doit :

1. Demeurer raisonnablement utilisable lorsque la vue est indisponible.
2. Demeurer raisonnablement utilisable lorsque le son est indisponible.
3. Demeurer raisonnablement utilisable lorsque le toucher est indisponible.
4. Préserver l’accès à la fonctionnalité essentielle dans chaque cas d’accessibilité requis.
5. Préserver l’accès à toute la fonctionnalité critique dans chaque cas d’accessibilité requis.
6. Fournir des voies raisonnables d’accès alternatif lorsque le sens essentiel ou l’opération dépendrait autrement du sens indisponible.
7. Utiliser un mécanisme d’accessibilité stable approprié au système examiné.
8. Éviter de dépendre exclusivement d’un sens primaire pour la fonctionnalité essentielle.

Un système n’a pas besoin de fournir des expériences identiques sur chaque voie sensorielle. Une expérience non visuelle peut être plus lente qu’une expérience visuelle. Une expérience sans son peut nécessiter des sous-titres, des indicateurs visuels ou une confirmation haptique. Une expérience sans toucher peut nécessiter une navigation au clavier, des alternatives au pointeur, une interaction vocale, une interaction compatible avec des contacteurs ou une autre méthode sans toucher.

La vérification porte sur l’accès pratique à la fonctionnalité essentielle, et non sur une présentation identique.

<a id="primary-accessibility-senses"></a>

## Sens primaires d’accessibilité

Pour A11YSPEC, les trois sens primaires d’accessibilité sont **la vue**, **le son** et **le toucher**.

Ces sens sont primaires parce qu’ils sont les voies sensorielles les plus courantes dans l’interaction avec les interfaces utilisateur. Un système peut fournir une sortie par la vue, le son ou le toucher, et il peut recevoir une interaction par le toucher, le mouvement, la voix, la saisie au clavier, la saisie au pointeur, la saisie par contacteur ou une autre voie d’entrée disponible.

<a id="sight"></a>

### Vue

La vue est la voie sensorielle visuelle par laquelle un utilisateur perçoit une sortie visuelle.

La vue peut intervenir dans la perception de :

* texte
* couleur
* forme
* position
* disposition
* animation
* icônes
* images
* vidéo
* avertissements visuels
* indicateurs visuels d’état
* contrôles visibles

Un système dépend de la vue lorsque le sens essentiel ou l’opération exige que l’utilisateur perçoive visuellement l’information.

<a id="sound"></a>

### Son

Le son est la voie sensorielle auditive par laquelle un utilisateur perçoit une sortie audio.

Le son peut intervenir dans la perception de :

* instructions parlées
* alertes
* alarmes
* indices musicaux
* effets sonores
* invites audio
* descriptions audio
* indicateurs auditifs d’état
* confirmation parlée
* navigation parlée

Un système dépend du son lorsque le sens essentiel ou l’opération exige que l’utilisateur entende l’information.

<a id="touch"></a>

### Toucher

Le toucher est la voie sensorielle tactile par laquelle un utilisateur perçoit une sortie physique ou haptique, ainsi que la voie d’interaction physique par laquelle un utilisateur peut utiliser des contrôles par contact direct, pression, geste ou mouvement.

Le toucher peut intervenir dans la perception ou l’exécution de :

* gestes tactiles
* retour haptique
* vibration
* texture physique
* force
* pression
* contrôles uniquement tactiles
* boutons physiques
* manipulation directe
* interaction avec écran tactile
* actions de glisser-déposer
* actions de balayage

Un système dépend du toucher lorsque le sens essentiel ou l’opération exige une perception tactile ou une interaction fondée sur le toucher sans voie raisonnable d’entrée ou de sortie alternative.

<a id="additional-sensory-domains"></a>

### Domaines sensoriels supplémentaires

CatalystUI reconnaît également **le goût** et **l’odorat** comme domaines sensoriels.

Le goût et l’odorat peuvent être pris en compte pendant l’examen d’accessibilité lorsqu’ils sont utilisés de manière significative par le système. Ces sens sont inclusifs pour la vérification, ce qui signifie qu’ils peuvent renforcer ou soutenir un examen d’accessibilité lorsqu’ils fournissent un accès alternatif significatif ou un contexte supplémentaire.

Le goût et l’odorat ne sont actuellement pas exclusifs pour l’échec. Un système n’échoue pas à A11YSPEC simplement parce qu’il ne fournit pas d’interaction fondée sur le goût ou l’odorat.

A11YSPEC vise principalement à déterminer si le système demeure raisonnablement utilisable lorsque la vue, le son ou le toucher est individuellement indisponible.

<a id="required-accessibility-cases"></a>

## Cas d’accessibilité requis

Un système conforme doit être examiné selon chaque cas d’accessibilité requis.

| Sens indisponible | Comportement d’accessibilité requis |
| ----------------- | ----------------------------------------------------------------- |
| Vue               | Le système doit demeurer raisonnablement utilisable par le son et le toucher. |
| Son               | Le système doit demeurer raisonnablement utilisable par la vue et le toucher. |
| Toucher           | Le système doit demeurer raisonnablement utilisable par la vue et le son. |

Chaque cas est examiné individuellement.

Un système n’est pas tenu de demeurer pleinement utilisable lorsque plusieurs sens primaires sont indisponibles en même temps, sauf si cette condition est incluse dans le périmètre examiné.

Un système n’est pas tenu de fournir tous les aménagements possibles. Il doit fournir un accès raisonnable à la fonctionnalité essentielle dans chaque cas d’accessibilité requis.

<a id="essential-functionality"></a>

## Fonctionnalité essentielle

<a id="essential-functionality-1"></a>

### Fonctionnalité essentielle

La fonctionnalité essentielle est tout comportement, contenu, contrôle, sortie, entrée, flux de travail ou configuration dont un utilisateur a raisonnablement besoin pour comprendre, parcourir, configurer ou utiliser le comportement essentiel d’un système.

La fonctionnalité essentielle peut inclure :

* navigation principale
* flux de travail principaux
* contrôles requis
* avertissements importants
* erreurs importantes
* messages de confirmation requis
* accès au compte ou à la session
* paramètres et préférences
* configuration de la langue
* configuration de l’accessibilité
* instructions essentielles
* informations d’état destinées à l’utilisateur
* toute interaction requise pour une utilisation normale

Un système n’a pas besoin de rendre chaque fonction décorative, facultative, redondante ou non essentielle également disponible par chaque voie sensorielle. Cependant, l’utilisateur ne doit pas être empêché d’utiliser le système essentiel par le sens indisponible.

<a id="critical-functionality"></a>

### Fonctionnalité critique

La fonctionnalité critique est une fonctionnalité essentielle dont la perte d’accès peut empêcher une utilisation significative, créer une erreur grave ou amener l’utilisateur à prendre une décision importante sans en comprendre la conséquence.

La fonctionnalité critique peut inclure :

* paramètres d’accessibilité
* paramètres de langue
* avertissements d’action destructive
* avertissements de suppression de compte
* confirmations de paiement
* confirmations d’achat
* choix de confidentialité
* avertissements de sécurité
* invites de consentement
* instructions de sécurité requises
* instructions de configuration requises
* messages d’erreur requis
* accès à la session
* comportement d’arrêt d’urgence ou d’annulation
* navigation principale requise pour atteindre les paramètres d’accessibilité

La fonctionnalité critique doit demeurer accessible dans chaque cas d’accessibilité requis.

Un système peut échouer à A11YSPEC si une fonctionnalité critique dépend exclusivement du sens indisponible.

<a id="nonessential-functionality"></a>

### Fonctionnalité non essentielle

La fonctionnalité non essentielle est une fonctionnalité qui n’est pas raisonnablement requise pour qu’un utilisateur comprenne, parcoure, configure ou utilise le comportement essentiel d’un système.

La fonctionnalité non essentielle peut inclure :

* animation décorative
* effets facultatifs
* finition visuelle cosmétique
* effets sonores non essentiels
* effets haptiques redondants
* contenu marketing facultatif
* contenu de tutoriel facultatif
* comportement de diagnostic caché
* contrôles destinés aux développeurs
* fonctionnalités expérimentales hors du périmètre examiné

La fonctionnalité non essentielle peut être inaccessible dans un ou plusieurs cas d’accessibilité sans provoquer automatiquement un échec. Cependant, la fonctionnalité non essentielle ne doit pas être confondue avec la fonctionnalité essentielle simplement parce qu’elle est peu pratique à prendre en charge.

<a id="accessibility-requirements"></a>

## Exigences d’accessibilité

<a id="essential-access-requirement"></a>

### Exigence d’accès essentiel

Un système satisfait à l’exigence d’accès essentiel lorsque la fonctionnalité essentielle demeure raisonnablement compréhensible, navigable, configurable et utilisable dans chaque cas d’accessibilité requis.

L’expérience essentielle n’a pas besoin d’être identique dans tous les sens.

L’expérience essentielle doit demeurer utilisable de manière significative.

<a id="critical-access-requirement"></a>

### Exigence d’accès critique

Un système satisfait à l’exigence d’accès critique lorsque toute la fonctionnalité critique demeure accessible dans chaque cas d’accessibilité requis.

La fonctionnalité critique ne doit pas être cachée derrière une seule voie sensorielle requise.

Par exemple, un système ne devrait pas fournir une interface accessible pour l’usage ordinaire tout en laissant les avertissements de suppression de compte, les confirmations de paiement, les décisions de confidentialité ou les paramètres d’accessibilité dépendre uniquement de la vue, du son ou du toucher.

<a id="alternate-access-requirement"></a>

### Exigence d’accès alternatif

Un système satisfait à l’exigence d’accès alternatif lorsque le sens essentiel ou l’opération fourni par un sens primaire est aussi raisonnablement disponible par une autre voie sensorielle ou d’interaction lorsque ce sens est indisponible.

L’accès alternatif peut être fourni par :

* alternatives textuelles
* sous-titres
* transcriptions
* sortie parlée
* structure compatible avec les lecteurs d’écran
* navigation au clavier
* alternatives au pointeur
* interaction compatible avec des contacteurs
* contrôle vocal
* alertes visuelles
* retour haptique
* indicateurs de focus
* structure sémantique
* API de plateforme accessibles
* intégration d’accessibilité au niveau de l’appareil
* autre mécanisme stable approprié au système

La voie alternative n’a pas besoin de correspondre parfaitement à la voie originale. Elle doit préserver le sens essentiel et l’opération.

<a id="no-single-sense-dependency"></a>

### Aucune dépendance à un seul sens

Un système ne doit pas exiger un sens primaire comme seule voie vers la fonctionnalité essentielle.

Un système peut utiliser la vue, le son ou le toucher comme expérience principale. Cependant, lorsque ce sens est indisponible, l’utilisateur doit encore disposer d’une manière raisonnable de comprendre et d’utiliser le système essentiel par les voies sensorielles restantes.

Un système peut échouer à l’examen lorsque des informations ou interactions essentielles sont disponibles uniquement par :

* sens uniquement visuel
* sens uniquement audio
* sens uniquement tactile
* opération uniquement gestuelle
* confirmation uniquement haptique
* état indiqué uniquement par couleur
* alertes uniquement sonores
* instructions uniquement fondées sur la disposition
* guidage uniquement par texture physique

<a id="sight-unavailable"></a>

## Vue indisponible

Lorsque la vue est indisponible, le système doit demeurer raisonnablement utilisable par le son et le toucher.

Cela signifie que les informations visuelles essentielles doivent avoir une voie d’accès non visuelle significative.

Un système peut satisfaire à cette exigence par :

* sortie parlée
* structure compatible avec les lecteurs d’écran
* ordre de focus significatif
* accès au clavier
* contrôles tactiles
* confirmation haptique
* descriptions audio
* prise en charge de la synthèse vocale
* libellés sémantiques
* noms accessibles
* rôles accessibles
* informations d’état accessibles
* autre mécanisme non visuel raisonnable

Un système ne devrait pas dépendre exclusivement de :

* position visuelle
* couleur
* forme
* animation
* icônes
* disposition
* images
* vidéo
* avertissements uniquement visuels
* indicateurs d’état uniquement visuels

lorsque ces informations sont nécessaires pour comprendre ou utiliser une fonctionnalité essentielle.

Un système peut échouer à ce cas si un utilisateur ne peut pas raisonnablement parcourir, comprendre ou utiliser le système essentiel sans la vue.

<a id="sound-unavailable"></a>

## Son indisponible

Lorsque le son est indisponible, le système doit demeurer raisonnablement utilisable par la vue et le toucher.

Cela signifie que les informations auditives essentielles doivent avoir une voie d’accès non auditive significative.

Un système peut satisfaire à cette exigence par :

* sous-titres
* transcriptions
* alertes visuelles
* équivalents textuels
* indicateurs de progression
* messages d’état visibles
* retour haptique
* confirmation visuelle
* instructions écrites
* indicateurs symboliques
* autre mécanisme non auditif raisonnable

Un système ne devrait pas dépendre exclusivement de :

* effets sonores
* instructions parlées
* alertes
* alarmes
* indices musicaux
* invites uniquement audio
* confirmation parlée
* avertissements uniquement audio
* indicateurs d’état uniquement audio

lorsque ces informations sont nécessaires pour comprendre ou utiliser une fonctionnalité essentielle.

Un système peut échouer à ce cas si un utilisateur ne peut pas raisonnablement parcourir, comprendre ou utiliser le système essentiel sans le son.

<a id="touch-unavailable"></a>

## Toucher indisponible

Lorsque le toucher est indisponible, le système doit demeurer raisonnablement utilisable par la vue et le son.

Cela signifie que les informations tactiles essentielles et les opérations fondées sur le toucher doivent avoir une voie d’accès sans toucher significative.

Un système peut satisfaire à cette exigence par :

* navigation au clavier
* alternatives au pointeur
* contrôle vocal
* télécommandes
* interaction compatible avec le regard
* interaction compatible avec des contacteurs
* invites parlées
* confirmation visuelle
* systèmes de raccourcis accessibles
* palettes de commandes
* interaction fondée sur le focus
* autre mécanisme raisonnable sans toucher

Un système ne devrait pas dépendre exclusivement de :

* gestes tactiles
* retour haptique
* texture physique
* vibration
* force
* pression
* contrôles uniquement tactiles
* comportement uniquement par glissement
* comportement uniquement par balayage
* comportement uniquement par pincement
* manipulation directe sans alternatives

lorsque cette interaction est nécessaire pour comprendre ou utiliser une fonctionnalité essentielle.

Un système peut échouer à ce cas si un utilisateur ne peut pas raisonnablement parcourir, comprendre ou utiliser le système essentiel sans le toucher.

<a id="implementation-requirements"></a>

## Exigences d’implémentation

<a id="stable-accessibility-mechanism"></a>

### Mécanisme d’accessibilité stable

Un système conforme doit utiliser un mécanisme d’accessibilité stable approprié au système examiné.

Un mécanisme d’accessibilité stable devrait permettre au comportement d’accessibilité d’être maintenu, mis à jour, examiné et étendu sans dépendre d’un comportement fragile ou non documenté.

Un mécanisme d’accessibilité stable peut inclure :

* API d’accessibilité natives de la plateforme
* structure sémantique
* méthodes d’entrée alternatives
* méthodes de sortie alternatives
* prise en charge des technologies d’assistance
* paramètres d’accessibilité intégrés
* intégration au niveau de l’appareil
* interaction clavier documentée
* interaction vocale documentée
* interaction non visuelle documentée
* autre structure stable appropriée au système

Un système devrait éviter d’implémenter la fonctionnalité essentielle d’une manière qui empêche un accès alternatif raisonnable.

<a id="semantic-structure"></a>

### Structure sémantique

Un système conforme devrait fournir une structure sémantique lorsque le système présente un contenu ou des contrôles significatifs.

La structure sémantique peut inclure :

* noms
* rôles
* états
* relations
* ordre
* regroupement
* libellés
* descriptions
* comportement de focus
* objectif du contrôle
* hiérarchie du contenu

La structure sémantique est particulièrement importante lorsque la vue est indisponible, parce que les technologies d’assistance s’appuient souvent sur des informations sémantiques pour communiquer les interfaces visuelles par une sortie non visuelle.

Un système peut échouer à l’examen si des contrôles ou contenus essentiels ne peuvent pas être compris parce que leur structure, leurs libellés ou leurs relations ne sont pas disponibles par des voies d’accès alternatives.

<a id="alternate-output"></a>

### Sortie alternative

Un système conforme doit fournir une sortie alternative raisonnable lorsque le sens essentiel dépendrait autrement du sens indisponible.

La sortie alternative peut inclure :

* sortie visuelle pour les informations auditives
* sortie auditive pour les informations visuelles
* sortie tactile pour les informations visuelles ou auditives
* équivalents textuels
* sous-titres
* transcriptions
* descriptions parlées
* messages d’état visibles
* confirmation haptique
* autre voie de sortie appropriée

La sortie alternative doit préserver le sens essentiel.

<a id="alternate-input"></a>

### Entrée alternative

Un système conforme doit fournir une entrée alternative raisonnable lorsque l’opération essentielle dépendrait autrement uniquement du toucher.

L’entrée alternative peut inclure :

* saisie au clavier
* saisie au pointeur
* saisie vocale
* saisie par contacteur
* saisie à distance
* saisie compatible avec le regard
* saisie par commande
* autre voie d’entrée appropriée

L’entrée alternative n’a pas besoin d’être la méthode d’entrée la plus rapide ou la plus pratique. Elle doit être suffisante pour l’opération essentielle.

<a id="accessible-feedback"></a>

### Retour accessible

Un système conforme doit fournir un retour accessible pour les actions essentielles.

Le retour accessible peut inclure :

* confirmation qu’une action a eu lieu
* indication qu’une action a échoué
* informations de progression
* messages de validation
* messages d’avertissement
* messages d’erreur
* état d’achèvement
* sélection actuelle
* focus actuel
* mode actuel
* état actuel du système

Le retour ne doit pas dépendre exclusivement du sens indisponible dans le cas d’accessibilité concerné.

Par exemple, un carillon de réussite uniquement sonore n’est pas suffisant lorsque le son est indisponible. Un état d’erreur indiqué uniquement par la couleur n’est pas suffisant lorsque la vue est indisponible. Une confirmation uniquement par vibration n’est pas suffisante lorsque le toucher est indisponible.

<a id="accessible-configuration"></a>

### Configuration accessible

Un système conforme doit permettre aux utilisateurs d’atteindre et d’utiliser les paramètres d’accessibilité requis selon les mêmes exigences d’accessibilité définies par cette spécification.

Les paramètres d’accessibilité ne doivent pas être cachés derrière une voie inaccessible.

Par exemple, un mode compatible avec les lecteurs d’écran n’est pas suffisant si l’utilisateur doit d’abord parcourir un menu uniquement visuel et non libellé pour l’activer.

Un système peut échouer à l’examen si sa configuration d’accessibilité ne peut pas être atteinte ou utilisée dans la condition qu’elle est censée prendre en charge.

<a id="verification"></a>

## Vérification

<a id="within-spec"></a>

### Conforme à la spécification

Un système est considéré conforme à la spécification lorsque l’équipe CatalystUI a examiné le système et a jugé raisonnable de conclure qu’il satisfait à A11YSPEC.

Un système peut être conforme à la spécification lorsque :

* l’utilisation sans la vue demeure raisonnablement prise en charge
* l’utilisation sans le son demeure raisonnablement prise en charge
* l’utilisation sans le toucher demeure raisonnablement prise en charge
* la fonctionnalité essentielle demeure accessible dans chaque cas requis
* la fonctionnalité critique demeure accessible dans chaque cas requis
* les voies d’accès alternatives préservent le sens essentiel et l’opération
* les paramètres d’accessibilité, lorsqu’ils sont présents, peuvent être atteints et utilisés de façon accessible
* le système n’enferme pas la fonctionnalité essentielle derrière un seul sens requis
* le système utilise un mécanisme d’accessibilité stable approprié à sa conception

Un système peut être conforme à la spécification même si les expériences ne sont pas identiques sur toutes les voies sensorielles.

Un système peut être conforme à la spécification même si certaines fonctionnalités non essentielles ne sont pas également disponibles dans chaque cas d’accessibilité requis.

<a id="warnings"></a>

### Avertissements

Un avertissement peut être émis lorsqu’un système semble satisfaire à A11YSPEC mais contient des préoccupations qui devraient être documentées.

Les avertissements peuvent inclure :

* contenu mineur non essentiel indisponible dans un cas d’accessibilité
* voies d’accès alternatives plus lentes mais utilisables
* sous-titres ou transcriptions imparfaits mais compréhensibles
* navigation au clavier limitée mais fonctionnelle
* prise en charge des lecteurs d’écran limitée mais fonctionnelle
* préoccupations mineures d’ordre de focus qui ne bloquent pas l’usage essentiel
* indices visuels, auditifs ou tactiles redondants manquants sur une voie
* paramètres d’accessibilité utilisables mais difficiles à trouver
* prise en charge des technologies d’assistance qui fonctionne mais pourrait être plus claire
* flux de travail facultatifs qui ne sont pas également accessibles

Les avertissements n’empêchent pas nécessairement la vérification.

<a id="failures"></a>

### Échecs

Un échec se produit lorsqu’un système ne satisfait pas à une ou plusieurs conditions requises d’A11YSPEC.

Les échecs peuvent inclure :

* fonctionnalité essentielle indisponible lorsque la vue est indisponible
* fonctionnalité essentielle indisponible lorsque le son est indisponible
* fonctionnalité essentielle indisponible lorsque le toucher est indisponible
* fonctionnalité critique indisponible dans tout cas d’accessibilité requis
* absence de voie d’accès alternative raisonnable pour les informations visuelles essentielles
* absence de voie d’accès alternative raisonnable pour les informations auditives essentielles
* absence de voie d’accès alternative raisonnable pour les opérations essentielles fondées sur le toucher
* paramètres d’accessibilité inaccessibles dans la condition qu’ils sont censés prendre en charge
* contrôles sans libellés ni structure significatifs lorsque cela est requis pour l’usage non visuel
* avertissements uniquement sonores sans équivalent visuel, tactile ou textuel
* état indiqué uniquement par couleur sans équivalent non visuel
* opération uniquement gestuelle sans clavier, pointeur, voix, contacteur ou autre alternative
* confirmation uniquement haptique sans équivalent visuel ou auditif
* prise en charge cassée des technologies d’assistance pour les flux de travail essentiels
* pièges de navigation majeurs
* flux de travail essentiels qui ne peuvent pas être terminés sans le sens indisponible

Les échecs empêchent la vérification jusqu’à leur résolution.

<a id="verification-validity"></a>

### Validité de la vérification

La vérification A11YSPEC s’applique uniquement à l’état examiné du système au moment où la vérification est délivrée.

Un système peut conserver la vérification lors de mises à jour ultérieures tant qu’il préserve la base d’accessibilité vérifiée.

Les changements mineurs de formulation, les raffinements visuels, les améliorations de performance, l’ajout de fonctionnalités d’accessibilité et les mises à jour ordinaires du contenu n’invalident pas automatiquement la vérification.

Un nouvel examen peut être requis si un système :

* supprime des voies d’accès alternatives
* rompt la prise en charge des technologies d’assistance
* modifie substantiellement la navigation essentielle
* supprime des paramètres d’accessibilité requis
* change le comportement d’interaction d’une manière qui affecte l’accessibilité vérifiée
* introduit de nouveaux flux de travail essentiels sans alternatives accessibles
* rend inaccessible une fonctionnalité critique auparavant accessible
* remplace un comportement accessible par un comportement dépendant d’un seul sens

En d’autres termes, améliorer l’accessibilité est généralement acceptable.

Rompre le modèle d’accès vérifié peut nécessiter un examen.
