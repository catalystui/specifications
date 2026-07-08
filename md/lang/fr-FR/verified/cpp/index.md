<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->
<!-- Supprimez ces lignes dans une pull request une fois la traduction vérifiée. -->

# Détails de vérification

## C++

### Vue d’ensemble

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Le langage de programmation C++ a été vérifié au regard des spécifications FDEFSPEC (Rév. 1) et FRELSPEC (Rév. 1) au 7 juillet 2026.

#### Déclaration de bonne foi

Nous croyons de bonne foi que le langage de programmation C++ peut représenter raisonnablement les concepts et dispositions définis dans les spécifications suivantes, et qu’il peut être utilisé pour implémenter des systèmes conformes à ces spécifications.

#### Hypothèses d’examen

Cet examen suppose la prise en charge du C++ standard moderne lorsque les fonctionnalités dépendantes de la version sont indiquées. La prise en charge des entiers à largeur exacte suppose que les types `<cstdint>` correspondants sont fournis par l’implémentation.

Cet examen traite C++ comme un langage de programmation système offrant un support direct pour la représentation bas niveau, la modélisation objet, le contrôle mémoire, la programmation générique et l’exécution concurrente.

### Avertissements

* Les types entiers à largeur exacte dépendent de la prise en charge par l’implémentation.
* CP1252 peut être représenté octet par octet, mais aucun codec standard nommé n’est fourni.
* La sérialisation UTF-16LE nécessite une gestion explicite de l’ordre des octets.
* Certaines fonctionnalités de concurrence et de caractères nécessitent des révisions modernes de C++.

### Échecs

* Aucun échec FDEFSPEC ou FRELSPEC connu n’a été trouvé pendant cette vérification.

### Vérification FDEFSPEC

#### Numériques

| Disposition | Vérifié | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Utiliser des champs de bits ou des masques.                    |
| Nibble    | ⚠️       | Utiliser des champs de bits ou des masques.                    |
| Byte      | ✅        | Pris en charge via `std::byte`.              |
| Short     | ✅        | Pris en charge via `int16_t` et `uint16_t`. |
| Int       | ✅        | Pris en charge via `int32_t` et `uint32_t`. |
| Long      | ✅        | Pris en charge via `int64_t` et `uint64_t`. |
| Float     | ✅        | Pris en charge via `float`.                  |
| Double    | ✅        | Pris en charge via `double`.                 |
| Boolean   | ✅        | Pris en charge via `bool`.                   |

#### Encodage de texte

| Disposition | Vérifié | Notes                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Pris en charge via `char32_t`.        |
| ASCII     | ✅        | Représentable comme valeurs d’octets.        |
| CP1252    | ⚠️        | Nécessite un mappage explicite des octets.      |
| UTF-8     | ✅        | Pris en charge via `char8_t` ; C++20+. |
| UTF-16LE  | ⚠️        | Nécessite une gestion de l’ordre des octets.        |

#### État d’opération

| Disposition | Vérifié | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Peut être représenté par une enum.           |
| Context   | ✅        | Peut être représenté par une valeur.           |
| Operation | ✅        | Peut être représenté par une valeur.           |
| Detail    | ✅        | Peut être représenté par une valeur.           |
| Result    | ✅        | Peut être représenté par une struct ou une classe. |

### Vérification FRELSPEC

#### Collections

| Disposition | Vérifié | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Pris en charge via `std::set`.              |
| Map       | ✅        | Pris en charge via `std::map`.              |
| Array     | ✅        | Pris en charge via les tableaux et `std::array`. |
| File      | ✅        | Pris en charge via les flux de fichiers.            |
| Stream    | ✅        | Pris en charge via les iostreams.               |

#### Mémoire

| Disposition | Vérifié | Notes                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Les adresses sont prises en charge.                   |
| Pointer   | ✅        | Les pointeurs sont pris en charge.                    |
| Variable  | ✅        | Les variables sont prises en charge.                   |
| Constant  | ✅        | Pris en charge via `const` et `constexpr`. |

#### Opérations

| Disposition   | Vérifié | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Représenté par des opérations machine. |
| Procedure   | ✅        | Pris en charge via les fonctions `void`.     |
| Function    | ✅        | Pris en charge via les fonctions qui renvoient une valeur.  |

#### Threading

| Disposition  | Vérifié | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Pris en charge via l’exécution hébergée.      |
| Thread     | ✅        | Pris en charge via `std::thread` ; C++11+. |
| Dispatcher | ✅        | Pris en charge via async et les ordonnanceurs.  |

#### Composites

| Disposition | Vérifié | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Les membres de classe sont pris en charge.            |
| Object    | ✅        | Les objets sont pris en charge.                  |
| Field     | ✅        | Les champs sont pris en charge.                   |
| Method    | ✅        | Les méthodes sont prises en charge.                  |
| Property  | ✅        | Les maps Get/Set peuvent être représentées.        |
| Structure | ✅        | Les structures sont prises en charge nativement.      |
| Class     | ✅        | Les classes sont prises en charge nativement.         |
| Interface | ✅        | Peut être représenté par des classes abstraites. |
