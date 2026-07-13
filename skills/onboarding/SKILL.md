---
name: onboarding
description: "Configure this BDR Starter Kit for a new rep. Run once, right after cloning. Interview the rep across 11 areas, fill config.json + voice-profile.md, replace every {{PLACEHOLDER}}, connect their stack, and verify no one else's data remains. Every question below exists because getting it wrong caused a real problem in a production BDR system."
---

# Onboarding — set this kit up for THIS rep

You are turning a blank BDR framework into *their* working system, in *their* voice, on *their* stack — importing none of anyone else's data. Go one area at a time. **Ask, confirm, then write.** Do not assume or invent company facts, personas, or proof points.

## Golden rules
- **Interview, don't assume.** Wait for real answers.
- **One config, many files.** Fill `config.json` first, then propagate its values into the `{{PLACEHOLDERS}}`.
- **Never paste in another rep's data.** Any real name/email/account/tool-ID that isn't this rep's is a leak — flag and remove.
- **Their voice, not the template's.** You elicit theirs; you don't copy anyone's.

---

## Step 0 — Discovery & machine setup (auto-detect FIRST, then one consolidated ask)
"Know before you go." Before interviewing, **auto-detect everything detectable**, then fold the gaps into the interview so the rep answers once. Establish:

- **Work folder on the machine.** Where does this system live / run? (A working directory on the rep's Desktop, e.g. `Desktop\Work`, holding `MASTER_SENT_LIST`, `memory/`, `skills/`, `batches/`.) If none exists, propose creating it — **ask before creating** (persistent change). Record the confirmed path.
- **Assigned WORK GitHub repo (Testsigma work account — NOT personal).** A work BDR's repo is under their **work** GitHub account and assigned to them by the company; they will NOT have a personal repo like a power-user might. Establish: (1) their work GitHub account, (2) the specific assigned repo URL, (3) confirm it's the Testsigma/work repo. Clone into the work folder / set `origin`; confirm the tracked branch. **Never push to a personal repo — only the assigned work repo.** If no repo is assigned yet, flag it: the rep/admin must assign one before git-backed work.
- **Tool/connection inventory.** Detect what's connected vs missing: work Chrome profile (via the browser extension), Apollo (web login + MCP), work Gmail (reply monitoring), Calendar/Drive, and **SF/G2 via the rep's WORK claude.ai "Work" browser tab group** (the only sanctioned path to SF/G2 — never sign in from a personal browser). List present-vs-absent MCP tools. Tell the rep exactly what to connect.

**The flow:** auto-detect → **one upfront consolidated ask** (multiple-choice/checklist — "here's what I found, here's what I still need, here's what you must do") → get approval for anything persistent → configure → **report done/pending/blocked** → persist the resolved config so later sessions don't re-ask. Then proceed to the interview.

## Step 1 — Interview (fill `config.json`)
Copy `config.example.json` → `config.json` first. Then work these 11 areas in order. Keep it conversational; batch related questions.

### 1. You & logistics
- Full name, work email, timezone.
- **Is there a personal email/account the agent must NEVER use for work?** (Prevents sending from the wrong identity.)
- **Which browser profile is your "work" profile?** The agent must never drive a personal profile for work tasks.

### 2. Company & product
- Company name, product name, one-sentence description, website.
- Top 3 value props (the problems you solve, in customers' words).
- Any product terms/glossary the agent must know so it never mis-describes the product.
- A few marquee customers it can name.

### 3. ICP & persona lock (be precise — this is the #1 quality lever)
- The exact titles you sell to, and your **seniority floor** (e.g. "Manager and above").
- **The title-TEXT rules:** which words must appear (Manager/Director/VP/Head/Chief) and which patterns to exclude *even if the enrichment tool says otherwise* (e.g. "Lead", "Senior <IC>", "Staff", "Principal IC"). Enrichment tools mis-classify seniority constantly; the title text wins.
- **Wrong-persona traps to exclude** (e.g. clinical/lab QA, hardware/mechanical, defense/systems, compliance/audit QA when you sell software QA).
- Verticals and geography.

### 4. Scope & ownership
- Where is your target-account list? (Goes in `data/target-accounts.csv`.)
- **Are accounts shared across a team of reps?** If yes, how does the agent confirm an account/contact is YOURS before touching it? (Prevents stepping on a teammate.)
- Any intent signals / tags that route a contact to a specific sequence?

### 5. Proof points (this is what makes outreach land — get real ones with real numbers)
- At least 3: customer, the **exact quantified result**, the angle (coverage / maintenance / velocity / scale / productivity / multi-platform), and which verticals it fits. Never vague ("significant improvement") — always a number.

### 6. Voice calibration (fills `voice-profile.md`)
- **Paste 2-3 messages you've actually sent that landed well** (or dictate how you'd naturally open a cold intro). Extract sentence length, formality, rhythm.
- Your **exact sign-off** (e.g. "Best," then your first name). Confirm what's banned ("— Name", "Cheers,", etc.).
- Em-dash rule, word-count range (cold vs follow-up), words you'd never use.
- **CTA style by motion:** cold outbound (engagement question vs meeting ask?), inbound (engagement-first, no meeting ask), warm follow-up (soft next step). These differ and using the wrong one tanks replies.
- **May the agent open by referencing a prospect's PUBLISHED content** (a post/blog/talk they authored)? This is distinct from creepy profile-mining and is a real judgment call — get the rep's ruling. Default false.

### 7. Tech stack & tool permissions
- CRM, enrichment tool, email/sequencing tool, LinkedIn (Sales Nav or basic?), calendar.
- **Sending address(es)** — and any rule where different motions send from different addresses.
- Sequence/campaign IDs (these go in gitignored `config.json` only — never a shared file).
- **Survey the rep's existing sequences (do this, don't just ask for IDs).** In the sequencing tool's web UI, list the rep's own sequences and read each one's **step structure** — which email steps are a **manual task** (creates a task, safe to enroll, we send tailored content) vs an **automated/scheduled template** (auto-fires on enroll — know its exact template first, or you double-send). This defines the routing menu; contacts get routed to a sequence (manual-task preferred) over one-offs. Note any LinkedIn steps.
- **Reply monitoring for the sending address.** If outreach sends from an address whose inbox the agent doesn't natively watch, confirm replies are still captured — usually the sequencing tool (e.g. Apollo) syncs replies on any connected mailbox natively, so read replies there; a mailbox→primary forward is an optional convenience, not required.
- **Which tools may the agent take ACTIONS in, and which is it read-only on?** (e.g. read replies but never post in a team chat.)

### 8. Guardrails & approvals
- **Approval model:** does the agent get one approval per send, or one per batch then execute? (Batch is the efficient default.)
- Confirm the hard nevers: never send without approval, never touch another rep's data, never take an action visible to coworkers, verified-email-only, follow-ups sent as replies on-thread, and **log every send to `MASTER_SENT_LIST.csv`** (a send isn't done until it's logged).
- Where the do-not-contact list lives.

### 9. Research standard (prevents the two most common failures: fabrication + laziness)
- Confirm: **live-profile read per contact is mandatory**; enrichment data is necessary but not sufficient.
- When a public profile is activity-thin, **pull the Sales Nav lead page for depth** before settling for company-level personalization.
- **Never fabricate a claim; never delegate a live profile capture to a subagent** (they hallucinate URLs/titles/activity).
- Expect heavy dedup overlap on worked accounts — **source 3-4× the target** so a batch of 10 doesn't collapse to 3.

### 10. Cadence & quota
- Monthly target (e.g. qualified opportunities) and daily activity targets (emails / LinkedIn / calls).
- Best send window / timezone; anything to avoid (e.g. no evening sends).
- Follow-up cadence.

### 11. Where everything lives
- Confirm the rep knows the map (README + this table). The agent reads `CLAUDE.md` + the gauntlet + `config.json` at the start of every session.

Read `config.json` back to the rep for confirmation before moving on.

## Step 2 — Fill their voice (`memory/context/voice-profile.md`)
Use their pasted examples to fill the Tone DNA + identity in *their* words. Keep the structural hard rules (no em dashes, one CTA, ask-don't-assert, length caps) — those are craft; the personality is theirs.

## Step 3 — Propagate placeholders
Replace every `{{...}}` across the kit from `config.json`:
- `CLAUDE.template.md` → `CLAUDE.md`; `AGENTS.template.md` → `AGENTS.md`.
- SOPs/playbooks in `memory/`, skill templates in `skills/` (fill tool names; point ID fields at `config.json`).
- Grep for `{{` again — zero hits = fully configured.

## Step 4 — Seed the empties
Copy each `*.example.*` to its live (gitignored) name: `MASTER_SENT_LIST`, `data/target-accounts.csv`, `data/suppression-list.csv`, `memory/do-not-contact.md`, `warm-leads.md`, `call-log.md`, `pipeline-state.md`. They stay the rep's own and never get pushed.

## Step 5 — Connect tools
Walk the rep through connecting their CRM / enrichment / email / LinkedIn / calendar. If their stack differs from the skill's examples, update the skill's tool references. Mark any missing tool's steps as manual.

## Step 6 — Verify
- Grep the repo for `{{` → empty.
- Grep for the new rep's name/email only — no one else's appears anywhere.
- `config.json` is gitignored and unstaged.
- **Dry run:** have the rep ask for a single small batch and confirm the gauntlet reads *their* ICP, proof points, sender, and voice — and stops for approval before any send.

Done: the skeleton is now their system. Hand off to `AGENTS.md`.
