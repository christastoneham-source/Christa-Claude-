# Harris County Heirs' Property Navigator

A guided, conversational, **education-and-navigation** platform for Harris County
residents and families dealing with heirs' property, probate, title questions,
public records, property taxes, exemptions, and housing preservation.

> **This tool provides general education and navigation support for Harris County
> residents. It is not legal advice, does not create an attorney-client
> relationship, and should not be relied upon to make legal decisions. For advice
> about your specific situation, please speak with a licensed Texas attorney.**

This platform is **recommendation-based, not score-based**. It contains no
numerical scores, grades, rankings, risk scores, or readiness scores. It spots
issues, routes users into one or more pathways, explains what a situation *may*
mean, lists records to gather, names public offices and partners that *may* be
involved, and generates questions to bring to a licensed Texas attorney.

## Core promise

> "Answer a few questions about your family property. We will help you understand
> what may be going on, what records may be needed, which Harris County offices or
> partners may be involved, and what questions to ask before you take your next step."

## Strategic principle

**Client-facing simplicity. Partner-facing clarity.**

The platform serves two audiences:

1. **Residents and families** — plain-language education, better questions,
   pathway guidance, and a personalized **Family Property Roadmap**.
2. **Partner organizations** — clear intake logic, referral rules, handoff
   protocols, consent language, escalation flags, and outcome tracking.

## The continuum

| Stage | Use when | Goal |
|---|---|---|
| **Prevention** | The owner is living; the family wants to avoid future heirs' property issues. | Stop new tangled titles from forming. |
| **Intervention** | The owner may be deceased; title may be unclear; taxes may be delinquent; a property may be at risk. | Move families from confusion to organized next steps. |
| **Preservation** | The family wants to keep, repair, insure, or protect the home and avoid displacement. | Keep families housed and protect generational wealth. |

## Deliverables in this repository

All 17 deliverables from the master prompt live in [`/docs`](./docs):

| # | Deliverable | File |
|---|---|---|
| 1 | Full site map | [docs/01-site-map.md](./docs/01-site-map.md) |
| 2 | Resident user journey | [docs/02-resident-user-journey.md](./docs/02-resident-user-journey.md) |
| 3 | Partner user journey | [docs/03-partner-user-journey.md](./docs/03-partner-user-journey.md) |
| 4 | Assessment question flow | [docs/04-assessment-question-flow.md](./docs/04-assessment-question-flow.md) |
| 5 | Pathway decision tree | [docs/05-pathway-decision-tree.md](./docs/05-pathway-decision-tree.md) |
| 6 | Education card library outline | [docs/06-education-card-library.md](./docs/06-education-card-library.md) |
| 7 | Harris County resource directory structure | [docs/07-resource-directory.md](./docs/07-resource-directory.md) |
| 8 | Legal disclaimer language | [docs/08-legal-disclaimer-language.md](./docs/08-legal-disclaimer-language.md) |
| 9 | Data privacy and consent language | [docs/09-privacy-and-consent.md](./docs/09-privacy-and-consent.md) |
| 10 | Family Property Roadmap template | [docs/10-roadmap-template.md](./docs/10-roadmap-template.md) |
| 11 | Escalation flag logic | [docs/11-escalation-flag-logic.md](./docs/11-escalation-flag-logic.md) |
| 12 | Warm handoff workflow | [docs/12-warm-handoff-workflow.md](./docs/12-warm-handoff-workflow.md) |
| 13 | Partner dashboard fields | [docs/13-partner-dashboard-fields.md](./docs/13-partner-dashboard-fields.md) |
| 14 | Lovable-ready MVP build prompt | [docs/14-lovable-build-prompt.md](./docs/14-lovable-build-prompt.md) |
| 15 | Plain-language landing page copy | [docs/15-landing-page-copy.md](./docs/15-landing-page-copy.md) |
| 16 | First draft of assessment questions | [docs/16-assessment-questions-draft.md](./docs/16-assessment-questions-draft.md) |
| 17 | First draft of final roadmap output | [docs/17-roadmap-output-draft.md](./docs/17-roadmap-output-draft.md) |

## Non-negotiable guardrails

This platform **never**:

- assigns numerical scores, grades, rankings, or risk/readiness ratings;
- says "you are the owner / heir," "you should file probate," "this clears your
  title," "you qualify," "you should sell/transfer/sign";
- determines ownership, heirship, probate requirements, court outcomes, or title
  status;
- claims to be a lawyer or substitute for legal counsel;
- shares a user's information with any partner without explicit consent.

Instead it uses **attorney-informed issue spotting** and safer language such as:
"Your answers suggest this *may* involve a probate, title, tax, or heirship
question," and "A licensed attorney can help determine whether this option applies."

## Build stages (MVP plan)

1. **Public website & education hub** — landing page, education, document
   checklist, office guide, disclaimers, "Start" button.
2. **Guided screener & digital navigator** — conversational intake, decision tree,
   pathway recommendations, roadmap output, email/download.
3. **Partner referral & tracking** — consent-based referral, routing, status,
   escalation flags, navigator dashboard, quarterly reporting.
4. **Pilot replication system** — data dashboard, conversion tracking, bottleneck
   analysis, expansion playbook beyond Kashmere Gardens.

## Pilot focus

Kashmere Gardens / Super Neighborhood 52, City of Houston, Harris County, Texas.

## A note on verification

**All** public office addresses, phone numbers, emails, websites, and program
details in the resource directory are placeholders pending verification against
official sources before any public launch. See
[docs/07-resource-directory.md](./docs/07-resource-directory.md).
