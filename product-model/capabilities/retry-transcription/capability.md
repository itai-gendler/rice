---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: src/main/session/meeting-session.ts
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/session/asr-service.ts
---

# Retry transcription

Restart the local transcription service after a failure while preserving the recording.
