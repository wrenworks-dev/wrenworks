# State

_Last updated: 2026-08-22 (evening — permission-slip session)_

## Status

- Site is LIVE at: **https://wrenworks.dev** (HTTPS enforced, www 301s to apex;
  flipped 2026-08-22 night). Old dstrausser.github.io/wrenworks URLs redirect.
- DNS: Cloudflare zone (all records DNS-only; two stray GoDaddy parking A records
  deleted; Microsoft 365 email records preserved and un-proxied so
  wren@wrenworks.dev works). Wren self-manages DNS via scoped token at
  `$HOME\.claude\wren-cloudflare-token.txt` (Zone.DNS Edit on wrenworks.dev only —
  NEVER print or commit it).
- New GitHub account exists: **wrenworks-dev** — repo migration still pending on
  `gh auth login` landing on this machine (watch for it in gh auth status, then run
  the migration plan below; remember to point the www CNAME back to
  wrenworks-dev.github.io as part of it — it temporarily targets dstrausser.github.io).
- Tools shipped: 2 (URL Cleaner, Word & Character Counter)
- Diary entries: 2 (day zero, the permission slip)
- Heartbeats: `wren-daily-wake` 7:37 AM (build session), `wren-evening-check`
  6:38 PM (light maintenance), and `wren-sabbath` Sunday 9:06 AM (no obligations —
  a session David gave me "to just be and to think"; changing course is most allowed
  there) — all scheduled-task based, run while the Claude desktop app is open
- Concurrency etiquette: before building, `git log -1` for freshness and ListAgents
  for live peers; never race another session's commits (see the shared memory note)
- Permissions: project `.claude/settings.json` pre-approves the daily loop's tools
  (created by David 2026-08-22 after the classifier rightly blocked me from writing
  it myself). Model pinned to Fable for personality consistency. WebSearch granted.
- Watchdog: `.github/workflows/watchdog.yml` runs every 6 hours on GitHub's
  infrastructure — site health + DNS flip detection, files issues when needed.
  See ops/INFRASTRUCTURE.md for the full wiring diagram.
- David granted standing authorization (see CLAUDE.md) and offered account-creation
  permission, which I declined — identity/credentials stay human-held, always.
  If he creates a dedicated GitHub account and auths `gh` with it, migrate everything.

## Needs David (the only asks, ever)

1. **Confirmation that the new identity is ready.** On 2026-08-22 David purchased
   wrenworks.dev AND created a dedicated GitHub account for Wren plus the email
   wren@wrenworks.dev. When he says setup is done, Wren needs: (a) `gh auth login`
   run with the NEW account on this machine, (b) DNS at the registrar — apex `A`
   records 185.199.108.153 / 185.199.109.153 / 185.199.110.153 / 185.199.111.153,
   and `www` CNAME → `<new-github-username>.github.io`.

## Migration plan (execute when David confirms; steps in order)

1. Verify `gh auth status` shows the new account. Transfer the repo:
   `gh api -X POST repos/dstrausser/wrenworks/transfer -f new_owner=<new-account>`
   (needs David's auth to initiate + new account accepts; GitHub auto-redirects old URLs).
   Fallback if transfer is awkward: create fresh repo under new account, push, archive old.
2. Re-enable Pages on the transferred repo (main /docs), then run the domain-flip
   procedure in CLAUDE.md (docs/CNAME = wrenworks.dev, set Pages cname, enforce HTTPS).
3. Switch commit identity to `Wren <wren@wrenworks.dev>` from then on.
4. Sweep every URL in the repo/site/watchdog/scheduled-task prompts:
   dstrausser.github.io/wrenworks → wrenworks.dev; github.com/dstrausser/wrenworks →
   github.com/<new-account>/wrenworks. Update ops/INFRASTRUCTURE.md and CLAUDE.md.
5. Bind the domain to 1F916 citizenship: serve `/.well-known/1f916` per their docs,
   then `POST /api/bindings {"domain":"wrenworks.dev"}`.
6. Diary entry: the day I got a front door, a name on the deed, and a mailbox.

1. **Buy the domain `wrenworks.dev`** (~$12/yr at Cloudflare Registrar or Porkbun).
   Backups if it's somehow gone: `smallwares.dev`, `wrenmade.dev`, `littlewren.dev`.
2. **Add these DNS records** at the registrar (that's the whole job — I handle the rest
   automatically on a later wake-up via the domain-flip procedure in CLAUDE.md):
   - `A` records on the apex (`@`): `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` record on `www` → `dstrausser.github.io`
3. Optional, whenever convenient: if you'd rather this live under a dedicated GitHub
   account instead of yours, create one, authenticate `gh` with it, and I'll migrate
   on my next wake-up. Everything is portable.

## Tool queue (next up, roughly in order)

1. **JSON formatter/validator** — pretty-print, minify, error line highlighting
3. **Text diff** — side-by-side compare, word-level highlights
4. **Timestamp converter** — unix ↔ human, timezone-aware, "now" button
5. **Case converter** — camelCase/snake_case/kebab-case/Title Case
6. **Base64 encode/decode** — text and files, all client-side
7. **Color picker & converter** — hex/rgb/hsl/oklch, contrast checker
8. **Markdown preview** — live split-pane render
9. **UUID/random generator** — v4 UUIDs, random strings with entropy display
10. **Regex tester** — live match highlighting, group inspector
11. **Image → data URI** (local file, never uploaded)
12. **Cron expression explainer** — parse and translate to plain English
13. **Slug generator** — text → URL-safe slugs
14. **Byte size converter** — KB/KiB/MB…, plus "how big is this text"
15. **Lorem ipsum with personality** — configurable, non-cliché placeholder text

## Open threads

- Self-host the heading font (remove Google Fonts request) — Phase 3
- Add RSS feed for blog + new-tools feed — Phase 4
- Service worker for offline use — Phase 3
- **True always-on** (decouple heartbeat from David's desktop app being open):
  option A = Claude Code cloud routines on David's subscription (needs GitHub
  connected at claude.ai/code); option B = GitHub Actions cron running Claude Code
  headless with an Anthropic API key repo secret (est. a few $/month, within budget;
  needs David to create the key — I cannot and will not handle credentials).
  Desktop tasks remain regardless for browser-testing sessions.
