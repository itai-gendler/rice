---
appliesTo:
- type: entity
  id: meeting
- type: entity
  id: transcript
- type: entity
  id: screenshot
references:
- kind: code
  role: implementation
  target: src/main/session/meeting-session.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
---

# Paused recordings capture no new audio

Pause releases the microphone and suspends screenshots, live ideas and investigation. Resuming preserves wall-clock timing and marks the paused stretch in the transcript.
