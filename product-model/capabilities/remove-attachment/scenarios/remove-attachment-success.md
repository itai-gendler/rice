---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user removes an attachment
  kind: actor
  entities:
  - entity: attachment
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice removes the attachment and its extracted text
  kind: product
  entities:
  - entity: attachment
    effect: removes
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
  target: src/main/attachments/store.ts
---

# Remove attachment

## Trigger

The user removes an attachment.

## Outcome

Rice removes the attachment and its extracted text.
