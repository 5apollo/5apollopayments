# 5 Apollo — landing page

Static single-page site. No build step, no dependencies.

## Files
- `index.html` — the entire site (HTML, CSS, JS in one file)
- `privacy.html` — privacy policy stub, linked from the footer
- `README.md` — this file

## Deploy on GitHub Pages
1. Create a public repo (e.g. `5apollo-site`).
2. Upload `index.html`, `privacy.html`, `README.md` to the root of the `main` branch.
3. Settings → Pages → Source: **Deploy from a branch** → Branch: `main`, folder: `/ (root)` → Save.
4. Live in ~1 minute at `https://<username>.github.io/5apollo-site/`.

## Custom domain (5apollo.com)
1. Settings → Pages → Custom domain → enter `5apollo.com` → Save. (This creates a `CNAME` file in the repo.)
2. At your registrar, add four A records for the apex domain pointing to:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
3. Add a CNAME record for `www` → `<username>.github.io`.
4. Back in Settings → Pages, tick **Enforce HTTPS** once the certificate is issued.

## Before going live — required
- [ ] Replace `[SPONSOR BANK NAME], [CITY, STATE]` in the footer disclosure. Card brand rules require the sponsor bank name and location; a missing disclosure is a fineable violation.
- [ ] Confirm the legal entity name used in the footer and copyright.
- [ ] Paste your JotForm embed code into `<div id="jotform-embed">` and delete the dashed placeholder block above it. GitHub Pages serves static files only, so the form must be hosted by JotForm.
- [ ] Decide whether to publish equipment pricing. The PayBotX Advantage Plan rate card is public; the site currently omits prices because it is unclear whether those are cost or retail.
- [ ] Point the "Schedule a strategy session" button at a real booking link if you have one (it currently scrolls to the form).
- [ ] Fill the `[DATE]` and `[X] months` placeholders in `privacy.html`.

## Editing the copy
All visible text carries a `data-copy="section.key"` attribute. Those keys match column B of `5-apollo-copy-sheet.xlsx` — edit column E in that sheet and the text can be regenerated back into the page without touching the layout.
