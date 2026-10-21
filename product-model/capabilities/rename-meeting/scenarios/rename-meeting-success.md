---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user enters a replacement meeting title
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice saves the normalized meeting title
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Title
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
  target: src/main/store/meeting-files.ts#renameMeeting
---

# Rename meeting

## Trigger

The user enters a replacement meeting title.

## Outcome

Rice saves the normalized meeting title.

## Edge cases

- An empty title is refused.
