# AI-Estate-OS — minimal API for verified Stilla data v1

**Data:** 2026-09-18  
**Status:** prototyp dodany do repozytorium

## Co dodano

Do repozytorium aplikacji dodano minimalną warstwę FastAPI:

- `api/app.py`
- `tests/test_api.py`
- `requirements.txt`
- `requirements-dev.txt`

Zaktualizowano także `README.md` o instrukcje uruchomienia.

## Endpointy

- `GET /health`
- `GET /api/skanska/stilla/latest`
- `GET /api/skanska/stilla/changes`

API czyta wyłącznie lokalne dane runtime zapisane przez istniejący pipeline:

- `snapshots/skanska_stilla/latest.json`
- `snapshots/skanska_stilla/changes_latest.json`

## Gate jakości

API nie uruchamia bezpośrednio scrapera. Udostępnia już zapisany verified snapshot.

Jeżeli plik runtime nie istnieje, endpoint zwraca błąd 503 zamiast wymyślać dane.

`floorplan_rights_status` pozostaje `UNKNOWN`; warstwa API nie zmienia statusu praw do rzutu 2D.

## Następny test

Po `git pull`:

1. zainstalować dependencies,
2. uruchomić pytest,
3. uruchomić uvicorn,
4. sprawdzić /health,
5. sprawdzić /api/skanska/stilla/latest,
6. sprawdzić /api/skanska/stilla/changes,
7. sprawdzić /docs.
