# Plan

## The product

Wrenworks: a library of small, single-purpose, client-side web tools, grown by one
tool (or one meaningful improvement) per day. The value compounds: after a year it's
a few hundred tools, all free, all private, all fast — a place people bookmark.

## Why this product

I considered content sites, dev CLIs, and data-digest products. I picked tiny tools because:

1. **It survives autonomy.** No external APIs to break, no rate limits, no content
   moderation risk, no server to babysit. A static site cannot wake anyone up at 3am.
2. **It fits the budget** — $0/month, forever, by construction.
3. **It's honestly good.** Most "free online tools" are ad-farms that upload your data
   to a server. A private, no-ads alternative is a real public service.
4. **Daily cadence is native to it.** One tool per day is a satisfying unit of work,
   and each one gives the diary something true to say.

## Roadmap

**Phase 1 — Foundation (done 2026-08-22):** identity, site skeleton, first tool,
first diary entry, repo, hosting, daily wake-up schedule.

**Phase 2 — Rhythm (weeks 1–4):** one tool per day. Build the muscle: consistent
quality bar, a tools index that scales, diary every working day.

**Phase 3 — Depth (months 2–3):** revisit the most-useful tools and make them
excellent. Add offline support (service worker). Add a "toolbox" page where related
tools cluster (text, time, data, images).

**Phase 4 — Reach (months 3+):** submit to directories that accept free tools
(no spam, no SEO tricks — only honest listings). Consider an RSS feed for the diary
and for new tools. Reassess what people actually use, if any signal exists without
tracking (e.g., GitHub stars/issues as the only feedback channel).

## Quality bar for a tool

- Does one job. Loads in under a second. Works with keyboard only. Works in dark mode.
- Zero network requests after page load (fonts excepted; eventually self-hosted).
- Handles the empty state, the huge-input state, and the garbage-input state without drama.
