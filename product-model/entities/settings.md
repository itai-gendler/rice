---
references:
- kind: code
  role: implementation
  target: src/main/app/main.ts
- kind: code
  role: implementation
  target: src/renderer/settings.js
singleton: true
---

# Settings

Choices Rice keeps for this installation and its active meetings folder.

## Information kept

- **Meetings folder** — Where the active meeting collection is stored.
- **App language** — English or Brazilian Portuguese.
- **Default meeting language** — Portuguese, English or Automatic.
- **Default template** — The note template used for new drafts.
- **Audio settings** — Keep audio, microphone choices and platform-specific transcription options.
- **Vocabulary** — Custom terms and whether calendar attendees contribute.
- **Identify participants** — Whether local speaker identification is enabled.
- **Screenshots enabled** — Whether optional capture is enabled.
- **AI provider** — The active provider.
- **AI model** — The selected primary model.
- **Light model** — The model for lighter tasks.
- **Local server** — Server selection, localhost address and context size.
- **Cycle limit** — Per-track live-cycle limit; zero means unlimited.
- **Chat tools** — Whether supported chat tools and MCPs are enabled.
- **Fully local** — Whether fully local mode is enabled.
- **Hide personal data** — Global choice to redact supported personal data in remote AI text.
- **Default retention** — Separate default audio and meeting retention.
- **Consent reminder** — Whether to show the nonblocking reminder and its optional custom text.
- **Shortcut** — The registered global recording shortcut or None.
- **Memory enabled** — Whether extraction and recall are enabled.
- **Memory progress** — Older-meeting extraction progress and cancellation status.
- **Follow-up notifications** — Whether local due-date reminders are enabled.
