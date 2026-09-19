# AI-Estate-OS — renderer 3D własnego rzutu testowego

Data: 2026-09-19

Dodano interaktywny renderer 3D działający wyłącznie dla własnego syntetycznego rzutu testowego z prawami OWN_TEST_ASSET.

Renderer pobiera deterministyczną scenę 3D JSON, sprawdza status praw i walidację geometrii, a następnie generuje samowystarczalny plik HTML z renderowaniem perspektywicznym na canvasie. Model można obracać myszą, przybliżać rolką oraz przełączać na widok z góry.

Brak zależności od zewnętrznych bibliotek JavaScript i brak użycia materiałów Skanska.

Output lokalny: build/test_floorplan_3d.html

Następny krok: uruchomić testy i renderer lokalnie, a po PASS rozważyć etap 5C: model ścian/otworów jako właściwa geometria architektoniczna zamiast prostych brył pomieszczeń.
