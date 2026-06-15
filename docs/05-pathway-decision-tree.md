# Deliverable 5 — Pathway Decision Tree

The engine routes each user into **one or more** of eleven pathways (A–K). Pathways
are **not mutually exclusive** — a deceased-owner-without-will case with delinquent
taxes and multiple heirs can trigger C + E + G simultaneously. The roadmap lists
all triggered pathways, ordered by the user's stated goal and by urgency.

> The decision tree performs **issue spotting only**. It never determines
> ownership, heirship, probate need, or title status, and never tells the user
> what legal action to take.

## Pathway catalog

| ID | Pathway | Continuum stage |
|---|---|---|
| A | Living Owner Prevention | Prevention |
| B | Deceased Owner With Will | Intervention |
| C | Deceased Owner Without Known Will | Intervention |
| D | Informal "Passed Down" Property | Intervention |
| E | Multiple Heirs | Intervention |
| F | Family Conflict or Pressure | Intervention |
| G | Tax Delinquency or Foreclosure Risk | Intervention / Preservation |
| H | Keep and Repair the Family Home | Preservation |
| I | Sell, Transfer, or Redevelop | Preservation |
| J | No One Knows Where to Start | Intervention |
| K | Vacant, Abandoned, or "In the Estate Of" | Intervention |

## Primary branch (owner status)

```
START
 │
 ├─ Owner is LIVING ───────────────────────────► add Pathway A
 │
 ├─ Owner is DECEASED ─┐
 │                     ├─ Will exists ─────────► add Pathway B
 │                     └─ No / unknown will ───► add Pathway C
 │
 └─ Owner status UNKNOWN ──────────────────────► add Pathway C + Pathway J
```

## Overlay rules (evaluated for every case, additive)

```
IF property given/promised/inherited/passed-down with no clear paperwork
        → add Pathway D
IF more than one possible heir (S5.Q13, S6.Q4, S6.Q5)
        → add Pathway E
IF disagreement OR pressure to sign OR suspected coercion/competing claims
   (S5.Q12, S6.Q6, condition signals)
        → add Pathway F  [and likely an escalation flag]
IF taxes delinquent OR notice received OR lawsuit OR tax-sale/foreclosure notice
   (S9.Q2,Q3,Q4,Q5)
        → add Pathway G  [escalation flag if lawsuit/sale/foreclosure notice]
IF goal includes keep/repair/insure/apply-for-assistance OR denied help due to title
   (S10.Q3,Q4; S11)
        → add Pathway H
IF goal includes sell/transfer/lease/develop/program use (S11)
        → add Pathway I
IF user does not know owner/probate/deed/tax/family-docs (many "I don't know")
        → add Pathway J
IF property vacant/abandoned/"in the estate of"/deteriorating/no responsible party
   (S2.Q5, S3.Q6, S10)
        → add Pathway K
```

## Worked routing examples

**Example 1 — Living mother, no will yet, has homestead exemption, wants to protect
home for kids.**
→ Owner living → **A**. Goal "protect for next generation" reinforces **A**.
Roadmap: prevention guidance, estate-planning attorney questions, exemption review.

**Example 2 — Father died 10 years ago, no known will, four siblings, taxes
delinquent, certified letter received.**
→ Deceased + no will → **C**. Multiple heirs → **E**. Delinquent taxes + certified
notice → **G** + **escalation flag**. Roadmap leads with the tax/foreclosure
urgency, then heirship and probate-records steps.

**Example 3 — "Grandma always said the house is mine" but deed unchecked, user
unsure if probate ever happened, wants to repair it.**
→ Passed down, no paperwork → **D**. Many unknowns → **J**. Goal repair → **H**.
Roadmap starts with HCAD/deed lookup and document gathering, then repair-eligibility
questions for an attorney.

**Example 4 — Vacant inherited lot listed "in the estate of," nobody paying taxes.**
→ Vacant + "in the estate of" → **K**. No will known → **C**. Delinquent taxes → **G**.
Roadmap notes the Public Probate Administrator and Houston Land Bank *may* be
relevant (only if program rules and legal review support it).

## Ordering logic for the roadmap

When multiple pathways trigger, present them in this priority order:

1. **Urgent / escalation-linked** pathways first (typically **G**, **F**, or a
   condition/displacement flag).
2. **Foundational title pathways** next (**B**, **C**, **D**, **K**) — because most
   other actions depend on title clarity.
3. **Coordination pathways** (**E**) — who must participate.
4. **Goal pathways** (**H**, **I**) — what the family is trying to do.
5. **Orientation pathway** (**J**) — the simple starting roadmap, shown first to
   users with many unknowns even though it sorts here logically.
6. **Prevention** (**A**) — for living-owner cases, presented as the primary path.

## Anti-conclusion checks (applied to every routed pathway)

Before rendering, the engine strips/blocks any phrasing that would:

- assert ownership or heirship ("you are the owner/heir");
- direct a legal action ("you should file probate / sell / sign");
- promise a remedy ("this will clear your title / you qualify");
- predict a court outcome.

Replaced with: "this **may** involve…", "a licensed Texas attorney can help
determine whether…", "you **may** want to gather…", "this is not a legal
conclusion."
