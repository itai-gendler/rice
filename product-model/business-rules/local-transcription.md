---
appliesTo:
- type: entity
  id: transcript
- type: entity
  id: meeting
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

# Meeting audio is transcribed locally

Rice records microphone and system audio and sends it to its local transcription service. AI note and chat generation use derived text and eligible images rather than recorded audio.
