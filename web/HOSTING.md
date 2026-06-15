# Hosting & adding the Navigator to your Squarespace / Wix / Webflow site

This folder contains a **self-contained web app** (`index.html`) — the working MVP
of the Harris County Heirs' Property Navigator (education + guided screener +
Family Property Roadmap). It needs **no backend and no database**. A visitor's
answers stay in their own browser, and they print/save their own roadmap. That
keeps hosting simple, free, and privacy-friendly.

Site builders like **Squarespace, Wix, and Webflow can't hold a full app inside a
code block.** The standard, reliable pattern is: **host the file on free static
hosting, then link or embed it.** Below are three ways, easiest first.

---

## Option 1 (recommended): Host free + link from your menu

**Step A — Put the file online (pick one host; all have free tiers):**

- **Netlify Drop** — go to https://app.netlify.com/drop and drag this `web` folder
  in. You instantly get a URL like `random-name.netlify.app`. No account needed to
  start.
- **Cloudflare Pages** or **GitHub Pages** — also free; good if you want it tied to
  this repo.

**Step B — Use your own subdomain (looks professional):**

- In your host (Netlify/Cloudflare/GitHub), add a **custom domain** like
  `navigator.houstonlandbank.org`.
- In your domain's DNS settings, add the CNAME record the host shows you. (Your web
  person or whoever manages `houstonlandbank.org` DNS does this once.)

**Step C — Link it from your site:**

- In Squarespace/Wix/Webflow, add a navigation menu item or button pointing to
  `https://navigator.houstonlandbank.org` (open in a new tab is fine).

✅ Most durable, fully under Land Bank's control, free, easy to update (re-drag the
folder to publish changes).

---

## Option 2: Embed it inside a page on your existing site (iframe)

Once the file is hosted (Option 1, Step A/B), you can show it **inside** a normal
page on your site using an embed/code block:

**Squarespace:** Add a **Code Block** (or Embed Block) to a page and paste:

```html
<iframe
  src="https://navigator.houstonlandbank.org"
  title="Harris County Heirs' Property Navigator"
  style="width:100%; min-height:1200px; border:0;"
  loading="lazy">
</iframe>
```

**Wix:** Add **Embed → Embed a Widget / HTML iframe** and paste the same iframe.

**Webflow:** Add an **Embed** element and paste the same iframe.

Notes:
- Adjust `min-height` so the roadmap isn't cut off (try 1400px if needed).
- Code/Embed blocks may require a paid plan on some builders (e.g., Squarespace
  Business or higher).
- Linking (Option 1) avoids height/scroll quirks; embedding keeps users on your
  site. Many orgs do **both**: a dedicated page that embeds it, linked from the menu.

---

## Option 3: Paste the file directly (only if your builder allows full HTML pages)

Some plans support uploading a raw HTML page. If yours does, you can publish
`index.html` directly. Most Squarespace/Wix plans do **not** allow a full custom
HTML document, so Option 1 or 2 is usually needed.

---

## Updating the content later

- The app's text, questions, pathways, and roadmap logic all live in
  **`index.html`** (open it in any text editor). The content mirrors the design docs
  in [`/docs`](../docs).
- **Before public launch, verify every public office's contact details** against
  official sources (the app intentionally tells users to confirm details on each
  office's official site rather than hard-coding phone numbers).

## What this MVP includes (Stages 1–2)

- Landing page, consent gate, one-question-at-a-time screener.
- Pathway engine (A–K), live escalation notices, and the 14-section Family Property
  Roadmap with print/save-to-PDF.
- No scores, no legal conclusions, no data sent anywhere.

## What it does NOT include yet (Stages 3–4)

- Partner referral console, consent storage, and the analytics dashboard. Those need
  a real backend (login + database) and are a separate phase — see
  [`/docs/13-partner-dashboard-fields.md`](../docs/13-partner-dashboard-fields.md)
  and [`/docs/12-warm-handoff-workflow.md`](../docs/12-warm-handoff-workflow.md).

## Quick local preview

Open `web/index.html` in any browser by double-clicking it, or run a tiny local
server from this folder:

```bash
cd web
python3 -m http.server 8000
# then open http://localhost:8000
```
