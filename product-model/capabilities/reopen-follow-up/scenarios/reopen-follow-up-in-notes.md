---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user unchecks a notes task
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
- text: Rice saves notes and reopens the matching memory fact
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
    from: Done
    to: Open
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

# Reopen a manually completed task from notes

## Trigger

The user unchecks a task whose matching follow-up was completed manually.

## Outcome

Rice saves the unchecked task and reopens the matching follow-up.
