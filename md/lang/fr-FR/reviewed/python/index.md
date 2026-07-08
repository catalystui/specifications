<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->
<!-- Supprimez ces lignes dans une pull request une fois la traduction vérifiée. -->

# Détails d’examen

## Python

### Vue d’ensemble

Le langage de programmation Python a été examiné au regard des spécifications FDEFSPEC (Rév. 1) et FRELSPEC (Rév. 1) au 7 juillet 2026.

#### Déclaration d’examen

Même si Python peut représenter de nombreux concepts requis au moyen de types intégrés, d’objets, de fonctions, de classes, de modules de bibliothèque standard et d’une validation personnalisée, ces mécanismes ne sont pas suffisants pour satisfaire les spécifications CatalystUI applicables au niveau du langage.

Python fournit un solide support pour l’encodage de texte, les fichiers, les flux, les objets, les fonctions, les classes, les propriétés, les processus, les threads et l’exécution répartie au moyen de son comportement intégré et de sa bibliothèque standard. Toutefois, Python ne fournit pas les types numériques scalaires à largeur fixe requis, ne définit pas de véritables constantes et s’appuie sur un comportement dynamique à l’exécution pour plusieurs constructions que d’autres langages vérifiés peuvent exprimer plus directement.

Pour cette raison, nous ne pensons pas que Python fournisse une base suffisamment stable pour une implémentation conforme à CatalystUI sans infrastructure supplémentaire significative.

Par conséquent, Python n’a pas reçu le statut CatalystUI Verified pour les langages de programmation.

#### Hypothèses d’examen

Cet examen évalue Python lui-même ainsi que sa bibliothèque standard incluse.

Les paquets tiers, les extensions propres à une implémentation, les modules natifs facultatifs, les vérificateurs de types externes, les transpileurs et les frameworks de runtime personnalisés ne sont pas traités comme un support au niveau du langage.

### Avertissements

* Python fournit des entiers à précision illimitée, et non des primitives entières à largeur fixe.
* En Python, `float` est généralement en double précision, mais ne constitue pas une famille distincte à largeur fixe.
* Certains comportements mémoire bas niveau peuvent nécessiter `ctypes` ou un comportement propre à l’implémentation.
* Les indications de type de Python ne sont pas imposées à l’exécution.
* Python prend en charge les propriétés, mais le comportement de setter peut être omis.
* Python peut modéliser plusieurs structures au moyen de fonctionnalités de bibliothèque standard, mais pas comme un type structure natif.

### Échecs

* Python ne fournit pas la plupart des types numériques scalaires à largeur fixe requis.
* Python ne fournit pas de type scalaire dédié pour les flottants 32 bits.
* Python ne fournit pas de véritables constantes au niveau du langage.
* Python ne définit pas les procédures séparément des fonctions.
* Python ne fournit pas de support natif des pointeurs.
* Python ne fournit pas de support natif des interfaces.

### Vérification FDEFSPEC

#### Numériques

| Disposition | Vérifié | Notes                                |
| --------- | -------- | ------------------------------------ |
| Bit       | ❌        | Aucun type numérique 1 bit.               |
| Nibble    | ❌        | Aucun type numérique 4 bits.               |
| Byte      | ❌        | Aucun type entier scalaire 8 bits.        |
| Short     | ❌        | Aucun type entier scalaire 16 bits.       |
| Int       | ❌        | Aucun type entier scalaire 32 bits.       |
| Long      | ❌        | Aucun type entier scalaire 64 bits.       |
| Float     | ❌        | Aucun type flottant scalaire 32 bits.         |
| Double    | ⚠️       | `float` is usually double precision. |
| Boolean   | ✅        | Pris en charge via `bool`.            |

#### Encodage de texte

| Disposition | Vérifié | Notes                            |
| --------- | -------- | -------------------------------- |
| Codepoint | ✅        | Les chaînes utilisent des points de code Unicode. |
| ASCII     | ✅        | Codec pris en charge.                 |
| CP1252    | ✅        | Codec pris en charge.                 |
| UTF-8     | ✅        | Codec pris en charge.                 |
| UTF-16LE  | ✅        | Codec pris en charge.                 |

#### État d’opération

| Disposition | Vérifié | Notes                       |
| --------- | -------- | --------------------------- |
| Status    | ⚠️       | Nécessite une validation personnalisée. |
| Context   | ⚠️       | Nécessite une validation personnalisée. |
| Operation | ⚠️       | Nécessite une validation personnalisée. |
| Detail    | ⚠️       | Nécessite une validation personnalisée. |
| Result    | ⚠️       | Nécessite une validation personnalisée. |

### Vérification FRELSPEC

#### Collections

| Disposition | Vérifié | Notes                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Pris en charge via `set`.       |
| Map       | ✅        | Pris en charge via `dict`.      |
| Array     | ✅        | Pris en charge via les séquences.   |
| File      | ✅        | Pris en charge via les API de fichiers.   |
| Stream    | ✅        | Pris en charge via les API de flux. |

#### Mémoire

| Disposition | Vérifié | Notes                        |
| --------- | -------- | ---------------------------- |
| Address   | ⚠️       | Identité d’objet seulement.        |
| Pointer   | ❌        | Aucun support natif des pointeurs.   |
| Variable  | ✅        | Les liaisons de noms sont prises en charge. |
| Constant  | ❌        | Aucune vraie constante.           |

#### Opérations

| Disposition   | Vérifié | Notes                             |
| ----------- | -------- | --------------------------------- |
| Instruction | ⚠️       | Le bytecode relève de l’implémentation. |
| Procedure   | ❌        | Les fonctions renvoient `None`.          |
| Function    | ✅        | Les fonctions sont prises en charge.          |

#### Threading

| Disposition  | Vérifié | Notes                            |
| ---------- | -------- | -------------------------------- |
| Process    | ✅        | Pris en charge via les API de processus.  |
| Thread     | ✅        | Pris en charge via `threading`.   |
| Dispatcher | ✅        | Pris en charge via les API d’executor. |

#### Composites

| Disposition | Vérifié | Notes                            |
| --------- | -------- | -------------------------------- |
| Member    | ✅        | Les membres d’objet sont pris en charge.    |
| Object    | ✅        | Les objets sont pris en charge.           |
| Field     | ✅        | Les attributs peuvent représenter des champs. |
| Method    | ✅        | Les méthodes sont prises en charge.           |
| Property  | ⚠️       | Le support getter/setter existe.    |
| Structure | ⚠️       | Modèles de bibliothèque standard seulement.    |
| Class     | ✅        | Les classes sont prises en charge.           |
| Interface | ❌        | Aucun support natif des interfaces.     |
