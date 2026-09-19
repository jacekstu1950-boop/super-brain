# AI-Estate-OS — własny testowy pipeline 2D → geometria → 3D

Data: 2026-09-19

Zakres ograniczono wyłącznie do syntetycznego, własnego rzutu testowego. Materiały Skanska nie są używane.

Dodano własny SVG testowego mieszkania, parser geometrii oparty na standardowej bibliotece XML, walidację geometrii oraz deterministyczny model sceny 3D w JSON.

Pipeline zachowuje pozycję i wymiary pomieszczeń z 2D, przelicza centymetry na metry, przenosi wysokość ścian oraz rejestruje otwory drzwiowe i okienne. Każdy model testowy ma status praw OWN_TEST_ASSET.

Wyniki generowane są lokalnie do katalogu build i nie są commitowane.

Następny krok: uruchomić pytest oraz geometry.test_floorplan_pipeline lokalnie i potwierdzić PASS przed dodaniem renderera 3D.
