# AI-Estate-OS — Skanska Stilla live discovery v1

**Data:** 2026-09-18  
**Status:** test live zakończony

## Wynik

Uruchomiono lokalnie:

`python -m adapters.skanska_stilla_listing --show-browser`

Listing discovery wykrył 6 kodów lokali Stilla:

- AC0340
- BA0003
- BA0005
- BA0351
- BA0577
- BA0688

Każdy rekord otrzymał `listing_status = DISCOVERED`.

## Znaczenie wyniku

Discovery działa na aktualnej stronie Stilla i nie zwrócił sztucznych rekordów typu „Mieszkanie_1” ani zakresów powierzchni traktowanych jako lokale.

Status `DISCOVERED` nie oznacza jeszcze pełnego PASS. Każdy kod musi zostać osobno zweryfikowany przez `SkanskaAdapter`, który sprawdza spójność identyfikatora i podstawowych danych mieszkania.

## Następny krok

Uruchomić ograniczoną weryfikację trzech pierwszych odkrytych lokali:

`python -m adapters.skanska_stilla_listing --verify --limit 3`

Oczekiwany rezultat to raport PASS / FAIL / UNKNOWN oraz plik `skanska_stilla_verified.json`.

Dopiero po tym teście należy zdecydować, czy uruchamiać weryfikację całej listy 6 lokali.
