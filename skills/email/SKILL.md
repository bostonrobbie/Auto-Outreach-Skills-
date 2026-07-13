---
name: email-outreach
description: "End-to-end email outreach for one contact or a whole batch: source → dedup → persona + live research → company anchor → draft to the 4-paragraph standard → QC gauntlet to 9/10 → present for approval → send → log. Batch quality equals single-message quality. Runs every gate every time, automatically. Configured from config.json + voice-profile.md."
---

# Email Outreach — the complete channel process

This is ONE skill that owns the entire email motion end to end. It does not hand off to five smaller skills — research, drafting, QA, and sending are all built in, and none of them may be skipped or done lazily, even in a large batch. A batch of 50 is 50 individually-researched messages, not one template mail-merged.

Load first: `skills/_shared/outreach-gauntlet.md`, `skills/_shared/draft-qc-rubric.md`, `memory/context/writing-canon-index.md`, `config.json`.

---

## Phase 0 — Session preflight (MANDATORY, before anything else)
Run `skills/_shared/session-preflight.md`: load and state the approved account universe + ownership rule (scope), the ICP want/don't-want (persona), and today's number (quota — from the rep's explicit ask, else `config.quota` daily targets, minus what's already sent today). Compute how many to oversource to net the target given dedup overlap. Announce the plan, then run continuously to the number. Do not source until this is stated.

## Phase 1 — Intake & source
- The rep names a set of accounts (or says "pull from my target list").
- Pull contacts scoped to `config.json` ICP + `data/target-accounts.csv`. Apply the persona filter (seniority floor + included titles, minus excluded patterns) up front.
- **Source wide.** Expect heavy dedup overlap on any account you've worked before (routinely 50-70%). Source at least `config.research.source_width_multiplier`× the target count, and prefer less-worked accounts, so a batch of 10 doesn't collapse to 3 after dedup.
- Output a candidate list. Do NOT enrich or draft yet.

## Phase 2 — Gauntlet A/B: scope, ownership, dedup (per contact)
Run gates 1-7 of the gauntlet for every candidate:
- Account on the target list; assigned to the rep; not another rep's.
- Not in `MASTER_SENT_LIST.csv`; not already enrolled; not a saved/prior contact; not on `memory/do-not-contact.md`.
- Drop or route-to-follow-up anyone who fails. Log why.

> **Ordering rule (throughput):** Phase 2 (free screens: persona filter + dedup + DNC) runs on the WHOLE oversourced list FIRST. Only Phase-2 survivors reach Phase 3 enrichment + live research. Never enrich or research before screening — that's what wasted effort on contacts that later drop.

## Phase 3 — Gauntlet C: persona + live research (MANDATORY, per survivor only)
For every survivor:
- Read the **live** profile (LinkedIn or primary): headline, About, experience, connection degree, recent activity. Catch stale enrichment, wrong-persona, title inflation. Reconcile the live title against the enrichment title (they diverge — trust the live one).
- **Depth fallback (mandatory):** if the public profile is activity-thin (no About, no recent posts), pull the **Sales Nav lead page** for About + Experience before settling. Company-level-only personalization (MQS personalization = 2) is the signal you skipped this. Only accept a tenure/company-level anchor when Sales Nav depth genuinely comes up empty too — and say so.
- Web-search the company for ONE specific, verified, ideally quantified fact for the opener anchor.
- Write a short evidence note per contact (the fact + its source) into the batch's evidence file under `batches/active/<batch>/` (gitignored — it contains real names). This is what the draft anchors to. No evidence → no draft (drop or flag).
- **Never skip this because the batch is large.** If research is thin for someone, say so honestly and drop them rather than fabricating.

## Phase 4 — Draft to the 4-paragraph standard (load the canon first)
Load `voice-profile.md` + `gold-standards.md` + `qa-rules.md` BEFORE writing. For each contact:
```
Hi {First},

[P1] One diagnostic question grounded in the verified fact. Ask, don't assert. No role-recap.

[P2] One line on why that compounds for companies like theirs.

[P3] {Customer} used {Product} to {quantified result}, after they stopped {pain}. (one named proof, rotated per contact, matched to vertical — from config.json proof_points)

[P4] One engagement question inviting them to share their situation. Not a meeting ask.

{{SIGN_OFF_LINE_1}}
{{SIGN_OFF_LINE_2}}
```
Subject: a specific pain angle at {Company}, no em dash.
**Across the batch:** vary the opener SHAPE, the P2 construction, and the CTA so no two drafts share a frame.

## Phase 5 — QC gauntlet (automatic, every batch)
Run `draft-qc-rubric.md` on every draft: MQS ≥9/12, zero hard-rule violations, opener≠CTA, opener-shape variety, context variety, scaffolding-honesty, evidence trace, could-anyone-tell test. **Rework anything below bar before the rep sees it.**

## Phase 6 — Present for approval
Show the batch with the mandatory QC table (`# · Name · MQS · opener-frame · weakness-or-clean`) plus each full draft. WAIT for the rep's explicit "send." Nothing sends before that.

## Phase 7 — Send (on approval)
- Create/verify the contact (verified email only). Enroll in the correct sequence/sender per `config.json` if the flow requires it.
- Send via the rep's email tool. **Pre-send readback:** confirm recipient, sender address, subject, and body (paragraph breaks intact) before firing. Verify success.
- **Log a row to `MASTER_SENT_LIST.csv` per send** (`name,batch,send_date,channel,credits,file,norm`). The send is not done until the row exists.
- Update the batch tracker.

## Phase 8 — Follow-ups (T2/T3)
- Follow-ups are sent as REPLIES on the original thread, not new cold emails.
- Shorter, a NEW angle/proof, not a rehash (40-70 words). Same gauntlet, same QC.
- Never send a follow-up to anyone who replied, bounced, or opted out — re-check dedup + DNC first.

## Phase 9 — Learn
Run `skills/_shared/learning-loop.md`: log low-scoring patterns, what landed, evidence gaps, any new rules the rep gave.
