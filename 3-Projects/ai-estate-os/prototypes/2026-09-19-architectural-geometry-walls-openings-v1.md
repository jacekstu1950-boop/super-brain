# AI-Estate-OS — architektoniczna geometria ścian i otworów v1

Data: 2026-09-19

Etap 5C rozwinięto wyłącznie na własnym syntetycznym rzucie testowym OWN_TEST_ASSET.

Dodano jawne ściany źródłowe z grubością oraz powiązanie otworów drzwiowych i okiennych z konkretną ścianą. Pipeline buduje rzeczywiste segmenty ścian jako bryły 3D i wycina otwory deterministycznie.

Drzwi tworzą pełny otwór od posadzki do wysokości 210 cm z nadprożem do wysokości ściany 270 cm. Okno ma parapet 90 cm, wysokość 120 cm i nadproże od 210 do 270 cm.

Pomieszczenia są reprezentowane jako cienkie płyty podłogowe do orientacji i etykiet, a ściany jako osobne wall_segment. Renderer rozróżnia ściany od podłóg.

Nie użyto materiałów Skanska. Następny krok: lokalny pytest oraz ponowne wygenerowanie sceny i HTML, a następnie wizualna kontrola drzwi i okna.
