# The Investment Map · Portfolio Demonstration

One self contained HTML file. No backend, no build step, vanilla JavaScript.
Open `index.html` in any browser. It works from a local file with no internet
except fonts and charts, and it degrades to tables when the chart library
does not load.

This is an internal demonstration with stylized data for a client proposal.
It is not a client deliverable. Every figure of record carries a reference
badge. Every projection is a planning estimate with editable assumptions,
never an appraisal or a tax determination.

## What it holds

One shared decision engine powers three workspaces:

| Workspace | Deal type | The question it answers |
|---|---|---|
| The District | District revitalization study, about 40 stylized parcels in a small Southern city | What does it take for the gap to close, and what role does that imply |
| The Five Acre Site | One parcel, 217,800 sqft, eight deal structures | Which structure fits on capital day one, control, risk, and income |
| The Twenty Acres | One bank owned site, 871,200 sqft, large metro | Should we buy it, what is highest and best use, one parcel or subdivide |

Shared engine: construction modes (Rehab, Historic Preservation, New
Construction, Demolition plus New), sustainability toggle, market profiles,
capital stack with the gap always in view, scenarios with a visual strip and a
compare table, a print ready Partner Brief, an Edit Pillars view, localStorage
persistence, and a guided tour.

## Projection math (planning estimates)

- cost = basis sqft × cost per sqft × mode adjustment × market multiplier
- count outcomes = floor(basis sqft ÷ sqft per unit factor)
- dollar outcomes = basis sqft × dollars per sqft factor
- value after investment = total investment × value factor
- value created = value after investment minus current assessed value
- new annual property tax = value after investment × effective tax rate
- the gap = total cost minus committed sources

## Files

- `index.html` is the instrument.
- `screenshots/` holds the acceptance walkthrough captures and the printed
  Partner Brief PDF, one image or more per checklist item.

## Reset

Everything saves in the browser. Use the help button or the footer Reset link
to return to the demonstration defaults.
