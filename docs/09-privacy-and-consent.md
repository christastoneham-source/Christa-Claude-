# Deliverable 9 — Data Privacy and Consent Language

Principle: **collect only the minimum information needed**, never collect sensitive
identifiers, and never share with a partner without explicit, scoped consent.

## 1. Privacy notice (resident-facing)

> "We ask only for what we need to help you understand your situation and prepare
> for next steps. **Please do not enter Social Security numbers, full bank account
> numbers, or other highly sensitive information.** Your answers are used to build
> your Family Property Roadmap. We do not share your information with any partner
> organization unless you give us permission. You can stop at any time, and you can
> ask us to delete your information."

## 2. Do-not-collect list (hard rule)

The platform must **never** collect or store:

- Social Security numbers
- Bank account numbers
- Full driver's license numbers
- Full dates of birth *(unless legally reviewed and necessary)*
- Private financial records
- Sensitive allegations
- Confidential attorney communications

Input fields are designed so these are never requested; free-text fields carry a
reminder and should be scanned/blocked for obvious patterns (e.g., 9-digit SSN).

## 3. What we do collect (with consent), for operations & aggregate reporting

- Number of users who started / completed the screener
- Property geography (e.g., ZIP, neighborhood, in/out of Harris County)
- User pathway(s)
- Documents missing
- Referral type (legal aid, tax exemption, foreclosure prevention, home repair,
  Public Probate Administrator, Houston Land Bank)
- Time from first contact to referral
- Closed-loop referral completion
- Applications received vs. served; denial reasons
- Language needs; age range; vulnerability indicators; ownership status
- Outcomes reported by partners

Operational data is minimized, access-controlled, and used to improve the pilot,
identify bottlenecks, support funding, and build a replicable model.

## 4. Consent model

Consent is **explicit, specific, and revocable**. A single "I agree to everything"
is not used. There are distinct consent moments:

| Consent type | When | Scope |
|---|---|---|
| **Educational use** | Section 1 (required to proceed) | Use answers to build the roadmap only |
| **Partner referral** | Before any handoff (optional) | Share specified results with named partner(s) for a stated purpose |
| **Follow-up contact** | Optional | Allow a navigator/partner to contact the resident |
| **Aggregate reporting** | Optional | Include de-identified data in reporting |

Each consent is logged with timestamp, scope, and the partner(s) covered. Expanding
scope (new org, new purpose) requires a **new** consent.

## 5. Partner-referral consent language (resident-facing)

> "To connect you with help, we would share the following with **[partner name(s)]**:
> **[list of what is shared]**.
>
> - **What we share:** [e.g., your pathway, the records you still need, your
>   property's neighborhood, your goal]. We do **not** share sensitive identifiers.
> - **Who receives it:** [named partner organization(s)].
> - **Why:** so they can help you with [legal review / tax help / home repair /
>   foreclosure prevention / housing counseling].
> - **How it helps you:** [plain-language benefit].
> - **Your confidentiality:** legal confidentiality and privacy rules are
>   protected.
> - **Your choice:** you may decline. Declining will not stop you from using this
>   tool or downloading your roadmap.
>
> ☐ Yes, share my information with the partner(s) listed above.
> ☐ No, do not share my information."

## 6. Rights

Residents can:

- Use the full tool and get a roadmap **without** consenting to any sharing.
- Decline or withdraw consent at any time.
- Request deletion of their information.
- Download or email their own roadmap.

## 7. Security & retention (operational requirements)

- Encrypt data in transit and at rest.
- Least-privilege access; partner access bounded by consent scope.
- Retention limited to what the pilot needs; define a retention/deletion schedule.
- Audit log for consent events and partner access.
- Free-text inputs screened to prevent storage of prohibited identifiers.

## 8. Partner-side obligations

- Partners may only use shared data for the consented purpose.
- Partners may not re-share outside the consented scope.
- Warm handoffs to a **new** partner require confirming consent covers that partner
  (see [Deliverable 12](./12-warm-handoff-workflow.md)).
- Partners protect any applicable legal confidentiality (e.g., attorney-client,
  legal-aid confidentiality).

## 9. Plain-language summary (shown to residents)

> "Short version: We only collect what we need. We never ask for your Social
> Security number or bank account number. We don't share your information with
> anyone unless you say yes, and you can change your mind."
