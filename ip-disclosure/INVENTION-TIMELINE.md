# INVENTION TIMELINE — The Investment Map (W. McNichols Corridor Tool)

Prepared 2026-08-03 for provisional patent disclosure. Attorney work product.
All git output below is verbatim from the repository `christastoneham-source/Christa-Claude-`,
branch `claude/wizardly-meitner-eigjm9`. Where a date is inferred rather than
recorded in git, it is marked INFERRED.

---

## ⚠️ FLAG: EARLIEST PLAUSIBLE OUTSIDE DISCLOSURE

**Earliest date this project could plausibly have been shown to a person outside
the project: on or about 2026-07-03 (the Kresge Foundation demo).**

Evidence:

1. The tool itself is addressed to an outside party from its first commit. The
   guided tour text in the code reads "A quick tour of this corridor decision
   demo, built for The Kresge Foundation" (`McNichols_Kresge_DEMOv2.html:802`),
   and the PDF export header reads "Prepared for The Kresge Foundation"
   (`McNichols_Kresge_DEMOv2.html:792`). The same Kresge-facing language exists
   in the v1 file committed 2026-06-29 (commit 913a55a).
2. `McNichols_DEMO_TODO.md:2` (committed 2026-07-03 23:47 UTC) says: "Saved
   2026-07-03. Items deliberately NOT built before the Kresge demo" — written
   in anticipation of a demo.
3. An offline backup build was created 2026-07-03 23:28 UTC (commit 5f93f95,
   "Add offline backup build with Leaflet, Chart.js, and html2canvas embedded")
   — the kind of artifact prepared immediately before presenting in a room with
   uncertain internet.
4. The next commit after the 2026-07-03 cluster (24d2a64, 2026-07-06) defers new
   work "until contract," consistent with the demo having occurred between
   2026-07-03 and 2026-07-06.

**The demo date itself is NOT recorded in git.** UNVERIFIED: whether the demo
actually occurred, on what date, to whom, and whether under any confidentiality
understanding. The inventor should confirm the actual meeting date (calendar
entry, email) and whether any NDA or confidentiality expectation applied.
**Counsel should treat 2026-07-03 as the conservative earliest possible public
disclosure date** when computing the US one-year grace period (bar date on or
about 2027-07-03) and when assessing loss of foreign (absolute-novelty) rights.

Secondary disclosure vectors visible in the repo, each UNVERIFIED as to whether
it was exercised:
- The scenario Share/Load feature is designed to send files to other people
  ("sends it by email or Teams", `McNichols_Kresge_DEMOv2.html:609`).
- The one-pager prompt (`cds-investment-map-onepager-prompt.md`, 2026-07-13)
  references a marketing one-pager PDF that predates it and describes the
  offering publicly-facing language; whether that PDF was distributed is not
  in the repo.

---

## ⚠️ FLAG: THE INVENTION PREDATES THIS REPOSITORY

The first commit of the tool (913a55a, 2026-06-29) says it was **"forked from
ai-planner."** The predecessor "ai-planner" codebase is NOT in this repository.
Conception and some reduction to practice occurred before 2026-06-29 in that
predecessor. UNVERIFIED: the ai-planner repository's location, dates, and
contents. The inventor should preserve and produce that history to counsel; it
may move conception dates earlier (helpful) and may contain its own disclosure
events (must be checked).

---

## 1. Full commit history, oldest first

Command: `git log --reverse --date=iso --pretty=format:"%ad %h %s"`

Verbatim output:

```
2026-06-15 02:00:52 +0000 f8fe2a1 Add Harris County Heirs' Property Navigator design package
2026-06-15 02:16:30 +0000 4a21d86 Add 7811 Harrisburg RFP review workspace: workflow, templates, and reference materials
2026-06-15 02:30:48 +0000 eff0eba Add Lovable build prompt for the 7811 Harrisburg RFP reviewer platform
2026-06-29 06:00:50 +0000 913a55a Add McNichols Kresge corridor demo (forked from ai-planner, locked to W. McNichols, CDS rebrand)
2026-06-29 06:16:39 +0000 52c4e9c Add 24 not-in-scope context parcels to corridor schematic and map; keep them excluded from all tallies/exports
2026-06-29 06:32:21 +0000 336bbf3 Demo: editable pillars + per-parcel cost, existing assessor use, property value/tax-base impact on dashboard; remove readiness checklist
2026-06-29 06:49:12 +0000 edeee1a Add Marygrove Conservancy as green not-in-scope feature; add global cost-adjustment sensitivity; existing land use throughout
2026-07-03 18:57:38 +0000 354f07d Add v2 build: scenario export/import, provenance stamp + versioning, exempt-parcel handling, Kresge navy/gold chrome
2026-07-03 19:16:44 +0000 103ebc9 Scenarios: plain-language share/load + visual corridor strips + tax compare row; dashboard tax card; live building-footprint overlay
2026-07-03 19:30:33 +0000 3a2eb87 Add building floor area + year built of record to parcel detail; harden footprint layer with multiple sources; GIS Layers label
2026-07-03 21:46:05 +0000 c88392d Fix 7303 condo parcel: merge both unit geometries + combined assessed value; merge Detroit + OSM footprint sources with dedup
2026-07-03 23:28:32 +0000 5f93f95 Add offline backup build with Leaflet, Chart.js, and html2canvas embedded
2026-07-03 23:41:15 +0000 2a204e3 Cache building footprints in browser after first successful load; footprints then persist offline and across both builds
2026-07-03 23:47:16 +0000 2cbbfdf Add parked to-do list for the McNichols demo (post-Kresge work items)
2026-07-03 23:57:44 +0000 be44a89 Show pillar assignment symbols on Map View parcels
2026-07-06 01:25:58 +0000 24d2a64 Add approved environmental screening approach (EGLE-first, three rings) to demo TODO; build deferred until contract
2026-07-13 20:22:22 +0000 8ac46d8 Add architectural visualization alignment assessment (data vs rendering, three-views frame) to TODO
2026-07-13 23:37:44 +0000 353da8c Add Investment Map one-pager design prompt with brand alignment notes
```

## 2. First commit

- **Repository first commit:** 2026-06-15 02:00:52 +0000, f8fe2a1, "Add Harris
  County Heirs' Property Navigator design package." This commit is a DIFFERENT
  project (see Scope note below), not the Investment Map.
- **First commit of the invention:** 2026-06-29 06:00:50 +0000, 913a55a, "Add
  McNichols Kresge corridor demo (forked from ai-planner, locked to W.
  McNichols, CDS rebrand)" — adds `McNichols_Kresge_DEMO.html` complete with
  the pillar-assignment engine, cost/outcome projection, dashboard, scenarios,
  map, AMI reference, and readiness checklist already present. This confirms
  substantial pre-repository development (see flag above).

## 3. Capability first-appearance dates (traced by commit)

All dates documented in git unless marked otherwise.

| Date (UTC) | Capability first appears | Commit | Evidence |
|---|---|---|---|
| ≤2026-06-29 | Corridor schematic (frontage-scaled parcel band), 4 investment pillars, per-parcel pillar assignment, sqft-driven cost and outcome projection, live tally/narrative, dashboard charts, cost-per-outcome table, property value/tax projection inputs (valueFactor, taxRate), AMI reference table, scenario save/load/compare, Leaflet map with real parcel polygons + satellite, zoning color mode, PNG/PDF export, localStorage persistence, guided tour, readiness checklist (later removed) | 913a55a | file present in `git show 913a55a:McNichols_Kresge_DEMO.html`; features predate repo (ai-planner fork) |
| 2026-06-29 | Not-in-scope context parcels excluded from all tallies | 52c4e9c | commit message + `buildContext()` |
| 2026-06-29 | Editable pillars (user-defined pillar costs/metrics), per-parcel cost override, existing assessor use display, dashboard property value + tax base impact section; readiness checklist REMOVED | 336bbf3 | commit message; `parcelCost` gains `costOverride` |
| 2026-06-29 | Global cost-adjustment sensitivity factor (`assume.costFactor`) | edeee1a | commit message |
| 2026-07-03 | v2 file: scenario export/import (share file), provenance stamp + `TOOL_VERSION`, exempt-parcel handling | 354f07d | adds `McNichols_Kresge_DEMOv2.html` |
| 2026-07-03 | Visual corridor mini-strips in scenario compare, scenario tax compare row, live building-footprint overlay (Detroit open data) | 103ebc9 | commit message |
| 2026-07-03 | Building floor area + year built of record in parcel detail; multi-source footprint fallback | 3a2eb87 | commit message |
| 2026-07-03 | Multi-source footprint merge with centroid dedup (Detroit + OSM); condo multi-unit parcel merge | c88392d | commit message |
| 2026-07-03 | Offline backup build (libraries embedded) | 5f93f95 | adds `McNichols_Kresge_DEMO_OFFLINE.html` |
| 2026-07-03 | Browser cache of building footprints (offline persistence of fetched GIS data) | 2a204e3 | commit message; `BLD_CACHE_KEY` |
| 2026-07-03 | Pillar assignment symbols on map parcels | be44a89 | commit message |
| 2026-07-06 | Environmental screening design (three-ring architecture; documented, NOT built) | 24d2a64 | `McNichols_DEMO_TODO.md` |
| 2026-07-13 | Architectural visualization design (three-altitude frame; documented, NOT built) | 8ac46d8 | `McNichols_DEMO_TODO.md` |

## 4. References to demos, clients, deploys, share links, presentations

- Commit 913a55a (2026-06-29): "McNichols **Kresge** corridor demo" — client-named demo.
- Commit 336bbf3 (2026-06-29): "**Demo**: editable pillars..."
- Commit 354f07d (2026-07-03): "**Kresge** navy/gold chrome" — client-branded UI.
- Commit 103ebc9 (2026-07-03): "plain-language **share**/load".
- Commit 5f93f95 (2026-07-03): "offline **backup** build" (presentation contingency).
- Commit 2cbbfdf (2026-07-03): "parked to-do list for the McNichols **demo** (post-**Kresge** work items)".
- Commit 24d2a64 (2026-07-06): "build deferred until **contract**".
- In-code: "Prepared for The Kresge Foundation" (`McNichols_Kresge_DEMOv2.html:168, 792`), tour step "built for The Kresge Foundation" (`:802`).
- Branch names: `claude/wizardly-meitner-eigjm9` (this work), `claude/epic-bardeen-er1ai6` (a separate Heirs' Property web build for Houston Land Bank, 2026-06-15 — different project). No tags exist.

## 5. Deployment configuration, hosting config, public URLs

- **None found.** No Netlify/Vercel/GitHub Pages/hosting config files exist in
  the repository. `McNichols_DEMO_TODO.md:110-111` records a hosted link
  (Netlify) as a PLANNED item "when Kresge says yes" — i.e., not deployed as of
  2026-07-13.
- The tool loads libraries and map data from public CDNs/APIs at runtime
  (unpkg, cdnjs, Google Fonts, OSM/Esri tiles, Detroit ArcGIS, Overpass); these
  are inbound dependencies, not deployments of the tool.

## 6. Exported files, screenshots, PDFs, build artifacts in the repo

- `McNichols_Kresge_DEMO_OFFLINE.html` — build artifact (libraries inlined),
  added 2026-07-03 23:28 UTC (5f93f95). This is the only build artifact.
- No screenshots, no PDFs, no exported scenario JSON files are committed.
- The tool GENERATES exports at runtime (PNG `w-mcnichols-corridor.png` at
  `:776`, print-to-PDF report at `:777-798`, scenario share file
  `W-McNichols-scenario-share.json` at `:558`); none are stored in the repo.
- UNVERIFIED: a marketing one-pager PDF exists outside the repo (referenced in
  conversation and by `cds-investment-map-onepager-prompt.md`) — obtain and
  date it separately.

## 7. Chronology table

| Date | Milestone | Evidence | Documented or inferred |
|---|---|---|---|
| Before 2026-06-29 | Conception + first reduction to practice in predecessor "ai-planner" | Fork note in 913a55a commit message | INFERRED (predecessor repo UNVERIFIED, not in this repo) |
| 2026-06-15 | Repository created; two unrelated projects committed | f8fe2a1, 4a21d86 | Documented |
| 2026-06-29 | Investment Map v1 committed: full decision engine present (pillars, projections, dashboard, scenarios, map, AMI) | 913a55a | Documented |
| 2026-06-29 | Same-day iteration: context parcels, editable pillars, per-parcel cost override, value/tax projection UI, sensitivity factor; readiness checklist removed | 52c4e9c, 336bbf3, edeee1a | Documented |
| 2026-07-03 | v2: share files, provenance stamp, exempt handling, corridor-picture compare, live GIS footprints, floor area of record, offline build, footprint caching | 354f07d…be44a89 (7 commits) | Documented |
| ~2026-07-03/07 | Kresge Foundation demo (external showing) | TODO header; offline backup timing; "until contract" on 07-06 | INFERRED — confirm actual date |
| 2026-07-06 | Environmental screening architecture documented (intended embodiment) | 24d2a64 | Documented |
| 2026-07-13 | Architectural visualization architecture documented (intended embodiment); marketing one-pager prompt | 8ac46d8, 353da8c | Documented |

## Scope note

`README.md`, `docs/` (Harris County Heirs' Property Navigator) and
`hlb-7811-harrisburg-rfp/` (RFP review workspace), plus branch
`claude/epic-bardeen-er1ai6`, are separate projects that happen to live in the
same repository. They are OUT OF SCOPE for this disclosure and are not part of
the Investment Map invention. The repo's `README.md` describes the Heirs'
Property project, not the Investment Map.
