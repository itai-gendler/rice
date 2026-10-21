---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user deletes a memory fact
  kind: actor
  entities:
  - entity: memory-fact
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::memory
  actor: user
- text: Rice removes the selected memory fact
  kind: product
  entities:
  - entity: memory-fact
    effect: removes
    from: Open
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
---

# Delete memory fact

## Trigger

The user deletes a memory fact.

## Outcome

Rice removes the selected memory fact.
