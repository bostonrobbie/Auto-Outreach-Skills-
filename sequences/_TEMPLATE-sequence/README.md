# Sequence: {{SEQUENCE_NAME}}

Copy this folder to create a new named outreach motion (e.g. "outbound-primary", "intent-inbound", "conference-followup"). Each sequence is self-contained.

## What this sequence is for
{{One line: the trigger, the audience, and the goal.}}

## Cadence
| Touch | Channel | Day | Formula |
|-------|---------|-----|---------|
| T1 | Email | 0 | 4-paragraph cold standard |
| T2 | Email (reply) | +3 | new angle, shorter |
| T3 | LinkedIn / Email | +7 | new proof |
| … | | | |

## Files
- `sop-prospect.md` — who qualifies, where they come from, the dedup/persona gates.
- `sop-draft.md` — the per-touch formula for this sequence (points at the writing canon).
- `sop-send.md` — the send steps + sender/sequence IDs (from config.json) + the MASTER-log gate.

## Rules
- Everything runs through `skills/_shared/outreach-gauntlet.md` + the QC rubric.
- Rosters and drafts live here but are gitignored (your own data).
