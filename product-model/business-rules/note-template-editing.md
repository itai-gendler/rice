---
appliesTo:
- type: entity
  id: note-template
  effect: changes
references:
- kind: code
  role: implementation
  target: src/main/templates/store.ts
permits:
- actors:
  - user
---

# The user edits note templates

The person using Rice can edit personal templates and save or restore customizations of shipped templates.
