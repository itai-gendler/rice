---
appliesTo:
- type: entity
  id: notes
- type: entity
  id: notes-version
references:
- kind: code
  role: implementation
  target: src/main/store/notes-versions.ts
- kind: code
  role: implementation
  target: src/main/session/notes.ts
---

# Replaced notes keep at most twenty prior versions

Successful changed generation archives replaced nonempty text. Empty or immediately repeated archived text is skipped. History is newest first and excess oldest versions are removed. Restoring makes a version current, archives the current text and removes the restored history entry.
