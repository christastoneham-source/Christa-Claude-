# LICENSE RISK — The Investment Map

Prepared 2026-08-03. Attorney work product. Scope: every third-party
dependency of the Investment Map files (`McNichols_Kresge_DEMO.html`,
`McNichols_Kresge_DEMOv2.html`, `McNichols_Kresge_DEMO_OFFLINE.html`). The
tool has NO package manager, NO package.json, NO vendored node_modules — its
complete dependency surface is three JavaScript libraries, two font families,
and the runtime data/tile services covered in DATA-INVENTORY.md.

## 1. Dependency table

| Dependency | Version | Purpose | How included | License | Evidence | Copyleft? | Commercial restriction? |
|---|---|---|---|---|---|---|---|
| Leaflet | 1.9.4 | Interactive map, polygons, tiles, markers | CDN `unpkg.com` (v2 lines 7, 222); source inlined in OFFLINE build | BSD-2-Clause | In-repo header in OFFLINE build: "Leaflet 1.9.4, a JS library for interactive maps. https://leafletjs.com" with copyright lines (Volodymyr Agafonkin / CloudMade). BSD-2 identification from the library's standard licensing — UNVERIFIED in repo beyond the header (the full BSD text travels in Leaflet's distribution comment) | No | No — permissive; requires copyright-notice retention |
| Chart.js | 4.4.1 | Dashboard bar/doughnut charts | CDN `cdnjs.cloudflare.com` (v2 line 223); inlined in OFFLINE | MIT | In-repo header in OFFLINE build: "Chart.js v4.4.1 … Released under the MIT License". Bundled `@kurkle/color` also MIT (header link github.com/kurkle/color) | No | No |
| html2canvas | 1.4.1 | DOM-to-PNG capture for PNG export and PDF report image | CDN `cdnjs.cloudflare.com` (v2 line 224); inlined in OFFLINE | MIT | In-repo header in OFFLINE build: "html2canvas 1.4.1 <https://html2canvas.hertzen.com> Copyright (c) 2022 Niklas von Hertzen … Released under the MIT License" | No | No |
| tslib (bundled inside html2canvas) | n/a | TypeScript runtime helpers | Transitively inlined in OFFLINE | 0BSD | In-repo header: "Copyright (c) Microsoft Corporation." (tslib's standard 0BSD grant; exact SPDX UNVERIFIED in repo — the header text present is the permission notice) | No | No |
| Fraunces (font) | via Google Fonts | Display/heading typeface | CSS link, live fetch (v2 line 10; OFFLINE still fetches fonts remotely) | Expected SIL OFL 1.1 — UNVERIFIED (no license in repo) | RESEARCH REQUIRED | OFL is copyleft-for-fonts only (derivative FONTS must be OFL); does not affect the app | No for embedding/use |
| Inter (font) | via Google Fonts | Body/UI typeface | Same | Expected SIL OFL 1.1 — UNVERIFIED | RESEARCH REQUIRED | Same as above | No for embedding/use |

Runtime services (not code dependencies; full detail in DATA-INVENTORY.md):
OSM tiles + Overpass data (ODbL — see §3), Esri World_Imagery tiles (terms
RESEARCH REQUIRED), Detroit ArcGIS open data (RESEARCH REQUIRED), Google Fonts
CDN, unpkg/cdnjs CDN terms (RESEARCH REQUIRED), HUD AMI figure (RESEARCH
REQUIRED, expected public domain).

The other projects in this repository (`docs/`, `hlb-7811-harrisburg-rfp/`)
are documentation-only (Markdown) with no code dependencies, and are out of
scope for this disclosure.

## 2. Copyleft flags

- **No GPL, AGPL, LGPL, MPL, or other code copyleft anywhere in the
  dependency surface.** All three JS libraries are permissive (BSD-2/MIT).
- **SIL OFL (fonts):** copyleft applies only to derivative font software, not
  to documents or apps using the fonts. No obligation triggered by this tool's
  usage pattern. (Verify the Google Fonts serving terms — RESEARCH REQUIRED.)
- **ODbL (OpenStreetMap DATA) — the one real share-alike consideration.** The
  tool (a) renders OSM tiles with attribution (v2:631), and (b) fetches OSM
  building footprints via Overpass, MERGES them with City of Detroit
  footprints after centroid dedup (v2:701-713), and caches the merged set in
  the user's browser (v2:662). ODbL requires attribution and, for publicly
  "used" derivative databases, share-alike of the derivative database. Counsel
  question: is the merged, cached footprint set a "derivative database" that
  is "publicly used" when the tool is sold/hosted? Mitigations if needed are
  cheap (attribute OSM in the footprint note, or drop the OSM supplement and
  use city data only). This does not encumber the tool's CODE or its
  inventive method — it touches only the footprint overlay data.

## 3. Does anything block selling this as hosted software?

**From the code dependencies: no.** BSD-2 and MIT expressly permit commercial
use, resale, and hosting; the only obligation is preserving copyright/license
notices — already satisfied in the OFFLINE build (headers retained) and
satisfied for the CDN build by not redistributing the libraries at all.

**From the data/services layer: three items need resolution before commercial
hosting, none of which look structural:**

1. **Esri World_Imagery tiles** (the default basemap) — most likely to require
   a paid ArcGIS plan or richer attribution for commercial apps. Fallback
   exists in-product (OSM basemap toggle, v2:724). RESEARCH REQUIRED.
2. **OSM tile usage policy + ODbL share-alike** for the merged footprint cache
   (§2). Fixable with attribution and/or source selection. RESEARCH REQUIRED.
3. **City of Detroit assessor/open-data terms** for redistributing parcel
   records (including owner names) inside a commercial deliverable. The tool
   already carries the provenance stamp (v2:228). RESEARCH REQUIRED.

Plain statement: **nothing in the repository imposes a copyleft or
non-commercial restriction on the inventive software itself; the open
questions are all data-service terms (Esri, OSM/ODbL, City of Detroit), each
of which has an in-architecture fallback or a trivial attribution fix.**

UNVERIFIED items: exact SPDX texts for Leaflet/tslib beyond the headers quoted
(the repo carries headers, not full LICENSE files, for the inlined libraries);
all RESEARCH REQUIRED rows above. Per instructions, no online license research
was performed.
