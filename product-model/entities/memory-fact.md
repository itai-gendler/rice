---
references:
- kind: code
  role: implementation
  target: src/main/memory/types.ts
- kind: code
  role: implementation
  target: src/main/memory/service.ts
- kind: code
  role: implementation
  target: src/main/memory/extract.ts
---

# Memory fact

A remembered commitment, request, decision, question, preference or context. Commitments and requests also appear as follow-ups.

## Information kept

- **Text** — The remembered statement.
- **Kind** — Commitment, request, decision, open question, preference or context.
- **Person** — Who the fact concerns.
- **Company** — Associated company, when established.
- **Topic** — The short subject.
- **Due date** — A stated deadline or an empty date.
- **Mine** — Whether a follow-up belongs to the user.
- **Source** — The originating meeting and date, or a manually entered item.
- **Completion** — When and how the item was resolved.
- **Edited** — Whether the person edited it.
- **Manual** — Whether it was entered by the person.

## States

### Open

The current fact or unresolved follow-up.

### Done

A follow-up has been completed manually or resolved by a later meeting.
