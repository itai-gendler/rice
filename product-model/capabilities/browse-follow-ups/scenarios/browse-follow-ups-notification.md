---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: Rice checks due follow-ups at or after 9 am with notifications enabled.
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Follow-up notifications
  contexts:
    desktop:
      place: desktop::follow-ups
  unattended: true
- text: Rice shows one local notice grouping newly due or overdue own follow-ups.
  kind: product
  entities:
  - entity: memory-fact
    effect: reads
    facts:
    - Text
    - Due date
    - Mine
    - Source
  contexts:
    desktop:
      place: desktop::follow-ups
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
- kind: code
  role: implementation
  target: src/renderer/followups.js
---

# Remind about due promises

## Trigger

Rice checks due follow-ups at or after 9 am with notifications enabled.

## Outcome

Rice shows one local notice grouping newly due or overdue own follow-ups.

## Edge cases

- Each item is notified once, including when first noticed overdue after the app opens.
