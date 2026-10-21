---
kind: primary
routes:
  desktop: Rice desktop
steps:
- text: The user picks the app language or the default spoken language
  kind: actor
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop::language
  actor: user
- text: Rice saves the language choices; the app language applies at once and the spoken language applies to later recordings
  kind: product
  entities:
  - entity: settings
    effect: changes
    facts:
    - App language
    - Default meeting language
  contexts:
    desktop:
      place: desktop::language
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

# Change language settings

## Trigger

The user changes App language or Meetings language in Language settings.

## Outcome

Rice shows its texts in the chosen app language, and later recordings default to the chosen meeting language.
