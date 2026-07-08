<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza-człowieka. -->
<!-- Usuń te wiersze w pull requeście po zweryfikowaniu tłumaczenia. -->

# Szczegóły weryfikacji

## C

### Omówienie

![Verified Indicator](https://www.catalystui.org/images/verification/verified-logo-generic.png)


Język programowania C został zweryfikowany względem specyfikacji FDEFSPEC (Rev. 1) i FRELSPEC (Rev. 1) według stanu na 7 lipca 2026 r.

#### Oświadczenie w dobrej wierze

W dobrej wierze uważamy, że język programowania C może rozsądnie reprezentować pojęcia i postanowienia zdefiniowane w poniższych specyfikacjach oraz że może być używany do implementowania systemów zgodnych z tymi specyfikacjami.

#### Oświadczenie z przeglądu

C zapewnia silną niskopoziomową obsługę podstawowej reprezentacji danych, dostępu do pamięci, plików, strumieni, procedur, funkcji, struktur i bezpośredniej implementacji zorientowanej systemowo.

Chociaż C nie zapewnia natywnie kilku obiektowych konstrukcji kompozytowych, ograniczenia te są odizolowane do konkretnych postanowień kompozytowych FRELSPEC i zostały udokumentowane poniżej. Te niepowodzenia nie uniemożliwiają uznania C za ogólnie zgodny ze specyfikacją, ale należy je rozumieć przy używaniu C do implementacji zgodnych z CatalystUI.

#### Założenia przeglądu

Ten przegląd zakłada współczesną obsługę standardowego C tam, gdzie odnotowano funkcje zależne od wersji. Obsługa liczb całkowitych o dokładnej szerokości zakłada, że implementacja udostępnia odpowiednie typy z `<stdint.h>`.

Ten przegląd traktuje C jako niskopoziomowy język reprezentacji. Kodowania dokładne co do bajtu mogą być reprezentowane bezpośrednio przez tablice bajtów, tabele wyszukiwania i jawną logikę parsowania, gdy nie udostępniono nazwanego standardowego kodeka.

### Ostrzeżenia

* Typy całkowite o dokładnej szerokości zależą od obsługi implementacji.
* CP1252 może być reprezentowane bajt po bajcie, ale nie udostępniono nazwanego standardowego kodeka.
* Serializacja UTF-16LE wymaga jawnej obsługi kolejności bajtów.
* Standardowe wątki mogą być pominięte przez niektóre implementacje C.
* Wzorce obiektowe można emulować ręcznie, ale nie są natywnymi konstrukcjami języka.

### Niepowodzenia

* C nie zapewnia natywnych elementów metod.
* C nie zapewnia natywnych właściwości.
* C nie zapewnia natywnych klas.
* C nie zapewnia natywnych interfejsów.

### Weryfikacja FDEFSPEC

#### Typy liczbowe

| Postanowienie | Zweryfikowano | Uwagi                                       |
| --------- | -------- | ------------------------------------------- |
| Bit       | ⚠️       | Użyj pól bitowych lub masek.                    |
| Nibble    | ⚠️       | Użyj pól bitowych lub masek.                    |
| Byte      | ✅        | Obsługiwane przez `unsigned char`.          |
| Short     | ✅        | Obsługiwane przez `int16_t` i `uint16_t`. |
| Int       | ✅        | Obsługiwane przez `int32_t` i `uint32_t`. |
| Long      | ✅        | Obsługiwane przez `int64_t` i `uint64_t`. |
| Float     | ✅        | Obsługiwane przez `float`.                  |
| Double    | ✅        | Obsługiwane przez `double`.                 |
| Boolean   | ✅        | Obsługiwane przez `bool`; C99+.             |

#### Kodowanie tekstu

| Postanowienie | Zweryfikowano | Uwagi                                   |
| --------- | -------- | --------------------------------------- |
| Kodpoint | ✅        | Obsługiwane przez `char32_t`; C11+.     |
| ASCII     | ✅        | Możliwe do reprezentacji jako wartości bajtowe.           |
| CP1252    | ⚠️        | Wymaga jawnego mapowania bajtów.         |
| UTF-8     | ✅        | Obsługiwane przez literały UTF-8; C11+. |
| UTF-16LE  | ⚠️        | Wymaga obsługi kolejności bajtów.           |

#### Status operacji

| Postanowienie | Zweryfikowano | Uwagi                           |
| --------- | -------- | ------------------------------- |
| Status    | ✅        | Może być reprezentowane przez enum.  |
| Context   | ✅        | Może być reprezentowane przez wartość.  |
| Operation | ✅        | Może być reprezentowane przez wartość.  |
| Szczegół    | ✅        | Może być reprezentowane przez wartość.  |
| Result    | ✅        | Może być reprezentowane przez strukturę. |

### Weryfikacja FRELSPEC

#### Kolekcje

| Postanowienie | Zweryfikowano | Uwagi                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Can be represented by structs. |
| Map       | ✅        | Can be represented by structs. |
| Array     | ✅        | Tablice natywne są obsługiwane.   |
| File      | ✅        | Obsługiwane przez API plików.   |
| Stream    | ✅        | Obsługiwane przez API strumieni. |

#### Pamięć

| Postanowienie | Zweryfikowano | Uwagi                      |
| --------- | -------- | -------------------------- |
| Address   | ✅        | Adresy są obsługiwane.   |
| Pointer   | ✅        | Wskaźniki są obsługiwane.    |
| Variable  | ✅        | Zmienne są obsługiwane.   |
| Constant  | ✅        | Obsługiwane przez `const`. |

#### Operacje

| Postanowienie   | Zweryfikowano | Uwagi                                   |
| ----------- | -------- | --------------------------------------- |
| Instruction | ✅        | Represented through machine operations. |
| Procedure   | ✅        | Obsługiwane przez funkcje `void`.     |
| Function    | ✅        | Obsługiwane przez funkcje zwracające wartość.  |

#### Wątki

| Postanowienie  | Zweryfikowano | Uwagi                                  |
| ---------- | -------- | -------------------------------------- |
| Process    | ✅        | Supported through hosted environments. |
| Thread     | ⚠️        | Obsługiwane przez `<threads.h>`; C11+. |
| Dispatcher | ✅        | Może być reprezentowane bezpośrednio.           |

#### Kompozyty

| Postanowienie | Zweryfikowano | Uwagi                                    |
| --------- | -------- | ---------------------------------------- |
| Member    | ✅        | Elementy struktur są obsługiwane.            |
| Object    | ✅        | Struktury mogą tworzyć adresowalne kompozyty. |
| Field     | ✅        | Pola struktur są obsługiwane.             |
| Method    | ❌        | Brak natywnych elementów metod.                |
| Property  | ❌        | Brak jawnej mapy accessorów Get/Set.        |
| Structure | ✅        | Struktury są obsługiwane natywnie.       |
| Class     | ❌        | Brak natywnej konstrukcji klasy.               |
| Interface | ❌        | Brak natywnej konstrukcji interfejsu.           |
