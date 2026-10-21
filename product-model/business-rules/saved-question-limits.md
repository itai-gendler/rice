---
appliesTo:
- type: entity
  id: saved-question
references:
- kind: code
  role: implementation
  target: src/shared/saved-prompts.ts
---

# Personal saved questions are unique and limited to eight

Questions are trimmed to one line and at most three hundred characters, deduplicated ignoring case, with at most eight retained personal entries.
