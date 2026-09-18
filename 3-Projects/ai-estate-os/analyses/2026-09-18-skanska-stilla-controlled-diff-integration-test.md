# AI-Estate-OS — Skanska Stilla controlled diff integration test

**Data:** 2026-09-18  
**Status:** test kontrolowany zakończony

## Wynik

Na kontrolowanej kopii snapshotu zasymulowano:

- zmianę ceny i dostępności jednego lokalu,
- usunięcie jednego lokalu,
- dodanie jednego sztucznego lokalu testowego.

Wynik diff:

- ADDED = 1
- REMOVED = 1
- CHANGED = 1
- UNCHANGED = 4

## Znaczenie

Mechanizm diff poprawnie sklasyfikował wszystkie cztery oczekiwane klasy zmian na poziomie integracyjnym.

## Korekta bezpieczeństwa procesu

Syntetyczny snapshot testowy nie powinien znajdować się w katalogu live `snapshots/skanska_stilla`, ponieważ mógłby zostać omyłkowo potraktowany jako rzeczywisty kolejny stan źródła.

Dlatego:

- generator testowy został zmieniony tak, aby zapisywać dane do `tests/fixtures/skanska_stilla/`,
- dodano `.gitignore` ignorujący katalog `snapshots/`,
- live snapshoty pozostają danymi runtime, nie źródłami testowymi.

## Następny krok

Usunąć lokalny syntetyczny snapshot z katalogu live, pobrać poprawkę z repozytorium i ponownie uruchomić testy. Następnie kolejne live snapshoty można wykonywać bez ryzyka zanieczyszczenia historii testowymi danymi.
