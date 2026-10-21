---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses no folder for the meeting
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  - entity: folder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::library
  actor: user
- text: Rice clears the meeting folder assignment
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Folder
  - entity: folder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::library
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/store/folders.ts
- kind: code
  role: implementation
  target: src/renderer/renderer.js
---

# Remove meeting from folder

## Trigger

The user chooses no folder for the meeting.

## Outcome

Rice clears the meeting folder assignment.
