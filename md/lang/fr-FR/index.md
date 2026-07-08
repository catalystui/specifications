<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->
<!-- Supprimez ces lignes dans une pull request une fois la traduction vérifiée. -->

![CatalystUI Verified for Programming Languages](/images/verification/verified-logo-languages.png)

# CatalystUI Verified pour les langages de programmation

Bienvenue dans la documentation de vérification CatalystUI pour les langages de programmation.

**CatalystUI Verified pour les langages de programmation** indique qu’un langage de programmation a été examiné par l’équipe CatalystUI et qu’il a été jugé capable de fournir les représentations de données fondamentales et les structures relationnelles nécessaires pour exprimer des systèmes compatibles avec CatalystUI.

Cette vérification n’est pas un classement général des langages de programmation. Elle ne décide pas si un langage est meilleur, plus rapide, plus simple, plus récent, plus populaire ou plus agréable qu’un autre. Elle identifie plutôt si le langage fournit une base stable et pratique pour les spécifications requises par la vérification CatalystUI.

En termes plus simples, cette vérification demande si un langage de programmation peut représenter fidèlement les données de base et les relations dont CatalystUI dépend.

## Objectif

Les langages de programmation forment la base représentationnelle située sous chaque implémentation CatalystUI. Avant qu’un framework, une bibliothèque, un runtime, une application ou un service puisse suivre la pile CatalystUI, le langage utilisé pour le construire doit être capable d’exprimer les concepts fondamentaux dont le modèle dépend.

Pour les langages de programmation, cela signifie principalement deux choses :

1. Le langage doit être capable de représenter des données fondamentales.
2. Le langage doit être capable de représenter des relations fondamentales entre les données.

Ces points sont définis par les spécifications fondamentales de CatalystUI. FDEFSPEC définit les représentations de données fondamentales attendues. FRELSPEC définit les relations fondamentales attendues entre ces représentations, notamment les collections, les relations de mémoire, les opérations, les relations de threading et les composites.

Un langage de programmation vérifié donne aux développeurs suffisamment de clarté et de contrôle pour construire des systèmes compatibles avec CatalystUI sans dépendre de contournements fragiles, peu clairs ou instables pour les concepts de base dont CatalystUI a besoin.

## Ce que signifie la vérification

Un langage de programmation devient **CatalystUI Verified** lorsqu’il est examiné au regard des spécifications indiquées dans cette section et jugé conforme à la spécification.

Pour la vérification des langages de programmation, l’examen porte sur la capacité du langage à exprimer les exigences fondamentales définies par les spécifications applicables. Cela ne signifie pas que le langage lui-même est une implémentation de CatalystUI. Cela signifie que le langage fournit une base appropriée à partir de laquelle des implémentations compatibles avec CatalystUI peuvent être construites.

Un langage n’a pas besoin de satisfaire ces exigences de la même manière qu’un autre langage. Les langages diffèrent par leur syntaxe, leurs systèmes de types, leurs bibliothèques standard, leurs compilateurs, leurs runtimes et leurs modèles de conception. La vérification CatalystUI autorise ces différences tant que les concepts requis peuvent être exprimés clairement, fiablement et de façon cohérente.

## Ce que signifie « Within Spec »

Lorsqu’un langage de programmation est considéré comme **within spec**, cela signifie que l’équipe CatalystUI a examiné manuellement le langage et a jugé raisonnable de conclure que le comportement requis décrit par les spécifications applicables peut être exprimé dans ce langage.

Cela n’impose pas un modèle d’implémentation rigide. Un langage peut satisfaire une exigence au moyen de primitives intégrées, de fonctionnalités de bibliothèque standard, du comportement du compilateur, du comportement du runtime, de garanties documentées ou de tout autre mécanisme stable approprié au langage.

La vérification concerne la capacité pratique à représenter et à préserver le sens de la spécification, et non le fait que le langage utilise exactement les mêmes noms, structures, syntaxes ou conceptions internes que le texte de la spécification.

## Pourquoi cette vérification existe

CatalystUI est conçu autour de la clarté, de la cohérence et de la représentation fidèle de la façon dont les humains et les ordinateurs interagissent. Les langages de programmation comptent parce qu’ils déterminent ce que les développeurs peuvent exprimer de manière réaliste, avec quel niveau de sûreté ces systèmes peuvent être modélisés, et avec quelle clarté des implémentations de plus haut niveau peuvent être construites.

Si un langage ne peut pas fournir les concepts fondamentaux requis de manière stable, les implémentations CatalystUI de plus haut niveau deviennent plus difficiles à garantir. Les développeurs peuvent être poussés vers des abstractions peu claires, des comportements imprévisibles, des dépendances fragiles ou des réécritures inutiles simplement pour exprimer des idées qui devraient être fiables dès le départ.

La vérification des langages de programmation existe pour identifier les langages qui fournissent une base suffisamment solide pour le travail CatalystUI. Elle donne aux développeurs, aux concepteurs de langages et aux organisations une compréhension plus claire de l’adéquation d’un langage à la construction de systèmes compatibles avec CatalystUI.

## Comment un langage est vérifié

Pour devenir **CatalystUI Verified pour les langages de programmation**, un langage doit être examiné au regard des spécifications indiquées dans cette section.

Le processus général est le suivant :

1. Les spécifications CatalystUI applicables sont identifiées.
2. Le langage est examiné au regard de chaque spécification requise.
3. L’équipe CatalystUI détermine si le langage satisfait l’intention et les exigences des spécifications.
4. Si le langage est jugé conforme à la spécification, la vérification CatalystUI peut lui être accordée.
5. Une fois vérifié, le langage peut être répertorié sur la page des [langages vérifiés](/verified/).

L’examen peut prendre en compte la documentation officielle du langage, le comportement de la bibliothèque standard, le comportement du compilateur, le comportement du runtime, des exemples d’implémentation, des cas de test et d’autres preuves nécessaires pour déterminer si le langage satisfait les exigences.

Le comportement du compilateur et du runtime peut être pris en compte lorsque ce comportement fait partie de l’utilisation courante et officielle du langage. Toutefois, vérifier un langage de programmation ne vérifie pas automatiquement tous les compilateurs, runtimes, paquets, frameworks, bibliothèques, applications ou outils de l’écosystème de ce langage.

## Spécifications applicables

Les spécifications indiquées dans cette section définissent les exigences utilisées pour la vérification des langages de programmation.

Pour les langages de programmation, la base active se concentre actuellement sur les catégories de spécifications suivantes :

* **FDEFSPEC**, qui définit les représentations de données fondamentales.
* **FRELSPEC**, qui définit les relations fondamentales entre les représentations de données.

Ensemble, ces spécifications établissent la base minimale nécessaire pour qu’un langage de programmation puisse représenter des systèmes compatibles avec CatalystUI.

Des spécifications supplémentaires pourront être introduites ultérieurement pour des catégories de vérification plus spécialisées. Ces spécifications pourront définir des exigences d’implémentation de plus haut niveau, de plateforme, d’accessibilité, d’internationalisation, de framework, de service ou de runtime. Toutefois, ces spécifications ultérieures s’appuient sur la base au lieu de la remplacer.

Un langage de programmation est vérifié en satisfaisant les spécifications requises pour cette catégorie. Il n’est pas censé satisfaire des exigences d’implémentation non liées, sauf si ces exigences sont ajoutées à la vérification des langages de programmation.

## Portée de la vérification

La vérification CatalystUI pour les langages de programmation s’applique au langage de programmation tel qu’il a été examiné.

Un langage vérifié fournit une base appropriée pour le développement compatible avec CatalystUI. Il ne garantit pas que chaque projet écrit dans ce langage suit correctement CatalystUI, et il ne vérifie pas automatiquement l’écosystème qui l’entoure.

Les outils, bibliothèques, frameworks, runtimes, applications, services ou implémentations indépendantes peuvent nécessiter leur propre examen selon la catégorie de vérification demandée.

Par conséquent, la vérification des langages de programmation doit être comprise comme une vérification de base. Elle confirme que le langage peut représenter les concepts requis. Elle ne confirme pas que chaque utilisation du langage applique correctement ces concepts.

## Validité de la vérification

La vérification CatalystUI s’applique uniquement à l’état examiné d’un langage de programmation au moment où la vérification est émise.

Les langages de programmation sont traités comme un cas particulier parce que de nombreux langages conservent la compatibilité sur plusieurs versions. Un langage peut conserver sa vérification dans les versions ultérieures tant qu’il préserve la compatibilité descendante avec les fonctionnalités, primitives, représentations et comportements dont dépendait l’examen initial.

Les nouvelles fonctionnalités du langage n’invalident pas à elles seules la vérification. Une vérification devient préoccupante lorsqu’un changement du langage supprime, modifie ou casse les capacités précédemment vérifiées d’une manière qui empêche le langage d’exprimer les exigences applicables.

Si vous pensez qu’un langage ou un service **CatalystUI Verified** a changé suffisamment pour que sa vérification ne soit plus valide, veuillez [nous contacter](mailto:contact@catalystui.org).

## Demander une vérification

Si vous souhaitez demander une vérification CatalystUI pour un langage de programmation, veuillez ouvrir une demande en utilisant le dépôt et le processus de vérification appropriés.

Une demande doit inclure le nom du langage, la version ou l’état du langage à examiner, la documentation officielle pertinente, ainsi que toute information utile permettant à l’équipe CatalystUI d’évaluer le langage au regard des spécifications applicables.

Des frais d’examen peuvent être exigés pour couvrir le temps nécessaire à l’évaluation. Les vérifications sont émises de bonne foi selon les informations disponibles au moment de l’examen.
