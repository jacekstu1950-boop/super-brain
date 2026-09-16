# AI-Estate-OS — Brief

> Dokument definiuje zakres projektu AI-Estate-OS.
> Zmiany w briefie wymagają akceptacji właściciela projektu.

---

## In one sentence

AI-Estate-OS to interaktywna platforma webowa dla osób szukających
mieszkania, która na podstawie kilku danych identyfikujących ofertę
odnajduje informacje o lokalu, pozyskuje rzut 2D i wykorzystuje go
do stworzenia wizualizacji 3D wspierającej decyzję zakupową.

## Context

Kupujący mieszkanie potrzebuje szybkiego dostępu do informacji
istotnych dla jego decyzji zakupowej, bez konieczności przeglądania
dużej liczby ofert i danych, które nie odpowiadają jego kryteriom.

AI-Estate-OS ma skrócić drogę od określenia potrzeb klienta
do uzyskania informacji o konkretnym mieszkaniu, jego rzutu 2D
oraz wizualizacji 3D.

Platforma ma działać jako interaktywna, wielotematyczna wyszukiwarka.

Użytkownik powinien móc identyfikować poszukiwane mieszkanie
na podstawie niewielkiej liczby danych wejściowych, takich jak:

- miasto,
- dzielnica,
- ulica,
- deweloper,
- numer lub kod identyfikacyjny mieszkania stosowany
  na stronie internetowej dewelopera.

System powinien na tej podstawie odnaleźć właściwą ofertę
i dostępne informacje dotyczące mieszkania.

Jednym z kluczowych elementów usługi ma być odnalezienie
lub pozyskanie rzutu 2D mieszkania, a następnie wykorzystanie
go jako źródła geometrii do przygotowania wizualizacji 3D.

Docelowo korzystanie z platformy ma być usługą płatną.

Rozważane są dwa lub trzy poziomy cenowe różniące się zakresem
oraz ilością informacji udostępnianych użytkownikowi.

Dokładny model cenowy nie jest jeszcze ustalony.

## Who it is for

Pierwszym klientem AI-Estate-OS jest:

**osoba prywatna kupująca nowe mieszkanie od dewelopera
w Warszawie.**

MVP nie jest obecnie projektowane dla:

- rynku wtórnego,
- klientów instytucjonalnych,
- pośredników jako głównej grupy klientów,
- całego rynku mieszkaniowego w Polsce.

Rozszerzenie zakresu może nastąpić po zweryfikowaniu MVP.

## What done looks like

MVP uznajemy za skuteczne, jeżeli działa pełny proces:

**wyszukanie oferty → poprawne pozyskanie rzutu 2D →
poprawne wygenerowanie wizualizacji 3D →
wykorzystanie wyniku przez klienta.**

W ciągu 3 miesięcy od uruchomienia platforma powinna osiągnąć:

- 500–1000 wejść miesięcznie,
- co najmniej 50 pełnych analiz mieszkań zakończonych
  wygenerowaniem wizualizacji 3D.

Przed testami produkcyjnymi należy zdefiniować mierzalne kryteria
określające, co oznacza:

- poprawne znalezienie mieszkania,
- poprawne pozyskanie rzutu 2D,
- poprawne odwzorowanie rzutu 2D,
- poprawna wizualizacja 3D,
- pełna analiza mieszkania.

Dzięki temu jakość systemu będzie oceniana według jawnych
kryteriów, a nie deklaracji AI.

## Constraints

### Budżet

Maksymalny budżet na uruchomienie MVP:

**500 PLN.**

Koszty początkowe powinny być minimalizowane.

Rozwiązania infrastrukturalne i AI powinny być dobierane
z uwzględnieniem kosztu pojedynczej analizy.

### Termin

Maksymalny czas przygotowania działającego MVP:

**14 dni.**

Preferowane jest skrócenie tego terminu poprzez zwiększenie
intensywności pracy, bez zwiększania budżetu ponad 500 PLN.

### Rynek

Pierwszy rynek:

**Warszawa — nowe mieszkania oferowane przez deweloperów.**

### Deweloperzy / projekty MVP

MVP może jednocześnie obsługiwać maksymalnie czterech
deweloperów lub wskazane projekty deweloperskie.

Początkowa lista:

1. Archicom — Modern Mokotów
2. Asbud — Towarowa Square / Tower
3. Skanska
4. Dom — dokładna identyfikacja dewelopera/projektu
   pozostaje do potwierdzenia.

Lista jest wymienna.

Dodanie nowego dewelopera do zakresu MVP wymaga wcześniejszego
usunięcia jednego z czterech aktualnie obsługiwanych.

Limit czterech pozostaje bez zmian do czasu świadomej decyzji
o rozszerzeniu zakresu projektu.

### Legalność pozyskiwania danych

Pozyskiwanie danych, informacji o ofertach oraz rzutów 2D może
odbywać się wyłącznie metodami zgodnymi z obowiązującym prawem
oraz dozwolonymi warunkami korzystania ze źródeł danych.

Nie należy zakładać, że każda informacja lub grafika dostępna
publicznie na stronie internetowej dewelopera może być
automatycznie pobierana, kopiowana, przetwarzana lub ponownie
udostępniana.

Dla wykorzystywanych źródeł należy odpowiednio zweryfikować
warunki dostępu oraz możliwość wykorzystania danych i materiałów.

### Zakres MVP

Ze względu na budżet 500 PLN i termin maksymalnie 14 dni
pierwsza wersja nie powinna próbować obsługiwać wszystkich
deweloperów, wszystkich formatów danych ani wszystkich
możliwych przypadków ofert mieszkaniowych.

Priorytetem jest działający i możliwy do zweryfikowania
proces dla ograniczonego zakresu.

## Open questions

### 1. Pozyskiwanie danych

Jak technicznie i zgodnie z prawem pozyskiwać dane dla każdego
z czterech wybranych deweloperów/projektów?

Do sprawdzenia m.in.:

- publiczne strony WWW,
- dostępne API,
- pliki SVG/PDF/JPG/PNG,
- dane strukturalne strony,
- inne legalnie dostępne źródła.

### 2. Identyfikacja mieszkania

Jaki minimalny zestaw danych wejściowych wystarczy do
jednoznacznego znalezienia konkretnego mieszkania?

Należy przetestować kombinacje takich danych jak:

- miasto,
- dzielnica,
- ulica,
- deweloper,
- inwestycja,
- budynek,
- numer/kod mieszkania.

### 3. Rzut 2D

Jakie formaty rzutów będą obsługiwane w MVP?

Należy ustalić priorytet m.in. dla:

- SVG,
- PDF,
- JPG,
- PNG.

### 4. 2D → 3D

Jak dokładnie przekształcać rzut 2D w model/wizualizację 3D?

Należy zdefiniować:

- źródło prawdy dla geometrii,
- sposób rozpoznawania ścian,
- drzwi,
- okien,
- pomieszczeń,
- wymiarów,
- skalowania,
- sposób postępowania z brakującymi danymi.

System nie powinien wymyślać brakujących elementów geometrii
bez ich wyraźnego oznaczenia jako założenia.

### 5. Kryteria jakości 3D

Należy opracować mierzalny standard zgodności wizualizacji 3D
z wejściowym rzutem 2D.

Celem jest ograniczenie halucynacji i zmian geometrii
nieuzasadnionych materiałem źródłowym.

### 6. Architektura technologiczna

Nie wybrano jeszcze ostatecznego stosu technologicznego MVP.

Należy określić:

- frontend,
- backend,
- bazę danych,
- hosting,
- mechanizm wyszukiwania,
- sposób pobierania danych,
- pipeline 2D → 3D,
- wykorzystanie modeli AI.

Decyzje technologiczne muszą uwzględniać limit budżetu 500 PLN
oraz możliwość przygotowania MVP maksymalnie w 14 dni.

### 7. Podział pracy pomiędzy AI

Należy ustalić optymalny podział zadań pomiędzy:

- ChatGPT Plus,
- Gemini Pro,
- Claude w dostępnej wersji bezpłatnej.

Należy ograniczyć dublowanie pracy i przypisać poszczególnym
systemom zadania, w których dają największą wartość.

### 8. Model płatności

Do ustalenia pozostają:

- liczba pakietów — 2 lub 3,
- ceny,
- zakres informacji w każdym pakiecie,
- limity analiz,
- koszt wygenerowania 3D,
- sposób realizacji płatności.

### 9. Ekonomika usługi

Przed uruchomieniem płatnej wersji należy określić:

- koszt pojedynczego wyszukania,
- koszt pobrania i przetworzenia danych,
- koszt analizy AI,
- koszt wygenerowania 3D,
- koszt infrastruktury,
- minimalną cenę pozwalającą utrzymać usługę.

### 10. Zgodność prawna

Należy zweryfikować wymagania prawne dotyczące m.in.:

- korzystania z danych dostępnych na stronach deweloperów,
- praw do rzutów mieszkań i innych materiałów,
- automatycznego pobierania danych,
- ponownego prezentowania informacji,
- ochrony danych osobowych,
- regulaminu platformy,
- płatnej usługi internetowej.

---

## Folders

- `discovery/` — badania, dane, źródła, analiza deweloperów,
  testy pozyskiwania ofert
- `decisions/` — decyzje architektoniczne, produktowe,
  prawne i biznesowe
- `prototypes/` — prototypy wyszukiwarki, pipeline 2D → 3D,
  interfejs użytkownika
- `analyses/` — wyniki testów, pomiary jakości,
  koszty i wnioski
