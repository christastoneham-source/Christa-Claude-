# DATA INVENTORY — The Investment Map

Prepared 2026-08-03. Attorney work product. Sources are listed as evidenced in
the repository only; no outside research was performed (per instructions).
File references are to `McNichols_Kresge_DEMOv2.html` (v2) unless noted; the
OFFLINE build contains the same data-source code with libraries inlined.

## 1. External data source table

| # | Source | What it provides | Access method | File / module that touches it | Format | Refresh method | Terms of use in repo? |
|---|---|---|---|---|---|---|---|
| 1 | City of Detroit Office of the Assessor (2026 extract) | Parcel ownership, existing use of record, land sqft, frontage, building floor area, year built, assessed value, zoning district, parcel boundary rings for 93 in-scope + 25 context parcels | Manual/offline extraction and join, method not in repo (UNVERIFIED) | Embedded as `const DATA`, v2 line 226; consumed by `buildParcels()` 276, `buildContext()` 282; attributed by `STAMP` line 228 | JSON embedded in HTML | None — static snapshot baked into the file; TODO:15-16 flags confirming the vintage year | No. RESEARCH REQUIRED |
| 2 | City of Detroit open data, ArcGIS FeatureServer (`services2.arcgis.com/qvkbeam7Wirps6zC`) | Building footprint polygons within corridor bbox | Live REST API query at runtime (`fetch`, GeoJSON out), 3 candidate service names | `loadBuildings()` 671-690 (`arcgisCandidates` 680-684, envelope query 679) | GeoJSON | Fetched once per browser, then localStorage-cached forever under `BLD_CACHE_KEY` (640, 662, 674-675) | No. RESEARCH REQUIRED |
| 3 | OpenStreetMap via Overpass API (3 mirrors: overpass-api.de, overpass.kumi.systems, maps.mail.ru) | Supplemental building footprints (`way["building"]`) | Live HTTP query at runtime | `loadBuildings()` 691-717 (`overpassMirrors` 692-696, dedup 705-711) | Overpass JSON → converted to GeoJSON (701) | Same cache as #2 | No, beyond the © OpenStreetMap attribution string on the tile layer (631). RESEARCH REQUIRED (ODbL) |
| 4 | OpenStreetMap raster tile server (`tile.openstreetmap.org`) | Street basemap tiles | Live tile requests via Leaflet | `ensureMap()` 631 | PNG tiles | Live per pan/zoom; not cached by the app | Attribution "© OpenStreetMap" set at 631; usage policy not in repo. RESEARCH REQUIRED |
| 5 | Esri ArcGIS Online World_Imagery (`server.arcgisonline.com`) | Satellite/aerial basemap tiles (default base layer) | Live tile requests via Leaflet | `ensureMap()` 632, `toggleSat()` 724 | JPEG/PNG tiles | Live per pan/zoom | Attribution "Esri" set at 632; license terms not in repo. RESEARCH REQUIRED |
| 6 | HUD FY2025 Median Family Income, Detroit-Warren-Livonia MI | Single AMI dollar figure used for the affordability reference table | Manually transcribed constant | `AMI_VALUE=95900`, line 230; `renderAmiTable()` 548 | Hard-coded number | Manual re-entry ("published yearly by HUD", TIPS.ami line 243) | No. RESEARCH REQUIRED (US federal data, expected public domain — verify) |
| 7 | Google Fonts (fonts.googleapis.com / fonts.gstatic.com) | Fraunces and Inter typefaces | Live CSS/font fetch | v2 lines 8-10 | WOFF2 | Live each load (v2); OFFLINE build note: font links remain remote in the offline file | No. RESEARCH REQUIRED (fonts themselves are OFL — verify) |
| 8 | unpkg.com CDN | Leaflet 1.9.4 JS + CSS | Live script/style fetch (v2 only; inlined in OFFLINE) | v2 lines 7, 222 | JS/CSS | Pinned version | License header embedded in OFFLINE build (BSD-2-Clause) |
| 9 | cdnjs.cloudflare.com CDN | Chart.js 4.4.1, html2canvas 1.4.1 | Live script fetch (v2 only; inlined in OFFLINE) | v2 lines 223-224 | JS | Pinned versions | License headers embedded in OFFLINE build (MIT) |
| 10 | Google Maps (www.google.com/maps/search) | Outbound "Open in Google Maps" links per parcel (no data ingested) | User-clicked hyperlink only | `detailHTML()` 455, `ctxDetailHTML()` 436 | n/a | n/a | n/a (outbound link; no API use) |

No API keys, tokens, or authenticated endpoints exist anywhere in the repo.
No scraping code exists; all live access is public HTTP APIs and tile servers.

## 2. Redistribution and resale analysis (repo evidence only)

For each source: does the REPO contain license terms, attribution
requirements, or commercial-resale restrictions?

1. **Detroit assessor extract (embedded `DATA`).** The repo contains no
   license or terms. It does contain self-imposed attribution/provenance: the
   `STAMP` string (line 228) credits "City of Detroit Office of the Assessor,
   2026" and is rendered on the map, PNG export, and PDF export. The embedded
   dataset includes personal names of parcel owners — note for counsel: these
   are public records, but they ARE redistributed inside the HTML file itself
   (anyone given the file receives all 93 owner names). **RESEARCH REQUIRED**
   (City of Detroit open data license, assessor data terms).
2. **Detroit ArcGIS building footprints.** No terms in repo. Footprint
   geometries are cached into the user's browser and, per commit 2a204e3,
   persist across builds; they are not committed to the repo itself.
   **RESEARCH REQUIRED.**
3. **OpenStreetMap data (Overpass footprints).** No terms in repo beyond the
   "© OpenStreetMap" attribution on the tile layer. OSM data is ODbL; ODbL is
   a share-alike DATA license — whether caching/merging OSM footprints with
   city data creates a "derivative database" with share-alike obligations is a
   real question for counsel. **RESEARCH REQUIRED (ODbL §4.4 derivative
   database analysis).**
4. **OSM tile server.** Attribution present (631). The public OSM tile server
   has a usage policy (heavy/commercial use discouraged) not present in the
   repo. Relevant if the tool is hosted commercially at scale. **RESEARCH
   REQUIRED.**
5. **Esri World_Imagery tiles.** Attribution string "Esri" present (632) but
   Esri's terms for World_Imagery generally require more than a bare "Esri"
   credit and may require an ArcGIS subscription for commercial apps. Nothing
   in repo. **RESEARCH REQUIRED — this is the most likely source to carry a
   commercial-use restriction.**
6. **HUD AMI figure.** Single transcribed number with in-app attribution
   (lines 230, 243, 524). **RESEARCH REQUIRED** (expected unrestricted as US
   government work — verify).
7. **Google Fonts.** No terms in repo. **RESEARCH REQUIRED** (Fraunces and
   Inter are expected SIL OFL 1.1 — verify; OFL permits commercial use).
8. **Leaflet / Chart.js / html2canvas.** The OFFLINE build embeds the
   libraries WITH their license headers — this is in-repo evidence:
   Leaflet BSD-2-Clause ("© 2010-2023 Volodymyr Agafonkin, © 2010-2011
   CloudMade", header in `McNichols_Kresge_DEMO_OFFLINE.html`), Chart.js MIT
   (chartjs.org header), html2canvas MIT (hertzen.com header). All three
   permit commercial redistribution with notice preservation. See
   LICENSE-RISK.md.

### RESEARCH REQUIRED list (terms not discoverable from the repo)

1. City of Detroit assessor data / open data portal license (sources 1, 2)
2. OpenStreetMap ODbL obligations for merged + cached footprints (source 3)
3. OSM tile server usage policy for hosted commercial use (source 4)
4. Esri World_Imagery commercial licensing (source 5)
5. HUD income-limit data terms (source 6)
6. Google Fonts / Fraunces / Inter font licenses (source 7)
7. unpkg and cdnjs CDN terms of service for production commercial apps (sources 8, 9)
