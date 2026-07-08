<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->
<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request içinde kaldırın. -->

# Doğrulama Ayrıntıları

## C#

### Genel Bakış

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


C# programlama dili, 7 Temmuz 2026 itibarıyla FDEFSPEC (Rev. 1) ve FRELSPEC (Rev. 1) spesifikasyonlarına göre doğrulanmıştır.

#### İyi Niyet Beyanı

C# programlama dilinin aşağıdaki spesifikasyonlarda tanımlanan kavramları ve hükümleri makul biçimde temsil edebileceğine ve bu spesifikasyonlara uygun sistemleri uygulamak için kullanılabileceğine iyi niyetle inanıyoruz.

#### İnceleme Varsayımları

Bu inceleme, sürüme bağlı özelliklerin belirtildiği yerlerde modern C# ve .NET desteğini varsayar.

### Uyarılar

* CP1252 support is available through the official .NET code pages provider, but may require provider registration or an additional package depending on the target runtime.
* Unsafe pointer behavior may require explicit unsafe authorization.

### Başarısızlıklar

* Bu doğrulama sırasında bilinen bir FDEFSPEC veya FRELSPEC başarısızlığı bulunmamıştır.

### FDEFSPEC Doğrulaması

#### Sayısal Türler

| Hüküm | Doğrulandı | Notlar                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | 1 bitlik sayısal tür yok; genişletin.                |
| Nibble    | ⚠️       | 4 bitlik sayısal tür yok; genişletin.                |
| Byte      | ✅        | Şunun aracılığıyla desteklenir `byte` and `sbyte`.   |
| Short     | ✅        | Şunun aracılığıyla desteklenir `short` and `ushort`. |
| Int       | ✅        | Şunun aracılığıyla desteklenir `int` and `uint`.     |
| Long      | ✅        | Şunun aracılığıyla desteklenir `long` and `ulong`.   |
| Float     | ✅        | Şunun aracılığıyla desteklenir `float`.              |
| Double    | ✅        | Şunun aracılığıyla desteklenir `double`.             |
| Boolean   | ✅        | Şunun aracılığıyla desteklenir `bool`.               |

#### Metin Kodlaması

| Hüküm | Doğrulandı | Notlar                                  |
| --------- | -------- | -------------------------------------- |
| Codepoint | ✅        | Şunun aracılığıyla desteklenir numerics and `Rune`. |
| ASCII     | ✅        | Şunun aracılığıyla desteklenir `Encoding.ASCII`.    |
| CP1252    | ⚠️       | Gerektirir code pages provider.          |
| UTF-8     | ✅        | Şunun aracılığıyla desteklenir `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | Şunun aracılığıyla desteklenir `Encoding.Unicode`.  |

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

| Hüküm | Doğrulandı | Notlar                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Şunun aracılığıyla desteklenir `HashSet<T>`.              |
| Map       | ✅        | Şunun aracılığıyla desteklenir `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Yerel diziler desteklenir.                 |
| File      | ✅        | Şunun aracılığıyla desteklenir file APIs.                 |
| Stream    | ✅        | Şunun aracılığıyla desteklenir `Stream`.                  |

#### Bellek

| Hüküm | Doğrulandı | Notlar                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Şunun aracılığıyla desteklenir references and pointers. |
| Pointer   | ✅        | Şunun aracılığıyla desteklenir unsafe pointers.         |
| Variable  | ✅        | Değişkenler desteklenir.                   |
| Constant  | ✅        | Şunun aracılığıyla desteklenir `const` and `readonly`.  |

#### İşlemler

| Provision   | Verified | Notes                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Represented through IL and operations. |
| Procedure   | ✅        | Şunun aracılığıyla desteklenir `void` methods.      |
| Function    | ✅        | Şunun aracılığıyla desteklenir returning methods.   |

#### İş Parçacığı

| Provision  | Verified | Notes                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Şunun aracılığıyla desteklenir application and `Process` APIs. |
| Thread     | ✅        | Şunun aracılığıyla desteklenir `Thread`.                       |
| Dispatcher | ✅        | Şunun aracılığıyla desteklenir tasks and schedulers.           |

#### Bileşikler

| Hüküm | Doğrulandı | Notlar                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Type members are supported.        |
| Object    | ✅        | Nesneler desteklenir.             |
| Field     | ✅        | Alanlar desteklenir.              |
| Method    | ✅        | Metotlar desteklenir.             |
| Property  | ✅        | Özellikler yerel olarak desteklenir. |
| Structure | ✅        | Yapılar yerel olarak desteklenir. |
| Class     | ✅        | Sınıflar desteklenir.             |
| Interface | ✅        | Arayüzler desteklenir.          |
