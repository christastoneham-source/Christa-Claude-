# Deliverable 21 · Lovable fix prompt · HDDC engagement models and features by tier

Middle path: shorter cards, scope and limits kept but folded away, no founding rate, the
confidentiality box untouched. Paste the block below into Lovable as one message.

```
Update the /hddc page in two places only: the ENGAGEMENT MODELS section above the confidentiality box, and the FEATURES BY TIER section. Do not edit, move, or remove the "Confidentiality and ownership" box, the NDA note under it, the "Pricing holds through November 24, 2026." line, or the "Read the NDA summary" link. Keep every other section, the palette, the typography, and the language rules (no em dashes, no en dashes, no hyphenated words, no exclamation points). Edit the strings in src/content/hddc.ts. Change nothing else.

1. TIER CARDS
Keep the eyebrow, the headline, the intro paragraph, and three cards side by side. Each card shows: eyebrow, name, one line description, time, price, line under the price, four bullets, then the existing Scope and limits text folded into a disclosure. The disclosure is a button labeled "Scope and limits" with aria-expanded, closed by default on screen, always open in print. Keep each card's Scope and limits wording as it is now.

TIER 1 · keep the "START HERE" ribbon
Name: "The Instrument"
Description: "The Investment Map, set up for HDDC's three decisions and run by your staff."
Time: "6 to 8 weeks"
Investment: "$45,000"
Line under the price: "Fixed fee. Includes 12 months of hosted access."
Bullets:
  "All three decisions loaded with HDDC's sites"
  "The capital stack, the gap, the role read, and the principles check on every scenario"
  "Onboarding and a written guide, so your staff runs it day to day"
  "Hosted access and support for 12 months"

TIER 2
Name: "Instrument and Practice"
Description: "The instrument plus my practice, working the three decisions with your team."
Time: "6 or 9 months"
Investment: "$95,000 to $135,000"
Line under the price: "Set by the length of the advisory term. Includes the 12 month license."
Bullets:
  "Everything in Tier 1"
  "Assumptions set to HDDC's own costs, rents, and standards"
  "Working sessions and written recommendations"
  "The three decisions in priority order, with a board decision brief"

TIER 3 · eyebrow "ADD ON TO TIER 2"
Name: "Lender Ready Case"
Description: "One priority site carried to a financing case a lender can review."
Time: "3 to 4 months"
Investment: "$60,000 to $90,000"
Line under the price: "Added to Tier 2. Set by the site's environmental and historic credit work."
Bullets:
  "Full pro formas and sources and uses for the priority site"
  "An appraisal support package"
  "An investment packet for lenders and a board presentation"
  "A phased implementation plan"
Remove the line "Available after a Tier 1 or Tier 2 engagement."

2. PRICE NOTES
Replace everything between the tier cards and the confidentiality box (the "WHAT THE PRICE COVERS" list and the paragraphs under it, including the founding rate sentence) with one short list under the eyebrow "GOOD TO KNOW":
  "Final scope, sessions, and fee are set together in a scoping call and confirmed in the engagement agreement."
  "Payments are spread across the engagement."
  "Year two hosted access and support: $15,000, optional."
  "Move from Tier 1 to Tier 2 within 90 days, and half of the Tier 1 fee counts toward Tier 2."
  "Any tier can be structured to fit a capacity building or technical assistance grant. I will help package the request."
  "Not included in any tier: appraisals, environmental assessments, surveys, title work, legal opinions, and travel."

3. FEATURES BY TIER
Keep the eyebrow, the headline, and "SCOPE AT A GLANCE" exactly as they are. Remove "HOW FEATURES ARE SCOPED".
Replace the table with this one. Header: "Deliverable", "Tier 1 · The Instrument ★", "Tier 2 · Instrument and Practice", "Tier 3 · Lender Ready Case (added to Tier 2)". The star carries visually hidden text "Start here". Tint the Tier 1 column. Use a filled dot for included and a short dash for not included, each with visually hidden text.
  "The full instrument for all three decisions" · included, included, included
  "Hosted access, staff logins, and support for 12 months" · included, included, included
  "Assumptions set to HDDC's costs, rents, and standards" · not included, included, included
  "Working sessions and written recommendations" · not included, included, included
  "Site control review and program screening for each site" · not included, included, included
  "Priority order and a board decision brief" · not included, included, included
  "Full pro formas and sources and uses for one priority site" · not included, not included, included
  "Appraisal support package" · not included, not included, included
  "Lender investment packet and board presentation" · not included, not included, included
  "Phased implementation plan" · not included, not included, included
One footnote under the table, hddc-muted: "Every tier covers all three decisions. Final scope is set in the engagement agreement."

4. CHECK
Confirm the confidentiality box, the NDA note, the pricing hold line, and the NDA summary link are unchanged and in the same place. Confirm the prices agree on the cards and in the table. Confirm no em dashes, en dashes, or hyphenated words were added. List what you changed.
```
