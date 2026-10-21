---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user completes a follow-up
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::follow-ups
  actor: user
- text: Rice marks the memory fact Done and checks its matching notes task
  kind: product
  entities:
  - entity: memory-fact
    effect: changes
    facts:
    - Completion
    from: Open
    to: Done
  - entity: notes
    effect: changes
    facts:
    - Content
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
---

# Complete follow-up

## Trigger

The user completes a follow-up.

## Outcome

Rice marks the memory fact Done and checks its matching notes task.

## Edge cases

- No matching notes task leaves the notes unchanged.
- Completing a matching task directly in notes also updates the follow-up.
