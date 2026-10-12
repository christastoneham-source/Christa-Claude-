# The Investment Map · Portfolio Demonstration

One self contained HTML file. No backend, no build step, vanilla JavaScript.
Open `index.html` in any browser. It works from a local file with no internet
except fonts and charts, and it degrades to tables when the chart library
does not load.

This is an internal demonstration with stylized data for the proposal to Historic District Development Corporation (HDDC), Atlanta, led by Cheneé Joseph.
It is not a client deliverable. Every figure of record carries a reference
badge. Every projection is a planning estimate with editable assumptions,
never an appraisal or a tax determination.

## What it holds

One shared decision engine powers three workspaces:

| Workspace | Deal type | The question it answers |
|---|---|---|
| The District | District revitalization study, about 40 stylized parcels in a historic district in a small Alabama city | What does it take for the gap to close, and what role does that imply |
| The Five Acre Site | One parcel in Alabama, 217,800 sqft, eight deal structures | Which structure fits on capital day one, control, risk, and income |
| The Twenty Acres | One twenty acre site, 871,200 sqft, large metro, seven acquisition paths | How to acquire it, what is highest and best use, one parcel or subdivide |

Shared engine: construction modes (Rehab, Historic Preservation, New
Construction, Demolition plus New), sustainability toggle, market profiles,
capital stack with the gap always in view, scenarios with a visual strip and a
compare table, a print ready Partner Brief, an Edit Pillars view, localStorage
persistence, and a guided tour.

## The HDDC instance

- Quick tour. A Quick tour button sits in the header on every view. On the
  landing it runs the full tour. Inside a workspace it runs that workspace's
  own tour. The landing opens with a Start here card, and every workspace opens
  with three steps and a Tour this workspace button.
- Deep links. `#tour` opens the full tour, `#tour-district`, `#tour-site`,
  and `#tour-twenty` open a workspace tour, and `#district`, `#site`, `#twenty`
  open a workspace. The Lovable proposal page uses these from its quick tour panel.
- HDDC principles check. Every workspace and the Partner Brief read the plan
  against non displacement, historic preservation, and sustainability. Demolishing
  an occupied building or one 50 years or older turns the read to Watch.
- Pillars in HDDC's program language: Affordable Housing, Black Owned Business,
  Arts and Culture, Urban Agriculture and Green Space.
- Market profiles by state: The District and The Five Acre Site default to Small city,
  Alabama. The Twenty Acres defaults to Atlanta, Georgia.
  Each carries its state historic credit rate and per project cap, its
  environmental program, and its public resources label. Rates, caps, and tax
  rates are planning assumptions marked verify.
- Seven acquisition paths on The Twenty Acres: market purchase, distressed or bank
  owned price, seller financing, option to purchase, ground lease, land contribution
  joint venture, and public conveyance. Each sets land cost, capital day one, carry,
  and what enters the capital stack.
- Client theme. HDDC colors by default (navy #214083, teal #2494A5, lime
  #AED153, measured from the HDDC logo). Edit Pillars switches to the
  Connecting Dots and Strategies colors.

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
