---
id: rice
summary: Local meeting transcription, AI notes and source-grounded recall on your desktop.
category: productivity
tags:
- meetings
- notes
- local-transcription
authors:
- name: WalissonCF
license: MIT
languages:
- en
- pt-BR
limitations:
- Transcription runs on the computer; Rice does not offer a hosted transcription service.
- Notes and chat require a configured AI provider or a separately installed local model server.
- Calendar connections read events; Rice does not edit calendar events.
- Folders organize meetings without moving their physical meeting directories.
references:
- kind: doc
  role: intent
  target: README.md
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/main/session/meeting-session.ts
---

# Rice

Rice records microphone and system audio, transcribes meetings locally and turns the conversation into template-based notes. People can prepare for calls, annotate and organize their meetings, ask questions grounded in saved material, track follow-ups and export what they need. The desktop app serves English and Brazilian Portuguese on macOS, with a Windows edition described by the project as ready for testing.

## Intent

The project describes Rice as an app that “records your meetings, transcribes them on your machine and writes the notes for you.” Its local-first workflow keeps meeting files in a folder the person chooses and lets them choose the AI for notes and questions. Plain Markdown makes the saved text usable in other applications.
