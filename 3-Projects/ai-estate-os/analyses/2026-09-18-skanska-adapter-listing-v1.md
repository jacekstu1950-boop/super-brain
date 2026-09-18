# AI-Estate-OS — Skanska adapter: wynik testów i listing discovery v1

**Data:** 2026-09-18  
**Status:** aktywny prototyp

## Co zostało zweryfikowane

Lokalny `SkanskaAdapter v1` został uruchomiony na Pythonie 3.14.7 i przetestowany przez `pytest`.

Wynik lokalny:

- BA0122 — PASS,
- BA0005 — PASS,
- BA0123 — FAIL / UNKNOWN bez wymyślania danych,
- łącznie: 3/3 testy parsera przeszły.

Adapter odczytuje i waliduje m.in.:

- projekt,
- kod mieszkania,
- budynek,
- piętro,
- liczbę pokoi,
- powierzchnię,
- cenę lokalu,
- cenę za m²,
- dostępność,
- źródło i czas pobrania,
- statusy identity/evidence,
- osobny `floorplan_rights_status`.

## Najważniejszy wniosek

Stary scraper klasyfikował dowolne fragmenty strony zawierające `m²` jako mieszkania. Nowy adapter zaczyna od jednoznacznego kodu lokalu i nie tworzy danych, gdy kodu nie potwierdzi źródło.

Przypadek BA0123 potwierdził pożądane zachowanie antyhalucynacyjne: brak identyfikatora na stronie skutkuje `identity_status = FAIL`, a pola pozostają puste.

## Listing discovery v1

Do repozytorium aplikacji dodano:

- `adapters/skanska_stilla_listing.py`
- `tests/test_skanska_stilla_listing.py`

Listing adapter:

1. otwiera oficjalną stronę Stilla przez Playwright,
2. zbiera wyłącznie linki pasujące do stron konkretnych lokali,
3. wydobywa kody w formacie np. `BA0122`,
4. deduplikuje rekordy,
5. nie uznaje zwykłego tekstu ani zakresu powierzchni za mieszkanie,
6. opcjonalnie przekazuje wykryte kody do istniejącego `SkanskaAdapter` w celu weryfikacji PASS / FAIL / UNKNOWN,
7. nie pobiera rzutów 2D.

## Testy listingu

Dodano testy jednostkowe sprawdzające:

- wybieranie tylko linków Stilla,
- deduplikację kodów,
- normalizację małych/dużych liter,
- odrzucanie zwykłego tekstu typu „26–76 m²” oraz kodu bez linku.

## Ograniczenie prawne

`floorplan_rights_status` pozostaje `UNKNOWN`. Listing discovery nie pobiera ani nie transformuje rzutów 2D. Prawa do materiałów są osobnym gate'em i nie mogą zostać podniesione do PASS przez sam fakt technicznej dostępności pliku.

## Następny test

Po pobraniu najnowszych zmian do lokalnego repozytorium należy uruchomić:

`python -m pytest -v`

Następnie:

`python -m adapters.skanska_stilla_listing --show-browser`

Jeżeli discovery wykryje rzeczywiste kody lokali, kolejnym krokiem jest ograniczona weryfikacja kilku rekordów przez:

`python -m adapters.skanska_stilla_listing --verify --limit 3`

Dopiero po tym należy zdecydować, czy listing adapter może stać się źródłem dla pionowego flow MVP.
