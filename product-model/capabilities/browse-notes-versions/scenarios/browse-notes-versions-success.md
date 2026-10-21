---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user selects a notes version
  kind: actor
  entities:
  - entity: notes
    effect: reads
    facts: []
  - entity: notes-version
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice displays the selected notes version read-only
  kind: product
  entities:
  - entity: notes-version
    effect: reads
    facts:
    - Content
    - Template
    - Date
  - entity: notes
    effect: reads
    facts: []
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
  target: src/main/store/notes-versions.ts
- kind: code
  role: implementation
  target: src/renderer/versions.js
---

# Browse notes versions

## Trigger

The user selects a notes version.

## Outcome

Rice displays the selected notes version read-only.

## Edge cases

- Back to current returns to the current notes.
