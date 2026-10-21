---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user confirms Erase memory
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::memory-settings
  actor: user
- text: Rice removes memory facts and clears extraction bookkeeping
  kind: product
  entities:
  - entity: memory-fact
    effect: removes
    from: Open
  contexts:
    desktop:
      place: desktop::memory-settings
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
  target: src/renderer/memory.js
---

# Erase memory

## Trigger

The user confirms Erase memory.

## Outcome

Rice removes memory facts and clears extraction bookkeeping.

## Edge cases

- Meeting notes and recordings remain.
