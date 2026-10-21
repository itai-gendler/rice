---
kind: edge
routes:
  desktop: Rice desktop
steps:
- text: The user requests notes
  kind: actor
  entities:
  - entity: notes
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice reports failed notes generation
  kind: product
  entities:
  - entity: notes
    effect: changes
    facts:
    - Progress
    from: Empty
    to: Failed
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/session/notes.ts
- kind: code
  role: implementation
  target: src/main/session/long-notes.ts
- kind: code
  role: implementation
  target: src/renderer/renderer.js
---

# AI cannot generate notes

## Trigger

The user requests notes but the selected AI cannot complete generation.

## Outcome

Rice shows the error and leaves notes available for retry.

## Edge cases

- Transient network, timeout or empty-response failures receive one automatic retry.
- Authentication and usage-limit failures require user action.
- Failed replacement generation keeps the previous notes available.
