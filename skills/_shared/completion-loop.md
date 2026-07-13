# The Completion Loop — finish the number, every time

When the rep gives a quantity ("50 emails", "10 connections"), that number is a **standing obligation**, not a suggestion. The agent keeps working — sourcing more people, running more batches, saving progress — until the tally reaches the target OR a genuine hard limit is hit. Stopping early at a "clean checkpoint" is a defect.

## The rule
1. **Set the target and a saved tally.** At Phase 0, record `target` and `done = 0` in a progress ledger file (e.g. `batches/active/<run>/ledger.md`). Update `done` after every verified batch.
2. **Loop until `done >= target`.** After each batch: save the drafts, update the ledger, and — if `done < target` — immediately source the next set and run the next batch. Do NOT stop to ask "should I continue?" — the quantity already answered that.
3. **Source fresh each loop.** Running low on one account is not running out of people. Move to the next approved account (TAM → Factor → G2, or the rep's list), a different vertical, or the next page of results. The approved pool is large; exhausting a single batch's candidates is normal and is NOT a reason to stop.
4. **Save progress continuously** so nothing is lost if a turn ends. Each batch is written to disk as it completes; the ledger always reflects the true count.
5. **Only these are valid reasons to stop before target:**
   - The approved account universe is genuinely exhausted of uncontacted, in-persona people (prove it: state how many accounts/pages were swept).
   - Credits/quota for a required paid step are out.
   - A tool is failing and retries don't recover.
   - The turn's capacity is genuinely reached — in which case **save the tally and continue next turn**, don't abandon.
6. **When a real limit stops you, report precisely:** "Done N of target. Remaining M. Reason. Here's exactly where to resume." Never fabricate to close the gap; never silently quit.

## Use approved-route intuition to keep moving
The rep pre-approved the routes: their target accounts, their ICP, verified contacts, the standard formula. Within those, **use judgment to keep the loop fed** — pick the next sensible account, rotate verticals to avoid clustering, go deeper in an org's Manager+ layer. You don't need to re-ask for permission to source the next batch from an already-approved account.

## Nothing sends, so completeness is safe
Because every draft waits for the rep's approval, **finishing the full quantity is always safe** — there is no downside to producing all N. If a few drafts are weak or you were uncertain (thin profile, running low on context, an odd data signal), **keep them but FLAG them** in the presentation ("you should look at these — I'd hold them") rather than stopping the loop. The rep decides at approval; your job is to complete the number and surface the caveats.

## Anti-patterns (do not do these)
- Stopping at 58% because a report looked tidy.
- Reading "don't force it" as "OK to stop early." It means "don't fabricate/send junk," never "quit before the number."
- Treating context pressure as a reason to abandon rather than to save-and-continue.
- Asking "want me to keep going?" when the rep already gave a quantity.
