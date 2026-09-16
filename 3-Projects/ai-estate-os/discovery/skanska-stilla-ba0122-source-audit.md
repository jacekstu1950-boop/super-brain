# Skanska / Stilla / BA0122 — Source Audit v1

**Date:** 2026-09-16  
**Purpose:** first source audit for the AI-Estate-OS end-to-end MVP experiment.  
**Status:** CONDITIONAL / BLOCKED FOR PRODUCTION REUSE pending rights/permission verification.

## 1. Candidate apartment

- Developer/source: Skanska Residential Development Poland
- Project: Stilla, Warszawa — Włochy
- Apartment: BA0122
- Building: B
- Floor: 1
- Rooms: 2
- Current Polish source page observed area: 47.49 m²
- Balcony: 8.50 m²

The apartment was selected because the official source page exposes a stable apartment identifier and a floor-plan acquisition path, making it useful for testing identity matching and source provenance.

## 2. Verified source observations

The official apartment page exposes:

- apartment identifier BA0122,
- project Stilla,
- room count,
- area,
- building/floor information,
- current price information,
- a floor-plan download/action,
- a 3D-model section.

The page also states that the floor plan can be sent by email in PDF format.

## 3. Important source inconsistency

A previously indexed English-language version of the same apartment page reported a different apartment area (47.11 m²) than the current Polish page (47.49 m²).

Therefore area must not be treated as immutable without source date/version. The current Polish page is preferred for the current audit, but the discrepancy must remain recorded until explained.

**QA status for area consistency:** UNKNOWN.

## 4. Rights / legal gate

The Skanska page footer states that materials on the website, particularly graphical elements, are Skanska property protected by copyright and that they may not be distributed, copied, adapted/processed or made available without written consent.

Therefore public accessibility of the floor plan is not sufficient evidence that AI-Estate-OS may automatically copy, transform into 3D, store, or republish it in a production service.

**Production-use rights gate:** UNKNOWN / BLOCKED pending written permission or another clearly permitted legal basis/source.

No access-control bypass is permitted.

## 5. E-E-A-T / evidence assessment

### Experience
PASS for source-audit work: a concrete real apartment/source is being tested rather than a hypothetical plan.

### Expertise
CONDITIONAL: architectural/geometry claims must pass the project quality standard; legal conclusions require appropriate legal verification where necessary.

### Authoritativeness
PASS for apartment identity/basic offer data because the primary developer page is used.

### Trustworthiness
CONDITIONAL because:
- area discrepancy exists between source versions,
- production reuse/transformation rights are not yet established,
- volatile facts such as price/status require retrieval-date tracking.

## 6. MVP gates

| Gate | Status | Reason |
|---|---|---|
| Apartment identity | PASS | Stable BA0122 identifier on official Skanska/Stilla page |
| Primary-source provenance | PASS | Official developer source |
| Current metadata extraction | PASS/CONDITIONAL | Core fields available; volatile values need timestamps |
| Area consistency | UNKNOWN | 47.49 m² current PL page vs 47.11 m² older indexed EN page |
| 2D acquisition path | PASS | Official page exposes floor-plan acquisition and PDF-by-email path |
| Rights for automated 2D reuse/transformation | UNKNOWN/BLOCKED | Footer restriction requires resolution |
| Geometry extraction | NOT STARTED | Do not process protected plan until rights/use gate is resolved for intended experiment |
| 3D generation | NOT STARTED | Depends on permitted 2D use and verified geometry |
| Final QA | NOT STARTED | Pipeline incomplete |

## 7. Decision

BA0122 is technically promising as the first Skanska source-adapter case, but the experiment must not silently treat public access as permission for automated copying/transformation/republication.

Proceed with metadata/source-adapter design and rights clarification. Do not count BA0122 as a successful full analysis until the legal/use gate and geometry QA are resolved.

## 8. Next actions

1. Define the minimum Skanska adapter schema using metadata that can be lawfully accessed/used.
2. Establish whether written permission/licence or another permitted route can cover floor-plan processing for the MVP.
3. If permission is obtained or a permitted test asset is supplied by the user/rightsholder, acquire the exact BA0122 plan and record its source/version/hash.
4. Reconcile the 47.49 vs 47.11 m² discrepancy.
5. Only then run 2D normalization → geometry validation → deterministic 3D → PASS/FAIL/UNKNOWN QA.

## 9. Evidence policy

No unsupported missing geometry will be invented. Any unavailable dimension or architectural element remains UNKNOWN or an explicitly approved DESIGN ASSUMPTION, in accordance with `rules.md` and `analyses/quality-standard-v1.md`.
