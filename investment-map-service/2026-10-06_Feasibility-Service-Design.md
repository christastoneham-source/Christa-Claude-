# The Investment Map Feasibility Service: Feature Evaluation, Service Design, and Methodology Protection

Prepared 2026-10-06 for Christa D. Stoneham, Connecting Dots and Strategies. Internal. Confidential.

Source note: the conversation with Ahmed is not in any file available to this session. This design is built from Christa's description (a full feasibility study, the attorney's role, the specialist's role) and the Investment Map record in this repository. Correct anything that differs from what was discussed.

## 1. The advice in brief

1. **Today the instrument answers "what could we do here, and what would it return." A feasibility study answers "can we actually do it."** The gap is the evidence the instrument does not yet hold: title and legal, environmental, physical site, market value, real construction cost, and a full pro forma.
2. **Do not make the instrument do the specialists' work. Make it the place where their findings land and change the answer.** That is the central design move: a Findings Ledger feeding Feasibility Gates. It also turns out to be your strongest protection anchor yet (section 5).
3. **Your original build already had the skeleton.** The readiness checklist removed on 2026-06-29 scored each parcel on five dimensions: funding, policy and zoning, stakeholder, environmental and title, timeline (`const READINESS`, commit 913a55a). Bring it back, upgraded from hand-checked boxes to gates set by evidence.
4. **Every number should show how much it can be trusted.** Mark each figure as Planning placeholder, Specialist estimate, or Verified. Funders and boards will see at a glance what is assumption and what is fact. No conventional tool does this, and it is the feature most likely to win the room.

## 2. Service architecture: Screen, Verify, Decide

[[DIAGRAM]]

**Stage 1 · Screen (CDS alone, days).** The instrument runs on records of record. Pillar and structure scenarios, use-based environmental flags, first-pass value and tax base. Output: a shortlist of sites and scenarios, plus the specific questions each specialist must answer. This is the Investment Map as it exists today, sharpened.

**Stage 2 · Verify (CDS leads, specialists engaged per site, weeks).** Seven workstreams, each owned by a named role:

| Workstream | Owner | What it settles | How it moves the model |
|---|---|---|---|
| Title and legal | Attorney | Ownership chain, liens, easements, deal-structure documents, credit eligibility | Can block a structure, add cost or months, clear the Site Control gate |
| Zoning and entitlement | Attorney, with planner | Permitted uses, variances needed, entitlement path and timeline | Can block a pillar on a parcel, add months, clear the Entitlement gate |
| Environmental | Environmental professional | Phase I ESA; Phase II if triggered | Adds a remediation cost line, clears or fails the Environmental gate |
| Physical site | Surveyor, civil engineer, architect (Christa) | Survey, utilities, access, buildable envelope, test fit | Replaces assumed building area with the tested area |
| Value and market | Appraiser, market analyst | As-is value, absorption, rents, comparables | Replaces the planning value factor with a defended number |
| Cost | Cost estimator or general contractor | Priced construction estimate | Replaces the $/sqft placeholder |
| Financial and community | CDS | Pro forma, capital stack, gap, stakeholder map | Clears the Financial and Community gates |

**Stage 3 · Decide (CDS, one workshop per site).** The team runs verified scenarios live, records the decision in a decision log, and leaves with the roadmap and partner briefs.

### How a specialist finding enters the instrument

Each finding is a structured record: site and parcel, workstream, specialist, date, finding type (constraint, cost, value, timeline, pass or fail), the model effect, and the attached report. Effects the instrument applies:

- **Adjust a cost line** (remediation, demolition, utility extension)
- **Set a value** (appraised as-is value replaces assessed value as the baseline)
- **Add timeline months** (entitlement path, title cure)
- **Block an option** (zoning prohibits a pillar on this parcel; title defect blocks a structure)
- **Set a gate status** (Clear, Conditional, Fail)

Each affected figure then rises one step on the confidence ladder, from Planning to Specialist to Verified, and the change is logged with its source.

### The six Feasibility Gates (readiness, reborn)

Site Control and Title · Entitlement and Zoning · Environmental · Physical Feasibility · Financial (the gap closes) · Community and Partners. Each gate reads Not started, In review, Clear, Conditional, or Fail, and is set by findings, not by hand. The rules for when a gate clears are yours alone (section 5).

## 3. Feature evaluation

Ranked by value to a feasibility service. Effort is relative to the current engine. Protection is the layer that guards each feature.

| # | Feature | What it adds | Value | Effort | Protection |
|---|---|---|---|---|---|
| 1 | Findings Ledger | Specialist findings become structured inputs that move the model | Very high | Medium | Patent anchor + trade secret (finding taxonomy) |
| 2 | Feasibility Gates | Readiness reborn, driven by evidence | Very high | Low to medium (prior code exists) | Trade secret (gate rules) + patent embodiment |
| 3 | Confidence ladder | Every figure marked Planning, Specialist, or Verified | High | Low | Patent embodiment; strongest differentiator |
| 4 | Specialist work-order generator | Produces each specialist's scope of work, pre-filled with site data and the exact questions the model needs answered | High | Low to medium | Trade secret (scope templates) + patent anchor |
| 5 | Full pro forma, capital stack, gap | The financial answer a feasibility study must give | Very high | Medium | Template as trade secret; math is conventional |
| 6 | Development modes incl. historic | Rehab vs new vs demo plus new; historic credits | High | Low to medium | Already in Addendum A4 |
| 7 | Invalidation alerts | A saved scenario is flagged when a new finding or an outside record contradicts its assumptions | High | Medium | Patent anchor (the "outside the software" element) |
| 8 | Environmental screening ring | Regulated-site layer from state databases, with proximity | High | Medium | Patent anchor; already designed |
| 9 | Market profiles | Alabama prices differently than Atlanta | High | Low | Trade secret (the values) |
| 10 | Deal structures + role toggle | Buy, option, ground lease, fee developer, JV, and more | High | Medium | Addendum A2 |
| 11 | Subdivision concepts | One site, several lot plans compared | Medium to high | Medium | Addendum A7 |
| 12 | Partner brief and funder packet | Paper for partners, the instrument stays with the client | Medium to high | Low to medium | Addendum A8 |
| 13 | Decision log + weighted criteria | Why the choice was made, on record | Medium | Low | Conventional |
| 14 | Phasing view | Year 1, 2, 3 capital needs | Medium | Medium | Conventional |
| 15 | AMI-aware housing pillar | Units and rents by income band | High for housing clients | Medium | Already designed |
| 16 | Calibration loop | Actual outcomes tune the coefficients over time | High, long term | High | Trade secret + patent anchor |
| 17 | External record monitoring | Watches assessor and regulatory changes | Medium | Medium to high (needs hosting) | Patent anchor |

**Build next: features 1 through 5.** Together they turn the demonstration into a feasibility service. Everything else is already designed, already in your disclosure addenda, or can follow.

## 4. Roles and how the money flows

**The attorney.** A named workstream in Verify. Legal findings enter the ledger as findings, and CDS never states legal conclusions itself. Consider having the client retain the attorney directly while CDS coordinates: attorney-client privilege belongs to the client, and so does the liability. This is a structure question for your own attorney to confirm.

**The specialists.** There are two ways to engage them:

- **Client engages, CDS coordinates.** Use this for the appraiser, the environmental professional, and the surveyor. Lenders typically require reliance on appraisals and Phase I reports addressed to them, so the client or the lender usually needs to be the party engaging these specialists.
- **CDS subcontracts.** Use this for soft studies such as the cost estimator, the market analyst, and test fits. CDS holds the contract, controls the timeline, and can carry a coordination margin, but it also carries more responsibility.

**Specialists as buyers and referrers.** Land use attorneys, appraisers, environmental firms, CDFIs, and lenders see many deals. They could refer clients or license screening capacity. This is an interpretation of "a specialist who needs this service" and is worth confirming against the Ahmed conversation.

Fees, margins, and pricing are Christa's call. This design sets the structure only.

## 5. Protecting the methodology

**Name the method.** Use "The Investment Map" for the instrument and a named method for the service, for example Screen · Verify · Decide. One trademark filing covers the instrument name, and the method name can follow. The name is what the market remembers, and the trademark protects it.

**Trade secret: the core protection of the methodology.** This layer guards the rules, which the patent never would:

- the coefficient library and market profile values
- the gate rules (what clears, what fails, what is conditional)
- the finding taxonomy and model-effect rules
- the specialist scope-of-work templates
- the pro forma and capital stack template

Practices that keep them secret: store them in one restricted location marked Confidential; demonstrations use stylized numbers only; never place them in a patent filing (a patent publishes everything in it); client deliverables show outputs, never the rules that produced them.

**Contracts.** Two documents, both reviewed by your attorney:

- **Client license.** Internal use only, no reverse engineering, no sublicensing, no partner access to the instrument. The client owns its data and its outputs. CDS owns the instrument, the method, and the templates.
- **Specialist teaming terms.** Confidentiality. CDS owns the instrument and its templates. The specialist owns their professional report and licenses CDS to enter its findings into the instrument. Non-circumvention of the client for a set period. No reuse of CDS templates.

**Copyright.** Register the code (you are doing this yourself). The scope-of-work templates and report formats are also copyrighted works.

**Patent.** The Findings Ledger, gates set by findings, the confidence ladder, the work-order generator, and invalidation alerts are the strongest "outside the software" anchors yet. The system sends structured work orders to outside professionals, takes in their findings, and changes scenario state and alerts as a result. That interaction with real-world professional processes is the kind of element your attorney described. These are written up as patent embodiments in `ip-disclosure/ADDENDUM-2026-10-06b-FEASIBILITY-EMBODIMENTS.md`. They are still subject to the section 101 question, so the specialist opinion governs.

## 6. Recommended sequence

1. **Protect first.** Hand the specialist patent practitioner the August package plus both October addenda. If there is a path, file the provisional before building or showing any of this. The deadline is about 2027-05-04.
2. **Build features 1 through 5 into the Portfolio demonstration.** A paste-ready addition to the build prompt is below.
3. **Pilot one real feasibility engagement.** HCDC's 20-acre Atlanta and Decatur site is the natural candidate. Real specialists and real findings make it the first full Screen · Verify · Decide engagement, and they also reduce the invention to practice.
4. **Paper the roles.** Get the specialist teaming terms and the client license language drafted and reviewed by your attorney before the pilot starts.

## 7. Build prompt addition (paste after the Shared Engine section of the Portfolio build prompt)

```
FEASIBILITY LAYER (add to all three workspaces)
- Findings Ledger: a panel listing structured findings per site. Each finding
  has: parcel or lot, workstream (Title and Legal, Zoning and Entitlement,
  Environmental, Physical Site, Value and Market, Cost, Financial and
  Community), specialist role, date, type (constraint, cost, value,
  timeline, pass or fail), and a model effect. Supported effects: add or
  change a cost line, set a value, add timeline months, block a pillar or a
  deal structure on a parcel, set a gate status. Adding a finding
  recomputes everything immediately. Preload 4 sample findings per
  workspace with stylized demonstration data.
- Feasibility Gates: six gates per site (Site Control and Title,
  Entitlement and Zoning, Environmental, Physical Feasibility, Financial,
  Community and Partners), each reading Not started, In review, Clear,
  Conditional, or Fail, set by findings, shown as a row of status chips at
  the top of each workspace. Financial clears automatically when the
  capital stack gap is zero or less.
- Confidence ladder: every displayed cost, value, and outcome figure
  carries a small marker: Planning (grey), Specialist (gold), Verified
  (grove green). A figure rises when a finding sets it. A legend explains
  the three levels.
- Work orders: for any workstream, a "Prepare work order" button produces
  a print-ready one-page scope for that specialist, pre-filled with the
  site data and the specific questions whose answers the model needs.
- Invalidation alerts: when a new finding contradicts an assumption a
  saved scenario relied on, that scenario shows an alert badge in the
  Scenarios list with a one-line reason.
Acceptance: add a zoning finding that blocks a pillar on one parcel and
show the pillar becomes unavailable there and a saved scenario using it is
flagged; add an environmental finding with a remediation cost and show the
cost line, the gap, and the Environmental gate all change; show a figure
moving from Planning to Verified.
```
