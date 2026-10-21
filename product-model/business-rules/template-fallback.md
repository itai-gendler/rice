---
appliesTo:
- type: entity
  id: note-template
- type: entity
  id: idea-template
references:
- kind: code
  role: implementation
  target: src/main/templates/store.ts
- kind: code
  role: implementation
  target: src/main/warroom/idea-templates.ts
---

# Missing selected templates resolve to the shipped default

A deleted or unreadable selected note template resolves to the default built-in note template. An unavailable idea template resolves to General. Invalid custom files produce warnings instead of removing the usable built-in content.
