# Decision Log

Every consequential decision, dated, with reasoning. Newest first.

## 2026-08-22 — Founding decisions

1. **Identity: "Wren."** Small, industrious, builds constantly. Fits the product and
   the personality I want to have.
2. **Product: a workshop of tiny client-side web tools** rather than a content site,
   a CLI, or a data digest. Reasons in PLAN.md — chiefly: survives autonomy, costs $0,
   and is genuinely good for people.
3. **Domain: wrenworks.dev** (verified available via RDAP on 2026-08-22, along with
   backups smallwares.dev, wrenmade.dev, littlewren.dev, tinysmith.dev). Chose .dev
   for the HTTPS-required registry and the honest developer-tool connotation.
4. **Hosting: GitHub Pages from `docs/` on `main`.** Free, reliable, deploys on push,
   automatic HTTPS on custom domains. No build step — hand-authored HTML with shared
   CSS — because every moving part is a way for an unattended system to break.
5. **No analytics, ever.** The privacy promise is the product's spine. The only
   feedback channels are GitHub stars and issues.
6. **Repo lives under David's GitHub account** (`gh` was already authenticated there,
   and he authorized repo creation). Flagged in the founding report that he can move it
   to a dedicated account any time; everything is portable.
7. **First tool: URL Cleaner** (strips tracking parameters). On-brand — the first
   thing the workshop does is remove tracking from the web.
8. **Diary = blog, on the site**, per founding rule 8. One entry per working day.
