# TECHNICAL DISCLOSURE — The Investment Map (W. McNichols Corridor Tool)

Prepared 2026-08-03. Attorney work product. Written to enable a competent GIS or
real estate technologist to rebuild the system from this document alone.

Primary source file: `McNichols_Kresge_DEMOv2.html` (864 lines; "v2", tool
version "2.1"). Secondary: `McNichols_Kresge_DEMO.html` ("v1"),
`McNichols_Kresge_DEMO_OFFLINE.html` (v2 with libraries inlined). All line
numbers below refer to v2 unless stated. All code quotes are verbatim.

## 0. System overview

A single self-contained HTML file implementing a corridor investment decision
tool. It embeds a pre-joined parcel dataset for 93 in-scope parcels plus 25
context parcels on the W. McNichols corridor, Detroit MI (line 226, constant
`DATA`, ~45 KB JSON). All computation is client-side JavaScript; there is no
server, no build system, and no database. State persists in browser
localStorage. Five views (tabs at lines 172-176): Corridor (diagrammatic
schematic), Map View (Leaflet GIS), Dashboard (charts + value/tax + AMI),
Scenarios (save/compare/share), Edit Pillars (assumption editor).

The core mechanism: a user assigns any parcel to one of N configurable
"investment pillars" (use types). Each pillar carries a development cost per
square foot and a list of outcome metrics expressed as square-feet-per-unit or
dollars-per-square-foot factors. Assignment immediately recomputes per-parcel
cost and outcomes, corridor-wide tallies, dashboard aggregates, and a projected
post-investment property value and new annual property tax for the assigned
set.

## 1. Formulas

### 1.1 Per-parcel outcome projection — `impactFor(p, pl)` (lines 399-403)

```js
function impactFor(p,pl){const sqft=Number(p.sqft)||0;return pl.metrics.map(m=>{
  let f=Number(m.factor)||0;
  const value=m.money?sqft*f:(f>0?Math.floor(sqft/f):0);
  return {label:m.label,money:m.money,value};
});}
```

For each metric `m` of the assigned pillar `pl`:
- If `m.money` is true: **outcome = sqft × factor** — units: dollars (factor is
  $ per sqft of land per year for revenue metrics; sqft is parcel LAND area).
- Else: **outcome = floor(sqft ÷ factor)** — units: whole counts (units, jobs,
  children, households); factor is sqft of land per one unit of outcome.
- A non-money factor of 0 yields 0 (division guarded by `f>0`).

Variables: `p.sqft` = parcel land area in square feet (assessor record, line
278); `m.factor` = pillar metric coefficient (user-editable, see §2.2);
`m.money` = boolean flag set per metric (line 853).

**Implied assumption:** outcomes scale linearly with parcel LAND area, not
building area, and are floor-rounded to whole units per parcel (so a parcel
smaller than one `factor` produces zero of that outcome).

### 1.2 Per-parcel cost projection — `parcelCost(p, pl)` (line 404)

```js
function parcelCost(p,pl){const cps=(p&&p.costOverride!=null)?Number(p.costOverride):(Number(pl.cost)||0);return (Number(p.sqft)||0)*cps*(state.assume.costFactor||1);}
```

**cost = land sqft × cost-per-sqft × global cost factor**, in dollars, where
cost-per-sqft ($/sqft) resolves in priority order: (1) per-parcel override
`p.costOverride` if set (any number, including 0), else (2) the pillar default
`pl.cost`. `state.assume.costFactor` is the global sensitivity multiplier
(default 1.0).

**Implied assumptions:** cost scales with LAND area even where a building
exists (the UI note at line 833 says "building square footage × cost per
square foot" and line 467 says "Estimated cost = {sqft} sqft × cost per
sqft" — the words say building sqft in the pillar editor but the CODE uses
`p.sqft`, the land area; the parcel-panel text correctly prints the land
figure. This wording/code divergence is itself worth noting to counsel).
Acquisition cost is not separated from construction cost; the single $/sqft is
described in-app as "a planning cost per square foot" (line 240).

### 1.3 Portfolio investment — `totalInvestment(list)` (line 409)

```js
function totalInvestment(list){return list.reduce((a,p)=>{const pl=state.pillars.find(x=>x.id===p.pillar);return a+(pl?parcelCost(p,pl):0);},0);}
```

Sum of `parcelCost` over a parcel list; parcels whose assigned pillar no longer
exists contribute 0.

### 1.4 Portfolio outcome aggregation — `aggregateOutcomes(list)` (line 408)

```js
function aggregateOutcomes(list){const t={};list.forEach(p=>{const pl=state.pillars.find(x=>x.id===p.pillar);if(!pl)return;impactFor(p,pl).forEach(m=>{t[m.label]=t[m.label]||{v:0,money:m.money};t[m.label].v+=m.value;});});return t;}
```

Outcomes accumulate into a map **keyed by metric LABEL string** across all
pillars. Two pillars that both define a metric labeled "Jobs" pool into one
"Jobs" total even though their factors differ. This label-keyed union is what
lets a mixed-use portfolio (housing + arts + parks) roll up into one outcome
table without a fixed schema.

### 1.5 Post-investment property value and tax — `renderDashboard()` (lines 484-491)

```js
const valued=list.filter(p=>Number(p.assessed)>0);
const curAssessed=valued.reduce((a,p)=>a+Number(p.assessed),0);
...
const invest=totalInvestment(list);
const postValue=invest*state.assume.valueFactor;
const valueCreated=postValue-curAssessed;
const newTax=postValue*state.assume.taxRate;
```

- **Estimated value after investment = total investment × valueFactor**
  (dollars). Default valueFactor 1.0 (line 286), i.e. $1 of value per $1
  invested, editable (line 511).
- **Estimated value created = postValue − current assessed value of assigned
  parcels** (only parcels with assessed > 0 count toward `curAssessed`).
- **Estimated new annual property tax = postValue × taxRate** (dollars/year).
  Default taxRate 0.034 (line 286), labeled "Effective annual tax rate" (line
  512).

The on-screen definition (line 508): "Estimated value after investment = total
development investment × value factor. Estimated new annual property tax =
value after investment × effective tax rate. Planning estimates only, not an
appraisal or a tax determination."

**Important structural fact:** post-investment VALUE is computed at the
PORTFOLIO level (from total investment), not per parcel. No per-parcel
post-investment value is computed or displayed anywhere in the code. Per-parcel
the system computes cost and outcomes only. (See NOVELTY-CANDIDATES.md §1.)

**Implied assumptions:** value uplift is proportional to spend, independent of
use type, location, or existing building; the tax estimate applies the single
effective rate to the full post value (not to the increment), and ignores
exemption status of the future use; `newTax` is not net of current taxes.

The same formulas recur:
- Scenario compare tax (line 601): `tax:inv*state.assume.valueFactor*state.assume.taxRate`.
- Print report (lines 780-783): `valueCreated=invest*state.assume.valueFactor-curAssessed`.

### 1.6 Vacancy KPI (lines 480-482)

```js
const vacTotal=state.parcels.filter(p=>p.use==="Vacant").length;
const vacAssigned=state.parcels.filter(p=>p.use==="Vacant"&&p.pillar).length;
const vacPct=vacTotal?Math.round(vacAssigned/vacTotal*100):0;
```

"Vacant land addressed" = assigned vacant parcels ÷ all vacant parcels, %.

### 1.7 Cost per outcome (lines 540-544)

```js
const cost=totalInvestment(pl_list);const agg=aggregateOutcomes(pl_list);
Object.entries(agg).forEach(([l,o])=>{if(o.money)return;const cpo=o.v>0?cost/o.v:0; ... });
```

Per pillar: **cost per outcome = pillar total investment ÷ pillar total of that
outcome**, computed only for non-money metrics; 0 when the outcome total is 0.
Note the numerator is the pillar's ENTIRE investment, charged in full against
EACH outcome type separately (jobs and units each see the whole cost — cost is
not allocated across outcome types).

### 1.8 AMI affordability table — `renderAmiTable()` (lines 548-552)

```js
const bands=[30,50,60,80,100,120];
const rows=bands.map(b=>{const inc=ami*b/100;const mo=inc*0.30/12;...});
```

For band b%: **income = AMI_VALUE × b/100**; **affordable monthly housing cost
= income × 0.30 ÷ 12**. `AMI_VALUE=95900` dollars, "Detroit-Warren-Livonia, MI
(HUD FY2025 Median Family Income)" (line 230). The 30% standard is hard-coded.
Read-only reference: AMI does not enter any projection formula in this build.

### 1.9 Rendering geometry (diagrammatic corridor)

- Parcel cell width px: `widthFor` (372): `Math.max(34,(Number(p.frontage)||40)*1.1)` — 1.1 px per foot of frontage, 34 px floor, 40 ft default frontage.
- Parcel cell height px: `heightFor` (373): `Math.max(46,Math.min(120,s/420))` with `s=sqft||3000` — 1 px per 420 sqft, clamped 46-120.
- Scenario mini-strip cell width px: `miniStrip` (594): `Math.max(2,Math.round((Number(p.frontage)||40)*0.09))` — 0.09 px per foot, 2 px floor.
- Corridor ordering (389): parcels and context sorted by `Number(address)`, split into north/south rows by `side` (391-392).
- Map footprint dedup thresholds (709): centroids within `0.00006`° latitude AND `0.00008`° longitude are duplicates (≈6.7 m × ≈6.6 m at Detroit's latitude).

## 2. Constants, defaults, coefficients, thresholds

### 2.1 Global constants

| Name | Value | Where | Meaning |
|---|---|---|---|
| `TOOL_VERSION` | `"2.1"` | 227 | version string; gates scenario import (§7) |
| `STAMP` | "Parcel data: City of Detroit Office of the Assessor, 2026. Boundaries and values are reference data of record. Tool v2.1, Connecting Dots and Strategies." | 228 | provenance stamp on map, PNG, PDF |
| `CORRIDOR`, `CITY` | "W. McNichols Corridor", "Detroit, MI" | 229 | labels |
| `AMI_VALUE` | 95900 ($) | 230 | HUD FY2025 MFI, Detroit metro |
| `AMI_METRO` | "Detroit-Warren-Livonia, MI (HUD FY2025 Median Family Income)" | 230 | label |
| `LS_KEY` | "cds_mcnichols_demo_v2" | 287 | localStorage key (v1 uses "cds_mcnichols_demo_v1", v1:281) |
| `BLD_CACHE_KEY` | "cds_mcnichols_bld_cache_v1" | 640 | footprint cache key (shared string across v2 and offline builds — cache deliberately interoperates, commit 2a204e3) |
| tour-done flag | "cds_mcnichols_tour_done" | 310, 829 | first-run tour gate |
| `LAND_USES` | 9 use→hex color entries | 232 | category palette |
| `ZONING_COLORS` | 11 district→hex entries; fallback `#7E8AA2` | 233-234 | zoning palette |
| expected counts | 93 in-scope, 25 context | 317-322 | console build report sanity checks |
| AMI bands | [30,50,60,80,100,120] % | 549 | table rows |
| affordability share | 0.30 of income | 550 | hard-coded |

### 2.2 Default pillars — `defaultPillars()` (lines 253-274)

| Pillar | Color | Cost $/sqft | Metrics (label: factor) |
|---|---|---|---|
| Housing & Commercial Development | #D95448 | 250 | Housing Units: 1200 sqft/unit; Jobs: 2000 sqft/job; Annual Revenue: $4/sqft (money) |
| Youth & Education | #F1BA4B | 300 | Children Served: 60 sqft/child; Educator Jobs: 600 sqft/job |
| Sustainable Public Realm | #47AB4F | 80 | Park Area (sqft): 1 sqft/sqft; Households Served: 500 sqft/household |
| Cultural & Arts Ecosystem | #00BCC5 | 220 | Arts Jobs: 800 sqft/job; Studio/Gallery Units: 1000 sqft/unit; Arts Revenue: $5/sqft (money) |

Each pillar also carries narrative fields `y1`, `y2`, `lt` (Year 1 / Year 2
outputs, long-term outcomes; lines 256-273) displayed verbatim on assignment.

New-pillar defaults (`addPillar`, 858): cost 150 $/sqft, one metric "Jobs" at
2000. New-metric default (`addMetric`, 856): label "New metric", factor 1000.

### 2.3 Assumption defaults — `state.assume` (line 286)

```js
const state={...,assume:{costFactor:1.0,valueFactor:1.0,taxRate:0.034},...};
```

| Assumption | Default | Edited at | Propagation |
|---|---|---|---|
| `costFactor` (global cost sensitivity) | 1.0 | Dashboard (510) and Edit Pillars (834) | multiplies every `parcelCost` (404) |
| `valueFactor` (value per $ invested) | 1.0 | Dashboard (511) | dashboard postValue (489), scenario tax (601), print (783) |
| `taxRate` (effective annual property tax) | 0.034 | Dashboard (512) | newTax (491), scenario tax (601) |

UNVERIFIED: the empirical basis of every coefficient above (pillar costs,
factors, 0.034, 95900). Nothing in the repo documents sources for the pillar
coefficients; the UI labels them "planning placeholder" (line 833) and
"planning assumption, editable" (line 467). `AMI_VALUE` is attributed to HUD
FY2025 but no source file exists in the repo. Calibrated coefficients are an
explicitly planned paid deliverable (`McNichols_DEMO_TODO.md:31`).

## 3. Data model

### 3.1 Embedded dataset `DATA` (line 226, single JSON literal)

```
DATA = { inscope: ParcelRecord[93], context: ContextRecord[25], bbox: [S,W,N,E] }
bbox = [42.416055,-83.162849,42.417779,-83.139783]
```

`ParcelRecord` fields (observed across all 93 records):
`address` (string house number, e.g. "6325"), `owner` (string, uppercase
assessor format), `use` (category: Commercial 69, Vacant 20, Governmental 4),
`existing_use` (assessor use string of record, e.g. "Store-Retail", "Dry
Cleaner", "Gas Station W/Conv Store-Resturant" [sic]; empty for 1+ records),
`floor_area` (sqft of building of record, null for 24 records), `year_built`
(null for the same 24), `sqft` (land area, range 1,995–48,520), `frontage`
(ft), `side` ("N"/"S"), `notes` (string), `zoning` (all 93 are "B2"),
`assessed` (dollars; null/0 for 16 records), `rings`
(lat/lon polygon array-of-rings; present on all 93).

`ContextRecord`: `address`, `side`, `frontage`, `vacant` (bool), `kind`
("grey"=24, "green"=1 [Marygrove Conservancy]), `name`, `existing_use`,
`rings`.

### 3.2 Runtime entities

- **Parcel** (`buildParcels()`, 276-280): DATA.inscope mapped to
  `{id, address, owner, use, existingUse, floorArea, yearBuilt, sqft, frontage,
  side, notes, zoning, assessed, rings, pillar:null, costOverride:null}`.
  `use` falls back to "Commercial" if not in `LAND_USES` (277).
- **Context** (`buildContext()`, 282-284): ids "c1".."c25"; cannot be assigned;
  excluded from every tally/export by construction (only `state.parcels` feeds
  computations).
- **Pillar**: `{id, name, color, icon, cost, metrics[], y1, y2, lt}`.
- **Metric**: `{label, factor, money?}`.
- **Scenario**: `{id, name, date, assignments: {parcelId→pillarId}}`
  (`saveScenario`, 586; `snapshotAssignments`, 554). Assignments only — cost
  overrides and pillar definitions are NOT captured in a scenario (noted as a
  planned change, `McNichols_DEMO_TODO.md:114-115`).
- **state** (286): `{parcels, context, pillars, scenarios, assume, filter,
  colorMode, selected, view}`.

### 3.3 Persistence schema — localStorage under `LS_KEY` (persist/restore, 289-300)

```js
{a:{parcelId→pillarId}, co:{parcelId→costOverride}, pillars:[...], assume:{...}, scenarios:[...]}
```

Restore merges: saved pillars replace defaults entirely if non-empty (295);
assume shallow-merges over defaults (296); assignments/overrides re-attach by
parcel id (297); id counters fast-forward past saved ids to avoid collisions
(295, 299).

### 3.4 Scenario share-file schema (`exportScenarios`, 555-559)

```js
{version:TOOL_VERSION, scenarios:[...], assume:{...}}   // downloaded as W-McNichols-scenario-share.json
```

## 4. Parcel identity strategy

- Runtime parcel ids are **sequential** — `par_id()` returns "r1","r2",…
  (line 251) in the array order of `DATA.inscope` (line 277). Identity is
  therefore POSITIONAL: it depends on the embedded dataset's ordering staying
  stable between sessions and between the v2 and offline builds. localStorage
  assignments (`o.a[p.id]`, 297) and shared scenario files
  (`s.assignments[pid]`, 587) both key on these positional ids.
  **Consequence:** reordering, adding, or removing a record in `DATA.inscope`
  would silently re-map every saved assignment. No assessor parcel number
  (APN) is stored.
- **Cross-source matching happens at data-preparation time, not runtime.** The
  assessor attributes (owner, use, value, floor area) and parcel geometry
  arrive already joined inside `DATA`. The join method is not in the repo —
  UNVERIFIED; the street address appears to be the working key (records carry
  only `address`, no APN). Commit c88392d documents a manual identity
  resolution: a condominium at 7303 had two unit records merged into one
  parcel with combined geometry and combined assessed value.
- **Building footprints are never joined to parcels.** They are a separate
  visual overlay layer (non-interactive, `interactive:false`, line 656).
  Identity between the Detroit and OSM footprint sources is resolved by
  centroid proximity dedup (§1.9 thresholds, lines 705-711).
- Scenario import collision handling is by scenario NAME: a duplicate name
  gains the suffix " (imported)" (565).

## 5. Error, gap, and missing-data handling

| Gap | Behavior | Where |
|---|---|---|
| No/zero assessed value (16 of 93 parcels) | Detail shows "Exempt / no value of record"; excluded from `curAssessed` sums; counted and disclosed in dashboard footnote ("{exemptAll} of {N} parcels are tax exempt or carry no assessed value…") and print report | 442, 484-487, 520, 780-781, 797 |
| No building of record (24 of 93) | Detail shows "No building of record"; floor area plays no computational role in this build | 448 |
| No owner | "Not available" | 445 |
| No zoning | "Not available" (in data, all 93 have B2) | 452 |
| Unknown land-use category | coerced to "Commercial" | 277 |
| Missing geometry | build report console warning; parcel simply not drawn on map; still fully functional in schematic/dashboard | 320-321, 739, 757 |
| Assigned pillar later deleted | assignment cleared on delete (859); defensive filter drops orphans from tallies (`committedParcels`, 407; `aggregateOutcomes`, 408; `scenarioTotals`, 599) |
| Metric factor 0 / negative sqft | outcome 0 (guards at 399-401); sqft coerced `Number(...)||0` throughout |
| localStorage unavailable | all persist/restore/cache wrapped in try/catch, silently degrades to in-memory session | 289-300, 662, 674-676 |
| Chart.js missing (offline first run) | dashboard renders tables/cards without charts (`typeof Chart==="undefined"` guard) | 529 |
| html2canvas missing | PNG export alerts and points to PDF path | 766 |
| All footprint sources fail | console warn; Buildings button disabled and relabeled "Buildings unavailable"; note updated | 719-722, 645-647 |
| Malformed scenario import | JSON parse alert; version/shape validation returns −1 → "not a scenarios export from this tool (version 2)" | 560-561, 578-580 |

## 6. Computation order and dependencies

1. `init()` (302): `buildParcels()` → `buildContext()` → `defaultPillars()` →
   stamp injection → `restore()` (localStorage overlays defaults) →
   `renderAll()` → `buildReport()` (console diagnostics) → first-run tour.
2. `renderAll()` (335) = renderLegend → renderFilters → renderSchematic →
   renderTally → renderNarrative → renderDetail → **persist()**. Every
   mutation funnels through a render call that ends in persist, so the stored
   state is always current; there is no dirty-tracking.
3. Mutations: `assign` (471), `setCost` (472), `setAssume` (473), pillar edits
   (854-859) — each calls `renderAll()` (or targeted renders) and, when the
   affected view is active, `renderMap()`/`renderDashboard()`/
   `renderPillarEditor()`.
4. **Everything is recomputed from scratch on every render; nothing is cached
   or memoized.** Scenario compare recomputes `scenarioTotals` per scenario per
   render (599-601) against CURRENT pillars/assumptions — so a saved scenario's
   dollars shift if assumptions change after saving (assignments are the only
   frozen part). The only caches in the system are localStorage state (§3.3)
   and the footprint cache (§8); Chart.js instances are destroyed and rebuilt
   each dashboard render (`destroyCharts`, 476, 530).
5. Map lifecycle: `ensureMap()` builds the Leaflet map once per session (629),
   fits bounds from all polygon points, else `DATA.bbox` (635-636), then
   `loadBuildings()` once (`bldTried` latch, 672).

## 7. Scenario mechanics

- Save (586): name prompt → snapshot of current assignments only.
- Load (587): overwrites every parcel's pillar from the scenario (parcels
  absent from the scenario get null).
- Compare (602-624): table over ALL saved scenarios — corridor mini-strip
  picture (`miniStrip`, 589-598), parcel count, investment, est. new annual
  property tax, then the union of outcome labels across scenarios with "-" for
  absent metrics (615-622).
- Share (555-585): JSON download / file-picker import; import requires
  `d.version` to be a string starting with "2" and `d.scenarios` to be an
  array (561); imports merge (never replace), rename on name collision, and
  may overwrite `assume` from the file (570).

## 8. Aerial imagery and building footprint handling

- Base layers (630-632): OSM raster tiles and Esri World_Imagery tiles;
  satellite on by default (`satOn=true`, 628), toggle swaps layers (724).
- Parcel polygons: in-scope drawn from `rings` at fillOpacity .78 colored by
  pillar/use/zoning (`parcelColor`, 367-371; 738-746); context in grey/green at
  .4/.5 (728-734); selected parcel gets dark 3px outline (742). Assigned
  parcels get a non-interactive emoji `divIcon` marker at the vertex-average
  centroid (736-737, 747-753).
- Footprints (`loadBuildings`, 671-723), order of precedence:
  1. localStorage cache (`BLD_CACHE_KEY`) — used verbatim, labeled
     "(saved copy)", never refreshed once present (675).
  2. City of Detroit ArcGIS FeatureServer — three candidate service names tried
     in order (`Buildings`, `Building_Footprints`, `building_footprints`,
     681-684) with an envelope query built from `DATA.bbox` returning GeoJSON
     (679); first success wins.
  3. OSM Overpass — three mirrors tried in order (693-695) with query
     `way["building"](bbox); out geom;` (691); results converted to GeoJSON
     Polygons (701). If Detroit data already loaded, OSM SUPPLEMENTS it:
     footprints whose centroid falls within the §1.9 thresholds of an existing
     one are dropped as duplicates, the rest are added (703-713).
  4. On any success the merged set is cached with its source label (662); on
     total failure the layer is disabled with user-visible notice (719-722).
- Rendering (648-658): GeoJSON Polygon/MultiPolygon → Leaflet polygons, ink
  outline at .75 opacity, .07 fill, non-interactive overlay above parcels.
- The offline build performs identically (same code); its inlined libraries
  remove the CDN dependency but tiles and first footprint fetch still require
  internet; the shared `BLD_CACHE_KEY` lets a cache captured in one build serve
  the other (commit 2a204e3).

## 9. Zoning and land-use ingestion and interpretation

- Zoning arrives as a per-parcel district string of record (all 93 = "B2");
  displayed read-only with "reference" badge (452), colored via
  `ZONING_COLORS` map with grey fallback (233-234), togglable color mode on
  schematic and map (359-363), legend states "All in-scope parcels are zoned
  B2 (local business). Reference data." (344). **Zoning is never interpreted
  or enforced** — no rule maps zoning to permitted pillars, density, or
  envelope (a B2 setback/envelope analysis is an explicitly deferred item,
  `McNichols_DEMO_TODO.md:27-28`).
- Land use is two-level: broad category `use` (drives color, vacancy logic,
  filters) and assessor `existing_use` string of record (display-only, 447).
  The category vocabulary and its 9 colors are fixed at line 232.
- The abandoned readiness checklist (see §11) contained the only zoning-aware
  logic ever present: a human-checked "Policy and zoning ready" flag.

## 10. AMI data integration and what it drives

`AMI_VALUE=95900` (line 230) drives exactly one artifact: the read-only
dashboard reference table (§1.8) of income bands and 30%-of-income monthly
housing costs (523-526, 548-552). It does NOT parameterize unit counts, rents,
eligibility, or any projection. An "AMI-aware housing pillar" that ties unit
counts and rents to AMI bands is a documented planned embodiment
(`McNichols_DEMO_TODO.md:25-26`).

## 11. Alternative approaches visible in the code and history

Preserved for claim breadth; none of this should be treated as deleted subject
matter.

1. **Readiness scoring (implemented, then removed 2026-06-29, commit
   336bbf3).** The original build (`git show 913a55a:McNichols_Kresge_DEMO.html`)
   scored each parcel on five boolean risk dimensions —
   funding / policy+zoning / stakeholder / environmental+title / timeline
   (`const READINESS`, 913a55a line 218) — with
   `rdScore(p)` counting checked flags, a percentage badge, and a
   red/amber/green threshold color: `rdColor(pct){return pct>=70?"#47AB4F":pct>=40?"#F1BA4B":"#D95448";}`.
   Readiness state persisted per parcel in localStorage. This is a parallel
   qualitative-risk axis alongside the quantitative projections — an
   alternative embodiment of decision support that could return in Tier 2/3.
2. **v1 vs v2 cost model.** Original `parcelCost` (913a55a:375):
   `(sqft)*(pl.cost)` — no per-parcel override, no sensitivity factor. The
   override + global factor chain is a second-generation refinement (336bbf3,
   edeee1a).
3. **Two coexisting builds of the same version** (online v2 vs OFFLINE with
   inlined libraries) — alternative packaging embodiments; plus the v1 file
   retained in-repo with a separate localStorage namespace ("…_v1" vs "…_v2"),
   demonstrating side-by-side version isolation.
4. **Three-candidate ArcGIS service-name fallback and three Overpass mirrors**
   (681-684, 692-696) — redundant-source acquisition strategy.
5. **Unused/vestigial code:** `findCtx`/context detail path duplicated between
   corridor and map panels (427, 763); `p.notes` displayed but sparsely
   populated; `DATA.bbox` fallback for fitBounds only used if no polygon
   exists (636, never in practice since all 93 have rings). `heightFor` uses a
   hard default of 3000 sqft when data absent (373, never in practice).
6. **No feature flags and no commented-out logic** exist in v2 (verified by
   read-through); the alternatives live in git history and in the TODO file
   rather than dead code.
7. **Wording/code divergence** on cost basis (building vs land sqft), §1.2 —
   evidence that a building-area cost basis is a contemplated variant; the
   development-modes plan below makes that explicit.

## 12. NOT YET BUILT — intended embodiments

Documented in `McNichols_DEMO_TODO.md` (committed 2026-07-03, extended
2026-07-06 and 2026-07-13) and, where noted, in conversation-derived roadmap
text inside that file. Each is described against the existing architecture so
a provisional can cover it with specificity.

1. **Development modes (rehab / new construction / demolition+new)**
   (TODO:21-24). A per-parcel `mode` field beside `costOverride`; `parcelCost`
   switches basis: rehab = existing `floorArea` × rehab $/sqft; new = proposed
   building sqft × new-construction $/sqft; demo+new adds a demolition line.
   The data foundation (floor_area, year_built per parcel) already ships in
   `DATA` (§3.1).
2. **AMI-aware housing pillar** (TODO:25-26). Housing metrics parameterized by
   AMI band: unit counts split across bands (30–120% of `AMI_VALUE`), band
   rents derived from the §1.8 affordability formula, feeding revenue and
   subsidy-gap lines in the pro forma below.
3. **Pro forma gap analysis** (TODO:32, "Preliminary pro formas; capital
   stack"). Per scenario: development cost (existing `totalInvestment`),
   stabilized income (money-type metrics per §1.1, e.g. Annual Revenue),
   supportable debt from income, equity, and the **gap = cost − (debt +
   equity)**; rendered as a dashboard card and per-scenario compare row using
   the same recompute-on-render pattern (§6.4). Assumption entry follows the
   existing `state.assume` + `setAssume` propagation path (§2.3).
4. **Funding fill-in (pipeline) tracking** (TODO:32, "funding pipeline
   status"). A per-scenario `sources[]` list ({name, program, amount, status:
   identified/applied/committed}) whose committed sum draws down the pro-forma
   gap; status rolls up to the compare table so funders see which plan is
   closest to fully funded. Persisted in the same localStorage/share-file
   schema (§3.3-3.4, with the share format's version gate bumped).
5. **Environmental screening, three rings** (TODO:39-70, design approved
   2026-07-06). Ring 0: `ENV_USE_FLAGS` mapping assessor use codes already in
   `existing_use` (dry cleaner, gas station, service/repair, car wash) to
   plain-language Phase-I-ESA screening flags in the parcel panel. Ring 1: a
   live EGLE Part 201/Part 213 point layer cloning the `loadBuildings()`
   pattern — bbox query, warning-style markers, localStorage cache with
   "(saved copy)" fallback, ~500 ft proximity lines in the parcel panel.
   Ring 2 (service, not software): records pulls, Phase I coordination,
   brownfield funding pathway.
6. **Architectural visualization, three altitudes** (TODO:72-107, design
   2026-07-13). (a) Map "proposed" mode: setback-respecting concept-massing
   rectangles tinted by pillar over existing footprints, before/after toggle;
   (b) street elevation tab: diagrammatic corridor wall from frontage +
   floor-area of record vs proposed massing in pillar colors; (c) per-site
   renderings produced outside the tool and attached to parcel detail /
   funder packet. All three read the same pillar assignments (single source
   of truth).
7. **Remaining TODO items:** clear-all-assignments control (TODO:5-8); tour
   updates (9-14); assessor vintage confirmation (15-16); calibrated
   projection coefficients (31); decision log + weighted criteria (33);
   phasing view of Year 1/2/3 capital needs and sensitivity stress tests
   (34); multi-page funder packet PDF export (35); study-grade millage-based
   tax modeling replacing the single effective rate (36); additional corridors
   (37); hosted deployment (110-111); multi-user shared workspace with a
   shared scenario database (112-113); embedding pillar definitions in the
   scenario share file so edited assumptions travel with scenarios (114-115).
8. **B2 buildable-envelope analysis** (TODO:27-28): zoning-interpretation
   layer computing setbacks/envelope per parcel — the first rule-based use of
   the zoning field (§9).

UNVERIFIED items in this section: none are implemented; all descriptions of
HOW they would work are architecture-consistent designs recorded in the repo's
TODO file (quoted locations given), except the pro forma debt-sizing detail in
item 3, which is the standard mechanism implied by "pro formas; capital stack"
but not spelled out in the repo.
