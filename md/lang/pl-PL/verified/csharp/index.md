<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza-człowieka. -->
<!-- Usuń te wiersze w pull requeście po zweryfikowaniu tłumaczenia. -->

# Szczegóły weryfikacji

## C#

### Omówienie

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Język programowania C# został zweryfikowany względem specyfikacji FDEFSPEC (Rev. 1) i FRELSPEC (Rev. 1) według stanu na 7 lipca 2026 r.

#### Oświadczenie w dobrej wierze

W dobrej wierze uważamy, że język programowania C# może rozsądnie reprezentować pojęcia i postanowienia zdefiniowane w poniższych specyfikacjach oraz że może być używany do implementowania systemów zgodnych z tymi specyfikacjami.

#### Założenia przeglądu

Ten przegląd zakłada współczesną obsługę C# i .NET tam, gdzie odnotowano funkcje zależne od wersji.

### Ostrzeżenia

* Obsługa CP1252 jest dostępna przez oficjalnego dostawcę stron kodowych .NET, ale może wymagać rejestracji dostawcy lub dodatkowego pakietu zależnie od docelowego runtime.
* Niebezpieczne zachowanie wskaźników może wymagać jawnej autoryzacji unsafe.

### Niepowodzenia

* Podczas tej weryfikacji nie znaleziono znanych niepowodzeń FDEFSPEC ani FRELSPEC.

### Weryfikacja FDEFSPEC

#### Typy liczbowe

| Postanowienie | Zweryfikowano | Uwagi                                   |
| --------- | -------- | --------------------------------------- |
| Bit       | ⚠️       | Brak 1-bitowego typu liczbowego; użyj szerszej reprezentacji.                |
| Nibble    | ⚠️       | Brak 4-bitowego typu liczbowego; użyj szerszej reprezentacji.                |
| Byte      | ✅        | Obsługiwane przez `byte` i `sbyte`.   |
| Short     | ✅        | Obsługiwane przez `short` i `ushort`. |
| Int       | ✅        | Obsługiwane przez `int` i `uint`.     |
| Long      | ✅        | Obsługiwane przez `long` i `ulong`.   |
| Float     | ✅        | Obsługiwane przez `float`.              |
| Double    | ✅        | Obsługiwane przez `double`.             |
| Boolean   | ✅        | Obsługiwane przez `bool`.               |

#### Kodowanie tekstu

| Postanowienie | Zweryfikowano | Uwagi                                  |
| --------- | -------- | -------------------------------------- |
| Kodpoint | ✅        | Obsługiwane przez typy liczbowe i `Rune`. |
| ASCII     | ✅        | Obsługiwane przez `Encoding.ASCII`.    |
| CP1252    | ⚠️       | Wymaga dostawcy stron kodowych.          |
| UTF-8     | ✅        | Obsługiwane przez `Encoding.UTF8`.     |
| UTF-16LE  | ✅        | Obsługiwane przez `Encoding.Unicode`.  |

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

| Postanowienie | Zweryfikowano | Uwagi                                        |
| --------- | -------- | -------------------------------------------- |
| Set       | ✅        | Obsługiwane przez `HashSet<T>`.              |
| Map       | ✅        | Obsługiwane przez `Dictionary<TKey,TValue>`. |
| Array     | ✅        | Tablice natywne są obsługiwane.                 |
| File      | ✅        | Obsługiwane przez API plików.                 |
| Stream    | ✅        | Supported through `Stream`.                  |

#### Pamięć

| Postanowienie | Zweryfikowano | Uwagi                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Obsługiwane przez referencje i wskaźniki. |
| Pointer   | ✅        | Obsługiwane przez niebezpieczne wskaźniki.         |
| Variable  | ✅        | Zmienne są obsługiwane.                   |
| Constant  | ✅        | Obsługiwane przez `const` i `readonly`.  |

#### Operacje

| Postanowienie   | Zweryfikowano | Uwagi                                  |
| ----------- | -------- | -------------------------------------- |
| Instruction | ✅        | Reprezentowane przez IL i operacje. |
| Procedure   | ✅        | Obsługiwane przez metody `void`.      |
| Function    | ✅        | Obsługiwane przez metody zwracające wartość.   |

#### Wątki

| Postanowienie  | Zweryfikowano | Uwagi                                             |
| ---------- | -------- | ------------------------------------------------- |
| Process    | ✅        | Obsługiwane przez aplikację i API `Process`. |
| Thread     | ✅        | Obsługiwane przez `Thread`.                       |
| Dispatcher | ✅        | Obsługiwane przez zadania i schedulery.           |

#### Kompozyty

| Postanowienie | Zweryfikowano | Uwagi                              |
| --------- | -------- | ---------------------------------- |
| Member    | ✅        | Elementy typów są obsługiwane.        |
| Object    | ✅        | Obiekty są obsługiwane.             |
| Field     | ✅        | Pola są obsługiwane.              |
| Method    | ✅        | Metody są obsługiwane.             |
| Property  | ✅        | Właściwości są obsługiwane natywnie. |
| Structure | ✅        | Struktury są obsługiwane natywnie. |
| Class     | ✅        | Klasy są obsługiwane.             |
| Interface | ✅        | Interfejsy są obsługiwane.          |
