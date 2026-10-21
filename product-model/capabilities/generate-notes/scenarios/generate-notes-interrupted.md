---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: Rice starts with a completed meeting whose notes generation was interrupted and whose transcript contains
    speech.
  kind: condition
  entities:
  - entity: transcript
    effect: reads
    facts:
    - Content
  - entity: meeting
    effect: reads
    facts: []
  - entity: notes
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice marks the notes Failed and offers Generate notes again.
  kind: product
  entities:
  - entity: notes
    effect: changes
    facts:
    - Progress
    from: Generating
    to: Failed
  contexts:
    desktop:
      place: desktop::meeting
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

# Make interrupted notes retryable

## Trigger

Rice starts with a completed meeting whose notes generation was interrupted and whose transcript contains speech.

## Outcome

Rice marks the notes Failed and offers Generate notes again.
