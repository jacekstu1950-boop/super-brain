# AI-Estate-OS — korekta Etapu 5E: proporcje, okno i staging

Data: 2026-09-19

Na podstawie kontroli wizualnej użytkownika skorygowano trzy problemy: zbyt duże wizualne powiększenie wnętrza, zbyt duże okno testowe oraz brak czytelnych mebli i kolorystyki w rendererze.

Zmiany:
- okno testowe zmniejszono z 200 x 120 cm do 160 x 120 cm przy parapecie 90 cm,
- kamera 35 mm została cofnięta i skierowana szerzej przez zmianę pozycji/targetu bez zmiany geometrii 2D,
- viewport renderera zmniejszono, aby zachować bardziej zbliżony odbiór skali do wcześniejszej wizualizacji,
- poprawiono resolver materiałów, aby staging korzystał z przypisanych kolorów,
- dodano wyraźniejsze elementy stagingu: oliwkowa sofa, terakotowy fotel, piaskowy dywan i stolik z jasnego dębu.

Geometria mieszkania pozostaje źródłem prawdy. Korekty dotyczą wyłącznie własnego testowego assetu i warstwy wizualizacyjnej.
