---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Copy for the privacy receipt
  kind: actor
  entities:
  - entity: privacy-receipt
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice copies the privacy receipt
  kind: product
  entities:
  - entity: privacy-receipt
    effect: reads
    facts:
    - Summary
    - Consent
    - Microphone
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
  target: src/main/privacy/egress.ts
---

# Copy privacy receipt

## Trigger

The user chooses Copy for the privacy receipt.

## Outcome

Rice copies the privacy receipt.
