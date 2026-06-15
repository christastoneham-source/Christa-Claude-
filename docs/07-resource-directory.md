# Deliverable 7 — Harris County Resource Directory Structure

> **Verification gate:** every address, phone number, email, website, hours, and
> program detail below is a **placeholder pending verification against official
> sources** before public launch. Fields are marked `[VERIFY]`. Do not publish any
> contact detail that has not been confirmed.

## Data model (one record per office/partner)

```
- id
- name
- category            (county_office | appraisal | tax | legal_aid | housing |
                       repair | foreclosure | disaster | community | land_bank |
                       probate_admin)
- what_they_do        plain-language description
- when_relevant       situations / pathways that point here
- what_they_cannot_do limits (especially for Public Probate Administrator)
- search_by           (address | owner_name | grantor | grantee | case_number |
                       document_number | date_range)  [for records offices]
- address             [VERIFY]
- phone               [VERIFY]
- email               [VERIFY]
- website             [VERIFY]
- hours               [VERIFY]
- languages           [VERIFY]
- intake_notes        how a resident should approach them
- questions_to_ask    resident-ready questions
- linked_pathways     [A..K]
- last_verified_date  [VERIFY]
```

---

## A. Harris County Clerk's Office  *(category: county_office)*

- **What they do** — Maintain and let the public search **real property records**
  (deeds, deeds of trust, releases, liens, affidavits, plats, easements),
  **probate records**, civil court records, and Commissioners Court records.
- **Search by** — property address, owner name, grantor or grantee name, case
  number, document number, date range.
- **When relevant** — finding the deed, checking transfers/liens, locating probate
  filings, recording documents. Pathways B, C, D, E, I, J, K.
- **Questions to ask** — "How do I search real property records by address?" ·
  "How do I find a probate case?" · "How do I get a certified copy of a recorded
  deed?"
- `address/phone/email/website/hours` — **[VERIFY]**

## B. Harris County Probate Courts  *(category: county_office)*

- **What they do** — Handle probate matters: probate records, case numbers, court
  filings and orders, executor/administrator appointments, hearings, estate
  administration records.
- **When relevant** — confirming whether probate happened, finding a case number,
  understanding court filings. Pathways B, C, E, K.
- **Questions to ask** — "Was a probate case ever opened for this person?" · "How do
  I find a probate case number?" · "How do I get copies of court orders?"
- `address/phone/email/website/hours` — **[VERIFY]**

## C. Harris County Public Probate Administrator  *(category: probate_admin)*

- **What they do** — A public office that may become involved in certain estates
  where no one is available or willing to act.
- **What they cannot do** — Not a private attorney for the family; cannot guarantee
  outcomes; involvement is limited by law and program rules. **State limits clearly
  to set expectations.**
- **When relevant** — vacant/abandoned/"in the estate of" property with no
  responsible party. Pathway K (and sometimes C).
- **Questions to ask before contacting** — "Could the Public Probate Administrator
  assist with this estate?" · "What does this office do and not do?" · "What
  information would they need from me?"
- `address/phone/email/website/hours` — **[VERIFY]**

## D. Harris Central Appraisal District (HCAD)  *(category: appraisal)*

- **What they do** — Property **account records**, appraised value, **exemption
  records** (homestead, over-65, disability, veteran), the protest process, and the
  mailing-address-vs-property-address distinction.
- **When relevant** — looking up the property account, checking/applying for
  exemptions, confirming what HCAD shows. Pathways A, G, H, J.
- **Questions to ask** — "What is the property account for this address?" · "What
  exemptions are on this property?" · "Can the resident apply for a homestead
  exemption?"
- `address/phone/email/website/hours` — **[VERIFY]**

## E. Harris County Tax Assessor-Collector  *(category: tax)*

- **What they do** — Tax bills, payment status, **delinquent taxes**, tax
  certificates, payment plans, and tax-sale/foreclosure questions. **Tax records
  differ from ownership records.**
- **When relevant** — checking if taxes are current, setting up a payment plan,
  understanding delinquency. Pathways G, H, J. *(Urgent if lawsuit/sale notice —
  also route to legal aid.)*
- **Questions to ask** — "Are the taxes on this property current or delinquent?" ·
  "Is a payment plan or deferral available?" · "Is there a tax suit or sale on this
  account?"
- `address/phone/email/website/hours` — **[VERIFY]**

---

## F. Legal assistance resources  *(category: legal_aid)*

| Organization | What they do | Notes |
|---|---|---|
| **Lone Star Legal Aid** | Civil legal aid incl. heirs' property/title, probate, tax issues | Income eligibility may apply — **[VERIFY]** |
| **Earl Carl Institute** (TSU Thurgood Marshall School of Law) | Legal research/advocacy, heirs' property work | **[VERIFY] intake path** |
| **Houston Volunteer Lawyers** | Pro bono attorney matching | Eligibility — **[VERIFY]** |
| **Houston Bar Association resources** | Lawyer referral & community resources | **[VERIFY]** |
| Other approved legal services orgs | — | Add after vetting |

`address/phone/email/website/hours/eligibility` for each — **[VERIFY]**

## G. Housing & community resources

| Resource | Category | Role |
|---|---|---|
| **Houston Land Bank** | land_bank | Heirs'-property-related programs; relevant **only if** program rules and legal review support it. Pathways I, K. **[VERIFY scope]** |
| Home repair programs | repair | Repair pre-eligibility; may require proof of ownership. Pathway H. **[VERIFY]** |
| Housing counseling agencies (HUD-approved) | housing | Counseling, foreclosure prevention. Pathways G, H. **[VERIFY]** |
| Foreclosure prevention resources | foreclosure | Urgent help for tax/mortgage foreclosure. Pathway G. **[VERIFY]** |
| Disaster recovery programs | disaster | Recovery assistance; title may affect eligibility. Pathway H. **[VERIFY]** |
| Community development partners | community | Local navigation. **[VERIFY]** |
| Trusted community touchpoints | community | Churches, libraries, neighborhood orgs in Kashmere Gardens / SN 52. **[VERIFY]** |

---

## Editorial rules for the directory

- Describe what each office **does** and, where it matters most (Public Probate
  Administrator), what it **cannot** do — so residents arrive with accurate
  expectations.
- Always pair an office with **resident-ready questions**.
- Distinguish clearly: **tax records ≠ ownership records**, and **exemptions ≠
  title resolution**.
- Mark Houston Land Bank and Public Probate Administrator referrals as conditional
  ("may be relevant only if program rules and legal review support it").
- Maintain a `last_verified_date` and re-verify on a regular cadence.
