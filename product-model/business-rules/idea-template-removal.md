---
appliesTo:
- type: entity
  id: idea-template
  effect: removes
references:
- kind: code
  role: implementation
  target: src/main/warroom/idea-templates.ts
permits:
- actors:
  - user
  when:
  - fact: Built in
    is: false
---

# Only the user removes personal idea templates

Shipped templates cannot be deleted. Their customizations can be restored to shipped content.
