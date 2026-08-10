# Operations Log

This file records dated changes that future AI assistants and maintainers may need before modifying Dingxi brand-image workflow rules.

Do not record or commit official crest files, mascot image files, source brand assets, generated one-off outputs, private network credentials, browser sessions, or sensitive school records.

## 2026-08-09 — Add repo-local AI memory layer

Changed:

- Updated `AGENTS.md` to include repo-local memory and skill/SOP files in required startup reading.
- Added `CLAUDE.md`.
- Added `docs/PROJECT_MEMORY.md`.
- Added `docs/RUNBOOK.md`.
- Added this operations log.
- Updated `README.md` to point to memory docs.

Reason:

- `dingxi-brand-image-workflow` is a cross-project brand-image SOP, prompt-pattern, and Codex skill source repo.
- Future agents need clear rules for official asset exclusion, crest strategy, mascot integrity, and repo boundaries.

Validation:

- Docs-only change.
- No browser image generation was run.
- No official crest, mascot file, internal source asset, generated output, or private school record was copied into memory docs.

Next-time warnings:

- Choose crest strategy before prompt writing.
- Keep browser execution in `browser-automation-workflow`.
- Keep deck-specific exports in `slidecraft-lab` or the owning project.

## 2026-08-10 — Change poster/card crest overlay guidance to low-interference landing spots

Changed:

- Updated `skills/dingxi-brand-image/SKILL.md` to replace the general "clean crest zone" standard with a "low-interference crest landing spot" standard.
- Updated `skills/dingxi-brand-image/references/prompt-patterns.md` so Unit 8-style poster prompts preserve balanced composition and avoid large blank logo patches.
- Updated `docs/dingxi-brand-image-sop.md` and `README.md` to describe modest overlay-safe areas instead of blank crest areas.
- Updated `docs/PROJECT_MEMORY.md` with the durable decision.

Reason:

- Three ChatGPT poster tests showed that low-interference top-right placement lets the official crest work as a small school identifier without pushing the entire poster composition left.
- Earlier clean-zone prompts could make the crest area dominate the layout.

Validation:

- Text-only change.
- No official crest, mascot file, internal source asset, generated output, or private school record was added to the repo.

Next-time warnings:

- For posters, LINE cards, and announcement images, do not ask for a large blank corner unless the user explicitly needs a fixed template safe zone.
- Keep stricter safe zones available for decks, recurring templates, and dense administrative graphics.
