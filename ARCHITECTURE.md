# Architecture — how the BDR Starter Kit works

This kit turns a blank folder into a working, agent-driven BDR system that a new rep can clone, configure to themselves, and run in batches at a 9/10 quality bar — on their own voice and tech stack, without ever touching anyone else's data.

Three ideas hold it together:

1. **One config drives everything.** `config.json` (name, company, product, ICP, proof points, tech stack, voice, quota) is the single source of truth. Every template reads from it. Fill it once; the whole kit configures itself.
2. **The agent does the work; the human approves the send.** Research, enrichment, drafting, quality gauntlet, and self-scoring all run autonomously. Nothing is shown to the rep until it clears 9/10. The rep's only job is "send / don't send."
3. **Nothing personal ships.** The repo is a skeleton. Contacts, sent history, DNC names, account lists, tool IDs, webhooks, and secrets are all gitignored or never committed. A rep brings their own.

---

## Repo layout (flow-for-agents)

```
bdr-starter-kit/
├── README.md                 # front door: what this is, who it's for, quick start
├── SETUP.md                  # human step-by-step
├── ARCHITECTURE.md           # this file — the mental model
├── config.example.json       # THE config (copy → config.json, fill placeholders)
├── .gitignore                # PII safety net (config + data files never commit)
│
├── CLAUDE.template.md        # the brain — agent reads it every session
├── AGENTS.template.md        # session-start protocol (what to load, in order)
│
├── prompts/                  # copy-paste prompts a rep hands their agent
│   ├── onboarding-prompt.md      # "set this kit up for me" (run once)
│   ├── build-batch-prompt.md     # "build me a batch of N" (the daily driver)
│   └── run-my-day-prompt.md      # morning: replies, follow-ups, batch, calls
│
├── skills/                   # the agent's capabilities, categorized by channel
│   ├── onboarding/               # interviews the rep, fills config, sets voice
│   ├── _shared/                  # cross-channel engine
│   │   ├── outreach-gauntlet.md      # the full gate sequence (scope→…→log)
│   │   ├── draft-qc-rubric.md        # the 9/10 scoring gate
│   │   └── learning-loop.md          # self-improve after each batch
│   ├── email/                    # email-channel skills (build batch, T2, send, verify)
│   ├── linkedin/                 # LinkedIn skills (connection batch, InMail, DM)
│   ├── calls/                    # call prep, live cues, post-call follow-up
│   └── ops/                      # dedup, master-logging, analytics, dashboards
│
├── memory/                   # the methodology (genericized, no personal data)
│   ├── context/                  # the writing canon
│   │   ├── voice-profile.md          # BLANK — rep's own voice goes here
│   │   ├── qa-rules.md               # the MQS 12-point rubric
│   │   ├── gold-standards.md         # structure of a great message (no rep copy)
│   │   └── writing-canon-index.md    # load-order entry point
│   ├── sops/                     # per-channel SOPs (email, linkedin, calls)
│   └── playbooks/                # dedup, follow-up cadence, warm-lead handling
│
├── sequences/
│   └── _TEMPLATE-sequence/       # blank sequence scaffold (readme+prospect+draft+send)
│
├── data/
│   └── target-accounts.example.csv   # header only — rep adds their accounts
│
├── analytics/
│   └── db_init.sql               # schema only — no rows
│
└── batches/
    └── active/.gitkeep           # where working batches land (gitignored)
```

**Categorization is by channel** (email / linkedin / calls) with a shared engine underneath, exactly as asked. Each channel folder is self-contained: its SOP, its templates, its skills — all of them calling the same `_shared/` gauntlet and QC rubric so quality is identical across channels.

---

## The autonomous batch engine (the flow every channel runs)

A rep says *"build me an email batch for these 15 accounts."* The agent runs this without further prompting:

```
  INTAKE      Rep names a channel + a set of accounts (or "pull from my target list").
    │
  SOURCE      Pull contacts scoped to config ICP + target-accounts.csv. Persona filter.
    │
  ┌─ GAUNTLET (per contact, fully autonomous) ───────────────────────────┐
  │  1 Scope + ownership   account in list, assigned to rep, right sender │
  │  2 Dedup               not in MASTER, not enrolled, not on DNC        │
  │  3 Persona + live      read live profile, catch stale/wrong-persona   │
  │  4 Anchor              one specific verified company fact             │
  │  5 Load canon          voice-profile + qa-rules BEFORE drafting       │
  │  6 Draft               rep's voice, one proof, distinct opener + CTA  │
  │  7 Self-QC             score vs 9/10 rubric; auto-remediate if below  │
  └──────────────────────────────────────────────────────────────────────┘
    │            (loop until every draft in the batch is ≥ 9/10)
  PRESENT     One table: contact, hook, draft, QC score, evidence trace.
    │         ONLY ≥9/10 drafts shown. Agent WAITS. Nothing sends yet.
    │
  ── APPROVAL ──  Rep reviews, says "send" (or edits, or drops).
    │
  SEND        Execute via rep's tool. Correct sender. Per-send readback verify.
    │
  LOG         Append a row to MASTER_SENT_LIST per send. Not done till logged.
    │
  LEARN       Update the learning loop: what scored low, what to reuse.
```

The key promises this delivers on:
- **Batches, not one-at-a-time.** The gauntlet runs across the whole set in parallel; the rep gets one review, one approval.
- **9/10 before a human sees it.** The self-QC gate remediates or drops weak drafts automatically. The rep never wastes time editing sub-standard work.
- **Adapts to the rep.** Every step reads `config.json` + `voice-profile.md`, so the same engine produces *their* ICP, *their* proof points, *their* voice.
- **Safe by construction.** Approval gate before send; DNC + dedup before draft; MASTER log after send.

---

## How a new rep gets from zero to running

1. Clone the repo into a folder on their desktop.
2. Open their agent in the folder and paste `prompts/onboarding-prompt.md`.
3. The onboarding skill interviews them → fills `config.json` → elicits their voice → replaces every `{{placeholder}}` → helps connect their tools.
4. They add their target accounts to `data/target-accounts.csv`.
5. They paste `prompts/build-batch-prompt.md` and start running batches.

From there the daily loop is: run-my-day → review the batch → approve → the agent sends and logs.

---

## The PII firewall (what never leaves the owner)

| Never committed | How it's blocked |
|---|---|
| Filled-in config (`config.json`) | gitignored |
| Contacts / sent history / warm leads / call log / pipeline | gitignored; templates ship empty |
| DNC names | gitignored; ships empty |
| Target account list | gitignored; only an example header ships |
| Tool IDs, sequence/campaign IDs, webhooks, API keys | live in `config.json` / `.env` only, both gitignored |
| Owner's voice + personal phrasing | `voice-profile.md` ships blank |

Before any push, a PII scan greps the whole tree for names, emails, phone numbers, and known tool-ID patterns. Zero hits is the gate.
