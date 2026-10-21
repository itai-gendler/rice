---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses a folder for the meeting
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
- text: Rice saves the meeting folder assignment
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Folder
  - entity: folder
    effect: reads
    facts:
    - Name
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

# Move meeting to folder

## Trigger

The user chooses a folder for the meeting.

## Outcome

Rice saves the meeting folder assignment.
