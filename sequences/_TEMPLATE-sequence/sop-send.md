# {{SEQUENCE_NAME}} — send SOP

- **Sender / sequence IDs:** pull from `config.json` `tech_stack` (never hardcode real IDs in a shared file).
- **Send:** only after explicit approval. Pre-send readback (recipient, sender, subject, body/breaks). Verify success.
- **Log:** append a row to `MASTER_SENT_LIST.csv` per send — the send is not done until the row exists.
- **Track:** update the sequence roster + `memory/pipeline-state.md`.
