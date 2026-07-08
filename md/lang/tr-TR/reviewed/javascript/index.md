<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->
<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request içinde kaldırın. -->

# Review Details

## JavaScript

### Genel Bakış

JavaScript programlama dili, 7 Temmuz 2026 itibarıyla FDEFSPEC (Rev. 1) ve FRELSPEC (Rev. 1) spesifikasyonlarına göre incelenmiştir.

#### Review Statement

While JavaScript can represent some required concepts through objects, functions, arrays, and built-in language behavior, these mechanisms are not sufficient to satisfy the applicable CatalystUI specifications at the language level.

This review evaluates JavaScript itself, not the surrounding JavaScript ecosystem. Browser APIs, Node.js APIs, Deno APIs, Bun APIs, Web APIs, TypeScript, WebAssembly, external libraries, and custom validation are not treated as language-level support.

Because JavaScript lacks many required fixed-width scalar numeric types, does not provide required text encodings as language features, and does not define several required system, memory, threading, and composite constructs, we do not believe JavaScript provides a stable enough foundation for CatalystUI-compliant implementation without significant additional infrastructure.

As a result, JavaScript has not been granted CatalystUI Verified status for Programming Languages.

#### İnceleme Varsayımları

This review applies a strict language-level standard. If a provision is not explicitly supported by JavaScript itself, it is marked as not verified.

Host-provided APIs, implementation-specific behavior, external libraries, transpilers, type systems, and custom runtime validation are excluded from verification.

### Uyarılar

* JavaScript can represent many numeric values through `Number`, but `Number` is a 64-bit floating point numeric type.
* JavaScript provides `BigInt`, but `BigInt` is arbitrary-width.
* Typed arrays provide binary storage views, not scalar language types.
* JavaScript strings use UTF-16 code units, not explicit text encoding values.
* `const` protects bindings, not object values.

### Başarısızlıklar

* JavaScript does not provide most required fixed-width scalar numeric types.
* JavaScript does not provide a dedicated scalar 32-bit floating point type.
* JavaScript does not provide ASCII, CP1252, UTF-8, or UTF-16LE as language-level text encodings.
* JavaScript does not provide language-level file or stream constructs.
* JavaScript does not provide language-level address or pointer constructs.
* JavaScript does not provide language-level process, thread, or dispatcher constructs.
* JavaScript properties do not provide an explicit keyed member backed by a required Get/Set accessor map.
* JavaScript does not provide structures or interfaces.

### FDEFSPEC Doğrulaması

#### Sayısal Türler

| Hüküm | Doğrulandı | Notlar                          |
| --------- | -------- | ------------------------------ |
| Bit       | ❌        | No 1-bit numeric type.         |
| Nibble    | ❌        | No 4-bit numeric type.         |
| Byte      | ❌        | No scalar 8-bit integer type.  |
| Short     | ❌        | No scalar 16-bit integer type. |
| Int       | ❌        | No scalar 32-bit integer type. |
| Long      | ❌        | No scalar 64-bit integer type. |
| Float     | ❌        | No scalar 32-bit float type.   |
| Double    | ✅        | Şunun aracılığıyla desteklenir `Number`.    |
| Boolean   | ✅        | Şunun aracılığıyla desteklenir `boolean`.   |

#### Metin Kodlaması

| Hüküm | Doğrulandı | Notlar                        |
| --------- | -------- | ---------------------------- |
| Codepoint | ❌        | No dedicated codepoint type. |
| ASCII     | ❌        | Not language-level.          |
| CP1252    | ❌        | Not language-level.          |
| UTF-8     | ❌        | Not language-level.          |
| UTF-16LE  | ❌        | Not language-level.          |

#### İşlem Durumu

| Hüküm | Doğrulandı | Notlar                           |
| --------- | -------- | ------------------------------- |
| Status    | ⚠️       | Representable, not enforceable. |
| Context   | ⚠️       | Representable, not enforceable. |
| Operation | ⚠️       | Representable, not enforceable. |
| Detail    | ⚠️       | Representable, not enforceable. |
| Result    | ⚠️       | Gerektirir runtime validation.    |

### FRELSPEC Doğrulaması

#### Koleksiyonlar

| Hüküm | Doğrulandı | Notlar                    |
| --------- | -------- | ------------------------ |
| Set       | ✅        | Şunun aracılığıyla desteklenir `Set`. |
| Map       | ✅        | Şunun aracılığıyla desteklenir `Map`. |
| Array     | ✅        | Arrays are supported.    |
| File      | ❌        | Not language-level.      |
| Stream    | ❌        | Not language-level.      |

#### Bellek

| Hüküm | Doğrulandı | Notlar                           |
| --------- | -------- | ------------------------------- |
| Address   | ❌        | No address support.             |
| Pointer   | ❌        | No pointer support.             |
| Variable  | ✅        | Değişkenler desteklenir.        |
| Constant  | ⚠️       | `const` protects bindings only. |

#### İşlemler

| Provision   | Verified | Notes                            |
| ----------- | -------- | -------------------------------- |
| Instruction | ❌        | No defined instruction type.     |
| Procedure   | ❌        | Functions always return a value. |
| Function    | ✅        | Functions are supported.         |

#### İş Parçacığı

| Provision  | Verified | Notes                       |
| ---------- | -------- | --------------------------- |
| Process    | ❌        | Not language-level.         |
| Thread     | ⚠️        | Represented through agents. |
| Dispatcher | ❌        | Gerektirir host scheduling.   |


#### Bileşikler

| Hüküm | Doğrulandı | Notlar                                 |
| --------- | -------- | ------------------------------------- |
| Member    | ✅        | Object members are supported.         |
| Object    | ✅        | Nesneler desteklenir.                |
| Field     | ✅        | Data properties can represent fields. |
| Method    | ✅        | Metotlar desteklenir.                |
| Property  | ❌        | Açık accessor map yok.             |
| Structure | ❌        | No structure support.                 |
| Class     | ✅        | Class syntax is supported.            |
| Interface | ❌        | No interface support.                 |
