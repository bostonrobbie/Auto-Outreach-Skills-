# QA Rules and Scoring Reference

The scoring gate every outbound message passes before presentation. Full detail lives in `skills/_shared/draft-qc-rubric.md`; this is the canon-side reference.

## Message Quality Score (MQS) — 12-point system
Every message scores on 4 dimensions (1-3 each), max 12:
- **Opener clarity** — 3 = specific insight-driven question; 1 = "I'm reaching out" / role-recap.
- **CTA confidence** — 3 = specific ask tied to value; 1 = permission-style/vague.
- **Personalization density** — 3 = something only this person would recognize; 1 = name/title/company swap only.
- **Friction (inverted)** — 3 = under ~100 words, one proof, one CTA, clean; 1 = wall of text, bullets, multiple CTAs.

**Thresholds:** 10-12 ready · 9 acceptable · <9 must be reworked.

## QA gate (mandatory before batch presentation)
1. Rule-violation scan against every hard constraint. Any violation = auto-rewrite.
2. Compute MQS for every message; show the breakdown.
3. Only ≥9/12 may be presented.
4. Structural dedup — no two messages in a batch may be structurally identical.
5. Evidence check — every personalization claim has a research source.
6. Angle rotation — no prospect gets the same angle in more than one touch.

## Prospect prioritization (reply-likelihood, not theoretical ICP fit)
- **Boost:** titled leaders in your ICP; companies where personalization-3 is achievable; companies in active transformation/scaling; intent signals.
- **Penalize:** only surface-level personalization possible; roles with no relevant scope; anything needing >120 words to explain relevance.

## Proof-point rotation
Never use the same proof point twice for the same prospect across a sequence. Match the proof angle (maintenance / velocity / scale / productivity) to the prospect's vertical and pain. Proof points live in `config.json`.

## Observed reply patterns (tune to your own data over time)
| Type | Action |
|------|--------|
| Polite ("thanks") | Follow up with value, not a commitment ask. |
| Positive ("interested") | Book the meeting immediately. Don't over-explain. |
| Negative ("not interested") | Log the objection. Maybe re-engage 60+ days later. |
| Curiosity ("tell me more") | Answer directly, then bridge to a meeting. |
| Referral ("talk to [name]") | Reach out to the referred person immediately. |
| Has tool ("we use X") | Handle the objection: ask about gaps. |
| Timing ("not right now") | Set a reminder; re-engage on a trigger. |
