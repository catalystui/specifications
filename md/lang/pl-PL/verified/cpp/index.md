<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza-człowieka. -->
<!-- Usuń te wiersze w pull requeście po zweryfikowaniu tłumaczenia. -->

# Szczegóły weryfikacji

## C++

### Omówienie

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Język programowania C++ został zweryfikowany względem specyfikacji FDEFSPEC (Rev. 1) i FRELSPEC (Rev. 1) według stanu na 7 lipca 2026 r.

#### Oświadczenie w dobrej wierze

W dobrej wierze uważamy, że język programowania C++ może rozsądnie reprezentować pojęcia i postanowienia zdefiniowane w poniższych specyfikacjach oraz że może być używany do implementowania systemów zgodnych z tymi specyfikacjami.

#### Założenia przeglądu

Ten przegląd zakłada współczesną obsługę standardowego C++ tam, gdzie odnotowano funkcje zależne od wersji. Obsługa liczb całkowitych o dokładnej szerokości zakłada, że implementacja udostępnia odpowiednie typy z `<cstdint>`.

Ten przegląd traktuje C++ jako systemowy język programowania z bezpośrednią obsługą niskopoziomowej reprezentacji, modelowania obiektów, kontroli pamięci, programowania generycznego i wykonywania współbieżnego.

### Ostrzeżenia

* Typy całkowite o dokładnej szerokości zależą od obsługi implementacji.
* CP1252 może być reprezentowane bajt po bajcie, ale nie udostępniono nazwanego standardowego kodeka.
* Serializacja UTF-16LE wymaga jawnej obsługi kolejności bajtów.
* Niektóre funkcje współbieżności i znaków wymagają współczesnych rewizji C++.

### Niepowodzenia

* Podczas tej weryfikacji nie znaleziono znanych niepowodzeń FDEFSPEC ani FRELSPEC.

### Weryfikacja FDEFSPEC

#### Typy liczbowe

| Postanowienie | Zweryfikowano | Uwagi                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Użyj pól bitowych lub masek.                    |
| Nibble    | ⚠️       | Użyj pól bitowych lub masek.                    |
| Byte      | ✅        | Obsługiwane przez `std::byte`.              |
| Short     | ✅        | Obsługiwane przez `int16_t` i `uint16_t`. |
| Int       | ✅        | Obsługiwane przez `int32_t` i `uint32_t`. |
| Long      | ✅        | Obsługiwane przez `int64_t` i `uint64_t`. |
| Float     | ✅        | Obsługiwane przez `float`.                  |
| Double    | ✅        | Obsługiwane przez `double`.                 |
| Boolean   | ✅        | Obsługiwane przez `bool`.                   |

#### Kodowanie tekstu

| Postanowienie | Zweryfikowano | Uwagi                                |
| --------- | -------- | ------------------------------------ |
| Kodpoint | ✅        | Obsługiwane przez `char32_t`.        |
| ASCII     | ✅        | Możliwe do reprezentacji jako wartości bajtowe.        |
| CP1252    | ⚠️        | Wymaga jawnego mapowania bajtów.      |
| UTF-8     | ✅        | Obsługiwane przez `char8_t`; C++20+. |
| UTF-16LE  | ⚠️        | Wymaga obsługi kolejności bajtów.        |

#### Status operacji

| Postanowienie | Zweryfikowano | Uwagi                                    |
| --------- | -------- | ---------------------------------------- |
| Status    | ✅        | Może być reprezentowane przez enum.           |
| Context   | ✅        | Może być reprezentowane przez wartość.           |
| Operation | ✅        | Może być reprezentowane przez wartość.           |
| Szczegół    | ✅        | Może być reprezentowane przez wartość.           |
| Result    | ✅        | Może być reprezentowane przez strukturę lub klasę. |

### Weryfikacja FRELSPEC

#### Kolekcje

| Postanowienie | Zweryfikowano | Uwagi                                      |
| --------- | -------- | ------------------------------------------ |
| Set       | ✅        | Obsługiwane przez `std::set`.              |
| Map       | ✅        | Obsługiwane przez `std::map`.              |
| Array     | ✅        | Obsługiwane przez tablice i `std::array`. |
| File      | ✅        | Obsługiwane przez strumienie plików.            |
| Stream    | ✅        | Obsługiwane przez iostreams.               |

#### Pamięć

| Postanowienie | Zweryfikowano | Uwagi                                      |
| --------- | -------- | ------------------------------------------ |
| Address   | ✅        | Adresy są obsługiwane.                   |
| Pointer   | ✅        | Wskaźniki są obsługiwane.                    |
| Variable  | ✅        | Zmienne są obsługiwane.                   |
| Constant  | ✅        | Obsługiwane przez `const` i `constexpr`. |

#### Operacje

| Postanowienie   | Zweryfikowano | Uwagi                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | Obsługiwane przez funkcje `void`.     |
| Function    | ✅        | Obsługiwane przez funkcje zwracające wartość.  |

#### Wątki

| Postanowienie  | Zweryfikowano | Uwagi                                    |
| ---------- | -------- | ---------------------------------------- |
| Process    | ✅        | Obsługiwane przez wykonywanie w środowisku hosta.      |
| Thread     | ✅        | Obsługiwane przez `std::thread`; C++11+. |
| Dispatcher | ✅        | Obsługiwane przez async i schedulery.  |

#### Kompozyty

| Postanowienie | Zweryfikowano | Uwagi                                   |
| --------- | -------- | --------------------------------------- |
| Member    | ✅        | Elementy klas są obsługiwane.            |
| Object    | ✅        | Obiekty są obsługiwane.                  |
| Field     | ✅        | Pola są obsługiwane.                   |
| Method    | ✅        | Metody są obsługiwane.                  |
| Property  | ✅        | Mapy Get/Set mogą być reprezentowane.        |
| Structure | ✅        | Struktury są obsługiwane natywnie.      |
| Class     | ✅        | Klasy są obsługiwane natywnie.         |
| Interface | ✅        | Can be represented by abstract classes. |
