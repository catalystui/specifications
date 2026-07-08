<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->
<!-- Supprimez ces lignes dans une pull request une fois la traduction vérifiée. -->

# Détails de vérification

## Java

### Vue d’ensemble

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Le langage de programmation Java a été vérifié au regard des spécifications FDEFSPEC (Rév. 1) et FRELSPEC (Rév. 1) au 7 juillet 2026.

#### Déclaration de bonne foi

Nous croyons de bonne foi que le langage de programmation Java peut représenter raisonnablement une grande partie des concepts et dispositions définis dans les spécifications suivantes, et qu’il peut être utilisé pour implémenter des systèmes conformes à ces spécifications.

#### Hypothèses d’examen

Cet examen suppose la prise en charge du langage Java moderne lorsque les fonctionnalités dépendantes de la version sont indiquées. Des fonctionnalités telles que l’inférence de variables locales, les records et l’accès mémoire étranger peuvent nécessiter des versions plus récentes de Java.

### Avertissements

* Java ne prend pas en charge nativement les types numériques non signés, ce qui peut nécessiter un élargissement ou des représentations alternatives pour certaines dispositions.
* Le comportement d’adresse mémoire directe et de type pointeur peut nécessiter la prise en charge de la Foreign Function and Memory API de Java 22+.
* Java n’a pas de syntaxe native de propriétés, ce qui nécessite plutôt des méthodes getter et setter.

### Échecs

* Java ne fournit pas CP1252 comme jeu de caractères standard garanti, ce qui nécessite une prise en charge propre à l’implémentation, des bibliothèques supplémentaires ou une gestion personnalisée pour une conformité complète.
* Les propriétés Java ne fournissent pas de membre à clé explicite appuyé par une map d’accesseurs Get/Set requise.

### Vérification FDEFSPEC

#### Numériques

| Disposition | Vérifié | Notes                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | Aucun numérique 1 bit ; élargir.                         |
| Nibble    | ⚠️       | Aucun numérique 4 bits ; élargir.                         |
| Byte      | ⚠️       | Signé 8 bits seulement ; élargir pour le non signé.           |
| Short     | ⚠️       | Signé 16 bits seulement ; élargir pour le non signé.          |
| Int       | ⚠️       | Signé 32 bits ; les helpers non signés nécessitent Java 8+. |
| Long      | ⚠️       | Signé 64 bits ; les helpers non signés nécessitent Java 8+. |
| Float     | ✅        | Les flottants 32 bits sont pris en charge.              |
| Double    | ✅        | Les flottants 64 bits sont pris en charge.              |
| Boolean   | ✅        | Le type booléen est pris en charge.                       |

#### Encodage de texte

| Disposition | Vérifié | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Pris en charge via `int` et `Character`. |
| ASCII     | ✅        | Jeu de caractères standard garanti.             |
| CP1252    | ❌        | Non garanti par `StandardCharsets`.    |
| UTF-8     | ✅        | Jeu de caractères standard garanti.             |
| UTF-16LE  | ✅        | Jeu de caractères standard garanti.             |

#### État d’opération

| Disposition | Vérifié | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Peut être représenté par un type personnalisé.        |
| Context   | ✅        | Peut être représenté par une valeur personnalisée.       |
| Operation | ✅        | Peut être représenté par une valeur personnalisée.       |
| Detail    | ✅        | Peut être représenté par une valeur personnalisée.       |
| Result    | ✅        | Peut être représenté par un type de retour personnalisé. |

### Vérification FRELSPEC

#### Collections

| Disposition | Vérifié | Notes                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Pris en charge via `Set`.       |
| Map       | ✅        | Pris en charge via `Map`.       |
| Array     | ✅        | Les tableaux natifs sont pris en charge.   |
| File      | ✅        | Pris en charge via les API de fichiers.   |
| Stream    | ✅        | Pris en charge via les API de flux. |

#### Mémoire

| Disposition | Vérifié | Notes                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Les adresses directes nécessitent Java 22+ FFM.                         |
| Pointer   | ⚠️       | L’accès de type pointeur nécessite Java 22+ FFM.                     |
| Variable  | ✅        | Les déclarations et `var` sont pris en charge ; `var` nécessite Java 10+. |
| Constant  | ✅        | Pris en charge via `final`.                                     |

#### Opérations

| Disposition   | Vérifié | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Représenté par le bytecode et des opérations. |
| Procedure   | ✅        | Pris en charge via les méthodes `void`.            |
| Function    | ✅        | Pris en charge via les méthodes qui renvoient une valeur.         |

#### Threading

| Disposition  | Vérifié | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Pris en charge via les API d’application et `Process`. |
| Thread     | ✅        | Pris en charge via `Thread`.                       |
| Dispatcher | ✅        | Pris en charge via les API `Executor`.                |

#### Composites

| Disposition | Vérifié | Notes                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Les membres de classe sont pris en charge.           |
| Object    | ✅        | Les objets sont pris en charge.                 |
| Field     | ✅        | Les champs sont pris en charge.                  |
| Method    | ✅        | Les méthodes sont prises en charge.                 |
| Property  | ❌        | Aucune map explicite d’accesseurs.              |
| Structure | ✅        | Pris en charge via les records ; Java 16+.   |
| Class     | ✅        | Les classes sont prises en charge.                 |
| Interface | ✅        | Les interfaces sont prises en charge.              |
