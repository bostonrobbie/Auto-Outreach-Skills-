# Readiness Checklist — before this kit goes to the team

Run top to bottom. The kit is ready to share when every box is checkable.

## Safety (do these before any push)
- [ ] PII scan clean: grep the whole tree for any real name, email, phone, customer, or tool ID. Zero hits outside `*.example.*` menu options.
- [ ] `config.json`, `.env`, and all live data files are gitignored and unstaged.
- [ ] Only `*.example.*` blank templates ship; no live `MASTER_SENT_LIST.csv` / `target-accounts.csv` / `do-not-contact.md` / warm-leads / call-log / pipeline.
- [ ] No sequence/campaign IDs, webhooks, or API keys anywhere in tracked files.

## Completeness
- [ ] Front door: `README.md`, `SETUP.md`, `ARCHITECTURE.md` present and accurate.
- [ ] Brain: `CLAUDE.template.md`, `AGENTS.template.md`.
- [ ] Config: `config.example.json` (every field placeholdered) + `voice-profile.md` (blank).
- [ ] Engine: `skills/_shared/` (gauntlet + QC rubric + learning-loop).
- [ ] Channels: `skills/email/`, `skills/linkedin/`, `skills/calls/`, `skills/ops/` — each end-to-end.
- [ ] Onboarding: `skills/onboarding/SKILL.md` (the 11-area interview).
- [ ] Prompts: `onboarding-prompt`, `build-batch-prompt`, `run-my-day-prompt`.
- [ ] Canon: `memory/context/` (voice-profile, qa-rules, gold-standards, writing-canon-index).
- [ ] Data/schema: `data/*.example.csv`, `analytics/db_init.sql`, `sequences/_TEMPLATE-sequence/`.

## Correctness (dogfood it)
- [ ] A test rep clones into a desktop folder, pastes `onboarding-prompt.md`, and the agent runs the full 11-area interview.
- [ ] After onboarding: grep `{{` returns nothing; the only name/email in the repo is the test rep's.
- [ ] Dry run: the agent builds one small batch and the gauntlet visibly runs every gate (scope → dedup → live research → draft → QC table) and STOPS for approval.
- [ ] The QC table appears automatically, unprompted, with the batch.

## The distribution message (what the rep receives)
> Clone this repo into a folder on your desktop. Open your AI agent (Claude Code / Cowork) in that folder and paste `prompts/onboarding-prompt.md`. Answer its interview honestly — it's calibrating the whole system to you, your accounts, and your voice. Then add your accounts to `data/target-accounts.csv` and paste `prompts/build-batch-prompt.md` to run your first batch. Nothing ever sends without your approval.

## Live-run lessons already baked in (from the Jul 9 benchmark)
- [x] Source-width rule (expect 50-70% dedup overlap on worked accounts).
- [x] Sales-Nav depth fallback when a public profile is activity-thin.
- [x] Live-title vs enrichment-title reconciliation as a hard gate.
- [x] Thought-leadership-opener as a per-rep config toggle (canon judgment call).
