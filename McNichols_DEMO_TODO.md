# W. McNichols Demo — Parked To-Do List
Saved 2026-07-03. Items deliberately NOT built before the Kresge demo, in rough priority order.

## Quick wins (minutes each, do after the meeting)
1. **"Clear all assignments / Start fresh" button.** Today a pillar can only be
   unassigned one parcel at a time. Add a toolbar button (with a confirm prompt)
   that clears every assignment at once. Consider a companion "save current as
   scenario first?" nudge so no plan is lost by accident.
2. **Update the help / guided tour for the new features.** The tour predates
   several additions. Add or update steps for: scenario Share/Load (the share
   file), the corridor picture in scenario compare, the Buildings layer and its
   saved-copy behavior, building floor area / year built on the parcel panel,
   exempt-parcel handling, the property value + tax base impact section, the
   cost adjustment (sensitivity) control, and Edit Pillars.
3. **Assessor data year.** The provenance stamp says 2026; confirm the actual
   vintage of the assessor extract and correct the one string if needed.
4. **Active tab color.** Active tabs are cream-on-navy; switch to gold if
   preferred after seeing it next to the proposal site.

## Demo-adjacent, hold for engagement scoping
5. **Development modes: rehab vs. new construction vs. demo + new.** Per-parcel
   mode selector; cost keyed to BUILDING sqft (existing for rehab, proposed for
   new) instead of land sqft; separate $/sqft per mode. Data foundation already
   in the tool (floor area + year built of record).
6. **AMI-aware housing pillar.** Tie unit counts and rents to AMI bands; feeds
   the pro forma. Explicitly Tier 2 calibration work.
7. **B2 setback / buildable-envelope note or analysis.** Light read-only note is
   cheap; real envelope math belongs in the paid site-planning tier.

## Tier 2 / Tier 3 inventory (sell, don't give away)
8. Calibrated projection coefficients (validated to the Foundation's standard).
9. Preliminary pro formas; capital stack; funding pipeline status.
10. Decision log + weighted decision criteria.
11. Phasing view (Year 1/2/3 capital needs); sensitivity stress tests.
12. Funder packet export (multi-page per-scenario PDF grant attachment).
13. Tax-base payoff at study grade (millage detail, not the demo estimate).
14. Additional corridors loaded and maintained.

## Environmental screening — approved approach (planned 2026-07-03, build after contract)
Decision: plan only for now; demo files unchanged. v1 live source: **EGLE Part 201
contamination sites + Part 213 LUST** (FEMA flood zones and EPA facilities are
later adds). Estimated effort: one working session, mirroring the
building-footprint pattern.

**Three rings:**
- **Ring 0 — embedded use-based flags (offline, no new data).** `ENV_USE_FLAGS`
  maps assessor uses of record already in the tool to plain-language screening
  flags: Dry Cleaner (7546) → solvents; Gas Station (8930) → underground storage
  tanks; Service & Repair (7100, 7591, 7642) → solvents/waste oil; Car Wash
  (7101, 8540). Shown in the parcel panel as "Environmental screen" with a
  REFERENCE badge. Screening language only — "typically examined in a Phase I
  ESA" — never a score or determination.
- **Ring 1 — live EGLE layer with cache (clone of loadBuildings).** New
  "Environmental" toggle in the map Layers row; `loadEnv()` queries
  `gisagoegle.state.mi.us/arcgis/rest/services/EGLE/RRDOpenData/MapServer`
  (Part 201 + LUST layers) by corridor bbox; distinct warning-style point
  markers (never pillar/land-use colors); tooltip = site name + program +
  "reference data of record"; localStorage cache with "(saved copy)" fallback,
  identical to `BLD_CACHE_KEY`. Parcel panel gains "Regulated site of record
  within ~500 ft" proximity lines from the cached points.
- **Ring 2 — the paid Tier 2 work (never in the tool).** Records pulls
  (EGLE RIDE/BEA), Phase I ESA coordination, brownfield funding pathway
  (EPA assessment grants, EGLE brownfield grants/loans, Act 381 TIF),
  remediation line item in the pro forma. Demo line: "the tool spots the
  question; the engagement answers it."

Build order when signed: Ring 0 flags → Ring 1 layer + cache → proximity lines →
tour/provenance updates → offline rebuild → mocked-fetch + offline tests
(same harness and Playwright patterns as the footprint layer). Note: EPA's
EJScreen is excluded (taken offline in 2025; mirrors unstable).

## Platform / operations
15. **Hosted link** (Netlify drag-and-drop; password protection; custom domain)
    so the tool is a URL, not a file. ~30 minutes, do when Kresge says yes.
16. **Shared workspace** (accounts, one shared scenario database — Lovable +
    Supabase path). The Tier 2/3 answer when they ask for real-time collaboration.
17. Scenario share-file could optionally embed pillar definitions too, so edited
    pillar costs travel with shared scenarios (today only assumptions travel).

## Known behaviors to remember (not bugs)
- Building footprints load live (Detroit open data → OpenStreetMap fallback) and
  are then cached in the browser; per-computer, per-browser; cleared browsing
  data clears the cache (reload once online to restore).
- Footprint coverage has real gaps where neither public source has traced a
  building; assessor floor area on the parcel panel is the more complete record.
- Fonts fall back to system serif/sans when offline (by design).
