# Deliverable 13 — Partner Dashboard Fields

Fields for the partner/navigator console. The dashboard supports coordinated
support and closed-loop tracking while honoring consent and the no-score rule.

## A. Referral record fields

| Field | Type | Notes |
|---|---|---|
| `referral_id` | id | Unique |
| `created_at` | datetime | |
| `consent_id` | ref | Links to consent record + scope |
| `consent_scope` | list | Partners covered, purpose, expiry |
| `pathways` | multi-enum A–K | From decision tree |
| `escalation_flags` | multi-enum | From [Deliverable 11](./11-escalation-flag-logic.md) |
| `expedited` | bool | True if a Critical flag present |
| `property_geography` | string | Neighborhood / ZIP / in-county (no full address unless consented) |
| `goal` | multi-enum | From Section 11 |
| `shared_screener_summary` | object | Consented fields only; no SSN/bank/full DL |
| `document_readiness` | object | `{have: [...], missing: [...]}` |
| `navigator_notes` | text | Internal notes |
| `assigned_partner` | ref | Partner org |
| `assigned_user` | ref | Staff member |
| `referral_type` | enum | legal_aid / tax_exemption / foreclosure_prevention / home_repair / housing_counseling / disaster_recovery / community / public_probate_admin / land_bank |
| `status` | enum | new / acknowledged / in_progress / handed_off / served / denied / withdrawn |
| `denial_reason` | enum + text | If denied |
| `acknowledged_at` | datetime | For SLA tracking |
| `closed_at` | datetime | Closed-loop confirmation |
| `outcome` | enum + text | Partner-reported result |

## B. Dashboard views & their fields

### 1. Queue / work list
`referral_id` · `created_at` · `expedited` · `escalation_flags` · `pathways` ·
`referral_type` · `status` · `assigned_user` · `acknowledged_at` (SLA timer).
Sort: expedited first, then oldest unacknowledged.

### 2. Single referral detail
All referral record fields + consent scope viewer + document-readiness editor +
navigator notes + warm-handoff controls + closed-loop confirmation.

### 3. Escalations board
Filtered to active `escalation_flags`; Critical pinned to top; shows time since
created and acknowledgment status.

### 4. Assignments
`assigned_partner` · `assigned_user` · workload counts · reassignment control.

### 5. Reports / aggregate dashboard (no individual scores)
| Metric | Source |
|---|---|
| Users started / completed screener | analytics |
| Pathway distribution | `pathways` |
| Property geography distribution | `property_geography` |
| Referral type distribution | `referral_type` |
| Documents-missing frequency | `document_readiness.missing` |
| Time from first contact to referral | timestamps |
| Closed-loop completion rate | `status`/`closed_at` |
| Applications received vs. served | `status` |
| Denial reasons | `denial_reason` |
| Bottleneck tracking | stage durations |
| Outreach conversion | source → started → completed → referred |
| Language needs | screener |
| Age range / vulnerability indicators | screener (aggregate only) |
| Ownership status distribution | screener |
| Partner-reported outcomes | `outcome` |

## C. Partner-side operating functions (mapped to fields)

| Function | Backed by |
|---|---|
| Shared screener results | `shared_screener_summary` (consent-bounded) |
| Consent-based referrals | `consent_id`, `consent_scope` |
| Warm handoff tracking | `status` transitions, `acknowledged_at` |
| Referral status | `status` |
| Escalation flags | `escalation_flags`, `expedited` |
| Partner assignment | `assigned_partner`, `assigned_user` |
| Document readiness status | `document_readiness` |
| Navigator notes | `navigator_notes` |
| Closed-loop referral confirmation | `closed_at`, `outcome`, `denial_reason` |
| Quarterly reporting | Reports view |
| Aggregate dashboard | Reports view |
| Denial-reason tracking | `denial_reason` |
| Bottleneck tracking | stage-duration metrics |
| Outreach conversion tracking | conversion funnel |

## D. Access control & consent enforcement

- A partner sees a referral **only** if `consent_scope` includes that partner and
  the consent is unexpired.
- Field-level redaction: sensitive identifiers are never stored, so never shown.
- Reports use **aggregate / de-identified** data only — no per-family scores or
  ratings (the platform produces none).
- Audit log records every view and status change.

## E. Denial-reason enumeration (starter set)

`outside_service_area` · `income_ineligible` · `title_unresolved_prereq` ·
`did_not_respond` · `withdrew` · `referred_elsewhere` · `program_capacity` ·
`documentation_incomplete` · `other (text)`.
