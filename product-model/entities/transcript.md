---
references:
- kind: code
  role: implementation
  target: src/main/store/meeting-files.ts
- kind: code
  role: implementation
  target: src/main/session/meeting-session.ts
---

# Transcript

The locally transcribed speech of one meeting.

## Information kept

- **Content** — Finalized speech with times and Me, Others or identified participant labels.
- **Partial speech** — Live provisional speech that can change before becoming final.
- **Gaps** — Pause, sleep, missing-audio and incomplete-transcription markers.
