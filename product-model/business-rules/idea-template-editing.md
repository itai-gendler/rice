---
appliesTo:
- type: entity
  id: idea-template
  effect: changes
references:
- kind: code
  role: implementation
  target: src/main/warroom/idea-templates.ts
permits:
- actors:
  - user
---

# The user edits idea templates

The person using Rice can edit personal templates and save or restore customizations of shipped templates.
