<!-- To tłumaczenie zostało wygenerowane przez ChatGPT i powinno zostać sprawdzone przez tłumacza. -->

<!-- Usuń te wiersze w pull request po zweryfikowaniu tłumaczenia. -->

![CatalystUI Verified for Internationalization](/images/verification/verified-logo-internationalization.png)

# CatalystUI Verified for Internationalization

Witamy w dokumentacji CatalystUI Verification dotyczącej internacjonalizacji.

**CatalystUI Verified for Internationalization** oznacza, że system, usługa, framework, aplikacja lub implementacja została sprawdzona przez CatalystUI Team i uznana za zapewniającą wystarczające wsparcie wielojęzyczne dla wymaganego zestawu języków internacjonalizacji CatalystUI.

Ta weryfikacja nie jest ogólnym rankingiem jakości tłumaczeń, stylu pisania, głębokości lokalizacji ani adaptacji kulturowej. Zamiast tego wskazuje, czy oceniany system zapewnia stabilną i praktyczną podstawę, dzięki której użytkownicy mogą korzystać z jego zasadniczej funkcjonalności w wymaganych obsługiwanych językach.

Mówiąc prościej, ta weryfikacja pyta, czy użytkownicy mogą w znaczący sposób korzystać z zasadniczych części systemu w wymaganych językach oraz czy otrzymują rozsądny sposób wyboru języka, który rozumieją.

<a id="purpose"></a>
## Cel

Internacjonalizacja ma znaczenie, ponieważ systemu nie można uznać za szeroko dostępny, jeżeli jego zasadnicze znaczenie jest zamknięte za jednym językiem.

CatalystUI jest projektowany wokół jasności, spójności i wiernego przedstawienia interakcji człowieka z komputerem. Język jest częścią tej interakcji. Jeśli użytkownik nie rozumie etykiet, instrukcji, ostrzeżeń, kontrolek, ustawień albo zasadniczej treści systemu, system nie komunikuje się jasno, nawet jeśli podstawowa funkcjonalność technicznie działa.

Internationalization Verification istnieje po to, aby identyfikować systemy, które zapewniają wystarczające przetłumaczone wsparcie dla użytkowników w wymaganym zestawie języków CatalystUI. Celem nie jest wymaganie doskonałego tłumaczenia każdego opcjonalnego słowa, ukrytego komunikatu deweloperskiego czy niezasadniczej strony. Celem jest ustalenie, czy zasadnicze części systemu mogą być rozumiane i używane przez ludzi w każdym wymaganym języku.

<a id="what-verification-means"></a>
## Co oznacza weryfikacja

System staje się **CatalystUI Verified for Internationalization**, gdy zostanie sprawdzony względem wymagań wymienionych w tej sekcji i uznany za zgodny ze specyfikacją.

Aby zostać zweryfikowanym, system musi zapewniać tłumaczenia dla ponad 75% zasadniczych części systemu skierowanych do użytkownika w każdym wymaganym języku. Musi także zapewniać rozsądny mechanizm dla użytkownika końcowego umożliwiający zmianę aktywnego języka.

System nie musi tłumaczyć każdego wewnętrznego identyfikatora, szczegółu implementacyjnego skierowanego do deweloperów, ciągu debugowania, opcjonalnej strony marketingowej ani niezasadniczego tekstu wsparcia. Jednak części skierowane do użytkownika wymagane do zrozumienia i obsługi zasadniczego systemu muszą być dostępne w każdym wymaganym języku.

<a id="required-languages"></a>
## Wymagane języki

Aktualny zestaw języków internacjonalizacji CatalystUI został wybrany na podstawie praktycznego przeglądu języków często potrzebnych w kontekstach technologicznych, w tym globalnego zasięgu liczby użytkowników, powszechnego użycia online, oczekiwań wobec oprogramowania wielojęzycznego oraz szerokich regionalnych potrzeb dostępności.

Ten zestaw języków nie ma reprezentować każdego języka, każdego dialektu ani każdego wariantu regionalnego. Zamiast tego ustanawia praktyczną podstawę dla systemów dążących do szerokiej międzynarodowej użyteczności w wielu najczęstszych na świecie grupach językowych związanych z technologią.

Aktualny zestaw języków internacjonalizacji CatalystUI obejmuje następujące locale:

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

System musi zapewniać wystarczające zasadnicze pokrycie tłumaczeniem dla każdej wymienionej grupy językowej, aby można było uznać go za zgodny ze specyfikacją.

Warianty regionalne mogą jednak być oceniane z rozsądną elastycznością, gdy różnice między wariantami są niewielkie i nie wpływają istotnie na zdolność użytkownika do zrozumienia lub obsługi systemu. Na przykład system może nadal kwalifikować się do weryfikacji, jeśli zapewnia jedno mocne tłumaczenie angielskie, ale nie tłumaczy osobno każdego regionalnego wariantu angielskiego, o ile zasadnicze znaczenie, nawigacja, instrukcje, ostrzeżenia i kontrolki pozostają jasne dla użytkowników brakujących wariantów.

Ta elastyczność nie ma zastosowania, gdy brakujący wariant powodowałby znaczącą dezorientację, pomijał regionalnie ważną terminologię, psuł zachowanie zależne od locale albo uniemożliwiał użytkownikom zrozumienie zasadniczych części systemu.

<a id="essential-translation-coverage"></a>
## Zasadnicze pokrycie tłumaczeniem

W przypadku Internationalization Verification **zasadnicze pokrycie tłumaczeniem** odnosi się do części systemu, których użytkownik rozsądnie potrzebuje, aby zrozumieć, nawigować, konfigurować i obsługiwać system.

Zasadnicze części mogą obejmować:

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

System uznaje się za spełniający wymóg pokrycia tłumaczeniem, gdy ponad 75% jego zasadniczej treści skierowanej do użytkownika jest dostępne w każdym wymaganym języku.

Ten próg istnieje, ponieważ praca nad internacjonalizacją może być duża, ciągła i zależna od kontekstu. System może nadal być zgodny ze specyfikacją, nawet jeśli część niezasadniczej lub mniej priorytetowej treści pozostaje nieprzetłumaczona. Jednak zasadnicze doświadczenie musi być znacząco dostępne w każdym wymaganym języku.

<a id="language-selection"></a>
## Wybór języka

Zweryfikowany system musi zapewniać rozsądny sposób, w jaki użytkownik końcowy może zmienić aktywny język.

Mechanizm wyboru języka powinien być łatwy do znalezienia, zrozumiały i dostępny bez wymagania wiedzy technicznej. Użytkownicy nie powinni musieć edytować plików konfiguracyjnych, modyfikować kodu źródłowego, instalować narzędzi deweloperskich ani polegać na nieudokumentowanym zachowaniu tylko po to, aby zmienić język.

Podczas wyświetlania opcji językowych system powinien identyfikować każdy język w sposób zrozumiały zarówno dla użytkowników, którzy mówią tym językiem, jak i dla użytkowników aktualnie korzystających z innego wybranego języka.

Na przykład opcja językowa może być wyświetlona tak:

```md
English (English) (en-US)
Español (Spanish) (es-ES)
Français (French) (fr-FR)
العربية (Arabic) (ar-SA)
```

Dokładne formatowanie może się różnić, ale intencja powinna pozostać taka sama: użytkownicy powinni móc rozpoznać własny język, w miarę możliwości zrozumieć aktualnie wyświetlaną nazwę języka i zidentyfikować powiązany kod locale.

<a id="what-within-spec-means"></a>
## Co oznacza „zgodny ze specyfikacją”

Gdy system jest uznany za **zgodny ze specyfikacją**, oznacza to, że CatalystUI Team ręcznie sprawdził system i uznał za rozsądne stwierdzenie, że spełnia wymagania internacjonalizacji opisane przez tę kategorię weryfikacji.

Nie wymaga to jednego sztywnego wzorca implementacji. System może spełnić wymaganie przez pliki zasobów, tabele tłumaczeń, trasowanie świadome locale, skompilowane zasoby językowe, tłumaczenia oparte na bazie danych, pakiety językowe ładowane w czasie działania albo inny stabilny mechanizm odpowiedni dla systemu.

Weryfikacja dotyczy praktycznej zdolności użytkowników do dostępu do zasadniczego systemu w wymaganych językach, a nie tego, czy system używa jednej konkretnej architektury tłumaczeń.

<a id="what-verification-does-not-mean"></a>
## Czego weryfikacja nie oznacza

CatalystUI Verified for Internationalization nie gwarantuje, że każde tłumaczenie jest doskonałe, literackie, idiomatyczne, kulturowo kompletne albo prawnie wystarczające dla każdego regionu.

Nie weryfikuje też automatycznie dostępności, typografii, układu od prawej do lewej, formatowania specyficznego dla locale, formatowania walut, formatowania dat, zgodności prawnej ani regionalnych wymagań biznesowych, chyba że te kwestie są uwzględnione w ocenianym zakresie internacjonalizacji.

System może zapewniać silne pokrycie tłumaczeniem i nadal wymagać osobnego przeglądu pod kątem dostępności, jakości lokalizacji, zgodności regionalnej albo innych specjalistycznych kwestii.

<a id="why-this-verification-exists"></a>
## Dlaczego ta weryfikacja istnieje

Interfejs użytkownika jest użyteczny tylko wtedy, gdy użytkownik rozumie, co on komunikuje.

Wiele systemów deklaruje obsługę języków, tłumacząc jedynie małą część doświadczenia, ukrywając wybór języka, pomijając ważne komunikaty albo pozostawiając zasadnicze przepływy pracy częściowo nieprzetłumaczone. To tworzy dezorientację i uniemożliwia użytkownikom zaufanie systemowi.

Internationalization Verification istnieje po to, aby ustanowić jaśniejszy standard. Identyfikuje systemy, które podejmują poważny, praktyczny wysiłek wspierania użytkowników w wymaganym zestawie języków CatalystUI i zapewniają rozsądny sposób wyboru potrzebnego języka.

<a id="verification-scope"></a>
## Zakres weryfikacji

CatalystUI Verification for Internationalization dotyczy ocenianego systemu, usługi, frameworka, aplikacji lub implementacji w stanie, w jakim istniała w momencie wydania weryfikacji.

Zweryfikowany system zapewnia wystarczające zasadnicze pokrycie tłumaczeniem dla wymaganych języków. Nie gwarantuje, że każda przyszła strona, funkcja, wersja, plugin, rozszerzenie albo integracja strony trzeciej automatycznie jest zgodna ze specyfikacją.

Oddzielne produkty, moduły, usługi, pakiety językowe albo większe rewizje mogą wymagać własnego przeglądu w zależności od żądanej kategorii weryfikacji.

<a id="verification-validity"></a>
## Ważność weryfikacji

CatalystUI Verification dotyczy tylko ocenionego stanu systemu w momencie wydania weryfikacji.

System może zachować weryfikację po późniejszych aktualizacjach, o ile zachowuje zweryfikowaną podstawę internacjonalizacji. Drobne zmiany brzmienia, dodane tłumaczenia i zwykłe aktualizacje treści nie unieważniają automatycznie weryfikacji.

Nowy przegląd może być wymagany, jeśli system usuwa wymaganą obsługę języka, psuje wybór języka, znacząco zmniejsza zasadnicze pokrycie tłumaczeniem albo zmienia architekturę internacjonalizacji w sposób wpływający na zweryfikowane zachowanie.

Innymi słowy, ulepszanie obsługi tłumaczeń jest zwykle w porządku. Zepsucie zweryfikowanej wielojęzycznej podstawy może wymagać przeglądu.

<a id="verified-systems"></a>
## Zweryfikowane systemy

Znane systemy zweryfikowane pod kątem internacjonalizacji są wymienione osobno na odpowiedniej stronie CatalystUI Verified.
