---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user chooses another location for the collection
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::meetings-folder
  actor: user
- text: Rice saves the chosen location as the place it reads and writes the collection
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Meetings folder
  contexts:
    desktop:
      place: desktop::meetings-folder
  actor: user
references:
- kind: code
  role: implementation
  target: src/renderer/renderer.js
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/renderer/settings.js
---

# Change meetings folder

## Trigger

The user chooses Change folder for the meetings folder.

## Outcome

Rice lists and saves meetings in the chosen folder; meetings already in the previous folder stay where they are.
