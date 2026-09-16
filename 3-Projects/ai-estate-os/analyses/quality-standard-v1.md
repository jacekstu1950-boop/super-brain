# AI-Estate-OS — Quality Standard v1.0

**Status:** active for MVP  
**Purpose:** measurable quality gate for apartment data, 2D plans, 3D visualizations and user-facing analyses.  
**Principle:** trust and architectural truth take precedence over visual attractiveness, speed and completeness.

---

## 1. Evidence model

Every material claim must be classified as one of:

- **VERIFIED FACT** — directly supported by an identified source.
- **INFERENCE** — logically derived from verified facts; reasoning must be explainable.
- **ESTIMATE** — approximate value with method or basis stated.
- **DESIGN ASSUMPTION** — introduced because source data is missing; must be visible and reversible.
- **UNVERIFIED** — insufficient evidence; must not be presented as fact.

For volatile facts such as price and availability, record source and retrieval/update date where technically available.

## 2. E-E-A-T operating standard

E-E-A-T is used as a quality framework, not as a numeric Google ranking factor.

### Experience

Where the platform makes practical claims about usability or spatial function, they should be supported by actual plan analysis, measurable geometry, documented tests or clearly identified expert review rather than generic AI assertions.

### Expertise

Technical, architectural, legal and financial statements must be limited to the evidence and competence available. Where professional verification is required, the system must say so and must not present an AI output as a licensed professional opinion.

### Authoritativeness

Prefer primary and authoritative sources: developer source materials for the apartment, official/legal sources for regulations, and documented technical standards for implementation. Secondary sources may supplement but should not silently override a relevant primary source.

### Trustworthiness

Trust is the controlling quality gate. The system must expose material uncertainty, source conflicts, assumptions, freshness limits and AI involvement where relevant. A plausible answer without adequate evidence is not acceptable.

### Who / How / Why

User-facing analyses should make it possible to determine, where relevant:

- **Who** produced or verified the analysis,
- **How** source data and AI/automation were used,
- **Why** the content exists — to support the buyer's apartment evaluation, not merely to generate search traffic.

## 3. Apartment identity gate

Before combining information, verify that developer/project, building (if applicable), apartment code/number, area and plan refer to the same apartment.

**PASS:** identity is sufficiently matched across required sources.  
**FAIL:** evidence indicates mixed apartments/offers.  
**UNKNOWN:** identity cannot be established with sufficient confidence.

FAIL or UNKNOWN blocks a final apartment-specific 3D result unless the user explicitly receives a non-final diagnostic output.

## 4. Source and freshness gate

For each material data item retain, where available:

- source identity or URL/reference,
- retrieval/update date,
- apartment identifier,
- data type,
- verification status.

Price and availability must not be described as current unless their freshness has been checked against an appropriate current source.

## 5. 2D plan gate

Before 3D generation verify:

- plan belongs to the identified apartment,
- file is readable enough for intended extraction,
- apartment outline is recoverable,
- room relationships are recoverable,
- doors/windows visible in source are captured,
- dimensions/scale/areas are retained where supplied,
- missing geometry is explicitly marked.

The source 2D plan remains the primary geometric source of truth.

## 6. 2D → 3D architectural gate

The 3D model must not introduce unsupported architectural changes.

Check at minimum:

1. apartment outline,
2. room topology,
3. wall positions,
4. door positions and openings when known,
5. window positions and dimensions when known,
6. entrance position,
7. balcony/loggia/terrace geometry,
8. dimensions and scale where available,
9. installation/shaft positions where documented,
10. ceiling/room height where documented.

Unknown values must remain UNKNOWN or be explicitly labeled DESIGN ASSUMPTION. They may not silently become source facts.

## 7. Functional and ergonomic gate

A proposed arrangement must be checked for reasonable use of:

- circulation paths,
- door operation,
- window access/operation,
- furniture access and clearance,
- kitchen equipment,
- sanitary equipment,
- wardrobes and storage,
- table/chair use,
- bed access,
- documented service/installation zones.

Do not claim legal or technical compliance solely because an arrangement looks plausible.

## 8. Visual truth gate

Rendering choices must not materially mislead the buyer about the apartment.

Do not use visual techniques that intentionally distort perceived space, including unsupported geometry, unrealistic furniture scale or perspective chosen to create a materially false impression of room size.

Decoration may vary; verified architecture may not.

## 9. Legal and rights gate

Before production use of third-party data/materials, verify the permitted method of access and intended use as appropriate for the source.

Public visibility alone is not evidence of permission to copy, automate, transform or republish a floor plan or other protected material.

If legal/use status is unresolved, mark it UNKNOWN and block the affected production feature until resolved or replaced by a permitted source/method.

## 10. Output status

Each full apartment analysis ends with one overall status:

- **PASS** — all mandatory gates passed.
- **FAIL** — at least one mandatory gate failed.
- **UNKNOWN** — no known failure, but evidence is insufficient for at least one mandatory gate.

UNKNOWN is never automatically converted to PASS.

A FAIL/UNKNOWN analysis may be shown as a diagnostic result, but must not be marketed or labeled as a verified final analysis.

## 11. Mandatory pre-publication checklist

- [ ] Apartment identity verified
- [ ] Source provenance retained
- [ ] Freshness checked for volatile facts
- [ ] Facts separated from inference/estimate/assumption
- [ ] 2D plan matched to apartment
- [ ] 2D geometry checked
- [ ] 3D geometry checked against 2D
- [ ] Doors/windows checked where source data exists
- [ ] Scale/dimensions checked where source data exists
- [ ] Functional/ergonomic conflicts checked
- [ ] Unsupported architectural changes absent
- [ ] Legal/use status sufficient for production use
- [ ] Material uncertainty disclosed
- [ ] AI/automation role disclosed where relevant
- [ ] Final PASS / FAIL / UNKNOWN assigned

## 12. MVP acceptance rule

For the MVP, success requires not merely generation of a 3D image but a reproducible evidence chain:

**identified apartment → traceable source data → verified 2D plan → controlled geometry extraction → 3D output → QA status.**

If this chain cannot be demonstrated for a supported developer/project, that case is not counted as a successful full analysis.

---

## Versioning

**v1.0** — initial quality standard combining evidence discipline, E-E-A-T principles, anti-hallucination controls, architectural truth, 2D→3D QA, legal/use checks and PASS/FAIL/UNKNOWN gating.
