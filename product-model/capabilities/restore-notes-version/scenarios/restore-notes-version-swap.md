---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user restores the selected notes version
  kind: actor
  entities:
  - entity: notes-version
    effect: reads
    facts:
    - Content
    - Template
    - Date
    as: selected
  - entity: notes
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice archives the current notes as another version
  kind: product
  entities:
  - entity: notes
    effect: reads
    facts:
    - Content
  - entity: notes-version
    effect: creates
    facts:
    - Content
    - Template
    - Date
    - Model
    as: replaced
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice restores the selected notes version and removes its history entry
  kind: product
  entities:
  - entity: notes
    effect: changes
    facts:
    - Content
  - entity: meeting
    effect: changes
    facts:
    - Template
  - entity: notes-version
    effect: removes
    as: selected
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
  target: src/main/store/notes-versions.ts#restoreVersion
---

# Restore and exchange versions

## Trigger

The user chooses Restore this one while reading a historical version.

## Outcome

The chosen text is current, its template is selected and the replaced text is in history.

## Edge cases

- Legacy versions without a known original template leave the current template choice unchanged.
