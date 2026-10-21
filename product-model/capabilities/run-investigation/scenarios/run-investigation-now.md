---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user requests investigation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice reads new transcript context and prioritized earlier findings
  kind: product
  entities:
  - entity: transcript
    effect: reads
    facts:
    - Content
    - Partial speech
  - entity: finding
    effect: reads
    facts:
    - Text
    - Source
    - Pinned
  contexts:
    desktop:
      place: desktop::meeting
  actor: user
- text: Rice adds findings and updates the meeting cycle count
  kind: product
  entities:
  - entity: finding
    effect: creates
    facts:
    - Text
    - Time
    - Source
    - Pinned
    to: Visible
  - entity: meeting
    effect: changes
    facts:
    - Investigation count
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

# Investigate new speech

## Trigger

The user chooses Investigate now during a recording.

## Outcome

Rice saves findings with source references and advances the investigation count.

## Edge cases

- A cycle with too little new speech is skipped with a notice.
- Only one cycle runs at a time for a meeting.
- Pinned and recent visible findings supply bounded context.
