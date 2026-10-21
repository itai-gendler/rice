---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user browses a person or company in Memory
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::memory
  actor: user
- text: Rice displays memory facts and their source meetings
  kind: product
  entities:
  - entity: memory-fact
    effect: reads
    facts:
    - Text
    - Kind
    - Person
    - Company
    - Topic
    - Due date
    - Source
    - Completion
    - Mine
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::memory
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
  target: src/renderer/memory-page.js
---

# Browse memory

## Trigger

The user browses a person or company in Memory.

## Outcome

Rice displays memory facts and their source meetings.
