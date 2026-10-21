---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: A recording finishes with finalized speech.
  kind: condition
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice generates notes using the current meeting template.
  kind: product
  entities:
  - entity: notes
    effect: changes
    facts:
    - Content
    - Progress
    from: Empty
    to: Ready
  - entity: meeting
    effect: reads
    facts:
    - Template
  - entity: transcript
    effect: reads
    facts:
    - Content
  - entity: annotations
    effect: reads
    facts:
    - Text
    - Times
  - entity: note-template
    effect: reads
    facts:
    - Sections
  - entity: screenshot
    effect: reads
    facts:
    - Caption
    - Time
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

# Generate after recording ends

## Trigger

A recording finishes with finalized speech.

## Outcome

Rice generates notes using the current meeting template.

## Edge cases

- Continuing a previously recorded meeting regenerates from the accumulated transcript and preserves replaced notes as a version.
