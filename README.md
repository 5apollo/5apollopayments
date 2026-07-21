# 5 Apollo — landing page

Static single-page site for 5 Apollo LLC. No build step, no dependencies, no framework.
Everything is in one file: `index.html` contains the HTML, CSS and JavaScript.

## Files

| File | What it is |
|---|---|
| `index.html` | The entire site — markup, styles, calculator logic |
| `privacy.html` | Privacy policy, linked from the footer |
| `README.md` | This file |
| `5-apollo-copy-sheet.xlsx` | Editable copy sheet (not deployed — keep it out of the repo, or in a `/docs` folder) |

## What's on the page

Sections in order: hero → effective-rate explainer → cash discount vs. traditional pricing (with
comparison table) → savings calculator → we work for you → what you get → equipment →
from analysis to active (JotForm) → FAQ → closing CTA → footer.

**Savings calculator.** Models the Cash Discount Program only. Four inputs (monthly card volume,
processing rate, monthly transactions, per-transaction fee) drive a live receipt and a
"what that could fund" band showing staff hours, marketing months, and the equivalent new sales
required at a 10% net margin. Every figure recalculates on each keystroke — nothing is hardcoded.
The assumptions ($20/hour, $1,500/month, 10% margin) live in the JavaScript at the bottom of
`index.html`.

**Contact routing.** Every call to action points at `#get-started`, the anchor on the JotForm panel.
There are deliberately **no `mailto:` or `tel:` links in `index.html`** — all inquiries route through
the form so they arrive with information attached. Don't reintroduce contact links without
deciding you want that.

## Deploy on GitHub Pages

1. Create a public repo (e.g. `5apollo-site`).
2. Upload `index.html`, `privacy.html` and `README.md` to the root of the `main` branch.
3. Settings → Pages → Source: **Deploy from a branch** → Branch: `main`, folder: `/ (root)` → Save.
4. Live in about a minute at `https://<username>.github.io/5apollo-site/`.

## Custom domain (5apollo.co)

The domain is **`.co`**, not `.com` — `5apollo.com` was unavailable. All email addresses use
`@5apollo.co`.

1. Settings → Pages → Custom domain → enter `5apollo.co` → Save. This creates a `CNAME` file in the repo.
2. At your registrar, add four A records for the apex domain pointing to:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
3. Add a CNAME record for `www` → `<username>.github.io`.
4. Return to Settings → Pages and tick **Enforce HTTPS** once the certificate is issued.

## The JotForm

The statement-analysis form is embedded in the panel with `id="get-started"`:

```html
<div id="jotform-embed">
  <script type="text/javascript" src="https://form.jotform.com/jsform/261524445490053"></script>
</div>
```

This is the `jsform` (script) embed, which auto-resizes to the form's content. To swap forms,
replace the `src` with the new form ID. Nothing else on the page needs to change.

Note: the embed will not render from a `file://` path in some browsers. If it looks blank when you
open `index.html` by double-clicking it, that's expected — it appears once served over https.

### Confirm on the JotForm side before launch

- [ ] The form has a **file upload field** accepting PDF, JPG, PNG **and HEIC**. iPhone photos
      default to HEIC and some upload widgets reject it silently. The page promises twice that a
      statement can be sent as "a PDF or a phone photo."
- [ ] Email notifications are on and pointed at an inbox you actually monitor. With no email
      fallback on the site, a misconfigured notification means leads sit in the JotForm dashboard
      and nowhere else.
- [ ] Suggested fields: name, business name, email, phone, current processor, monthly card volume,
      statement upload.

## Before going live — site checklist

- [ ] Confirm the legal entity name in the footer disclosure and copyright (currently "5 Apollo LLC").
- [ ] Fill the `[DATE]` and `[X] months` placeholders in `privacy.html`.
- [ ] Decide whether to publish equipment pricing. Prices are currently omitted — see the
      Settings tab of the copy sheet for the reasoning.
- [ ] Confirm the fee ranges in the "What actually shows up on a statement" table match what you
      see in the field.
- [ ] Optional but recommended: ask PayBotX compliance for their approved ISO/MSP disclosure
      wording, including the sponsoring member bank. The current disclosure is written so it does
      not require the bank name, but naming it is stronger — and using their approved string
      verbatim shifts the compliance risk onto them.

## Editing the copy

Every visible string carries a `data-copy="section.key"` attribute. Those keys match column B of
`5-apollo-copy-sheet.xlsx`. Edit column E (the yellow column), leave column B alone, and the page
can be regenerated from the sheet without touching layout or styling.

Colours, fonts and calculator assumptions are on the sheet's **Settings & links** tab.

## Brand reference

| Token | Value | Used for |
|---|---|---|
| Deep sage | `#2F4429` | Buttons, dark sections, headings |
| Sage | `#6E8A66` | Primary brand green |
| Sage tint | `#DDE6D8` | Section backgrounds, table headers |
| Bone | `#F7F6F0` | Page background |
| Brass | `#B0863A` | Accent — logo rays, step numbers, focus rings |

Fonts (Google Fonts, loaded in `<head>`): **Fraunces** for headlines, **Manrope** for body,
**JetBrains Mono** for numbers, labels and the calculator receipt.
