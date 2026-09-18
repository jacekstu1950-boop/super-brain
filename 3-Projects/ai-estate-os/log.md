# AI-Estate-OS — Log

Append-only. Newest entry at the top. The AI writes this - see `3-Projects/README.md`.

Types: `decision`, `prototype`, `analysis`, `research`, `scope-change`, `shipped`.

---

## 2026-09-18 - FastAPI: lokalny runtime potwierdzony

**Type:** analysis
**What changed:** Uvicorn został poprawnie uruchomiony jako proces tła, port 8000 nasłuchuje, a endpoint /health zwrócił HTTP 200 z wersją API 0.1.0.
**Why:** Potwierdza to, że problem nie leżał w FastAPI ani porcie, lecz w sposobie utrzymania procesu serwera w poprzednim oknie CMD.
**Next:** Zweryfikować endpointy latest, changes i Swagger /docs.
**Files:** `analyses/2026-09-18-fastapi-runtime-validation-v1.md`

---

## 2026-09-18 - Skanska Stilla: dodano minimal API v1

**Type:** prototype
**What changed:** Dodano FastAPI z endpointami health, latest verified snapshot i latest changes, wraz z testami kontraktu oraz plikami dependencies.
**Why:** Frontend nie powinien uruchamiać Playwrighta bezpośrednio; potrzebna jest stabilna warstwa aplikacyjna udostępniająca już zweryfikowane dane runtime.
**Next:** Pobrać zmiany lokalnie, zainstalować dependencies, uruchomić testy i sprawdzić API przez uvicorn.
**Files:** `prototypes/2026-09-18-skanska-stilla-api-v1.md`

---

## 2026-09-18 - Skanska Stilla: one-command pipeline przeszedł live validation

**Type:** analysis
**What changed:** Pełny live run one-command pipeline zakończył się statusem OK, wykrył 6 lokali, zweryfikował PASS=6 / FAIL=0 / UNKNOWN=0, zapisał snapshot i raport diff z UNCHANGED=6.
**Why:** Wynik potwierdza, że discovery, walidacja, snapshot i diff działają razem end-to-end bez ręcznego uruchamiania osobnych etapów i bez pomijania gate jakości.
**Next:** Dodać prostą warstwę aplikacyjną/API do udostępniania verified snapshotu i raportu zmian frontendowi.
**Files:** `analyses/2026-09-18-skanska-stilla-one-command-live-validation.md`

---

## 2026-09-18 - Skanska Stilla: dodano one-command pipeline

**Type:** prototype
**What changed:** Dodano jedno polecenie łączące discovery, walidację, snapshot i diff dla Stilla; pipeline blokuje zapis snapshotu, jeśli jakikolwiek lokal ma FAIL lub UNKNOWN.
**Why:** Ręczne uruchamianie czterech osobnych kroków zwiększa ryzyko pomyłki i niespójnego stanu; jeden kontrolowany pipeline upraszcza MVP i zachowuje gate jakości.
**Next:** Pobrać zmiany lokalnie, uruchomić pełny pytest i pierwszy live run one-command pipeline.
**Files:** `prototypes/2026-09-18-skanska-stilla-one-command-pipeline-v1.md`

---

## 2026-09-18 - Skanska Stilla: kontrolowany diff wykrył wszystkie zmiany

**Type:** analysis
**What changed:** Kontrolowany test integracyjny zwrócił ADDED=1, REMOVED=1, CHANGED=1, UNCHANGED=4; dodatkowo odseparowano syntetyczne snapshoty testowe od katalogu live i dodano ignorowanie generated snapshots w Git.
**Why:** Test potwierdza poprawność klasyfikacji zmian, a separacja danych testowych zapobiega zanieczyszczeniu historii live fałszywymi stanami ofert.
**Next:** Usunąć lokalny syntetyczny snapshot z katalogu live, pobrać poprawkę i ponownie uruchomić testy.
**Files:** `analyses/2026-09-18-skanska-stilla-controlled-diff-integration-test.md`

---

## 2026-09-18 - Skanska Stilla: snapshot diff potwierdzony

**Type:** analysis
**What changed:** Po dodaniu modułu diff przeszło 12/12 testów, a porównanie dwóch kolejnych live snapshotów Stilla zwróciło ADDED=0, REMOVED=0, CHANGED=0, UNCHANGED=6.
**Why:** Wynik potwierdza, że pipeline potrafi zapisać i porównać dwa rzeczywiste stany ofert bez fałszywego raportowania zmian.
**Next:** Wykonać kontrolowany test integracyjny zmian na kopii snapshotu, aby potwierdzić działanie raportowania zmiany ceny, dostępności, dodania i usunięcia lokalu.
**Files:** `analyses/2026-09-18-skanska-stilla-snapshot-diff-validation-v1.md`

---

## 2026-09-18 - Skanska Stilla: zapisano pierwszy snapshot ofert

**Type:** prototype
**What changed:** Lokalnie przeszło 10/10 testów, zapisano pierwszy pełny snapshot Stilla oraz dodano moduł porównujący dwa najnowsze snapshoty i klasyfikujący zmiany jako ADDED / REMOVED / CHANGED / UNCHANGED.
**Why:** MVP potrzebuje nie tylko jednorazowego odczytu ofert, lecz także kontrolowanego wykrywania zmian ceny, dostępności i składu listy między kolejnymi uruchomieniami.
**Next:** Pobrać moduł diff lokalnie, wykonać drugi snapshot i uruchomić porównanie dwóch kolejnych stanów.
**Files:** `analyses/2026-09-18-skanska-stilla-snapshot-baseline-v1.md`

---

## 2026-09-18 - Skanska Stilla: 6/6 lokali przeszło pełną weryfikację

**Type:** analysis
**What changed:** Pełna weryfikacja wszystkich 6 lokali wykrytych na stronie Stilla zakończyła się wynikiem PASS=6, FAIL=0, UNKNOWN=0.
**Why:** Wynik potwierdza, że bieżący flow listing discovery -> kod lokalu -> SkanskaAdapter działa poprawnie dla całego aktualnego snapshotu Stilla, bez tworzenia sztucznych rekordów i bez zgadywania brakujących danych.
**Next:** Dodać snapshot danych ofertowych oraz mechanizm porównywania zmian między kolejnymi uruchomieniami.
**Files:** `analyses/2026-09-18-skanska-stilla-full-verification-v1.md`

---

## 2026-09-18 - Skanska Stilla: 3/3 lokali przeszły weryfikację

**Type:** analysis
**What changed:** Ograniczona weryfikacja trzech wykrytych lokali Stilla zakończyła się wynikiem PASS=3, FAIL=0, UNKNOWN=0.
**Why:** Test potwierdza, że bieżący flow listing discovery -> kod lokalu -> SkanskaAdapter działa poprawnie na ograniczonej próbce rzeczywistych ofert bez wymyślania brakujących danych.
**Next:** Zweryfikować wszystkie 6 wykrytych lokali Stilla i dopiero po pełnym PASS uznać aktualny snapshot za stabilny.
**Files:** `analyses/2026-09-18-skanska-stilla-limited-verification-v1.md`

---

## 2026-09-18 - Skanska Stilla live discovery wykrył 6 lokali

**Type:** analysis
**What changed:** Live discovery na aktualnej stronie Stilla wykrył 6 kodów lokali: AC0340, BA0003, BA0005, BA0351, BA0577 i BA0688, bez sztucznych rekordów tworzonych z zakresów powierzchni.
**Why:** Wynik potwierdza, że listing discovery działa na realnym źródle i może przekazywać jednoznaczne kody lokali do dalszej walidacji adapterem zamiast zgadywać mieszkania na podstawie tekstu strony.
**Next:** Zweryfikować ograniczoną próbkę 3 wykrytych lokali przez SkanskaAdapter i sprawdzić PASS / FAIL / UNKNOWN przed weryfikacją całej listy.
**Files:** `analyses/2026-09-18-skanska-stilla-live-discovery-v1.md`

---

## 2026-09-18 - Skanska adapter i listing discovery v1

**Type:** prototype
**What changed:** Zweryfikowano lokalnie SkanskaAdapter v1 (3/3 testy PASS) i dodano listing discovery v1, który wykrywa kody lokali Stilla wyłącznie z linków do konkretnych mieszkań oraz opcjonalnie przekazuje je do walidacji PASS / FAIL / UNKNOWN.
**Why:** Stary scraper błędnie traktował dowolne fragmenty zawierające `m²` jako mieszkania; nowy flow zaczyna od jednoznacznego kodu lokalu i nie wypełnia brakujących danych.
**Next:** Pobrać najnowsze zmiany lokalnie, uruchomić pełny pytest oraz live discovery Stilla, a następnie ograniczoną weryfikację 3 wykrytych lokali.
**Files:** `analyses/2026-09-18-skanska-adapter-listing-v1.md`

---

## 2026-09-16 - Project created

**Type:** scope-change
**What changed:** AI-Estate-OS został formalnie utworzony jako aktywny projekt z zaakceptowanym `brief.md` i `rules.md`, w tym wymaganiami E-E-A-T oraz standardami architektoniczno-projektowymi dla wizualizacji 3D.
**Why:** Kupujący nowe mieszkanie potrzebuje szybkiego dostępu do zweryfikowanych informacji o konkretnym lokalu, rzutu 2D i wiarygodnej wizualizacji 3D bez przeglądania nieistotnych danych.
**Next:** Zdefiniować mierzalny standard jakości i wiarygodności MVP oraz rozpocząć discovery dla czterech wybranych deweloperów/projektów.
**Files:** `brief.md`, `rules.md`
