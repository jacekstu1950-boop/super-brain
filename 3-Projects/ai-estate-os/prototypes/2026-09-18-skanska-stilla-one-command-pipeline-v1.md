# AI-Estate-OS — Skanska Stilla one-command pipeline v1

**Data:** 2026-09-18  
**Status:** prototyp dodany do repozytorium

## Co dodano

Do repozytorium aplikacji dodano:

- `adapters/skanska_stilla_pipeline.py`
- `tests/test_skanska_stilla_pipeline.py`

Pipeline łączy w jednym uruchomieniu:

1. discovery aktualnych lokali Stilla,
2. walidację każdego lokalu przez SkanskaAdapter,
3. blokadę zapisu snapshotu, jeśli wystąpi FAIL lub UNKNOWN,
4. zapis nowego snapshotu,
5. porównanie dwóch najnowszych snapshotów,
6. zapis raportu diff.

## Reguła bezpieczeństwa

Pipeline zapisuje snapshot tylko wtedy, gdy wszystkie wykryte lokale mają:

- `identity_status = PASS`
- `evidence_status = PASS`

Jeżeli choć jeden lokal ma FAIL lub UNKNOWN, wynik ma status `BLOCKED` i nowy snapshot nie jest zapisywany.

## Uruchomienie

Standardowo:

`python -m adapters.skanska_stilla_pipeline`

Z widoczną przeglądarką:

`python -m adapters.skanska_stilla_pipeline --show-browser`

Pełny wynik JSON:

`python -m adapters.skanska_stilla_pipeline --json`

## Oczekiwany następny test

Po `git pull` należy uruchomić pełny `pytest`, a następnie jeden live run pipeline. Przy stabilnym źródle oczekiwany wynik to PASS dla wszystkich lokali i diff bez zmian.
