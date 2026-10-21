---
references:
- kind: code
  role: implementation
  target: src/main/warroom/store.ts
- kind: code
  role: implementation
  target: src/main/warroom/ipc.ts
---

# Finding

An investigation result and its supporting source.

## Information kept

- **Text** — The finding.
- **Time** — When it was produced.
- **Source** — The source type and reference.
- **Pinned** — Whether it is prioritized in later context.

## States

### Visible

Available in the investigation results.

### Dismissed

Hidden from the current results, with an undo action.
