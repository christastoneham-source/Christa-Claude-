# Deliverable 12 — Warm Handoff Workflow

A warm handoff moves a resident from the navigator (or one partner) to another
partner **without dropping them**, and **only within the bounds of consent**. No
cold transfers; no sharing beyond the consented scope.

## Principles

1. **Consent first** — nothing is shared until the resident consents to the specific
   partner(s) and purpose.
2. **No data drop** — the receiving partner gets context (screener results, document
   readiness, flags, notes) so the resident never re-explains from zero.
3. **Acknowledged transfers** — every handoff is accepted by the receiver
   (handoff tracking), not fire-and-forget.
4. **Closed loop** — the receiving partner confirms served / not served (with a
   denial reason).

## End-to-end flow

```
1. Roadmap generated → resident chooses "Connect me with help"
2. System proposes partner(s) based on pathway(s) + flags + geography
3. Resident reviews consent screen (what/who/why/how it helps/their choice)
4. Resident consents (or declines)
        ├─ Declines → no referral; resident keeps roadmap; can revisit later
        └─ Consents → referral created with consent record attached
5. Referral routed to matched partner(s) within consent scope
        └─ Critical escalation flag → referral marked EXPEDITED
6. Receiving partner ACKNOWLEDGES (accept / decline-with-reason)
        ├─ Accept → status = in_progress; partner adds navigator notes
        └─ Decline → re-route to alternate partner; notify navigator
7. Partner works the case; updates document readiness + status
8. Need another partner? → initiate secondary warm handoff
        └─ Re-check consent covers the NEW partner
                ├─ Covered → transfer context + acknowledge
                └─ Not covered → request NEW consent before sharing
9. CLOSE THE LOOP: receiving partner confirms served OR records denial reason
10. Referral marked complete; outcome flows to reporting
```

## Referral payload (consent-bounded)

```
- referral_id
- consent_id (+ scope: partners covered, purpose, expiry)
- pathway(s) [A..K]
- escalation_flags [...]  (+ expedited: bool)
- shared_screener_summary (no SSN/bank/full DL; only consented fields)
- document_readiness {have: [...], missing: [...]}
- navigator_notes
- property_geography (neighborhood / ZIP / in-county)
- goal(s)
- preferred_contact (only if follow-up-contact consent given)
- status (new | acknowledged | in_progress | handed_off | served | denied)
- denial_reason (if applicable)
- timestamps (created, acknowledged, served/closed)
```

## Handoff types

| Type | Example | Consent action |
|---|---|---|
| Navigator → Partner | Roadmap → Lone Star Legal Aid | Initial referral consent |
| Partner → Partner (same scope) | Legal aid → housing counseling, both pre-consented | Verify scope; transfer |
| Partner → New partner (new scope) | Legal aid → Houston Land Bank (not pre-consented) | **New consent required** |
| Escalated handoff | Critical flag → expedited legal aid | Initial consent + EXPEDITED tag |

## SLA / responsiveness targets (pilot defaults, tune with partners)

- **Critical** escalation referrals: acknowledged within 1 business day.
- Standard referrals: acknowledged within 3 business days.
- Closed-loop confirmation: within 30 days or status update with reason.
- If not acknowledged within SLA → auto-surface in navigator queue for re-routing.

## Guardrails

- A referral with no attached, in-scope consent record **cannot** be routed.
- Expanding to a new partner/purpose always requires fresh consent.
- Partners cannot re-share outside scope.
- Sensitive identifiers are never in the payload.
- The resident can withdraw consent, which halts further sharing.

## Resident-facing confirmation (after consent)

> "Thanks — with your permission, we've shared your roadmap summary and the records
> you still need with **[partner]** so they can help you with **[purpose]**. They
> may contact you at **[contact]**. You can also reach them directly: **[contact
> info]**. You can change your mind about sharing at any time."
