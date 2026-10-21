---
appliesTo:
- type: entity
  id: notes
- type: entity
  id: notes-version
references:
- kind: code
  role: implementation
  target: src/main/search/index.ts
- kind: code
  role: implementation
  target: src/main/search/retrieve.ts
- kind: code
  role: implementation
  target: src/main/share/actions.ts
- kind: code
  role: implementation
  target: src/renderer/versions.js
---

# Search, cross-meeting chat and exports read current notes

Reading a historical version does not change the text used by search, all-meetings retrieval, copying or PDF export. Restore changes which text is current.
