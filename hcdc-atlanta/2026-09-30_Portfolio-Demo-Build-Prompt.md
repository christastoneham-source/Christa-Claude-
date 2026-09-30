# Build Prompt — The Investment Map · Portfolio Demonstration (HCDC validation build)

Saved 2026-09-30. Paste everything between the lines into a NEW Claude Code
project. Strongly recommended: attach `Investment_Map_DEMO_WHITELABEL.html`
from this repo to that conversation as the reference implementation.

---

You are building a high-level working demonstration called **The Investment
Map · Portfolio Demonstration**. It extends a proven corridor decision tool
into site-level and deal-structure analysis. I am validating feasibility for
a client proposal, so this is an internal demonstration with stylized data,
not a client deliverable. I am a visual person: I need to click through every
feature, not read about it.

If I have attached a file named `Investment_Map_DEMO_WHITELABEL.html`, read
it first and reuse its engine patterns (state model, pillar objects, metric
factors, scenario snapshots, render-everything-on-change, localStorage
persistence, print export). If it is not attached, build from this spec alone.

## What it is

One self-contained HTML file. No backend, no build step, vanilla JavaScript.
A landing view opens on three workspaces. Each workspace is one live deal
type. One shared decision engine powers all three.

**Landing view.** Title: "The Investment Map". Tag: "Portfolio
Demonstration". One line: "One decision engine. Three live deal types.
Demonstration data." Three cards, one per workspace, each with a one-line
description and an Open button.

## Workspace 1: The District (a small Southern city)

A district revitalization study. About 40 stylized parcels drawn as a
schematic street grid or corridor band (no real addresses, label parcels
D-01, D-02, ...). Each parcel carries: land sqft, existing building sqft or
none, year built or none, assessed value or exempt, existing use.

- Assign editable investment pillars parcel by parcel (defaults: Housing,
  Commercial, Community and Education, Green and Public Realm; each has a
  color, an icon, cost per sqft by construction mode, and outcome metrics).
- Live totals: parcels assigned, estimated investment, outcomes, value
  created, new annual property tax.
- **Capital stack panel** (the new piece): per scenario, editable source
  lines: Public partner resources, Grants, Debt, Partner equity, HCDC
  equity. The panel always shows THE GAP: total cost minus committed
  sources, big and unmissable.
- **Role toggle: Advisor vs Equity Partner.** Advisor shows an advisory fee
  line and zero balance sheet exposure. Equity Partner moves HCDC equity
  into the stack and shows ownership share of projected value created. The
  toggle answers: what does it take for the gap to close, and what role does
  that imply?

## Workspace 2: The Five-Acre Site (single parcel)

One parcel, 217,800 sqft, with a small existing building. The scenario axis
here is DEAL STRUCTURE, not land use. Eight structure cards, each selectable
as the active scenario:

1. Buy outright (cash or debt)
2. Option contract with entitlement period
3. Ground lease
4. Fee developer
5. Joint venture, owner contributes land as equity
6. Phased takedown
7. Seller financing
8. Public conveyance or authority partnership

Each structure computes and displays: capital required day one, total
capital at completion, HCDC role, control timeline, risk level (Low, Medium,
High with color), income type (fee, equity return, both), and the capital
stack under that structure. A Compare view puts all eight in one table so
the tradeoff is visible at a glance. All assumption numbers are editable.

## Workspace 3: The Twenty Acres (bank-owned site, large metro)

One 871,200 sqft site owned by a bank. Two decisions on screen:

- **Subdivision concepts.** At least three preset concepts the user can
  switch between, drawn as a simple diagrammatic site plan (SVG or divs, no
  mapping library needed): (a) One parcel, single use. (b) Four to six lots,
  mixed use, user assigns a pillar per lot. (c) Three-phase takedown with
  phases shaded. Switching concepts recomputes everything. Compare table
  across concepts: investment, outcomes, value created, new annual tax.
- **Acquisition scenarios.** Price basis selector: market price, distressed
  or REO price, seller financing terms. The selection flows into every
  concept's numbers.

This workspace answers: should we buy it, what is highest and best use, and
should it stay one parcel or subdivide.

## Shared engine (all three workspaces)

- **Construction modes per parcel or lot:** Rehab (cost basis = existing
  building sqft), New Construction (cost basis = proposed building sqft, an
  editable input), Demolition plus New (adds a demolition cost per sqft
  line). Historic Preservation is a rehab variant that adds a historic tax
  credit line to the capital stack (placeholder 20 percent federal plus a
  state credit line, both editable).
- **Sustainability toggle per scenario:** adds an editable cost premium
  percentage, adds green outcome metrics (annual energy savings dollars,
  green building sqft), and adds unlockable funding lines to the stack
  (PACE financing, energy credits). Clearly labeled as planning assumptions.
- **Market profiles:** named assumption sets, switchable per workspace:
  "Small Southern City" and "Large Metro". Each profile sets a construction
  cost multiplier, a value factor, and an effective property tax rate. A
  visible chip always shows which profile is active. All values editable.
- **Projection math** (label everything as planning estimates, editable
  assumptions, never an appraisal or tax determination):
  - cost = basis sqft x cost per sqft x mode adjustment x market multiplier
  - count outcomes = floor(basis sqft / sqft-per-unit factor); dollar
    outcomes = basis sqft x dollars-per-sqft factor
  - value after investment = total investment x value factor
  - value created = value after investment minus current assessed value
  - new annual property tax = value after investment x effective tax rate
- **Scenarios:** save the current state of any workspace under a name, list
  saved scenarios with a small visual strip, load any scenario, and compare
  scenarios side by side in a table.
- **Partner Brief export:** a print-ready one-page brief for the active
  scenario: recommendation line, the key numbers, the capital stack, and
  the diagram. Framing: the client team keeps the instrument, partners
  receive the paper. Use the browser print dialog, no libraries required.
- **Edit Pillars view:** add, rename, recolor, reprice pillars and their
  outcome metrics at any time.
- **Persistence:** everything saves to localStorage and restores on reload.
- **Guided tour:** a short click-through tour, one step per major feature,
  that starts on first visit and can be reopened from a help button.

## Design system (non-negotiable)

Background cream #FCFAF1. Text ink #101C28. Accent colors in this fixed
order: Brick #D95448, Gold #F1BA4B, Grove #47AB4F, Turquoise #00BCC5.
Turquoise is the only action and link color. A four-dot mark (one dot of
each color, in order) sits beside the wordmark. One thin spectrum rule runs
Brick to Turquoise through Gold and Grove, never reversed. Headings in
Fraunces (Google Fonts, graceful fallback to Georgia). Body in Inter
(fallback to system sans). No em dashes anywhere in interface text. Footer:
"Connecting Dots and Strategies · Reclaiming the map. · Demonstration data."

## Language rules

Never use the words software, platform, product, AI-powered, or patent
pending. Say: instrument, decision environment, analysis, demonstration.
Every read-only figure of record gets a small "reference" badge. Every
projection carries "planning estimate, editable assumptions" language.

## Technical rules

Single HTML file. Chart.js from a CDN is allowed for dashboard charts but
the page must degrade gracefully without it (tables instead of charts). No
mapping library: the district and site plans are schematic (divs or inline
SVG). Works when opened from a local file with no internet except fonts and
charts. Keep it under 400 KB.

## Acceptance checklist (verify each before you finish, then show me)

1. Landing view shows three workspace cards and the exact title and line.
2. District: assign 5 parcels across 2 pillars, totals update live, the gap
   in the capital stack changes when a source line is edited.
3. District: Advisor vs Equity Partner toggle visibly changes the stack and
   the role summary.
4. Five-acre: all 8 structures selectable, each changes capital required,
   risk, and income type; the compare table shows all 8.
5. Twenty acres: switching the 3 subdivision concepts redraws the site plan
   and recomputes; assigning pillars per lot works in the mixed concept;
   REO vs market price basis changes the numbers.
6. Rehab vs New Construction vs Demo plus New produce different costs on
   the same parcel; Historic variant shows credit lines in the stack.
7. Sustainability toggle adds premium, green metrics, and funding lines.
8. Market profile switch changes costs, value, and tax figures visibly.
9. Save two scenarios, reload the page, both restore; compare table works.
10. Partner Brief prints one clean page for the active scenario.
11. Edit Pillars changes propagate to totals immediately.
12. The banned words appear nowhere; the brand system is applied throughout.

Work through the build, then walk me through the acceptance checklist with
screenshots so I can see every feature working.

---

## Note to self (not part of the prompt)

This demonstration stays internal until the provisional patent application
is filed. Do not host it or send it to HCDC or anyone else before filing or
before an engagement agreement with confidentiality language is signed. The
new mechanisms in it (deal structure scenarios, subdivision concepts, market
profiles, capital stack with role toggle) are claimable embodiments already
described in ip-disclosure/TECHNICAL-DISCLOSURE.md section 12.
