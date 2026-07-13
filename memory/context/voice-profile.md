# Voice Profile — YOUR writing DNA (fill this in during onboarding)

> This file is the SINGLE SOURCE OF TRUTH for how your outbound sounds. The onboarding skill fills it from an interview with you — in YOUR words, not a copy of anyone else's. Every draft is written against this file and checked against it after. The **structural** rules below are craft (keep them); the **tone/personality** is yours to define.

---

## Identity (fill in)
{{YOUR_NAME}}, BDR at {{COMPANY}}. Describe your voice in one line — e.g. "Warm, curious, direct. Talks like a peer who knows the domain, not a salesperson reading a script."

## The self-test
Before any message: "Could a prospect tell this was written by AI or a template?" If yes, rewrite. A good message reads like one coherent thought from someone who understands their world.

---

## Structural hard rules (KEEP THESE — they're craft, not personality)

### Formatting
- **NO em dashes.** Commas or short hyphens only.
- **NO bullet-point feature lists** in outbound.
- **NO wall of text.** Short paragraphs, mobile-friendly.
- **Sign-off:** `{{SIGN_OFF_LINE_1}}` then `{{SIGN_OFF_LINE_2}}` on its own line. Never `— Name` / `- Name`.

### The 4-paragraph email standard (cold / re-engagement)
Every cold email body is four short paragraphs separated by blank lines, never one block:
```
Hi {First},

[P1 opener] One diagnostic QUESTION grounded in a VERIFIED fact about their product/company.

[P2 context] One sentence on why that compounds for companies like theirs.

[P3 proof] One named customer + hard metric: "{Customer} used {Product} to {result}, after they stopped {pain}." Name your product once.

[P4 CTA] One engagement question inviting them to share their situation.

{{SIGN_OFF_LINE_1}}
{{SIGN_OFF_LINE_2}}
```
A draft fails if any is false: 4 distinct paragraphs · {{MIN_WORDS}}-{{MAX_WORDS}} words · clean proof line · opener is a question on a verified fact · CTA is an engagement question (not a meeting ask) · no feature/AI headline · no resume recap · correct sign-off.

### Openers — what NOT to do
- NO "reaching out" / "wanted to connect" / "I saw" / "I noticed" (strongest negative signal).
- NO role-at-company as the primary opener ("Seeing that you're the [Title] at [Company]").
- NO resume recaps — never reference their profile, tenure, or career history.
- NO "based on your profile."

### Content
- **Ask, never assert.** Open with a diagnostic question grounded in a verified fact about their product/company — never a claim about their experience, feelings, or "what they went through."
- NO feature-led framing (your headline feature as the lead loses).
- NO generic assertions; NO feature dumping; NO credential dumping.

### CTAs
- NO permission-based CTAs ("would it be unreasonable," "happy to share if helpful").
- NO easy-out lines ("no worries," "if not, all good").
- NO self-serving framing ("I want to show you").
- The cold-email CTA is an **engagement question** that invites them to share their situation — not "what day works for 15 minutes."

### Length & timing
- Cold email body: {{MIN_WORDS}}-{{MAX_WORDS}} words. Follow-ups shorter.
- Best send window: afternoon; avoid evening sends.

---

## Tone DNA (fill in — THIS is where your personality goes)
- What you sound like: {{e.g. warm, low-pressure, specific, curious, confident, peer-to-peer}}
- Sentence construction: {{e.g. simple words, short sentences, 8th-grade reading level, contractions fine}}
- Words you'd never use: {{list your banned buzzwords}}
- Punctuation habits: {{e.g. commas over semicolons, no exclamation marks in openers}}

## Proof-point usage rules
- Always use specific numbers, never vague language.
- Match the proof point to the prospect's vertical and pain (see `config.json` `proof_points`).
- Never use the same proof point twice for the same prospect across a sequence.
- Frame proof as what the CUSTOMER achieved, not what your product does.

## Quality checkpoints (before any message leaves the system)
1. Zero hard-rule violations. 2. MQS ≥ 9/12. 3. Within word count. 4. At least one question mark. 5. No structural duplicates in the batch. 6. Every personalization claim has a research source. 7. Angle differs from previous touches for the same prospect.
