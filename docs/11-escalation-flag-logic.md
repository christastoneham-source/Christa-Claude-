# Deliverable 11 — Escalation Flag Logic

Escalation flags identify situations that may need **urgent referral or
higher-touch navigation**. Flags can fire at any screener step. They change tone
and ordering — they do **not** produce a score and do **not** tell the user what
legal action to take.

## Escalation language (shown when any flag fires) — verbatim

> "Because you mentioned a notice, court paper, tax issue, foreclosure risk, or
> pressure to sign documents, this may require urgent review by a licensed attorney
> or qualified legal aid organization. This tool cannot tell you what legal action
> to take, but it can help you organize records and questions to bring to a
> professional as soon as possible."

## Flag catalog and triggers

| Flag | Trigger source (screener) | Severity |
|---|---|---|
| Tax sale notice | S9.Q5 = yes | **Critical** |
| Foreclosure notice | S9.Q5 / S10 | **Critical** |
| Lawsuit or court papers | S9.Q4 = yes; S5.Q11 | **Critical** |
| Certified mail (court/tax/attorney/collections) | S9.Q3 = yes | High |
| Family pressure to sign documents | S6.Q6, S5.Q12, Pathway F signals | High |
| Suspected fraud / coercion / predatory investor | free-text + anti-predatory signals | High |
| Elderly or disabled occupant at risk | S9.Q8/Q9 + S10.Q9 | High |
| Occupant facing displacement | S10.Q9 = yes | High |
| Unsafe housing condition | S10.Q1 = no | High |
| Property damage blocking safe occupancy | S10.Q2/Q8 | Medium-High |
| No one paying taxes | S6.Q7 = no + S9.Q2 | Medium-High |
| No clear person with authority to act | S3/S5/S6 unknowns | Medium |
| Multiple heirs in dispute | S5.Q13 + S5.Q12/S6.Q6 | Medium-High |
| Property listed "in the estate of" | S3.Q6 = yes | Medium |
| Home repair denied because of title | S10.Q3 = yes | Medium-High |
| Disaster recovery denied because of title | S10.Q4 = yes | Medium-High |
| Sale contract already signed | S6.Q8 / free-text | **Critical** |
| Someone trying to buy the property quickly for cash | free-text / Pathway F | High |

## Behavior by severity

**Critical** (tax sale, foreclosure, lawsuit/court papers, signed sale contract):
- Surface escalation language immediately.
- Place the linked pathway (usually **G** or **F**) at the **top** of the roadmap.
- Add an in-flow prompt: "You can finish these questions, but consider contacting
  legal aid right away." with a quick link to legal-aid resources.
- Mark the referral, if consented, as **expedited** for partners
  ([Deliverable 12](./12-warm-handoff-workflow.md), [13](./13-partner-dashboard-fields.md)).

**High / Medium-High:**
- Surface escalation language.
- Prioritize the linked pathway in roadmap ordering.
- Tag the partner referral with the flag.

**Medium:**
- Note in the roadmap's "What This May Mean" and add relevant office/attorney
  questions; tag for partner awareness.

## What flags must never do

- Never assign a number, grade, or risk score.
- Never say what legal action to take ("file an answer," "contest the sale").
- Never determine ownership/heirship.
- Never create alarm that shames the user — tone stays supportive and practical.

## Routing summary

```
Critical/High flag present
   → roadmap §3 & §4 lead with urgent pathway + escalation language
   → §7 prioritizes legal aid / Tax Assessor-Collector (and Clerk/Probate as needed)
   → §10 adds foreclosure-prevention / housing-stabilization referrals
   → §11 emphasizes "do not sign under pressure" / "do not ignore notices"
   → if consented, partner referral flagged & (Critical) expedited
```

## Partner-side handling

- Critical flags appear in `/partner/escalations` and at the top of the queue.
- Escalation flags travel with the referral payload (consent-bounded).
- Closed-loop confirmation should note whether the urgent issue was addressed or
  why not (denial-reason tracking).
