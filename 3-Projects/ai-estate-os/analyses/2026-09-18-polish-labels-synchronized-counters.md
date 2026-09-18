# AI-Estate-OS — Polish labels and synchronized result counters

**Data:** 2026-09-18  
**Status:** poprawka interfejsu dodana

## Co zmieniono

Frontend został ujednolicony językowo i licznikowo.

### Liczniki

Górny panel pokazuje teraz osobno:

- Wyświetlane lokale — liczba aktualnie widocznych wyników po filtrach,
- Łącznie w ofercie — pełna liczba lokali w verified snapshotcie,
- Zweryfikowane poprawnie — liczba aktualnie wyświetlanych lokali z PASS/PASS.

Dzięki temu po filtrze Cena do = 605000 PLN oczekiwane wartości to:

- Wyświetlane lokale = 3
- Łącznie w ofercie = 6
- Zweryfikowane poprawnie = 3

### Tłumaczenia

Widoczne wartości zostały przetłumaczone:

- available -> Tak
- unavailable -> Nie
- UNKNOWN -> Nieustalone

Sekcja zmian:

- ADDED -> DODANE
- REMOVED -> USUNIĘTE
- CHANGED -> ZMIENIONE
- UNCHANGED -> BEZ ZMIAN

## Następny test

Po git pull i restarcie serwera należy sprawdzić filtr Cena do = 605000 PLN oraz potwierdzić:

- Wyświetlane lokale = 3
- Łącznie w ofercie = 6
- Zweryfikowane poprawnie = 3
- wszystkie wartości dostępności są pokazane po polsku.
