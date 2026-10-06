# ADDENDUM B: Feasibility Service Embodiments (for the provisional)

Prepared 2026-10-06. Attorney work product. Supplements `TECHNICAL-DISCLOSURE.md` §11-12 and `ADDENDUM-2026-10-06-PORTFOLIO-EMBODIMENTS.md` (A1-A8). Source: the feasibility service design of record (`investment-map-service/2026-10-06_Feasibility-Service-Design.md`). Status of every item: SPECIFIED IN WRITING, NOT YET REDUCED TO PRACTICE.

These embodiments are offered specifically in response to counsel's observation that the invention should engage something outside the computation itself. Each one couples the projection engine to external professional processes or external records: the system emits structured requests to outside professionals, ingests their findings as typed records, and changes scenario state, gate status, figure confidence, and alerts as a result.

## B1. Findings Ledger: typed external findings that mutate scenario state

A store of structured finding records, each comprising: site and parcel or lot identifier; workstream (title and legal; zoning and entitlement; environmental; physical site; value and market; cost; financial and community); originating professional role; date; finding type (constraint, cost, value, timeline, pass or fail); a model-effect specification; and a reference to the source document. On insertion, the system applies the model effect to the projection engine (TECHNICAL-DISCLOSURE §1) as one of: (a) adding or modifying a cost line in `parcelCost`/`totalInvestment`; (b) replacing a baseline value (for example, an appraised as-is value replaces the assessed value of record in the value-created computation, §1.5); (c) adding schedule duration; (d) removing a use type (pillar) or deal structure (A2) from the permissible set for that parcel; (e) setting a gate status (B2). Recomputation follows the existing recompute-on-render path (§6), so every view and every saved scenario reflects the finding immediately.

## B2. Feasibility gates set by evidence

A fixed set of gates per site (site control and title; entitlement and zoning; environmental; physical feasibility; financial; community and partners), each in one of {not started, in review, clear, conditional, fail}, whose status is computed from the findings in B1 by gate rules rather than set by hand. The financial gate is computed from the capital stack (A3): clear when gap ≤ 0. This is the evidence-driven successor to the five-dimension readiness scoring implemented in commit 913a55a (`const READINESS`: funding, policy, stakeholder, environment, timeline; `rdScore`; `rdColor` thresholds 70/40) and removed in 336bbf3, which is preserved as an alternative embodiment (TECHNICAL-DISCLOSURE §11.1). The specific gate rules are maintained as a trade secret and are not disclosed here; the embodiment claimed is the mechanism of computing gate status from typed findings.

## B3. Per-figure confidence ladder

Each displayed figure (cost, value, outcome) carries a provenance state in {planning, specialist, verified}, initialized to planning when the figure derives from pillar coefficients or assumptions (§2) and promoted when a B1 finding sets or confirms it. Aggregates display the lowest confidence of their inputs, or the share of the total that is verified. Provenance propagates through `aggregateOutcomes` and `totalInvestment` alongside the values.

## B4. Specialist work-order generation

For a given site and workstream, the system generates a structured scope-of-work document pre-populated with the parcel data of record and with the specific open questions whose answers the model requires. The questions are derived from which figures for that site remain at planning confidence (B3) and which gates remain unresolved (B2). The scope templates are maintained as a trade secret; the embodiment claimed is generating the request from the model's own unresolved state, and then closing the loop when the returned finding is entered in B1.

## B5. Scenario invalidation alerts

Each saved scenario records the assumptions it depends on (the parcels, pillars, structures, and baseline values it uses). When a new B1 finding, or a change detected in an external record (assessor data, a regulatory database such as the environmental screening layer of TECHNICAL-DISCLOSURE §12.5), contradicts one of those assumptions, the system flags the scenario with an alert stating the reason. Examples: a pillar is now blocked on a parcel the scenario uses; a baseline value the scenario's value-created figure relied on has been replaced.

## Filing notes for counsel

1. B1-B5 are described embodiments only. None is built as of 2026-10-06. The enabling detail is the mechanisms above, the implemented engine they extend, and the build specification in the design document of record, section 7.
2. Trade secret carve-out: the gate rules (B2), finding taxonomy details and model-effect rules (B1), scope templates (B4), and all coefficient and market-profile values are deliberately withheld from this disclosure and should remain withheld from any filing. The claims should be directed to the mechanisms, not the values.
3. A pilot engagement with real outside professionals, potentially the HCDC Atlanta and Decatur site, would constitute reduction to practice of B1-B5. It should occur after filing, or under written confidentiality.
4. UNVERIFIED: nothing in this addendum has been tested in code.
