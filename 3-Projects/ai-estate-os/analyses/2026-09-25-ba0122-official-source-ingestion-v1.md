# AI-Estate-OS — BA0122 official source ingestion v1

Data: 2026-09-25

Po audycie wykryto niespójności w planszy pochodnej BA0122. Zamiast używać wygenerowanych wymiarów, przygotowano pipeline do pobrania oficjalnego BA0122.svg ze strony Skanska na lokalnym komputerze użytkownika.

Repo AI-Estate-OS otrzymało:
- `geometry/master/BA0122.master.json` — manifest Master Geometry z wyłącznie oficjalnie zweryfikowanymi faktami wejściowymi (47,49 m², balkon 8,50 m², B, 1 piętro, 2 pokoje),
- `geometry/ba0122_source_audit.py` — pobranie oficjalnego SVG, SHA256, inspekcja viewBox/prymitywów/tekstów oraz aktualizacja manifestu,
- `tests/test_ba0122_source_audit.py`,
- aktualizację compliance do `USER_CONFIRMED_PERMISSION` na podstawie jawnego oświadczenia użytkownika o zgodzie przedstawiciela Skanska; dokument zgody nie jest jeszcze zarchiwizowany, więc publiczna republish pozostaje wyłączona.

Następny krok po lokalnym uruchomieniu audytu: odczytać raport `build/BA0122_source_inspection.json` i napisać parser ścian/otworów pod realną strukturę SVG, bez inferowania brakujących wymiarów.
