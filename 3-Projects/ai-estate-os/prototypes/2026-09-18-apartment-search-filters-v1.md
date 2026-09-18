# AI-Estate-OS — apartment search and filters v1

**Data:** 2026-09-18  
**Status:** prototyp dodany do repozytorium

## Co dodano

Pierwszy rzeczywisty interfejs wyszukiwania i filtrowania mieszkań w `web/index.html`.

Dostępne kryteria:

- kod lokalu,
- liczba pokoi,
- piętro,
- dostępność,
- metraż od/do,
- cena od/do,
- sortowanie po kodzie, cenie, metrażu i cenie/m²,
- przycisk czyszczenia filtrów.

Interfejs pokazuje liczbę wyników w formacie `Znaleziono: X z Y` oraz komunikat, gdy żaden lokal nie spełnia kryteriów.

## Architektura

Filtrowanie działa po stronie przeglądarki na aktualnym verified snapshotcie pobranym z API. Jest to właściwe dla obecnej skali sześciu rekordów i nie wymaga rozszerzania API.

## Testy

Dodano `tests/test_frontend_filters.py`, które sprawdzają obecność kontrolek i logiki filtrowania w aktualnym froncie.

## Następny test lokalny

1. `git pull`
2. `python -m pytest -v`
3. restart Uvicorn
4. otworzyć `http://127.0.0.1:8000/`
5. sprawdzić wyszukiwanie BA0005, filtr ceny i reset filtrów.
