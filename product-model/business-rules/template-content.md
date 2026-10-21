---
appliesTo:
- type: entity
  id: note-template
references:
- kind: code
  role: implementation
  target: src/main/templates/schema.ts
---

# Note templates contain one to twelve named sections

A note template has a nonempty title of at most eighty characters, a description of at most five hundred characters and one to twelve ordered sections. Section titles are nonempty and at most eighty characters; their descriptions of what Rice should write are at most five hundred.
