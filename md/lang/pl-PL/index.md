<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza-człowieka. -->
<!-- Usuń te wiersze w pull requeście po zweryfikowaniu tłumaczenia. -->

![CatalystUI Verified for Programming Languages](/images/verification/verified-logo-languages.png)

# CatalystUI Verified dla języków programowania

Witamy w dokumentacji weryfikacji CatalystUI dla języków programowania.

**CatalystUI Verified dla języków programowania** oznacza, że język programowania został sprawdzony przez zespół CatalystUI i uznany za taki, który zapewnia podstawowe reprezentacje danych oraz struktury relacyjne wymagane do wyrażania systemów zgodnych z CatalystUI.

Ta weryfikacja nie jest ogólnym rankingiem języków programowania. Nie rozstrzyga, czy jeden język jest lepszy, szybszy, łatwiejszy, nowszy, popularniejszy albo przyjemniejszy od innego. Zamiast tego wskazuje, czy język zapewnia stabilny i praktyczny fundament dla specyfikacji wymaganych przez CatalystUI Verification.

Mówiąc prościej, ta weryfikacja pyta, czy język programowania potrafi wiernie reprezentować podstawowe dane i relacje, od których zależy CatalystUI.

## Cel

Języki programowania tworzą fundament reprezentacyjny pod każdą implementacją CatalystUI. Zanim framework, biblioteka, runtime, aplikacja lub usługa może podążać za Stosem CatalystUI, język użyty do jej zbudowania musi być zdolny do wyrażenia podstawowych pojęć, od których zależy model.

W przypadku języków programowania oznacza to przede wszystkim dwie rzeczy:

1. Język musi być zdolny do reprezentowania danych podstawowych.
2. Język musi być zdolny do reprezentowania podstawowych relacji między danymi.

Te kwestie są zdefiniowane przez podstawowe specyfikacje CatalystUI. FDEFSPEC definiuje oczekiwane reprezentacje danych podstawowych. FRELSPEC definiuje oczekiwane relacje podstawowe między tymi reprezentacjami, w tym kolekcje, relacje pamięci, operacje, relacje wątkowania i kompozyty.

Zweryfikowany język programowania daje deweloperom wystarczającą jasność i kontrolę, aby budować systemy zgodne z CatalystUI bez polegania na kruchych, niejasnych lub niestabilnych obejściach dla podstawowych pojęć wymaganych przez CatalystUI.

## Co oznacza weryfikacja

Język programowania staje się **CatalystUI Verified**, gdy zostanie sprawdzony względem specyfikacji wymienionych w tej sekcji i uznany za zgodny ze specyfikacją.

W przypadku weryfikacji języka programowania przegląd skupia się na tym, czy język może wyrazić podstawowe wymagania zdefiniowane przez odpowiednie specyfikacje. Nie oznacza to, że sam język jest implementacją CatalystUI. Oznacza to, że język zapewnia odpowiedni fundament, na którym można budować implementacje zgodne z CatalystUI.

Język nie musi spełniać tych wymagań w taki sam sposób jak inny język. Różne języki używają różnych składni, systemów typów, bibliotek standardowych, kompilatorów, runtime’ów i wzorców projektowych. CatalystUI Verification dopuszcza te różnice, o ile wymagane pojęcia mogą być wyrażone jasno, niezawodnie i spójnie.

## Co oznacza „zgodny ze specyfikacją”

Gdy język programowania jest uznany za **zgodny ze specyfikacją**, oznacza to, że zespół CatalystUI ręcznie sprawdził język i uznał za rozsądne stwierdzenie, że wymagane zachowanie opisane przez odpowiednie specyfikacje może zostać wyrażone w tym języku.

Nie wymaga to jednego sztywnego wzorca implementacji. Język może spełniać wymaganie przez prymitywy wbudowane, funkcje biblioteki standardowej, zachowanie kompilatora, zachowanie runtime’u, udokumentowane gwarancje albo inny stabilny mechanizm właściwy dla danego języka.

Weryfikacja dotyczy praktycznej zdolności do reprezentowania i zachowywania znaczenia specyfikacji, a nie tego, czy język używa dokładnie tych samych nazw, struktur, składni albo projektu wewnętrznego co tekst specyfikacji.

## Dlaczego ta weryfikacja istnieje

CatalystUI jest projektowany wokół jasności, spójności i wiernej reprezentacji tego, jak ludzie i komputery wchodzą ze sobą w interakcję. Języki programowania mają znaczenie, ponieważ określają, co deweloperzy mogą realistycznie wyrazić, jak bezpiecznie można modelować te systemy oraz jak jasno można budować implementacje wyższego poziomu.

Jeśli język nie może zapewnić wymaganych pojęć podstawowych w stabilny sposób, implementacjom CatalystUI wyższego poziomu trudniej zaufać. Deweloperzy mogą zostać popchnięci w stronę niejasnych abstrakcji, nieprzewidywalnego zachowania, kruchych zależności albo niepotrzebnych przepisań tylko po to, aby wyrazić idee, które powinny być niezawodne od samego początku.

Weryfikacja języków programowania istnieje po to, aby wskazać, które języki zapewniają wystarczająco mocny fundament dla pracy z CatalystUI. Daje deweloperom, projektantom języków i organizacjom jaśniejsze zrozumienie tego, czy język nadaje się do budowania systemów zgodnych z CatalystUI.

## Jak język zostaje zweryfikowany

Aby zostać **CatalystUI Verified dla języków programowania**, język musi zostać sprawdzony względem specyfikacji wymienionych w tej sekcji.

Ogólny proces wygląda następująco:

1. Identyfikowane są odpowiednie specyfikacje CatalystUI.
2. Język jest sprawdzany względem każdej wymaganej specyfikacji.
3. Zespół CatalystUI ustala, czy język spełnia intencję i wymagania specyfikacji.
4. Jeśli język zostanie uznany za zgodny ze specyfikacją, może otrzymać weryfikację CatalystUI.
5. Po weryfikacji język może zostać wymieniony na stronie [Zweryfikowane języki](/verified/).

Przegląd może uwzględniać oficjalną dokumentację języka, zachowanie biblioteki standardowej, zachowanie kompilatora, zachowanie runtime’u, przykłady implementacji, przypadki testowe oraz inne dowody potrzebne do ustalenia, czy język spełnia wymagania.

Zachowanie kompilatora i runtime’u może być brane pod uwagę podczas przeglądu, gdy to zachowanie jest częścią tego, jak język jest powszechnie i oficjalnie używany. Weryfikacja języka programowania nie weryfikuje jednak automatycznie każdego kompilatora, runtime’u, pakietu, frameworka, biblioteki, aplikacji ani narzędzia w ekosystemie tego języka.

## Odpowiednie specyfikacje

Specyfikacje wymienione w tej sekcji definiują wymagania używane przy weryfikacji języków programowania.

Dla języków programowania aktywny fundament jest obecnie skupiony na następujących kategoriach specyfikacji:

* **FDEFSPEC**, która definiuje podstawowe reprezentacje danych.
* **FRELSPEC**, która definiuje podstawowe relacje między reprezentacjami danych.

Razem te specyfikacje ustanawiają minimalny fundament wymagany, aby język programowania mógł reprezentować systemy zgodne z CatalystUI.

Dodatkowe specyfikacje mogą zostać wprowadzone później dla bardziej wyspecjalizowanych kategorii weryfikacji. Takie specyfikacje mogą definiować wymagania dotyczące implementacji wyższego poziomu, platform, dostępności, internacjonalizacji, frameworków, usług lub runtime’ów. Te późniejsze specyfikacje budują jednak na fundamencie, zamiast go zastępować.

Język programowania zostaje zweryfikowany przez spełnienie wymaganych specyfikacji dla tej kategorii. Nie oczekuje się, że spełni niepowiązane wymagania specyficzne dla implementacji, chyba że takie wymagania zostaną dodane do weryfikacji języków programowania.

## Zakres weryfikacji

CatalystUI Verification dla języków programowania dotyczy języka programowania w takim stanie, w jakim został sprawdzony.

Zweryfikowany język zapewnia odpowiedni fundament dla rozwoju zgodnego z CatalystUI. Nie gwarantuje, że każdy projekt napisany w tym języku poprawnie stosuje CatalystUI, ani nie weryfikuje automatycznie otaczającego ekosystemu.

Oddzielne narzędzia, biblioteki, frameworki, runtime’y, aplikacje, usługi lub implementacje mogą wymagać własnego przeglądu zależnie od żądanej kategorii weryfikacji.

Weryfikację języka programowania należy więc rozumieć jako sprawdzenie fundamentu. Potwierdza ona, że język może reprezentować wymagane pojęcia. Nie potwierdza, że każde użycie języka stosuje te pojęcia poprawnie.

## Ważność weryfikacji

CatalystUI Verification ma zastosowanie wyłącznie do sprawdzonego stanu języka programowania w chwili wydania weryfikacji.

Języki programowania są traktowane jako szczególny przypadek, ponieważ wiele języków zachowuje kompatybilność przez wiele wersji. Język może zachować swoją weryfikację w późniejszych wersjach, o ile zachowuje kompatybilność wsteczną z funkcjami, prymitywami, reprezentacjami i zachowaniem, od których zależał pierwotny przegląd.

Same nowe funkcje języka nie unieważniają weryfikacji. Przyszła wersja może wymagać nowego przeglądu tylko wtedy, gdy usuwa, łamie lub istotnie zmienia zweryfikowany fundament.

Innymi słowy, rozszerzanie języka jest zwykle w porządku. Naruszenie zweryfikowanej podstawy może wymagać przeglądu.

## Zweryfikowane języki

Znane zweryfikowane języki programowania są wymienione osobno na stronie [Zweryfikowane języki](/verified/).
