# Deliverable 20 · Lovable build prompts · The Investment Map proposal for HDDC

Prepared October 12, 2026. Replaces the earlier version of this file.

The Kresge page was written to a funder deciding where grants go. HDDC is an owner and
developer deciding what to build, how to finance it, and what role to take. Same layout,
different buyer, different pain. Every line of copy below is written for HDDC. Nothing is
carried over from Kresge except Christa's own biography, stats, and case studies.

Paste the three prompts into Lovable one at a time, in order. Wait for each build to finish
and check it before sending the next. Three short prompts land cleaner than one long one.

1. Prompt A builds the /hddc page: palette, layout, and every line of copy.
2. Prompt B hosts the live demonstration and adds the quick tour component.
3. Prompt C sweeps out anything left from Kresge and runs the checks.

Fill the four placeholders before pasting: [ACCESS WORD], [DEMO URL], [PROPOSAL DATE],
[PORTRAIT]. The table at the end says where each comes from.

---

## Prompt A · Build the /hddc page

```
Create a new page at the route /hddc. Use the Kresge proposal page only as a layout reference: same section order, same components, same password gate pattern, same print to PDF behavior, same spacing scale. Do not copy any Kresge copy, colors, or images except the four case study images and the portrait. Do not edit the Kresge page. Put every line of copy for /hddc in one constants file, src/content/hddc.ts, so copy edits never touch layout code.

PALETTE (HDDC brand, sampled from HDDC's own logo file)
Create these tokens and use only these on /hddc:
  hddc-navy        #214083  HDDC wordmark blue. Display headings, section numbers, eyebrow labels, links, table header row, filled legend dots, gate button background, primary buttons, stat figures.
  hddc-teal        #2494A5  HDDC skyline teal. Italic accent words inside large headlines (32px and up only), card top borders, stat card borders, icons, focus rings, the left border of tinted boxes.
  hddc-teal-deep   #1B6E7B  Darker teal for anything small: the Recommended ribbon background (white text), small labels that would otherwise be teal, hover state of links.
  hddc-lime        #AED153  HDDC house line green. Decorative only: the right end of the horizontal rule, the top border of the recommended tier card, the half dot in the legend, a 6px bar on top of each numbered card. Never use lime for text and never put text directly on lime smaller than 18px.
  hddc-ink         #1E2A3B  Body text.
  hddc-muted       #5A6578  Secondary text, captions, footnotes.
  hddc-paper       #FFFFFF  Page background.
  hddc-mist        #F3F6FB  Background for every other full height section, and for tinted boxes.
  hddc-line        #DCE2EE  Hairline borders and table rules.
  hddc-teal-tint   rgba(36,148,165,0.08)  Fill of the What it demonstrates boxes and the Honest framing box.
  hddc-lime-tint   rgba(174,209,83,0.18)  Fill of the Tier 2 column in the details table.
The horizontal rule on the cover and on the close is 4px tall and runs hddc-navy to hddc-teal to hddc-lime, left to right, never reversed.
Remove every Kresge color token from /hddc. No gold, no Kresge navy, no cream page background.
Typography stays as on the Kresge page: Fraunces for display headings, Inter for body, small uppercase eyebrow labels with letter spacing in hddc-navy.

LANGUAGE RULES (apply to every string on /hddc)
Never use: software, platform, product, tool, AI, AI powered, app, patent pending. Say instrument, decision environment, analysis, demonstration.
No em dashes and no hyphenated words anywhere. Write "non displacement", "place based", "Black owned", "decision ready", "side by side", "board ready".
Short sentences. Active voice. No exclamation points.
Name the organization "Historic District Development Corporation" on first use in each section, then "HDDC".
Name the leader "Cheneé Joseph, President and CEO". Keep the accent on Cheneé.

GATE
Title: "The Investment Map"
Line: "Prepared for Historic District Development Corporation. Confidential."
Access word: [ACCESS WORD]
Wrong word message: "That is not the access word. Check the note that came with this link."

COVER
Eyebrow: "PREPARED FOR HISTORIC DISTRICT DEVELOPMENT CORPORATION · ATLANTA · [PROPOSAL DATE]"
Headline, two lines, the second line in hddc-teal italic: "A decision instrument for" / "Sweet Auburn."
Lede: "Turning HDDC's next decisions into ones you can fund, defend, and build, with the receipts."
Rule beneath.

SECTION 01 · WHO I AM
Headline: "I build the systems that move community capital."
Portrait at left: [PORTRAIT]. Caption: "Christa Stoneham · Founder, Connecting Dots and Strategies"
Paragraph 1: "I am Christa Stoneham. Architect by training, with two decades of practice in community development across acquisition, disposition, capital stacking, and community engagement."
Paragraph 2: "I currently serve as President and CEO of the largest geographic land bank in the United States, stewarding a public portfolio of vacant and tax delinquent property, and the decisions that move that land from liability to community asset."
Paragraph 3: "Connecting Dots and Strategies is the advisory practice I founded to bring that same operator discipline to community development corporations, cities, CDFIs, and foundations weighing place based capital decisions."
Paragraph 4: "The instrument you will see today is built from real redevelopment, land banking, brownfield, housing, and community development work. I built this version for HDDC, to help move Sweet Auburn's next decisions from vision to decision, and from decision to implementation."
Three stat cards, hddc-navy figures, hddc-teal top border: "$150M+" / "Land assets stewarded" · "$100M" / "Property reactivated" · "100+" / "Affordable homes"

PROOF OF PRACTICE
Headline: "Built from real decisions involving land, capital, environmental risk, housing, and community trust."
Note: "These examples are intentionally summarized at a high level. Project names, partners, and full figures can be shared with the right context."
Four case study cards, alternating image left and right, in this order. Reuse the matching image from the Kresge page for each case. Each card has Capital moved, What the work required, and a tinted What it demonstrates box with an hddc-teal left border.

01 "Contaminated Land to Neighborhood Future"
Summary: "Helped lead the reuse pathway for historically burdened property in a legacy Black community."
Capital moved: "$5.5 million in federal Brownfields funding secured for assessment and cleanup, including major cleanup funding for a long standing contaminated site."
What the work required: "Environmental strategy, federal funding, regulatory coordination, public accountability, resident trust, and a credible long term vision for land that had carried decades of harm."
What it demonstrates: "Site decisions sit on top of history, risk, trust, and timing. Sweet Auburn carries all four. I have worked where the stakes were real and the path forward needed technical structure and community accountability at the same time."

02 "Resilient Housing on Overlooked Land"
Summary: "Small and difficult parcels translated into a housing pipeline for affordable, resilient, and accessible homes."
Capital moved: "More than $700K in design, planning, technical assistance, and partner support aligned around replicable home plans and resilient housing implementation."
What the work required: "Design standards, builder readiness, community input, resilience criteria, partner coordination, and a scalable approach for turning scattered parcels into housing production."
What it demonstrates: "How to connect parcel level conditions to housing production at scale. It is the block by block method HDDC pioneered in the 1990s, run with a production system behind it."

03 "Public Land to Community Asset"
Summary: "Led decisions across a large public portfolio of vacant, tax delinquent, and underused property in a major American city."
Capital moved: "More than $100 million in property value put back in play through public land stewardship, disposition, and redevelopment activity."
What the work required: "Parcel strategy, partner selection, legal authority, affordability terms, development readiness, public accountability, and a repeatable way to decide which properties should move, when, to whom, and for what outcome."
What it demonstrates: "How land moves from liability to community asset, and how to build the decision system that makes each choice clearer, faster, and easier to defend in front of a board and a lender."

04 "Brownfield to Housing Opportunity"
Summary: "Helped move a former transportation and industrial site from environmental uncertainty toward a new affordable housing future."
Capital moved: "More than $12 million in publicly documented acquisition and predevelopment capital helped assemble the site and position it for roughly 120 multifamily units and 40 single family homes."
What the work required: "Brownfield assessment, demolition sequencing, public agency coordination, financing alignment, community storytelling, and a reuse strategy that could carry both neighborhood memory and future housing need."
What it demonstrates: "How to turn a complicated site into an implementation pathway when contamination, cost, capital gaps, and community expectation all arrive at once. HDDC knows this path. Dynamic Metal Lofts was the first cleanup completed under Georgia's brownfield law."

SECTION 02 · THE PROBLEM
Headline: "Good deals stall when the numbers miss the neighborhood."
Intro: "Across Sweet Auburn and the Old Fourth Ward, the same three patterns slow the work. The commitment is there. The decision picture is not."
Three cards with small line icons in hddc-teal:
Card 1 title: "The appraisal misreads the place." Body: "Comparable sales carry decades of disinvestment. They miss what a walkable, historic, transit served district is worth today. When the value comes in low, the capital stack breaks and the team rebuilds the case under deadline."
Card 2 title: "Every phase starts from scratch." Body: "Parcel data, credit eligibility, TAD terms, design review status, and partner terms sit in separate files. The next phase, the next acquisition, and the next block each restart the same work."
Card 3 title: "The principles are hard to show in numbers." Body: "Lenders read the pro forma. Funders ask for impact. Residents ask who gets to stay. Historic preservation, non displacement, and sustainability live in the mission statement, not in the model the deal is judged by."
Closing line, Fraunces, hddc-navy: "The work is strategic. The current process makes it harder to move."

WHAT I'M HEARING
Headline: "I am bringing four working assumptions into this conversation."
Four numbered cards, each with a 6px hddc-lime bar on top:
01 Title: "Front Porch proved Auburn Avenue can build again." Body: "Front Porch opened in April 2025, the first new development on its stretch of Auburn Avenue in nearly two decades. Phase II and the parcels around it are the next decisions, with real timing, lenders, and partners."
02 Title: "The role question is real." Body: "HDDC has led as owner and developer at Front Porch, contributed its land to a partnership with Mercy Housing Southeast at Henderson Place, and developed with partners at Flats at The Indie and Auburn Glenn. Each new deal asks which role fits and what exposure comes with it."
03 Title: "HDDC is becoming a capital investment corporation." Body: "That is HDDC's own language for its next chapter. An investor's discipline needs a decision trail a board, a lender, and an appraiser can each follow."
04 Title: "The principles should score the deal." Body: "Historic preservation, non displacement, and sustainability have guided HDDC since Coretta Scott King, Christine King Farris, and John Cox founded it in 1980. They belong inside the numbers, read scenario by scenario."
Italic line under the cards: "Your corrections set the scope."

THE PORTFOLIO, LIVE
Eyebrow: "THE PORTFOLIO, LIVE"
Headline: "Let me show you three decisions."
Italic subline: "Three deal types, one engine, live."
Intro: "I built the decision types in front of HDDC into one live decision environment. This demonstration runs on stylized parcels so nothing confidential leaves your office. In the engagement it runs on HDDC's parcels of record. You will see a historic district on a schematic grid, a single site under eight deal structures, and a larger bank owned site under three subdivision concepts and three price bases. Every number moves when an assumption moves. The capital stack keeps the gap in view. A principles check reads every scenario against non displacement, historic preservation, and sustainability."
Eyebrow: "ONE INSTRUMENT · FOUR MOVES". Four cards:
"See the district": "Parcels, four HDDC pillars, and historic preservation as its own construction mode, with the federal and Georgia historic credit lines in the capital stack."
"Build the scenarios": "Assign pillars, change any assumption, save a scenario, and put scenarios side by side."
"Price the structure": "Eight deal structures for one site. Three subdivision concepts and three price bases for a larger one. One compare table for each."
"Read the role and the principles": "Advisor or Equity Partner. The toggle shows what closes the gap and what exposure that implies. The principles check shows what each choice does to residents, buildings, and the planet."
Below the four cards leave a full width slot with the id demo-slot. Prompt B fills it.
Eyebrow: "BUILT FOR GEORGIA". One row of four small chips with hddc-teal borders: "Federal 20% and Georgia 25% historic credits, with the per project cap" · "Invest Atlanta and TAD resources in the capital stack" · "Georgia EPD brownfield program" · "Fulton County effective property tax rate". Footnote under the chips: "Program rates and caps are planning assumptions. The engagement confirms each one with Georgia HPD, Invest Atlanta, and HDDC's tax advisor."
Tinted box with an hddc-teal left border, eyebrow "HONEST FRAMING", headline "The numbers are directional, by design." Body: "This model is built for early decisions. It compares scenarios before time and money are spent proving one path in full. The goal is relative impact, cost, and tradeoffs. The engagement calibrates every assumption to HDDC's data, standards, and investment method. Every projection is a planning estimate with editable assumptions. It is never an appraisal or a tax determination."

THE IMPACT
Headline: "What HDDC gets when its decisions run through the instrument."
Intro: "Four outcomes show up in every engagement. They are the outputs your team carries into the room where the decision gets made."
Four numbered cards:
01 "Decision ready pictures in days": "Phase II, the next acquisition, or the next block, organized for review in one place, with the assumptions stated."
02 "Value evidence before the appraisal": "A documented value story built from stated assumptions and directional estimates, ready before the appraiser walks the block. It informs the appraisal conversation. It never replaces an appraisal."
03 "Principles you can show": "Non displacement, historic preservation, and sustainability read for every scenario, in language a lender and a legacy resident both understand."
04 "One shared picture": "Staff, the board, lenders, Invest Atlanta, partners, and residents working from the same map, numbers, assumptions, and tradeoffs."

WHAT YOU ARE BUYING
Headline: "An instrument, a practice, or both."
Three cards:
01 "The Instrument": "A hosted decision environment your team operates directly. HDDC keeps the Sweet Auburn instance and every output for the engagement and any renewal term."
02 "The Practice": "Advisory from a practitioner who has moved land, capital, and community decisions at scale. The practice calibrates the instrument to the real deal."
03 "The Combination": "Tiers 2 and 3 pair both. The instrument gives speed and a shared picture. The practice gives judgment and defensibility."

ENGAGEMENT MODELS
Headline: "Three ways to work together."
Intro: "Each tier builds on the one before it. The work starts with one live decision, then grows into a portfolio view and a lender ready investment case."
Three tier cards. The middle card carries the Recommended ribbon (hddc-teal-deep background, white text) and an hddc-lime top border.
Tier 1 "Phase II Clarity". Time: "6 to 8 weeks". Investment: "$" with "Confirmed after scoping." Outcomes: "A live decision environment for one HDDC decision, recommended Front Porch Phase II, on parcels of record" · "Deal structures, capital stack, and the gap for that decision, with the Advisor or Equity Partner read" · "The principles check on every scenario" · "Partner Brief exports and a hosted link your team operates directly" · "Onboarding and a user guide".
Tier 2 "Sweet Auburn Portfolio". Time: "6 months and up". Investment: "$$" with "Confirmed after scoping." Outcomes: "Everything in Tier 1 across all three deal types, calibrated to HDDC's data, standards, and investment method" · "A practitioner working alongside your team in structured working sessions" · "A prioritized pipeline across Phase II, Herndon Plaza, and the next block, scored on HDDC's three principles" · "Georgia historic credit, TAD, and brownfield screening by site, with funding pipeline tracking against the gap" · "Built to feed the Sweet Auburn Equitable Development and Preservation Strategy now underway with the Georgia Tech Urban Design Studio" · "A documented decision trail your board and lenders trust".
Tier 3 "Investment Case". Time: "9 to 12 months". Investment: "$$$" with "Confirmed after scoping." Outcomes: "Everything in Tier 2, delivered to full feasibility grade" · "Detailed pro formas, capital stack options, and sources and uses by priority site" · "An appraisal support package: the value story, comparable logic, and assumptions, ready for the appraiser" · "A lender and board ready investment packet and recommendation" · "Application support for Invest Atlanta and Georgia DCA resources" · "An implementation roadmap with phases, partners, funding sequence, and milestones" · "In person working sessions in Atlanta, priced as a scoped component".
Eyebrow "HOW THE INVESTMENT IS BUILT", four small cards: 01 "Instrument license" / "for the Sweet Auburn instance" · 02 "Advisory retainer" / "monthly, Tiers 2 and 3" · 03 "Feasibility components" / "priced per module" · 04 "Annual license and support" / "after the engagement".
Footnote 1: "Investment will be confirmed after budget guidance, scope, users, term, and level of support are defined."
Footnote 2: "Any tier can be underwritten in whole or in part by a capacity building or technical assistance grant. I will help HDDC package that request."

THE DETAILS
Headline: "Every deliverable, side by side."
Legend: filled hddc-navy dot "Live in the instrument now" · half dot, hddc-navy and hddc-lime "Partially built" · empty dot with hddc-navy outline "Built during the engagement" · a thin dash in hddc-muted "Not in this tier".
Table: header row hddc-navy with white text: "Deliverable", "Tier 1 · Phase II Clarity", "Tier 2 · Sweet Auburn Portfolio ★", "Tier 3 · Investment Case". Tier 2 column filled with hddc-lime-tint. Category rows in small caps hddc-navy. In each row below, the three marks are Tier 1, Tier 2, Tier 3.
DECISION ENVIRONMENT
  District grid with parcel reference data · filled, filled, filled
  Scenario builder across HDDC's four pillars · filled, filled, filled
  Construction modes with federal and Georgia historic credit lines · filled, filled, filled
  Capital stack with the gap and the Advisor or Equity Partner read · filled, filled, filled
  Principles check: non displacement, historic preservation, sustainability · filled, filled, filled
  Eight deal structures compared for one site · filled, filled, filled
  Three subdivision concepts and three price bases for a larger site · filled, filled, filled
  Scenario comparison and one page Partner Brief · filled, filled, filled
  Hosted link with access control · filled, filled, filled
  Shared workspace with accounts and roles · dash, empty, empty
DATA AND CALIBRATION
  Directional planning coefficients · filled, filled, filled
  HDDC parcels of record loaded · empty, empty, empty
  Calibrated to HDDC cost, rent, and outcome data · dash, empty, empty
  Georgia program assumptions confirmed with HPD and Invest Atlanta · dash, empty, empty
  Custom data integrations · dash, half, empty
STRATEGY AND ADVISORY
  Onboarding session and user guide · filled, filled, filled
  Structured working sessions and office hours · dash, empty, empty
  Prioritized pipeline: Phase II, Herndon Plaza, the next block · dash, empty, empty
  Weighted criteria from HDDC's principles and a decision log · dash, empty, empty
FINANCIAL ANALYSIS
  Site level financial views · dash, empty, empty
  Funding pipeline tracker against the gap · dash, empty, empty
  Full pro formas and capital stack options · dash, dash, empty
  Sources and uses by priority site · dash, dash, empty
  Appraisal support package · dash, dash, empty
ENVIRONMENTAL
  Georgia EPD brownfield and Hazardous Site Inventory screening · dash, empty, empty
  Phase I and Phase II status tracking · dash, empty, empty
  Remediation pathway integrated into the finance · dash, dash, empty
BOARD AND LENDER MATERIALS
  Partner Brief exports · filled, filled, filled
  Documented decision trail · dash, empty, empty
  Lender ready investment packet · dash, dash, empty
  Board ready presentation and recommendation · dash, dash, empty
IMPLEMENTATION
  Implementation roadmap with phases and milestones · dash, dash, empty
  In person working sessions in Atlanta · dash, dash, empty
  Alignment narrative for HDDC's board, lenders, and partners · dash, dash, empty

CLARIFYING QUESTIONS
Headline: "The right scope depends on the decision, the users, and the level of confidence needed."
Three numbered cards with an hddc-teal left border:
01 "Who is the primary user?": "Your team, the board, lenders, Invest Atlanta, partners, or a combination?"
02 "Which decision comes first?": "Front Porch Phase II, Herndon Plaza, or the next block? What needs to be decided, by whom, and with what evidence?"
03 "What would make this a clear yes?": "What would create confidence, and what would give you pause? What would the next step be?"
Eyebrow "THE FEATURE SET IS A MENU, NOT A MYSTERY". Headline: "Three ways any feature enters the Sweet Auburn instance."
Three cards:
"CORE · Ships in every engagement": District grid · Scenario builder · Deal structure comparison · Subdivision concepts · Capital stack and the gap · Principles check · Partner Brief · Hosted access
"CONFIGURABLE · Set during scoping": Pillars and outcome measures · Market profiles and Georgia program assumptions · Principle weights · Branding · Access levels
"BUILT TO ORDER · Scoped in Tiers 2 and 3": Financial modules · Appraisal support package · Environmental screening · Custom data integrations · Fiscal impact views · Shared workspace with accounts and roles · Additional sites and districts

CLOSE
Rule above. Headline, two lines, the second in hddc-teal italic: "Let's scope what this looks like for" / "Sweet Auburn."
Body: "Thank you for your time, the opportunity, and the work HDDC has carried on Auburn Avenue since 1980. I would be honored to build this with you."
Contact block in Fraunces: "Christa Stoneham, Founder, Connecting Dots and Strategies LLC" / "info@christastoneham.com" / "www.christastoneham.com"
Last line, small, hddc-muted: "Reclaiming the map."

BEHAVIOR
Same as the Kresge page: smooth scroll between full height sections, visible focus states in hddc-teal, reduced motion respected, one column on phones with 16px side gutters and no horizontal scroll. Print to PDF breaks before each section.
```

---

## Prompt B · Host the demonstration and add the quick tour

Before you send this prompt, host the demonstration file and get its link. Use one of these.

1. Recommended: open app.netlify.com/drop, drag `investment-map/index.html` from this repo onto
   the page, and copy the link it gives you. One minute, no account needed to start.
2. Or attach `investment-map/index.html` to the Lovable chat with this prompt and tell
   Lovable to save it unchanged at `public/demo/investment-map.html`. Then [DEMO URL] is
   `/demo/investment-map.html`. Check that Lovable did not rewrite the file: it should open
   on its own at that path and look exactly like the screenshots in `investment-map/screenshots/`.

The demonstration already supports these links:

| Link | What it opens |
|---|---|
| [DEMO URL]#tour | The full guided tour, 18 steps, about two minutes |
| [DEMO URL]#tour-district | The District, with its own 8 step tour |
| [DEMO URL]#tour-site | The Five Acre Site, with its own 6 step tour |
| [DEMO URL]#tour-twenty | The Twenty Acres, with its own 6 step tour |
| [DEMO URL]#district, #site, #twenty | Opens that workspace, no tour |

```
On the /hddc page, fill the slot with the id demo-slot with a quick tour component and the live demonstration. Use only the hddc tokens.

Layout on screens wider than 1024px: a two column block. Left column 320px wide, the quick tour panel. Right column, the demonstration frame. On smaller screens, stack the panel above the frame.

QUICK TOUR PANEL
Eyebrow: "QUICK TOUR"
Headline, Fraunces, hddc-navy: "See it in two minutes."
Three numbered steps, each with an hddc-navy number circle:
1 "Open a workspace." "Each one is a live decision type."
2 "Change one assumption." "Watch the capital stack and the gap move."
3 "Save a scenario." "Then print the one page Partner Brief."
Four buttons stacked full width. The first is primary (hddc-navy background, white text). The others are outlined in hddc-navy.
  "Start the full tour" sets the frame src to [DEMO URL]#tour
  "Tour The District" sets the frame src to [DEMO URL]#tour-district
  "Tour The Five Acre Site" sets the frame src to [DEMO URL]#tour-site
  "Tour The Twenty Acres" sets the frame src to [DEMO URL]#tour-twenty
When a button is pressed, mark it active with an hddc-teal left border, set the frame src, and scroll the frame into view if it is off screen.
Small note under the buttons, hddc-muted: "Demonstration data. Stylized parcels, no real addresses. Your parcels load in the engagement."

DEMONSTRATION FRAME
Eyebrow above the frame: "LIVE DEMO · THE INVESTMENT MAP · PREPARED FOR HDDC"
An iframe with src [DEMO URL]#tour, title "The Investment Map, live demonstration", width 100%, height 760px on desktop and 640px on phones, 1px hddc-line border, 12px radius, loading lazy.
Under the frame, right aligned: a link "Open in a new tab" to [DEMO URL]#tour, target _blank, rel noopener.

PRINT
In print, hide the quick tour buttons and replace the iframe with a static card: hddc-mist background, hddc-teal left border, text "Live demonstration: [DEMO URL]#tour. Open the link for the guided tour."
```

---

## Prompt C · Sweep out Kresge and run the checks

```
Run these checks on /hddc only and fix every hit. Do not change the Kresge page.

1. Search every file used by /hddc, including src/content/hddc.ts, components, metadata, alt text, aria labels, the page title, the og tags, and the print stylesheet, for each of these terms, case insensitive, and remove or rewrite every hit: Kresge, Foundation (when it means Kresge), Detroit, Michigan, McNichols, W. McNichols, West McNichols, Live6, Livernois, ninety three, 93 parcels, corridor instrument, Corridor Clarity, Strategy Partnership, grantees, funder ready, assessor data, July 2026, tool.
2. Confirm no Kresge color token or hex value is used anywhere on /hddc. Every color must be one of the hddc tokens.
3. Confirm there are zero em dashes and zero en dashes in the copy, and no hyphenated words in visible text.
4. Confirm the banned words never appear: software, platform, product, tool, AI, app, patent pending.
5. Confirm "Cheneé" keeps its accent everywhere.
6. Confirm small text never uses hddc-teal or hddc-lime as its color. Small teal text uses hddc-teal-deep.
7. Set the page title to "The Investment Map · Prepared for HDDC" and the meta description to "A decision instrument for Sweet Auburn, prepared for Historic District Development Corporation."
8. Check the page at 390px wide: no horizontal scroll, the details table scrolls inside its own container, the quick tour panel stacks above the frame.
9. Print to PDF and confirm each section starts on a new page and the demonstration frame prints as the static card.
List what you changed when you are done.
```

---

## Placeholders

| Placeholder | What goes there |
|---|---|
| [ACCESS WORD] | One lowercase word. Send it in the note that carries the link, never in the same line as the link. |
| [DEMO URL] | The hosted demonstration from the Prompt B instructions. Netlify Drop link, or `/demo/investment-map.html` inside Lovable. |
| [PROPOSAL DATE] | Month and year the proposal goes out, for example OCTOBER 2026. |
| [PORTRAIT] | Reuse the portrait from the Kresge page. |

## HDDC palette, for reference

| Token | Hex | Where it comes from | Use |
|---|---|---|---|
| hddc-navy | #214083 | HDDC wordmark | Headings, numbers, links, table header, primary buttons |
| hddc-teal | #2494A5 | HDDC skyline blocks | Large italic accents, borders, icons, focus |
| hddc-teal-deep | #1B6E7B | Derived, darker teal | Small teal text, the Recommended ribbon |
| hddc-lime | #AED153 | HDDC house line | Decoration only, never text |

The three logo colors were measured from the HDDC logo in Cheneé's email signature. HDDC has
not published official hex codes or fonts. Ask for the brand guide at kickoff and swap the
exact values in if they differ. Everything else in the table is derived, not HDDC's.

## Facts used in the copy, and how sure we are

| Fact | Status |
|---|---|
| Founded 1980 by Coretta Scott King, Christine King Farris, and John Cox | Confirmed by HDDC's About page and press |
| Principles: Historic Preservation, Non Displacement, Sustainability | Confirmed, HDDC supplied listings |
| Block by block strategy pioneered in the late 1990s | HDDC's About page |
| "Evolution into a capital investment corporation" | One HDDC page, the careers page, early 2026. Confirm with Cheneé before the proposal leans on it. If she does not use the phrase, rewrite assumption 03. |
| Front Porch opened April 2025, first new development on its stretch of Auburn in nearly two decades | Urbanize, SaportaReport, Bisnow. Print as "nearly two decades", not "since 2007". |
| Henderson Place: HDDC's site since 1995, Mercy Housing Southeast developing | HDDC, Mercy Housing |
| Flats at The Indie and Auburn Glenn developed with partners | HDDC projects page |
| Dynamic Metal Lofts, first cleanup under Georgia's brownfield law | HDDC projects page. Verify the wording before sending. |
| Sweet Auburn Equitable Development and Preservation Strategy with Georgia Tech | ARC award, May 14, 2026 |
| Herndon Plaza, 142 to 148 Auburn Ave NE, listed by HDDC as a preservation project | HDDC projects page. Ownership, budget, and schedule not public. |
| Georgia historic credit 25%, $5M per project cap | Planning assumption. Sunset date and annual cap not confirmed. Verify with Georgia HPD. |

Left out on purpose: occupancy, debt service, the encampment, and the appraisal dollar figure.
Those are Cheneé's to raise. HDDC's board chair and its lender may read this page.

## Answers for Lovable's eight questions

1. Two states. Georgia is confirmed. Alabama is not part of HDDC's work, so it stays out of
   this proposal. The instrument carries an Alabama profile for other pursuits.
2. The three decisions. Front Porch Phase II. Herndon Plaza. The next block, tied to the
   Sweet Auburn Equitable Development and Preservation Strategy. Not Henderson Place: Mercy
   Housing leads it and it is in lease up.
3. Pillars. Affordable Housing, Black Owned Business, Arts and Culture, Urban Agriculture and
   Green Space. HDDC's three principles become the scoring check, not pillars.
4. Front Porch struggles. Do not name them. Frame the instrument around Phase II and the
   appraisal problem in general terms.
5. Readers. Cheneé first, then Nasim Fluker and Ron Kirkpatrick, Vice President of Real
   Estate. Nasim's title conflicts: the website says Vice President of Program Development,
   HDDC's own September emails say VP of Programs. Use the one in her email signature. Then the board and Reinvestment Fund. Write
   so a lender can read every line.
6. Roles. Yes. HDDC has been owner developer, land partner, and co developer. Keep the
   Advisor or Equity Partner toggle.
7. Pricing. Keep it hidden, $ to $$$, confirmed after scoping, plus the grant underwriting line.
8. Atlanta trips. One kickoff walk of Auburn Avenue in Tier 1. Quarterly in Tier 2. Monthly
   in Tier 3. Priced as a scoped component.

## What changed from the Kresge page

- Buyer: a foundation choosing grants becomes an owner and developer choosing deals, structures, and roles.
- Palette: Kresge navy, gold, and cream become HDDC navy #214083, teal #2494A5, and lime #AED153 on white.
- Problem: rewritten around the appraisal, phase by phase rework, and principles that never reach the model.
- Assumptions: rewritten around Front Porch, the role question, the capital investment corporation, and HDDC's principles.
- Case studies: reordered to put the legacy Black community case first, each tied to HDDC's own history.
- Live section: three deal types, a principles check, a Built for Georgia row, and a quick tour panel.
- Tiers: Phase II Clarity, Sweet Auburn Portfolio, Investment Case, with a grant underwriting line.
- Every reference to Detroit, McNichols, Live6, grantees, and the word tool is gone.
