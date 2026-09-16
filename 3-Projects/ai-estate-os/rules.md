# AI-Estate-OS — Rules

> Reguły obowiązujące wyłącznie w projekcie AI-Estate-OS.
> Mają pierwszeństwo przed standardowym sposobem pracy agenta,
> jeśli nie są sprzeczne z wymaganiami bezpieczeństwa lub prawa.
> Zmiany wymagają akceptacji właściciela projektu.

---

## Hard rules

### 1. Źródło prawdy

- Rzut 2D oraz zweryfikowane dane źródłowe są podstawowym źródłem prawdy dla geometrii mieszkania.
- Nie wolno zmieniać układu mieszkania tylko po to, aby wizualizacja 3D wyglądała lepiej.
- Nie wolno bez podstawy przesuwać, dodawać ani usuwać ścian, drzwi, okien lub innych elementów geometrii.
- Dane znalezione w innym źródle nie mogą automatycznie zastępować danych dotyczących konkretnego analizowanego lokalu.

### 2. Zakaz wymyślania brakujących danych

- AI nie może przedstawiać danych wygenerowanych, oszacowanych lub wywnioskowanych jako danych źródłowych.
- Brakujący wymiar, wysokość, położenie elementu lub inna informacja musi zostać oznaczona jako brak danych.
- Jeżeli wykonanie modelu wymaga przyjęcia założenia, należy je jawnie oznaczyć przed wykorzystaniem.
- Założenie nie staje się faktem tylko dlatego, że zostało wykorzystane w poprzedniej analizie.

### 3. Fakty, wnioski i szacunki

Wyniki analiz należy, gdy ma to znaczenie dla decyzji klienta, rozróżniać jako:

- **ZWERYFIKOWANY FAKT** — potwierdzony przez wskazane źródło,
- **WNIOSKOWANIE** — logicznie wyprowadzone z dostępnych danych,
- **SZACUNEK** — wartość przybliżona,
- **ZAŁOŻENIE** — informacja przyjęta roboczo z powodu braku danych,
- **NIEZWERYFIKOWANE** — informacja wymagająca dalszego sprawdzenia.

AI nie może podnosić poziomu pewności informacji bez nowego dowodu lub źródła.

### 4. Weryfikacja przed prezentacją

- Kluczowe dane dotyczące konkretnego mieszkania powinny być możliwe do powiązania ze źródłem.
- Numer mieszkania, inwestycja, deweloper, powierzchnia, cena, status dostępności i rzut 2D muszą dotyczyć tego samego lokalu przed połączeniem ich w jedną analizę.
- W przypadku sprzeczności między źródłami należy ją wskazać, zamiast arbitralnie wybierać wygodniejszą wartość.
- Aktualność informacji, szczególnie ceny i dostępności, musi być uwzględniana w ocenie wiarygodności.

### 5. Zgodność z prawem

- Pozyskiwanie, przetwarzanie i prezentowanie danych musi odbywać się zgodnie z obowiązującym prawem.
- Należy respektować prawa do rzutów, grafik, zdjęć, opisów i innych materiałów.
- Publiczna dostępność materiału w internecie nie oznacza automatycznie prawa do jego kopiowania, przetwarzania lub dalszego rozpowszechniania.
- Nie wolno omijać technicznych lub prawnych ograniczeń dostępu tylko po to, aby uzyskać dane.
- Jeżeli status prawny wykorzystania materiału jest niejasny, należy oznaczyć problem do weryfikacji przed wdrożeniem funkcji produkcyjnej.

### 6. Kontrola 2D → 3D

Proces 2D → 3D musi zachowywać geometrię wynikającą ze źródła.

Przed uznaniem wizualizacji za poprawną należy sprawdzić co najmniej:

- układ pomieszczeń,
- położenie ścian,
- drzwi,
- okna,
- proporcje pomieszczeń,
- położenie wejścia,
- relacje pomiędzy pomieszczeniami.

Elementy dekoracyjne i wyposażenie nie mogą prowadzić do zmiany geometrii mieszkania.

### 7. Kontrola zakresu MVP

- MVP dotyczy nowych mieszkań deweloperskich w Warszawie.
- Jednocześnie obsługiwanych jest maksymalnie czterech deweloperów/projektów wskazanych w `brief.md`.
- Dodanie kolejnego wymaga usunięcia jednego z aktualnej listy.
- Nie rozszerzamy MVP na rynek wtórny ani całą Polskę bez świadomej decyzji o zmianie zakresu.
- Maksymalny budżet MVP wynosi 500 PLN.
- Docelowy maksymalny czas wykonania MVP wynosi 14 dni.

### 8. Standardy architektoniczno-projektowe wizualizacji 3D

Wizualizacja 3D mieszkania musi respektować zarówno dane wynikające ze źródłowego rzutu 2D, jak również właściwe dla danego przypadku wymagania architektoniczne i projektowe.

**Zasada nadrzędna:** AI-Estate-OS nie może „upiększać” mieszkania kosztem prawdy architektonicznej. Dokładność geometrii, skali i funkcjonalności ma pierwszeństwo przed atrakcyjnością renderu.

#### A. Geometria architektoniczna

Należy zachować:

- rzeczywisty obrys lokalu,
- układ i proporcje pomieszczeń,
- położenie ścian,
- położenie i szerokość otworów drzwiowych,
- położenie i wymiary okien, jeżeli są dostępne,
- kierunki otwierania drzwi, jeżeli wynikają z dokumentacji,
- położenie pionów i elementów instalacyjnych, jeżeli są oznaczone,
- balkony, loggie i tarasy,
- wysokość pomieszczeń, jeżeli została podana,
- inne elementy konstrukcyjne widoczne w dokumentacji.

Nie wolno poprawiać geometrii mieszkania wyłącznie ze względów estetycznych.

#### B. Skala i wymiary

Wszystkie dostępne wymiary źródłowe mają pierwszeństwo przed wymiarami oszacowanymi przez AI.

Jeżeli dokumentacja zawiera skalę, wymiary lub powierzchnie, należy wykorzystywać je do kontroli modelu.

Nieznanych wymiarów nie wolno przedstawiać jako pomierzonych.

Wymiary przyjęte pomocniczo muszą być oznaczone jako **ZAŁOŻENIE PROJEKTOWE**.

#### C. Funkcjonalność pomieszczeń

Rozmieszczenie wyposażenia powinno uwzględniać funkcję danego pomieszczenia oraz podstawowe zasady ergonomii.

Należy kontrolować między innymi:

- możliwość otwierania drzwi,
- możliwość otwierania okien,
- dostęp do ciągów komunikacyjnych,
- możliwość korzystania z mebli i urządzeń,
- kolizje pomiędzy wyposażeniem,
- dostęp do elementów wymagających obsługi.

Wizualizacja nie może przedstawiać rozwiązania funkcjonalnego, którego nie da się racjonalnie zastosować w przedstawionej geometrii mieszkania.

#### D. Kuchnia i łazienka

Przy aranżacji kuchni i łazienki należy uwzględniać dostępne informacje dotyczące:

- przyłączy wodno-kanalizacyjnych,
- wentylacji,
- urządzeń sanitarnych,
- urządzeń kuchennych,
- pionów instalacyjnych,
- wymaganych przestrzeni użytkowych.

AI nie może dowolnie przenosić instalacji tylko dlatego, że poprawia to wygląd wizualizacji.

Jeżeli lokalizacja instalacji nie jest znana, należy ją oznaczyć jako informację wymagającą potwierdzenia.

#### E. Ergonomia

Projekt wyposażenia powinien uwzględniać odpowiednie dla danego rozwiązania zasady ergonomii i przestrzeni użytkowej.

Należy kontrolować między innymi:

- przejścia,
- dostęp do drzwi,
- dostęp do okien,
- przestrzeń przed szafami,
- przestrzeń wokół łóżek,
- przestrzeń użytkową przy stołach i krzesłach,
- korzystanie z wyposażenia kuchennego,
- korzystanie z urządzeń sanitarnych.

#### F. Wymagania techniczne i prawne

Jeżeli wizualizacja jest przedstawiana jako rozwiązanie możliwe do realizacji, należy uwzględnić właściwe dla danego przypadku obowiązujące wymagania techniczne, budowlane, architektoniczne i bezpieczeństwa.

Nie wolno przedstawiać rozwiązania jako zgodnego z przepisami, jeżeli zgodność nie została zweryfikowana.

Należy rozróżniać:

- wizualizację koncepcyjną,
- projekt aranżacji,
- rozwiązanie zweryfikowane pod względem technicznym.

Wizualizacja AI nie zastępuje dokumentacji projektowej wymagającej odpowiednich uprawnień.

#### G. Realizm wizualizacji

Materiały, meble, oświetlenie i dekoracje mogą być dodawane w celu uzyskania realistycznej wizualizacji, ale nie mogą maskować ani zmieniać rzeczywistej geometrii mieszkania.

Perspektywa kamery nie powinna celowo powodować mylnego wrażenia większej powierzchni pomieszczenia.

Należy unikać:

- nienaturalnie szerokiego kąta widzenia,
- deformacji proporcji,
- zmiany skali mebli,
- ukrywania istotnych elementów architektury,
- przedstawiania wyposażenia o wymiarach nierealnych dla danego pomieszczenia.

#### H. Kontrola jakości przed publikacją

Każda finalna wizualizacja 3D powinna przejść kontrolę:

1. zgodności z rzutem 2D,
2. zgodności wymiarowej,
3. układu drzwi i okien,
4. komunikacji,
5. ergonomii,
6. kolizji wyposażenia,
7. instalacji — jeśli dane są dostępne,
8. zasad architektoniczno-projektowych,
9. realizmu skali wyposażenia,
10. niewprowadzania klienta w błąd.

Wynik kontroli powinien mieć status:

- **PASS** — kryterium spełnione,
- **FAIL** — wykryto błąd,
- **UNKNOWN** — brak wystarczających danych.

Status **UNKNOWN** nie może być automatycznie traktowany jako **PASS**.

---

## Working agreements

### 1. Sposób podejmowania decyzji

Przy istotnych decyzjach należy przedstawiać:

1. problem,
2. dostępne fakty,
3. niewiadome,
4. proponowane rozwiązanie,
5. koszt lub konsekwencje,
6. główne ryzyko.

Nie należy rekomendować bardziej złożonego rozwiązania, jeżeli prostsze wystarcza do zweryfikowania MVP.

### 2. Minimalizacja kosztów

- Preferowane są rozwiązania bezpłatne lub niskokosztowe, jeżeli spełniają wymagania jakościowe.
- Każdy istotny płatny komponent powinien mieć uzasadnienie.
- Koszt infrastruktury i AI powinien być analizowany również w przeliczeniu na pojedynczą pełną analizę mieszkania.

### 3. Szybkość bez utraty kontroli

Termin 14 dni oznacza ograniczanie zakresu, a nie pomijanie weryfikacji danych, legalności lub kontroli geometrii.

Jeżeli wymagania nie mieszczą się w terminie lub budżecie, należy najpierw zaproponować ograniczenie zakresu MVP.

### 4. Wykorzystanie wielu AI

ChatGPT, Gemini i Claude mogą wykonywać różne części projektu.

- Nie należy bez potrzeby zlecać wszystkim trzem AI tego samego.
- Wynik jednego AI nie jest automatycznie dowodem jego poprawności.
- Dla zadań krytycznych można stosować niezależną kontrolę wyniku przez drugi model.
- Ostateczne decyzje projektowe powinny być zapisane w Super Brain, aby uniknąć powstawania sprzecznych wersji projektu.

### 5. Dokumentowanie decyzji

Ważne decyzje, testy i zmiany zakresu powinny trafiać odpowiednio do:

- `decisions/`
- `analyses/`
- `discovery/`
- `prototypes/`
- `log.md`

Nie należy traktować historii rozmowy z AI jako jedynego repozytorium wiedzy projektu.

---

## Vocabulary

- **AI-Estate-OS** — projekt interaktywnej platformy webowej wspierającej klienta przy wyszukiwaniu i ocenie mieszkania.
- **MVP** — pierwsza ograniczona wersja produktu służąca do zweryfikowania najważniejszych założeń projektu.
- **Oferta** — informacje dotyczące konkretnego mieszkania udostępnione przez dewelopera lub inne legalnie wykorzystywane źródło.
- **Rzut 2D** — źródłowy plan mieszkania wykorzystywany jako podstawowe źródło geometrii do procesu 2D → 3D.
- **Render / wizualizacja 3D** — wizualne przedstawienie mieszkania utworzone na podstawie zweryfikowanej geometrii rzutu 2D.
- **Pełna analiza** — proces od identyfikacji właściwej oferty, przez pozyskanie i weryfikację danych oraz rzutu 2D, do uzyskania zaakceptowanego wyniku 3D.
- **Źródło prawdy** — materiał lub dane, których zgodność z konkretnym analizowanym mieszkaniem została zweryfikowana.
- **Halucynacja AI** — informacja wygenerowana przez model, która nie ma wystarczającego potwierdzenia w dostępnych źródłach, lecz mogłaby zostać błędnie przedstawiona jako fakt.
