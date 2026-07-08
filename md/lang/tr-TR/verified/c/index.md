<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->
<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request içinde kaldırın. -->

# Doğrulama Ayrıntıları

## C

### Genel Bakış

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C programlama dili, 7 Temmuz 2026 itibarıyla FDEFSPEC (Rev. 1) ve FRELSPEC (Rev. 1) spesifikasyonlarına göre doğrulanmıştır.

#### İyi Niyet Beyanı

C programlama dilinin aşağıdaki spesifikasyonlarda tanımlanan kavramları ve hükümleri makul biçimde temsil edebileceğine ve bu spesifikasyonlara uygun sistemleri uygulamak için kullanılabileceğine iyi niyetle inanıyoruz.

#### Review Statement

C provides strong low-level support for foundational data representation, memory access, files, streams, procedures, functions, structures, and direct system-oriented implementation.

While C does not natively provide several object-oriented composite constructs, these limitations are isolated to specific FRELSPEC composite provisions and are documented below. These failures do not prevent C from being considered within spec overall, but they should be understood when using C for CatalystUI-compatible implementations.

#### İnceleme Varsayımları

This review assumes modern standard C support where version-dependent features are noted. Exact-width integer support assumes the corresponding `<stdint.h>` types are provided by the implementation.

This review treats C as a low-level representation language. Byte-exact encodings may be represented directly through byte arrays, lookup tables, and explicit parsing logic when no named standard codec is provided.

### Uyarılar

* Exact-width integer types depend on implementation support.
* CP1252 can be represented byte-for-byte, but no named standard codec is provided.
* UTF-16LE serialization requires explicit byte-order handling.
* Standard threads may be omitted by some C implementations.
* Object-oriented patterns may be manually emulated, but are not native language constructs.

### Başarısızlıklar

* C does not provide native method members.
* C does not provide native properties.
* C does not provide native classes.
* C does not provide native interfaces.

### FDEFSPEC Doğrulaması

#### Sayısal Türler

| Hüküm | Doğrulandı | Notlar                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | Şunun aracılığıyla desteklenir `unsigned char`.          |
| Short     | ✅        | Şunun aracılığıyla desteklenir `int16_t` and `uint16_t`. |
| Int       | ✅        | Şunun aracılığıyla desteklenir `int32_t` and `uint32_t`. |
| Long      | ✅        | Şunun aracılığıyla desteklenir `int64_t` and `uint64_t`. |
| Float     | ✅        | Şunun aracılığıyla desteklenir `float`.                  |
| Double    | ✅        | Şunun aracılığıyla desteklenir `double`.                 |
| Boolean   | ✅        | Şunun aracılığıyla desteklenir `bool`; C99+.             |

#### Metin Kodlaması

| Hüküm | Doğrulandı | Notlar                                   |
| --------- | -------- | --------------------------------------- |
| Codepoint | ✅        | Şunun aracılığıyla desteklenir `char32_t`; C11+.     |
| ASCII     | ✅        | Şu şekilde temsil edilebilir byte values.           |
| CP1252    | ⚠️        | Gerektirir explicit byte mapping.         |
| UTF-8     | ✅        | Şunun aracılığıyla desteklenir UTF-8 literals; C11+. |
| UTF-16LE  | ⚠️        | Gerektirir byte-order handling.           |

#### İşlem Durumu

| Hüküm | Doğrulandı | Notlar                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Şununla temsil edilebilir an enum.  |
| Context   | ✅        | Şununla temsil edilebilir a value.  |
| Operation | ✅        | Şununla temsil edilebilir a value.  |
| Detail    | ✅        | Şununla temsil edilebilir a value.  |
| Result    | ✅        | Şununla temsil edilebilir a struct. |

### FRELSPEC Doğrulaması

#### Koleksiyonlar

| Hüküm | Doğrulandı | Notlar                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Şununla temsil edilebilir structs. |
| Map       | ✅        | Şununla temsil edilebilir structs. |
| Array     | ✅        | Yerel diziler desteklenir.   |
| File      | ✅        | Şunun aracılığıyla desteklenir file APIs.   |
| Stream    | ✅        | Şunun aracılığıyla desteklenir stream APIs. |

#### Bellek

| Hüküm | Doğrulandı | Notlar                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Addresses are supported.   |
| Pointer   | ✅        | Pointers are supported.    |
| Variable  | ✅        | Değişkenler desteklenir.   |
| Constant  | ✅        | Şunun aracılığıyla desteklenir `const`. |

#### İşlemler

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | Şunun aracılığıyla desteklenir `void` functions.     |
| Function    | ✅        | Şunun aracılığıyla desteklenir returning functions.  |

#### İş Parçacığı

| Provision  | Verified | Notes                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Şunun aracılığıyla desteklenir hosted environments. |
| Thread     | ⚠️        | Şunun aracılığıyla desteklenir `<threads.h>`; C11+. |
| Dispatcher | ✅        | Can be represented directly.           |

#### Bileşikler

| Hüküm | Doğrulandı | Notlar                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Struct members are supported.            |
| Object    | ✅        | Structs can form addressable composites. |
| Field     | ✅        | Struct fields are supported.             |
| Method    | ❌        | No native method members.                |
| Property  | ❌        | No explicit Get/Set accessor map.        |
| Structure | ✅        | Yapılar yerel olarak desteklenir.       |
| Class     | ❌        | No native class construct.               |
| Interface | ❌        | No native interface construct.           |
