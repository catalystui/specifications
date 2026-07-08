<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->

<!-- Supprimez ces lignes dans une pull request après vérification de la traduction. -->

# I18NSPEC

<br/>

> **Spécification d’internationalisation**<br/>
> Révision 1<br/>
> 8 juillet 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Les définitions, exigences et concepts présentés ici décrivent le support pratique de l’internationalisation et peuvent être librement reformulés.

<a id="introduction"></a>
## Introduction

La **Spécification d’internationalisation (I18NSPEC)** établit les concepts, la terminologie et les exigences de base utilisés pour évaluer le support multilingue dans l’écosystème CatalystUI. Son objectif est de fournir un standard clair pour déterminer si un système, service, framework, application ou implémentation fournit un support linguistique suffisant pour être considéré within spec.

L’internationalisation est importante parce qu’une user interface ne peut pas communiquer clairement si son sens essentiel n’est disponible que dans une seule langue. Un système peut être techniquement fonctionnel, mais si les utilisateurs ne peuvent pas comprendre ses libellés, instructions, contrôles, paramètres, avertissements, erreurs ou flux de travail principaux, alors le système n’a pas fourni une interface significative pour ces utilisateurs.

Cette spécification ne tente pas de mesurer une qualité de traduction parfaite, le style littéraire, l’adaptation culturelle, la conformité légale ou une localisation régionale complète. Elle définit plutôt la base multilingue minimale requise pour que les utilisateurs puissent accéder et utiliser de manière significative les portions essentielles d’un système dans l’ensemble de locales requis par CatalystUI.

En termes plus simples, I18NSPEC pose trois questions principales :

1. Les utilisateurs peuvent-ils accéder aux parties essentielles du système dans chaque langue requise ?
2. Les utilisateurs peuvent-ils raisonnablement sélectionner la langue qu’ils comprennent ?
3. Le système préserve-t-il assez de sens d’une langue à l’autre pour rester utilisable ?

> [!IMPORTANT]
>
> I18NSPEC définit les exigences d’internationalisation pour la vérification. Ce n’est pas une spécification séparée pour chaque langue. Chaque locale requise est vérifiée selon la même spécification.

<a id="table-of-contents"></a>
## Table des matières

* [I18NSPEC](#i18nspec)

  * [Introduction](#introduction)
  * [Table des matières](#table-of-contents)
  * [Conformité](#conformance)
  * [Ensemble de locales requis](#required-locale-set)
  * [Contenu destiné aux utilisateurs](#user-facing-content)

    * [Contenu destiné aux utilisateurs](#user-facing-content-1)
    * [Contenu essentiel destiné aux utilisateurs](#essential-user-facing-content)
    * [Contenu critique destiné aux utilisateurs](#critical-user-facing-content)
    * [Contenu non essentiel](#nonessential-content)
  * [Couverture de traduction](#translation-coverage)

    * [Couverture de traduction essentielle](#essential-translation-coverage)
    * [Exigence de couverture](#coverage-requirement)
    * [Exigence de contenu critique](#critical-content-requirement)
  * [Sélection de la langue](#language-selection)

    * [Locale active](#active-locale)
    * [Locale par défaut](#default-locale)
    * [Mécanisme de sélection de la langue](#language-selection-mechanism)
    * [Libellés des options de langue](#language-option-labels)
  * [Fallbacks et équivalence de locale](#fallbacks-and-locale-equivalence)

    * [Locale de fallback](#fallback-locale)
    * [Comportement de fallback](#fallback-behavior)
    * [Équivalence de locale](#locale-equivalence)
  * [Exigences d’implémentation](#implementation-requirements)

    * [Mécanisme de traduction stable](#stable-translation-mechanism)
    * [Préservation du sens](#preservation-of-meaning)
    * [Langues sensibles à la direction](#direction-sensitive-languages)
    * [Valeurs sensibles à la locale](#locale-sensitive-values)
  * [Vérification](#verification)

    * [Within Spec](#within-spec)
    * [Avertissements](#warnings)
    * [Échecs](#failures)
    * [Validité de la vérification](#verification-validity)

<a id="conformance"></a>
## Conformité

Un système est considéré conforme à I18NSPEC lorsqu’il satisfait aux exigences définies par ce document pour chaque locale de l’ensemble de locales requis.

Un système conforme doit :

1. Prendre en charge chaque locale de l’ensemble de locales requis.
2. Fournir du contenu traduit pour plus de 75% du contenu essentiel destiné aux utilisateurs dans chaque locale requise.
3. Fournir du contenu traduit pour tout le contenu critique destiné aux utilisateurs dans chaque locale requise.
4. Fournir un mécanisme raisonnable permettant à l’utilisateur final de sélectionner la locale active.
5. Utiliser un mécanisme de traduction stable approprié au système.
6. Préserver le sens essentiel du contenu traduit destiné aux utilisateurs.
7. Éviter de s’appuyer sur du contenu de fallback pour revendiquer une couverture de traduction, sauf lorsque l’équivalence de locale est acceptée pendant l’examen.

Un système n’a pas besoin d’utiliser un modèle d’implémentation spécifique pour se conformer à cette spécification. Il peut utiliser des fichiers de ressources, des tables de traduction, un routage sensible à la locale, des ressources linguistiques compilées, des pages statiques localisées, des packs de langue au runtime, des traductions soutenues par une base de données ou un autre mécanisme stable approprié au système.

La vérification porte sur l’accès pratique des utilisateurs et le sens essentiel, pas sur une architecture technique rigide.

<a id="required-locale-set"></a>
## Ensemble de locales requis

L’ensemble de locales requis définit les langues et variantes régionales qui doivent être examinées pour CatalystUI Internationalization Verification.

L’ensemble actuel de locales requis comprend les locales suivantes :

| Locale    | Langue                   |
| --------- | ------------------------ |
| `ar-SA`   | Arabe (Arabie saoudite)  |
| `bn-BD`   | Bengali (Bangladesh)     |
| `de-DE`   | Allemand (Allemagne)     |
| `en-GB`   | Anglais (Royaume-Uni)    |
| `en-IN`   | Anglais (Inde)           |
| `en-US`   | Anglais (États-Unis)     |
| `es-ES`   | Espagnol (Espagne)       |
| `es-MX`   | Espagnol (Mexique)       |
| `fa-IR`   | Persan (Iran)            |
| `fr-FR`   | Français (France)        |
| `hi-IN`   | Hindi (Inde)             |
| `id-ID`   | Indonésien (Indonésie)   |
| `it-IT`   | Italien (Italie)         |
| `ja-JP`   | Japonais (Japon)         |
| `ko-KR`   | Coréen (Corée du Sud)    |
| `nl-NL`   | Néerlandais (Pays-Bas)   |
| `pl-PL`   | Polonais (Pologne)       |
| `pt-BR`   | Portugais (Brésil)       |
| `ru-RU`   | Russe (Russie)           |
| `tl-PH`   | Tagalog (Philippines)    |
| `tr-TR`   | Turc (Turquie)           |
| `uk-UA`   | Ukrainien (Ukraine)      |
| `ur-PK`   | Ourdou (Pakistan)        |
| `vi-VN`   | Vietnamien (Vietnam)     |
| `zh-CN`   | Chinois (Chine)          |
| `zh-Hans` | Chinois (simplifié)      |

Un système doit fournir un support de traduction essentielle suffisant pour chaque locale listée afin d’être considéré within spec.

L’ensemble de locales requis n’est pas destiné à représenter chaque langue, dialecte, région ou écriture. Il établit plutôt une base pratique pour une large utilisabilité internationale dans de nombreux groupes linguistiques courants dans les contextes technologiques.

<a id="user-facing-content"></a>
## Contenu destiné aux utilisateurs

<a id="user-facing-content-1"></a>
### Contenu destiné aux utilisateurs

Le contenu destiné aux utilisateurs est tout contenu destiné à être perçu, lu, entendu, sélectionné, compris ou utilisé par un utilisateur final.

Le contenu destiné aux utilisateurs peut inclure :

* la navigation
* les libellés
* les boutons
* les menus
* les contrôles
* les titres
* les dialogues
* les paramètres
* les instructions
* les invites
* les avertissements
* les erreurs
* les confirmations
* les messages d’état
* le texte d’accueil
* le texte d’aide requis
* les contrôles de sélection de langue
* le contenu des flux de travail principaux

Le contenu destiné aux utilisateurs n’a pas besoin d’être visuel. Il peut aussi inclure du contenu auditif, tactile, symbolique ou multisensoriel lorsque ce contenu communique un sens à l’utilisateur.

<a id="essential-user-facing-content"></a>
### Contenu essentiel destiné aux utilisateurs

Le contenu essentiel destiné aux utilisateurs est le contenu destiné aux utilisateurs dont une personne a raisonnablement besoin pour comprendre, parcourir, configurer ou utiliser le comportement essentiel d’un système.

Le contenu essentiel destiné aux utilisateurs peut inclure :

* la navigation principale
* les écrans et vues principaux
* les paramètres et préférences
* les libellés destinés aux utilisateurs
* les contrôles destinés aux utilisateurs
* les instructions requises
* les avertissements importants
* les erreurs importantes
* les invites essentielles
* les messages de confirmation requis
* les contrôles de sélection de langue
* les flux de travail principaux nécessaires à l’utilisation normale

Un système n’a pas besoin de traduire chaque page facultative, message caché, libellé interne ou texte non essentiel pour satisfaire à I18NSPEC. Toutefois, le contenu requis pour l’utilisation essentielle ordinaire doit être traduit selon les exigences de cette spécification.

<a id="critical-user-facing-content"></a>
### Contenu critique destiné aux utilisateurs

Le contenu critique destiné aux utilisateurs est un contenu essentiel destiné aux utilisateurs dont la mauvaise compréhension peut empêcher une utilisation significative, créer une erreur grave ou amener l’utilisateur à prendre une décision importante sans en comprendre la conséquence.

Le contenu critique destiné aux utilisateurs peut inclure :

* les contrôles de sélection de langue
* les avertissements d’action destructive
* les avertissements de suppression de compte
* les confirmations de paiement
* les confirmations d’achat
* les choix de confidentialité
* les avertissements de sécurité
* les demandes de consentement
* les instructions de sécurité requises
* les instructions de configuration requises
* les messages d’erreur requis
* la navigation principale requise pour atteindre les paramètres de langue

Le contenu critique destiné aux utilisateurs doit être traduit pour chaque locale requise.

Le seuil de 75% de couverture de traduction essentielle ne doit pas être utilisé pour laisser du contenu critique non traduit.

<a id="nonessential-content"></a>
### Contenu non essentiel

Le contenu non essentiel est un contenu qui n’est pas raisonnablement requis pour qu’un utilisateur comprenne, parcoure, configure ou utilise le comportement essentiel d’un système.

Le contenu non essentiel peut inclure :

* les identifiants internes
* les noms de code source
* les chaînes réservées au débogage
* les détails d’implémentation destinés aux développeurs
* le texte de diagnostic caché
* les pages marketing facultatives
* les pages d’assistance facultatives
* le texte légal ou commercial non essentiel hors du périmètre examiné
* le contenu tiers non contrôlé par le système examiné

Le contenu non essentiel peut être traduit, mais ce n’est pas requis pour la conformité à I18NSPEC sauf s’il devient nécessaire à la compréhension ou à l’utilisation essentielle par l’utilisateur.

<a id="translation-coverage"></a>
## Couverture de traduction

<a id="essential-translation-coverage"></a>
### Couverture de traduction essentielle

La couverture de traduction essentielle est la quantité de contenu essentiel destiné aux utilisateurs qui est traduite pour une locale précise.

La couverture devrait être évaluée selon des unités significatives de contenu destiné aux utilisateurs plutôt que selon la taille des fichiers, le nombre d’octets, le nombre de lignes, la taille du repository ou le nombre de pages.

Par exemple, un bouton non traduit qui contrôle une action essentielle peut compter davantage qu’un long paragraphe facultatif non traduit qui n’affecte pas l’utilisation ordinaire.

La couverture de traduction devrait être jugée selon la capacité de l’utilisateur à comprendre et à utiliser de manière significative le système essentiel dans la locale examinée.

<a id="coverage-requirement"></a>
### Exigence de couverture

Un système satisfait à l’exigence de couverture de traduction pour une locale lorsque plus de 75% du contenu essentiel destiné aux utilisateurs est traduit pour cette locale.

Un système satisfait à l’exigence de couverture I18NSPEC lorsqu’il atteint ce seuil pour chaque locale de l’ensemble de locales requis.

Dans un examen pratique, cela peut être représenté ainsi :

| Locale  | Couverture de traduction essentielle | Résultat |
| ------- | ------------------------------------ | -------- |
| `en-US` | 100%                                 | Réussite |
| `es-ES` | 94%                                  | Réussite |
| `ar-SA` | 78%                                  | Réussite |
| `ja-JP` | 61%                                  | Échec    |

Une locale avec une couverture de 75% ou moins ne satisfait pas à l’exigence de couverture.

Une locale avec plus de 75% de couverture peut tout de même échouer si du contenu critique destiné aux utilisateurs n’est pas traduit.

<a id="critical-content-requirement"></a>
### Exigence de contenu critique

Tout le contenu critique destiné aux utilisateurs doit être traduit pour chaque locale requise.

Un système peut échouer à I18NSPEC même lorsqu’il satisfait au seuil général de couverture si un ou plusieurs éléments de contenu critique destiné aux utilisateurs sont manquants, non traduits, trompeurs ou non compréhensibles de manière significative.

Par exemple, un système ne devrait pas être considéré within spec si l’interface générale est traduite mais que l’avertissement de suppression de compte, la confirmation d’achat, l’avertissement de sécurité ou le sélecteur de langue reste non traduit.

<a id="language-selection"></a>
## Sélection de la langue

<a id="active-locale"></a>
### Locale active

La locale active est la locale actuellement sélectionnée pour l’expérience de l’utilisateur.

La locale active détermine quel contenu traduit doit être affiché, fourni ou autrement communiqué à l’utilisateur.

<a id="default-locale"></a>
### Locale par défaut

La locale par défaut est la locale utilisée lorsque l’utilisateur n’a pas sélectionné de locale active ou lorsqu’aucune préférence utilisateur n’est disponible.

Un système doit définir une locale par défaut.

La locale par défaut devrait être documentée ou raisonnablement déductible par l’examinateur.

<a id="language-selection-mechanism"></a>
### Mécanisme de sélection de la langue

Un système conforme doit fournir un moyen raisonnable permettant à l’utilisateur final de modifier la locale active.

Le mécanisme de sélection de la langue doit être disponible sans exiger que l’utilisateur :

* modifie le code source
* utilise des outils de développement
* modifie des fichiers de configuration non documentés
* installe des correctifs non officiels
* s’appuie sur un comportement caché
* contacte l’assistance pour des changements de langue ordinaires

Un mécanisme de sélection de la langue peut être fourni par :

* les paramètres de l’application
* les préférences du compte
* un sélecteur de langue
* une invite de démarrage
* les paramètres du navigateur
* les paramètres du système d’exploitation
* les paramètres de l’appareil
* un autre mécanisme approprié accessible à l’utilisateur final

Le mécanisme n’a pas besoin de suivre un modèle de conception spécifique. Il doit raisonnablement permettre à l’utilisateur de sélectionner une langue prise en charge.

<a id="language-option-labels"></a>
### Libellés des options de langue

Lors de l’affichage des options de langue, un système devrait identifier chaque langue d’une manière compréhensible pour les utilisateurs qui parlent cette langue.

Une option de langue peut inclure :

* le nom de la langue dans cette langue
* le nom de la langue dans la langue actuellement active
* le code de locale
* un libellé régional
* un libellé d’écriture

Par exemple :

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

La mise en forme exacte peut varier.

L’intention est que les utilisateurs puissent reconnaître leur propre langue, comprendre lorsque possible le nom de langue actuellement affiché et identifier le code de locale associé.

<a id="fallbacks-and-locale-equivalence"></a>
## Fallbacks et équivalence de locale

<a id="fallback-locale"></a>
### Locale de fallback

Une locale de fallback est une locale utilisée lorsque le contenu traduit est indisponible pour la locale active.

Les locales de fallback peuvent aider à préserver l’utilisabilité, mais le contenu de fallback n’est pas automatiquement considéré comme du contenu traduit pour la locale active.

Par exemple, si un système est réglé sur `es-MX` mais affiche du texte `en-US` parce que la traduction espagnole manque, ce texte anglais peut être utile comme fallback, mais il ne devrait pas être compté comme couverture de traduction espagnole.

<a id="fallback-behavior"></a>
### Comportement de fallback

Un système conforme peut utiliser un comportement de fallback lorsque le contenu localisé est indisponible.

Le comportement de fallback devrait éviter les sorties cassées, vides ou trompeuses.

Le comportement de fallback ne doit pas être utilisé pour revendiquer faussement une couverture de traduction pour une locale requise.

Un système peut recevoir un avertissement ou un échec si le comportement de fallback est excessif, confus, non documenté ou fait apparaître du contenu essentiel non traduit dans une locale requise.

<a id="locale-equivalence"></a>
### Équivalence de locale

L’équivalence de locale se produit lorsqu’une traduction peut raisonnablement servir plus d’une locale sans empêcher la compréhension ou l’utilisation essentielle.

Par exemple, un système peut utiliser une seule traduction anglaise pour `en-US`, `en-GB` et `en-IN` si le sens essentiel reste clair pour les utilisateurs de chaque locale.

L’équivalence de locale peut être acceptée pendant l’examen lorsque les différences régionales sont mineures et n’affectent pas matériellement l’utilisabilité essentielle.

L’équivalence de locale ne doit pas être utilisée lorsqu’une locale manquante créerait une confusion significative, omettrait une terminologie régionale importante, casserait un comportement essentiel ou empêcherait les utilisateurs de comprendre le système.

Par exemple, un système ne devrait pas supposer que des langues sans lien sont équivalentes parce qu’elles partagent une direction d’écriture, une région géographique, une famille d’écritures ou une large catégorie culturelle.

L’équivalence de locale est un jugement d’examen, pas une règle automatique.

<a id="implementation-requirements"></a>
## Exigences d’implémentation

<a id="stable-translation-mechanism"></a>
### Mécanisme de traduction stable

Un système conforme doit utiliser un mécanisme de traduction stable approprié au système examiné.

Un mécanisme de traduction stable devrait permettre au contenu traduit d’être maintenu, mis à jour, examiné et étendu sans dépendre d’un comportement fragile ou non documenté.

Un mécanisme de traduction stable peut inclure :

* des fichiers de ressources
* des tables de traduction
* un routage sensible à la locale
* des ressources linguistiques compilées
* des pages statiques localisées
* des packs de langue au runtime
* des traductions soutenues par une base de données
* une autre structure de traduction documentée

Un système devrait éviter de coder en dur le contenu essentiel destiné aux utilisateurs d’une manière qui empêche le support de traduction requis.

<a id="preservation-of-meaning"></a>
### Préservation du sens

Une traduction préserve le sens lorsque l’utilisateur peut raisonnablement comprendre la même instruction essentielle, le même libellé, avertissement, contrôle, paramètre ou flux de travail que les utilisateurs de la langue source.

Une traduction n’a pas besoin d’être identique mot à mot au contenu source.

Une traduction peut modifier l’ordre des mots, la grammaire, la structure des phrases, les expressions idiomatiques, le ton ou la formulation lorsque cela est nécessaire pour communiquer le même sens essentiel dans la langue cible.

Une traduction peut échouer à l’examen si elle est trompeuse, incomplète, absurde, corrompue par machine ou significativement différente du contenu source d’une manière qui affecte l’utilisation essentielle.

<a id="direction-sensitive-languages"></a>
### Langues sensibles à la direction

Certaines locales requises utilisent couramment une direction de texte de droite à gauche.

Un système conforme ne doit pas empêcher le contenu essentiel traduit d’être lu, compris, sélectionné ou utilisé parce que la locale active utilise une direction de texte différente.

Le système devrait préserver un ordre lisible, le comportement de la ponctuation et l’association des contrôles pour les langues sensibles à la direction.

Le polissage visuel complet, la qualité typographique, le comportement d’accessibilité et le raffinement de la mise en page peuvent nécessiter un examen séparé. Toutefois, le contenu essentiel traduit doit rester utilisable de manière significative.

<a id="locale-sensitive-values"></a>
### Valeurs sensibles à la locale

Les valeurs sensibles à la locale sont des valeurs dont le sens ou la lisibilité peut varier selon la langue, la région, l’écriture ou la culture.

Les valeurs sensibles à la locale peuvent inclure :

* les dates
* les heures
* les nombres
* les devises
* les mesures
* les formes plurielles
* le genre grammatical
* l’ordre de tri
* les formats d’adresse
* les formats de numéro de téléphone

I18NSPEC n’exige pas une localisation complète de chaque valeur sensible à la locale, sauf si cette valeur est essentielle pour comprendre ou utiliser le système.

Lorsque des valeurs sensibles à la locale sont essentielles, le système devrait les représenter d’une manière que les utilisateurs de la locale active peuvent raisonnablement comprendre.

<a id="verification"></a>
## Vérification

<a id="within-spec"></a>
### Within Spec

Un système est considéré within spec lorsque l’équipe CatalystUI a examiné le système et a jugé raisonnable de conclure qu’il satisfait à I18NSPEC.

Un système peut être within spec lorsque :

* chaque locale requise est prise en charge
* plus de 75% du contenu essentiel destiné aux utilisateurs est traduit pour chaque locale requise
* tout le contenu critique destiné aux utilisateurs est traduit pour chaque locale requise
* les utilisateurs peuvent raisonnablement sélectionner la locale active
* le comportement de fallback ne revendique pas faussement une couverture de traduction
* l’équivalence de locale, si elle est utilisée, est raisonnable et documentée
* le contenu traduit préserve le sens essentiel

Un système peut être within spec même si certains contenus non essentiels restent non traduits.

Un système peut être within spec même si les traductions ne sont pas parfaites, à condition que le sens essentiel soit préservé et que les exigences de cette spécification soient satisfaites.

<a id="warnings"></a>
### Avertissements

Un avertissement peut être émis lorsqu’un système semble satisfaire à I18NSPEC mais contient des préoccupations qui devraient être documentées.

Les avertissements peuvent inclure :

* du contenu non essentiel mineur non traduit
* une terminologie incohérente entre les locales
* des traductions imparfaites mais compréhensibles
* une équivalence de locale acceptable qui devrait être documentée
* un comportement de fallback limité
* des pages facultatives partiellement traduites
* des préoccupations de mise en page sensibles à la direction qui n’empêchent pas l’utilisation essentielle
* des valeurs sensibles à la locale compréhensibles mais non idéales

Les avertissements n’empêchent pas nécessairement la vérification.

<a id="failures"></a>
### Échecs

Un échec se produit lorsqu’un système ne satisfait pas à une ou plusieurs conditions requises par I18NSPEC.

Les échecs peuvent inclure :

* l’absence de support pour une locale requise
* une couverture de traduction essentielle égale ou inférieure à 75% pour une locale requise
* du contenu critique destiné aux utilisateurs non traduit
* l’absence de mécanisme raisonnable de sélection de la langue
* une sélection de langue nécessitant une modification du code source
* une sélection de langue nécessitant des outils de développement
* un chargement de traduction cassé
* des revendications de locale trompeuses
* un comportement de fallback excessif
* du contenu de fallback compté comme contenu traduit sans équivalence de locale valide
* du contenu sensible à la direction illisible ou inutilisable
* des flux de travail essentiels indisponibles dans une ou plusieurs locales requises

Les échecs empêchent la vérification jusqu’à leur résolution.

<a id="verification-validity"></a>
### Validité de la vérification

La vérification I18NSPEC s’applique uniquement à l’état examiné du système au moment où la vérification est émise.

Un système peut conserver sa vérification lors de mises à jour ultérieures tant qu’il préserve la base d’internationalisation vérifiée.

Les changements mineurs de formulation, les traductions ajoutées, les traductions améliorées et les mises à jour ordinaires du contenu n’invalident pas automatiquement la vérification.

Un nouvel examen peut être requis si un système :

* supprime le support d’une locale requise
* casse la sélection de langue
* réduit substantiellement la couverture de traduction essentielle
* laisse de nouveaux flux de travail essentiels non traduits
* remplace du contenu traduit par du contenu de fallback
* modifie son architecture de traduction d’une manière qui affecte le comportement vérifié
* introduit des changements majeurs destinés aux utilisateurs qui modifient le périmètre examiné

Autrement dit, améliorer le support de traduction est généralement acceptable.

Casser la base multilingue vérifiée peut nécessiter un examen.
