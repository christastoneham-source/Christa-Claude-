# NOVELTY CANDIDATES — The Investment Map

Prepared 2026-08-03. Attorney work product. Written for a professional patent
searcher who has never seen this product. All code references are to
`McNichols_Kresge_DEMOv2.html` (v2). "Core" = load-bearing to the product's
value proposition; "peripheral" = supporting.

The system in one sentence: a self-contained, client-side corridor investment
decision instrument that binds a pre-joined parcel-of-record dataset to a set
of user-configurable "investment pillars" (use types carrying cost-per-sqft
and outcome-per-sqft coefficients), recomputing per-parcel costs and outcomes,
portfolio rollups, and a projected post-investment property value and tax
yield on every assignment, with savable, shareable, visually-compared
scenarios.

---

## The inventor's four believed distinguishing elements — verdicts first

### A. "Projected post-investment property value from a selected use type at the individual parcel level"

**The code does NOT support this belief as stated.** Post-investment value is
computed at the PORTFOLIO level only: `postValue = totalInvestment(list) ×
assume.valueFactor` (lines 488-489), where `list` is all assigned parcels
together. No per-parcel post-investment value is computed, stored, or
displayed anywhere in the build. What IS per-parcel: cost (`parcelCost`, 404)
and outcomes (`impactFor`, 399), both driven by the selected use type; and the
per-parcel current assessed value of record is carried (line 279) and
subtracted in aggregate (490). Because value is linear in investment
(valueFactor × cost) and cost is per-parcel, a per-parcel value figure is
arithmetically implied by the existing formulas — but it is an intended
embodiment, not an implemented one. **Recommendation: claim the per-parcel
value projection as a described embodiment in the provisional (it follows
directly from parcelCost × valueFactor against the parcel's assessed baseline)
and claim the implemented portfolio-level value/tax projection as the built
embodiment.** Do not represent per-parcel value output as current
functionality.

### B. "Holding multiple investment pillars against the same parcel set and switching between them live"

**Supported.** Two mechanisms implement this: (1) per-parcel live reassignment
among N pillars with immediate full recompute — `assign()` (471) →
`renderAll()` (335), with the pillar set itself user-definable at runtime
(`addPillar`/`updPillar`/`delPillar`, 854-859); (2) whole-plan swapping —
`applyScenario()` (587) replaces the entire assignment map in one action, and
`scenarioTotals()` (599) re-prices every saved plan against CURRENT
assumptions on every render, so alternatives stay comparable as assumptions
move. Core.

### C. "Aggregating parcel-level projections into a portfolio view across mixed use types"

**Supported.** The label-keyed outcome union (`aggregateOutcomes`, 408) is the
specific mechanism: each pillar carries its own arbitrary metric schema
(user-editable labels/factors), and portfolio rollup accumulates by metric
label across heterogeneous pillars without a fixed outcome taxonomy — housing
units, jobs, park sqft, and arts revenue coexist in one tally, dashboard, and
scenario-compare table (410-417, 477-545, 614-623). Core.

### D. "Consolidating GIS, zoning, land use, ownership, valuation, and AMI into one decision surface rather than separate reports"

**Supported, with one honest qualifier.** All six data families are present on
one surface: parcel polygons on satellite + live building footprints (GIS,
629-758), zoning of record with color mode (233, 359-363, 452), two-level land
use (232, 277, 446-447), ownership (445), assessed valuation feeding the
value/tax card (453, 484-491), and AMI (230, 548-552). The qualifier: **AMI is
a read-only reference table; it does not parameterize any computation in this
build** (the AMI-aware housing pillar is a documented planned embodiment,
`McNichols_DEMO_TODO.md:25-26`). Also note zoning is displayed, never
interpreted (no rule engine). The consolidation claim is honest as
"one decision surface"; it would overreach as "AMI-driven underwriting." Core.

---

## Full candidate list

### 1. Coefficient-driven use-type assignment engine (built)

- **Claim-like statement:** A system that associates each of a plurality of
  user-configurable use types with a cost-per-unit-area coefficient and a set
  of outcome coefficients, and, upon assignment of a land parcel of record to
  a use type, computes a development cost and a plurality of outcome
  quantities from the parcel's recorded land area and immediately propagates
  the results to parcel, corridor, and portfolio displays.
- **Technical steps:** parcel record with `sqft` of record (226, 278) →
  assignment (471) → `parcelCost` = sqft × ($/sqft override ?? pillar default)
  × global sensitivity (404) → `impactFor` = sqft×factor ($) or
  floor(sqft/factor) (counts) (399-403) → synchronous re-render of every view
  + persistence (335, 289).
- **Files:** `McNichols_Kresge_DEMOv2.html` (all); same engine in v1 and OFFLINE.
- **Conventional alternative:** a spreadsheet pro forma per site, or GIS
  suitability scoring that ranks parcels but does not price a chosen use;
  parcel viewers (Regrid, Landgrid, county GIS) display records without
  projection.
- **Core.**

### 2. Live multi-pillar scenario switching re-priced against current assumptions (built)

- **Claim-like statement:** A method of holding a plurality of saved
  assignment maps over a common parcel set and, on each display cycle,
  re-computing every saved map's cost, outcome, and tax projections against
  the currently prevailing assumption set, such that saved alternatives remain
  commensurable after any assumption change.
- **Technical steps:** frozen assignment snapshot (554, 586) → per-render
  rebuild of a virtual parcel list per scenario (599) → same cost/outcome/tax
  functions as the live plan (408-409, 601) → side-by-side compare table with
  outcome-label union (614-623) → one-step whole-plan swap (587).
- **Files:** v2 lines 554-626.
- **Conventional alternative:** static scenario reports frozen at authoring
  time; BI dashboards that snapshot numbers, not assignments.
- **Core.**

### 3. Label-keyed heterogeneous outcome rollup (built)

- **Claim-like statement:** Aggregating outcome projections from parcels
  assigned to differently-schema'd use types by accumulating values under
  their textual metric labels, whereby use types with disjoint or overlapping
  outcome vocabularies roll up into a single portfolio table without a
  predefined outcome taxonomy.
- **Technical steps:** per-pillar arbitrary metric arrays (255-273, editable
  850-857) → `aggregateOutcomes` label-map accumulation (408) → dashboard
  charts/tables filter by money flag (537-545) → scenario compare unions
  labels across scenarios with "-" fill (615-622).
- **Files:** v2 lines 408, 537-545, 615-622.
- **Conventional alternative:** fixed KPI schemas (jobs/units columns defined
  in advance) or manual consolidation across separate models.
- **Core** (it is what makes mixed-use portfolios roll up).

### 4. Portfolio value-creation and tax-yield projection from assignment state (built)

- **Claim-like statement:** Computing, from an assignment state over parcels
  of record, an estimated post-investment property value as a scalar multiple
  of aggregate projected development cost, an estimated value created as that
  figure net of the parcels' assessed values of record (excluding exempt
  parcels with disclosure of the exclusion count), and an estimated new annual
  property tax as the post-investment value times an effective rate, each
  factor being user-adjustable with immediate recomputation.
- **Technical steps:** lines 484-491 (dashboard), 601 (per-scenario), 780-783
  (print); exempt handling 442, 486-487, 520; assumption inputs 510-512 via
  `setAssume` (473).
- **Files:** v2 lines 442, 473, 484-491, 508-521, 601, 780-783.
- **Conventional alternative:** fiscal-impact studies produced offline by
  consultants; TIF projection spreadsheets.
- **Core.**

### 5. Frontage-proportional diagrammatic corridor with scenario "corridor picture" (built)

- **Claim-like statement:** Rendering a street corridor as two facing rows of
  parcel cells ordered by address and dimensioned from each parcel's recorded
  frontage and land area, colored by assignment state, and rendering a
  miniaturized strip of the same encoding as a per-scenario fingerprint in a
  comparison table.
- **Technical steps:** `widthFor` 1.1 px/ft (372), `heightFor` sqft/420
  clamped (373), address-sort + side split (389-392), road band (393-396);
  miniature: 0.09 px/ft, 2 px floor (589-598) reused in scenario list and
  compare row (611, 618).
- **Files:** v2 lines 367-397, 589-598.
- **Conventional alternative:** map choropleths or tabular scenario diffs; no
  schematic elevation-style strip.
- **Core-adjacent** (signature visualization; also the seed of the planned
  street-elevation embodiment).

### 6. Multi-source building-footprint acquisition with proximity dedup and offline-persistent cache (built)

- **Claim-like statement:** Acquiring building footprints for a bounding box
  by querying a municipal feature service under multiple candidate service
  names, supplementing with crowd-sourced footprints deduplicated by centroid
  proximity thresholds, and persisting the merged set in browser storage such
  that subsequent sessions, including offline sessions and sibling builds
  sharing the storage key, render footprints without network access.
- **Technical steps:** lines 671-723 (fallback chain), 705-711 (0.00006°/
  0.00008° dedup), 640+662+674-675 (cache), commit 2a204e3 (cross-build
  persistence).
- **Files:** v2 lines 640-723; `McNichols_Kresge_DEMO_OFFLINE.html` (same code).
- **Conventional alternative:** single-source GIS layer requiring live server.
- **Peripheral** (robustness engineering; possibly claimable as a dependent
  limitation, not standalone).

### 7. Versioned plain-file scenario interchange (built)

- **Claim-like statement:** Sharing decision scenarios between users of a
  server-less tool via a downloaded JSON artifact carrying a tool-version
  gate, scenario assignment maps, and the author's assumption set, imported by
  merge with collision renaming.
- **Technical steps:** lines 555-585; version prefix check (561), rename
  " (imported)" (565), assumption adoption (570).
- **Conventional alternative:** shared server database / SaaS accounts.
- **Peripheral**, but it evidences the single-file, no-backend architecture.

### 8. Readiness scoring axis (built, removed — alternative embodiment)

- **Claim-like statement:** Scoring each parcel on a set of boolean readiness
  dimensions (funding, policy/zoning, stakeholder, environmental/title,
  timeline) and displaying a threshold-colored composite alongside the
  quantitative projections.
- **Technical steps:** `git show 913a55a:McNichols_Kresge_DEMO.html` lines
  218-224 (READINESS), 341 (rdScore), rdColor thresholds 70%/40%; removed in
  commit 336bbf3.
- **Peripheral / historical**; include for breadth as an alternative decision
  axis.

### 9. Intended embodiments (not built — described in TECHNICAL-DISCLOSURE.md §12)

Per-parcel post-investment value (see verdict A); development-mode cost
switching on floor area of record; AMI-band-parameterized housing pillar; pro
forma gap + funding-pipeline drawdown; three-ring environmental screening from
uses of record; before/after concept massing and street elevation from the
same assignment state. Each is architecture-specific in §12 and can be claimed
as described embodiments.

---

## Clearly conventional — do not claim

- Leaflet map with tile layers, polygons, tooltips, markers (629-758).
- Chart.js bar/doughnut charts (535-538); html2canvas PNG capture (766-776);
  print-to-PDF via `window.print()` (777).
- localStorage persistence per se (289-300) and JSON file download/upload per
  se (555-585) — the SCHEMAS and version gating may matter, the browser APIs
  do not.
- Guided tour overlays (801-830); filter chips; color legends; single-page
  tabbed HTML app; CSS theming; emoji markers.
- Displaying assessor attributes (owner, zoning, value) on a parcel popup —
  every county GIS viewer does this.
- Percent-of-AMI affordability arithmetic (income × band%, × 30% ÷ 12) — HUD
  standard practice.
- Centroid computation, bbox queries, GeoJSON parsing.

## Prior art search terms (most → least specific)

1. "parcel-level investment scenario" tool corridor revitalization
2. "cost per outcome" parcel assignment "investment pillar"
3. corridor parcel "scenario comparison" "tax base" projection interactive
4. "post-investment" assessed value projection parcel "value factor"
5. land bank parcel disposition scenario modeling software patent
6. "commercial corridor" revitalization decision support system parcels
7. parcel assignment use type "cost per square foot" outcome projection
8. fiscal impact "new property tax" scenario tool parcel-level interactive
9. mixed-use portfolio rollup parcel projections heterogeneous metrics
10. "scenario planning" GIS parcel "side by side" comparison neighborhood investment
11. TIF district projection interactive parcel tool
12. brownfield corridor reuse planning software parcel scoring
13. site readiness scoring checklist parcel development tool
14. "frontage" proportional corridor diagram visualization parcels schematic
15. offline single-file HTML GIS decision tool localStorage
16. building footprint merge municipal OpenStreetMap dedup centroid
17. scenario JSON export import planning tool version
18. community development financial modeling parcel "area median income"
19. US patent classification G06Q 50/16 (real estate) + scenario simulation
20. US patent classification G06Q 10/0637 (strategic planning) parcel
21. Urban Footprint scenario planning patent
22. CityEngine / TestFit / Envision Tomorrow scenario "return on investment" parcel
23. CoStar / Regrid / Landgrid parcel analytics patent
24. land use suitability analysis weighted overlay interactive
25. "what-if" land use scenario tax revenue municipal software
26. real estate underwriting automation parcel batch pro forma
27. capital allocation dashboard place-based philanthropy
28. participatory planning tool scenario voting parcels
29. GIS "decision support system" corridor commercial district
30. property value uplift estimation redevelopment model

Suggested searcher note: the closest commercial genre is scenario-planning
platforms (UrbanFootprint, Envision Tomorrow, CommunityViz, TestFit) and
parcel-data platforms (Regrid, CoStar). The distinguishing axis to probe is
(a) parcel-of-record granularity + (b) user-editable coefficient engine +
(c) live multi-scenario re-pricing + (d) tax-base output in a single
serverless surface, versus their zone/grid-level or fixed-model approaches.
