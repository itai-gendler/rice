---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses Send to Reminders
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::follow-ups
  actor: user
- text: Rice creates system reminders from the selected memory facts
  kind: product
  entities:
  - entity: memory-fact
    effect: reads
    facts:
    - Text
    - Due date
    - Mine
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

# Send follow-ups to Reminders

## Trigger

The user chooses Send to Reminders.

## Outcome

Rice creates system reminders from the selected memory facts.

## Edge cases

- The action reports success or failure and the number sent.
