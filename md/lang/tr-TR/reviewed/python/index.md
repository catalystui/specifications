<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->
<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request içinde kaldırın. -->

# Review Details

## Python

### Genel Bakış

Python programlama dili, 7 Temmuz 2026 itibarıyla FDEFSPEC (Rev. 1) ve FRELSPEC (Rev. 1) spesifikasyonlarına göre incelenmiştir.

#### Review Statement

While Python can represent many required concepts through built-in types, objects, functions, classes, standard-library modules, and custom validation, these mechanisms are not sufficient to satisfy the applicable CatalystUI specifications at the language level.

Python provides strong support for text encoding, files, streams, objects, functions, classes, properties, processes, threads, and dispatched execution through its built-in behavior and standard library. However, Python does not provide the required fixed-width scalar numeric types, does not define true constants, and relies on dynamic runtime behavior for several constructs that other verified languages can express more directly.

Because of this, we do not believe Python provides a stable enough foundation for CatalystUI-compliant implementation without significant additional infrastructure.

As a result, Python has not been granted CatalystUI Verified status for Programming Languages.

#### İnceleme Varsayımları

This review evaluates Python itself and its bundled standard library.

Third-party packages, implementation-specific extensions, optional native modules, external type checkers, transpilers, and custom runtime frameworks are not treated as language-level support.

### Uyarılar

* Python provides unlimited-precision integers, not fixed-width integer primitives.
* Python `float` is usually double precision, but not a distinct fixed-width family.
* Some low-level memory behavior may require `ctypes` or implementation-specific behavior.
* Python type hints are not enforced at runtime.
* Python supports properties, but setter behavior may be omitted.
* Python can model several structures through standard-library features, but not as a native structure type.

### Başarısızlıklar

* Python does not provide most required fixed-width scalar numeric types.
* Python does not provide a dedicated scalar 32-bit floating point type.
* Python does not provide true language-level constants.
* Python does not define procedures separately from functions.
* Python does not provide native pointer support.
* Python does not provide native interface support.

### FDEFSPEC Doğrulaması

#### Sayısal Türler

| Hüküm | Doğrulandı | Notlar                                |
| --------- | -------- | ------------------------------------ |
| Bit       | ❌        | No 1-bit numeric type.               |
| Nibble    | ❌        | No 4-bit numeric type.               |
| Byte      | ❌        | No scalar 8-bit integer type.        |
| Short     | ❌        | No scalar 16-bit integer type.       |
| Int       | ❌        | No scalar 32-bit integer type.       |
| Long      | ❌        | No scalar 64-bit integer type.       |
| Float     | ❌        | No scalar 32-bit float type.         |
| Double    | ⚠️       | `float` is usually double precision. |
| Boolean   | ✅        | Şunun aracılığıyla desteklenir `bool`.            |

#### Metin Kodlaması

| Hüküm | Doğrulandı | Notlar                            |
| --------- | -------- | -------------------------------- |
| Codepoint | ✅        | Strings use Unicode code points. |
| ASCII     | ✅        | Supported codec.                 |
| CP1252    | ✅        | Supported codec.                 |
| UTF-8     | ✅        | Supported codec.                 |
| UTF-16LE  | ✅        | Supported codec.                 |

#### İşlem Durumu

| Hüküm | Doğrulandı | Notlar                       |
| --------- | -------- | --------------------------- |
| Status    | ⚠️       | Gerektirir custom validation. |
| Context   | ⚠️       | Gerektirir custom validation. |
| Operation | ⚠️       | Gerektirir custom validation. |
| Detail    | ⚠️       | Gerektirir custom validation. |
| Result    | ⚠️       | Gerektirir custom validation. |

### FRELSPEC Doğrulaması

#### Koleksiyonlar

| Hüküm | Doğrulandı | Notlar                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Şunun aracılığıyla desteklenir `set`.       |
| Map       | ✅        | Şunun aracılığıyla desteklenir `dict`.      |
| Array     | ✅        | Şunun aracılığıyla desteklenir sequences.   |
| File      | ✅        | Şunun aracılığıyla desteklenir file APIs.   |
| Stream    | ✅        | Şunun aracılığıyla desteklenir stream APIs. |

#### Bellek

| Hüküm | Doğrulandı | Notlar                        |
| --------- | -------- | ---------------------------- |
| Address   | ⚠️       | Object identity only.        |
| Pointer   | ❌        | No native pointer support.   |
| Variable  | ✅        | Name bindings are supported. |
| Constant  | ❌        | No true constants.           |

#### İşlemler

| Provision   | Verified | Notes                             |
| ----------- | -------- | --------------------------------- |
| Instruction | ⚠️       | Bytecode is implementation-level. |
| Procedure   | ❌        | Functions return `None`.          |
| Function    | ✅        | Functions are supported.          |

#### İş Parçacığı

| Provision  | Verified | Notes                            |
| ---------- | -------- | -------------------------------- |
| Process    | ✅        | Şunun aracılığıyla desteklenir process APIs.  |
| Thread     | ✅        | Şunun aracılığıyla desteklenir `threading`.   |
| Dispatcher | ✅        | Şunun aracılığıyla desteklenir executor APIs. |

#### Bileşikler

| Hüküm | Doğrulandı | Notlar                            |
| --------- | -------- | -------------------------------- |
| Member    | ✅        | Object members are supported.    |
| Object    | ✅        | Nesneler desteklenir.           |
| Field     | ✅        | Attributes can represent fields. |
| Method    | ✅        | Metotlar desteklenir.           |
| Property  | ⚠️       | Getter/setter support exists.    |
| Structure | ⚠️       | Standard-library models only.    |
| Class     | ✅        | Sınıflar desteklenir.           |
| Interface | ❌        | No native interface support.     |
