---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user browses Follow-ups
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::follow-ups
  actor: user
- text: Rice displays memory facts that are follow-ups with owners, due dates and source links
  kind: product
  entities:
  - entity: memory-fact
    effect: reads
    facts:
    - Text
    - Person
    - Due date
    - Mine
    - Source
    - Completion
  contexts:
    desktop:
      place: desktop::follow-ups
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/memory/service.ts
- kind: code
  role: implementation
  target: src/main/memory/extract.ts
- kind: code
  role: implementation
  target: src/main/memory/ipc.ts
- kind: code
  role: implementation
  target: src/main/memory/followups.ts
- kind: code
  role: implementation
  target: src/renderer/followups.js
---

# Browse follow-ups

## Trigger

The user browses Follow-ups.

## Outcome

Rice displays memory facts that are follow-ups with owners, due dates and source links.

## Edge cases

- This week includes the next seven days, rather than ending on a calendar week boundary.
- The overdue counter counts the user’s own open overdue follow-ups.
