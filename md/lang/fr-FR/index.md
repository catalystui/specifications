<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->

<!-- Supprimez ces lignes dans une pull request après vérification de la traduction. -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified for Internationalization

Bienvenue dans la documentation CatalystUI Verification pour l’internationalisation.

**CatalystUI Verified for Internationalization** indique qu’un système, service, framework, application ou implémentation a été examiné par l’équipe CatalystUI et jugé capable de fournir un support multilingue suffisant pour l’ensemble de langues d’internationalisation requis par CatalystUI.

Cette vérification n’est pas un classement général de la qualité de traduction, du style rédactionnel, de la profondeur de localisation ou de l’adaptation culturelle. Elle indique plutôt si le système examiné fournit une base stable et pratique permettant aux utilisateurs d’accéder à ses fonctionnalités essentielles dans les langues requises.

En termes plus simples, cette vérification demande si les utilisateurs peuvent utiliser de manière significative les parties essentielles d’un système dans les langues requises, et s’ils disposent d’un moyen raisonnable de choisir la langue qu’ils comprennent.

<a id="purpose"></a>
## Objectif

L’internationalisation est importante parce qu’un système ne peut pas être considéré comme largement accessible si son sens essentiel est enfermé dans une seule langue.

CatalystUI est conçu autour de la clarté, de la cohérence et de la représentation fidèle de l’interaction entre l’être humain et l’ordinateur. La langue fait partie de cette interaction. Si un utilisateur ne peut pas comprendre les libellés, instructions, avertissements, contrôles, paramètres ou contenus essentiels d’un système, alors le système n’a pas communiqué clairement, même si la fonctionnalité sous-jacente fonctionne techniquement.

Internationalization Verification existe pour identifier les systèmes qui fournissent un support traduit suffisant aux utilisateurs dans l’ensemble des langues requises par CatalystUI. Le but n’est pas d’exiger la traduction parfaite de chaque mot facultatif, message caché destiné aux développeurs ou page non essentielle. Le but est de déterminer si les parties essentielles du système peuvent être comprises et utilisées par les personnes dans chaque langue requise.

<a id="what-verification-means"></a>
## Ce que signifie la vérification

Un système devient **CatalystUI Verified for Internationalization** lorsqu’il est examiné selon les exigences listées dans cette section et jugé within spec.

Pour être vérifié, un système doit fournir des traductions pour plus de 75% des parties essentielles destinées aux utilisateurs dans chaque langue requise. Il doit également fournir un mécanisme raisonnable permettant à l’utilisateur final de modifier la langue active.

Un système n’a pas besoin de traduire chaque identifiant interne, détail d’implémentation destiné aux développeurs, chaîne de débogage, page marketing facultative ou texte d’assistance non essentiel. Cependant, les portions destinées aux utilisateurs qui sont nécessaires pour comprendre et utiliser le système essentiel doivent être disponibles dans chaque langue requise.

<a id="required-languages"></a>
## Langues requises

L’ensemble actuel de langues d’internationalisation de CatalystUI a été sélectionné à partir d’un examen pratique des langues couramment nécessaires dans les contextes technologiques, notamment la portée mondiale des locuteurs, l’usage courant en ligne, les attentes liées aux logiciels multilingues et les besoins larges d’accessibilité régionale.

Cet ensemble de langues n’est pas destiné à représenter toutes les langues, tous les dialectes ou toutes les variantes régionales. Il établit plutôt une base pratique pour les systèmes cherchant une large utilisabilité internationale dans de nombreux groupes linguistiques parmi les plus courants dans les contextes technologiques.

L’ensemble actuel de langues d’internationalisation de CatalystUI comprend les locales suivantes :

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

Un système doit fournir une couverture de traduction essentielle suffisante pour chaque groupe linguistique listé afin d’être considéré within spec.

Cependant, les variantes régionales peuvent être examinées avec une flexibilité raisonnable lorsque les différences entre variantes sont mineures et n’affectent pas matériellement la capacité de l’utilisateur à comprendre ou à utiliser le système. Par exemple, un système peut toujours être admissible à la vérification s’il fournit une seule traduction anglaise solide, sans traduire séparément chaque variante régionale de l’anglais, tant que le sens essentiel, la navigation, les instructions, les avertissements et les contrôles restent clairs pour les utilisateurs des variantes manquantes.

Cette flexibilité ne s’applique pas lorsqu’une variante manquante créerait une confusion significative, omettrait une terminologie régionale importante, casserait un comportement sensible à la locale ou empêcherait les utilisateurs de comprendre des parties essentielles du système.

<a id="essential-translation-coverage"></a>
## Couverture de traduction essentielle

Pour Internationalization Verification, la **couverture de traduction essentielle** désigne les parties d’un système dont un utilisateur a raisonnablement besoin pour comprendre, parcourir, configurer et utiliser le système.

Les parties essentielles peuvent inclure :

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

Un système est considéré comme satisfaisant à l’exigence de couverture de traduction lorsque plus de 75% de son contenu essentiel destiné aux utilisateurs est disponible dans chaque langue requise.

Ce seuil existe parce que le travail d’internationalisation peut être vaste, continu et dépendant du contexte. Un système peut toujours être within spec même si certains contenus non essentiels ou de moindre priorité restent non traduits. Toutefois, l’expérience essentielle doit être disponible de manière significative dans chaque langue requise.

<a id="language-selection"></a>
## Sélection de la langue

Un système vérifié doit fournir à l’utilisateur final un moyen raisonnable de changer la langue active.

Le mécanisme de sélection de la langue doit être facile à trouver, compréhensible et disponible sans exiger de connaissances techniques. Les utilisateurs ne devraient pas avoir à modifier des fichiers de configuration, modifier le code source, installer des outils de développement ou dépendre d’un comportement non documenté simplement pour changer la langue.

Lors de l’affichage des options de langue, le système devrait identifier chaque langue d’une manière compréhensible à la fois pour les utilisateurs qui parlent cette langue et pour les utilisateurs qui utilisent actuellement une autre langue sélectionnée.

Par exemple, une option de langue peut être affichée ainsi :

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

La mise en forme exacte peut varier, mais l’intention doit rester la même : les utilisateurs doivent pouvoir reconnaître leur propre langue, comprendre lorsque possible le nom de langue actuellement affiché et identifier le code de locale associé.

<a id="what-within-spec-means"></a>
## Ce que signifie “Within Spec”

Lorsqu’un système est considéré **within spec**, cela signifie que l’équipe CatalystUI a examiné manuellement le système et a jugé raisonnable de conclure qu’il satisfait aux exigences d’internationalisation décrites par cette catégorie de vérification.

Cela n’exige pas un modèle d’implémentation unique et rigide. Un système peut satisfaire à l’exigence grâce à des fichiers de ressources, des tables de traduction, un routage sensible à la locale, des ressources linguistiques compilées, des traductions soutenues par une base de données, des packs de langue au runtime ou un autre mécanisme stable approprié au système.

La vérification concerne la capacité pratique des utilisateurs à accéder au système essentiel dans les langues requises, et non le fait que le système utilise une architecture de traduction spécifique.

<a id="what-verification-does-not-mean"></a>
## Ce que la vérification ne signifie pas

CatalystUI Verified for Internationalization ne garantit pas que chaque traduction est parfaite, littéraire, idiomatique, culturellement complète ou légalement suffisante pour chaque région.

Elle ne vérifie pas non plus automatiquement l’accessibilité, la typographie, la mise en page de droite à gauche, le formatage propre à une locale, le formatage des devises, le formatage des dates, la conformité légale ou les exigences commerciales régionales, sauf si ces préoccupations sont incluses dans le périmètre d’internationalisation examiné.

Un système peut fournir une forte couverture de traduction et tout de même nécessiter un examen séparé pour l’accessibilité, la qualité de localisation, la conformité régionale ou d’autres préoccupations spécialisées.

<a id="why-this-verification-exists"></a>
## Pourquoi cette vérification existe

Une user interface n’est utile que lorsque l’utilisateur peut comprendre ce qu’elle communique.

De nombreux systèmes revendiquent un support linguistique tout en ne traduisant qu’une petite partie de l’expérience, en cachant la sélection de langue, en omettant des messages importants ou en laissant des flux de travail essentiels partiellement non traduits. Cela crée de la confusion et empêche les utilisateurs de faire confiance au système.

Internationalization Verification existe pour établir un standard plus clair. Elle identifie les systèmes qui font un effort sérieux et pratique pour soutenir les utilisateurs dans l’ensemble de langues CatalystUI requis et qui fournissent un moyen raisonnable pour les utilisateurs de sélectionner la langue dont ils ont besoin.

<a id="verification-scope"></a>
## Périmètre de vérification

CatalystUI Verification for Internationalization s’applique au système, service, framework, application ou implémentation examiné tel qu’il existait au moment où la vérification a été émise.

Un système vérifié fournit une couverture de traduction essentielle suffisante pour les langues requises. Cela ne garantit pas que chaque page, fonctionnalité, version, plugin, extension ou intégration tierce future soit automatiquement within spec.

Des produits, modules, services, packs de langue ou révisions majeures séparés peuvent nécessiter leur propre examen selon la catégorie de vérification demandée.

<a id="verification-validity"></a>
## Validité de la vérification

CatalystUI Verification s’applique uniquement à l’état examiné du système au moment où la vérification est émise.

Un système peut conserver sa vérification lors de mises à jour ultérieures tant qu’il préserve la base d’internationalisation vérifiée. Les changements mineurs de formulation, les traductions ajoutées et les mises à jour ordinaires du contenu n’invalident pas automatiquement la vérification.

Un nouvel examen peut être requis si un système supprime le support d’une langue requise, casse la sélection de langue, réduit substantiellement la couverture de traduction essentielle ou modifie son architecture d’internationalisation d’une manière qui affecte le comportement vérifié.

Autrement dit, améliorer le support de traduction est généralement acceptable. Casser la base multilingue vérifiée peut nécessiter un examen.

<a id="verified-systems"></a>
## Systèmes vérifiés

Les systèmes connus vérifiés pour l’internationalisation sont listés séparément sur la page CatalystUI Verified appropriée.
