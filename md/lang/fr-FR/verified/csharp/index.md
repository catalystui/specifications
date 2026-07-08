<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->
<!-- Supprimez ces lignes dans une pull request une fois la traduction vérifiée. -->

# Détails de vérification

## C#

### Vue d’ensemble

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Le langage de programmation C# a été vérifié au regard des spécifications FDEFSPEC (Rév. 1) et FRELSPEC (Rév. 1) au 7 juillet 2026.

#### Déclaration de bonne foi

Nous croyons de bonne foi que le langage de programmation C# peut représenter raisonnablement les concepts et dispositions définis dans les spécifications suivantes, et qu’il peut être utilisé pour implémenter des systèmes conformes à ces spécifications.

#### Hypothèses d’examen

Cet examen suppose la prise en charge du C# moderne et de .NET lorsque les fonctionnalités dépendantes de la version sont indiquées.

### Avertissements

* La prise en charge de CP1252 est disponible via le fournisseur officiel de pages de codes .NET, mais peut nécessiter l’enregistrement du fournisseur ou un paquet supplémentaire selon le runtime cible.
* Le comportement des pointeurs unsafe peut nécessiter une autorisation unsafe explicite.

### Échecs

* Aucun échec FDEFSPEC ou FRELSPEC connu n’a été trouvé pendant cette vérification.

### Vérification FDEFSPEC

#### Numériques

| Disposition | Vérifié | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | Aucun numérique 1 bit ; élargir.                |
| Nibble    | ⚠️       | Aucun numérique 4 bits ; élargir.                |
| Byte      | ✅        | Pris en charge via `byte` et `sbyte`.   |
| Short     | ✅        | Pris en charge via `short` et `ushort`. |
| Int       | ✅        | Pris en charge via `int` et `uint`.     |
| Long      | ✅        | Pris en charge via `long` et `ulong`.   |
| Float     | ✅        | Pris en charge via `float`.              |
| Double    | ✅        | Pris en charge via `double`.             |
| Boolean   | ✅        | Pris en charge via `bool`.               |

#### Encodage de texte

| Disposition | Vérifié | Notes                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | Pris en charge via les numériques et `Rune`. |
| ASCII     | ✅        | Pris en charge via `Encoding.ASCII`.    |
| CP1252    | ⚠️       | Nécessite un fournisseur de pages de codes.          |
| UTF-8     | ✅        | Pris en charge via `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | Pris en charge via `Encoding.Unicode`.  |

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

| Disposition | Vérifié | Notes                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Pris en charge via `HashSet<T>`.              |
| Map       | ✅        | Pris en charge via `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Les tableaux natifs sont pris en charge.                 |
| File      | ✅        | Pris en charge via les API de fichiers.                 |
| Stream    | ✅        | Pris en charge via `Stream`.                  |

#### Mémoire

| Disposition | Vérifié | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Pris en charge via les références et les pointeurs. |
| Pointer   | ✅        | Pris en charge via les pointeurs unsafe.         |
| Variable  | ✅        | Les variables sont prises en charge.                   |
| Constant  | ✅        | Pris en charge via `const` et `readonly`.  |

#### Opérations

| Disposition   | Vérifié | Notes                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Représenté par IL et des opérations. |
| Procedure   | ✅        | Pris en charge via les méthodes `void`.      |
| Function    | ✅        | Pris en charge via les méthodes qui renvoient une valeur.   |

#### Threading

| Disposition  | Vérifié | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Pris en charge via les API d’application et `Process`. |
| Thread     | ✅        | Pris en charge via `Thread`.                       |
| Dispatcher | ✅        | Pris en charge via les tâches et les ordonnanceurs.           |

#### Composites

| Disposition | Vérifié | Notes                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Les membres de type sont pris en charge.        |
| Object    | ✅        | Les objets sont pris en charge.             |
| Field     | ✅        | Les champs sont pris en charge.              |
| Method    | ✅        | Les méthodes sont prises en charge.             |
| Property  | ✅        | Les propriétés sont prises en charge nativement. |
| Structure | ✅        | Les structures sont prises en charge nativement. |
| Class     | ✅        | Les classes sont prises en charge.             |
| Interface | ✅        | Les interfaces sont prises en charge.          |
