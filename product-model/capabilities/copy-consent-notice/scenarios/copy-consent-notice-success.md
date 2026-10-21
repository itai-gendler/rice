---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Copy notice after recording starts
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Language
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice copies the notice and records when it was copied for the meeting
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Consent copied
  - entity: settings
    effect: reads
    facts:
    - Consent reminder
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/privacy/consent.ts
- kind: code
  role: implementation
  target: src/renderer/consent-toast.js
---

# Copy consent notice

## Trigger

The user chooses Copy notice after recording starts.

## Outcome

Rice copies the notice and records when it was copied for the meeting.

## Edge cases

- The notice is nonblocking; copying records a user action, not participant agreement.
