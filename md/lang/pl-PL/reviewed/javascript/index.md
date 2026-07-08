<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza-człowieka. -->
<!-- Usuń te wiersze w pull requeście po zweryfikowaniu tłumaczenia. -->

# Szczegóły przeglądu

## JavaScript

### Omówienie

Język programowania JavaScript został sprawdzony względem specyfikacji FDEFSPEC (Rev. 1) i FRELSPEC (Rev. 1) według stanu na 7 lipca 2026 r.

#### Oświadczenie z przeglądu

While JavaScript can represent some required concepts through objects, functions, arrays, and built-in language behavior, these mechanisms are not sufficient to satisfy the applicable CatalystUI specifications at the language level.

This review evaluates JavaScript itself, not the surrounding JavaScript ecosystem. Browser APIs, Node.js APIs, Deno APIs, Bun APIs, Web APIs, TypeScript, WebAssembly, external libraries, and custom validation are not treated as language-level support.

Because JavaScript lacks many required fixed-width scalar numeric types, does not provide required text encodings as language features, and does not define several required system, memory, threading, and composite constructs, we do not believe JavaScript provides a stable enough foundation for CatalystUI-compliant implementation without significant additional infrastructure.

W rezultacie JavaScript nie otrzymał statusu CatalystUI Zweryfikowano dla języków programowania.

#### Założenia przeglądu

This review applies a strict language-level standard. If a provision is not explicitly supported by JavaScript itself, it is marked as not verified.

Host-provided APIs, implementation-specific behavior, external libraries, transpilers, type systems, and custom runtime validation are excluded from verification.

### Ostrzeżenia

* JavaScript can represent many numeric values through `Number`, but `Number` is a 64-bit floating point numeric type.
* JavaScript provides `BigInt`, but `BigInt` is arbitrary-width.
* Typed arrays provide binary storage views, not scalar language types.
* JavaScript strings use UTF-16 code units, not explicit text encoding values.
* `const` protects bindings, not object values.

### Niepowodzenia

* JavaScript nie zapewnia większości wymaganych skalarnych typów liczbowych o stałej szerokości.
* JavaScript does not provide a dedicated scalar 32-bit floating point type.
* JavaScript does not provide ASCII, CP1252, UTF-8, or UTF-16LE as language-level text encodings.
* JavaScript does not provide language-level file or stream constructs.
* JavaScript does not provide language-level address or pointer constructs.
* JavaScript does not provide language-level process, thread, or dispatcher constructs.
* JavaScript properties do not provide an explicit keyed member backed by a required Get/Set accessor map.
* JavaScript nie zapewnia struktur ani interfejsów.

### Weryfikacja FDEFSPEC

#### Typy liczbowe

| Postanowienie | Zweryfikowano | Uwagi                          |
| --------- | -------- | ------------------------------ |
| Bit       | ❌        | Brak 1-bitowego typu liczbowego.         |
| Nibble    | ❌        | Brak 4-bitowego typu liczbowego.         |
| Byte      | ❌        | Brak skalarnego 8-bitowego typu całkowitego.  |
| Short     | ❌        | Brak skalarnego 16-bitowego typu całkowitego. |
| Int       | ❌        | Brak skalarnego 32-bitowego typu całkowitego. |
| Long      | ❌        | Brak skalarnego 64-bitowego typu całkowitego. |
| Float     | ❌        | Brak skalarnego 32-bitowego typu zmiennoprzecinkowego.   |
| Double    | ✅        | Obsługiwane przez `Number`.    |
| Boolean   | ✅        | Obsługiwane przez `boolean`.   |

#### Kodowanie tekstu

| Postanowienie | Zweryfikowano | Uwagi                        |
| --------- | -------- | ---------------------------- |
| Kodpoint | ❌        | Brak dedykowanego typu punktu kodowego. |
| ASCII     | ❌        | Nie na poziomie języka.          |
| CP1252    | ❌        | Nie na poziomie języka.          |
| UTF-8     | ❌        | Nie na poziomie języka.          |
| UTF-16LE  | ❌        | Nie na poziomie języka.          |

#### Status operacji

| Postanowienie | Zweryfikowano | Uwagi                           |
| --------- | -------- | ------------------------------- |
| Status    | ⚠️       | Możliwe do reprezentacji, ale nie do wymuszenia. |
| Context   | ⚠️       | Możliwe do reprezentacji, ale nie do wymuszenia. |
| Operation | ⚠️       | Możliwe do reprezentacji, ale nie do wymuszenia. |
| Szczegół    | ⚠️       | Możliwe do reprezentacji, ale nie do wymuszenia. |
| Result    | ⚠️       | Wymaga walidacji w czasie wykonywania.    |

### Weryfikacja FRELSPEC

#### Kolekcje

| Postanowienie | Zweryfikowano | Uwagi                    |
| --------- | -------- | ------------------------ |
| Set       | ✅        | Obsługiwane przez `Set`. |
| Map       | ✅        | Obsługiwane przez `Map`. |
| Array     | ✅        | Tablice są obsługiwane.    |
| File      | ❌        | Nie na poziomie języka.      |
| Stream    | ❌        | Nie na poziomie języka.      |

#### Pamięć

| Postanowienie | Zweryfikowano | Uwagi                           |
| --------- | -------- | ------------------------------- |
| Address   | ❌        | Brak obsługi adresów.             |
| Pointer   | ❌        | Brak obsługi wskaźników.             |
| Variable  | ✅        | Zmienne są obsługiwane.        |
| Constant  | ⚠️       | `const` protects bindings only. |

#### Operacje

| Postanowienie   | Zweryfikowano | Uwagi                            |
| ----------- | -------- | -------------------------------- |
| Instruction | ❌        | Brak zdefiniowanego typu instrukcji.     |
| Procedure   | ❌        | Funkcje zawsze zwracają wartość. |
| Function    | ✅        | Funkcje są obsługiwane.         |

#### Wątki

| Postanowienie  | Zweryfikowano | Uwagi                       |
| ---------- | -------- | --------------------------- |
| Process    | ❌        | Nie na poziomie języka.         |
| Thread     | ⚠️        | Reprezentowane przez agenty. |
| Dispatcher | ❌        | Wymaga planowania przez hosta.   |


#### Kompozyty

| Postanowienie | Zweryfikowano | Uwagi                                 |
| --------- | -------- | ------------------------------------- |
| Member    | ✅        | Elementy obiektów są obsługiwane.         |
| Object    | ✅        | Obiekty są obsługiwane.                |
| Field     | ✅        | Właściwości danych mogą reprezentować pola. |
| Method    | ✅        | Metody są obsługiwane.                |
| Property  | ❌        | Brak jawnej mapy accessorów.             |
| Structure | ❌        | Brak obsługi struktur.                 |
| Class     | ✅        | Składnia klas jest obsługiwana.            |
| Interface | ❌        | Brak obsługi interfejsów.                 |
