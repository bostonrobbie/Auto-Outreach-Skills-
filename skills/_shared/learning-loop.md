# Learning Loop — how the system improves itself

Run this at the end of every batch and every session. The goal: the agent gets better at *your* motion over time, and hard-won lessons become permanent rules instead of things you have to re-explain.

## After every batch
1. **What scored low and why.** Log the drafts that needed rework and the specific weakness (opener=CTA collision, generic proof, shape collision). Feed the pattern back into the QC audit so it's caught earlier next time.
2. **What landed.** Note openers/angles/proof pairings that the rep approved without edits — reuse the *shape*, not the words.
3. **Evidence gaps.** If a live-research step came up thin for an account, note it so sourcing improves.

## After every session
1. **New rules.** If the rep corrected something ("never phrase it that way", "always check X first"), write it as a durable rule in `CLAUDE.md` or the relevant SOP — not just a one-off fix. A correction you have to give twice is a rule that should have been written down once.
2. **Incidents.** If a send went wrong (wrong recipient, placeholder text, bounce, wrong sender), log it in `memory/incidents.md` with root cause and the preventive gate so it never repeats.
3. **Metrics.** Update the analytics DB / dashboards so reply-rate and quality trends stay current.

## The principle
Every mistake becomes a gate. Every re-explanation becomes a written rule. Every strong result becomes a reusable pattern. The rep should never have to teach the system the same thing twice.
