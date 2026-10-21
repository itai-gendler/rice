---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: New notes explicitly establish that an earlier open follow-up was completed.
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Memory enabled
  - entity: notes
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::memory
  unattended: true
- text: Rice marks that memory fact Done and records the completing meeting.
  kind: product
  entities:
  - entity: memory-fact
    effect: changes
    facts:
    - Completion
    from: Open
    to: Done
  - entity: notes
    effect: reads
    facts:
    - Content
  - entity: meeting
    effect: reads
    facts:
    - Title
    - Date
  contexts:
    desktop:
      place: desktop::memory
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
---

# Resolve an earlier promise from a later meeting

## Trigger

New notes explicitly establish that an earlier open follow-up was completed.

## Outcome

Rice marks that memory fact Done and records the completing meeting.
