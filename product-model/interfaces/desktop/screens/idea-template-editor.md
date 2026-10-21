---
entities:
- entity: idea-template
  shows:
  - Title
  - Description
  - Instruction
  - Categories
  - Built in
  - Customized
  collects:
  - Title
  - Description
  - Instruction
  - Categories
- entity: idea
  shows:
  - Text
references:
- kind: code
  role: implementation
  target: src/renderer/idea-templates.js
---

# Idea template editor

Edit one selected idea template.
