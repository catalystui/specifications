<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza-człowieka. -->
<!-- Usuń te wiersze w pull requeście po zweryfikowaniu tłumaczenia. -->

# Szczegóły przeglądu

## Python

### Omówienie

Język programowania Python został sprawdzony względem specyfikacji FDEFSPEC (Rev. 1) i FRELSPEC (Rev. 1) według stanu na 7 lipca 2026 r.

#### Oświadczenie z przeglądu

Chociaż Python może reprezentować wiele wymaganych pojęć przez typy wbudowane, obiekty, funkcje, klasy, moduły biblioteki standardowej i niestandardową walidację, mechanizmy te nie wystarczają do spełnienia odpowiednich specyfikacji CatalystUI na poziomie języka.

Python zapewnia silną obsługę kodowania tekstu, plików, strumieni, obiektów, funkcji, klas, właściwości, procesów, wątków i wykonywania dispatchowanego przez swoje zachowanie wbudowane oraz bibliotekę standardową. Jednak Python nie zapewnia wymaganych skalarnych typów liczbowych o stałej szerokości, nie definiuje prawdziwych stałych i w kilku konstrukcjach polega na dynamicznym zachowaniu środowiska uruchomieniowego, podczas gdy inne zweryfikowane języki mogą wyrazić je bardziej bezpośrednio.

Z tego powodu nie uważamy, aby Python zapewniał wystarczająco stabilny fundament dla implementacji zgodnej z CatalystUI bez znaczącej dodatkowej infrastruktury.

W rezultacie Python nie otrzymał statusu CatalystUI Zweryfikowano dla języków programowania.

#### Założenia przeglądu

Ten przegląd ocenia samego Pythona oraz dołączoną do niego bibliotekę standardową.

Pakiety zewnętrzne, rozszerzenia zależne od implementacji, opcjonalne moduły natywne, zewnętrzne narzędzia sprawdzania typów, transpilery oraz niestandardowe frameworki runtime nie są traktowane jako obsługa na poziomie języka.

### Ostrzeżenia

* Python zapewnia liczby całkowite o nieograniczonej precyzji, a nie prymitywy całkowite o stałej szerokości.
* Pythonowy `float` zwykle ma podwójną precyzję, ale nie stanowi odrębnej rodziny o stałej szerokości.
* Niektóre niskopoziomowe zachowania pamięci mogą wymagać `ctypes` lub zachowania zależnego od implementacji.
* Podpowiedzi typów w Pythonie nie są wymuszane w czasie wykonywania.
* Python obsługuje właściwości, ale zachowanie settera może zostać pominięte.
* Python może modelować kilka struktur przez funkcje biblioteki standardowej, ale nie jako natywny typ struktury.

### Niepowodzenia

* Python nie zapewnia większości wymaganych skalarnych typów liczbowych o stałej szerokości.
* Python nie zapewnia dedykowanego skalarnego 32-bitowego typu zmiennoprzecinkowego.
* Python nie zapewnia prawdziwych stałych na poziomie języka.
* Python nie definiuje procedur oddzielnie od funkcji.
* Python nie zapewnia natywnej obsługi wskaźników.
* Python nie zapewnia natywnej obsługi interfejsów.

### Weryfikacja FDEFSPEC

#### Typy liczbowe

| Postanowienie | Zweryfikowano | Uwagi                                |
| --------- | -------- | ------------------------------------ |
| Bit       | ❌        | Brak 1-bitowego typu liczbowego.               |
| Nibble    | ❌        | Brak 4-bitowego typu liczbowego.               |
| Byte      | ❌        | Brak skalarnego 8-bitowego typu całkowitego.        |
| Short     | ❌        | Brak skalarnego 16-bitowego typu całkowitego.       |
| Int       | ❌        | Brak skalarnego 32-bitowego typu całkowitego.       |
| Long      | ❌        | Brak skalarnego 64-bitowego typu całkowitego.       |
| Float     | ❌        | Brak skalarnego 32-bitowego typu zmiennoprzecinkowego.         |
| Double    | ⚠️       | `float` is usually double precision. |
| Boolean   | ✅        | Obsługiwane przez `bool`.            |

#### Kodowanie tekstu

| Postanowienie | Zweryfikowano | Uwagi                            |
| --------- | -------- | -------------------------------- |
| Kodpoint | ✅        | Ciągi znaków używają punktów kodowych Unicode. |
| ASCII     | ✅        | Obsługiwany kodek.                 |
| CP1252    | ✅        | Obsługiwany kodek.                 |
| UTF-8     | ✅        | Obsługiwany kodek.                 |
| UTF-16LE  | ✅        | Obsługiwany kodek.                 |

#### Status operacji

| Postanowienie | Zweryfikowano | Uwagi                       |
| --------- | -------- | --------------------------- |
| Status    | ⚠️       | Wymaga niestandardowej walidacji. |
| Context   | ⚠️       | Wymaga niestandardowej walidacji. |
| Operation | ⚠️       | Wymaga niestandardowej walidacji. |
| Szczegół    | ⚠️       | Wymaga niestandardowej walidacji. |
| Result    | ⚠️       | Wymaga niestandardowej walidacji. |

### Weryfikacja FRELSPEC

#### Kolekcje

| Postanowienie | Zweryfikowano | Uwagi                          |
| --------- | -------- | ------------------------------ |
| Set       | ✅        | Supported through `set`.       |
| Map       | ✅        | Obsługiwane przez `dict`.      |
| Array     | ✅        | Obsługiwane przez sekwencje.   |
| File      | ✅        | Obsługiwane przez API plików.   |
| Stream    | ✅        | Obsługiwane przez API strumieni. |

#### Pamięć

| Postanowienie | Zweryfikowano | Uwagi                        |
| --------- | -------- | ---------------------------- |
| Address   | ⚠️       | Tylko tożsamość obiektu.        |
| Pointer   | ❌        | Brak natywnej obsługi wskaźników.   |
| Variable  | ✅        | Wiązania nazw są obsługiwane. |
| Constant  | ❌        | Brak prawdziwych stałych.           |

#### Operacje

| Postanowienie   | Zweryfikowano | Uwagi                             |
| ----------- | -------- | --------------------------------- |
| Instruction | ⚠️       | Bytecode jest na poziomie implementacji. |
| Procedure   | ❌        | Funkcje zwracają `None`.          |
| Function    | ✅        | Funkcje są obsługiwane.          |

#### Wątki

| Postanowienie  | Zweryfikowano | Uwagi                            |
| ---------- | -------- | -------------------------------- |
| Process    | ✅        | Obsługiwane przez API procesów.  |
| Thread     | ✅        | Obsługiwane przez `threading`.   |
| Dispatcher | ✅        | Obsługiwane przez API wykonawców. |

#### Kompozyty

| Postanowienie | Zweryfikowano | Uwagi                            |
| --------- | -------- | -------------------------------- |
| Member    | ✅        | Elementy obiektów są obsługiwane.    |
| Object    | ✅        | Obiekty są obsługiwane.           |
| Field     | ✅        | Atrybuty mogą reprezentować pola. |
| Method    | ✅        | Metody są obsługiwane.           |
| Property  | ⚠️       | Obsługa getterów/setterów istnieje.    |
| Structure | ⚠️       | Tylko modele biblioteki standardowej.    |
| Class     | ✅        | Klasy są obsługiwane.           |
| Interface | ❌        | Brak natywnej obsługi interfejsów.     |
