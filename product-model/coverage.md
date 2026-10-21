---
scope: Desktop meeting recording, local transcription, notes, templates, chat, organization, sharing, calendar preparation,
  memory, follow-ups and live research.
method: Static source tracing from desktop controls through handlers, services and stored effects, with documentation
  and selected tests read as supporting evidence.
covered:
- description: Desktop recording entry points, meeting surfaces, live controls and recovery orchestration.
  paths:
  - src/main/app/
  - src/renderer/renderer.js
  - src/renderer/home.js
  - src/renderer/nub.js
  - src/renderer/alert.js
  - src/renderer/onboarding.js
- description: Recording, local transcription outcomes, interruption recovery, notes generation and local persistence.
  paths:
  - src/main/session/
  - src/main/asr/
  - src/main/store/
  - src/shared/
- description: Template catalogs, editable overrides and history controls.
  paths:
  - src/main/templates/
  - src/renderer/templates.js
  - src/renderer/idea-templates.js
  - src/renderer/versions.js
  - src/renderer/template-picker.js
- description: AI selection, grounded retrieval, chat and exported meeting material.
  paths:
  - src/main/ai/
  - src/main/search/
  - src/main/share/
  - src/main/claude/
  - src/renderer/global-chat.js
  - src/renderer/share.js
  - src/renderer/prompts-menu.js
  - src/renderer/web-search.js
- description: Optional calendar sources, attachments, screenshots and user-visible privacy behavior.
  paths:
  - src/main/calendar/
  - src/main/attachments/
  - src/main/screenshots/
  - src/main/privacy/
  - src/renderer/calendar-connect.js
  - src/renderer/attachments.js
  - src/renderer/screenshots.js
  - src/renderer/privacy.js
  - src/renderer/receipt-card.js
- description: Memory facts, briefings, follow-up tracking and live suggestions and investigation.
  paths:
  - src/main/memory/
  - src/main/warroom/
  - src/renderer/memory.js
  - src/renderer/memory-page.js
  - src/renderer/followups.js
  - src/renderer/warroom.js
- description: Settings subjects and platform-specific microphone choices.
  paths:
  - src/renderer/settings.js
  - src/renderer/audio-settings.js
  - src/renderer/language-settings.js
  - src/renderer/ai-providers.js
  - src/renderer/mic-chip.js
  - src/main/platform/mic-pick.ts
exclusions:
- description: Build, packaging, installer, distribution and developer automation.
  paths:
  - scripts/
  - .github/
  - build/
  - package.json
  - install.sh
  - get.sh
  - update.sh
  - install.ps1
  - install-win.ps1
- description: Automated tests.
  paths:
  - tests/
- description: Interface text catalogs.
  paths:
  - src/main/i18n.ts
  - src/renderer/locales/
- description: Visual tokens, icon assets and layout styling.
  paths:
  - design/
  - assets/
  - src/renderer/assets/
- description: Native capture helpers and transcription-model numeric internals.
  paths:
  - native/
  - resources/
  - src/main/asr/fbank.ts
  - src/main/asr/silero-vad.ts
- description: Internal operational logging.
  paths:
  - src/main/log.ts
unmapped:
- description: Update checking, download, installation and restart code.
  paths:
  - src/main/update/
  - src/renderer/update-page.js
  - src/renderer/win-update.js
- description: Live translation and optional offline translation package code.
  paths:
  - src/main/translate/
  - src/renderer/translate.js
- description: Home code that lists and completes the system's own reminders.
  paths:
  - src/main/app/main.ts
  - src/renderer/home.js
- description: Windows start-at-login code.
  paths:
  - src/main/app/login-item.ts
  - src/renderer/settings.js
limitations:
- description: Platform helpers whose device, permission and call-detection results depend on the operating system.
  paths:
  - src/main/platform/
---

# Coverage


