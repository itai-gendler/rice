---
appliesTo:
- type: entity
  id: note-template
  effect: removes
references:
- kind: code
  role: implementation
  target: src/main/templates/store.ts
permits:
- actors:
  - user
  when:
  - fact: Built in
    is: false
---

# Only the user removes personal note templates

Shipped templates cannot be deleted. Their customizations can be restored to shipped content.
