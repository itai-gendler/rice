---
references:
- kind: code
  role: implementation
  target: src/main/store/folders.ts
- kind: code
  role: implementation
  target: src/main/privacy/folder-rules.ts
domain: folders
---

# Folder

An organizational label in the meetings hierarchy.

## Information kept

- **Name** — A name unique among siblings, ignoring case.
- **Parent** — The optional containing folder.
- **Order** — Position among siblings.
- **Sensitive** — Whether this folder requests personal-data hiding, inherited by descendants.
- **Audio retention** — Own audio retention choice or inheritance.
- **Meeting retention** — Own whole-meeting retention choice or inheritance.
