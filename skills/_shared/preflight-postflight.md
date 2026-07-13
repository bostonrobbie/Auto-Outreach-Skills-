# Pre-Send & Post-Send Checks — the flight-check discipline

Two gates bracket every send, like a pilot's pre-flight instrument check and the ground crew's post-landing inspection. Neither is optional. The compliance auditor (`compliance-auditor.md`) runs first (is the *content* right?); these two gates verify the *mechanics* are safe before and after the send.

---

## ✈️ PRE-SEND FLIGHT CHECK (run immediately before each send; all must be green)
Nothing takes off until every instrument reads green. If any item is red, the send is held for that contact.

1. **Approval** — the rep gave explicit APPROVE SEND for this batch.
2. **Compliance auditor PASS** — this draft cleared the independent audit (channel-fit, touch-fit, formula, traceability, distinctiveness, persona).
3. **Dedup (re-run at send time)** — not in MASTER_SENT_LIST, not in an active sequence, no thread already open. (State can change between sourcing and send.)
4. **Do-not-contact** — not on the DNC list.
5. **Employer still current** — for anything anchored on a company fact, the recipient still works there (re-confirm if hours/days passed).
6. **Verified email** — sending to a verified address only; bounce-risk domains excluded.
7. **Correct sender** — the From address matches the rep's locked sender for this motion.
8. **Content readback** — recipient, subject, and body match the approved draft character-for-character. No placeholder text anywhere.
8a. **Composition/whitespace check** — the email body in the composer shows the real 4 paragraphs with blank lines between them (not a collapsed single block); the sign-off is on its own lines. A CR is the single short block it should be. Verify the literal whitespace, not just the words — collapsed paragraph breaks are a silent, common failure.
9. **Right channel + right touch** — sending the email as an email / the CR as a CR; a follow-up goes as a reply on the existing thread, not a new cold message.

Only when 1-9 are green does the send fire.

## 🛬 POST-SEND MAINTENANCE CHECK (run right after each send; catches anything that changed at the last second)
The ground crew inspects the plane after it lands. After the send:

1. **Send confirmed** — the tool reported success (e.g. a 200 / message-sent state), and the composer/thread closed cleanly.
2. **Landed as intended** — verify in the Sent folder / thread that what actually went out matches the approved draft (right recipient, subject, body, sender). Catches last-second mutations, encoding breaks, collapsed paragraph breaks, autocomplete swaps.
3. **MASTER logged** — a row was appended to MASTER_SENT_LIST for this send. The send is NOT complete until the row exists.
4. **Trackers updated** — sequence roster / pipeline / warm-lead state reflects the send.
5. **Anomaly sweep** — any immediate bounce, auto-reply, or error is captured and, if it's a hard bounce or opt-out, the contact goes straight onto the DNC list.
6. **Incident check** — if anything went wrong (wrong recipient, placeholder, double-send), log it in `memory/incidents.md` with root cause + the preventive gate, and feed it to `learning-loop.md`.

## Why both exist
Pre-flight stops a bad send from ever leaving the ground. Post-flight proves the send that left actually arrived as intended and is recorded — because "I clicked send" is not the same as "the right message went to the right person and is logged." Together they make the outcome **reliable and auditable**, every time, for any rep on any model.
