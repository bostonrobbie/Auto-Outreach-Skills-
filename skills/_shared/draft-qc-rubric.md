# Draft QC Rubric — the 9/10 quality gate

Every outbound message is scored before a human ever sees it. Only drafts that clear the bar are presented; everything else is reworked or dropped automatically. This is the gate that lets the agent hand the rep a batch that's approvable on the first pass.

## Message Quality Score (MQS) — 12 points, 4 dimensions (1-3 each)

### Opener clarity (1-3)
- **3** = specific, insight-driven question about the prospect's situation. No "reaching out," no role-recap.
- **2** = company-specific reference but a generic frame.
- **1** = opens with "I'm reaching out" or "Seeing that you're the [Title]." Template-visible.

### CTA confidence (1-3)
- **3** = a clear, specific ask tied to the value angle. No easy outs.
- **2** = asks a question but doesn't tie it to the value angle.
- **1** = permission-style, vague, or puts the work on the prospect.

### Personalization density (1-3)
- **3** = references something only THIS person would recognize (a project, a launch, a career move, a company event).
- **2** = references their company specifically, but the opener could apply to anyone in that role.
- **1** = only swaps name/title/company. Indistinguishable from a template.

### Friction (1-3, inverted — 3 = low friction)
- **3** = under ~100 words, one proof point, one CTA, no bullet lists, clean.
- **2** = 100-120 words, still readable.
- **1** = over 120 words, bullet-point features, multiple CTAs, wall of text.

### Thresholds
- **10-12** = ready to send
- **9** = acceptable, present it
- **< 9** = must be reworked or dropped (never presented)

## The self-audit checks (run on every batch, automatically)
Beyond the numeric score, each draft must pass:
1. **Zero hard-rule violations** (see `voice-profile.md`): no em dashes, correct sign-off, length in range, one CTA, no feature-led headline, no resume recap / "I noticed".
2. **Opener ≠ CTA** — the two questions ask different things.
3. **Opener-shape variety** — across the batch, no two drafts share an opener frame.
4. **Context-line variety** — no reused middle-line construction.
5. **Scaffolding-honesty** — the opener + context are genuinely recipient-specific and traceable to research evidence, not just a company name in a template.
6. **Evidence trace** — every personalization claim maps to a real research source (live profile / web fact).
7. **The "could-anyone-tell" test** — if two drafts could swap company names and still read fine, they fail.

## Presentation artifact (mandatory)
Every batch is presented with a QC table:

| # | Name | MQS | Opener frame | Weakness / clean |
|---|------|-----|--------------|------------------|
| 1 | … | 10/12 | grow-faster-than-cover | clean |
| 2 | … | 9/12 | keep-pace-as-ship | proof line slightly generic |

The rep spot-checks the table instead of having to ask "how good are these?" — the audit already ran.
