---
appliesTo:
- type: entity
  id: memory-fact
- type: entity
  id: notes
references:
- kind: code
  role: implementation
  target: src/main/memory/followups.ts
- kind: code
  role: implementation
  target: src/main/memory/service.ts
---

# Manual completion synchronizes matching notes tasks

Follow-up completion and reopening update a sufficiently matching source-notes checkbox. Changes to notes update matching follow-ups. Unchecking source notes does not undo a completion attributed to a later meeting.
