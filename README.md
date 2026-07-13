# BDR Agent Starter Kit

A clone-and-configure framework for running an AI-assisted BDR motion (email + LinkedIn + calls) end-to-end. This is the **skeleton** of a working system — the processes, the safety gates, the skills, and the file structure — with **none of the original owner's data, identity, credentials, or voice**. You fill it in to fit you.

> **What this is NOT:** a plug-and-play bot. It's a framework + an onboarding flow. You (and your agent) configure it to your company, your ICP, your tech stack, and your voice, then run it.

---

## What's inside

| Folder | What it is |
|--------|-----------|
| `CLAUDE.template.md` | The "brain" — operating rules the agent reads every session. Templated with `{{PLACEHOLDERS}}` you fill during setup. |
| `AGENTS.template.md` | Session startup protocol (read-first order, handoff rules). |
| `config.example.json` | The single config file that drives everything — your name, company, ICP, proof points, tech stack, voice, quota. Copy to `config.json` and fill it in. |
| `SETUP.md` | The onboarding guide. Start here after cloning. |
| `skills/onboarding/` | An **onboarding skill** — point your agent at it and it interviews you, then fills every placeholder across the kit to configure it to *you*. |
| `memory/` | The methodology: SOPs, playbooks, the outreach-send pipeline/gauntlet, the writing-canon framework, and a **blank voice profile** you define. Plus empty templates for your working memory (warm leads, call log, pipeline). |
| `skills/` | Reusable process skills (prospect, draft, QA, send, reply-handling, analytics, etc.) as templates — hardcoded tool IDs swapped for config values. |
| `data/` | Empty data templates (sent-list header only, account-list header only). |
| `analytics/` | Database schema only (`db_init.sql`) — no data. |
| `sequences/` | A blank `_TEMPLATE-sequence/` you copy per outreach motion. |

## What is deliberately NOT inside

No contacts, no sent history, no warm leads, no call logs, no do-not-contact names, no target-account lists, no CRM/enrichment tool IDs or credentials, no personal email, no owner-specific voice locks. You bring your own.

---

## Quick start

1. **Clone** this repo into your work folder.
2. `cp config.example.json config.json` and open `config.json`.
3. **Run onboarding:** open your agent in this folder and say *"run the onboarding skill"* (or follow `SETUP.md` by hand). The agent will interview you and fill in your company, ICP, proof points, tech stack, and voice across the kit.
4. **Connect your tools** (CRM, enrichment, email, LinkedIn) per `SETUP.md` → "Tech stack."
5. **Define your voice** in `memory/context/voice-profile.md` (the setup flow walks you through it).
6. Start a session and run your first batch. The safety gates (dedup, persona, scope, QA, per-send verification, logging) are already wired — they just read *your* config.

---

## Core principles baked in (keep these)

- **Every message runs the full gate every time** (scope → dedup → persona → research → draft-to-standard → QA → send → log). See `skills/_shared/outreach-gauntlet.md`.
- **Nothing sends without your explicit approval.**
- **Never leak or reuse another rep's data** — this kit ships empty on purpose.
- **Your voice, not a template's.** The writing framework is here; the *tone* is yours to define.

---

*Built from a working BDR system, stripped to the skeleton. Configure it, make it yours, and good hunting.*
