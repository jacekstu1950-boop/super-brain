# AI-Estate-OS — Log

Append-only. Newest entry at the top. The AI writes this - see `3-Projects/README.md`.

Types: `decision`, `prototype`, `analysis`, `research`, `scope-change`, `shipped`.

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
