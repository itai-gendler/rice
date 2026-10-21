---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user cancels the memory build
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop::memory-settings
  actor: user
- text: Rice stops the pass once the current extraction finishes and shows it in Memory settings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Memory progress
  contexts:
    desktop:
      place: desktop::memory-settings
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
---

# Cancel memory build

## Trigger

The user cancels the memory build.

## Outcome

Rice stops the pass once the current extraction finishes and shows it in Memory settings.

## Edge cases

- The in-progress meeting finishes before the pass stops; completed extractions remain.
