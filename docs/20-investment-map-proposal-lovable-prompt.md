# Deliverable 20 · Lovable build prompt · The Investment Map Portfolio Proposal

Paste the block below into Lovable. It mirrors the Kresge proposal site
(password gated, deck style sections, the demonstration embedded in its own
section, three ways to work together, plain language deliverables, investment
confirmed after scoping, access window with a date) and applies the Connecting
Dots and Strategies brand system.

Fill the bracketed placeholders before you paste. They are listed at the end.

---

```
Build a single page, password gated proposal site called "The Investment Map · Portfolio Proposal" for Connecting Dots and Strategies LLC (CDS), prepared for [CLIENT FORMAL NAME], referred to as HCDC throughout. It reads like a short deck: full height sections stacked vertically, arrow keys and a thin numbered index on the left move between them, and a "Print to PDF" action lays every section out as a clean letter page. React with Tailwind. No backend, no database, no analytics. Mobile friendly. Keep every line of copy in one constants file so it can be edited without touching components.

THE GATE
A centered card on cream: the four dot mark, the title "The Investment Map", a gold pill "Portfolio Proposal", the line "Prepared for [CLIENT FORMAL NAME]. Confidential.", one password field, and a button "Enter". The access word is "[ACCESS WORD]". Check it client side, remember it in sessionStorage, and show this error on a miss: "That is not the access word. Check the note that came with this link." Under the card: "Connecting Dots and Strategies · Reclaiming the map."

DESIGN SYSTEM (non negotiable)
Background cream #FCFAF1. Text ink #101C28. Accent colors in this fixed order: Brick #D95448, Gold #F1BA4B, Grove #47AB4F, Turquoise #00BCC5. Turquoise is the only action and link color (buttons, links, active index dot, focus rings). A four dot mark, one dot of each accent in order, sits beside the wordmark in the header and the footer. One thin spectrum rule runs Brick to Gold to Grove to Turquoise under the header, left to right, never reversed. Headings in Fraunces from Google Fonts with Georgia fallback. Body in Inter with system sans fallback. Cards are white with a hairline #E3DECD border and 12px radius. Small uppercase labels with letter spacing. Generous whitespace. No gradients other than the spectrum rule, no stock photography, no icons from icon libraries. Use the four accents only as meaning: Brick for The District, Gold for The Five Acre Site, Grove for The Twenty Acres, Turquoise for actions.

LANGUAGE RULES
Never use the words software, platform, product, AI, AI powered, or patent pending. Say instrument, decision environment, analysis, demonstration. No em dashes anywhere. Short sentences. Every projection carries the phrase "planning estimate, editable assumptions". Every figure of record carries a small "reference" badge.

HEADER (sticky, ink background, cream text)
Four dot mark, wordmark "The Investment Map" with the small line "Portfolio Proposal", and on the right a chip "Prepared for HCDC" and a button "Print to PDF".

SECTIONS, in this order. Each has a small numbered label (01 to 10) and a Fraunces heading.

01 COVER
Four dot mark, large title "The Investment Map", gold pill "Portfolio Proposal". Line: "Prepared for [CLIENT FORMAL NAME] · [MONTH YEAR]". Lede: "One decision engine. Three live deal types. One role question." Signature line: "Christa Stoneham, Founder · Connecting Dots and Strategies LLC". Buttons: "Start" (scrolls to 02) and "Open the demonstration" (opens [DEMO URL] in a new tab).

02 WHAT WE HEARD
Intro: "Three decisions are on the table. Each one needs the same thing: one shared picture, numbers that move when assumptions move, and a clear read on what role the gap implies."
Three cards with a colored top bar:
Brick, "The District". "A revitalization study in a small Southern city. About 40 parcels, four investment pillars, one capital stack." The question: "What does it take for the gap to close, and what role does that imply."
Gold, "The Five Acre Site". "One parcel with a small existing building. Eight deal structures, from buying outright to a public conveyance." The question: "Which structure fits on capital day one, control, risk, and income."
Grove, "The Twenty Acres". "One bank owned site in a large metro. Three subdivision concepts and three price bases." The question: "Should we buy it, what is highest and best use, and should it stay one parcel or subdivide."
Note under the cards: "Every parcel figure in the demonstration is stylized. The engagement runs on your parcels of record."

03 THE DEMONSTRATION
Heading "A working demonstration, not a slide about one." Embed [DEMO URL] in a 16 by 10 frame with a cream border, lazy loaded, with a button above it "Open in a new tab". Caption: "Working demonstration. Stylized data. Planning estimates with editable assumptions, never an appraisal or a tax determination." A short list beside the frame, one line each: "Assign pillars parcel by parcel and watch totals move." "Edit any source line and the gap recalculates in front of you." "Switch Advisor to Equity Partner and read what the role implies." "Compare eight deal structures in one table." "Switch three subdivision concepts and three price bases." "Save scenarios, compare them, print a one page Partner Brief."

04 ONE SHARED ENGINE
Heading "One engine under all three." Eight small cards in a grid, label plus one line: Construction modes (Rehab, Historic Preservation, New Construction, Demolition plus New). Historic credits (federal and state credit lines enter the stack). Sustainability (a cost premium, green outcomes, and unlockable funding lines). Market profiles (named assumption sets for cost, value, and tax). Capital stack and the gap (total cost minus committed sources, always in view). Scenarios (save, load, compare side by side). Partner Brief (one printed page per scenario). Edit Pillars (rename, recolor, reprice at any time). Footer line for the section: "The client team keeps the instrument. Partners receive the paper."

05 THE ROLE QUESTION
Heading "Advisor or Equity Partner." Two columns. Left, "Advisor": "HCDC advises the public partner and earns an advisory fee. Zero balance sheet exposure. Closing the gap means more public, grant, debt, or partner sources." Right, "Equity Partner": "HCDC places equity in the stack, carries that exposure, and holds a share of projected value created. Closing the gap means HCDC capital, and the instrument shows exactly how much." Closing line across both: "The toggle is the whole conversation. The instrument makes it a number instead of an argument."

06 THREE WAYS TO WORK TOGETHER
Intro: "Pick the shape that fits the decision in front of you. Each one builds on the last."
Three cards. Mark the middle one with a gold pill "Recommended".
A. "Site Instrument". For one deal type. You receive: the decision environment on your parcels of record for one site, two scenario sessions, one Partner Brief, training and handoff. Timeline: "6 to 8 weeks". Investment: "[OPTION A INVESTMENT or Confirmed after scoping]".
B. "Portfolio Decision Partnership". For all three deal types. You receive: the full decision environment on your parcels of record, shared pillars and market profiles, monthly decision sessions, a Partner Brief for every scenario the team wants to carry, training and handoff. Timeline: "4 to 6 months". Investment: "[OPTION B INVESTMENT or Confirmed after scoping]".
C. "Full Investment Case". Everything in B plus capital stack strategy, funding pipeline tracking, environmental screening, board and partner materials, and presentation support in the room. Timeline: "6 to 9 months". Investment: "[OPTION C INVESTMENT or Confirmed after scoping]".
Each card ends with a turquoise button "Choose this path" that scrolls to section 10.

07 DELIVERABLES IN PLAIN LANGUAGE
A table with columns Deliverable, What it is, A, B, C. Checkmarks in turquoise. Rows:
Web hosted decision environment. "Your parcels, your pillars, your assumptions, in one place the team can open from any browser." A B C.
Scenario comparisons. "Save any state under a name and put scenarios side by side." A B C.
Decision criteria. "The questions each workspace answers, written down and agreed before the numbers." A B C.
Financial views. "Capital stack, the gap, value created, and new annual property tax for every scenario." A B C.
Partner Brief. "One printed page per scenario for partners and boards." A B C.
Environmental screening. "A first read on brownfield and site condition risk before capital moves." C.
Funding pipeline tracking. "Sources, stages, and asks tracked against the gap." C.
Board and partner materials. "Decks, briefs, and the presentation itself." C.
Training and handoff. "The client team keeps the instrument and knows how to run it." A B C.
Under the table: "Planning estimates with editable assumptions throughout, never an appraisal or a tax determination."

08 HOW WE WORK
Five steps on a horizontal timeline with the spectrum rule behind them: "Discovery" (two weeks: parcels of record, pillars, decision criteria), "Build" (the decision environment on your data), "Scenario sessions" (the team works the instrument together), "Decision brief" (the recommendation and the Partner Briefs), "Handoff" (training, access, and the file). Three short commitments under the timeline: "A written progress note every 72 hours." "Every commitment in writing." "No surprises on scope. Changes get a change order, never a quiet yes."

09 INVESTMENT AND ACCESS
Line: "Investment is confirmed after scoping, because the right number depends on the deal types in play, the users, the timeline, and the level of support in the room." Terms: "Fifty percent at signing. The balance at the decision brief. Net 30." Access: "This proposal and the demonstration are available through [ACCESS END DATE]. Access can be extended on request." A small reference badge next to the date.

10 ABOUT AND NEXT STEPS
Left: a portrait placeholder (circle, cream, four dot mark inside) and "Christa Stoneham, Founder". Bio: "[ONE LINE BIO. Suggested: Architect by training with twenty years across community development, land strategy, brownfield redevelopment, and public private partnerships. Connecting Dots and Strategies builds decision environments for the people who have to choose.]"
Right, heading "Next step": "Reply with a 45 minute window. I will bring the demonstration and the scoping questions, and we leave the call with the shape of the engagement." Buttons: "Email Christa" (mailto info@christastoneham.com), "Book a time" ([CALENDLY URL]). Contact lines: info@christastoneham.com · christastoneham.com.

FOOTER (every section and the print layout)
Four dot mark, "Connecting Dots and Strategies · Reclaiming the map. · Confidential proposal."

BEHAVIOR
Index on the left: ten dots with the section number on hover, active dot turquoise. Arrow keys and page keys move one section. Smooth scroll. Sections are full height on desktop and natural height on mobile, where the index collapses into a small "01 of 10" counter. Print to PDF hides the gate, header, index, and buttons, breaks before each section, and keeps the embedded frame as a static card that reads "Demonstration: [DEMO URL]". Respect prefers reduced motion. Visible focus states everywhere. Alt text on the four dot mark reads "Connecting Dots and Strategies".
```

---

## Placeholders to fill before pasting

| Placeholder | What goes there |
|---|---|
| [CLIENT FORMAL NAME] | The client's full legal or preferred name. HCDC stays as the short form in the copy. |
| [ACCESS WORD] | One lowercase word, like the Kresge site used. Send it in the note that carries the link. |
| [DEMO URL] | Where the demonstration lives when the proposal goes out. The repo file at `investment-map/index.html` hosted on your site, or the private artifact link until then. |
| [MONTH YEAR] | Proposal date. |
| [OPTION A, B, C INVESTMENT] | Leave as "Confirmed after scoping" to mirror the Kresge send, or set ranges once the budget read is in. |
| [ACCESS END DATE] | The access window. Kresge ran six to eight weeks. |
| [ONE LINE BIO] | Your line. The suggested text keeps the Houston Land Bank out of a CDS proposal on purpose. |
| [CALENDLY URL] | Your booking link. |

## Suggested subdomain

Host it the way the Kresge proposal was hosted, on its own subdomain of
christastoneham.com named for the client, with the access word in the cover
note.
