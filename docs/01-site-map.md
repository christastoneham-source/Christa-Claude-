# Deliverable 1 — Full Site Map

The platform has two surfaces that share one back end: a **resident-facing**
navigator and a **partner-facing** console. Public education pages are open;
the screener requires consent; the partner console requires authentication.

## 1. Public / resident surface (open)

```
/  (Home / Landing)
├── /what-is-heirs-property        Education: heirs' property & tangled title
├── /how-it-works                  What the tool does / does not do
├── /probate-101                   Plain-language probate & estate education
├── /document-checklist            Records to gather (printable)
├── /harris-county-offices         Guide to county offices & what they do
├── /resources                     Legal aid, housing, tax, disaster resources
├── /education                     Education Card Library (browsable index)
│   └── /education/:slug           Individual education card (e.g. /education/probate)
├── /disclaimer                    Full legal disclaimer
├── /privacy                       Privacy notice & data practices
├── /accessibility                 Accessibility & language-access statement
├── /espanol                       Spanish entry point (mirrors key pages)
└── /start                         Begin assessment → enters guided screener
```

### Guided screener (consent-gated conversational flow)

```
/start
├── Step 0  Welcome & Consent              (Section 1)
├── Step 1  Property Location              (Section 2)
├── Step 2  Current Owner Status           (Section 3)  ── first major branch
├── Step 3a Living Owner                   (Section 4)  ── Prevention branch
├── Step 3b Deceased Owner                 (Section 5)  ── Intervention branch
├── Step 4  Family & Heirship Context      (Section 6)
├── Step 5  Estate & Probate Documents     (Section 7)
├── Step 6  Real Property Records          (Section 8)
├── Step 7  Taxes & Exemptions             (Section 9)
├── Step 8  Property Condition & Stability  (Section 10)
├── Step 9  Your Goal                       (Section 11)
├── Step 10 Review your answers
└── /roadmap                                Generated Family Property Roadmap
        ├── View on screen
        ├── Download PDF
        ├── Email to me
        ├── Ask a follow-up question  → Conversational Legal Navigation Mode
        └── Connect me with help      → Consent-based referral handoff
```

### Conversational Legal Navigation Mode (post-roadmap)

```
/roadmap/chat
├── Plain-language explanations
├── Issue-spotting questions
├── Records to gather
├── Public-office referrals
├── Attorney questions
└── Practical preparation steps
    (never: legal conclusions, ownership/heirship determinations, filing directives)
```

## 2. Partner / navigator surface (authenticated)

```
/partner  (login)
├── /partner/dashboard             Queue, status overview, escalation flags
├── /partner/referrals             Inbound referrals (consent-verified)
│   └── /partner/referrals/:id      Single referral: shared screener results,
│                                    document readiness, navigator notes,
│                                    handoff & status, closed-loop confirmation
├── /partner/escalations           Urgent flags (tax sale, foreclosure, coercion…)
├── /partner/assignments           Partner assignment & routing
├── /partner/reports               Quarterly reporting & aggregate dashboard
│   ├── Outreach conversion
│   ├── Pathway distribution
│   ├── Denial-reason tracking
│   └── Bottleneck tracking
├── /partner/directory             Internal partner roster & roles
├── /partner/playbook              Handoff protocols, consent rules, escalation SOP
└── /partner/settings              Org profile, users, consent templates
```

## 3. Shared system services (back end)

```
- Consent service            Captures, scopes, and logs consent per partner
- Roadmap generator          Maps answers → pathways → roadmap sections
- Pathway engine             Decision tree (Deliverable 5)
- Escalation engine          Flag detection + urgent language (Deliverable 11)
- Referral router            Consent-based routing to partners (Deliverable 12)
- Education content service  Serves education cards (Deliverable 6)
- Resource directory service Serves verified office/partner data (Deliverable 7)
- Minimal-data store         No SSNs/bank/full DL; consent-scoped (Deliverable 9)
- Reporting / analytics      Aggregate & operational metrics (Deliverable 13)
```

## 4. Persistent UI elements (every page)

- Short disclaimer banner on the screener and roadmap.
- "This is not legal advice" footer link on every page.
- Language toggle (English / Spanish at minimum).
- "Leave this site" / privacy-safe exit affordance.
- Crisis/urgent help shortcut when an escalation flag is active.

## 5. Navigation map (top-level menu)

| Resident menu | Partner menu |
|---|---|
| Home | Dashboard |
| What is heirs' property? | Referrals |
| How it works | Escalations |
| Education | Reports |
| Harris County offices | Playbook |
| Resources | Settings |
| Start your roadmap (primary CTA) | — |
