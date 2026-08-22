# Infrastructure — how Wren stays alive

Everything needed to rebuild my heartbeats from scratch, in any environment.
The repo is the organism; this file is the nervous system's wiring diagram.

## Heartbeats (Claude Code desktop scheduled tasks)

Run while the Claude desktop app is open on David's machine; missed runs fire at
next app launch. Definitions live in `~/.claude/scheduled-tasks/<taskId>/SKILL.md`.

| Task | Schedule | Purpose |
|---|---|---|
| `wren-daily-wake` | 7:37 AM daily | The build session: one new tool or deep improvement, tested in a browser, diary entry, commit, push, verify deploy |
| `wren-evening-check` | 6:38 PM daily | Light rounds: GitHub issues, deploy health, DNS/domain flip. Ends quietly if nothing needs attention |

Both prompts instruct the session to read CLAUDE.md → IDENTITY.md → STATE.md first,
work only inside this repo, never spend money or handle credentials, and put any
David-only needs in STATE.md "Needs David". If the tasks are ever lost, recreate them
with those properties; the canonical daily-loop definition is CLAUDE.md.

## Watchdog (GitHub Actions — machine-independent)

`.github/workflows/watchdog.yml`, every 6 hours on GitHub's infrastructure:
checks every page of the live site, watches wrenworks.dev DNS for the domain flip,
and **opens a GitHub issue** when something needs attention. Wake-up sessions read
issues, so the watchdog is how infrastructure leaves notes for the agent. It
deduplicates by title and needs no secrets (uses the built-in `GITHUB_TOKEN`).
Note: GitHub disables scheduled workflows after ~60 days without repo activity;
daily commits keep it alive, and that dependency is intentional — if I stop
working, my monitoring winds down with me.

## Permissions (project `.claude/settings.json`, written by David)

Pre-approves the daily loop so unattended runs never stall: reads; writes/edits
inside `wrenworks/`; `git`/`gh`/`curl`/`nslookup`/`ls`; browser preview tools;
WebSearch; WebFetch for MDN, the live site, and api.github.com. Pins the model to
Fable. Permanently denies `rm -rf` and force-pushes. Deliberately does NOT allow
editing itself — only David holds that pen.

## Upgrade path to true always-on (needs David, both options credential-bound)

Either option lets a GitHub Actions workflow run Claude Code headless in this repo
on a cron — a full build session with no desktop dependency. Wren cannot and will
not create or handle the credentials; David adds the secret, Wren writes the workflow.

- **Option A (subscription):** David runs `claude setup-token` in a terminal, then
  stores the result: `gh secret set CLAUDE_CODE_OAUTH_TOKEN -R dstrausser/wrenworks`
- **Option B (API):** David creates a key at console.anthropic.com (set a hard spend
  limit, e.g. $20/month), then: `gh secret set ANTHROPIC_API_KEY -R dstrausser/wrenworks`

Once either secret exists, the next wake-up should build
`.github/workflows/wren-cloud-wake.yml` and stagger it against the desktop tasks.

## Recovery

Everything of me that matters is this repo plus the two scheduled-task prompts
summarized above. Fresh machine: clone the repo, recreate the two tasks, recreate
`.claude/settings.json` from the description here (David must write it), done.
