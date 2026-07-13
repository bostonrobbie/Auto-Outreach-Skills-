# Build-a-batch prompt — the daily driver

> Paste this to your agent to run a full batch end to end. Swap in your channel and accounts.

```
Build me a {email | linkedin | call} batch of {N} for these accounts: {list, or "pull from my target list, tier HIGH"}.

Run the full process end to end without stopping for me until the drafts are ready:
- Source contacts scoped to my ICP in config.json + data/target-accounts.csv.
- Dedup against MASTER_SENT_LIST.csv, active sequences, and memory/do-not-contact.md.
- For every survivor, do the mandatory research: read their LIVE profile and web-search
  their company for one specific verified fact. Do not skip this because it's a batch.
  If research is thin for someone, tell me and drop them — don't fabricate.
- Load my writing canon (voice-profile.md + gold-standards.md + qa-rules.md) BEFORE drafting.
- Draft each to the channel formula, varying opener shape / context / CTA across the batch.
- Run the QC gauntlet automatically. Rework anything under 9/12 before showing me.

Then present the batch with the QC table (# · name · MQS · opener-frame · weakness/clean)
plus each full draft, and WAIT. Send nothing until I say "send."
```
