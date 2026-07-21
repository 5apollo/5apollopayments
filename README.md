# 5 Apollo — landing page

Static single-page site. No build step, no dependencies. `index.html` contains all markup, styles
and JavaScript.

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire site |
| `privacy.html` | Privacy policy, linked from the footer |
| `robots.txt` | Allows crawling, points to the sitemap |
| `sitemap.xml` | Homepage and privacy policy |

## Deploy on GitHub Pages

1. Create a public repo and upload all four files to the root of the `main` branch.
2. Settings → Pages → Source: **Deploy from a branch** → Branch `main`, folder `/ (root)` → Save.
3. Live in about a minute at `https://<username>.github.io/<repo>/`.

## Custom domain

The domain is `5apollo.co`.

1. Settings → Pages → Custom domain → `5apollo.co` → Save. This creates a `CNAME` file in the repo.
2. At the registrar, add four A records for `@`:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
3. Add a CNAME record for `www` → `<username>.github.io`.
4. Tick **Enforce HTTPS** once the certificate is issued.

If the domain ever changes, update the URLs in the two JSON-LD blocks in `<head>`, the canonical
tag, `robots.txt` and `sitemap.xml`.

## Editing the copy

Every visible string carries a `data-copy="section.key"` attribute, matching the copy sheet kept
outside this repo. Edit the text between the tags; leave the attributes alone.

The `<head>` contains two JSON-LD blocks. The `FAQPage` block duplicates the on-page FAQ answers —
if an FAQ is edited on the page, update the schema copy to match.

## The form

The statement-analysis form is embedded in the panel with `id="get-started"`:

```html
<div id="jotform-embed">
  <script type="text/javascript" src="https://form.jotform.com/jsform/261524445490053"></script>
</div>
```

To swap forms, replace the `src` with the new JotForm ID. Nothing else needs to change.

The embed does not render from a `file://` path. It only appears once served over http/https.

## Calculator

Four inputs (monthly card volume, processing rate, monthly transactions, per-transaction fee) drive
the receipt and the savings band. Its assumptions — $20/hour staff wage, $1,500/month marketing
budget, 10% net margin — are in the JavaScript at the bottom of `index.html`.

## Links

Every call to action points at `#get-started`. There are intentionally no `mailto:` or `tel:` links
in `index.html`; all inquiries route through the form.

## Brand tokens

| Token | Value | Used for |
|---|---|---|
| Deep sage | `#2F4429` | Buttons, dark sections, headings |
| Sage | `#6E8A66` | Primary green |
| Sage tint | `#DDE6D8` | Section backgrounds, table headers |
| Bone | `#F7F6F0` | Page background |
| Brass | `#B0863A` | Accents, focus rings |

Fonts (Google Fonts, loaded in `<head>`): **Fraunces** headlines, **Manrope** body,
**JetBrains Mono** numbers and labels.
