# Onboarding prompt — paste this into your agent, once

> Copy everything in the block below and paste it to your AI agent (Claude Code or Cowork) **with this repo folder open**. It will set the whole kit up for you.

```
I just cloned the BDR Starter Kit into this folder. Set it up for me.

Run the onboarding skill at skills/onboarding/SKILL.md. Go one section at a time and
WAIT for my answers — do not assume or invent anything about me, my company, or my customers.

Interview me for:
- Me: full name, work email, timezone.
- My company + product: name, what it does in one sentence, website, top 3 value props.
- My ICP: the titles I sell to, seniority floor, verticals, titles to exclude, geography.
- My proof points: at least 3 real customer results (customer, the number, the angle).
- My tech stack: CRM, enrichment tool, email/sequencing tool, LinkedIn, my sending address.
- My quota + daily activity targets (emails / LinkedIn / calls).
- My voice: ask me for 2-3 messages I've actually sent that landed, and pull my tone from them.

Then:
1. Write my answers into config.json (copy from config.example.json first).
2. Fill my voice into memory/context/voice-profile.md in MY words, keeping the structural
   rules (no em dashes, one CTA, ask-don't-assert, length caps).
3. Replace every {{placeholder}} across the kit using config.json, and save the
   .template.md files as their real names (CLAUDE.template.md -> CLAUDE.md, etc.).
4. Grep the repo for "{{" and confirm zero results.
5. Confirm config.json is gitignored, and that the only name/email anywhere in the
   repo is mine.
6. Walk me through connecting my tools.

Do NOT import anyone else's contacts, accounts, sent lists, or tool IDs. This kit ships
empty on purpose — I bring my own data. When you're done, tell me how to run my first batch.
```

## After onboarding
- Add your accounts to `data/target-accounts.csv`.
- Paste `prompts/build-batch-prompt.md` to run your first batch.
- Each morning, paste `prompts/run-my-day-prompt.md`.
