# AI-Estate-OS — Skanska Adapter v1

**Status:** prototype specification  
**Pilot:** Skanska / Stilla / BA0122  
**Quality gate:** `../analyses/quality-standard-v1.md`  
**Architecture:** `../decisions/mvp-architecture-v1.md`

---

## 1. Purpose

The adapter converts permitted, apartment-specific Skanska source data into a normalized evidence record for AI-Estate-OS.

It does **not** bypass access controls and does **not** treat public visibility as permission to copy, transform or republish protected floor-plan/graphic assets.

## 2. Adapter input

Minimum preferred input:

- developer = Skanska,
- project/investment,
- apartment code.

Pilot input:

- developer: Skanska,
- project: Stilla,
- apartment_code: BA0122.

## 3. Normalized output contract

```json
{
  "developer": "Skanska",
  "project": "Stilla",
  "apartment_code": "BA0122",
  "building": null,
  "floor": null,
  "rooms": null,
  "area_m2": null,
  "balcony_m2": null,
  "price_pln": null,
  "price_per_m2_pln": null,
  "availability": null,
  "source_url": null,
  "retrieved_at": null,
  "floorplan_reference": null,
  "floorplan_rights_status": "UNKNOWN",
  "evidence_status": "UNKNOWN",
  "conflicts": [],
  "notes": []
}
```

Null is preferable to an invented value.

## 4. Evidence fields

Every populated field should retain or be reproducibly linked to:

- source URL/reference,
- retrieval timestamp/date,
- apartment identifier,
- raw/source value where useful,
- normalized value,
- verification class: VERIFIED / INFERRED / ESTIMATED / DESIGN_ASSUMPTION / UNKNOWN.

Volatile fields — especially price and availability — require a freshness check before being presented as current.

## 5. BA0122 current source snapshot

At the time of this prototype check, the current Polish Skanska page reports:

- project: Stilla,
- apartment: BA0122,
- rooms: 2,
- area: 47.49 m²,
- building: B,
- floor: 1,
- balcony: 8.50 m²,
- apartment price: 846,775.67 PLN,
- price per m²: 17,830.61 PLN.

A current Skanska search result also describes BA0122 as available.

These values are a time-specific evidence snapshot, not immutable master data.

## 6. Conflict handling

Older indexed source material has shown a different area value for BA0122 (47.11 m²), while current Skanska pages report 47.49 m².

Adapter rule:

1. never silently merge conflicting historical/current values,
2. prefer a current primary source for a current-state field,
3. preserve the conflict in evidence metadata,
4. mark historical discrepancy explicitly,
5. do not rewrite history as though the older value never existed.

## 7. Floor-plan rights gate

The Skanska page exposes a floor-plan download function, but the site also states copyright restrictions covering site materials/graphics.

Therefore the adapter separates:

### Metadata gate

Public apartment metadata may be normalized only to the extent permitted for the intended use.

### Asset gate

The floor-plan file/reference is not automatically authorized for copying, transformation, storage or republication merely because a download/view function exists.

Until permitted use is established for the intended MVP workflow:

`floorplan_rights_status = UNKNOWN`

and the production 2D→3D transformation gate remains blocked.

No technical workaround may convert UNKNOWN rights status into PASS.

## 8. Extraction strategy

Preferred order:

1. official apartment detail page,
2. official structured page data/API if documented or otherwise permitted,
3. stable public metadata references where permitted,
4. browser automation only when necessary and permitted.

For each extraction:

- match project + apartment code first,
- reject mixed-apartment records,
- parse locale-specific numbers deterministically,
- retain source provenance,
- record missing values as UNKNOWN,
- detect changes between snapshots.

## 9. Deterministic validation

Before adapter result receives PASS:

- developer matches Skanska,
- project matches requested project,
- apartment code matches exactly,
- building/floor/rooms/area belong to same record,
- price is associated with same apartment and timestamp/source,
- no unresolved identity conflict exists,
- required provenance is present.

Rights status for the 2D asset is a separate mandatory gate for the 2D→3D pipeline.

## 10. Pilot normalized record

```json
{
  "developer": "Skanska",
  "project": "Stilla",
  "apartment_code": "BA0122",
  "building": "B",
  "floor": 1,
  "rooms": 2,
  "area_m2": 47.49,
  "balcony_m2": 8.50,
  "price_pln": 846775.67,
  "price_per_m2_pln": 17830.61,
  "availability": "available",
  "source_url": "official Skanska apartment page",
  "retrieved_at": "2026-09-16",
  "floorplan_reference": "download function present on official apartment page",
  "floorplan_rights_status": "UNKNOWN",
  "evidence_status": "PASS_WITH_RIGHTS_GATE",
  "conflicts": [
    "Older indexed English source reported area 47.11 m²; current primary page reports 47.49 m²."
  ],
  "notes": [
    "Current price and availability are volatile and require refresh before user-facing presentation.",
    "Do not start production floor-plan transformation until rights/use gate is resolved."
  ]
}
```

`PASS_WITH_RIGHTS_GATE` is a prototype adapter state only; it does not mean the full apartment analysis has passed the project QA standard.

## 11. Implementation interface

Suggested Python boundary:

```text
SkanskaAdapter.fetch(project, apartment_code)
  -> SourceSnapshot

SourceSnapshot.normalize()
  -> ApartmentEvidence

ApartmentEvidence.validate_identity()
  -> PASS | FAIL | UNKNOWN

ApartmentEvidence.floorplan_rights_gate()
  -> PASS | FAIL | UNKNOWN
```

The adapter must not contain rendering logic. Geometry and 3D remain downstream components.

## 12. Acceptance criteria for Skanska Adapter v1

The adapter prototype is accepted when it can reproducibly:

1. identify BA0122 from official Skanska data,
2. extract/normalize the approved metadata fields,
3. retain provenance and retrieval time,
4. detect missing/conflicting values,
5. refresh volatile fields without mixing records,
6. expose the floor-plan reference without bypassing the rights gate,
7. return a machine-readable validation state.

## 13. Next technical action

Implement the adapter as executable Python in the application/code repository and test it against BA0122 plus at least one second Stilla apartment.

The test should compare normalized fields against the official source and record PASS / FAIL / UNKNOWN per field. Floor-plan transformation remains a separate gated experiment.
