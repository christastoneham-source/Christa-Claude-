# Deliverable 20 · Lovable build prompt · The Investment Map proposal for HDDC

Paste the block below into Lovable, into the project that holds the Kresge
proposal at dot-connect-proposals.lovable.app, as an update instruction. It keeps
the Kresge pattern (password gate, deck style sections, the demonstration
embedded in its own section, three ways to work together, plain language
deliverables, investment confirmed after scoping, an access window with a date)
and re-dresses it in the client's brand: Historic District Development
Corporation (HDDC), Atlanta, led by Cheneé Joseph, President and CEO.

Fill the bracketed placeholders before you paste. They are listed at the end.
The HDDC hex codes are the one thing to collect first: open hddc.org or the HDDC
logo file, sample the two or three brand colors, and put them in the palette
block. Do not let Lovable guess them.

---

```
Update this proposal site for a new client. Keep the structure, navigation, gate, and print behavior exactly as they work today. Replace the client, the copy, and the palette as specified below. The site is a single page, password gated proposal called "The Investment Map · Proposal for HDDC", prepared by Connecting Dots and Strategies LLC (CDS) for Historic District Development Corporation (HDDC), Atlanta, led by Cheneé Joseph, President and CEO. It reads like a short deck: full height sections, arrow keys and a thin numbered index on the left, and a "Print to PDF" action that lays every section out as a clean letter page. Keep every line of copy in one constants file.

THE GATE
Centered card: the HDDC wordmark line "Prepared for Historic District Development Corporation" above the title "The Investment Map", a pill "Proposal · Sweet Auburn", one password field, and a button "Enter". The access word is "[ACCESS WORD]". Check it client side, remember it in sessionStorage, and show this error on a miss: "That is not the access word. Check the note that came with this link." Under the card, small: "Connecting Dots and Strategies · Reclaiming the map."

PALETTE (client brand, non negotiable once filled)
This proposal is dressed in HDDC's colors, not CDS colors. Define tokens and use only these:
hddc-primary [HDDC PRIMARY HEX]. Headings, section numbers, the gate button, every action and link. This is the only action color.
hddc-secondary [HDDC SECONDARY HEX]. Card top bars, the index dots, table checkmarks.
hddc-accent [HDDC ACCENT HEX, or reuse secondary if HDDC has two colors]. Pills and the recommended option badge.
Page background a warm off white [HDDC NEUTRAL HEX, or #FCFAF1 if none]. Text ink #101C28. Hairline borders #E3DECD. White cards, 12px radius.
The three deal type cards in section 02 use primary, secondary, and accent in that order so the proposal reads as HDDC's document.
CDS keeps one signature only: the four dot mark (Brick #D95448, Gold #F1BA4B, Grove #47AB4F, Turquoise #00BCC5, in that order) beside the CDS name in the footer, and a thin spectrum rule in those four colors, left to right, under the demonstration frame. Nowhere else.
Headings in Fraunces from Google Fonts with Georgia fallback. Body in Inter with system sans fallback. No gradients other than the spectrum rule, no stock photography, no icon libraries.

LANGUAGE RULES
Never use the words software, platform, product, AI, AI powered, or patent pending. Say instrument, decision environment, analysis, demonstration. No em dashes anywhere. Short sentences. Every projection carries "planning estimate, editable assumptions". Every figure of record carries a small "reference" badge.

HEADER (sticky, ink background, off white text)
Left: "The Investment Map" with the small line "Proposal for HDDC". Right: a chip "Prepared for Cheneé Joseph" and a button "Print to PDF".

SECTIONS, in this order, numbered 01 to 10, each with a Fraunces heading.

01 COVER
Line: "Prepared for Historic District Development Corporation". Title "The Investment Map". Pill "Proposal · Sweet Auburn · [MONTH YEAR]". Lede: "One decision engine. Three live deal types. One role question." Beneath: "For Cheneé Joseph, President and CEO, and the HDDC team." Signature: "Christa Stoneham, Founder · Connecting Dots and Strategies LLC". Buttons: "Start" (scrolls to 02) and "Open the demonstration" (opens [DEMO URL] in a new tab).

02 WHAT WE HEARD
Intro: "HDDC has kept residents in place on Auburn Avenue for forty five years. Front Porch proved the model can build again. The next three decisions need the same thing: one shared picture, numbers that move when assumptions move, and a clear read on what role the gap implies."
Three cards with a colored top bar:
Primary, "The District". "The Auburn Avenue blocks as one revitalization study. Parcels of record, four investment pillars, historic preservation priced as its own construction mode with the federal and state credit lines in the stack." The question: "What does it take for the gap to close, and what role does that imply."
Secondary, "[NEXT SITE NAME]". "One parcel with an existing building. Eight deal structures, from buying outright to a public conveyance." The question: "Which structure fits on capital day one, control, risk, and income."
Accent, "[LARGER SITE NAME]". "One larger site, [ACRES] acres. Three subdivision concepts and three price bases." The question: "Should we buy it, what is highest and best use, and should it stay one parcel or subdivide."
Note under the cards: "The demonstration runs on stylized parcels. The engagement runs on HDDC's parcels of record. Non displacement, historic preservation, and sustainability stay the decision criteria throughout."

03 THE DEMONSTRATION
Heading "A working demonstration, not a slide about one." Embed [DEMO URL] in a 16 by 10 frame with a hairline border, lazy loaded, with a button above it "Open in a new tab". The CDS spectrum rule sits under the frame. Caption: "Working demonstration. Stylized data. Planning estimates with editable assumptions, never an appraisal or a tax determination." A short list beside the frame, one line each: "Assign pillars parcel by parcel and watch totals move." "Edit any source line and the gap recalculates in front of you." "Switch Advisor to Equity Partner and read what the role implies for HDDC." "Compare eight deal structures in one table." "Switch three subdivision concepts and three price bases." "Save scenarios, compare them, print a one page Partner Brief."

04 ONE SHARED ENGINE
Heading "One engine under all three." Eight small cards, label plus one line: Construction modes (Rehab, Historic Preservation, New Construction, Demolition plus New). Historic credits (federal and state credit lines enter the stack). Sustainability (a cost premium, green outcomes, and unlockable funding lines). Market profiles (named assumption sets for cost, value, and tax). Capital stack and the gap (total cost minus committed sources, always in view). Scenarios (save, load, compare side by side). Partner Brief (one printed page per scenario). Edit Pillars (rename, recolor, reprice at any time). Closing line: "The HDDC team keeps the instrument. Partners, lenders, and the board receive the paper."

05 THE ROLE QUESTION
Heading "Advisor or Equity Partner." Two columns. Left, "Advisor": "HDDC advises the public partner and earns an advisory fee. Zero balance sheet exposure. Closing the gap means more public, grant, debt, or partner sources." Right, "Equity Partner": "HDDC places equity in the stack, carries that exposure, and holds a share of projected value created. Closing the gap means HDDC capital, and the instrument shows exactly how much." Closing line: "The toggle is the whole conversation. The instrument makes it a number instead of an argument."

06 THREE WAYS TO WORK TOGETHER
Intro: "Pick the shape that fits the decision in front of you. Each one builds on the last."
Three cards. Mark the middle one with an accent pill "Recommended".
A. "Site Instrument". For one deal type. You receive: the decision environment on HDDC's parcels of record for one site, two scenario sessions, one Partner Brief, training and handoff. Timeline: "6 to 8 weeks". Investment: "[OPTION A INVESTMENT or Confirmed after scoping]".
B. "Portfolio Decision Partnership". For all three deal types. You receive: the full decision environment on HDDC's parcels of record, shared pillars and market profiles, monthly decision sessions with the HDDC team, a Partner Brief for every scenario the team wants to carry, training and handoff. Timeline: "4 to 6 months". Investment: "[OPTION B INVESTMENT or Confirmed after scoping]".
C. "Full Investment Case". Everything in B plus capital stack strategy, funding pipeline tracking, environmental screening, lender and board materials, and presentation support in the room. Timeline: "6 to 9 months". Investment: "[OPTION C INVESTMENT or Confirmed after scoping]".
Each card ends with a primary colored button "Choose this path" that scrolls to section 10.

07 DELIVERABLES IN PLAIN LANGUAGE
A table with columns Deliverable, What it is, A, B, C. Checkmarks in hddc-secondary. Rows:
Web hosted decision environment. "HDDC's parcels, pillars, and assumptions in one place the team can open from any browser." A B C.
Scenario comparisons. "Save any state under a name and put scenarios side by side." A B C.
Decision criteria. "Non displacement, historic preservation, and sustainability written down as the questions each workspace answers, agreed before the numbers." A B C.
Financial views. "Capital stack, the gap, value created, and new annual property tax for every scenario." A B C.
Partner Brief. "One printed page per scenario for lenders, partners, and the board." A B C.
Environmental screening. "A first read on brownfield and site condition risk before capital moves." C.
Funding pipeline tracking. "Sources, stages, and asks tracked against the gap." C.
Lender and board materials. "Decks, briefs, and the presentation itself." C.
Training and handoff. "The HDDC team keeps the instrument and knows how to run it." A B C.
Under the table: "Planning estimates with editable assumptions throughout, never an appraisal or a tax determination."

08 HOW WE WORK
Five steps on a horizontal timeline: "Discovery" (two weeks: parcels of record, pillars, decision criteria), "Build" (the decision environment on HDDC's data), "Scenario sessions" (the team works the instrument together), "Decision brief" (the recommendation and the Partner Briefs), "Handoff" (training, access, and the file). Three commitments under the timeline: "A written progress note every 72 hours." "Every commitment in writing." "No surprises on scope. Changes get a change order, never a quiet yes."

09 INVESTMENT AND ACCESS
Line: "Investment is confirmed after scoping, because the right number depends on the deal types in play, the users, the timeline, and the level of support in the room." Terms: "Fifty percent at signing. The balance at the decision brief. Net 30." Access: "This proposal and the demonstration are available through [ACCESS END DATE]. Access can be extended on request." A small reference badge next to the date.

10 ABOUT AND NEXT STEPS
Left: a portrait placeholder and "Christa Stoneham, Founder". Bio: "[ONE LINE BIO. Suggested: Architect by training with twenty years across community development, land strategy, brownfield redevelopment, and public private partnerships. Connecting Dots and Strategies builds decision environments for the people who have to choose.]"
Right, heading "Next step": "Cheneé, reply with a 45 minute window. I will bring the demonstration and the scoping questions, and we leave the call with the shape of the engagement." Buttons: "Email Christa" (mailto info@christastoneham.com), "Book a time" ([CALENDLY URL]). Contact lines: info@christastoneham.com · christastoneham.com.

FOOTER (every section and the print layout)
Left: "Prepared for Historic District Development Corporation · Confidential proposal." Right: the CDS four dot mark and "Connecting Dots and Strategies · Reclaiming the map."

BEHAVIOR
Index on the left: ten dots in hddc-secondary with the section number on hover, active dot hddc-primary. Arrow keys and page keys move one section. Smooth scroll. Sections are full height on desktop and natural height on mobile, where the index collapses into a small "01 of 10" counter. Print to PDF hides the gate, header, index, and buttons, breaks before each section, and keeps the embedded frame as a static card that reads "Demonstration: [DEMO URL]". Respect prefers reduced motion. Visible focus states everywhere. Alt text on the four dot mark reads "Connecting Dots and Strategies".
```

---

## Placeholders to fill before pasting

| Placeholder | What goes there |
|---|---|
| [HDDC PRIMARY HEX], [HDDC SECONDARY HEX], [HDDC ACCENT HEX], [HDDC NEUTRAL HEX] | Sampled from hddc.org or the HDDC logo file. Three colors is enough; reuse secondary for accent if they have two. |
| [ACCESS WORD] | One lowercase word, sent in the note that carries the link. |
| [DEMO URL] | Where the demonstration lives when the proposal goes out. `investment-map/index.html` hosted on your site, or the private artifact link until then. Rename the instrument's role labels from HCDC to HDDC first. |
| [NEXT SITE NAME], [LARGER SITE NAME], [ACRES] | The two HDDC sites behind the five acre and twenty acre workspaces. If they are not named yet, use "The next site" and "The assemblage". |
| [MONTH YEAR] | Proposal date. |
| [OPTION A, B, C INVESTMENT] | Leave as "Confirmed after scoping" to mirror the Kresge send, or set ranges once the budget read is in. |
| [ACCESS END DATE] | The access window. Kresge ran six to eight weeks. |
| [ONE LINE BIO] | Your line. The suggested text keeps the Houston Land Bank out of a CDS proposal on purpose. |
| [CALENDLY URL] | Your booking link. |

## Context used for the copy

Public record, verify before the call: HDDC was organized in 1980 by Coretta
Scott King, Christine King Farris, and John Cox to restore the Sweet Auburn and
Martin Luther King Jr. historic district. Its principles are non displacement,
historic preservation, and sustainability, with more than 110 single family
homes and more than 50 affordable rental units built or rehabilitated since
1994. Front Porch on Auburn opened in 2025 as the first new development on that
stretch of Auburn Avenue in about two decades, with Reinvestment Fund
construction financing. Cheneé Joseph is President and CEO. Office: 522 Auburn
Ave NE, Atlanta, GA 30312.
