<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->

<!-- Supprimez ces lignes dans une pull request après vérification de la traduction. -->

![CatalystUI Verified for Accessibility](/images/verification/verified-logo-accessibility.png)

# CatalystUI Verified for Accessibility

Bienvenue dans la documentation de vérification CatalystUI pour l’accessibilité.

**CatalystUI Verified for Accessibility** indique qu’un service, framework, application, bibliothèque ou système a été examiné par l’équipe CatalystUI et jugé raisonnablement utilisable lorsqu’un des trois sens primaires impliqués dans l’interaction avec une interface utilisateur est individuellement indisponible.

Pour cette vérification, CatalystUI identifie les trois sens primaires d’accessibilité comme étant **la vue**, **le son** et **le toucher**. Un système vérifié doit préserver un accès raisonnable à ses fonctionnalités essentielles lorsque l’un de ces sens est indisponible, en s’appuyant sur les domaines sensoriels restants disponibles.

En termes plus simples, cette vérification demande si un utilisateur peut encore comprendre, parcourir et utiliser de manière significative les parties essentielles d’un système lorsqu’il ne peut pas s’appuyer individuellement sur la vue, le son ou le toucher.

## Objectif

L’accessibilité est importante parce qu’une interface utilisateur ne devrait pas dépendre entièrement d’une seule voie sensorielle lorsque le même sens essentiel peut raisonnablement être communiqué par une autre voie.

CatalystUI est conçu autour du mouvement fidèle des données entre les systèmes et la perception humaine. Si une information importante est seulement visible, seulement audible ou seulement disponible par le toucher, le système peut devenir inutilisable pour les utilisateurs qui ne peuvent pas s’appuyer sur ce sens. La vérification d’accessibilité existe pour identifier les systèmes qui préservent l’accès en permettant aux informations et aux interactions essentielles de continuer par des routes sensorielles alternatives.

Le but n’est pas d’exiger toutes les méthodes d’interaction possibles, toutes les technologies d’assistance ou tous les aménagements spécialisés. Le but est de déterminer si le système essentiel demeure utilisable de manière significative lorsque la vue, le son ou le toucher est individuellement indisponible.

## Ce que signifie la vérification

Un système devient **CatalystUI Verified for Accessibility** lorsqu’il est examiné selon les exigences énumérées dans cette section et jugé conforme à la spécification.

Pour être vérifié, un système doit demeurer raisonnablement utilisable dans chacun des cas suivants :

| Sens indisponible | Comportement d’accessibilité requis |
| ----------------- | ----------------------------------------------------------------- |
| Vue               | Le système doit demeurer raisonnablement utilisable par le son et le toucher. |
| Son               | Le système doit demeurer raisonnablement utilisable par la vue et le toucher. |
| Toucher           | Le système doit demeurer raisonnablement utilisable par la vue et le son. |

Un système n’a pas besoin de fournir des expériences identiques sur chaque voie sensorielle. Une expérience non visuelle peut être plus lente qu’une expérience visuelle. Une expérience sans son peut nécessiter des sous-titres, des indicateurs visuels ou d’autres substitutions. Une expérience sans toucher peut nécessiter des contrôles alternatifs, une interaction vocale, une navigation au clavier, une navigation au pointeur ou d’autres méthodes sans toucher.

Ce qui importe est de savoir si la fonctionnalité essentielle demeure accessible, compréhensible et utilisable sans exiger le sens indisponible.

## Fonctionnalité essentielle

Pour la vérification d’accessibilité, la **fonctionnalité essentielle** désigne les parties d’un système dont un utilisateur a raisonnablement besoin pour comprendre, parcourir, configurer et utiliser le système.

La fonctionnalité essentielle peut inclure :

* la navigation principale
* les flux de travail principaux
* les contrôles requis
* les avertissements importants
* les erreurs importantes
* les messages de confirmation requis
* l’accès au compte ou à la session
* les paramètres et préférences
* la configuration de la langue ou de l’accessibilité
* les instructions essentielles
* les informations d’état destinées à l’utilisateur
* toute interaction requise pour une utilisation normale

Un système peut tout de même être conforme à la spécification si les éléments décoratifs, redondants, facultatifs ou non essentiels ne sont pas également disponibles par chaque voie sensorielle. Cependant, l’utilisateur doit quand même pouvoir utiliser le système essentiel sans être bloqué par le sens manquant.

## Vue indisponible

Lorsque la vue est indisponible, le système devrait demeurer raisonnablement utilisable par le son et le toucher.

Cela peut inclure une sortie parlée, une structure compatible avec les lecteurs d’écran, un ordre de focus significatif, des contrôles tactiles, l’accès au clavier, une confirmation haptique, des descriptions audio ou une autre méthode non visuelle raisonnable pour communiquer les informations essentielles.

Un système ne devrait pas dépendre exclusivement de la position visuelle, de la couleur, de la forme, de l’animation, des icônes ou de la disposition lorsque ces informations sont nécessaires pour comprendre ou utiliser une fonctionnalité essentielle.

## Son indisponible

Lorsque le son est indisponible, le système devrait demeurer raisonnablement utilisable par la vue et le toucher.

Cela peut inclure des sous-titres, des transcriptions, des alertes visuelles, des équivalents textuels, des indicateurs de progression, des messages d’état visibles, un retour haptique ou une autre méthode non auditive raisonnable pour communiquer les informations essentielles.

Un système ne devrait pas dépendre exclusivement d’effets sonores, d’instructions parlées, d’alertes, d’alarmes, d’indices musicaux ou d’invites uniquement audio lorsque ces informations sont nécessaires pour comprendre ou utiliser une fonctionnalité essentielle.

## Toucher indisponible

Lorsque le toucher est indisponible, le système devrait demeurer raisonnablement utilisable par la vue et le son.

Cela peut inclure le contrôle vocal, la navigation au clavier, des alternatives au pointeur, des télécommandes, une interaction compatible avec le regard, une interaction compatible avec des contacteurs, des invites parlées, une confirmation visuelle ou une autre méthode raisonnable qui ne requiert pas d’interaction tactile ni de perception tactile.

Un système ne devrait pas dépendre exclusivement de gestes tactiles, de retour haptique, de texture physique, de vibration, de force, de pression ou de contrôles uniquement tactiles lorsque ces interactions sont nécessaires pour comprendre ou utiliser une fonctionnalité essentielle.

## Domaines sensoriels supplémentaires

CatalystUI reconnaît également **le goût** et **l’odorat** comme domaines sensoriels. Ces domaines peuvent être pris en compte pendant l’examen d’accessibilité lorsque le système les utilise de manière significative.

Le goût et l’odorat sont **inclusifs** pour la vérification, ce qui signifie qu’ils peuvent renforcer ou soutenir un examen d’accessibilité lorsqu’ils fournissent un accès alternatif significatif ou un contexte supplémentaire.

Le goût et l’odorat ne sont actuellement pas **exclusifs** pour l’échec, ce qui signifie qu’un système n’échoue pas à la vérification d’accessibilité simplement parce qu’il ne fournit pas d’interaction fondée sur le goût ou l’odorat.

La vérification d’accessibilité de CatalystUI porte principalement sur le fait que le système demeure raisonnablement utilisable lorsque la vue, le son ou le toucher est individuellement indisponible.

## Ce que signifie « conforme à la spécification »

Lorsqu’un système est considéré comme **conforme à la spécification**, cela signifie que l’équipe CatalystUI a examiné manuellement le système et a jugé raisonnable de conclure qu’il satisfait aux exigences d’accessibilité décrites par cette catégorie de vérification.

Cela n’exige pas un modèle d’implémentation unique et rigide. Un système peut satisfaire aux exigences d’accessibilité au moyen d’API d’accessibilité natives de la plateforme, d’une structure sémantique, de méthodes d’entrée alternatives, de méthodes de sortie alternatives, de la prise en charge des technologies d’assistance, de paramètres d’accessibilité intégrés, d’une intégration au niveau de l’appareil ou d’un autre mécanisme stable approprié au système.

La vérification concerne la capacité pratique des utilisateurs à accéder au système essentiel lorsqu’un sens primaire est indisponible, et non le fait que le système utilise une architecture d’accessibilité particulière.

## Ce que la vérification ne signifie pas

CatalystUI Verified for Accessibility ne garantit pas que chaque handicap possible, appareil, technologie d’assistance, condition médicale, exigence légale, norme régionale ou cas d’usage spécialisé a été entièrement examiné.

Elle ne vérifie pas non plus automatiquement l’internationalisation, la qualité de traduction, la typographie, la localisation, la conformité régionale ou la qualité générale de conception, sauf si ces préoccupations sont incluses dans le périmètre d’accessibilité examiné.

Un système peut être raisonnablement accessible selon le modèle d’accessibilité de CatalystUI et nécessiter malgré tout un examen séparé pour la conformité légale, la certification de plateforme, la prise en charge spécialisée des technologies d’assistance ou d’autres normes d’accessibilité.

## Pourquoi cette vérification existe

Une interface utilisateur ne réussit que lorsque les utilisateurs peuvent réellement l’utiliser.

De nombreux systèmes traitent l’accessibilité comme une réflexion après coup, une liste de contrôle ou une exigence technique étroite plutôt que comme une partie fondamentale de l’interaction humain-ordinateur. CatalystUI adopte une approche plus simple et plus directe : si un système dépend de la perception humaine, alors il devrait préserver le sens essentiel lorsqu’une voie sensorielle primaire est indisponible.

La vérification d’accessibilité existe pour identifier les systèmes qui prennent cette responsabilité au sérieux. Elle reconnaît les systèmes qui fournissent un accès alternatif significatif, préservent la fonctionnalité essentielle et évitent d’enfermer les utilisateurs derrière un seul sens requis.

## Périmètre de la vérification

La vérification CatalystUI pour l’accessibilité s’applique au système, service, framework, application, bibliothèque ou implémentation examiné tel qu’il existait au moment où la vérification a été délivrée.

Un système vérifié fournit une accessibilité raisonnable pour sa fonctionnalité essentielle dans les conditions examinées. Cela ne garantit pas que chaque future page, fonctionnalité, version, plugin, extension, intégration tierce, appareil ou version spécifique à une plateforme soit automatiquement conforme à la spécification.

Des produits, modules, services, révisions majeures ou builds propres à une plateforme peuvent nécessiter leur propre examen selon la catégorie de vérification demandée.

## Validité de la vérification

La vérification CatalystUI s’applique uniquement à l’état examiné du système au moment où elle est délivrée.

Un système peut conserver sa vérification lors de mises à jour ultérieures tant qu’il préserve la base d’accessibilité vérifiée. Les changements mineurs de formulation, les raffinements visuels, les améliorations de performance et les mises à jour ordinaires du contenu n’invalident pas automatiquement la vérification.

Un nouvel examen peut être requis si un système supprime des voies d’accès alternatives, rompt la prise en charge des technologies d’assistance, modifie substantiellement la navigation essentielle, supprime des paramètres d’accessibilité requis ou change le comportement d’interaction d’une manière qui affecte la base d’accessibilité vérifiée.

En d’autres termes, améliorer l’accessibilité est généralement acceptable. Rompre le modèle d’accès vérifié peut nécessiter un examen.

## Systèmes vérifiés

Les systèmes connus vérifiés pour l’accessibilité sont répertoriés séparément sur la page CatalystUI Verified appropriée.
