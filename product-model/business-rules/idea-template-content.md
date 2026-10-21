---
appliesTo:
- type: entity
  id: idea-template
references:
- kind: code
  role: implementation
  target: src/main/warroom/idea-templates.ts
---

# Idea templates contain an instruction and at most six categories

Titles are nonempty and at most eighty characters, descriptions at most two hundred, instructions nonempty and at most twelve hundred. Optional categories are unique ignoring case and each at most twenty-four characters.
