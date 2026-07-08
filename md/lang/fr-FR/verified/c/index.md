<!-- Cette traduction a été générée par ChatGPT et doit être relue par un traducteur humain. -->
<!-- Supprimez ces lignes dans une pull request une fois la traduction vérifiée. -->

# Détails de vérification

## C

### Vue d’ensemble

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Le langage de programmation C a été vérifié au regard des spécifications FDEFSPEC (Rév. 1) et FRELSPEC (Rév. 1) au 7 juillet 2026.

#### Déclaration de bonne foi

Nous croyons de bonne foi que le langage de programmation C peut représenter raisonnablement les concepts et dispositions définis dans les spécifications suivantes, et qu’il peut être utilisé pour implémenter des systèmes conformes à ces spécifications.

#### Déclaration d’examen

C fournit un solide support bas niveau pour la représentation des données fondamentales, l’accès mémoire, les fichiers, les flux, les procédures, les fonctions, les structures et l’implémentation directe orientée système.

Même si C ne fournit pas nativement plusieurs constructions composites orientées objet, ces limites sont isolées à des dispositions composites précises de FRELSPEC et sont documentées ci-dessous. Ces échecs n’empêchent pas C d’être considéré comme globalement conforme à la spécification, mais ils doivent être compris lors de l’utilisation de C pour des implémentations compatibles avec CatalystUI.

#### Hypothèses d’examen

Cet examen suppose la prise en charge du C standard moderne lorsque les fonctionnalités dépendantes de la version sont indiquées. La prise en charge des entiers à largeur exacte suppose que les types `<stdint.h>` correspondants sont fournis par l’implémentation.

Cet examen traite C comme un langage de représentation bas niveau. Les encodages exacts à l’octet près peuvent être représentés directement par des tableaux d’octets, des tables de correspondance et une logique d’analyse explicite lorsqu’aucun codec standard nommé n’est fourni.

### Avertissements

* Les types entiers à largeur exacte dépendent de la prise en charge par l’implémentation.
* CP1252 peut être représenté octet par octet, mais aucun codec standard nommé n’est fourni.
* La sérialisation UTF-16LE nécessite une gestion explicite de l’ordre des octets.
* Les threads standard peuvent être omis par certaines implémentations de C.
* Les modèles orientés objet peuvent être émulés manuellement, mais ce ne sont pas des constructions natives du langage.

### Échecs

* C ne fournit pas de membres méthode natifs.
* C ne fournit pas de propriétés natives.
* C ne fournit pas de classes natives.
* C ne fournit pas d’interfaces natives.

### Vérification FDEFSPEC

#### Numériques

| Disposition | Vérifié | Notes                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Utiliser des champs de bits ou des masques.                    |
| Nibble    | ⚠️       | Utiliser des champs de bits ou des masques.                    |
| Byte      | ✅        | Pris en charge via `unsigned char`.          |
| Short     | ✅        | Pris en charge via `int16_t` et `uint16_t`. |
| Int       | ✅        | Pris en charge via `int32_t` et `uint32_t`. |
| Long      | ✅        | Pris en charge via `int64_t` et `uint64_t`. |
| Float     | ✅        | Pris en charge via `float`.                  |
| Double    | ✅        | Pris en charge via `double`.                 |
| Boolean   | ✅        | Pris en charge via `bool` ; C99+.             |

#### Encodage de texte

| Disposition | Vérifié | Notes                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | Pris en charge via `char32_t` ; C11+.     |
| ASCII     | ✅        | Représentable comme valeurs d’octets.           |
| CP1252    | ⚠️        | Nécessite un mappage explicite des octets.         |
| UTF-8     | ✅        | Pris en charge via les littéraux UTF-8 ; C11+. |
| UTF-16LE  | ⚠️        | Nécessite une gestion de l’ordre des octets.           |

#### État d’opération

| Disposition | Vérifié | Notes                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Peut être représenté par une enum.  |
| Context   | ✅        | Peut être représenté par une valeur.  |
| Operation | ✅        | Peut être représenté par une valeur.  |
| Detail    | ✅        | Peut être représenté par une valeur.  |
| Result    | ✅        | Peut être représenté par une struct. |

### Vérification FRELSPEC

#### Collections

| Disposition | Vérifié | Notes                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Peut être représenté par des structs. |
| Map       | ✅        | Peut être représenté par des structs. |
| Array     | ✅        | Les tableaux natifs sont pris en charge.   |
| File      | ✅        | Pris en charge via les API de fichiers.   |
| Stream    | ✅        | Pris en charge via les API de flux. |

#### Mémoire

| Disposition | Vérifié | Notes                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Les adresses sont prises en charge.   |
| Pointer   | ✅        | Les pointeurs sont pris en charge.    |
| Variable  | ✅        | Les variables sont prises en charge.   |
| Constant  | ✅        | Pris en charge via `const`. |

#### Opérations

| Disposition   | Vérifié | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Représenté par des opérations machine. |
| Procedure   | ✅        | Pris en charge via les fonctions `void`.     |
| Function    | ✅        | Pris en charge via les fonctions qui renvoient une valeur.  |

#### Threading

| Disposition  | Vérifié | Notes                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Pris en charge via les environnements hébergés. |
| Thread     | ⚠️        | Pris en charge via `<threads.h>` ; C11+. |
| Dispatcher | ✅        | Peut être représenté directement.           |

#### Composites

| Disposition | Vérifié | Notes                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Les membres de struct sont pris en charge.            |
| Object    | ✅        | Les structs peuvent former des composites adressables. |
| Field     | ✅        | Les champs de struct sont pris en charge.             |
| Method    | ❌        | Aucun membre méthode natif.                |
| Property  | ❌        | Aucune map explicite d’accesseurs Get/Set.        |
| Structure | ✅        | Les structures sont prises en charge nativement.       |
| Class     | ❌        | Aucune construction de classe native.               |
| Interface | ❌        | Aucune construction d’interface native.           |
