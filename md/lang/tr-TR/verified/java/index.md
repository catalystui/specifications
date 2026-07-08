<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->
<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request içinde kaldırın. -->

# Doğrulama Ayrıntıları

## Java

### Genel Bakış

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Java programlama dili, 7 Temmuz 2026 itibarıyla FDEFSPEC (Rev. 1) ve FRELSPEC (Rev. 1) spesifikasyonlarına göre doğrulanmıştır.

#### İyi Niyet Beyanı

Java programlama dilinin aşağıdaki spesifikasyonlarda tanımlanan kavramların ve hükümlerin büyük bir kısmını makul biçimde temsil edebileceğine ve bu spesifikasyonlara uygun sistemleri uygulamak için kullanılabileceğine iyi niyetle inanıyoruz.

#### İnceleme Varsayımları

This review assumes modern Java language support where version-dependent features are noted. Features such as local variable inference, records, and foreign memory access may require later Java versions.

### Uyarılar

* Java does not have native support for unsigned numeric types, which may require widening or alternative representations for certain provisions.
* Direct memory address and pointer-style behavior may require Java 22+ Foreign Function and Memory API support.
* Java does not have native property syntax, requiring getter and setter methods instead.

### Başarısızlıklar

* Java does not provide CP1252 as a guaranteed standard charset, requiring implementation-specific support, additional libraries, or custom handling for full compliance.
* Java properties do not provide an explicit keyed member backed by a required Get/Set accessor map.

### FDEFSPEC Doğrulaması

#### Sayısal Türler

| Hüküm | Doğrulandı | Notlar                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | 1 bitlik sayısal tür yok; genişletin.                         |
| Nibble    | ⚠️       | 4 bitlik sayısal tür yok; genişletin.                         |
| Byte      | ⚠️       | Signed 8-bit only; widen for unsigned.           |
| Short     | ⚠️       | Signed 16-bit only; widen for unsigned.          |
| Int       | ⚠️       | Signed 32-bit; unsigned helpers require Java 8+. |
| Long      | ⚠️       | Signed 64-bit; unsigned helpers require Java 8+. |
| Float     | ✅        | 32-bit floating point is supported.              |
| Double    | ✅        | 64-bit floating point is supported.              |
| Boolean   | ✅        | Boolean type is supported.                       |

#### Metin Kodlaması

| Hüküm | Doğrulandı | Notlar                                    |
| --------- | -------- | ---------------------------------------- |
| Codepoint | ✅        | Şunun aracılığıyla desteklenir `int` and `Character`. |
| ASCII     | ✅        | Garantili standart karakter kümesi.             |
| CP1252    | ❌        | Tarafından garanti edilmez `StandardCharsets`.    |
| UTF-8     | ✅        | Garantili standart karakter kümesi.             |
| UTF-16LE  | ✅        | Garantili standart karakter kümesi.             |

#### İşlem Durumu

| Hüküm | Doğrulandı | Notlar                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Şununla temsil edilebilir a custom type.        |
| Context   | ✅        | Şununla temsil edilebilir a custom value.       |
| Operation | ✅        | Şununla temsil edilebilir a custom value.       |
| Detail    | ✅        | Şununla temsil edilebilir a custom value.       |
| Result    | ✅        | Şununla temsil edilebilir a custom return type. |

### FRELSPEC Doğrulaması

#### Koleksiyonlar

| Hüküm | Doğrulandı | Notlar                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Şunun aracılığıyla desteklenir `Set`.       |
| Map       | ✅        | Şunun aracılığıyla desteklenir `Map`.       |
| Array     | ✅        | Yerel diziler desteklenir.   |
| File      | ✅        | Şunun aracılığıyla desteklenir file APIs.   |
| Stream    | ✅        | Şunun aracılığıyla desteklenir stream APIs. |

#### Bellek

| Hüküm | Doğrulandı | Notlar                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Direct addresses require Java 22+ FFM.                         |
| Pointer   | ⚠️       | Pointer-like access requires Java 22+ FFM.                     |
| Variable  | ✅        | Declarations and `var` are supported; `var` requires Java 10+. |
| Constant  | ✅        | Şunun aracılığıyla desteklenir `final`.                                     |

#### İşlemler

| Provision   | Verified | Notes                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Represented through bytecode and operations. |
| Procedure   | ✅        | Şunun aracılığıyla desteklenir `void` methods.            |
| Function    | ✅        | Şunun aracılığıyla desteklenir returning methods.         |

#### İş Parçacığı

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Şunun aracılığıyla desteklenir application and `Process` APIs. |
| Thread     | ✅        | Şunun aracılığıyla desteklenir `Thread`.                       |
| Dispatcher | ✅        | Şunun aracılığıyla desteklenir `Executor` APIs.                |

#### Bileşikler

| Hüküm | Doğrulandı | Notlar                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Class members are supported.           |
| Object    | ✅        | Nesneler desteklenir.                 |
| Field     | ✅        | Alanlar desteklenir.                  |
| Method    | ✅        | Metotlar desteklenir.                 |
| Property  | ❌        | Açık accessor map yok.              |
| Structure | ✅        | Şunun aracılığıyla desteklenir records; Java 16+.   |
| Class     | ✅        | Sınıflar desteklenir.                 |
| Interface | ✅        | Arayüzler desteklenir.              |
