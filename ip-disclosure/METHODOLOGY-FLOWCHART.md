# METHODOLOGY FLOWCHARTS — The Investment Map

Prepared 2026-08-03. Attorney work product. Every node names the actual
function, constant, or file location in `McNichols_Kresge_DEMOv2.html` (line
numbers in labels). Companion to TECHNICAL-DISCLOSURE.md.

## 1. Master flow — raw inputs to the decision output

```mermaid
flowchart TD
  A1["Assessor extract: parcels, owners, uses,<br>values, geometry (pre-joined offline,<br>method not in repo - UNVERIFIED)"] --> D0["const DATA (line 226):<br>93 inscope + 25 context + bbox"]
  A2["HUD FY2025 MFI"] --> C1["AMI_VALUE=95900 (line 230)"]
  D0 --> B1["buildParcels() 276"]
  D0 --> B2["buildContext() 282"]
  P0["defaultPillars() 253:<br>4 pillars, $/sqft + metric factors"] --> S0
  B1 --> S0["state (286)"]
  B2 --> S0
  L0["localStorage LS_KEY (287)"] --> R0["restore() 293:<br>saved pillars, assume,<br>assignments, overrides, scenarios"]
  R0 --> S0
  S0 --> U0["USER: selectParcel() 425 -> assign(pid,plid) 471"]
  U0 --> K1["parcelCost() 404"]
  U0 --> K2["impactFor() 399"]
  K1 --> V1["Corridor: renderTally() 410 + renderNarrative() 418"]
  K2 --> V1
  K1 --> V2["Dashboard: renderDashboard() 477:<br>postValue, valueCreated, newTax (484-491)"]
  K2 --> V2
  C1 --> V2
  K1 --> V3["Scenarios: renderScenarios() 602<br>scenarioTotals() 599 + miniStrip() 589"]
  K2 --> V3
  S0 --> V4["Map: renderMap() 725 (polygons colored<br>by parcelColor() 367, pillar pins 747-753)"]
  V1 --> X1["exportPNG() 766 / exportPDF() 777<br>buildPrint() 778"]
  V3 --> X2["exportScenarios() 555:<br>W-McNichols-scenario-share.json"]
  U0 --> PS["persist() 289 -> localStorage"]
```

## 2. Data acquisition and normalization

Parcels, zoning, land use, ownership, and valuation are pulled and joined
BEFORE the code runs; the file ships with the joined result. AMI is a single
embedded constant. Only building footprints are acquired live.

```mermaid
flowchart TD
  subgraph OFFLINE_PREP["Data preparation (outside the repo - UNVERIFIED method)"]
    Z1["City of Detroit Office of the Assessor 2026 extract:<br>owner, existing_use, floor_area, year_built,<br>sqft, assessed, zoning (STAMP, line 228)"]
    Z2["Parcel boundary geometry (lat/lon rings)"]
    Z3["Manual fixes, e.g. 7303 condo:<br>2 unit records merged, values summed<br>(commit c88392d)"]
    Z1 --> J1["Join keyed by street address<br>(no APN stored) -> DATA.inscope[93]"]
    Z2 --> J1
    Z3 --> J1
  end
  J1 --> N1["buildParcels() 276-280:<br>Number() coercions; use fallback to<br>'Commercial' (277); side S/N; null-safe<br>assessed/floorArea/yearBuilt"]
  N1 --> ID1["par_id() 251: positional ids r1..r93<br>(identity = DATA array order)"]
  J1 --> N2["buildContext() 282: ids c1..c25,<br>kind grey/green, never assignable"]
  subgraph LIVE["Runtime acquisition (map only)"]
    F0["loadBuildings() 671"] --> F1{"cache in BLD_CACHE_KEY? (674)"}
    F1 -- yes --> F2["addBuildings(cache,'(saved copy)') 675"]
    F1 -- no --> F3["Detroit ArcGIS FeatureServer:<br>3 service names tried (681-684),<br>bbox envelope query (679)"]
    F3 --> F4["Overpass OSM: 3 mirrors (692-696),<br>way[building](bbox) (691)"]
    F4 --> F5["centroid dedup vs Detroit set:<br>0.00006 lat / 0.00008 lon (705-711)"]
    F5 --> F6["addBuildings() 648: draw + cache (662)"]
    F3 -- all fail --> F4
    F4 -- all fail --> F7["disable Buildings button (719-722)"]
  end
```

## 3. Investment pillar logic — every branch

```mermaid
flowchart TD
  A["assign(pid, plid) 471"] --> B{"plid null or 'null'?"}
  B -- yes --> C["p.pillar = null (clear)"]
  B -- no --> D["p.pillar = plid"]
  C --> E["renderAll() 335 (ends in persist() 289)"]
  D --> E
  E --> F["For each committed parcel:<br>committedParcels() 407 filters<br>p.pillar set AND pillar still exists"]
  F --> G["parcelCost(p,pl) 404"]
  G --> G1{"p.costOverride != null?"}
  G1 -- yes --> G2["cps = costOverride"]
  G1 -- no --> G3["cps = pl.cost (pillar default)"]
  G2 --> G4["cost = sqft x cps x assume.costFactor"]
  G3 --> G4
  F --> H["impactFor(p,pl) 399: per metric m"]
  H --> H1{"m.money?"}
  H1 -- "yes ($/sqft)" --> H2["outcome_$ = sqft x m.factor"]
  H1 -- "no (sqft/unit)" --> H3{"m.factor > 0?"}
  H3 -- yes --> H4["outcome_n = floor(sqft / m.factor)"]
  H3 -- no --> H5["outcome_n = 0"]
  G4 --> I["totalInvestment() 409 sums costs"]
  H2 --> J["aggregateOutcomes() 408:<br>accumulate by metric LABEL"]
  H4 --> J
  H5 --> J
  I --> K["Post-investment value (portfolio level):<br>postValue = invest x assume.valueFactor (489)"]
  K --> L["valueCreated = postValue - curAssessed (490)<br>curAssessed = sum assessed where >0 (484-485)"]
  K --> M["newTax = postValue x assume.taxRate (491)"]
  I --> N["Cost per outcome (540-544):<br>per pillar, non-money metrics only:<br>cpo = pillar invest / outcome total (0 if 0)"]
```

## 4. Assumption engine — entry, storage, override, propagation

```mermaid
flowchart TD
  D1["Pillar defaults: defaultPillars() 253<br>cost 250/300/80/220 $/sqft, metric factors"] --> S["state.pillars + state.assume (286)<br>assume = costFactor 1.0, valueFactor 1.0, taxRate 0.034"]
  D2["restore() 293: saved pillars REPLACE defaults;<br>assume shallow-merged"] --> S
  U1["Edit Pillars tab: renderPillarEditor() 832<br>updPillar() 854 (cost/name/color/icon)<br>updMetric() 855, addMetric() 856,<br>delMetric() 857, addPillar() 858, delPillar() 859"] --> S
  U2["Parcel panel: setCost(pid,v) 472<br>per-parcel costOverride ('' resets to null)"] --> S
  U3["Dashboard inputs 510-512 and Pillars input 834:<br>setAssume(k,v) 473 for costFactor,<br>valueFactor, taxRate"] --> S
  U4["Scenario import: applyImportedScenarios() 560<br>may OVERWRITE assume from file (570)"] --> S
  S --> P1["parcelCost() 404 reads costOverride,<br>pl.cost, assume.costFactor"]
  S --> P2["impactFor() 399 reads m.factor, m.money"]
  S --> P3["Value/tax (489-491, 601, 783) read<br>assume.valueFactor, assume.taxRate"]
  P1 --> R["Every render recomputes from state:<br>renderAll() 335, renderDashboard() 477,<br>renderScenarios() 602 - no memoization"]
  P2 --> R
  P3 --> R
  R --> W["persist() 289 writes pillars + assume +<br>overrides + assignments to localStorage"]
```

## 5. Scenario comparison — swap and recompute; cached vs recomputed

```mermaid
flowchart TD
  A["saveScenario() 586: prompt name -><br>snapshotAssignments() 554<br>FROZEN: assignments map only"] --> ST["state.scenarios[] -> persist() 289"]
  B["applyScenario(id) 587: every parcel gets<br>s.assignments[p.id] or null -> renderAll()"] --> LIVE["Live plan swapped in one step<br>(this is the use-for-use swap)"]
  ST --> C["renderScenarios() 602: for EVERY scenario<br>on EVERY render -> scenarioTotals(s) 599"]
  C --> C1["Rebuild parcel list from CURRENT parcels<br>+ frozen assignment ids; drop parcels/pillars<br>that no longer exist (599)"]
  C1 --> C2["RECOMPUTED LIVE against current<br>assumptions: totalInvestment() 409,<br>aggregateOutcomes() 408,<br>tax = inv x valueFactor x taxRate (601)"]
  C2 --> C3["Compare table 614-623: corridor picture<br>miniStrip() 589, parcels, investment, tax,<br>union of outcome labels ('-' where absent)"]
  X["exportScenarios() 555 -> JSON file"] --> Y["importScenarios() 574 -> parse -><br>applyImportedScenarios() 560:<br>version must start with '2' (561),<br>rename collisions ' (imported)' (565),<br>merge scenarios, adopt assume (570)"]
  Y --> ST
  NOTE1["CACHED: only the assignment snapshot<br>(and localStorage state / footprint cache).<br>RECOMPUTED: every dollar and outcome figure,<br>every render, from current assumptions."]
```

## 6. Portfolio rollup — parcel to dashboard across pillars

```mermaid
flowchart TD
  P["state.parcels (93)"] --> F["committedParcels() 407"]
  F --> A1["Per parcel: parcelCost() 404 + impactFor() 399"]
  A1 --> R1["invByP / parByP maps built per pillar name (531-533)"]
  A1 --> R2["aggregateOutcomes() 408: label-keyed union<br>across mixed pillars (mixed-use rollup)"]
  A1 --> R3["totalInvestment() 409"]
  R3 --> D1["Summary cards 493-499: parcels, investment,<br>value created, new annual tax, vacant % (480-482)"]
  R1 --> D2["Chart.js: bar cInv (535), doughnut cPar (536)"]
  R2 --> D3["bar cOut, non-money labels only (537-538)"]
  R3 --> D4["Cost-per-outcome table per pillar (539-545)"]
  R2 --> D4
  D0["AMI_VALUE 230"] --> D5["renderAmiTable() 548: read-only reference"]
  R3 --> D6["Value/tax table 514-521 + exempt-parcel<br>footnote (486-487, 520)"]
  D1 --> E["Exports: buildPrint() 778 replays the same<br>functions for the PDF; exportPNG() 766<br>stamps STAMP (228) onto the schematic image"]
```

## 7. Configuration flow — pillars and square-footage inputs

```mermaid
flowchart TD
  A["Edit Pillars tab: renderPillarEditor() 832"] --> B["updPillar(id,k,v) 854:<br>name / color / icon / cost $/sqft / y1 / y2 / lt"]
  A --> C["Metric editor: metricRow() 850<br>updMetric(id,i,k,v) 855: label, factor,<br>money checkbox toggles $-per-sqft vs sqft-per-unit"]
  A --> D["addMetric() 856 (default factor 1000)<br>delMetric() 857"]
  A --> E["addPillar() 858 (cost 150, Jobs/2000)<br>delPillar() 859: clears that pillar's<br>assignments from every parcel first"]
  A --> F["Global sensitivity input 834 -> setAssume('costFactor') 473"]
  G["Parcel sqft: fixed reference data from DATA<br>(sqft, frontage per assessor record) - the tool has<br>NO input to change parcel square footage; the only<br>sqft-side lever is each metric's sqft-per-unit factor<br>and each pillar's $/sqft cost"] --> H
  B --> H["persist() 289 + rerender: renderFilters() 351,<br>renderSchematic() 374, renderTally() 410,<br>renderDetail() 427, renderDashboard() 477 if active"]
  C --> H
  D --> H
  E --> H
  F --> H
```

Note on diagram 7: the disclosure request asked "how square footage inputs are
changed." In this build parcel square footage is immutable assessor reference
data (`DATA`, line 226); user-changeable square-footage-related inputs are the
metric factors (sqft per unit) and pillar/parcel costs per sqft, as drawn. A
proposed-building-sqft input is part of the planned development-modes
embodiment (TECHNICAL-DISCLOSURE.md §12.1), not this build.
