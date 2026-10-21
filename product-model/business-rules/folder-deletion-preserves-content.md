---
appliesTo:
- type: entity
  id: folder
  effect: removes
- type: entity
  id: meeting
  effect: changes
  facts:
  - Folder
references:
- kind: code
  role: implementation
  target: src/main/store/folders.ts
- kind: code
  role: implementation
  target: src/renderer/renderer.js
---

# Deleting a folder promotes its children and preserves meetings

Child folders and directly assigned meetings move to the deleted folder’s parent, or the root. Promoted child names are disambiguated with a suffix and their sibling order is retained around the deleted position.
