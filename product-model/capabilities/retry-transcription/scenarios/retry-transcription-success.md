---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Retry transcription from the recording alert
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice retries local transcription and updates the meeting alert
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Recording alerts
  - entity: transcript
    effect: changes
    facts:
    - Partial speech
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
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

## Trigger

The user chooses Retry transcription from the recording alert.

## Outcome

Rice retries local transcription and updates the meeting alert.

## Edge cases

- If the model or transcription binary remains unavailable the failure is shown again.
