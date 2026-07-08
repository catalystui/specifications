<!-- Bu çeviri ChatGPT tarafından oluşturulmuştur ve bir insan çevirmen tarafından gözden geçirilmelidir. -->
<!-- Çeviri doğrulandıktan sonra bu satırları bir pull request içinde kaldırın. -->

![CatalystUI Verified for Programming Languages](/images/verification/verified-logo-languages.png)

# Programlama Dilleri için CatalystUI Verified

Programlama dilleri için CatalystUI Verification belgelerine hoş geldiniz.

**Programlama Dilleri için CatalystUI Verified**, bir programlama dilinin CatalystUI Ekibi tarafından incelendiğini ve CatalystUI uyumlu sistemleri ifade etmek için gereken temel veri temsillerini ve ilişkisel yapıları sağladığının belirlendiğini gösterir.

Bu doğrulama, programlama dillerinin genel bir sıralaması değildir. Bir dilin başka bir dilden daha iyi, daha hızlı, daha kolay, daha yeni, daha popüler veya daha keyifli olup olmadığına karar vermez. Bunun yerine, dilin CatalystUI Verification tarafından gereken spesifikasyonlar için kararlı ve pratik bir temel sağlayıp sağlamadığını belirler.

Daha basit bir ifadeyle bu doğrulama, bir programlama dilinin CatalystUI'nin dayandığı temel verileri ve ilişkileri doğru şekilde temsil edip edemediğini sorar.

## Amaç

Programlama dilleri, her CatalystUI uygulamasının altındaki temsil temelini oluşturur. Bir framework, kütüphane, runtime, uygulama veya hizmet CatalystUI Stack'i izleyebilmeden önce, onu oluşturmak için kullanılan dilin modelin dayandığı temel kavramları ifade edebilmesi gerekir.

Programlama dilleri için bu öncelikle iki anlama gelir:

1. Dil, temel verileri temsil edebilmelidir.
2. Dil, veriler arasındaki temel ilişkileri temsil edebilmelidir.

Bu konular, temel CatalystUI spesifikasyonları aracılığıyla tanımlanır. FDEFSPEC beklenen temel veri temsillerini tanımlar. FRELSPEC ise koleksiyonlar, bellek ilişkileri, işlemler, iş parçacığı ilişkileri ve bileşikler dahil olmak üzere bu temsiller arasındaki beklenen temel ilişkileri tanımlar.

Doğrulanmış bir programlama dili, geliştiricilere CatalystUI'nin gerektirdiği temel kavramlar için kırılgan, belirsiz veya kararsız geçici çözümlere güvenmeden CatalystUI uyumlu sistemler oluşturacak kadar açıklık ve denetim sağlar.

## Doğrulama Ne Anlama Gelir

Bir programlama dili, bu bölümde listelenen spesifikasyonlara göre incelendiğinde ve spesifikasyon dahilinde bulunduğunda **CatalystUI Verified** olur.

Programming Language Verification için inceleme, dilin geçerli spesifikasyonlarda tanımlanan temel gereksinimleri ifade edip edemediğine odaklanır. Bu, dilin kendisinin bir CatalystUI uygulaması olduğu anlamına gelmez. Dilin, CatalystUI uyumlu uygulamaların inşa edilebileceği uygun bir temel sağladığı anlamına gelir.

Bir dilin bu gereksinimleri başka bir dille aynı şekilde karşılaması gerekmez. Farklı diller farklı söz dizimleri, tip sistemleri, standart kütüphaneler, derleyiciler, runtime'lar ve tasarım desenleri kullanır. CatalystUI Verification, gerekli kavramlar açık, güvenilir ve tutarlı biçimde ifade edilebildiği sürece bu farklılıklara izin verir.

## “Within Spec” Ne Anlama Gelir

Bir programlama dili **within spec** kabul edildiğinde, CatalystUI Ekibi'nin dili manuel olarak incelediği ve geçerli spesifikasyonlarda açıklanan gerekli davranışın o dil içinde ifade edilebileceği sonucuna varmayı makul bulduğu anlamına gelir.

Bu, tek ve katı bir uygulama deseni gerektirmez. Bir dil, bir gereksinimi yerleşik ilkel türler, standart kütüphane özellikleri, derleyici davranışı, runtime davranışı, belgelenmiş garantiler veya o dile uygun başka bir kararlı mekanizma aracılığıyla karşılayabilir.

Doğrulama, dilin spesifikasyon metniyle tamamen aynı adları, yapıları, söz dizimini veya iç tasarımı kullanıp kullanmadığıyla değil, spesifikasyonun anlamını temsil etme ve koruma konusundaki pratik yeteneğiyle ilgilenir.

## Bu Doğrulama Neden Var

CatalystUI; açıklık, tutarlılık ve insanların bilgisayarlarla nasıl etkileşime geçtiğinin doğru temsili etrafında tasarlanmıştır. Programlama dilleri önemlidir çünkü geliştiricilerin gerçekçi olarak neyi ifade edebileceğini, bu sistemlerin ne kadar güvenli modellenebileceğini ve daha yüksek düzey uygulamaların ne kadar açık biçimde inşa edilebileceğini belirler.

Bir dil gerekli temel kavramları kararlı biçimde sağlayamazsa, daha yüksek düzey CatalystUI uygulamalarına güvenmek zorlaşır. Geliştiriciler, en baştan güvenilir olması gereken fikirleri ifade etmek için belirsiz soyutlamalara, öngörülemez davranışlara, kırılgan bağımlılıklara veya gereksiz yeniden yazımlara itilebilir.

Programming Language Verification, hangi dillerin CatalystUI çalışmaları için yeterince güçlü bir temel sağladığını belirlemek için vardır. Geliştiricilere, dil tasarımcılarına ve kuruluşlara bir dilin CatalystUI uyumlu sistemler oluşturmak için uygun olup olmadığı konusunda daha açık bir anlayış sağlar.

## How a Language Becomes Verified

To become **CatalystUI Verified for Programming Languages**, a language must be reviewed against the specifications listed in this section.

The general process is:

1. The applicable CatalystUI specifications are identified.
2. The language is reviewed against each required specification.
3. The CatalystUI Team determines whether the language satisfies the intent and requirements of the specifications.
4. If the language is found to be within spec, it may be granted CatalystUI Verification.
5. Once verified, the language may be listed on the [Verified Languages](/verified/) page.

The review may consider official language documentation, standard library behavior, compiler behavior, runtime behavior, implementation examples, test cases, and other evidence needed to determine whether the language meets the requirements.

Compiler and runtime behavior may be considered during review when that behavior is part of how the language is commonly and officially used. However, verifying a programming language does not automatically verify every compiler, runtime, package, framework, library, application, or tool in that language’s ecosystem.

## Applicable Specifications

The specifications listed in this section define the requirements used for Programming Language Verification.

For programming languages, the active foundation is currently centered on the following specification categories:

* **FDEFSPEC**, which defines foundational data representations.
* **FRELSPEC**, which defines foundational relations between data representations.

Together, these specifications establish the minimum foundation required for a programming language to represent CatalystUI-compatible systems.

Additional specifications may be introduced later for more specialized verification categories. Those specifications may define higher-level implementation, platform, accessibility, internationalization, framework, service, or runtime requirements. However, those later specifications build on the foundation rather than replacing it.

A programming language becomes verified by satisfying the required specifications for this category. It is not expected to satisfy unrelated implementation-specific requirements unless those requirements are added to Programming Language Verification.

## Doğrulama Kapsamı

CatalystUI Verification for Programming Languages applies to the programming language as reviewed.

A verified language provides a suitable foundation for CatalystUI-compatible development. It does not guarantee that every project written in that language follows CatalystUI correctly, nor does it automatically verify the surrounding ecosystem.

Separate tools, libraries, frameworks, runtimes, applications, services, or implementations may require their own review depending on the verification category being requested.

Programming Language Verification should therefore be understood as a foundation check. It confirms that the language can represent the required concepts. It does not confirm that every use of the language applies those concepts correctly.

## Verification Validity

CatalystUI Verification applies only to the reviewed state of a programming language at the time verification is issued.

Programming languages are treated as a special case because many languages preserve compatibility across multiple versions. A language may retain its verification across later versions so long as it preserves backward compatibility with the features, primitives, representations, and behavior the original review depended on.

New language features alone do not invalidate verification. A future version may require a new review only if it removes, breaks, or substantially changes the verified foundation.

In other words, extending a language is usually fine. Breaking the verified base may require review.

## Doğrulanmış Diller

Known verified programming languages are listed separately on the [Verified Languages](/verified/) page.
