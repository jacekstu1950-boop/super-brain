# AI-Estate-OS — minimal frontend v1

**Data:** 2026-09-18  
**Status:** prototyp dodany do repozytorium

## Co dodano

Do repozytorium aplikacji dodano minimalny frontend:

- `web/index.html`

FastAPI udostępnia go teraz pod:

- `GET /`

Frontend pobiera dane wyłącznie z API:

- `/api/skanska/stilla/latest`
- `/api/skanska/stilla/changes`

Wyświetla:

- dewelopera i projekt,
- liczbę lokali,
- liczbę Verified PASS,
- status praw do 2D,
- tabelę lokali z metrażem, ceną, ceną/m², dostępnością i linkiem źródłowym,
- podsumowanie ostatnich zmian.

## Zakres

To jest prosty frontend walidacyjny MVP, nie docelowy UI produkcyjny.

## Następny test

Po `git pull`:

1. uruchomić pytest,
2. uruchomić Uvicorn,
3. otworzyć `http://127.0.0.1:8000/`,
4. sprawdzić, czy tabela pokazuje 6 aktualnych lokali i Verified PASS = 6.
