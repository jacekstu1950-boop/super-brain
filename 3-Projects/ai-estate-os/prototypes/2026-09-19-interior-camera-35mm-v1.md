# AI-Estate-OS — Etap 5D: kamera wnętrza 35 mm v1

Data: 2026-09-19

Etap wykonany wyłącznie na własnym syntetycznym rzucie testowym OWN_TEST_ASSET.

Dodano preset kamery interior_living z wysokością oka 1,65 m i ogniskową 35 mm. Preset jest jawnie oznaczony jako TEST_PRESET, czyli jest ustawieniem demonstracyjnym, a nie faktem wynikającym z rzutu 2D.

Dodano osobny renderer perspektywiczny wnętrza. Renderer korzysta z istniejącej zweryfikowanej geometrii ścian, podłóg i otworów, generuje samowystarczalny HTML, pozwala rozglądać się myszą i regulować pole widzenia rolką.

Output lokalny: build/test_floorplan_interior_35mm.html

Zachowana zasada: 2D jest źródłem prawdy dla geometrii; kamera jest oddzielnym parametrem wizualizacyjnym. Materiały Skanska nie są używane.

Następny krok: lokalny pytest, uruchomienie geometry.test_floorplan_interior_renderer i wizualna kontrola perspektywy wnętrza.
