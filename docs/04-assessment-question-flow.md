# Deliverable 4 — Assessment Question Flow

This is the **structure and routing logic** of the guided screener. The full draft
wording of each question lives in
[Deliverable 16](./16-assessment-questions-draft.md). The pathway logic that
consumes these answers lives in [Deliverable 5](./05-pathway-decision-tree.md).

## Universal answer options

Every question offers, where applicable:

- **Yes**
- **No**
- **I do not know**
- **I need help finding this**
- **This does not apply**
- **I want to skip this**

"I do not know" and "I need help finding this" are **never** dead ends — they set
flags that add records-to-gather items and office referrals to the roadmap.

## Flow overview

```
S1 Welcome & Consent ─(must confirm)→ S2
S2 Property Location ──(in Harris County?)──┬─ No → Out-of-county notice (continue, flagged)
                                            └─ Yes → S3
S3 Current Owner Status ──(owner living/deceased/unknown?)──┐
        ├─ Living  → S4 (Prevention)
        ├─ Deceased→ S5 (Intervention)
        └─ Unknown → S5 (treated as "may be deceased / unclear")
S4 or S5 → S6 Family & Heirship Context
        → S7 Estate & Probate Documents
        → S8 Real Property Records
        → S9 Taxes & Exemptions
        → S10 Property Condition & Stability
        → S11 Your Goal
        → Review → Generate Roadmap
```

Escalation flags (see [Deliverable 11](./11-escalation-flag-logic.md)) can fire at
**any** step and surface supportive urgency language without interrupting the flow.

---

## Section 1 — Welcome & Consent  *(gate)*

- Explain what the tool does / does not do, educational-only, no legal advice, may
  need a Texas attorney, do-not-enter-sensitive-info, consent-based sharing.
- **Required confirmation:** "I understand this tool is educational and does not
  provide legal advice." → unlocks the screener.

## Section 2 — Property Location

1. Is the property in Harris County, Texas?
2. Property address (street, city, ZIP).
3. Is it inside the City of Houston?
4. Is it in Kashmere Gardens or Super Neighborhood 52?
5. Occupancy: occupied / vacant / rented / abandoned / damaged / unknown.
6. Type: home / vacant lot / multifamily / commercial / church-owned / other.

**Routing:**
- Q1 = No → show out-of-county notice; continue but flag `out_of_county`.
- Q5 ∈ {vacant, abandoned, damaged} → candidate for **Pathway K** + condition flags.
- Q6 = church-owned/commercial → note for partner; may need specialized referral.

## Section 3 — Current Owner Status  *(first major branch)*

1. Who is listed as the owner, if known?
2. Is that person living or deceased? *(living / deceased / I do not know)*
3. Is the user the listed owner?
4. Is the user related to the listed owner?
5. Does the user live in the property?
6. Is the property listed as "in the estate of"?
7. Does the user know whether the deed has been updated?

**Routing:**
- Q2 = living → **Section 4** (Living Owner / Prevention).
- Q2 = deceased **or** I do not know → **Section 5** (Deceased / Intervention).
- Q6 = Yes → candidate for **Pathway K**.

## Section 4 — If the Owner Is Living  *(Prevention branch)*

1. Does the owner have a will?
2. Does the owner have a trust?
3. Has the owner named who should receive the property?
4. Has the owner considered a transfer on death deed or other planning tool?
5. Does the owner have a homestead exemption?
6. Over-65, disability, veteran, or other exemptions?
7. Does the family know where the deed and property records are?
8. Are family members aware of the owner's wishes?

→ Routes toward **Pathway A (Living Owner Prevention)**. Then continue to S6.

## Section 5 — If the Owner Is Deceased  *(Intervention branch)*

1. Approximate date of death.
2. Was there a will?
3. Is the original will available?
4. Was the will filed with a court?
5. Was probate opened?
6. Was anyone named executor or administrator?
7. Was there a trust?
8. Was there a transfer on death deed?
9. Was there an affidavit of heirship?
10. Was there a small estate affidavit?
11. Were any court orders issued?
12. Is there disagreement among family members?
13. Are there multiple possible heirs?
14. Are taxes current or delinquent?

**Routing seeds:**
- Will = Yes → **Pathway B (Deceased With Will)**.
- Will = No/Unknown → **Pathway C (Deceased Without Known Will)**.
- Q12 = Yes → **Pathway F (Family Conflict/Pressure)**.
- Q13 = Yes → **Pathway E (Multiple Heirs)**.
- Q14 = delinquent → **Pathway G (Tax/Foreclosure Risk)** + escalation check.

## Section 6 — Family & Heirship Context

1. Was the deceased owner married?
2. Did the deceased owner have children?
3. Are any children deceased?
4. Grandchildren, siblings, parents, or other relatives possibly involved?
5. Is the user one of several possible heirs?
6. Does anyone disagree about who should receive the property?
7. Has anyone been paying taxes, insurance, repairs, or utilities?
8. Has anyone tried to sell, transfer, refinance, lease, or repair the property?

*Always shown reminder:* the platform cannot determine heirship or ownership; it
only identifies questions for attorney review.

**Routing:** Q5/Q4 → reinforce **Pathway E**; Q6 → reinforce **Pathway F**;
Q8 attempt blocked → reinforce **Pathway H / I**.

## Section 7 — Estate Planning & Probate Documents

Has / knows about: will · trust · death certificate · probate case number ·
court order · executor paperwork · administrator paperwork · small estate
affidavit · affidavit of heirship · transfer on death deed · life estate deed ·
family agreement · attorney paperwork.

For each missing item → add to **Records to Gather** with "where it may be found /
who may know."

## Section 8 — Real Property Records

1. Do you have the deed?
2. Do you know whose name is on the deed?
3. Has the property ever been transferred?
4. Has anyone searched Harris County real property records?
5. Liens, deeds of trust, releases, judgments, tax liens, other recorded docs?
6. Has a title company ever reviewed the property?

**Routing:** "passed down / no paperwork" signals → **Pathway D**; liens/judgments
→ note for attorney + possible **Pathway G**.

## Section 9 — Taxes & Exemptions

1. Taxes current? 2. Taxes delinquent? 3. Notices from tax office/court/
attorney/collection firm? 4. Tax lawsuit? 5. Foreclosure or tax-sale notice?
6. Payment plan? 7. Homestead exemption? 8. Over-65? 9. Disability?
10. Disabled veteran? 11. Primary residence? 12. Does the resident's Texas ID /
driver's license match the property address?

*Always shown reminder:* exemptions may reduce taxes but do not necessarily
resolve title.

**Routing:** Q2/Q4/Q5 → **Pathway G** + **escalation flags**; Q7–Q11 → preservation
exemption guidance.

## Section 10 — Property Condition & Housing Stability

1. Safe to live in? 2. Repairs needed? 3. Denied home-repair help because of title?
4. Denied disaster-recovery help because of title? 5. Insurance? 6. Utilities
active? 7. Code violations? 8. Dumping/trespassing/fire/storm damage?
9. Anyone at risk of displacement?

**Routing:** Q3/Q4 → **Pathway H**; Q9 + elderly/disabled → **escalation**; vacant/
damaged → reinforce **Pathway K**.

## Section 11 — Your Goal  *(multi-select)*

Keep the family home · Understand who owns it · Find the deed · Find probate
records · Apply for an exemption · Stop tax delinquency · Avoid foreclosure/tax
sale · Clear title · Repair the property · Sell · Transfer · Redevelop · Protect
for the next generation · Resolve family disagreement · Talk to legal aid · Talk
to an attorney · I do not know where to start.

**Routing:** goals weight and order the recommended pathways and customize the
roadmap (e.g., "Repair" → **Pathway H**; "Sell/Transfer/Redevelop" → **Pathway I**;
"I do not know where to start" → **Pathway J**).

## Review → Generate

The resident reviews a plain-language summary of answers, can edit any section,
then generates the **Family Property Roadmap** ([Deliverable 10](./10-roadmap-template.md)).
