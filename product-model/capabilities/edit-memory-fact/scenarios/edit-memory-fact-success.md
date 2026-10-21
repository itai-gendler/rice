---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user saves changes to a memory fact
  kind: actor
  entities:
  - entity: memory-fact
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::memory
  actor: user
- text: Rice saves the memory fact and marks it edited
  kind: product
  entities:
  - entity: memory-fact
    effect: changes
    facts:
    - Text
    - Kind
    - Due date
    - Edited
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

# Edit memory fact

## Trigger

The user saves changes to a memory fact.

## Outcome

Rice saves the memory fact and marks it edited.

## Edge cases

- Invalid dates or text shorter than two characters are rejected.
