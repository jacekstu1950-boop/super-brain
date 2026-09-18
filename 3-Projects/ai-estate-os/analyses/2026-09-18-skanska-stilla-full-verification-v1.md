# AI-Estate-OS — Skanska Stilla full verification v1

**Data:** 2026-09-18  
**Status:** pełna weryfikacja aktualnego snapshotu zakończona

## Wynik

Uruchomiono pełną weryfikację wszystkich 6 lokali wykrytych przez listing discovery Stilla.

Wynik zbiorczy:

- PASS = 6
- FAIL = 0
- UNKNOWN = 0

## Znaczenie

Aktualny flow:

`Stilla listing discovery -> kod lokalu -> SkanskaAdapter -> PASS / FAIL / UNKNOWN`

zadziałał poprawnie dla wszystkich 6 lokali obecnych w bieżącym snapshotcie źródła.

To oznacza, że dla aktualnego stanu strony Stilla:

- discovery wykrywa konkretne kody lokali zamiast ogólnych fragmentów strony,
- każdy wykryty lokal przechodzi walidację tożsamości i podstawowych danych,
- nie wystąpiły przypadki FAIL ani UNKNOWN,
- adapter nie musiał wymyślać brakujących danych.

## Zakres wniosku

Wynik potwierdza stabilność bieżącego snapshotu Stilla, ale nie gwarantuje odporności na przyszłe zmiany HTML, struktury strony lub danych.

Dlatego następnym etapem powinien być zapis pełnego snapshotu ofertowego oraz porównywanie kolejnych uruchomień.

## Następny krok

Dodać mechanizm snapshotów, który zapisze dla każdego uruchomienia:

- timestamp,
- listę wykrytych kodów,
- znormalizowane dane mieszkań,
- status PASS / FAIL / UNKNOWN,
- źródło,
- różnice względem poprzedniego snapshotu.

Minimalne wykrywane zmiany:

- lokal dodany,
- lokal usunięty,
- zmiana ceny,
- zmiana ceny za m²,
- zmiana dostępności,
- zmiana powierzchni lub innych pól identyfikacyjnych.

Rzuty 2D pozostają poza tym etapem, a `floorplan_rights_status` nadal wymaga osobnej decyzji prawnej.
