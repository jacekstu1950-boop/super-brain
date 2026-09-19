# AI-Estate-OS — karta szczegółów mieszkania v1

Data: 2026-09-19

Dodano pierwszy widok pojedynczego mieszkania.

Nowa ścieżka: /mieszkanie/{kod_lokalu}

Nowy endpoint: GET /api/skanska/stilla/apartments/{apartment_code}

Karta pokazuje kod lokalu, dewelopera, projekt, cenę, powierzchnię, cenę za m2, liczbę pokoi, piętro, budynek, dostępność, status weryfikacji, status praw do rzutu 2D, datę aktualizacji i źródło.

Kody lokali w tabeli wyników prowadzą do kart szczegółów.

Dane pochodzą wyłącznie z verified snapshotu; brakujące wartości nie są zgadywane. Status praw do rzutu 2D pozostaje Nieustalone.
