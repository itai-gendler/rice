---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Export PDF for the privacy receipt
  kind: actor
  entities:
  - entity: privacy-receipt
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice writes the privacy receipt PDF
  kind: product
  entities:
  - entity: privacy-receipt
    effect: reads
    facts:
    - Summary
    - Consent
    - Microphone
  - entity: meeting
    effect: reads
    facts:
    - Title
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
  target: src/main/privacy/receipt-html.ts
---

# Export privacy receipt

## Trigger

The user chooses Export PDF for the privacy receipt.

## Outcome

Rice writes the privacy receipt PDF.

## Edge cases

- Existing export files are preserved with a suffixed filename.
