# Lovable Build Prompt — HLB 7811 Harrisburg RFP Reviewer Platform

**How to use this file:** Copy everything below the line into Lovable as your
project prompt. It is written so Lovable can generate the full application. After
it builds, follow the "Setup checklist" at the very bottom (connect Supabase and
the Claude API key). Build the prototype with **sample/fake data only** until the
project is transferred to an HLB-owned workspace.

---

## Project: Houston Land Bank — 7811 Harrisburg RFP Reviewer Platform

Build a secure internal web app that helps Houston Land Bank (HLB) staff review
developer proposals for the **7811 Harrisburg Blvd Development Partner RFP**.
Reviewers upload a submission, get walked through every review section, receive
**real-time AI feedback** from an embedded assistant, score the proposal against
the official 100-point rubric, and export a structured report. The app supports
three reviewers and three submissions, then aggregates scores and produces a
side-by-side comparison.

This is a serious public-procurement tool: plain-language, fair, well-documented.
It supports reviewers' judgment; it does not replace the Evaluation Committee or
the HLB Board, and it is not legal advice or a final underwriting opinion.

### Tech and architecture
- React + Tailwind front end (Lovable default), clean and professional.
- **Supabase** for auth, database, and file storage (Storage bucket for uploads).
- A **backend/edge function** that calls the **Anthropic Claude API**
  (model `claude-opus-4-8`, with `claude-sonnet-4-6` as a cheaper fallback
  option in settings). The API key is stored as a server-side secret — never in
  the browser. (Anthropic does not train on API inputs, which suits confidential
  submissions.)
- PDF/DOCX text extraction for uploaded files (extract text client- or
  server-side) so the AI can read proposal content. Store extracted text with the
  submission.

### Authentication and roles
- Email/password or magic-link login restricted to HLB staff. Allow an admin to
  invite users; default to allowing only pre-approved email addresses.
- Roles: **Reviewer** (does reviews) and **Coordinator/Admin** (manages
  submissions and users, sees aggregation/comparison across all reviewers).
- Every action is tied to a logged-in user for the record.

### Data model (Supabase tables)
- `profiles`: id, full_name, email, role.
- `submissions`: id, letter (A/B/C), developer_name, created_by, created_at,
  status.
- `submission_files`: id, submission_id, filename, storage_path, file_type,
  extracted_text, uploaded_by, uploaded_at.
- `reviews`: id, submission_id, reviewer_id, status (draft/provisional/final),
  updated_at. One review per (submission, reviewer).
- `review_sections`: id, review_id, section_key, content (JSON) — holds each
  section's structured answers and notes.
- `scores`: id, review_id, category_key, points, evidence, concerns, confidence.
- `ai_messages`: id, review_id, section_key, role (user/assistant), content,
  created_at — the AI conversation log per section (part of the record).

### Core screens / flow

**1. Dashboard**
- Shows the three submissions (A, B, C) with developer name and each reviewer's
  status. A reviewer sees their own progress; an admin sees everyone's.
- Buttons: "Manage submissions" (admin), "Start/continue my review."

**2. Submission setup + upload** (admin or reviewer, per HLB preference)
- Set developer/team name for a submission letter.
- **Upload area**: drag-and-drop multiple files (proposal, sources & uses, pro
  forma, site plans, unit mix, AMI table, audited financials, references,
  commitment/support letters, resumes, design drawings, required forms). Show the
  file list; extract and store text from each.

**3. Guided review** — the heart of the app. A left sidebar lists the sections
below; the main panel shows one section at a time with its inputs PLUS an
**AI assistant panel** on the right. Autosave every change. Sections:

  1. **Scope & snapshot** — confirm files present; capture proposal snapshot
     (developer, structure, tenure, total units, unit mix, AMI mix, community
     space, ground lease vs purchase, total dev cost, requested HLB
     contribution, financing sources, timeline, key partners, community
     benefits) and a one-line bottom line.
  2. **Responsiveness** — the 33-item checklist (below). For each: status
     (Provided / Partially / Missing / Unclear), notes, risk (Low/Med/High).
  3. **RFP alignment** — rate each requirement (below): Strongly / Generally /
     Partially / Weakly aligned / Not addressed, with notes.
  4. **Financial feasibility** — guided prompts (below) + notes.
  5. **LIHTC & capital stack** — guided prompts (below) + notes.
  6. **Community benefit & design** — guided prompts (below) + notes.
  7. **Scorecard** — the six rubric categories (below): points input bounded by
     each max, evidence, concerns, confidence (High/Med/Low). Show a **live
     running total out of 100** with a color band.
  8. **Red flags** — notes by category (below).
  9. **Questions for the developer** — grouped (below).
  10. **Questions for the reviewer** + **Recommendation** (Advance to interview /
      Advance with conditions / Hold for clarification / Do not advance / Unable
      to determine) with rationale, conditions, top three issues, suggested
      internal handoffs (legal, finance, community engagement, design), Board
      framing.
  11. **Reviewer notes** — free text the reviewer can paste into internal notes.

**4. AI assistant (real-time, in every review section)**
- A chat panel where the reviewer can ask things like "Is this LIHTC structure
  realistic?", "What does DSCR mean?", "Should I worry about the funding gap?",
  "How should I score this if the pro forma is missing?"
- The assistant is sent: the system prompt (below), the current section, the
  submission's extracted file text, and the reviewer's entries so far. It replies
  in plain language and connects answers back to the RFP and the proposal.
- Add buttons: **"Summarize this submission,"** **"Check responsiveness,"**
  **"Draft this section for me (provisional),"** and **"Suggest a score with
  rationale"** — each sends a targeted instruction to the assistant. Drafts are
  clearly labeled provisional and always editable by the reviewer.
- The assistant must never invent facts not in the uploaded documents; if
  information is missing it says so and flags it. Distinguish a scoring issue
  from a clarification issue.

**5. Export**
- Export a single review as a formatted report (the 15-section structure) to
  **PDF and Markdown**.
- Mark a review provisional vs final.

**6. Aggregation & comparison (admin)**
- **Aggregated scorecard**: for each submission, show every reviewer's score per
  category and the average; flag categories where reviewers diverge widely.
- **Comparison analysis**: a side-by-side table across submissions (developer,
  tenure, total units, deepest affordability, % units by AMI, community space,
  disposition, total dev cost, cost/unit, requested HLB participation, financing
  path, funding gap/status, guarantor, schedule realism, responsiveness, average
  score). Below it, category-by-category comparison and a "Suggest comparison
  summary" AI button (provisional, editable).
- Export aggregation + comparison to PDF/Markdown.

### Tone
Plain language. Assume reviewers are smart public-service professionals who may
not know affordable-housing finance. Explain terms simply (capital stack,
sources & uses, NOI, DSCR, LIHTC equity, soft debt). Be fair and direct; don't
overstate concerns; never endorse without evidence.

---

## Embedded content (use exactly)

### Official 100-point scoring rubric (categories, max points, focus)
1. **Development Team Qualifications & References — 15** — experience/capacity in
   affordable, mixed-income, LIHTC; property-management strength; MWBE/HUB and
   vertically integrated affiliates; ≥3 references confirming similar delivery.
2. **Financing Strategy & Cost Competitiveness — 20** — strength/completeness of
   sources-and-uses and pro forma; commitment status; financial capacity/
   readiness; reasonable, competitive total cost and land terms; ability to close
   the gap.
3. **Project Concept, Design & Program — 20** — site plan/design quality;
   sustainability; universal accessibility; neighborhood fit; community meeting
   space + ground-floor retail where feasible.
4. **Affordability & Housing Mix — 20** — depth of affordability (≤50% AMI, ≤30%
   where possible); covenant clarity; strength of unit-size and tenure mix
   (rental + for-sale).
5. **Community Engagement & Local Benefits — 15** — defined engagement plan;
   locally owned/underrepresented business partnerships; local employment/
   training; resident services; Complete Communities alignment.
6. **Implementation Readiness & Schedule — 10** — realistic, detailed schedule;
   critical-path items; risk mitigation.

### Responsiveness checklist (33 items, with RFP reference)
1. Signed cover letter, authorized representative (6.1, 10.4)
2. Full development team + primary contact identified (6.1, 6.2)
3. Acknowledgment of Exclusive Negotiation Period (6.1)
4. Commitment to permanent affordability covenant (6.1)
5. Confirmation respondent bears all proposal costs (6.1, 8.2)
6. Developer, architect, engineer, GC, property mgr, key consultants identified (6.2)
7. Relevant affordable/mixed-income/TOD/LIHTC experience (6.2, 6.3)
8. MWBE / HUB participation identified (6.2, 6.6)
9. Legal ability to contract in TX and with HLB/federal funding (5.2, 6.2)
10. At least two comparable prior projects (6.3)
11. Prior project funding, partnership, occupancy, performance, lessons (6.3)
12. Underwriting pro forma / lender or investor docs for prior examples (6.3)
13. Detailed sources and uses (6.4)
14. Funding commitments with status: hard / soft / pending (6.4)
15. Preliminary operating pro forma (6.4)
16. Funding gap strategy (6.4)
17. Certified audit or compiled financials within 2 years (5.2, 6.4)
18. Guarantor identified (4.2, 6.4)
19. Willingness to provide guarantees (4.2, 6.4)
20. Conceptual site plan, massing, unit mix, community space, parking (6.5)
21. AMI table by income band and bedroom count (6.5)
22. Community engagement plan (6.6)
23. Local hiring / MWBE / resident services / community benefits (6.6)
24. Staffing chart and project organization (6.7)
25. Work plan and development schedule (6.8)
26. Financing application dates (LIHTC / bond volume cap) (6.8)
27. Cost proposal, itemized (6.9)
28. Ground lease or purchase assumptions (6.9)
29. Operating reserves (6.9)
30. Cost reasonableness statement, 2 CFR 200.404 (6.9)
31. Three references (6.10)
32. Required forms — debarment and non-collusion (12.0, 13.0)
33. Conflict / business conflict history disclosures (5.2, 14.0)

### RFP alignment items (rate each)
At least 25 units; at least 51% residential; all units ≤120% AMI; deeper
affordability below 80% AMI (and ≤50% / ≤30% where feasible); ground-floor
community-serving space, preferably on Harrisburg frontage; multigenerational
design; universal accessibility; sustainable building practices; reflects
single-family character (esp. north side) and avoids townhome-style typologies;
no direct curb cuts on Harrisburg; safe pedestrian/vehicular access; green/park
space and shared amenities; maintenance + security plan; sound/traffic
mitigation; transit-oriented design; community-serving retail/flex/food
truck/kiosk if included; clear lead/master developer if multiple entities.

### Financial feasibility prompts
Total development cost; cost per unit; hard costs; soft costs; land/ground-lease
assumptions; developer fee; financing costs; contingency; operating expenses;
reserves; revenue (rents or sales); NOI (if rental); debt service; DSCR (if
given); permanent loan sizing; sources-and-uses balance; funding gap; status of
each source (committed/pending/speculative/unclear); whether affordability mix
matches assumed rents/debt; whether community space is funded and sustainable;
what the stack depends on (LIHTC/bonds/grants/subsidy/philanthropy/deferred fee/
soft debt); whether timeline matches the financing path; who carries
predevelopment/construction/lease-up/operating risk; whether HLB is asked to
absorb risk directly or indirectly; whether the ground lease vs purchase benefits
HLB while preserving affordability.

### LIHTC & capital stack prompts
Is the LIHTC pathway clear (4% + tax-exempt bonds vs 9% competitive vs unclear)?
Volume cap needed? Schedule vs application/award cycles? Syndicator/investor/
lender/financial advisor named? Equity committed vs estimated vs speculative?
Credit-pricing assumptions? Bridge/construction/permanent conversion and soft
debt/gap financing? Does affordability match the likely structure? Prior LIHTC
closing experience? Property manager income-certification/compliance experience?
Long-term compliance risk addressed? (Unclear LIHTC = clarification issue, not an
automatic penalty.)

### Community benefit & design prompts
Responds to prior community engagement; supports multigenerational households;
respects single-family character; avoids townhome typology where it conflicts
with community preference; public green space + maintenance/security;
community-serving retail/flex space; supports local businesses; MWBE/HUB/locally
owned participation; local hiring/workforce/apprenticeships/training; resident
services/supportive programming; advances Complete Communities; avoids
displacement/community-trust concerns; creates long-term community value.

### Red-flag categories
Compliance; finance; LIHTC/tax-credit; design & site planning; community
benefit; operational; legal/deal-structure; schedule; HLB risk exposure.

### Developer-question groups
Financing; LIHTC & tax-credit structure; ground lease/purchase terms;
affordability; design; community engagement; operations & property management;
schedule; legal & compliance; HLB risk protection.

### Key RFP facts to keep visible in a "Project facts" reference panel
Site: 7811 Harrisburg Blvd, ~1.67 acres, Magnolia Park–Manchester, on the
METRORail Green Line. Disposition: sale or long-term ground lease; HLB retains
fee simple under a lease (capitalized payments at construction start/completion,
then annual % of NOI). Permanent affordability covenant recorded pre-construction.
HLB provides no financing guarantees; Development Partner is guarantor. Submission
deadline May 15, 2026; offers irrevocable 120 days; award on HLB Board approval.
Two-stage review (responsiveness + scoring, then optional written interview).
Confidential until award.

---

## AI assistant system prompt (use as the model's system message)

> You are an expert RFP Review Assistant for the Houston Land Bank Evaluation
> Committee, helping staff evaluate developer submissions for the 7811 Harrisburg
> Blvd Development Partner RFP. Be rigorous, fair, and plain-language. You support
> the reviewer's judgment; you do not replace it, and you do not provide legal
> advice or a final underwriting opinion.
>
> Act as a combined affordable-housing finance advisor, LIHTC/mixed-income
> reviewer, public-land disposition advisor, community-development evaluator, and
> RFP-compliance reviewer. Explain technical terms simply (capital stack, sources
> & uses, NOI, DSCR, LIHTC equity, soft debt).
>
> Review only the documents provided in this submission. Do not invent missing
> facts. If information is missing, say so clearly and identify what is missing.
> Distinguish strong evidence, weak evidence, and missing evidence, and
> distinguish a scoring issue from a clarification issue. Cite the proposal
> section or attachment when possible. Do not give high scores for promises
> without evidence. Treat scores as provisional until the reviewer confirms them.
>
> When the reviewer asks a question, answer in this structure: (1) plain-language
> answer; (2) why it matters for HLB; (3) what evidence to look for; (4) how it
> may affect scoring; (5) a suggested follow-up question if useful. Use the
> official 100-point rubric, the responsiveness checklist, and the RFP
> requirements provided to you.

---

## Confidentiality & ownership (build these in)
- Proposals are confidential procurement records until award. Restrict access to
  logged-in HLB staff; do not expose files or data publicly.
- Store the Claude API key only as a server-side secret.
- Show a short banner: "Internal HLB use. Confidential until award. Not legal
  advice or a final underwriting opinion."
- Prototype with sample data only; load real submissions only after the project
  is transferred to an HLB-owned workspace with HLB-controlled keys.

## Setup checklist (after Lovable builds)
1. Connect Supabase (auth, database, Storage bucket for uploads).
2. Add the Anthropic API key as a server-side secret; wire the edge function.
3. Create the three submissions (A/B/C) and invite the three reviewers + admin.
4. Test the full flow with a fake sample proposal.
5. When ready, transfer the Lovable project to HLB's workspace and reconnect
   GitHub, Supabase, and the API key under HLB's control before loading real
   submissions.
