# Deliverable 14 — Lovable-Ready MVP Build Prompt

Paste the block below into [Lovable](https://lovable.dev) to scaffold the MVP
(Stages 1–2: public education hub + guided screener + roadmap). Stages 3–4
(partner console, analytics) are noted as a follow-on.

---

```
Build a warm, accessible, mobile-first web app called "Harris County Heirs'
Property Navigator." It is an EDUCATIONAL navigation tool — NOT a legal service.
It must NEVER give legal advice, NEVER determine ownership or heirship, and NEVER
show scores, grades, rankings, or risk ratings. It is recommendation-based: it
spots issues, routes users into pathways, and produces a personalized "Family
Property Roadmap."

TONE & DESIGN
- Compassionate, plain language (~6th–8th grade), no legal jargon unless instantly
  explained. Calm, trustworthy, community-centered. Mobile-first, high contrast,
  large tap targets, screen-reader friendly. English + Spanish toggle.
- Never make the user feel judged or tested. Show progress as a gentle journey, not
  a grade.

GLOBAL ELEMENTS
- Persistent footer link "This is not legal advice" → /disclaimer.
- A reusable Disclaimer banner component.
- Store all legal/disclaimer strings in one constants file.

PAGES (Stage 1 — Education Hub)
- / (Landing): core promise, what the tool does/doesn't do, disclaimer, primary CTA
  "Start your roadmap", secondary links "Learn first" and "Browse resources."
- /what-is-heirs-property, /how-it-works, /probate-101, /document-checklist,
  /harris-county-offices, /resources, /education (card index), /education/:slug
  (single card), /disclaimer, /privacy, /accessibility.
- Education cards use a 5-part template: What it is / Why it matters / Records
  involved / Harris County office / Question to ask an attorney.

GUIDED SCREENER (Stage 2 — conversational, one question at a time)
- /start runs a step-by-step flow. EVERY question offers: Yes / No / I do not know /
  I need help finding this / This does not apply / I want to skip this. Allow Back,
  Save & resume.
- Sections in order:
  1. Welcome & Consent — require checkbox "I understand this tool is educational and
     does not provide legal advice." Warn: do NOT enter SSNs, full bank numbers, or
     highly sensitive info.
  2. Property Location (Harris County? address; City of Houston?; Kashmere Gardens /
     Super Neighborhood 52?; occupancy; property type).
  3. Current Owner Status (owner name; living/deceased/unknown; user is owner?;
     related?; lives there?; "in the estate of"?; deed updated?). This is the FIRST
     BRANCH.
  4. If owner LIVING → Living-Owner Prevention questions.
  5. If owner DECEASED or UNKNOWN → Deceased-Owner questions (date of death, will,
     original will, filed, probate, executor, trust, TOD deed, affidavit of
     heirship, small estate affidavit, court orders, family disagreement, multiple
     heirs, taxes current/delinquent).
  6. Family & Heirship Context.
  7. Estate & Probate Documents (checklist; for each missing, note where to find it).
  8. Real Property Records.
  9. Taxes & Exemptions (always remind: exemptions may reduce taxes but do not
     resolve title).
  10. Property Condition & Housing Stability.
  11. Goal (multi-select).
  12. Review answers (editable) → Generate Roadmap.

PATHWAY ENGINE (issue spotting only — additive, multiple allowed: A–K)
- A Living Owner Prevention (owner living)
- B Deceased With Will / C Deceased Without Known Will
- D Informal "Passed Down" / E Multiple Heirs / F Family Conflict or Pressure
- G Tax Delinquency or Foreclosure Risk / H Keep & Repair / I Sell/Transfer/
  Redevelop / J No One Knows Where to Start / K Vacant/Abandoned/"In the Estate Of"
- Route by owner status, then overlay rules (delinquent taxes→G, multiple heirs→E,
  disagreement/pressure→F, passed-down-no-paper→D, vacant/"in estate of"→K, goal→H/
  I, many unknowns→J).

ESCALATION FLAGS (change tone + ordering; NEVER a score)
- Trigger on: tax-sale/foreclosure notice, lawsuit/court papers, certified mail,
  pressure to sign, suspected coercion/predatory buyer, elderly/disabled occupant at
  risk, displacement risk, unsafe condition, no one paying taxes, "in the estate of,"
  repair/disaster denial due to title, signed sale contract, fast cash offer.
- When any fires, show verbatim: "Because you mentioned a notice, court paper, tax
  issue, foreclosure risk, or pressure to sign documents, this may require urgent
  review by a licensed attorney or qualified legal aid organization. This tool
  cannot tell you what legal action to take, but it can help you organize records
  and questions to bring to a professional as soon as possible." Put the urgent
  pathway at the top of the roadmap.

FAMILY PROPERTY ROADMAP (/roadmap) — NO scores, NO legal conclusions. 14 sections:
1 Educational Disclaimer, 2 What You Shared, 3 What This May Mean (issue spotting),
4 Recommended Pathway(s), 5 Why This Pathway, 6 Records to Gather (with where to
find each), 7 Harris County Offices to Contact (with why), 8 Questions to Ask an
Attorney, 9 Questions to Ask Public Offices, 10 Non-Legal Support Referrals, 11
Things to Avoid Until Legal Review, 12 Suggested Next 30 Days, 13 Longer-Term
Protection Steps, 14 Closing Message (verbatim): "You do not have to resolve every
issue at once. The first step is understanding what is known, what is missing, and
who can help. This roadmap is designed to help you prepare for informed
conversations with qualified professionals and public agencies."
- Roadmap actions: View, Download PDF, Email to me.

CONVERSATIONAL MODE (/roadmap/chat) — after the roadmap, allow follow-up questions.
The assistant MAY give: plain-language explanations, issue-spotting questions,
records to gather, public-office referrals, attorney questions, prep steps. The
assistant MUST NOT give: legal conclusions, ownership/heirship determinations, court
strategy, filing/sign/sell/transfer directives, or outcome predictions. If asked for
legal advice, respond verbatim: "I cannot provide legal advice or tell you what
legal action to take. I can explain the general issue, help you identify records to
gather, and suggest questions to ask a licensed Texas attorney." Then keep helping
educationally.

GUARDRAILS (enforce everywhere, including AI output)
- NEVER output: "you should file probate," "you are the owner/heir," "this person
  owns the property," "this option applies to you," "this will clear your title,"
  "you qualify," "you should sell/transfer/sign."
- Prefer: "this may be something to discuss with a licensed Texas attorney," "your
  answers suggest this may involve a probate/title/tax/heirship question," "a
  licensed attorney can help determine whether this option applies," "this is not a
  legal conclusion."

PRIVACY
- Do NOT collect SSNs, bank account numbers, full driver's license numbers, or full
  DOB. Screen free-text for these patterns. Sharing with partners only with explicit,
  scoped consent.

DATA (local/simple store for MVP)
- Persist screener answers locally so the user can resume and edit. No login for
  residents. Keep a clean service boundary so a partner console + analytics
  (Stage 3–4) can be added later.

STACK
- React + TypeScript, component-based, Tailwind for styling. Clean, documented
  components: DisclaimerBanner, QuestionCard (with the 6 standard answer options),
  EducationCard, RoadmapSection, EscalationNotice, ConsentGate.

DELIVER Stages 1–2 now. Leave clear TODO hooks for Stage 3 (consent-based partner
referral + warm handoff + navigator dashboard) and Stage 4 (aggregate analytics).
```

---

## Notes for the builder

- The pathway logic, question wording, education cards, resource directory,
  disclaimers, and roadmap template in this repo (`/docs`) are the source content to
  load into the app.
- Keep all public office contact details behind a `[VERIFY]` flag until confirmed
  (see [Deliverable 7](./07-resource-directory.md)).
- Stage 3–4 require a backend (auth, consent service, partner roles); plan that as a
  second Lovable iteration or a dedicated backend.
