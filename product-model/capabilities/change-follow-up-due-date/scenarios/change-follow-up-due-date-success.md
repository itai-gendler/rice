---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses a follow-up date or clears it
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::follow-ups
  actor: user
- text: Rice saves the memory fact due date
  kind: product
  entities:
  - entity: memory-fact
    effect: changes
    facts:
    - Due date
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

# Change follow-up due date

## Trigger

The user chooses a follow-up date or clears it.

## Outcome

Rice saves the memory fact due date.

## Edge cases

- An invalid nonempty date is refused.
