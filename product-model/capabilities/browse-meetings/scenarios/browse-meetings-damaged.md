---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: Rice reads a meeting whose saved details are unreadable.
  kind: condition
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::library
  unattended: true
- text: Rice presents the meeting as Needs repair using its folder name and date.
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Title
    - Date
    from: Done
    to: Needs repair
  - entity: folder
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::library
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/search/index.ts
- kind: code
  role: implementation
  target: src/main/search/handler.ts
---

# Show a meeting needing repair

## Trigger

Rice reads a meeting whose saved details are unreadable.

## Outcome

Rice presents the meeting as Needs repair using its folder name and date.
