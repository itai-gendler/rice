---
appliesTo:
- type: entity
  id: folder
references:
- kind: code
  role: implementation
  target: src/main/store/folders.ts
- kind: code
  role: implementation
  target: src/renderer/renderer.js
---

# Folders have at most four levels and unique sibling names

Names are nonempty, at most sixty characters after whitespace normalization and unique among siblings ignoring case. Moving a subtree cannot create a cycle or exceed four levels. Reordering names exactly the complete sibling set.
