<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->
<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request içinde kaldırın. -->

# Doğrulama Ayrıntıları

## C++

### Genel Bakış

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C++ programlama dili, 7 Temmuz 2026 itibarıyla FDEFSPEC (Rev. 1) ve FRELSPEC (Rev. 1) spesifikasyonlarına göre doğrulanmıştır.

#### İyi Niyet Beyanı

C++ programlama dilinin aşağıdaki spesifikasyonlarda tanımlanan kavramları ve hükümleri makul biçimde temsil edebileceğine ve bu spesifikasyonlara uygun sistemleri uygulamak için kullanılabileceğine iyi niyetle inanıyoruz.

#### İnceleme Varsayımları

This review assumes modern standard C++ support where version-dependent features are noted. Exact-width integer support assumes the corresponding `<cstdint>` types are provided by the implementation.

This review treats C++ as a systems programming language with direct support for low-level representation, object modeling, memory control, generic programming, and concurrent execution.

### Uyarılar

* Exact-width integer types depend on implementation support.
* CP1252 can be represented byte-for-byte, but no named standard codec is provided.
* UTF-16LE serialization requires explicit byte-order handling.
* Some concurrency and character features require modern C++ revisions.

### Başarısızlıklar

* Bu doğrulama sırasında bilinen bir FDEFSPEC veya FRELSPEC başarısızlığı bulunmamıştır.

### FDEFSPEC Doğrulaması

#### Sayısal Türler

| Hüküm | Doğrulandı | Notlar                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Use bit-fields or masks.                    |
| Nibble    | ⚠️       | Use bit-fields or masks.                    |
| Byte      | ✅        | Şunun aracılığıyla desteklenir `std::byte`.              |
| Short     | ✅        | Şunun aracılığıyla desteklenir `int16_t` and `uint16_t`. |
| Int       | ✅        | Şunun aracılığıyla desteklenir `int32_t` and `uint32_t`. |
| Long      | ✅        | Şunun aracılığıyla desteklenir `int64_t` and `uint64_t`. |
| Float     | ✅        | Şunun aracılığıyla desteklenir `float`.                  |
| Double    | ✅        | Şunun aracılığıyla desteklenir `double`.                 |
| Boolean   | ✅        | Şunun aracılığıyla desteklenir `bool`.                   |

#### Metin Kodlaması

| Hüküm | Doğrulandı | Notlar                                |
| --------- | -------- | ------------------------------------ |
| Codepoint | ✅        | Şunun aracılığıyla desteklenir `char32_t`.        |
| ASCII     | ✅        | Şu şekilde temsil edilebilir byte values.        |
| CP1252    | ⚠️        | Gerektirir explicit byte mapping.      |
| UTF-8     | ✅        | Şunun aracılığıyla desteklenir `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Gerektirir byte-order handling.        |

#### İşlem Durumu

| Hüküm | Doğrulandı | Notlar                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Şununla temsil edilebilir an enum.           |
| Context   | ✅        | Şununla temsil edilebilir a value.           |
| Operation | ✅        | Şununla temsil edilebilir a value.           |
| Detail    | ✅        | Şununla temsil edilebilir a value.           |
| Result    | ✅        | Şununla temsil edilebilir a struct or class. |

### FRELSPEC Doğrulaması

#### Koleksiyonlar

| Hüküm | Doğrulandı | Notlar                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Şunun aracılığıyla desteklenir `std::set`.              |
| Map       | ✅        | Şunun aracılığıyla desteklenir `std::map`.              |
| Array     | ✅        | Şunun aracılığıyla desteklenir arrays and `std::array`. |
| File      | ✅        | Şunun aracılığıyla desteklenir file streams.            |
| Stream    | ✅        | Şunun aracılığıyla desteklenir iostreams.               |

#### Bellek

| Hüküm | Doğrulandı | Notlar                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Addresses are supported.                   |
| Pointer   | ✅        | Pointers are supported.                    |
| Variable  | ✅        | Değişkenler desteklenir.                   |
| Constant  | ✅        | Şunun aracılığıyla desteklenir `const` and `constexpr`. |

#### İşlemler

| Provision   | Verified | Notes                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | Şunun aracılığıyla desteklenir `void` functions.     |
| Function    | ✅        | Şunun aracılığıyla desteklenir returning functions.  |

#### İş Parçacığı

| Provision  | Verified | Notes                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Şunun aracılığıyla desteklenir hosted execution.      |
| Thread     | ✅        | Şunun aracılığıyla desteklenir `std::thread`; C++11+. |
| Dispatcher | ✅        | Şunun aracılığıyla desteklenir async and schedulers.  |

#### Bileşikler

| Hüküm | Doğrulandı | Notlar                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Class members are supported.            |
| Object    | ✅        | Nesneler desteklenir.                  |
| Field     | ✅        | Alanlar desteklenir.                   |
| Method    | ✅        | Metotlar desteklenir.                  |
| Property  | ✅        | Get/Set maps can be represented.        |
| Structure | ✅        | Yapılar yerel olarak desteklenir.      |
| Class     | ✅        | Classes are natively supported.         |
| Interface | ✅        | Şununla temsil edilebilir abstract classes. |
