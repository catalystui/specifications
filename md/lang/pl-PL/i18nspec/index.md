<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza. -->

<!-- Usuń te wiersze w pull request po zweryfikowaniu tłumaczenia. -->

# I18NSPEC

<br/>

> **Specyfikacja internacjonalizacji**<br/>
> Rewizja 1<br/>
> 8 lipca 2026<br/> <br/>
> Copyright © 2026 CatalystUI LLC. <br/>
> All rights reserved.<br/> <br/>
> Definicje, wymagania i pojęcia przedstawione w tym dokumencie opisują praktyczne wsparcie internacjonalizacji i mogą być swobodnie wyrażane innymi słowami.

<a id="introduction"></a>
## Wprowadzenie

**Internationalization Specification (I18NSPEC)** ustanawia podstawowe pojęcia, terminologię i wymagania używane do oceny obsługi wielu języków w ekosystemie CatalystUI. Jej celem jest zapewnienie jasnego standardu pozwalającego określić, czy system, usługa, framework, aplikacja lub implementacja zapewnia wystarczającą obsługę językową, aby można było uznać ją za zgodną ze specyfikacją.

Internacjonalizacja ma znaczenie, ponieważ interfejs użytkownika nie może komunikować się jasno, jeżeli jego zasadnicze znaczenie jest dostępne tylko w jednym języku. System może działać technicznie, ale jeżeli użytkownicy nie rozumieją jego etykiet, instrukcji, kontrolek, ustawień, ostrzeżeń, błędów lub podstawowych przepływów pracy, system nie zapewnił tym użytkownikom znaczącego interfejsu.

Ta specyfikacja nie próbuje mierzyć doskonałej jakości tłumaczenia, stylu literackiego, adaptacji kulturowej, zgodności prawnej ani pełnej regionalnej lokalizacji. Zamiast tego definiuje minimalną wielojęzyczną podstawę wymaganą, aby użytkownicy mogli w znaczący sposób uzyskać dostęp do zasadniczych części systemu i obsługiwać je w wymaganym zestawie locale CatalystUI.

Mówiąc prościej, I18NSPEC zadaje trzy główne pytania:

1. Czy użytkownicy mogą uzyskać dostęp do zasadniczych części systemu w każdym wymaganym języku?
2. Czy użytkownicy mogą rozsądnie wybrać język, który rozumieją?
3. Czy system zachowuje wystarczająco dużo znaczenia między językami, aby pozostać użyteczny?

> [!IMPORTANT]
>
> I18NSPEC definiuje wymagania internacjonalizacji na potrzeby weryfikacji. Nie jest to osobna specyfikacja dla każdego języka. Każde wymagane locale jest sprawdzane względem tej samej specyfikacji.

<a id="table-of-contents"></a>
## Spis treści

* [I18NSPEC](#i18nspec)

  * [Wprowadzenie](#introduction)
  * [Spis treści](#table-of-contents)
  * [Zgodność](#conformance)
  * [Wymagany zestaw locale](#required-locale-set)
  * [Treść skierowana do użytkownika](#user-facing-content)

    * [Treść skierowana do użytkownika](#user-facing-content-1)
    * [Zasadnicza treść skierowana do użytkownika](#essential-user-facing-content)
    * [Krytyczna treść skierowana do użytkownika](#critical-user-facing-content)
    * [Treść niezasadnicza](#nonessential-content)
  * [Pokrycie tłumaczeniem](#translation-coverage)

    * [Zasadnicze pokrycie tłumaczeniem](#essential-translation-coverage)
    * [Wymóg pokrycia](#coverage-requirement)
    * [Wymóg dotyczący treści krytycznej](#critical-content-requirement)
  * [Wybór języka](#language-selection)

    * [Aktywne locale](#active-locale)
    * [Domyślne locale](#default-locale)
    * [Mechanizm wyboru języka](#language-selection-mechanism)
    * [Etykiety opcji językowych](#language-option-labels)
  * [Fallbacki i równoważność locale](#fallbacks-and-locale-equivalence)

    * [Fallback locale](#fallback-locale)
    * [Zachowanie fallback](#fallback-behavior)
    * [Równoważność locale](#locale-equivalence)
  * [Wymagania implementacyjne](#implementation-requirements)

    * [Stabilny mechanizm tłumaczenia](#stable-translation-mechanism)
    * [Zachowanie znaczenia](#preservation-of-meaning)
    * [Języki wrażliwe na kierunek tekstu](#direction-sensitive-languages)
    * [Wartości zależne od locale](#locale-sensitive-values)
  * [Weryfikacja](#verification)

    * [W zgodzie ze specyfikacją](#within-spec)
    * [Ostrzeżenia](#warnings)
    * [Niepowodzenia](#failures)
    * [Ważność weryfikacji](#verification-validity)

<a id="conformance"></a>
## Zgodność

System uznaje się za zgodny z I18NSPEC, gdy spełnia wymagania zdefiniowane w tym dokumencie dla każdego locale w wymaganym zestawie locale.

System zgodny musi:

1. Obsługiwać każde locale z wymaganego zestawu locale.
2. Zapewniać przetłumaczoną treść dla ponad 75% zasadniczej treści skierowanej do użytkownika w każdym wymaganym locale.
3. Zapewniać przetłumaczoną treść dla całej krytycznej treści skierowanej do użytkownika w każdym wymaganym locale.
4. Zapewniać rozsądny mechanizm dla użytkownika końcowego pozwalający wybrać aktywne locale.
5. Używać stabilnego mechanizmu tłumaczenia odpowiedniego dla systemu.
6. Zachowywać zasadnicze znaczenie przetłumaczonej treści skierowanej do użytkownika.
7. Unikać polegania na treści fallback w celu deklarowania pokrycia tłumaczeniem, z wyjątkiem sytuacji, w których równoważność locale zostanie zaakceptowana podczas przeglądu.

System nie musi używać jednego konkretnego wzorca implementacji, aby spełnić tę specyfikację. Może używać plików zasobów, tabel tłumaczeń, trasowania świadomego locale, skompilowanych zasobów językowych, statycznych stron lokalizowanych, pakietów językowych ładowanych w czasie działania, tłumaczeń opartych na bazie danych albo innego stabilnego mechanizmu odpowiedniego dla systemu.

Weryfikacja dotyczy praktycznego dostępu użytkownika i zasadniczego znaczenia, a nie jednej sztywnej architektury technicznej.

<a id="required-locale-set"></a>
## Wymagany zestaw locale

Wymagany zestaw locale definiuje języki i warianty regionalne, które muszą zostać sprawdzone w ramach CatalystUI Internationalization Verification.

Aktualny wymagany zestaw locale obejmuje następujące locale:

| Locale    | Język                    |
| --------- | ------------------------ |
| `ar-SA`   | arabski (Arabia Saudyjska) |
| `bn-BD`   | bengalski (Bangladesz)   |
| `de-DE`   | niemiecki (Niemcy)       |
| `en-GB`   | angielski (Wielka Brytania) |
| `en-IN`   | angielski (Indie)        |
| `en-US`   | angielski (Stany Zjednoczone) |
| `es-ES`   | hiszpański (Hiszpania)   |
| `es-MX`   | hiszpański (Meksyk)      |
| `fa-IR`   | perski (Iran)            |
| `fr-FR`   | francuski (Francja)      |
| `hi-IN`   | hindi (Indie)            |
| `id-ID`   | indonezyjski (Indonezja) |
| `it-IT`   | włoski (Włochy)          |
| `ja-JP`   | japoński (Japonia)       |
| `ko-KR`   | koreański (Korea Południowa) |
| `nl-NL`   | niderlandzki (Niderlandy) |
| `pl-PL`   | polski (Polska)          |
| `pt-BR`   | portugalski (Brazylia)   |
| `ru-RU`   | rosyjski (Rosja)         |
| `tl-PH`   | tagalski (Filipiny)      |
| `tr-TR`   | turecki (Turcja)         |
| `uk-UA`   | ukraiński (Ukraina)      |
| `ur-PK`   | urdu (Pakistan)          |
| `vi-VN`   | wietnamski (Wietnam)     |
| `zh-CN`   | chiński (Chiny)          |
| `zh-Hans` | chiński (uproszczony)    |

System musi zapewniać wystarczające zasadnicze wsparcie tłumaczeniowe dla każdego wymienionego locale, aby można było uznać go za zgodny ze specyfikacją.

Wymagany zestaw locale nie ma reprezentować każdego języka, dialektu, regionu ani systemu pisma. Zamiast tego ustanawia praktyczną podstawę szerokiej międzynarodowej użyteczności w wielu typowych, technologicznie istotnych grupach językowych.

<a id="user-facing-content"></a>
## Treść skierowana do użytkownika

<a id="user-facing-content-1"></a>
### Treść skierowana do użytkownika

Treść skierowana do użytkownika to każda treść przeznaczona do tego, aby użytkownik końcowy ją postrzegał, czytał, słyszał, wybierał, rozumiał albo na jej podstawie działał.

Treść skierowana do użytkownika może obejmować:

* nawigację
* etykiety
* przyciski
* menu
* kontrolki
* nagłówki
* okna dialogowe
* ustawienia
* instrukcje
* prompty
* ostrzeżenia
* błędy
* potwierdzenia
* komunikaty statusu
* tekst wprowadzający
* wymaganą treść pomocy
* kontrolki wyboru języka
* treść podstawowych przepływów pracy

Treść skierowana do użytkownika nie musi być wizualna. Może również obejmować treść słuchową, dotykową, symboliczną lub multisensoryczną, gdy ta treść przekazuje użytkownikowi znaczenie.

<a id="essential-user-facing-content"></a>
### Zasadnicza treść skierowana do użytkownika

Zasadnicza treść skierowana do użytkownika to treść skierowana do użytkownika, której użytkownik rozsądnie potrzebuje, aby zrozumieć, nawigować, konfigurować lub obsługiwać zasadnicze działanie systemu.

Zasadnicza treść skierowana do użytkownika może obejmować:

* główną nawigację
* podstawowe ekrany i widoki
* ustawienia i preferencje
* etykiety skierowane do użytkownika
* kontrolki skierowane do użytkownika
* wymagane instrukcje
* ważne ostrzeżenia
* ważne błędy
* zasadnicze prompty
* wymagane komunikaty potwierdzenia
* kontrolki wyboru języka
* podstawowe przepływy pracy potrzebne do normalnego użycia

System nie musi tłumaczyć każdej opcjonalnej strony, ukrytego komunikatu, wewnętrznej etykiety ani niezasadniczego tekstu, aby spełnić I18NSPEC. Treść wymagana do zwykłego zasadniczego użycia musi jednak zostać przetłumaczona zgodnie z wymaganiami tej specyfikacji.

<a id="critical-user-facing-content"></a>
### Krytyczna treść skierowana do użytkownika

Krytyczna treść skierowana do użytkownika to zasadnicza treść skierowana do użytkownika, w przypadku której niezrozumienie może uniemożliwić znaczące użycie, spowodować poważny błąd albo skłonić użytkownika do podjęcia ważnej decyzji bez zrozumienia konsekwencji.

Krytyczna treść skierowana do użytkownika może obejmować:

* kontrolki wyboru języka
* ostrzeżenia przed działaniami destrukcyjnymi
* ostrzeżenia przed usunięciem konta
* potwierdzenia płatności
* potwierdzenia zakupu
* wybory dotyczące prywatności
* ostrzeżenia bezpieczeństwa
* prompty zgody
* wymagane instrukcje bezpieczeństwa
* wymagane instrukcje konfiguracji
* wymagane komunikaty błędów
* podstawową nawigację wymaganą do dotarcia do ustawień języka

Krytyczna treść skierowana do użytkownika musi zostać przetłumaczona dla każdego wymaganego locale.

Progu 75% zasadniczego pokrycia tłumaczeniem nie wolno używać do pozostawiania treści krytycznej bez tłumaczenia.

<a id="nonessential-content"></a>
### Treść niezasadnicza

Treść niezasadnicza to treść, która nie jest rozsądnie wymagana, aby użytkownik mógł zrozumieć, nawigować, konfigurować lub obsługiwać zasadnicze działanie systemu.

Treść niezasadnicza może obejmować:

* wewnętrzne identyfikatory
* nazwy w kodzie źródłowym
* ciągi tylko do debugowania
* szczegóły implementacyjne skierowane do deweloperów
* ukryty tekst diagnostyczny
* opcjonalne strony marketingowe
* opcjonalne strony wsparcia
* niezasadniczy tekst prawny lub biznesowy poza ocenianym zakresem
* treść stron trzecich niekontrolowaną przez oceniany system

Treść niezasadnicza może zostać przetłumaczona, ale nie jest wymagana dla zgodności z I18NSPEC, chyba że stanie się konieczna dla zasadniczego zrozumienia lub działania użytkownika.

<a id="translation-coverage"></a>
## Pokrycie tłumaczeniem

<a id="essential-translation-coverage"></a>
### Zasadnicze pokrycie tłumaczeniem

Zasadnicze pokrycie tłumaczeniem to ilość zasadniczej treści skierowanej do użytkownika przetłumaczonej dla określonego locale.

Pokrycie powinno być oceniane według znaczących jednostek treści skierowanej do użytkownika, a nie według rozmiaru plików, liczby bajtów, liczby wierszy, rozmiaru repozytorium czy liczby stron.

Na przykład jeden nieprzetłumaczony przycisk sterujący zasadniczym działaniem może mieć większe znaczenie niż duży nieprzetłumaczony opcjonalny akapit, który nie wpływa na zwykłe użycie.

Pokrycie tłumaczeniem powinno być oceniane według tego, czy użytkownik może w znaczący sposób zrozumieć i obsługiwać zasadniczy system w ocenianym locale.

<a id="coverage-requirement"></a>
### Wymóg pokrycia

System spełnia wymóg pokrycia tłumaczeniem dla locale, gdy ponad 75% zasadniczej treści skierowanej do użytkownika jest przetłumaczone dla tego locale.

System spełnia wymóg pokrycia I18NSPEC, gdy osiąga ten próg dla każdego locale w wymaganym zestawie locale.

W praktycznym przeglądzie można to przedstawić tak:

| Locale  | Zasadnicze pokrycie tłumaczeniem | Wynik |
| ------- | -------------------------------- | ----- |
| `en-US` | 100%                             | Pass  |
| `es-ES` | 94%                              | Pass  |
| `ar-SA` | 78%                              | Pass  |
| `ja-JP` | 61%                              | Fail  |

Locale z pokryciem 75% lub niższym nie spełnia wymogu pokrycia.

Locale z pokryciem powyżej 75% nadal może nie przejść, jeśli krytyczna treść skierowana do użytkownika pozostaje nieprzetłumaczona.

<a id="critical-content-requirement"></a>
### Wymóg dotyczący treści krytycznej

Cała krytyczna treść skierowana do użytkownika musi zostać przetłumaczona dla każdego wymaganego locale.

System może nie przejść I18NSPEC nawet wtedy, gdy spełnia ogólny próg pokrycia, jeżeli brakuje jednego lub więcej elementów krytycznej treści skierowanej do użytkownika, są one nieprzetłumaczone, mylące albo nie są znacząco zrozumiałe.

Na przykład system nie powinien zostać uznany za zgodny ze specyfikacją, jeśli ogólny interfejs jest przetłumaczony, ale ostrzeżenie o usunięciu konta, potwierdzenie zakupu, ostrzeżenie bezpieczeństwa albo selektor języka pozostają nieprzetłumaczone.

<a id="language-selection"></a>
## Wybór języka

<a id="active-locale"></a>
### Aktywne locale

Aktywne locale to locale aktualnie wybrane dla doświadczenia użytkownika.

Aktywne locale określa, jaka przetłumaczona treść powinna być wyświetlana, dostarczana albo w inny sposób komunikowana użytkownikowi.

<a id="default-locale"></a>
### Domyślne locale

Domyślne locale to locale używane wtedy, gdy użytkownik nie wybrał aktywnego locale albo gdy żadna preferencja użytkownika nie jest dostępna.

System musi zdefiniować domyślne locale.

Domyślne locale powinno być udokumentowane albo rozsądnie możliwe do ustalenia przez recenzenta.

<a id="language-selection-mechanism"></a>
### Mechanizm wyboru języka

System zgodny musi zapewniać rozsądny sposób, w jaki użytkownik końcowy może zmienić aktywne locale.

Mechanizm wyboru języka musi być dostępny bez wymagania od użytkownika, aby:

* modyfikował kod źródłowy
* używał narzędzi deweloperskich
* edytował nieudokumentowane pliki konfiguracyjne
* instalował nieoficjalne poprawki
* polegał na ukrytym zachowaniu
* kontaktował się ze wsparciem w celu zwykłej zmiany języka

Mechanizm wyboru języka może być zapewniony przez:

* ustawienia aplikacji
* preferencje konta
* selektor języka
* prompt startowy
* ustawienia przeglądarki
* ustawienia systemu operacyjnego
* ustawienia urządzenia
* inny odpowiedni mechanizm dostępny dla użytkownika końcowego

Mechanizm nie musi podążać za jednym konkretnym wzorcem projektowym. Musi rozsądnie pozwalać użytkownikowi wybrać obsługiwany język.

<a id="language-option-labels"></a>
### Etykiety opcji językowych

Podczas wyświetlania opcji językowych system powinien identyfikować każdy język w sposób zrozumiały dla użytkowników, którzy mówią tym językiem.

Opcja językowa może zawierać:

* nazwę języka w tym języku
* nazwę języka w aktualnie aktywnym języku
* kod locale
* etykietę regionalną
* etykietę pisma

Na przykład:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Dokładne formatowanie może się różnić.

Intencją jest to, aby użytkownicy mogli rozpoznać własny język, w miarę możliwości zrozumieć aktualnie wyświetlaną nazwę języka i zidentyfikować powiązany kod locale.

<a id="fallbacks-and-locale-equivalence"></a>
## Fallbacki i równoważność locale

<a id="fallback-locale"></a>
### Fallback locale

Fallback locale to locale używane wtedy, gdy przetłumaczona treść nie jest dostępna dla aktywnego locale.

Fallback locale może pomóc zachować użyteczność, ale treść fallback nie jest automatycznie uznawana za przetłumaczoną treść dla aktywnego locale.

Na przykład, jeśli system jest ustawiony na `es-MX`, ale wyświetla tekst `en-US`, ponieważ brakuje tłumaczenia hiszpańskiego, ten angielski tekst może być przydatny jako fallback, ale nie powinien być liczony jako pokrycie tłumaczeniem na język hiszpański.

<a id="fallback-behavior"></a>
### Zachowanie fallback

System zgodny może używać zachowania fallback, gdy treść zlokalizowana jest niedostępna.

Zachowanie fallback powinno unikać uszkodzonego, pustego lub mylącego wyniku.

Zachowania fallback nie wolno używać do fałszywego deklarowania pokrycia tłumaczeniem dla wymaganego locale.

System może otrzymać ostrzeżenie albo nie przejść weryfikacji, jeśli zachowanie fallback jest nadmierne, mylące, nieudokumentowane albo powoduje, że zasadnicza treść wygląda na nieprzetłumaczoną w wymaganym locale.

<a id="locale-equivalence"></a>
### Równoważność locale

Równoważność locale występuje wtedy, gdy jedno tłumaczenie może rozsądnie obsłużyć więcej niż jedno locale bez uniemożliwiania zasadniczego zrozumienia lub obsługi.

Na przykład system może używać jednego tłumaczenia angielskiego dla `en-US`, `en-GB` i `en-IN`, jeżeli zasadnicze znaczenie pozostaje jasne dla użytkowników każdego locale.

Równoważność locale może zostać zaakceptowana podczas przeglądu, gdy różnice regionalne są niewielkie i nie wpływają istotnie na zasadniczą użyteczność.

Równoważności locale nie wolno używać, gdy brakujące locale powodowałoby znaczącą dezorientację, pomijałoby ważną terminologię regionalną, psuło zasadnicze zachowanie albo uniemożliwiało użytkownikom zrozumienie systemu.

Na przykład system nie powinien zakładać, że niepowiązane języki są równoważne, ponieważ mają wspólny kierunek pisma, region geograficzny, rodzinę pisma albo szeroką kategorię kulturową.

Równoważność locale jest osądem przeglądu, a nie automatyczną regułą.

<a id="implementation-requirements"></a>
## Wymagania implementacyjne

<a id="stable-translation-mechanism"></a>
### Stabilny mechanizm tłumaczenia

System zgodny musi używać stabilnego mechanizmu tłumaczenia odpowiedniego dla ocenianego systemu.

Stabilny mechanizm tłumaczenia powinien pozwalać utrzymywać, aktualizować, przeglądać i rozszerzać przetłumaczoną treść bez polegania na kruchym lub nieudokumentowanym zachowaniu.

Stabilny mechanizm tłumaczenia może obejmować:

* pliki zasobów
* tabele tłumaczeń
* trasowanie świadome locale
* skompilowane zasoby językowe
* statyczne strony lokalizowane
* pakiety językowe ładowane w czasie działania
* tłumaczenia oparte na bazie danych
* inną udokumentowaną strukturę tłumaczeń

System powinien unikać twardego kodowania zasadniczej treści skierowanej do użytkownika w sposób, który uniemożliwia wymaganą obsługę tłumaczeń.

<a id="preservation-of-meaning"></a>
### Zachowanie znaczenia

Tłumaczenie zachowuje znaczenie, gdy użytkownik może rozsądnie zrozumieć tę samą zasadniczą instrukcję, etykietę, ostrzeżenie, kontrolkę, ustawienie lub przepływ pracy co użytkownicy języka źródłowego.

Tłumaczenie nie musi być identyczne słowo w słowo z treścią źródłową.

Tłumaczenie może zmienić szyk wyrazów, gramatykę, strukturę zdania, idiom, ton lub sformułowanie, gdy jest to konieczne, aby przekazać to samo zasadnicze znaczenie w języku docelowym.

Tłumaczenie może nie przejść przeglądu, jeśli jest mylące, niekompletne, bezsensowne, uszkodzone maszynowo albo znacząco różne od treści źródłowej w sposób, który wpływa na zasadnicze użycie.

<a id="direction-sensitive-languages"></a>
### Języki wrażliwe na kierunek tekstu

Niektóre wymagane locale powszechnie używają kierunku tekstu od prawej do lewej.

System zgodny nie może uniemożliwiać odczytania, zrozumienia, wybrania ani użycia zasadniczej przetłumaczonej treści tylko dlatego, że aktywne locale używa innego kierunku tekstu.

System powinien zachowywać czytelną kolejność, zachowanie interpunkcji oraz powiązanie kontrolek w językach wrażliwych na kierunek tekstu.

Pełne dopracowanie wizualne, jakość typografii, zachowanie dostępności i udoskonalenie układu mogą wymagać osobnego przeglądu. Zasadnicza przetłumaczona treść musi jednak pozostać znacząco użyteczna.

<a id="locale-sensitive-values"></a>
### Wartości zależne od locale

Wartości zależne od locale to wartości, których znaczenie lub czytelność może różnić się w zależności od języka, regionu, pisma lub kultury.

Wartości zależne od locale mogą obejmować:

* daty
* godziny
* liczby
* waluty
* jednostki miary
* formy liczby mnogiej
* rodzaj gramatyczny
* kolejność sortowania
* formaty adresów
* formaty numerów telefonów

I18NSPEC nie wymaga pełnej lokalizacji każdej wartości zależnej od locale, chyba że ta wartość jest zasadnicza dla zrozumienia lub obsługi systemu.

Gdy wartości zależne od locale są zasadnicze, system powinien przedstawiać je w sposób, który użytkownicy aktywnego locale mogą rozsądnie zrozumieć.

<a id="verification"></a>
## Weryfikacja

<a id="within-spec"></a>
### W zgodzie ze specyfikacją

System uznaje się za zgodny ze specyfikacją, gdy CatalystUI Team przejrzał system i uznał za rozsądne stwierdzenie, że spełnia I18NSPEC.

System może być zgodny ze specyfikacją, gdy:

* każde wymagane locale jest obsługiwane
* ponad 75% zasadniczej treści skierowanej do użytkownika jest przetłumaczone dla każdego wymaganego locale
* cała krytyczna treść skierowana do użytkownika jest przetłumaczona dla każdego wymaganego locale
* użytkownicy mogą rozsądnie wybrać aktywne locale
* zachowanie fallback nie deklaruje fałszywie pokrycia tłumaczeniem
* równoważność locale, jeśli jest używana, jest rozsądna i udokumentowana
* przetłumaczona treść zachowuje zasadnicze znaczenie

System może być zgodny ze specyfikacją nawet wtedy, gdy pewna treść niezasadnicza pozostaje nieprzetłumaczona.

System może być zgodny ze specyfikacją nawet wtedy, gdy tłumaczenia nie są doskonałe, pod warunkiem że zasadnicze znaczenie jest zachowane, a wymagania tej specyfikacji są spełnione.

<a id="warnings"></a>
### Ostrzeżenia

Ostrzeżenie może zostać wydane, gdy system wydaje się spełniać I18NSPEC, ale zawiera kwestie, które powinny zostać udokumentowane.

Ostrzeżenia mogą obejmować:

* drobną nieprzetłumaczoną treść niezasadniczą
* niespójną terminologię między locale
* niedoskonałe, lecz zrozumiałe tłumaczenia
* akceptowalną równoważność locale, którą należy udokumentować
* ograniczone zachowanie fallback
* częściowo przetłumaczone strony opcjonalne
* problemy z układem wrażliwym na kierunek tekstu, które nie uniemożliwiają zasadniczego użycia
* wartości zależne od locale, które są zrozumiałe, ale nie idealne

Ostrzeżenia niekoniecznie uniemożliwiają weryfikację.

<a id="failures"></a>
### Niepowodzenia

Niepowodzenie występuje, gdy system nie spełnia jednego lub więcej wymaganych warunków I18NSPEC.

Niepowodzenia mogą obejmować:

* brak obsługi wymaganego locale
* zasadnicze pokrycie tłumaczeniem na poziomie 75% lub niższym dla wymaganego locale
* nieprzetłumaczoną krytyczną treść skierowaną do użytkownika
* brak rozsądnego mechanizmu wyboru języka
* wybór języka wymagający modyfikacji kodu źródłowego
* wybór języka wymagający narzędzi deweloperskich
* uszkodzone ładowanie tłumaczeń
* mylące deklaracje locale
* nadmierne zachowanie fallback
* treść fallback liczona jako przetłumaczona treść bez ważnej równoważności locale
* treść wrażliwa na kierunek tekstu, która jest nieczytelna lub nieużyteczna
* zasadnicze przepływy pracy niedostępne w jednym lub więcej wymaganych locale

Niepowodzenia uniemożliwiają weryfikację do czasu rozwiązania problemów.

<a id="verification-validity"></a>
### Ważność weryfikacji

Weryfikacja I18NSPEC dotyczy tylko ocenionego stanu systemu w momencie wydania weryfikacji.

System może zachować weryfikację po późniejszych aktualizacjach, o ile zachowuje zweryfikowaną podstawę internacjonalizacji.

Drobne zmiany brzmienia, dodane tłumaczenia, ulepszone tłumaczenia i zwykłe aktualizacje treści nie unieważniają automatycznie weryfikacji.

Nowy przegląd może być wymagany, jeśli system:

* usuwa obsługę wymaganego locale
* psuje wybór języka
* znacząco zmniejsza zasadnicze pokrycie tłumaczeniem
* pozostawia nowe zasadnicze przepływy pracy bez tłumaczenia
* zastępuje przetłumaczoną treść treścią fallback
* zmienia architekturę tłumaczeń w sposób wpływający na zweryfikowane zachowanie
* wprowadza duże zmiany skierowane do użytkownika, które zmieniają oceniany zakres

Innymi słowy, ulepszanie obsługi tłumaczeń jest zwykle w porządku.

Zepsucie zweryfikowanej wielojęzycznej podstawy może wymagać przeglądu.
