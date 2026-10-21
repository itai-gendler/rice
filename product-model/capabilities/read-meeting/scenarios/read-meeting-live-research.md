---
kind: alternate
routes:
  desktop: Rice desktop
steps:
- text: The user opens the meeting research area
  kind: actor
  entities:
  - entity: meeting
    effect: reads
    facts:
    - Mode
    - Ideas settings
    - Investigation settings
    - Extra cycles
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice displays suggestions and findings
  kind: product
  entities:
  - entity: idea
    effect: reads
    facts:
    - Text
    - Time
    - Category
    - Template
  - entity: finding
    effect: reads
    facts:
    - Text
    - Time
    - Source
    - Pinned
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
---

# Read ideas and findings

## Trigger

The user opens Ideas or Investigation for the meeting.

## Outcome

Rice presents the meeting’s live settings, suggestions and findings.
