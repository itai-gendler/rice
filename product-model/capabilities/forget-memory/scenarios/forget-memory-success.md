---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user confirms Forget this person or company
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::memory
  actor: user
- text: Rice removes matching memory facts
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
- kind: code
  role: implementation
  target: src/main/memory/store.ts
---

# Forget a person or company

## Trigger

The user confirms Forget this person or company.

## Outcome

Rice removes matching memory facts.
