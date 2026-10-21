---
kind: alternate
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
- text: Rice splits the transcript into overlapping parts and reuses unchanged earlier extracts
  kind: product
  entities:
  - entity: transcript
    effect: reads
    facts:
    - Content
  - entity: notes
    effect: changes
    facts:
    - Progress
    from: Empty
    to: Generating
  - entity: screenshot
    effect: reads
    facts:
    - Caption
    - Time
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice combines the extracts and annotations into notes
  kind: product
  entities:
  - entity: notes
    effect: changes
    facts:
    - Content
    - Progress
    from: Generating
    to: Ready
  - entity: annotations
    effect: reads
    facts:
    - Text
    - Times
  - entity: note-template
    effect: reads
    facts:
    - Sections
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

# Generate a long meeting in parts

## Trigger

The user requests notes for a transcript exceeding the active model’s direct-input budget.

## Outcome

Rice shows part progress and writes one set of notes in the chosen template.

## Edge cases

- The default direct-input threshold is 60,000 characters; local-model budgets can reduce it.
- Parts are about fifteen minutes with roughly one minute of overlap.
