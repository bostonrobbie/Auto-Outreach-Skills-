---
name: call-outreach
description: "End-to-end cold-call support for one contact or a whole call block: source → dedup → persona + live research → generate per-contact prep cards (opener + hook + proof + objection handles + voicemail) → log dials/connects → post-call follow-up drafted through the full email/LinkedIn gauntlet. Configured from config.json + voice-profile.md."
---

# Call Outreach — the complete channel process

ONE skill owning the call motion end to end: research and prep every prospect in a call block, support the live call, then log and drive the post-call follow-up. The follow-up itself runs through the same gauntlet + QC as email/LinkedIn so quality is identical across channels.

Load first: `skills/_shared/outreach-gauntlet.md`, `memory/context/writing-canon-index.md`, `config.json`.

---

## Phase 1 — Build the call block
- Rep names accounts or a warm-lead segment (e.g. "prospects who opened but didn't reply"). Pull candidates scoped to ICP + target list.
- Dedup against `MASTER_SENT_LIST.csv` for prior call activity and check `memory/do-not-contact.md`.

## Phase 2 — Persona + live research (per contact)
- Read the live profile: role, tenure, recent activity. Web-search the company for one specific fact.
- This is the same mandatory research as the other channels — a call without a real hook is a cold dial that wastes the connect.

## Phase 3 — Generate a prep card per contact
Each card is 3 lines the rep can glance at and dial:
```
{Name} · {Title} · {Company} · {phone}
Hook:  "Hey {Name}, this is {You} from {Company} — {personalized hook from research}."
Pain:  "{Specific problem tied to their context}."
Proof: "We helped {proof point from config.json}. Worth 60 seconds to see if it's relevant?"
Objections: {2-3 likely objections + one-line handles}
Voicemail: {15-second script — different proof than the opener}
```
- Use a DIFFERENT proof and pain hypothesis than any email/InMail touch the contact already got.

## Phase 4 — Live-call support (optional)
- Surface the card on request; capture notes the rep dictates.
- Never auto-dial or take any action visible to others; the rep runs the call.

## Phase 5 — Log activity
- Log dials, connects, positives, voicemails, callbacks for the day (feeds the analytics DB `call_activity` table).
- Calls are a tracked activity metric — log every block.

## Phase 6 — Post-call follow-up (through the full gauntlet)
- A connect that went well gets a same-day follow-up. Draft it through the email or LinkedIn skill's gauntlet + QC — warmer than a cold open, recaps what the prospect said and what was covered, one proof, a soft next-step CTA.
- Send only on approval. Log to `MASTER_SENT_LIST.csv`. Update warm-leads / pipeline.

## Phase 7 — Learn
Run `skills/_shared/learning-loop.md`: which openers connected, which objections recurred, which prep hooks worked.
