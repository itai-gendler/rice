---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user reopens a follow-up
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::follow-ups
  actor: user
- text: Rice reopens the memory fact and unchecks a matching notes task
  kind: product
  entities:
  - entity: memory-fact
    effect: changes
    facts:
    - Completion
    from: Done
    to: Open
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

# Reopen follow-up

## Trigger

The user reopens a follow-up.

## Outcome

Rice reopens the memory fact and unchecks a matching notes task.

## Edge cases

- Unchecking a task in notes does not undo a completion attributed to a later meeting; use Reopen on the follow-up.
