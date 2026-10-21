---
kind: edge
routes:
  desktop: Rice desktop
steps:
- text: The user requests an email draft
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice reports why a draft could not be produced
  kind: product
  entities:
  - entity: notes
    effect: reads
    facts:
    - Content
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/share/actions.ts
- kind: code
  role: implementation
  target: src/renderer/share.js
- kind: code
  role: implementation
  target: src/main/share/mailto.ts
---

# Email drafting fails

## Trigger

The user asks for a follow-up draft but notes are absent or the AI fails.

## Outcome

Rice shows the failure and leaves meeting content unchanged.
