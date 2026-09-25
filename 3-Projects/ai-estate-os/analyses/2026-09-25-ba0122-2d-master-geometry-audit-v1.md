# BA0122 — audyt 2D → Master Geometry

Data audytu: 2026-09-25

## Zakres
Audyt porównuje:
1. aktualne dane publiczne Skanska dla lokalu BA0122,
2. istniejący w bibliotece materiał „Prezentacja projektu mieszkania 2D i 3D.png”,
3. spójność metryczną i topologiczną obecnego modelu 2D/3D.

## Fakty zweryfikowane z oficjalnej strony Skanska
- Lokal: BA0122
- Inwestycja: Stilla
- Budynek: B
- Piętro: 1
- Liczba pokoi: 2
- Powierzchnia lokalu: 47,49 m²
- Balkon: 8,50 m²

## Dane z istniejącego materiału 2D/3D — wymagają ponownej weryfikacji
Materiał biblioteczny podaje:
- Przedpokój 4,80 m²
- Łazienka 4,34 m²
- Aneks garderobiany 3,49 m²
- Pokój dzienny z aneksem kuchennym 23,04 m²
- Pokój 11,82 m²
- Suma 47,49 m²
- Balkon 9,33 m²
- szerokość bryły 577 cm
- długość bryły 700 cm
- głębokość balkonu 160 cm

Suma powierzchni pomieszczeń zgadza się arytmetycznie z oficjalnymi 47,49 m², ale nie dowodzi zgodności z oryginalnym rzutem.

## Krytyczne niespójności
1. Balkon: 9,33 m² w materiale pochodnym vs 8,50 m² oficjalnie — FAIL.
2. Obrys 5,77 m × 7,00 m daje tylko 40,39 m² powierzchni prostokąta, więc nie może zawierać 47,49 m² powierzchni użytkowej. Oznaczenia 577/700 cm są niespójne z oficjalną powierzchnią — FAIL.
3. Z tego wynika, że obecna plansza 2D nie może być traktowana jako metryczne źródło prawdy.
4. Umeblowanie i wystrój w obecnych wizualizacjach są warstwą stagingową; nie są zweryfikowaną geometrią źródłową.

## Topologia, którą można zachować roboczo
Na obecnej planszy układ relacji jest następujący:
- wejście od górnej krawędzi do przedpokoju,
- aneks garderobiany po lewej stronie wejścia,
- łazienka po prawej stronie wejścia,
- salon z aneksem kuchennym w lewej/dolnej części mieszkania,
- sypialnia w prawej/dolnej części,
- balkon wzdłuż dolnej elewacji,
- wyjście na balkon z salonu i z sypialni.

Ta topologia może być użyta tylko jako robocza hipoteza do czasu odczytu oryginalnego rzutu BA0122.

## Umeblowanie widoczne na obecnej planszy — tylko referencja stagingowa
- kuchnia liniowa przy górnej/lewej ścianie salonu,
- stół jadalniany w pobliżu kuchni,
- sofa ustawiona przy ścianie rozdzielającej salon i sypialnię,
- TV przy lewej ścianie salonu,
- fotel i stolik kawowy w strefie dziennej,
- łóżko w sypialni z osią wzdłuż dłuższego wymiaru pokoju,
- zabudowa szafowa przy górnej ścianie sypialni,
- wanna/prysznic, WC i umywalka w łazience.

Żadne z tych ustawień nie powinno być blokowane jako FACT bez porównania z oryginalnym SVG/PDF.

## Status Master Geometry
- identity: PASS
- total_area: PASS
- room_count: PASS
- balcony_area: FAIL w materiale pochodnym
- room_areas: UNVERIFIED
- outer_dimensions: FAIL
- wall geometry: UNVERIFIED
- door positions: UNVERIFIED
- window positions: UNVERIFIED
- furniture positions: UNVERIFIED
- metric_master_geometry: BLOCKED

## Decyzja
Nie należy generować kolejnych „wiernych” wizualizacji BA0122 z obecnej planszy pochodnej. Następny wymagany krok to pozyskanie i odczyt oryginalnego rzutu 2D BA0122 (SVG/PDF), a następnie utworzenie Master Geometry v1.0 z tabelą ścian, otworów, pomieszczeń i punktów kontrolnych.

Do czasu tego kroku Image Generation może być używane tylko do wariantów stylistycznych, nie do deklarowania zgodności architektonicznej.
