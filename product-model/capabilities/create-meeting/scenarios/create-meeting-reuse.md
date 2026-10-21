---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user asks for a new meeting
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::home
  actor: user
- text: Rice reuses the empty meeting and refreshes its date and folder
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Date
    - Folder
    from: Draft
    to: Draft
  - entity: folder
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
  target: src/main/store/drafts.ts
---

# Reuse an empty draft

## Trigger

The user chooses New meeting while an unused empty draft exists.

## Outcome

Rice opens the most recent empty draft with a refreshed date and requested folder.

## Edge cases

- A renamed draft, a calendar-linked draft or a draft with user content is retained and is not treated as empty.
