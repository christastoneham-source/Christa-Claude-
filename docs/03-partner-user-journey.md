# Deliverable 3 — Partner User Journey

Partners (legal aid, housing counselors, tax-help organizations, community
navigators, public agencies) move **from fragmented referrals to coordinated
support**. The partner experience is built for clarity: who does what, when a
case hands off, when to escalate, and how outcomes are tracked — all under
consent.

## Journey at a glance

```
Onboard → Receive (consented) → Review → Act → Hand off → Close the loop → Report
```

## Stage 1 — Onboard

- Organization is added to the partner directory with a defined **role** (e.g.,
  legal services, tax assistance, home repair, housing counseling, disaster
  recovery, public agency, community navigator).
- Staff get authenticated accounts with least-privilege access.
- Reviews the **Partner Playbook**: intake logic, referral rules, handoff
  protocols, consent language, escalation SOP, and outcome definitions.

## Stage 2 — Receive (consent-verified referral)

- A referral appears **only** when the resident has consented to share with that
  partner type/organization.
- The referral card shows: consent scope, shared screener results, recommended
  pathway(s), document-readiness status, escalation flags, and navigator notes.
- No referral ever arrives without a consent record attached.

**Guardrail:** if consent is missing or its scope does not cover this partner,
the referral is not routed.

## Stage 3 — Review

- Partner reviews the **shared screener results** (not raw sensitive data — no
  SSNs, bank numbers, etc.).
- Sees what records the family already has vs. still needs.
- Sees escalation flags front and center (tax sale, foreclosure, court papers,
  coercion, displacement risk).

## Stage 4 — Act

- Partner accepts/assigns the referral, adds navigator notes, and updates
  **document readiness** and **referral status**.
- For urgent flags, partner follows the escalation SOP (e.g., expedite a legal-aid
  intake when a tax-sale or foreclosure notice is present).
- Partner can request additional records via the navigator (closed-loop), without
  re-collecting prohibited data.

## Stage 5 — Hand off (warm handoff)

- When the case needs another partner (e.g., title clarified → now home repair),
  the partner initiates a **warm handoff**:
  - Confirms the resident's consent covers the next partner.
  - Transfers status, notes, and document readiness.
  - The receiving partner acknowledges (handoff tracking).
- No "cold" transfers: the resident is never dropped between organizations.

## Stage 6 — Close the loop

- Receiving partner confirms the resident was served or records a **denial reason**
  (e.g., title still unresolved, outside service area, did not respond).
- Closed-loop confirmation marks the referral complete.

## Stage 7 — Report

- Aggregate dashboard surfaces: pathway distribution, referral types, time from
  first contact to referral, closed-loop completion, applications received vs.
  served, denial reasons, and bottlenecks.
- Quarterly reporting supports pilot evaluation, funding, and replication.

## Roles & responsibilities (RACI-style)

| Function | Navigator / intake | Legal partner | Housing/tax/repair partner | Program admin |
|---|---|---|---|---|
| Capture consent | **R** | C | C | A |
| Review screener results | R | **R** | **R** | I |
| Issue spotting / legal review | C | **R** | I | I |
| Document readiness updates | R | C | C | I |
| Escalation action | C | **R** | C | A |
| Warm handoff initiation | **R** | R | R | I |
| Closed-loop confirmation | C | R | **R** | A |
| Reporting | I | C | C | **R** |

*R = Responsible, A = Accountable, C = Consulted, I = Informed.*

## Consent is the spine

At **every** stage, partner access is bounded by what the resident consented to:

- **What** information may be shared.
- **Which** partners may receive it.
- **Why** it is being shared and how it helps the resident.
- That legal confidentiality and privacy rules are protected.
- That the resident may decline data sharing at any time.

If a partner needs to expand sharing (new organization, new purpose), the system
requires a **new consent** before routing.

## What partners never get

- Social Security numbers, bank account numbers, full driver's license numbers.
- Confidential attorney communications.
- Any resident data outside the consented scope.
- A numerical score or risk rating for the family (the platform produces none).
