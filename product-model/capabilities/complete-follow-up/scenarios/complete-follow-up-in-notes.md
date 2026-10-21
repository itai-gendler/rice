---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user checks a task in notes
  kind: actor
  entities:
  - entity: notes
    effect: reads
    facts:
    - Content
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice saves notes and completes a matching memory fact
  kind: product
  entities:
  - entity: notes
    effect: changes
    facts:
    - Content
  - entity: memory-fact
    effect: changes
    facts:
    - Completion
    from: Open
    to: Done
  contexts:
    desktop:
      place: desktop::meeting
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

# Complete a task from notes

## Trigger

The user checks a task in the current notes.

## Outcome

Rice saves the task state and completes matching follow-ups.

## Edge cases

- A task without a corresponding remembered follow-up still remains checked in notes.
