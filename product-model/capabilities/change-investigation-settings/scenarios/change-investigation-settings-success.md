---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user changes investigation settings
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice saves the meeting mode, investigation settings and extra cycle allowance
  kind: product
  entities:
  - entity: meeting
    effect: changes
    facts:
    - Mode
    - Investigation active
    - Investigation settings
    - Extra cycles
    - Cycle ceiling
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
references:
- kind: code
  role: implementation
  target: src/main/warroom/ipc.ts
- kind: code
  role: implementation
  target: src/main/warroom/engine.ts
- kind: code
  role: implementation
  target: src/renderer/warroom.js
---

# Change investigation settings

## Trigger

The user changes investigation settings.

## Outcome

Rice saves the meeting mode, investigation settings and extra cycle allowance.

## Edge cases

- Intervals are 2, 5, 10 or 15 minutes, independently of ideas.
- Continue more adds thirty cycles to the meeting allowance.
- Claude subscription supports web, MCPs and a work folder; ChatGPT subscription supports web and MCPs.
- Turning investigation off preserves sources and findings.
