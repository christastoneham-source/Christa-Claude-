# Deliverable 20 · Lovable build prompts · The Investment Map proposal for HDDC

Revised October 12, 2026. Replaces the earlier version of this file.

The Kresge page was written to a funder deciding where grants go. HDDC is an owner and
developer deciding where to build, how to acquire and finance a site, and what role to take.
Same layout, different buyer, different decisions. Every line of copy below is written for
HDDC. Nothing is carried over from Kresge except Christa's biography, stats, and case study
facts.

This revision rests on what Christa knows as of October 12. HDDC's three decisions are a
district in Alabama, a five acre site in Alabama, and a twenty acre site with several ways to
acquire it. Whether the Alabama district is a designated historic district is not known, so
the page calls it "a district" wherever it states HDDC's decision. No notes or transcript exist from the September 30 session, and no HDDC
email answers the five questions sent September 29. No line on the page quotes HDDC or
depends on what HDDC said.

Paste the three prompts into Lovable one at a time, in order. Wait for each build to finish
and check it before you send the next.

1. Prompt A builds the /hddc page: palette, layout, accessibility, and every line of copy.
2. Prompt B adds the quick tour panel and the live demonstration.
3. Prompt C sweeps out anything left from Kresge or the earlier HDDC draft, then runs the checks.

---

## Before you paste

- [ ] Send the recap to Cheneé, Nasim, and Nakia first. It names the three decisions and asks
      HDDC to correct them. If HDDC replies before this page goes out, update every line that
      names the three decisions or a state: the cover lede, the problem intro, working
      assumptions 01 and 03, the live section intro and its four cards, the Tier 1 outcomes,
      and the three clarifying questions. Then delete the CONFIRM notes those answers settle.
- [ ] Host the demonstration with the steps under Prompt B. Open all four tour links once.
      Do not use the claude.ai preview link. It is private and will not open for HDDC.
- [ ] Fill the four placeholders across the three prompts: [ACCESS WORD], [PROPOSAL DATE],
      and [PORTRAIT] in Prompt A, and [DEMO URL] in Prompt B (three times). Then search the
      prompts for "[". Only the two [CONFIRM: ...] notes in Prompt A and the quoted
      "[CONFIRM" in check 9 of Prompt C should remain.
- [ ] Work through the confirm list below. Any note you leave in place stays off the page.
      Lovable lists it at the end of its report.
- [ ] Give each print safe source in the fact table a fifteen minute look before sending.
- [ ] Keep internal facts out of every prompt and every reply to Lovable. Nothing about any
      HDDC project's leasing, loans, debt, appraisal amounts, security, or neighborhood
      conditions. Nothing from HDDC's tax filings. Nothing about personal relationships
      among HDDC leaders.
- [ ] Prompt A runs about 30,000 characters. If Lovable says it is too long, send it in two
      parts of about 14,000 and 16,000. The second part starts at the line "LIVE DEMONSTRATION".
      Start the second part with "Continue the /hddc build. Keep the palette, contrast,
      language, and CONFIRM rules from my last message."

### Confirm before sending

1. The three decisions, as HDDC states them. CONFIRM note on working assumption 01.
2. The state of the twenty acre site. The demonstration runs it on Atlanta, Georgia.
   CONFIRM note on the live section intro.
3. That HDDC is comfortable seeing "Alabama" on the page. No city or county is printed.
4. Nasim Fluker's title. The page does not print it, and does not print her name.
   HDDC's website says Vice President of Program Development. HDDC's own emails (Cheneé on
   September 2, Ann Johnson on September 21) say VP of Programs.
5. "Capital investment corporation." It is off the page. Use it only if Cheneé confirms
   the phrase. The fact table has an optional line for that case.
6. Whether the Alabama district is a designated historic district. The page says
   "a district" when it names HDDC's decision. The demonstration models a historic one.

---

## Prompt A · Build the /hddc page

```
Build the page at the route /hddc. If /hddc already exists from an earlier prompt, rebuild it to this spec. This spec replaces every earlier instruction for /hddc.

Use the Kresge proposal page only as a layout reference: same section order, same components, same password gate pattern, same print to PDF behavior, same spacing scale, same fonts. Do not reuse any Kresge copy, colors, or images except the four case study images and the portrait. Every line of /hddc copy comes from the strings in this prompt. Do not edit the Kresge page. If a component is shared with the Kresge page, make an /hddc copy of it instead of changing the shared one. Put every line of copy for /hddc in one constants file, src/content/hddc.ts, so copy edits never touch layout code. Use every string exactly as written inside the double quotes below, including capitals and punctuation.

CONFIRM NOTES
Two strings below are followed by a note in square brackets that starts with CONFIRM. The note is not part of the string. In src/content/hddc.ts, put the note on the line above that string as a comment in the form // CONFIRM: followed by the note text. Never render a CONFIRM note on the page, in alt text, in metadata, or in print.

PALETTE (HDDC brand, measured from HDDC's own logo file)
Create these tokens and use only these on /hddc:
  hddc-navy        #214083  HDDC wordmark blue. Display headings, section numbers, eyebrow labels, links, the details table header row, filled legend dots, the gate button, primary buttons, stat figures.
  hddc-teal        #2494A5  HDDC skyline teal. Italic accent lines inside headlines 32px and larger, card top borders, stat card borders, icons, focus rings, the left border of tinted boxes.
  hddc-teal-deep   #1B6E7B  Darker teal for anything small: the Recommended ribbon background with white text, small labels that would otherwise be teal, link hover, primary button hover.
  hddc-lime        #AED153  HDDC house line green. Decoration only: the right end of the horizontal rule, the top border of the recommended tier card, the lime half of the half dot in the legend, the 6px bar on top of each working assumption card. No other card gets a lime bar.
  hddc-ink         #1E2A3B  Body text.
  hddc-muted       #5A6578  Secondary text, captions, footnotes, form field borders.
  hddc-paper       #FFFFFF  Page background.
  hddc-mist        #F3F6FB  Background of every other full height section, and of tinted boxes.
  hddc-line        #DCE2EE  Hairline borders and table rules.
  hddc-teal-tint   rgba(36,148,165,0.08)  Fill of the What it demonstrates boxes and the How to read the numbers box.
  hddc-lime-tint   rgba(174,209,83,0.18)  Fill of the Tier 2 column in the details table.
Wherever this spec says white, use hddc-paper. Use no color outside these tokens.
The horizontal rule on the cover and on the close is 4px tall and runs hddc-navy to hddc-teal to hddc-lime, left to right, never reversed.
Remove every Kresge color token from /hddc. No gold, no Kresge navy, no cream page background.
Typography stays as on the Kresge page: Fraunces for display headings, Inter for body, small uppercase eyebrow labels with letter spacing in hddc-navy.

CONTRAST (WCAG 2.1 AA; ratios measured on hddc-paper)
  hddc-ink 14.5:1, hddc-navy 9.9:1, hddc-muted 5.9:1 (5.4:1 on hddc-mist), hddc-teal-deep 5.9:1: allowed for text of any size.
  hddc-teal 3.6:1: allowed only for text 32px and larger, borders, icons, and focus rings.
  hddc-lime 1.7:1: never text, and never the only cue that tells two things apart.
  White text is allowed on hddc-navy (9.9:1) and hddc-teal-deep (5.9:1). Never put white text on hddc-teal or hddc-lime.

LANGUAGE RULES (apply to every string on /hddc)
Never use: software, platform, product, tool, AI, AI powered, app, patent pending. Say instrument, decision environment, analysis, demonstration.
Never use: just, really, very, literally, actually, certainly, basically, delve, embark, craft, unlock, leverage, game changer, revolutionize, exciting, groundbreaking, cutting edge, powerful, robust, seamless, synergy.
No em dashes, no en dashes, and no hyphenated words anywhere. Write "non displacement", "place based", "Black owned", "side by side", "five acre", "one page", "in person".
Short sentences. Active voice. No exclamation points.
The strings below already set where the full name "Historic District Development Corporation" appears. Do not add it anywhere else, and do not change "HDDC" in any string.
Write "Cheneé" with the accent every time.

GATE
Title: "The Investment Map"
Line: "Prepared for Historic District Development Corporation. Confidential."
Input label, visible: "Access word"
Access word: [ACCESS WORD]
Button: "Open"
Wrong word message: "That is not the access word. Check the note that came with this link."
The input uses type password and a 1.5px hddc-muted border. Enter submits. The wrong word message sits in an element with aria-live polite and is linked to the input with aria-describedby.

COVER
Eyebrow: "PREPARED FOR HISTORIC DISTRICT DEVELOPMENT CORPORATION · ATLANTA · [PROPOSAL DATE]"
Headline, the page's only h1, two lines, the second line in hddc-teal italic: "A clear picture of" / "HDDC's next three decisions."
Lede: "A district, a five acre site, and a twenty acre site. One decision environment shows what each one costs, what closes the gap, and what role HDDC takes."
Rule beneath.

SECTION 01 · WHO I AM
Eyebrow: "SECTION 01 · WHO I AM"
Headline: "I build the systems that move community capital."
Portrait at left: [PORTRAIT]. Alt text: "Portrait of Christa Stoneham, Founder of Connecting Dots and Strategies". Caption: "Christa Stoneham · Founder, Connecting Dots and Strategies"
Paragraph 1: "I am Christa Stoneham. Architect by training, with two decades of practice in community development across acquisition, disposition, capital stacking, and community engagement."
Paragraph 2: "I currently serve as President and CEO of the largest geographic land bank in the United States, stewarding a public portfolio of vacant and tax delinquent property, and the decisions that move that land from liability to community asset."
Paragraph 3: "Connecting Dots and Strategies is the advisory practice I founded to bring that same operator discipline to community development corporations, cities, CDFIs, and foundations weighing place based capital decisions."
Paragraph 4: "This instrument grew out of my own work in land banking, brownfield cleanup, housing, and redevelopment. I built this version for HDDC and the three decisions in front of it."
Three stat cards, hddc-navy figures, hddc-teal top border: "$150M+" / "Land assets stewarded" · "$100M" / "Property reactivated" · "100+" / "Affordable homes"

PROOF OF PRACTICE
Eyebrow: "PROOF OF PRACTICE"
Headline: "Four projects where land, capital, cleanup, and trust had to move together."
Note: "Each case is summarized here. I walk through the specifics in a direct conversation."
Four case study cards in this order, image left on cards 01 and 03 and image right on cards 02 and 04 at 1024px and wider. Each card uses the image that sat beside the same case title on the Kresge page. Each card has an eyebrow ("01 · CASE STUDY" through "04 · CASE STUDY"), the title, the summary, two labeled columns "CAPITAL MOVED" and "WHAT THE WORK REQUIRED", and a hddc-teal-tint box with a 4px hddc-teal left border labeled "WHAT IT DEMONSTRATES".
Alt text for the four case study images: open each image and write one sentence that says what is visible, such as the kind of land, building, or housing in view. Do not name a city, state, street, project, partner, or funder. Keep each under 125 characters. Do not start with "Image of" or "Photo of". If an image shows readable signs, logos, or text that name a place or an organization, leave that card without an image and report it at the end.

01 "Contaminated Land to Neighborhood Future"
Summary: "Helped lead the reuse pathway for historically burdened property in a legacy Black community."
Capital moved: "$5.5 million in federal Brownfields funding secured for assessment and cleanup, including major cleanup funding for a long standing contaminated site."
What the work required: "Environmental strategy, federal funding, regulatory coordination, public accountability, resident trust, and a credible long term vision for land that had carried decades of harm."
What it demonstrates: "A site's past shapes what it can become. So does the trust of its neighbors. In a historic district, both weigh more. This work held technical rigor and community accountability in one plan."

02 "Resilient Housing on Overlooked Land"
Summary: "Small and difficult parcels translated into a housing pipeline for affordable, resilient, and accessible homes."
Capital moved: "More than $700K in design, planning, technical assistance, and partner support aligned around replicable home plans and resilient housing implementation."
What the work required: "Design standards, builder readiness, community input, resilience criteria, partner coordination, and a scalable approach for turning scattered parcels into housing production."
What it demonstrates: "Scattered lots become a pipeline when every parcel is read the same way. HDDC pioneered its block by block strategy in the late 1990s. This is that discipline with a production system behind it."

03 "Public Land to Community Asset"
Summary: "Led decisions across a large public portfolio of vacant, tax delinquent, and underused property in a major American city."
Capital moved: "More than $100 million in property value put back in play through public land stewardship, disposition, and redevelopment activity."
What the work required: "Parcel strategy, partner selection, legal authority, affordability terms, development readiness, public accountability, and a repeatable way to decide which properties should move, when, to whom, and for what outcome."
What it demonstrates: "Land decisions move faster and hold up better when each one follows the same method, with the reasons on record for a board and a lender."

04 "Brownfield to Housing Opportunity"
Summary: "Helped move a former transportation and industrial site from environmental uncertainty toward a new affordable housing future."
Capital moved: "More than $12 million in publicly documented acquisition and predevelopment capital helped assemble the site and position it for roughly 120 multifamily units and 40 single family homes."
What the work required: "Brownfield assessment, demolition sequencing, public agency coordination, financing alignment, community storytelling, and a reuse strategy that could carry both neighborhood memory and future housing need."
What it demonstrates: "On a former industrial site, the cleanup bill, the capital gap, and the neighbors' hopes arrive at once. The way through is a sequence: assess, clean, finance, build. HDDC knows this path. Its Dynamic Metal Lofts was the first cleanup under Georgia's brownfields law."

SECTION 02 · THE PROBLEM
Eyebrow: "SECTION 02 · THE PROBLEM"
Headline: "Good deals stall when the numbers miss the neighborhood."
Intro: "HDDC is weighing a district, a five acre site, and a twenty acre acquisition. Two of them sit in Alabama, under rules that differ from Georgia's. Three patterns slow decisions like these."
Three cards, each with a small line icon in hddc-teal (aria-hidden):
Card 1 title: "The appraisal misreads the place." Body: "Comparable sales carry decades of disinvestment. They miss what a place is worth once people live and work there again. When value comes in low, the capital stack breaks and the team rebuilds the case under deadline."
Card 2 title: "One structure gets priced. The rest get guessed." Body: "Buying outright, an option, a ground lease, a fee developer role, and a joint venture each change capital on day one, control, risk, and income. When only one structure is modeled, the cost of the others shows up after the commitment."
Card 3 title: "The principles are hard to show in numbers." Body: "Lenders read the pro forma. Funders ask for impact. Residents ask who gets to stay. Historic preservation, non displacement, and sustainability guide HDDC's work. They seldom appear in the model a deal is judged by."
Closing line, Fraunces, hddc-navy: "Each of these can be solved before the money moves."

WORKING ASSUMPTIONS
Eyebrow: "WORKING ASSUMPTIONS"
Headline: "Four working assumptions, offered for your correction."
Four numbered cards, each with a 6px hddc-lime bar on top:
01 Title: "Three decisions are on the table." Body: "A district and a five acre site, both in Alabama, and a twenty acre site with more than one way to acquire it. Each asks a different question. Each needs its own answer before capital moves." [CONFIRM: these are the three decisions as HDDC describes them in its reply to the recap, including whether the Alabama district is a designated historic district]
02 Title: "The role question is real." Body: "HDDC served as developer and owner at Front Porch on Auburn, as landowner at Henderson Place with Mercy Housing Southeast as developer, and as a development partner at Flats at The Indie and Auburn Glenn. Each new deal asks which role fits and what exposure comes with it."
03 Title: "Acquisition is its own decision." Body: "The twenty acre site could be bought at market, bought at a distressed or bank owned price, seller financed, optioned, ground leased, contributed to a joint venture, or conveyed by a land bank or public owner. Each path sets the land cost, the cash needed on day one, the carry, and who holds control."
04 Title: "The principles should score the deal." Body: "Coretta Scott King, Christine King Farris, and John Cox founded HDDC in 1980. Its three principles belong inside the numbers, read scenario by scenario: historic preservation, non displacement, and sustainability."
Italic line under the cards: "Correct anything here. The scope follows what you tell me."

LIVE DEMONSTRATION
Eyebrow: "LIVE DEMONSTRATION"
Headline: "Three decisions in one decision environment."
Italic subline: "A district, a five acre site, and twenty acres."
Intro: "This demonstration models the three decision types in front of HDDC. It runs on stylized parcels and holds nothing confidential. In the engagement, it runs on HDDC's actual sites. The District and The Five Acre Site run on a market profile for a small Alabama city. The Twenty Acres runs on an Atlanta, Georgia profile and compares seven ways to acquire the land. Every number moves when an assumption moves. The capital stack keeps the gap in view. A principles check reads each scenario for historic preservation, non displacement, and sustainability." [CONFIRM: the state of the twenty acre site; the demonstration uses Atlanta, Georgia until HDDC says otherwise]
Eyebrow: "FOUR THINGS TO TRY". Four cards:
"Read the district": "About 40 stylized parcels in a historic district. Four development pillars, each one editable. Historic preservation priced as its own construction mode, with federal and state historic credit lines in the capital stack."
"Test the scenarios": "Assign pillars, change any assumption, save a scenario, and compare saved scenarios side by side."
"Compare structures and paths": "Eight deal structures for The Five Acre Site, side by side in one table. Seven acquisition paths and three subdivision concepts for The Twenty Acres, with the concepts compared under the path you choose."
"Choose the role": "Advisor or Equity Partner. The toggle shows what closes the gap and the exposure that comes with it. The principles check shows what each choice means for residents, historic buildings, and the environment."
Below the four cards, leave an empty full width div with the id demo-slot. My next prompt fills it.
Eyebrow: "BUILT FOR GEORGIA AND ALABAMA". One row of four chips with 1px hddc-teal borders and hddc-ink text, wrapping to two rows on tablets and one column on phones: "Federal and state historic tax credits" · "Georgia EPD and ADEM brownfield programs" · "Public partner resources for each state" · "Property tax for each market profile"
Footnote under the chips, hddc-muted: "Rates, caps, and tax figures in the demonstration are planning assumptions. The engagement confirms each one with the Georgia Historic Preservation Division, the Alabama Historical Commission, each state's environmental agency, and HDDC's tax advisor."
Box with hddc-teal-tint fill and a 4px hddc-teal left border. Eyebrow: "HOW TO READ THE NUMBERS". Headline: "Use it to narrow the options." Body: "Every projection here is a planning estimate, and every assumption can be edited. The demonstration shows which options deserve full underwriting and which can be set aside. It compares scenarios on cost, the gap, and outcomes. It does not price any one of them to the dollar. None of its figures is an appraisal or a tax determination. In the engagement, HDDC's own costs, rents, and standards replace the planning assumptions."

THE IMPACT
Eyebrow: "THE IMPACT"
Headline: "Four results HDDC can put in front of its board and its lenders."
Intro: "Each one is something your team can hand to a board member, a lender, or a partner."
Four numbered cards:
01 "Options compared in days": "Structures, acquisition paths, and scenarios for each decision, side by side, with every assumption stated."
02 "Value evidence before the appraisal": "A documented value story built from stated assumptions and directional estimates, ready before the appraiser visits the site. It informs the appraisal conversation. It never replaces an appraisal."
03 "Principles you can show": "Historic preservation, non displacement, and sustainability read for every scenario, in language a lender and a legacy resident both understand."
04 "Everyone on the same page": "Staff, the board, lenders, and residents read from one set of assumptions. When a number changes, each of them can see why."

WHAT YOU ARE BUYING
Eyebrow: "WHAT YOU ARE BUYING"
Headline: "Two parts, offered alone or together."
Three cards:
01 "The Instrument": "Your own hosted copy of the decision environment, set up for HDDC's sites. Your staff runs it day to day. The instance and every output stay with HDDC through the engagement and each renewal."
02 "The Practice": "Counsel from a practitioner who leads a public land portfolio today. I set the instrument's assumptions to each real deal and test every answer before HDDC commits."
03 "The Combination": "Tiers 2 and 3 bring the two together. The instrument lets your team move faster. The practice gives each recommendation reasons a board and a lender can test."

ENGAGEMENT MODELS
Eyebrow: "ENGAGEMENT MODELS"
Headline: "Start with one decision, or take on all three."
Intro: "Tier 1 answers one decision. Tier 2 carries all three. Tier 3 takes the first priority to a case a lender can underwrite."
Three tier cards. Each card shows, in order: the eyebrow ("TIER 1", "TIER 2", "TIER 3"), the tier name, the label "TIME" and its value, the label "INVESTMENT" with the dollar signs and the line "Set during scoping.", then the label "OUTCOMES" and a bulleted list. The middle card carries a ribbon reading "RECOMMENDED" (hddc-teal-deep background, white text) and a 4px hddc-lime top border.
Tier 1 name: "First Decision". Time: "6 to 8 weeks". Investment: "$". Outcomes:
  "One decision HDDC chooses, run live on its actual site: the Alabama district, the Alabama five acre site, or the twenty acre site"
  "The market profile set to that site's state"
  "Deal structures or acquisition paths, the capital stack, and the gap, with the Advisor or Equity Partner read"
  "The principles check on every scenario"
  "A hosted link for your staff, with Partner Brief exports"
  "An onboarding session and a written user guide"
Tier 2 name: "Decision Portfolio". Time: "6 months and up". Investment: "$$". Outcomes:
  "Everything in Tier 1, for all three decisions"
  "Assumptions set to HDDC's own costs, rents, and standards"
  "Working sessions with your team on a set schedule"
  "A ranked view of the three decisions, scored on HDDC's principles"
  "A site control and ownership review for each site, including the acquisition path for the twenty acres"
  "Historic credit, brownfield, and public resource screening for each site, with funding tracked against the gap"
  "A written record of each decision and its reasons, for your board and lenders"
Tier 3 name: "Lender Ready Case". Time: "9 to 12 months". Investment: "$$$". Outcomes:
  "Everything in Tier 2, with the priority site carried to full feasibility"
  "Full pro formas, sources and uses, and capital stack options for the priority site"
  "An appraisal support package: the value story, comparable logic, and assumptions, ready for the appraiser"
  "An investment packet and recommendation written for your lenders and your board"
  "Application support for state and local resources in each site's state"
  "A phased implementation plan with partners, funding order, and milestones"
  "Site visits and in person working sessions, scoped and priced separately"
Eyebrow: "WHAT THE PRICE COVERS". Four small cards: 01 "Instrument license" / "for HDDC's instance" · 02 "Advisory retainer" / "monthly, in Tiers 2 and 3" · 03 "Feasibility work" / "priced by module" · 04 "License and support" / "each year after the engagement".
Footnote 1: "Price follows scope. We set it together after we agree on which decisions are in scope, who will use the instrument, for how long, and with what support."
Footnote 2: "Any tier can be underwritten in whole or in part by a capacity building or technical assistance grant. I will help HDDC package that request."

THE DETAILS
Eyebrow: "THE DETAILS"
Headline: "The full list, tier by tier."
Legend, four items, each a shape plus its label: filled hddc-navy dot "In the demonstration today" · half dot, left half hddc-navy and right half hddc-lime, with a 1.5px hddc-navy outline "Partly included in this tier" · empty dot with a 1.5px hddc-navy outline "Built in the engagement" · short hddc-muted dash "Not in this tier".
Table. Header row hddc-navy with white text: "Deliverable", "Tier 1 · First Decision", "Tier 2 · Decision Portfolio ★", "Tier 3 · Lender Ready Case". The star carries visually hidden text "Recommended". Fill the Tier 2 column with hddc-lime-tint. Category rows in small capitals, hddc-navy. Every mark carries visually hidden text equal to its legend label. In each row below, the three marks are Tier 1, Tier 2, Tier 3.
"DECISION ENVIRONMENT"
  "District grid with parcel reference data" · filled, filled, filled
  "Scenario builder across four development pillars" · filled, filled, filled
  "Construction modes with federal and state historic credit lines" · filled, filled, filled
  "Georgia and Alabama market profiles" · filled, filled, filled
  "Capital stack with the gap and the Advisor or Equity Partner read" · filled, filled, filled
  "Principles check: historic preservation, non displacement, sustainability" · filled, filled, filled
  "Eight deal structures compared for The Five Acre Site" · filled, filled, filled
  "Seven acquisition paths and three subdivision concepts for The Twenty Acres" · filled, filled, filled
  "Scenario comparison and a one page Partner Brief" · filled, filled, filled
  "Quick tour and in page guide" · filled, filled, filled
  "Hosted demonstration link your team can open anywhere" · filled, filled, filled
  "Access control on the hosted link" · empty, empty, empty
  "Team workspace with named users and roles" · dash, empty, empty
"DATA AND CALIBRATION"
  "Editable directional planning assumptions" · filled, filled, filled
  "HDDC's actual sites loaded" · empty, empty, empty
  "Assumptions set to HDDC's cost, rent, and outcome data" · dash, empty, empty
  "Georgia and Alabama program assumptions confirmed with each state" · dash, empty, empty
  "Connections to HDDC's own data sources" · dash, half, empty
"STRATEGY AND ADVISORY"
  "Onboarding session and written user guide" · empty, empty, empty
  "Site control and ownership review" · dash, empty, empty
  "Working sessions and office hours on a set schedule" · dash, empty, empty
  "Ranked view of the three decisions" · dash, empty, empty
  "Weighted criteria from HDDC's principles, with a decision log" · dash, empty, empty
"FINANCIAL ANALYSIS"
  "Financial view for each site" · dash, empty, empty
  "Funding pipeline tracked against the gap" · dash, empty, empty
  "Full pro formas with capital stack options" · dash, dash, empty
  "Sources and uses for the priority site" · dash, dash, empty
  "Appraisal support package" · dash, dash, empty
"ENVIRONMENTAL"
  "Brownfield screening against Georgia EPD and ADEM records" · dash, empty, empty
  "Phase I and Phase II environmental status, by site" · dash, empty, empty
  "Cleanup cost and timing carried into the finance" · dash, dash, empty
"BOARD AND LENDER MATERIALS"
  "Partner Brief exports" · filled, filled, filled
  "Written decision record" · dash, empty, empty
  "Investment packet for lenders" · dash, dash, empty
  "Recommendation and presentation for the board" · dash, dash, empty
"IMPLEMENTATION"
  "Phased plan with partners, funding order, and milestones" · dash, dash, empty
  "Site visits and in person working sessions" · half, half, empty
  "Alignment narrative for the board, lenders, and partners" · dash, dash, empty
Footnote under the table, hddc-muted: "Tier 1 covers the one decision HDDC chooses. Tiers 2 and 3 cover all three. Site visits: one kickoff visit in Tier 1, quarterly visits in Tier 2, monthly visits in Tier 3, each priced as a scoped component."

CLARIFYING QUESTIONS
Eyebrow: "CLARIFYING QUESTIONS"
Headline: "The scope turns on three answers."
Three numbered cards with a 4px hddc-teal left border:
01 "Where are the sites?": "Which Alabama city holds the district? Where is the five acre site? Where is the twenty acre site?"
02 "Who controls each site today?": "Does HDDC own it, hold an option on it, or still need to acquire it? Who owns the twenty acres now?"
03 "Which decision comes first?": "Who makes the call, by when, and what would they need to see to say yes? Who on your team would use the instrument each week?"
Eyebrow: "HOW FEATURES ARE SCOPED". Headline: "Every feature is core, configurable, or built to order."
Three cards, each with a label line and a list:
"CORE · Included in every tier": "District grid" · "Scenario builder" · "Eight deal structures" · "Seven acquisition paths" · "Subdivision concepts" · "Capital stack and the gap" · "Principles check" · "Partner Brief" · "Hosted access"
"CONFIGURABLE · Set with HDDC during scoping": "Pillars and outcome measures" · "Georgia and Alabama market profiles" · "Branding" · "Access levels"
"BUILT TO ORDER · Added in Tiers 2 and 3": "Financial modules" · "Appraisal support package" · "Environmental screening" · "Connections to HDDC's data" · "Team workspace with named users and roles" · "Additional sites"

CLOSE
Rule above. Headline, two lines, the second in hddc-teal italic: "The next step is to choose" / "the first decision together."
Body: "Thank you, Cheneé, and the HDDC team for your time and the conversations so far. HDDC has carried this work since 1980. It would be a privilege to help with the three decisions in front of you."
Contact block in Fraunces: "Christa Stoneham, Founder, Connecting Dots and Strategies LLC" / "info@christastoneham.com" as a mailto link / "www.christastoneham.com" as a link to https://www.christastoneham.com
Last line, small, hddc-muted: "Reclaiming the map."

LAYOUT AND MOBILE
Breakpoints: phone below 640px, tablet 640px to 1023px, desktop 1024px and wider.
Full height sections alternate hddc-paper and hddc-mist, starting with hddc-paper on the cover.
Phone: one column, 16px side gutters, no horizontal page scroll at 360px and 390px. Scale display headings with clamp() so the cover headline is never more than four lines at 360px. The two hddc-teal italic headline lines, on the cover and on the close, never render below 32px: set their clamp() minimum to 32px. Body text at least 16px, captions and footnotes at least 14px.
Case study cards: image above the text on phones and tablets, alternating sides on desktop.
Stat cards: one column on phones, three across from tablet up.
Problem, assumption, four things to try, impact, buying, price, question, and feature scope cards: one column on phones, two across on tablets, the full row on desktop. Tier cards: one column on phones and tablets, three across on desktop. The RECOMMENDED ribbon stays visible at every width.
Details table: wrap it in a container with overflow-x auto, role region, aria-label "Deliverables by tier", and tabindex 0, so it scrolls sideways inside its own box. Give the table a minimum width of 720px. Keep the Deliverable column sticky on the left on phones and tablets.
Every button and link target is at least 44px tall on touch screens.

ACCESSIBILITY
html lang "en". One h1, the cover headline. Each section headline is an h2. Each card title is an h3. Eyebrows are paragraphs, not headings.
Every interactive element shows a visible focus ring: 2px solid hddc-teal with a 2px offset. Never remove focus outlines.
Decorative icons, the horizontal rules, and the lime bars carry aria-hidden true. The portrait and the four case study images carry the alt text set above.
Respect prefers-reduced-motion: no smooth scrolling and no transitions when it is set.

PRINT
Print to PDF starts each full height section on a new page. Hide the gate and any navigation. Keep the hddc-navy table header, the tinted boxes, and the hddc-lime-tint column in print with print-color-adjust exact. Do not split a card or a table row across pages. Letter size, portrait, 0.5 inch margins.

METADATA
Page title: "The Investment Map · Prepared for HDDC". Meta description and og:description: "Three decisions in one decision environment, prepared for Historic District Development Corporation." og:title equals the page title. No og:image. Add a robots meta tag with "noindex, nofollow".
```

---

## Prompt B · Host the demonstration and add the quick tour

Before you send this prompt, host the demonstration and get its link. Use one of these.

1. Recommended, Netlify Drop. Make a new folder on your computer named `investment-map-demo`.
   Copy `investment-map/index.html` from this repo into it, and nothing else. Leave the
   screenshots and the README behind. Log in at app.netlify.com first; a free account works,
   and a site dropped without an account can expire. Open app.netlify.com/drop, drag the
   folder onto the page, and copy the site link it gives you, for example
   `https://example-name.netlify.app/`. That link is [DEMO URL]. Anyone with the link can
   open it. It holds only stylized data, but it carries HDDC's name and colors, so share it
   only through the proposal.
2. Or inside Lovable. Attach `investment-map/index.html` to the Lovable chat with this
   prompt and tell Lovable to save it unchanged at `public/demo/investment-map.html`. Then
   [DEMO URL] is `/demo/investment-map.html`. That path sits outside the password gate.
   Check that Lovable did not rewrite the file: it should open on its own at that path and
   match the screenshots in `investment-map/screenshots/`.

The demonstration already answers these links. The tour counts come from its source.

| Link | What it opens |
|---|---|
| [DEMO URL]#tour | The full guided tour, 18 steps, about two minutes |
| [DEMO URL]#tour-district | The District, small city, Alabama profile, with its own 8 step tour |
| [DEMO URL]#tour-site | The Five Acre Site, small city, Alabama profile, eight deal structures, with its own 6 step tour |
| [DEMO URL]#tour-twenty | The Twenty Acres, Atlanta, Georgia profile, seven acquisition paths, with its own 6 step tour |
| [DEMO URL]#district, #site, #twenty | Opens that workspace. On a first visit it also starts that workspace's tour. |

Why the frame waits for a press: the demonstration starts a tour on its first load and
scrolls to each step. Loaded on page open, it could pull a reader down the page. Prompt B
loads it only when someone asks for it.

```
On the /hddc page, fill the empty div with the id demo-slot with a quick tour panel and the live demonstration. Use only the hddc tokens. Put every string below in src/content/hddc.ts, and add a constant DEMO_BASE with the value "[DEMO URL]". Build every demonstration address as DEMO_BASE, then the # character, then a hash name, for example [DEMO URL]#tour-district. If DEMO_BASE ends with a slash, keep the slash and put # directly after it.

LAYOUT
At 1024px wide and up: two columns inside demo-slot with a 32px gap. The left column is 320px wide and holds the quick tour panel. The right column takes the remaining width and holds the frame area. Below 1024px: one column, the panel first, then the frame area, both full width.

QUICK TOUR PANEL
Eyebrow: "QUICK TOUR"
Headline, an h3 in Fraunces, hddc-navy: "See it in two minutes."
Three numbered steps. Each number sits in a 28px hddc-navy circle with white text. The first sentence of each step is bold, the second is regular, both hddc-ink:
1 "Pick a tour." "Each one opens a live decision type."
2 "Change one assumption." "Watch the capital stack and the gap move."
3 "Save a scenario." "Then print the one page Partner Brief."
Four buttons, stacked, full width, at least 44px tall, 16px text, label aligned left. Each is a button element with type button, aria-controls "demo-frame", and aria-pressed false on load. The first is primary: hddc-navy background, white text, hover hddc-teal-deep background. The other three have a white background, a 1.5px hddc-navy border, hddc-navy text, and an hddc-mist hover background.
  Label "Start the full tour", hash tour
  Label "Tour The District", hash tour-district
  Label "Tour The Five Acre Site", hash tour-site
  Label "Tour The Twenty Acres", hash tour-twenty
Note under the buttons, 14px, hddc-muted: "Demonstration data. Stylized parcels, no real addresses. Your sites load in the engagement."
Under the note, a visually hidden element with aria-live polite. It starts empty.

FRAME AREA
Eyebrow above the frame area, always visible: "THE INVESTMENT MAP · LIVE DEMONSTRATION FOR HDDC"
On page load, do not create the iframe and do not request DEMO_BASE. Show a poster card in its place, the same width as the frame and 760px tall at 1024px and up, 640px tall below: hddc-mist background, 1px hddc-line border, 12px radius, content centered. The poster holds one line in Fraunces, hddc-navy: "The live demonstration opens here." Under it, a primary button: "Load the demonstration". That button behaves exactly like "Start the full tour", with hash tour.
The iframe, once created, replaces the poster: id "demo-frame", title "The Investment Map, live demonstration", width 100%, height 760px at 1024px and up and 640px below, 1px hddc-line border, 12px radius, allow "fullscreen". Do not add a sandbox attribute. The Partner Brief inside the demonstration uses the browser print dialog.
Under the frame area, right aligned and always visible: a link "Open in a new tab" to DEMO_BASE#tour, target _blank, rel noopener, with visually hidden text " (opens in a new tab)".

ON EVERY BUTTON PRESS
1. Take the hash from the pressed button.
2. If the iframe does not exist yet, create it in place of the poster with src set to DEMO_BASE#hash.
3. If the iframe exists and this hash equals the last hash you set, set src to DEMO_BASE#ready, wait 60 milliseconds, then set src to DEMO_BASE#hash. The demonstration starts a tour when its hash changes, so the same hash twice in a row would do nothing. The hash ready is not a route, so it changes nothing on screen.
4. Otherwise, set src to DEMO_BASE#hash. A change of hash alone does not reload the demonstration.
5. Never reload the page and never open a new window.
6. Store the hash as the last hash. On the pressed panel button, set aria-pressed true and add a 4px hddc-teal left border. On the other three panel buttons, set aria-pressed false and remove the border. The poster button counts as "Start the full tour".
7. Set the live element's text to the matching line: "Loading the full tour." for tour, "Loading the tour of The District." for tour-district, "Loading the tour of The Five Acre Site." for tour-site, "Loading the tour of The Twenty Acres." for tour-twenty.
8. If any part of the frame sits outside the viewport, scroll the page so the frame's top sits 16px below the top of the viewport. Scroll smoothly, or jump when prefers-reduced-motion is set.
9. Leave keyboard focus on the pressed button. If the pressed button was the poster button, move focus to the "Start the full tour" panel button.

PRINT
Hide the four panel buttons, the live element, the poster, the iframe, and the new tab link. In the frame area, show a static card instead: hddc-mist background, 4px hddc-teal left border, 16px padding, hddc-ink text: "Live demonstration: ADDRESS. Open the link for the guided tour." Replace ADDRESS with DEMO_BASE#tour written out in full. If DEMO_BASE starts with a slash, print the page origin followed by DEMO_BASE#tour. Do not split this card across pages.
```

---

## Prompt C · Sweep out Kresge and the earlier draft, then run the checks

```
Run these checks on /hddc only and fix every hit. Do not change the Kresge page. If a file is shared with the Kresge page, do not edit it; make an /hddc copy and point /hddc at the copy. Do not open or edit public/demo/investment-map.html if it exists. It is the hosted demonstration and must stay unchanged.

1. Search every file used by /hddc, including src/content/hddc.ts, components, metadata, alt text, aria labels, the page title, the og tags, and the print styles. The search is case insensitive. Remove or rewrite every hit.
   Kresge terms: Kresge, Foundation (when it means Kresge), Detroit, Michigan, McNichols, Live6, Livernois, ninety three, 93 parcels, corridor, Corridor Clarity, Strategy Partnership, grantees, funder ready, assessor data, July 2026.
   Earlier HDDC draft terms: Sweet Auburn, Sweet Auburn Portfolio, Phase II Clarity, Front Porch Phase II, Investment Case, Herndon Plaza, the next block, Georgia Tech, capital investment corporation, Program Development, VP of Programs, Fulton County, What I'm hearing.
   The word "live" is allowed. Keep "LIVE DEMONSTRATION", "run live", aria-live, and every other use.
   Phrases that must not survive in any form: "The portfolio, live", "fund, defend, and build", "with the receipts", "from vision to decision", "Let me show you", "I am bringing four working assumptions", "Your corrections set the scope", "The work is strategic", "four moves", "a menu, not a mystery", "Three ways to work together", "An instrument, a practice, or both", "Every deliverable, side by side", "The right scope depends on", "directional, by design", "Confirmed after scoping", "Decision ready pictures in days", "One shared picture", "Let's scope what this looks like".
2. Front Porch appears once, in working assumption 02. The page says nothing about any HDDC project's leasing, loans, debt, appraisal amounts, security, or neighborhood conditions, and nothing from HDDC's financial statements.
3. Confirm no Kresge color token or hex value is used anywhere on /hddc. Every color must be one of the hddc tokens.
4. Confirm there are zero em dashes (U+2014) and zero en dashes (U+2013) in any /hddc file. Confirm no visible string contains a letter, a hyphen, and a letter in a row. Ignore URLs, email addresses, file paths, CSS, and code identifiers.
5. Confirm none of these appear in visible text, alt text, or metadata, matching whole words only: software, platform, platforms, product, products, tool, tools, AI, AI powered, app, apps, patent pending, just, really, very, literally, actually, certainly, basically, delve, embark, craft, unlock, leverage, game changer, revolutionize, exciting, groundbreaking, cutting edge, powerful, robust, seamless, synergy. Words such as every, production, approach, and application are fine. Confirm there are no exclamation points.
6. Confirm "Cheneé" keeps its accent everywhere.
7. Confirm no text under 32px uses hddc-teal or hddc-lime as its color. Small teal text uses hddc-teal-deep. Confirm no white text sits on hddc-teal or hddc-lime.
8. Confirm the page title is "The Investment Map · Prepared for HDDC", the meta description and og:description are "Three decisions in one decision environment, prepared for Historic District Development Corporation.", there is no og:image, and the robots meta tag reads "noindex, nofollow".
9. Find every // CONFIRM comment in src/content/hddc.ts. Confirm that no text containing "CONFIRM" or "[CONFIRM" renders on the page, in alt text, in metadata, or in print.
10. Check the page at 360px and 390px wide: no horizontal page scroll, the details table scrolls inside its own container with the Deliverable column sticky, the quick tour panel stacks above the frame area, and every button is at least 44px tall.
11. Accessibility: one h1; section headlines are h2 and card titles are h3; the portrait and the four case study images have alt text and none names a city, state, street, project, partner, or funder; tab through the whole page and confirm every interactive element, including the details table container, receives a visible hddc-teal focus ring; the gate error message is announced; the legend shapes and table marks have text equivalents.
12. Before any button press, confirm the page sends no request to the demonstration address. Press each quick tour button, then press the same button twice, and confirm the matching tour starts each time.
13. Print to PDF and confirm each section starts on a new page, the demonstration area prints as the static card with the full address, and no buttons print.
When you are done, report in three parts: 1) what you changed; 2) "Items to confirm before sending", listing each // CONFIRM comment with the string it sits above; 3) any case study image you could not describe without naming a place or an organization.
```

---

## Placeholders

| Placeholder | What goes there |
|---|---|
| [ACCESS WORD] | One lowercase word. Send it in the note that carries the link, never on the same line as the link. |
| [DEMO URL] | The hosted demonstration from the Prompt B steps: the Netlify site link, or `/demo/investment-map.html` inside Lovable. Never the claude.ai preview link, which is private. |
| [PROPOSAL DATE] | Month and year in capitals, for example OCTOBER 2026. |
| [PORTRAIT] | The portrait from the Kresge page. If Lovable holds more than one portrait, name the file. |

The two [CONFIRM: ...] notes are not placeholders. Leave them in place until they are settled.

## HDDC palette, for reference

| Token | Hex | Where it comes from | Use | Contrast on white |
|---|---|---|---|---|
| hddc-navy | #214083 | HDDC wordmark | Headings, numbers, links, table header, primary buttons | 9.9:1, any text |
| hddc-teal | #2494A5 | HDDC skyline blocks | Large italic accents, borders, icons, focus rings | 3.6:1, text 32px and up only |
| hddc-teal-deep | #1B6E7B | Derived, darker teal | Small teal text, the Recommended ribbon, hovers | 5.9:1, any text |
| hddc-lime | #AED153 | HDDC house line | Decoration only | 1.7:1, never text |
| hddc-ink | #1E2A3B | Derived | Body text | 14.5:1 |
| hddc-muted | #5A6578 | Derived | Captions, footnotes, form borders | 5.9:1 (5.4:1 on hddc-mist) |

The three logo colors were measured from the HDDC logo in Cheneé's email signature. HDDC has
not published official hex codes or fonts. Ask for the brand guide at kickoff and swap the
exact values in if they differ. Every other token is derived and is not HDDC's.

## Facts used in the copy, and how sure we are

Labels follow the fact sheet, section 8. Print safe still means a quick look at the cited
page before sending.

| Fact or line | Where it appears | Status |
|---|---|---|
| Founded 1980 by Coretta Scott King, Christine King Farris, and John Cox | Working assumption 04; close ("since 1980") | Print safe (fact sheet 1.6). Spell it "Farris". |
| Principles: Historic Preservation, Non Displacement, Sustainability | Assumption 04, problem card 3, live section, impact, details | Print safe (1.12). HDDC writes "Non-Displacement". The page drops the hyphen under the house rule. |
| Block by block strategy, late 1990s | Case study 02 | Print safe (1.13). The earlier draft said "the 1990s". |
| HDDC as developer and owner of Front Porch on Auburn | Assumption 02 | Print safe (2.1). The opening date and "nearly two decades" are print safe too, but no longer on the page. |
| Henderson Place: HDDC as landowner, Mercy Housing Southeast as developer | Assumption 02 | Print safe (2.2: HDDC site since 1995). The earlier draft said HDDC "contributed its land to a partnership". The ownership split of the new building was not found, so the page says only "landowner". |
| Flats at The Indie and Auburn Glenn, HDDC as a development partner | Assumption 02 | Print safe (2.7, 2.9). |
| Dynamic Metal Lofts, the first cleanup under Georgia's brownfields law | Case study 04 | Print safe (2.10, 5.7). The earlier draft added "completed", which the sources do not say. |
| HDDC in Atlanta | Cover eyebrow | Print safe (1.3). |
| Cheneé Joseph | Close | Print safe (1.31). Her title is not on the page. |
| Nasim Fluker and Nakia Romans | Not on the page | The close thanks "Cheneé and the HDDC team". The sources do not show whether Nasim and Nakia joined on September 30. Nasim's title is Verify (1.33). |
| The Alabama district, the Alabama five acre site, the twenty acre site and its seven acquisition paths | Cover lede (no state), problem intro, assumptions 01 and 03, live section, tiers, questions | From Christa, October 12, 2026. Not in any written HDDC record. CONFIRM note on assumption 01. No city or county is printed. The page says "a district", not "a historic district", when it names HDDC's decision, because the district's historic status is not known. |
| The four pillars (Affordable Housing, Black Owned Business, Arts and Culture, Urban Agriculture and Green Space) | Live section card, details table | Demonstration defaults. HDDC's print safe program areas are Affordable Housing, Urban Agriculture, and Arts and Culture (1.16). The page calls them "development pillars", not "HDDC's pillars". |
| The Twenty Acres on the Atlanta, Georgia profile | Live section intro | Demonstration default only. CONFIRM note on the intro. |
| State programs: federal and state historic credits, Georgia EPD and ADEM brownfield programs | Built for Georgia and Alabama row, details table | Program names only. The rates and caps (federal 20%; Georgia 25% with a $5M project cap; Alabama 25% with a $5M project cap) are Verify (5.1, 5.3, 6.2, 6.3). They stay in the demonstration as planning assumptions and off the page. |
| "Capital investment corporation" | Off the page | Verify (1.22). If Cheneé confirms the phrase, add this sentence to the end of assumption 02: "HDDC describes its next chapter as an evolution into a capital investment corporation." Then delete "capital investment corporation" from the term list in Prompt C check 1, or Lovable will strip it. |
| Front Porch Phase II, Herndon Plaza, the next block, the ARC and Georgia Tech strategy | Off the page | Not the three decisions (Christa, October 12). |
| Christa's stats and case study figures | Section 01, proof of practice | Christa's own record, as on the Kresge page. |
| HDDC colors | Palette | Measured from HDDC's logo (4.3 to 4.5). Verify before print. |

Left out on purpose: anything about Front Porch leasing, lending, appraisal amounts, or
neighborhood conditions, anything from HDDC's tax filings, and anything personal about
HDDC's leaders. Those are HDDC's to raise. HDDC's board and its lender may read this page.

## Answers for Lovable's eight questions

1. **Which states?** Two. The District and The Five Acre Site run on the "Small city,
   Alabama" profile. Their cities are not confirmed, so never name a city or a county. The
   Twenty Acres runs on the "Atlanta, Georgia" profile until HDDC confirms where the site
   is. HDDC's office and track record are in Atlanta. Both state profiles are built into the
   demonstration, and their rates and caps are planning assumptions.
2. **Which three decisions?** The district in Alabama (its historic status is not yet
   confirmed). The five acre site in Alabama. The twenty acre site and how to acquire it: market purchase, distressed or bank
   owned price, seller financing, option to purchase, ground lease, land contribution in a
   joint venture, or public conveyance from a land bank or public owner. Front Porch Phase
   II, Herndon Plaza, and the next block on Auburn Avenue are not the three decisions. Do
   not name them on the page.
3. **Pillars?** Affordable Housing, Black Owned Business, Arts and Culture, Urban
   Agriculture and Green Space. HDDC's three principles, Historic Preservation, Non
   Displacement, and Sustainability, are the scoring check, not pillars.
4. **Front Porch?** Name it once, in working assumption 02, as a project where HDDC served
   as developer and owner. Say nothing about its leasing, financing, lenders, appraisal, or
   neighborhood conditions. Treat the appraisal problem in general terms only.
5. **Who reads it?** Cheneé Joseph first, then Nasim Fluker and Nakia Romans. If Nasim is
   ever named, use her name without a title until her own signature confirms it. HDDC's
   board and Reinvestment Fund, which made the introduction, may also read it. Write so a
   lender can read every line.
6. **Roles?** Yes. HDDC has served as developer and owner, as the landowner with a partner
   developer, and as a development partner. Keep the Advisor or Equity Partner toggle.
7. **Pricing?** Hidden. Show $, $$, and $$$ with "Set during scoping." Keep the grant
   underwriting line.
8. **Site visits?** One kickoff visit to the chosen site in Tier 1. Quarterly visits in
   Tier 2. Monthly visits in Tier 3. Each is priced as a scoped component. Visits go to the
   Alabama sites, the twenty acre site, and HDDC's office in Atlanta as the work requires.

## What changed from the Kresge page

- Buyer: a foundation choosing grants becomes an owner and developer choosing sites,
  structures, acquisition paths, and roles.
- Palette: Kresge navy, gold, and cream become HDDC navy #214083, teal #2494A5, and lime
  #AED153 on white.
- Decisions: one corridor becomes three decision types: a district and a five acre site in
  Alabama, and a twenty acre site with seven acquisition paths.
- Problem: rewritten around the appraisal, structures priced one at a time, and principles
  that never reach the model.
- Assumptions: four working assumptions offered for correction, built on the three
  decisions, HDDC's roles, acquisition, and HDDC's principles.
- Case studies: the legacy Black community case comes first, and each lesson is rewritten
  for HDDC. The facts are Christa's and unchanged.
- Live section: three workspaces, a principles check, a Built for Georgia and Alabama row,
  and a quick tour panel that loads the demonstration on request.
- Tiers: First Decision, Decision Portfolio, and Lender Ready Case, with a grant
  underwriting line.
- Every Kresge sentence outside Christa's biography, stats, and case study facts is
  rewritten. Every reference to Detroit, McNichols, Live6, grantees, and the word tool is
  gone.
