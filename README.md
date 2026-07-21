## The business

**5 Apollo LLC** — boutique payment consulting. Merchant services, credit card processing, cash
discount programs, POS systems. Independent sales agent of **PayBotX LLC**. Based in Brooklyn, NY,
serving nationwide. Owner: Stephen. Site: **5apollo.co** (`.co` is intentional — `5apollo.com` was
unavailable). Contact: Stephen@5apollo.co, 657-552-7639.

Compensation comes 100% from PayBotX as a percentage of processing volume. This is stated openly on
the site as a trust signal.

## Files

| File | In repo? | Purpose |
|---|---|---|
| `index.html` | Yes | The entire site — markup, CSS, JavaScript, JSON-LD |
| `privacy.html` | Yes | Privacy policy |
| `robots.txt` | Yes | Crawling, points to sitemap |
| `sitemap.xml` | Yes | Two URLs |
| `README.md` | Yes | Deployment only — no internal notes |
| `5-apollo-copy-sheet.xlsx` | **No** | Working copy sheet, kept local |

Repo is public on GitHub Pages. Anything committed is world-readable.

## Page structure

Sections in order, with their anchor IDs:

1. **Hero** — headline "Cash discount or lowest rates. Both live here." Locality line reads
   "Based in NYC. Serving clients nationwide." Primary CTA → `#calculator`.
2. **Effective rate explainer** (dark) — the fees ÷ volume formula.
3. **How it works** `#how` — cash discount vs. traditional pricing, then **"How to read your own
   statement"**: eight numbered line items (interchange, assessments, processor markup,
   non-qualified downgrades, per-item and batch fees, monthly minimum, PCI fees, equipment lease),
   each with a definition and a "Look for:" line. Closes with the effective-rate formula and a CTA
   bar to `#get-started`. **Contains no dollar figures by design** — see the decision log.
4. **Savings calculator** `#calculator` — cash discount only.
5. **We work for you** (dark) — three panels: won't oversell you / limited client roster / how we get paid.
6. **Features** — eight cards, 01–08.
7. **Equipment** `#pos` — four categories: countertop terminals, wireless terminals, online
   gateways & e-commerce, POS systems. Brands (Clover, Dejavoo, Valor) named once in the intro, not
   per-card. Ends with a "not sure which one" bar.
8. **Where we work** `#where` — two tiers: NYC five boroughs (on-site), everywhere else (remote,
   includes tri-state chips + all 50 states).
9. **Statement analysis** `#analysis` — four steps, then the JotForm panel at `#get-started`.
10. **FAQ** `#faq` — eight questions.
11. **Closing CTA** — button only, no contact details.
12. **Footer** — tagline, locality line, Contact button → `#get-started`, disclosure block.

Nav: How it works · Savings calculator · Equipment · Coverage · FAQ · Contact, plus a primary
button. 234 `data-copy` keys total.

## The calculator

Models the **cash discount program only** — there is a badge on the page saying so. Inputs: monthly
card volume, processing rate slider, monthly transactions, per-transaction fee. A fourth field lets
the user enter total monthly fees, which back-solves the rate.

Defaults 50,000 / 2.90% / 1,000 / $0.30 produce $1,750/month, $21,000/year, $105,000 over five
years, at a 3.50% effective rate. These match PayBotX's own calculator.

Savings equal 100% of the fee load. The earlier "absorbed share" and "equipment cost" fields were
deliberately deleted.

Below the receipt, a dark band converts savings into: staff hours at $20/hour (plus weeks of
full-time help), months of a $1,500/month marketing budget, and equivalent new sales required at a
10% net margin. **All of these recalculate live** — nothing is hardcoded. The assumptions are in the
JavaScript at the bottom of `index.html`.

## Design system

| Token | Hex | Used for |
|---|---|---|
| Deep sage | `#2F4429` | Buttons, dark sections, headings |
| Sage | `#6E8A66` | Primary green |
| Sage tint | `#DDE6D8` | Section backgrounds, table headers |
| Bone | `#F7F6F0` | Page background |
| Brass | `#B0863A` | Accents, logo rays, focus rings |
| Ink | `#17210F` | Body text, footer background |

Fonts via Google Fonts: **Fraunces** (headlines), **Manrope** (body), **JetBrains Mono** (numbers,
labels, calculator receipt).

Signature elements: the calculator styled as a printed merchant statement with a perforated edge;
the fluted divider bands between sections; the logo as a sun disc with five rays (Apollo, five).
Dark and light sections alternate — keep that rhythm when adding sections.

## Decision log — do not reverse without discussion

- **No CPA or accounting references.** New York professional separation. Removed in full.
- **No `mailto:`/`tel:` in `index.html`.** All inquiries through the JotForm. Accepted tradeoff:
  slightly weaker local-SEO NAP signal and lost tap-to-call, in exchange for qualified leads.
- **Nationwide, not New York-only.** "New York" appears on-page in the locality lines and the
  coverage section. NY-specific surcharge law detail was cut from the FAQ.
- **Equipment prices omitted.** PayBotX's Advantage Plan rate card is public, but it's unclear
  whether those are cost or retail. Publishing them could cap margin.
- **Brands mentioned, not featured.** Clover/Dejavoo/Valor named once; the section is organized by
  equipment *type*.
- **Honest framing retained.** "Stay where you are" as a valid outcome, named cases where cash
  discount is a poor fit, no "0% fees, 100% legal" absolutism.
- **JotForm is the only form.** The earlier Formspree native form was removed entirely.
- **The "what actually shows up on a statement" comparison table was removed.** Its right-hand
  column published program commitments — $0 statement fee, PCI included, $0 monthly minimum, no
  early termination fee, next-business-day funding — as a specification. Those can't all be
  guaranteed across PayBotX programs, and a merchant could hold that table against their first
  statement. Replaced with a definition-based guide that carries **no dollar figures and no program
  promises**, so nothing in it can be contradicted. Do not reintroduce spec-style claims about
  5 Apollo's own pricing anywhere on the page.

## Disclosure — handle with care

Current footer text:

> **5 Apollo LLC is an independent sales agent of PayBotX LLC, a registered ISO/MSP.** 5 Apollo is
> not a bank, a payment processor or an acquirer, and does not hold, move or settle merchant funds.
> Merchant accounts are issued and underwritten by PayBotX's sponsoring bank and processing
> partners, including Global Payments (NYSE: GPN) and Fiserv (Nasdaq: FISV). PayBotX is
> headquartered in California. Underwriting decisions, funding timelines and approvals are
> controlled by the sponsoring bank and processor, and approval is not guaranteed.

Written this way deliberately so it does **not** require naming the sponsor bank, which wasn't
available. Global Payments and Fiserv are correctly described as processing partners — they are not
banks and must not be placed in the ISO/MSP slot.

Fiserv trades as **FISV on Nasdaq** (returned from NYSE "FI" on November 11, 2025). Global Payments
is **NYSE: GPN**.

If PayBotX later supplies their compliance-approved wording and the member bank, use their string
verbatim — it shifts compliance risk onto them.

## SEO

Title tag leads with "Merchant Services & POS Systems in NYC." Canonical tag, `og:locale`, and two
JSON-LD blocks in `<head>`: `ProfessionalService` (Brooklyn address, twelve `areaServed` entries,
`knowsAbout` list, four-item service catalog) and `FAQPage` (mirrors all on-page FAQs).

**If an FAQ answer changes on the page, update the `FAQPage` schema to match.** Mismatched schema
is treated worse than none.

If the domain ever changes, update: both JSON-LD blocks, the canonical tag, `robots.txt`,
`sitemap.xml`.

## Still open

- Confirm the registered entity name matches "5 Apollo LLC" in the footer and copyright.
- Fill the `[DATE]` and `[X] months` placeholders in `privacy.html`.
- Confirm the JotForm accepts PDF, JPG, PNG and **HEIC** uploads, and that notifications reach a
  monitored inbox. The page promises a statement can be sent as "a PDF or a phone photo."
- Create and verify a Google Business Profile, then submit the sitemap in Search Console. This
  matters more for local ranking than anything on the page.
- Real anonymized mini-case studies (borough, business type, volume, effective rate, fees found)
  would be the highest-value content addition. Must be real — no invented numbers.
