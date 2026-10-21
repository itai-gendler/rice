---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user requests notes
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Template
  - entity: notes
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice starts notes generation from the transcript, annotations and available attachment text
  kind: product
  entities:
  - entity: notes
    effect: changes
    facts:
    - Progress
    from: Failed
    to: Generating
  - entity: transcript
    effect: reads
    facts:
    - Content
  - entity: annotations
    effect: reads
    facts:
    - Text
    - Times
  - entity: attachment
    effect: reads
    facts:
    - Extracted text
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
  actor: user
- text: Rice saves notes and preserves any unincorporated annotations in Other notes
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

# Retry failed notes

## Trigger

The user chooses Generate notes after an earlier generation failed.

## Outcome

The generated notes are Ready, preserving user jottings.
