---
name: linkedin-outreach
description: "End-to-end LinkedIn outreach for one contact or a whole batch: source → dedup → persona + live-title lock → degree check → draft to the locked formula → QC gauntlet → present for approval → char-for-char readback send → log. Covers connection requests, InMail, and DMs. Runs every gate every time. Configured from config.json + voice-profile.md."
---

# LinkedIn Outreach — the complete channel process

ONE skill owning the entire LinkedIn motion end to end (connection requests, InMail, DMs). Research, drafting, QA, and sending are all built in; none may be skipped, even in a large batch.

Load first: `skills/_shared/outreach-gauntlet.md`, `skills/_shared/draft-qc-rubric.md`, `memory/context/writing-canon-index.md`, `config.json`.

---

## Phase 0 — Session preflight (MANDATORY, before anything else)
Run `skills/_shared/session-preflight.md`: state the approved account universe + ownership rule, the ICP want/don't-want, and today's LinkedIn number (from the rep's ask, else `config.quota.daily_activity_targets.linkedin_requests`, minus what's already sent today). Oversource for degree-drops + dedup. Announce the plan, then run to the number.

## Phase 1 — Intake & source
Rep names accounts (or "pull from my target list"). Pull candidates scoped to ICP + target list; apply the persona filter. **Source wide** (≥ `config.research.source_width_multiplier`×) and prefer less-worked accounts — dedup overlap on worked accounts routinely runs 50-70%.

## Phase 2 — Dedup (per contact)
Gates 4-7: not in `MASTER_SENT_LIST.csv`, not already enrolled/messaged, not on `memory/do-not-contact.md`. Drop matches.

## Phase 3 — Persona + LIVE-TITLE LOCK (MANDATORY, main context, per contact)
- Capture the person's **live public profile** (≤24h before send): current-role title verbatim, tenure, connection degree, recent activity.
- The draft's hook must quote the **live** title verbatim (or a documented faithful derivation) — enrichment/cached data is NOT an acceptable source for the live-title field. Persist the capture to an evidence file per contact under `batches/active/<batch>/evidence-linkedin.md` (gitignored — evidence contains real names and never gets committed).
- **Reconcile live title vs enrichment title** — they diverge (e.g. enrichment "VP of Engineering" vs live "VP, Platform Engineering"); the live one is source of truth and must be what the hook quotes.
- **Wrong-persona / left-company / title-inflation checks** apply here — drop anyone who fails.
- **Never delegate this capture to a subagent** and never fabricate profile facts. If a capture fails, retry, then drop the candidate rather than guessing.

## Phase 4 — Degree check → route
- **1st-degree** → route to a DM (don't spend a connection request / InMail credit on an existing connection).
- **2nd / 3rd-degree** → connection request or InMail.

## Phase 5 — Draft to the locked formula (load the canon first)
Connection request / InMail body (short form, one template, variable swaps):
```
Hi {First}, I'm at {Company}, {one-line product frame}, and I connect with {dept} leaders to share what we're building. {One verified signal line from the live profile / company fact}. Happy to connect if that sounds worthwhile. {{YOUR_FIRST_NAME}}
```
- {dept} matched to their title tier. {signal} = the substantive anchor from the live evidence.
- ~200-300 characters, NO em dashes, NO question marks, no product name-drops beyond the one frame.
- InMail adds a subject = the signal clause, truncated to ~60 chars.
- **Vary the signal line across the batch** so no two are structurally identical.

## Phase 6 — QC gauntlet (automatic)
Run `draft-qc-rubric.md` adapted for short-form: hook traces to the live capture, character range, zero em dashes/question marks, no two drafts structurally identical, could-anyone-tell test. Rework below-bar before presenting.

## Phase 7 — Present for approval
Batch table: `# · Name · live-title (captured) · degree · hook · clean/weakness` + each full message. WAIT for explicit approval.

## Phase 8 — Send (on approval) — char-for-char readback
The ONLY text that enters the invite/message box is the EXACT approved message from the tracker. Never compose, rewrite, or "improve" at send time. Never read the profile again to regenerate personalization mid-send.

**⛔ JS-only connection-request sending is UNSAFE (field-proven).** LinkedIn's invite modal ignores synthetic JS clicks (React portal), the "Add a note" box is a **closed shadow DOM** (invisible to querySelector/form_input), and generic selectors match the sidebar "people you may know" Connect buttons — a **wrong-recipient** failure (a live run grabbed the sidebar's "Invite <someone else>" on the target's page). The safe procedure:
- **Enter via the Sales Nav lead page** (no suggestion sidebar → wrong-recipient risk structurally eliminated). Use the **free Connect action** — never "Message" from Sales Nav (that's a paid InMail).
- Drive the note with a **real-mouse-click flow**: screenshot → coordinate-click the TOP-CARD Connect → click the note placeholder to focus → type via the computer/keyboard tool → readback → Send.
- **Test-and-lock the flow on 1-2 contacts** before running any batch through it.

1. Extract the exact approved text from the tracker (programmatic read).
2. Enter the note via the real-mouse flow above.
3. Read back the box content.
4. Compare character-for-character against the tracker source.
5. Only click Send if they match exactly. On mismatch: clear, re-extract, re-inject.
6. For connection requests: check for an existing "Pending" state first and skip if present.
- **Log a row to `MASTER_SENT_LIST.csv` per send.** Update the tracker.

## Phase 9 — Accept/reply sweep + learn
- Sweep for accepted requests and replies; route warm ones to the reply workflow.
- Run `skills/_shared/learning-loop.md`.
