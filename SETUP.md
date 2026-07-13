# Setup — go from clone to running

**First run = discovery before execution.** Before any outreach, the agent configures to YOUR machine and work accounts: it auto-detects what it can (work folder, connected tools, whether a git remote is set), then asks you in ONE consolidated pass for the rest and gets your approval before creating/changing anything. It establishes:
- **Work folder** on your Desktop (where this system lives + your live files) — created only with your OK.
- **Your assigned WORK GitHub repo** — under your *work* GitHub account, assigned by the company (Testsigma), **never a personal repo**, and never pushed to personal. If none is assigned yet, the agent flags it.
- **Tool/connection inventory** — work Chrome profile, sequencing tool (web + API), work email for reply capture, and SF/G2 via your WORK claude.ai "Work" browser tab group.

Then it does the interview below. Full protocol: `skills/onboarding/SKILL.md` Step 0.

Two ways to do this: let your agent run it (fast), or do it by hand.

## Option A — Agent-driven (recommended)
1. Open your AI agent (Claude Code / Cowork) in this folder.
2. Say: **"Run the onboarding skill."**
3. It will interview you, fill `config.json`, define your voice, replace every placeholder, and help connect your tools. Answer honestly — the quality of your outreach depends on real proof points and a real ICP, not guesses.

## Option B — By hand
Work through these in order. The onboarding skill (`skills/onboarding/SKILL.md`) is the same checklist if you want detail.

1. **Config:** `cp config.example.json config.json`, then fill in every `{{PLACEHOLDER}}`. This one file drives the whole kit.
2. **Voice:** open `memory/context/voice-profile.md` and make it yours (your tone, your do's/don'ts, your sign-off). Keep the structural rules; change the personality.
3. **Placeholders:** replace `{{...}}` tokens in `CLAUDE.template.md` → save as `CLAUDE.md`; `AGENTS.template.md` → `AGENTS.md`; and across `memory/` + `skills/`. Grep for `{{` when done — zero hits = configured.
4. **Tools:** connect your CRM / enrichment / email / LinkedIn. The skills call tools by the names in `config.json` — if your stack differs from the examples, update those references.
5. **Empties:** copy each `*.example.*` file to its live name (`cp MASTER_SENT_LIST.example.csv MASTER_SENT_LIST.csv`, same for `data/*.example.csv` and `memory/*.example.md`). The live names are gitignored, so you fill them through real work and `.gitignore` keeps them from ever being pushed.
6. **First run:** start a session, ask for one small prospect batch, and confirm the gates use *your* ICP, proof points, sender, and voice.

## Operating rules baked in from live runs (your agent honors these out of the box)
- **Quota semantics:** "send N emails / M LinkedIn" always means **N net-new first-touch emails and M new connection requests** — due follow-up tasks are pulled first and done IN ADDITION, never counted toward N/M.
- **Your formulas are editable, on request.** Say "use this formula instead" / "write them more like X" and the agent captures your version verbatim, writes it into the writing canon as a dated override (old formula archived), confirms with one sample, and uses yours from then on. Style is fully swappable; safety gates (verified-email only, dedup/DNC, no fabrication, one batch approval, send logging) are not.
- **Performance analysis on request:** "analyze my outreach performance" runs a read-only statistical review (rates with confidence intervals by formula/persona/anchor/subject; no recommendations from tiny samples) and proposes KEEP/CHANGE/TEST — changes only apply through the formula-override flow with your approval.
- **Security at transfer:** everything operator-specific lives in gitignored files (`config.json`, live CSVs/memory). Before any push, the agent greps for names/emails/IDs that aren't yours and blocks the commit if it finds someone else's.

## The one rule that matters most
This kit ships **empty on purpose**. Never paste another rep's contacts, sent list, DNC names, account list, or tool IDs into it. Bring your own — that's the whole point.

## What "good" looks like after setup
- `grep -r "{{" .` returns nothing.
- The only person's name/email in the repo is yours.
- `config.json` is gitignored and not staged.
- A dry-run batch reads your config end to end.
