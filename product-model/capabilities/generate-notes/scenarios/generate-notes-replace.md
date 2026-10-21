---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user asks to regenerate notes
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Template
  - entity: notes
    effect: reads
    facts:
    - Content
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice generates replacement notes
  kind: product
  entities:
  - entity: notes
    effect: changes
    facts:
    - Progress
    from: Ready
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
- text: Rice saves the new notes and archives the replaced text
  kind: product
  entities:
  - entity: notes
    effect: changes
    facts:
    - Content
    - Progress
    from: Generating
    to: Ready
  - entity: notes-version
    effect: creates
    facts:
    - Content
    - Template
    - Date
    - Model
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

# Regenerate existing notes

## Trigger

The user chooses Regenerate after selecting a template.

## Outcome

New notes become current and the replaced text is available in history.

## Edge cases

- Empty or duplicate archived content is not stored twice.
- At most twenty previous versions are retained, newest first.
