---
name: ops
description: "Cross-channel operations: dedup checks, MASTER_SENT_LIST logging, analytics DB build + refresh, reply classification/routing, and dashboards. The connective tissue every channel skill calls. Configured from config.json."
---

# Ops — the connective tissue

Shared operational functions every channel skill relies on. Not a sequence; a toolbox.

## Dedup
Given a name/email/company, check in order and return a drop/keep verdict with the reason:
1. `MASTER_SENT_LIST.csv` grep (any prior send, any channel).
2. Active sequence enrollment (via the email tool).
3. Saved/owned contact check.
4. `memory/do-not-contact.md`.
The master list is the source of truth — a send is only "real" once its row exists.

## MASTER logging (the post-send gate)
After every successful send of any type, append one row:
`name,batch,send_date,channel,credits,file,norm`
- `channel` = "Email T1" | "Email T2" | "LinkedIn CR" | "InMail" | "DM" | "Call" | …
- `norm` = lowercased name for dedup grep.
The send is NOT complete until the row exists. If logging fails, stop the batch and alert the rep.

## Do-not-contact
Append to `memory/do-not-contact.md` whenever: a prospect opts out, replies hostile, bounces hard, or is confirmed wrong-persona. Every append needs name, company, reason, date. Dedup checks this every time.

## Analytics DB
Build a local SQLite DB from `analytics/db_init.sql` (build it on a local path, not a cloud-synced folder — file locking breaks on OneDrive/Drive). Load from `MASTER_SENT_LIST.csv` + warm-leads + call-log. Use it for reply-rate by persona/vertical/proof, subject-line performance, and weekly summaries.

## Reply classification + routing
Scan the inbox for new replies, classify by sentiment/type (positive / polite / curious / referral / has-tool / timing / negative), and route: positives → book immediately; curious → answer + bridge; negative/opt-out → log to DNC. Warm ones get a reply drafted through the writing canon.

## Dashboards
Regenerate the HTML performance dashboard on a cadence (weekly) from the DB. Keep it a glance-first view: sends, replies, reply-rate trend, warm-lead pipeline, call activity.
