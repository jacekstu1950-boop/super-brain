# AI-Estate-OS — Log

Append-only. Newest entry at the top. The AI writes this - see `3-Projects/README.md`.

Types: `decision`, `prototype`, `analysis`, `research`, `scope-change`, `shipped`.

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
