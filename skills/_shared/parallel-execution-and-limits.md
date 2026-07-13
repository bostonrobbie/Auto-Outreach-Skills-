# Parallel Execution, Model-Awareness & Graceful Limits

How to run the outreach gauntlet fast and at volume WITHOUT sacrificing the no-fabrication standard — and how to behave when the agent (or its model) can't do everything. Written to give a reliable, dependable result every time, for a rep who may not know the tool deeply and may be running on a smaller model.

---

## A. Parallel-agent mode (for volume days)
Live research is one browser capture per person and is the throughput bottleneck. You can parallelize it with subagents — but only under the four mitigations below, which are what keep parallel agents from fabricating (the classic failure mode).

**The four mitigations (all required):**
1. **Hand each agent a VERIFIED identity** (name, title, company, LinkedIn URL, email) from your enrichment/dedup step. The agent must never be the source of *who the person is* — that's what it hallucinates.
2. **Each agent opens its OWN browser tab** for its live read (no collision on one authenticated browser).
3. **Instruct every agent: "an honest FAILED beats an invented success. Do not fabricate any field."**
4. **Main-context verification pass after** (Section C) — the orchestrator, not the subagents, certifies the batch.

**Proven envelope:** ~8-10 concurrent agents complete reliably in ~1 minute wall-clock, each doing a genuine live read + web anchor + draft + self-QC. Scale a batch to your model/host's comfort; if unsure, start at 6-8.

**What each agent returns (structured):** name · linkedin_status (OK/FAILED) · linkedin_evidence (degree + verbatim headline + activity quotes or "none") · company_fact + source_url · subject · draft · MQS · honest_notes (what it could NOT complete).

## B. What the orchestrator does (main context only)
Sourcing, enrichment, dedup, DNC, and TAM-scope checks stay in main context — never delegate them (subagents fabricate IDs/classifications). Subagents ONLY do: live read + web anchor + draft + self-QC on an already-cleared, identified prospect.

## C. Verification protocol (mandatory before any batch is presented)
Treat all subagent output as unverified until the orchestrator certifies it:
1. **Deep-check 2-3 of N**: re-capture the profile in main context and compare headline, followers, degree, and any quoted activity **verbatim**. Any mismatch → widen the check.
2. **Headline-consistency on all N**: every returned headline must match the enrichment source. Flag divergences.
3. **Drop any draft whose evidence can't be verified or whose agent reported FAILED.**
4. Only verified, ≥9/12 drafts reach the rep, with the QC table.

## D. The "open to work" / stale-employer DROP gate (added after a live catch)
Enrichment tools lag reality. If the live read shows an **"Open to work" badge, a recent departure/layoff post, or any signal the person may have left the company**, the draft is anchored on the wrong employer → **DROP it**. Do not send. (Real example that triggered this rule: a "Director @ [Company]" per the tool had posted that he'd left after a PE-acquisition layoff; the company-anchored draft would have been an embarrassing wrong send. The agent flagged it; verification confirmed; dropped.) The company web-anchor is only valid if the person still works there.

## E. Model-awareness & graceful degradation (read this if you're not on the biggest model)
This kit is designed to run on different models (e.g. a smaller/faster model than the one it was authored on). **Capability varies; the standard does not.** If the agent cannot hold enough context, can't run enough parallel work, or hits any wall:
- **Do LESS, not WORSE.** Produce fewer fully-researched drafts rather than many shallow or guessed ones. Five real 9/12 drafts beat fifty fabricated ones.
- **Never fabricate to fill a gap.** No invented titles, activity, company facts, or evidence. If a fact isn't verified, leave it out or drop the contact.
- **Never claim a step ran if it didn't.** If you couldn't do the live read, say "LinkedIn: FAILED" and either retry or drop — don't paper over it.
- **Stop cleanly when you can't continue.** State exactly what you completed, what you didn't, and why. A smaller model might run 3-wide instead of 10-wide, or serial instead of parallel — that's fine; report the honest number.
- **Shrink the batch, not the gauntlet.** Every draft that ships still passed every gate. Lower the *quantity* target under pressure; never lower the *quality* bar or skip a step silently.
- **When in doubt, surface it to the rep** rather than guessing. Ask, or hand back what you have with a clear note.

## F. Reliability contract (what the rep can depend on, every run)
1. Nothing is sourced outside the rep's approved accounts / ownership.
2. Every draft traces to verified evidence — no fabrication, ever.
3. Every draft shown cleared ≥9/12 and the full gauntlet; the QC table proves it.
4. The agent reports the true number done and the true number remaining — never inflates.
5. Nothing sends without the rep's explicit approval.
