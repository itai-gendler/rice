---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user opens What to remember for a calendar-linked meeting
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice presents relevant memory facts and source links
  kind: product
  entities:
  - entity: memory-fact
    effect: reads
    facts:
    - Text
    - Person
    - Company
    - Due date
    - Source
    - Completion
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
  target: src/main/memory/recall.ts
- kind: code
  role: implementation
  target: src/renderer/memory.js
---

# Read What to remember

## Trigger

The user opens What to remember for a calendar-linked meeting.

## Outcome

Rice presents relevant memory facts and source links.

## Edge cases

- No relevant facts means no brief card.
- Home can show the first point for an event starting within fifteen minutes.
- If AI briefing fails, locally selected facts remain a fallback.
