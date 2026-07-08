<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza-człowieka. -->
<!-- Usuń te wiersze w pull requeście po zweryfikowaniu tłumaczenia. -->

# Szczegóły weryfikacji

## Java

### Omówienie

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Język programowania Java został zweryfikowany względem specyfikacji FDEFSPEC (Rev. 1) i FRELSPEC (Rev. 1) według stanu na 7 lipca 2026 r.

#### Oświadczenie w dobrej wierze

W dobrej wierze uważamy, że język programowania Java może rozsądnie reprezentować dużą część pojęć i postanowień zdefiniowanych w poniższych specyfikacjach oraz że może być używany do implementowania systemów zgodnych z tymi specyfikacjami.

#### Założenia przeglądu

Ten przegląd zakłada współczesną obsługę języka Java tam, gdzie odnotowano funkcje zależne od wersji. Funkcje takie jak inferencja zmiennych lokalnych, rekordy i dostęp do pamięci zewnętrznej mogą wymagać nowszych wersji Javy.

### Ostrzeżenia

* Java nie ma natywnej obsługi typów liczbowych bez znaku, co może wymagać szerszej reprezentacji lub alternatywnych reprezentacji dla niektórych postanowień.
* Bezpośredni adres pamięci i zachowanie podobne do wskaźników mogą wymagać obsługi Java 22+ Foreign Function and Memory API.
* Java nie ma natywnej składni właściwości, więc wymaga metod getter i setter.

### Niepowodzenia

* Java nie zapewnia CP1252 jako gwarantowanego standardowego zestawu znaków, co dla pełnej zgodności wymaga obsługi zależnej od implementacji, dodatkowych bibliotek lub niestandardowej obsługi.
* Właściwości Javy nie zapewniają jawnego kluczowanego elementu członkowskiego opartego na wymaganej mapie accessorów Get/Set.

### Weryfikacja FDEFSPEC

#### Typy liczbowe

| Postanowienie | Zweryfikowano | Uwagi                                            |
| --------- | -------- | ------------------------------------------------ |
| Bit       | ⚠️       | Brak 1-bitowego typu liczbowego; użyj szerszej reprezentacji.                         |
| Nibble    | ⚠️       | Brak 4-bitowego typu liczbowego; użyj szerszej reprezentacji.                         |
| Byte      | ⚠️       | Tylko 8-bitowy typ ze znakiem; dla bez znaku użyj szerszej reprezentacji.           |
| Short     | ⚠️       | Tylko 16-bitowy typ ze znakiem; dla bez znaku użyj szerszej reprezentacji.          |
| Int       | ⚠️       | 32-bitowy typ ze znakiem; pomocnicze operacje bez znaku wymagają Java 8+. |
| Long      | ⚠️       | 64-bitowy typ ze znakiem; pomocnicze operacje bez znaku wymagają Java 8+. |
| Float     | ✅        | Obsługiwana jest 32-bitowa liczba zmiennoprzecinkowa.              |
| Double    | ✅        | Obsługiwana jest 64-bitowa liczba zmiennoprzecinkowa.              |
| Boolean   | ✅        | Typ logiczny jest obsługiwany.                       |

#### Kodowanie tekstu

| Postanowienie | Zweryfikowano | Uwagi                                    |
| --------- | -------- | ---------------------------------------- |
| Kodpoint | ✅        | Obsługiwane przez `int` i `Character`. |
| ASCII     | ✅        | Gwarantowany standardowy zestaw znaków.             |
| CP1252    | ❌        | Nie jest gwarantowane przez `StandardCharsets`.    |
| UTF-8     | ✅        | Gwarantowany standardowy zestaw znaków.             |
| UTF-16LE  | ✅        | Gwarantowany standardowy zestaw znaków.             |

#### Status operacji

| Postanowienie | Zweryfikowano | Uwagi                                       |
| --------- | -------- | ------------------------------------------- |
| Status    | ✅        | Może być reprezentowane przez typ niestandardowy.        |
| Context   | ✅        | Może być reprezentowane przez wartość niestandardową.       |
| Operation | ✅        | Może być reprezentowane przez wartość niestandardową.       |
| Szczegół    | ✅        | Może być reprezentowane przez wartość niestandardową.       |
| Result    | ✅        | Może być reprezentowane przez niestandardowy typ zwracany. |

### Weryfikacja FRELSPEC

#### Kolekcje

| Postanowienie | Zweryfikowano | Uwagi                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Obsługiwane przez `Set`.       |
| Map       | ✅        | Obsługiwane przez `Map`.       |
| Array     | ✅        | Tablice natywne są obsługiwane.   |
| File      | ✅        | Obsługiwane przez API plików.   |
| Stream    | ✅        | Obsługiwane przez API strumieni. |

#### Pamięć

| Postanowienie | Zweryfikowano | Uwagi                                                          |
| --------- | -------- | -------------------------------------------------------------- |
| Address   | ⚠️       | Bezpośrednie adresy wymagają Java 22+ FFM.                         |
| Pointer   | ⚠️       | Dostęp podobny do wskaźników wymaga Java 22+ FFM.                     |
| Variable  | ✅        | Declarations and `var` are supported; `var` requires Java 10+. |
| Constant  | ✅        | Obsługiwane przez `final`.                                     |

#### Operacje

| Postanowienie   | Zweryfikowano | Uwagi                                        |
| ----------- | -------- | -------------------------------------------- |
| Instruction | ✅        | Reprezentowane przez bytecode i operacje. |
| Procedure   | ✅        | Obsługiwane przez metody `void`.            |
| Function    | ✅        | Obsługiwane przez metody zwracające wartość.         |

#### Wątki

| Postanowienie  | Zweryfikowano | Uwagi                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Obsługiwane przez aplikację i API `Process`. |
| Thread     | ✅        | Obsługiwane przez `Thread`.                       |
| Dispatcher | ✅        | Obsługiwane przez API `Executor`.                |

#### Kompozyty

| Postanowienie | Zweryfikowano | Uwagi                                  |
| --------- | -------- | -------------------------------------- |
| Member    | ✅        | Elementy klas są obsługiwane.           |
| Object    | ✅        | Obiekty są obsługiwane.                 |
| Field     | ✅        | Pola są obsługiwane.                  |
| Method    | ✅        | Metody są obsługiwane.                 |
| Property  | ❌        | Brak jawnej mapy accessorów.              |
| Structure | ✅        | Supported through records; Java 16+.   |
| Class     | ✅        | Klasy są obsługiwane.                 |
| Interface | ✅        | Interfejsy są obsługiwane.              |
