---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: A never-recorded draft with only its default title and no entered content has been left.
  kind: condition
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  unattended: true
- text: Rice moves the unused draft to Trash.
  kind: product
  entities:
  - entity: meeting
    effect: removes
    from: Draft
  contexts:
    desktop:
      place: desktop::meeting
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/app/delete-meeting.ts
- kind: code
  role: implementation
  target: src/main/store/drafts.ts
- kind: code
  role: implementation
  target: src/main/privacy/retention.ts
---

# Discard an empty draft

## Trigger

A never-recorded draft with only its default title and no entered content has been left.

## Outcome

Rice moves the unused draft to Trash.
