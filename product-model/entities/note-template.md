---
references:
- kind: code
  role: implementation
  target: src/main/templates/store.ts
- kind: code
  role: implementation
  target: src/main/templates/schema.ts
domain: note-templates
---

# Note template

A built-in template with a user-editable override, or a custom template for generated notes.

## Information kept

- **Title** — The template name.
- **Description** — The meeting purpose.
- **Sections** — Ordered section titles, each with a description of what Rice should write there.
- **Built in** — Whether the template ships with Rice.
- **Customized** — Whether the built-in content has a local override.
