# AI-Estate-OS — MVP Architecture v1

**Status:** proposed baseline for implementation  
**Constraints:** ≤ 500 PLN initial budget; ≤ 14 days to working MVP  
**Quality gate:** `../analyses/quality-standard-v1.md`

---

## 1. Architectural decision

The MVP will validate one complete, auditable path before attempting broad automation:

**user identifies apartment → source adapter finds/matches offer → evidence record is created → 2D plan is acquired → geometry is extracted/verified → 3D representation is produced → QA returns PASS / FAIL / UNKNOWN → user receives analysis with provenance.**

The MVP is not a universal crawler and not an autonomous architectural design system.

## 2. Scope control

The product may support up to four approved developer/projects, but implementation proceeds sequentially.

**Gate 1:** one apartment from one developer/project must complete the full pipeline successfully.  
**Gate 2:** only then add a second source adapter.  
**Gate 3:** expand toward the remaining approved sources only when the adapter pattern is reproducible.

This prevents the 14-day/500-PLN constraint from being consumed by four unrelated scraping integrations before the core 2D→3D hypothesis is proven.

## 3. Proposed MVP stack

### Frontend

- Next.js + TypeScript.
- Simple responsive web UI.
- Input fields for developer/project and apartment identifier; optional additional identifying fields.
- Result page exposes source provenance, verification state, 2D plan, 3D output and QA status.

### Backend/API

- Next.js server routes/actions for MVP orchestration where practical.
- Python worker/module for source extraction and geometry processing, because existing local Python/Playwright work can be reused.
- Avoid microservices in MVP unless a concrete technical blocker appears.

### Database / evidence ledger

- PostgreSQL-compatible store; Supabase is a candidate for MVP because a free tier exists.
- Store structured metadata and evidence records, not uncontrolled copies of third-party assets.

Minimum entities:

- `developers`
- `projects`
- `apartments`
- `sources`
- `source_snapshots`
- `floorplans`
- `geometry_versions`
- `renders`
- `qa_checks`
- `analyses`

Every material derived value should be traceable to source/evidence or explicitly marked as inference/estimate/design assumption.

### Hosting

Use a low-cost/free deployment during technical validation. Do not commit to a paid hosting plan until commercial-use terms, limits and the actual MVP workload have been checked.

### Source acquisition

Use one adapter per developer/project rather than one generic scraper.

Adapter contract:

1. identify offer,
2. collect permitted metadata,
3. locate permitted 2D source,
4. record provenance and retrieval time,
5. return normalized data,
6. expose missing/conflicting fields rather than invent them.

Preferred acquisition order:

1. documented API/structured feed if available and permitted,
2. structured data embedded in public page where permitted,
3. stable public asset references where permitted,
4. browser automation only where necessary and permitted.

Do not bypass access controls.

## 4. 2D → geometry → 3D pipeline

### Stage A — plan intake

Initial priority: SVG when available because vector geometry is potentially more deterministic than raster interpretation. PDF/PNG/JPG are supported only after a test demonstrates acceptable extraction reliability.

### Stage B — normalization

Convert source information into an internal geometry model containing, when known:

- apartment outline,
- walls,
- rooms,
- doors,
- windows,
- dimensions/scale,
- balcony/loggia/terrace,
- shafts/installations,
- room/ceiling height.

Every field carries provenance/status: VERIFIED, INFERRED, ESTIMATED, DESIGN_ASSUMPTION or UNKNOWN.

### Stage C — geometry validation

Before rendering, run deterministic checks where possible:

- topology consistency,
- dimensions/scale consistency,
- room-area plausibility against source values,
- door/window mapping,
- missing mandatory geometry,
- unsupported changes.

A model with unresolved mandatory geometry remains UNKNOWN and cannot become a verified final result.

### Stage D — 3D generation

Generate the 3D scene from the normalized geometry model, not directly from a generative image prompt.

For MVP, prefer deterministic/scriptable geometry generation (for example a Blender-based or web-3D pipeline selected after spike testing) and use generative AI for assistance, interpretation or presentation only where it cannot silently alter verified architecture.

### Stage E — render QA

Apply `quality-standard-v1.md` and produce PASS / FAIL / UNKNOWN with machine-readable check results plus a user-readable explanation.

## 5. AI allocation

### ChatGPT Plus

Primary role:

- project orchestration and Super Brain maintenance,
- architecture/code review,
- research with source verification,
- structured extraction reasoning,
- QA design,
- generation/review of implementation tasks,
- contradiction detection between evidence and outputs.

ChatGPT subscription usage is treated as development assistance, not assumed to be a production API backend.

### Gemini Pro

Primary complementary role:

- independent review of difficult visual/document inputs,
- alternative interpretation of floor plans where needed,
- second-model verification for selected high-risk extraction cases,
- research cross-checks when independent confirmation materially improves confidence.

### Claude (available free tier)

Primary complementary role:

- independent review of specifications/code/documents within available limits,
- adversarial review for omissions and contradictions,
- second opinion on architecture or data model when useful.

### Rule

Do not run every task through all three systems. Cross-model verification is reserved for high-risk or ambiguous steps. Agreement between models is not evidence by itself; source evidence remains controlling.

## 6. Production AI/API policy

Do not assume ChatGPT Plus, Gemini Pro or a free Claude subscription can be embedded as the production inference layer.

If the MVP requires programmatic model calls, API use is a separate metered cost and must be budgeted per analysis. Start with the cheapest model that passes the quality test; escalate only failed/ambiguous cases to a more capable model.

## 7. Cost envelope

Target during the 14-day build:

- repository: existing GitHub — no new MVP cost assumed,
- local Python/Playwright development — reuse existing environment,
- database/evidence store — free tier during validation if sufficient,
- hosting — free/low-cost validation tier subject to commercial-use terms,
- AI API — optional and capped; only after unit-cost measurement,
- domain/payment system — defer until core technical pipeline passes unless required for the user test.

**Budget rule:** maintain a reserve inside the 500 PLN ceiling rather than spending the full amount on infrastructure before the core pipeline passes.

No exact monthly production cost is asserted in this document; it must be measured from the implemented pipeline and current provider pricing.

## 8. 14-day implementation sequence

### Days 1–2 — source spike

- select one concrete apartment,
- verify identity and source rights/access method,
- acquire metadata and 2D plan,
- create evidence record.

**Kill/redirect criterion:** if the selected source cannot be used legally/reliably, change the source/apartment rather than bypass restrictions.

### Days 3–5 — geometry spike

- parse/normalize the selected 2D plan,
- create internal geometry schema,
- validate walls/rooms/doors/windows/dimensions,
- record UNKNOWN fields.

**Gate:** no rendering work is considered validated until geometry can be compared against the source plan.

### Days 6–8 — 3D spike

- generate deterministic 3D geometry,
- create initial camera/render,
- compare output with source geometry,
- implement QA statuses.

### Days 9–10 — vertical web slice

- input apartment identifier,
- execute/retrieve pipeline result,
- show evidence, 2D, 3D and QA result,
- make uncertainty visible.

### Days 11–12 — second-source reproducibility test

- attempt a second approved developer/project,
- measure adapter effort and pipeline reuse,
- document incompatibilities.

### Days 13–14 — hardening and decision

- fix critical defects,
- measure cost/time per full analysis,
- run final quality checklist,
- decide whether to expand, narrow, or redesign before adding remaining sources.

## 9. First technical experiment

Do not begin with four developers simultaneously.

Choose one real apartment with:

- unambiguous apartment identifier,
- accessible source page/data,
- usable 2D plan,
- enough dimensions/areas to verify geometry,
- permitted acquisition/use for the experiment.

Run it end-to-end and save the result under `prototypes/` plus an analysis under `analyses/`.

The experiment succeeds only if the evidence chain is reproducible and the final QA can justify PASS. A visually attractive render without traceable geometry is a failure of the experiment.

## 10. Open technical decisions

The following are deliberately not frozen until spike results exist:

- exact hosting provider,
- exact database provider,
- Blender vs web-native 3D engine or another deterministic renderer,
- exact production AI models/APIs,
- PDF/raster floor-plan support,
- payment provider,
- automated crawling frequency.

This avoids converting untested assumptions into architecture.

---

## Decision summary

**MVP architecture:** evidence-first modular monolith + per-source adapters + normalized geometry model + deterministic 3D generation + mandatory QA gate.

**Primary technical risk:** reliable, source-faithful 2D → structured geometry conversion across heterogeneous developer plans.

**Immediate next action:** select and audit one real apartment from the approved developer/project list for the first end-to-end technical experiment.
