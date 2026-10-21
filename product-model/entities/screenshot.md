---
references:
- kind: code
  role: implementation
  target: src/main/screenshots/capture.ts
- kind: code
  role: implementation
  target: src/shared/screenshots.ts
---

# Screenshot

A captured image linked to a point in the meeting conversation.

## Information kept

- **Image** — The locally stored picture.
- **Time** — Capture time and offset.
- **Caption** — The explanation associated with the capture.
- **Trigger** — The speech that prompted capture, or a manual capture indication.
- **Transcript position** — The speech passage next to which it is shown.
