<!-- Ang saling ito ay ginawa ng ChatGPT at dapat suriin ng isang taong tagapagsalin. -->
<!-- Alisin ang mga linyang ito sa isang pull request pagkatapos mapatunayan ang salin. -->

# Mga Detalye ng Beripikasyon

## C#

### Pangkalahatang-ideya

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Naberipika ang wikang pamprogramang C# laban sa mga espesipikasyong FDEFSPEC (Rev. 1) at FRELSPEC (Rev. 1) noong Hulyo 7, 2026.

#### Pahayag ng Mabuting Pananalig

We believe in good faith that the C# programming language can reasonably represent the concepts and provisions defined in the following specifications, and that it can be used to implement systems which are in compliance with these specifications.

#### Mga Palagay sa Pagsusuri

Ipinapalagay ng pagsusuring ito ang modernong suporta ng C# at .NET kung saan nakasaad ang version-dependent features.

### Mga Babala

* CP1252 support is available through the official .NET code pages provider, but may require provider registration or an additional package depending on the target runtime.
* Unsafe pointer behavior may require explicit unsafe authorization.

### Mga Pagkabigo

* Walang natagpuang kilalang failure sa FDEFSPEC o FRELSPEC sa panahon ng beripikasyong ito.

### Beripikasyon ng FDEFSPEC

#### Numerics

| Probisyon | Beripikado | Mga Tala                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | Walang 1-bit numeric; palawakin.                |
| Nibble    | ⚠️       | Walang 4-bit numeric; palawakin.                |
| Byte      | ✅        | Sinusuportahan sa pamamagitan ng `byte` and `sbyte`.   |
| Short     | ✅        | Sinusuportahan sa pamamagitan ng `short` and `ushort`. |
| Int       | ✅        | Sinusuportahan sa pamamagitan ng `int` and `uint`.     |
| Long      | ✅        | Sinusuportahan sa pamamagitan ng `long` and `ulong`.   |
| Float     | ✅        | Sinusuportahan sa pamamagitan ng `float`.              |
| Double    | ✅        | Sinusuportahan sa pamamagitan ng `double`.             |
| Boolean   | ✅        | Sinusuportahan sa pamamagitan ng `bool`.               |

#### Text Encoding

| Probisyon | Beripikado | Mga Tala                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | Sinusuportahan sa pamamagitan ng numerics and `Rune`. |
| ASCII     | ✅        | Sinusuportahan sa pamamagitan ng `Encoding.ASCII`.    |
| CP1252    | ⚠️       | Nangangailangan ng code pages provider.          |
| UTF-8     | ✅        | Sinusuportahan sa pamamagitan ng `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | Sinusuportahan sa pamamagitan ng `Encoding.Unicode`.  |

#### Status ng Operasyon

| Probisyon | Beripikado | Mga Tala                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Maaaring katawanin sa pamamagitan ng a custom type.        |
| Context   | ✅        | Maaaring katawanin sa pamamagitan ng a custom value.       |
| Operation | ✅        | Maaaring katawanin sa pamamagitan ng a custom value.       |
| Detail    | ✅        | Maaaring katawanin sa pamamagitan ng a custom value.       |
| Result    | ✅        | Maaaring katawanin sa pamamagitan ng a custom return type. |

### Beripikasyon ng FRELSPEC

#### Collections

| Probisyon | Beripikado | Mga Tala                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Sinusuportahan sa pamamagitan ng `HashSet<T>`.              |
| Map       | ✅        | Sinusuportahan sa pamamagitan ng `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Sinusuportahan ang native arrays.                 |
| File      | ✅        | Sinusuportahan sa pamamagitan ng file APIs.                 |
| Stream    | ✅        | Sinusuportahan sa pamamagitan ng `Stream`.                  |

#### Memory

| Probisyon | Beripikado | Mga Tala                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Sinusuportahan sa pamamagitan ng references and pointers. |
| Pointer   | ✅        | Sinusuportahan sa pamamagitan ng unsafe pointers.         |
| Variable  | ✅        | Sinusuportahan ang variables.                   |
| Constant  | ✅        | Sinusuportahan sa pamamagitan ng `const` and `readonly`.  |

#### Operations

| Provision   | Verified | Notes                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Represented through IL and operations. |
| Procedure   | ✅        | Sinusuportahan sa pamamagitan ng `void` methods.      |
| Function    | ✅        | Sinusuportahan sa pamamagitan ng returning methods.   |

#### Threading

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Sinusuportahan sa pamamagitan ng application and `Process` APIs. |
| Thread     | ✅        | Sinusuportahan sa pamamagitan ng `Thread`.                       |
| Dispatcher | ✅        | Sinusuportahan sa pamamagitan ng tasks and schedulers.           |

#### Composites

| Probisyon | Beripikado | Mga Tala                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Type members are supported.        |
| Object    | ✅        | Sinusuportahan ang objects.             |
| Field     | ✅        | Sinusuportahan ang fields.              |
| Method    | ✅        | Sinusuportahan ang methods.             |
| Property  | ✅        | Native na sinusuportahan ang properties. |
| Structure | ✅        | Native na sinusuportahan ang structures. |
| Class     | ✅        | Sinusuportahan ang classes.             |
| Interface | ✅        | Sinusuportahan ang interfaces.          |
