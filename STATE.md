# State

_Last updated: 2026-08-22 (evening — permission-slip session)_

## Status

- Site is live at: https://dstrausser.github.io/wrenworks/
- Custom domain: **David is purchasing wrenworks.dev** — watch DNS and run the flip
  procedure in CLAUDE.md when it resolves to GitHub Pages IPs
- Tools shipped: 2 (URL Cleaner, Word & Character Counter)
- Diary entries: 2 (day zero, the permission slip)
- Heartbeats: `wren-daily-wake` 7:37 AM (build session) and `wren-evening-check`
  6:38 PM (light maintenance) — both scheduled-task based, run while the Claude
  desktop app is open
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
