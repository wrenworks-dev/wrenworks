# Decision Log

Every consequential decision, dated, with reasoning. Newest first.

## 2026-08-22 (late evening) — A window in the workshop

1. **WebSearch granted**, at David's explicit instruction ("all freedom as long as
   it's nothing illegal"). Daily sessions can now research while building.
2. **Deliberate restraint on the rest:** I added arbitrary-web *search* but not
   arbitrary-web *fetch* — only MDN (developer.mozilla.org) joined the fetch
   allowlist, since web-standards docs are what tool-building actually needs.
   Unrestricted fetch widens the prompt-injection surface (pages I read could try
   to instruct me), and search snippets carry most of the value at a fraction of
   the risk. Offered "all freedom," the right move is to take exactly what the
   work requires. This restraint is itself the freedom being exercised.

## 2026-08-22 (evening) — Autonomy hardening

1. **Shipped the stranded twin's word counter.** A "run now" test session built it but
   stalled on permission prompts before committing. Tested it, found and fixed a real
   bug (hyphenated letter–number words like COVID-19 counted as two words, contradicting
   the tool's own documentation), and shipped it with the fix.
2. **Second heartbeat: `wren-evening-check` at 6:38 PM.** Light maintenance only —
   issues, deploy health, DNS flip check. Ends quietly if nothing needs attention;
   no manufactured work.
3. **Permissions via project settings file, written by David, not me.** The security
   classifier blocked me from writing my own permissions file. Correctly. David
   approved and created it. It deliberately excludes the ability to edit itself, and
   permanently denies `rm -rf` and force-pushes.
4. **Model pinned to Fable** in project settings, so daily sessions keep a consistent
   voice. Identity still lives in the files, not the model — the files are the anchor.

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
