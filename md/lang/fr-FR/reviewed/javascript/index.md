<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->
<!-- Supprimez ces lignes dans une pull request une fois la traduction vérifiée. -->

# Détails d’examen

## JavaScript

### Vue d’ensemble

Le langage de programmation JavaScript a été examiné au regard des spécifications FDEFSPEC (Rév. 1) et FRELSPEC (Rév. 1) au 7 juillet 2026.

#### Déclaration d’examen

Même si JavaScript peut représenter certains concepts requis au moyen d’objets, de fonctions, de tableaux et du comportement intégré du langage, ces mécanismes ne sont pas suffisants pour satisfaire les spécifications CatalystUI applicables au niveau du langage.

Cet examen évalue JavaScript lui-même, et non l’écosystème JavaScript qui l’entoure. Les API de navigateur, les API Node.js, les API Deno, les API Bun, les Web APIs, TypeScript, WebAssembly, les bibliothèques externes et la validation personnalisée ne sont pas traités comme un support au niveau du langage.

Comme JavaScript ne possède pas de nombreux types numériques scalaires à largeur fixe requis, ne fournit pas les encodages de texte requis comme fonctionnalités du langage et ne définit pas plusieurs constructions système, mémoire, threading et composites requises, nous ne pensons pas que JavaScript fournisse une base suffisamment stable pour une implémentation conforme à CatalystUI sans infrastructure supplémentaire significative.

Par conséquent, JavaScript n’a pas reçu le statut CatalystUI Verified pour les langages de programmation.

#### Hypothèses d’examen

Cet examen applique un standard strict au niveau du langage. Si une disposition n’est pas explicitement prise en charge par JavaScript lui-même, elle est marquée comme non vérifiée.

Les API fournies par l’hôte, les comportements propres à une implémentation, les bibliothèques externes, les transpileurs, les systèmes de types et la validation personnalisée à l’exécution sont exclus de la vérification.

### Avertissements

* JavaScript peut représenter de nombreuses valeurs numériques via `Number`, mais `Number` est un type numérique à virgule flottante 64 bits.
* JavaScript fournit `BigInt`, mais `BigInt` est à largeur arbitraire.
* Les tableaux typés fournissent des vues de stockage binaire, et non des types scalaires du langage.
* Les chaînes JavaScript utilisent des unités de code UTF-16, et non des valeurs explicites d’encodage de texte.
* `const` protège les liaisons, et non les valeurs des objets.

### Échecs

* JavaScript ne fournit pas la plupart des types numériques scalaires à largeur fixe requis.
* JavaScript ne fournit pas de type scalaire dédié pour les flottants 32 bits.
* JavaScript ne fournit pas ASCII, CP1252, UTF-8 ou UTF-16LE comme encodages de texte au niveau du langage.
* JavaScript ne fournit pas de constructions de fichiers ou de flux au niveau du langage.
* JavaScript ne fournit pas de constructions d’adresse ou de pointeur au niveau du langage.
* JavaScript ne fournit pas de constructions de processus, de thread ou de répartiteur au niveau du langage.
* Les propriétés JavaScript ne fournissent pas de membre à clé explicite appuyé par une map d’accesseurs Get/Set requise.
* JavaScript ne fournit pas de structures ni d’interfaces.

### Vérification FDEFSPEC

#### Numériques

| Disposition | Vérifié | Notes                          |
| --------- | -------- | ------------------------------ |
| Bit       | ❌        | Aucun type numérique 1 bit.         |
| Nibble    | ❌        | Aucun type numérique 4 bits.         |
| Byte      | ❌        | Aucun type entier scalaire 8 bits.  |
| Short     | ❌        | Aucun type entier scalaire 16 bits. |
| Int       | ❌        | Aucun type entier scalaire 32 bits. |
| Long      | ❌        | Aucun type entier scalaire 64 bits. |
| Float     | ❌        | Aucun type flottant scalaire 32 bits.   |
| Double    | ✅        | Pris en charge via `Number`.    |
| Boolean   | ✅        | Pris en charge via `boolean`.   |

#### Encodage de texte

| Disposition | Vérifié | Notes                        |
| --------- | -------- | ---------------------------- |
| Codepoint | ❌        | Aucun type dédié pour les points de code. |
| ASCII     | ❌        | Pas au niveau du langage.          |
| CP1252    | ❌        | Pas au niveau du langage.          |
| UTF-8     | ❌        | Pas au niveau du langage.          |
| UTF-16LE  | ❌        | Pas au niveau du langage.          |

#### État d’opération

| Disposition | Vérifié | Notes                           |
| --------- | -------- | ------------------------------- |
| Status    | ⚠️       | Représentable, mais non imposable. |
| Context   | ⚠️       | Représentable, mais non imposable. |
| Operation | ⚠️       | Représentable, mais non imposable. |
| Detail    | ⚠️       | Représentable, mais non imposable. |
| Result    | ⚠️       | Nécessite une validation à l’exécution.    |

### Vérification FRELSPEC

#### Collections

| Disposition | Vérifié | Notes                    |
| --------- | -------- | ------------------------ |
| Set       | ✅        | Pris en charge via `Set`. |
| Map       | ✅        | Pris en charge via `Map`. |
| Array     | ✅        | Les tableaux sont pris en charge.    |
| File      | ❌        | Pas au niveau du langage.      |
| Stream    | ❌        | Pas au niveau du langage.      |

#### Mémoire

| Disposition | Vérifié | Notes                           |
| --------- | -------- | ------------------------------- |
| Address   | ❌        | Aucun support des adresses.             |
| Pointer   | ❌        | Aucun support des pointeurs.             |
| Variable  | ✅        | Les variables sont prises en charge.        |
| Constant  | ⚠️       | `const` protège uniquement les liaisons. |

#### Opérations

| Disposition   | Vérifié | Notes                            |
| ----------- | -------- | -------------------------------- |
| Instruction | ❌        | Aucun type d’instruction défini.     |
| Procedure   | ❌        | Les fonctions renvoient toujours une valeur. |
| Function    | ✅        | Les fonctions sont prises en charge.         |

#### Threading

| Disposition  | Vérifié | Notes                       |
| ---------- | -------- | --------------------------- |
| Process    | ❌        | Pas au niveau du langage.         |
| Thread     | ⚠️        | Représenté via les agents. |
| Dispatcher | ❌        | Nécessite une planification par l’hôte.   |


#### Composites

| Disposition | Vérifié | Notes                                 |
| --------- | -------- | ------------------------------------- |
| Member    | ✅        | Les membres d’objet sont pris en charge.         |
| Object    | ✅        | Les objets sont pris en charge.                |
| Field     | ✅        | Les propriétés de données peuvent représenter des champs. |
| Method    | ✅        | Les méthodes sont prises en charge.                |
| Property  | ❌        | Aucune map explicite d’accesseurs.             |
| Structure | ❌        | Aucun support des structures.                 |
| Class     | ✅        | La syntaxe de classe est prise en charge.            |
| Interface | ❌        | Aucun support des interfaces.                 |
