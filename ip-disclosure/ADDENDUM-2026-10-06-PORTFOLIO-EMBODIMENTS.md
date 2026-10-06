# ADDENDUM — Portfolio Edition Embodiments (for the provisional)

Prepared 2026-10-06. Attorney work product. Supplements
`TECHNICAL-DISCLOSURE.md` §12 (Not yet built — intended embodiments) and
`NOVELTY-CANDIDATES.md`. Source: prospective-client requirements gathered
2026-09-30 (HCDC, Atlanta) and the build specification committed the same day
(`hcdc-atlanta/2026-09-30_Portfolio-Demo-Build-Prompt.md`). Status of every
item: SPECIFIED IN WRITING, NOT YET REDUCED TO PRACTICE. Include these in the
provisional as described embodiments so the filing covers them before any
demonstration or client build exists.

These embodiments extend the implemented engine (TECHNICAL-DISCLOSURE §§1-10)
from one corridor to a portfolio of decision workspaces, and add a second
scenario axis: the DEAL STRUCTURE under which the operator enters a site, in
addition to the existing axis of WHAT USE goes on each parcel.

## A1. Multi-workspace portfolio architecture

A single decision instrument holding a plurality of workspaces, each bound to
its own parcel set (a district of many parcels, a single parcel, or one large
site subdivided into candidate lots), all powered by one shared projection
engine (the coefficient engine of §1.1-1.2), with per-workspace state
persisted under separate storage namespaces and a landing view enumerating
the workspaces. Mechanism: the existing `state` object (§3.2) becomes a map
of workspace states; `persist()/restore()` (§3.3) key on workspace id; all
compute functions (`parcelCost`, `impactFor`, `aggregateOutcomes`,
`totalInvestment`) operate unchanged on the active workspace's parcels.

## A2. Deal-structure scenario axis with role toggle

For a given site, a set of alternative entry structures (fee-simple purchase;
option contract with entitlement period; ground lease; fee-developer
engagement; joint venture with land contributed as owner equity; phased
takedown; seller financing; public conveyance) each modeled as a scenario on
the SAME parcel record, where the structure selection parameterizes: capital
required at day one and at completion, the operator's role, a control
timeline, a categorical risk level, an income type (fee, equity return, or
both), and the composition of the capital stack. A role toggle (advisor vs
equity partner) re-renders the stack and the operator's return line without
changing the underlying site program. Mechanism: a `structure` object per
scenario carrying coefficient overrides consumed by the same
recompute-on-render loop (§6.4); the compare table reuses the scenario
comparison pattern (§7) with structures as columns.

## A3. Capital stack with live gap computation

Per scenario, an editable list of funding source lines (public partner
resources, grants, debt, partner equity, operator equity, credit-derived
sources), where the instrument continuously displays GAP = projected total
development cost (the engine's `totalInvestment`) minus the sum of committed
source lines, recomputed on every edit, and where the gap figure drives the
advisory-vs-equity role analysis of A2. Historic-preservation and
sustainability variants (A4, A5) inject additional credit lines into the same
stack. This extends the funding fill-in tracking embodiment already described
in TECHNICAL-DISCLOSURE §12.4.

## A4. Construction-mode cost basis switching (per parcel)

Per parcel or lot, a mode selector in {rehabilitation, new construction,
demolition plus new construction, historic preservation}, where the mode
selects the COST BASIS: rehabilitation prices on the existing building floor
area of record (already carried per parcel, §3.1); new construction prices on
a user-entered proposed building area; demolition adds a per-sqft demolition
line; historic preservation is a rehabilitation variant that adds federal and
state historic tax credit lines to the A3 stack. This sharpens the §12.1
development-modes embodiment with the credit-line mechanics.

## A5. Sustainability scenario modifier

A per-scenario toggle that simultaneously (a) applies an editable cost
premium multiplier to the A4 cost computation, (b) appends sustainability
outcome metrics (annual energy savings in dollars, green building area) to
the pillar's metric set via the existing arbitrary-metric engine (§1.1,
§2.2), and (c) appends sustainability-contingent funding lines (assessed
clean-energy financing, energy credits) to the A3 capital stack — so one
toggle consistently moves cost, outcomes, and funding together.

## A6. Named market assumption profiles

Switchable, named assumption sets ("market profiles"), each carrying a
construction cost multiplier, a value factor, and an effective property tax
rate, applied at the workspace level so the same program priced in two
regions yields calibrated, comparable results. Mechanism: generalization of
the existing `state.assume` object (§2.3) from one anonymous set to named,
selectable sets, with the active profile displayed persistently. Directly
motivated by multi-state use (costs in one region price differently than
another).

## A7. Subdivision-concept comparison on a single site

For one large site of record, a plurality of stored subdivision concepts
(single parcel single use; N lots mixed use with per-lot pillar assignment;
phased takedown), each concept generating candidate lots as virtual parcel
records fed to the unchanged projection engine, with a compare table across
concepts (investment, outcomes, value created, new annual tax) answering
highest-and-best-use and subdivide-or-not questions quantitatively.
Acquisition price basis (market, distressed/REO, seller-financed) is a
scenario parameter flowing into every concept.

## A8. Partner brief export (output without instrument access)

A per-scenario, print-formatted one-page brief (recommendation line, key
projections, capital stack, site diagram) generated client-side from the
active scenario state, enabling the operating team to distribute conclusions
to counterparties WITHOUT granting access to the instrument, its assumption
set, or its full dataset. Extends the §12 funder-packet embodiment with the
access-asymmetry purpose stated explicitly.

## Filing notes for counsel

1. A1-A8 are described embodiments only; none is built as of 2026-10-06. The
   enabling detail is the mechanisms above plus the build specification of
   record (`2026-09-30_Portfolio-Demo-Build-Prompt.md`, committed to the
   repository 2026-09-30) and the implemented engine they extend.
2. The commercial driver is documented: a prospective client requested these
   capabilities on 2026-09-30 (pipeline card of record). No disclosure of
   these mechanisms has been made outside privileged and internal documents;
   the client conversation described needs, not mechanisms.
3. Claim-drafting posture: tie each claim to the concrete computational
   mechanism (cost-basis switching, label-keyed aggregation, gap recompute on
   edit, virtual-parcel generation from subdivision concepts) rather than the
   business outcome, consistent with the §101 framing in NOVELTY-CANDIDATES.
4. UNVERIFIED: nothing in this addendum has been tested in code; effort
   estimates and feasibility rest on the architecture mapping stated per item.
