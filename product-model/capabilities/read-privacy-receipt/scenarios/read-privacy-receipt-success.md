---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user opens the privacy receipt
  kind: actor
  entities:
  - entity: privacy-receipt
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice displays the privacy receipt summary and activity
  kind: product
  entities:
  - entity: privacy-receipt
    effect: reads
    facts:
    - Summary
    - Activity
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
- kind: code
  role: implementation
  target: src/renderer/receipt-card.js
---

# Read privacy receipt

## Trigger

The user opens the privacy receipt.

## Outcome

Rice displays the privacy receipt summary and activity.
