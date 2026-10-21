---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user turns Tools and MCPs in chat on or off
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::tools
  actor: user
- text: Rice saves whether supported chat may use the configured tools and MCPs
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - Chat tools
  contexts:
    desktop:
      place: desktop::tools
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

# Change tools and MCPs settings

## Trigger

The user changes Tools and MCPs in chat.

## Outcome

Supported chat uses the configured tools and MCPs only while the option is on.
