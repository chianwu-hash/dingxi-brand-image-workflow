# Project Runbook

Last reviewed: 2026-08-09
Owner: project maintainers and authorized AI assistants

## Scope

This runbook covers repeatable maintenance for the Dingxi brand-image workflow repo: SOP updates, prompt-pattern updates, Codex skill source updates, safe internal asset routing, public repo validation, and boundaries with browser automation / deck projects.

It does not authorize copying official brand assets into this repo, running browser-generation workflows, editing deck exports, or publishing one-off generated images.

## Safety rules

- Do not commit official Dingxi crest files, mascot image files, scan outputs, contact sheets, Illustrator/PSD/PDF sources, temporary generated images, or one-off production exports.
- Do not copy the whole internal brand folder.
- Do not scan parent network folders or guess credentials.
- If the internal asset path is unavailable, ask the user to open it in Windows File Explorer and authenticate.
- Keep browser launch/session logic in `cbs-workflows` or `browser-automation-workflow`.
- Keep deck-specific outputs in `slidecraft-lab` or the owning project.

## Routine procedures

### Start a maintenance task

1. Read `AGENTS.md`.
2. Read `README.md`.
3. Read `docs/PROJECT_MEMORY.md`.
4. Read `docs/RUNBOOK.md`.
5. Read `docs/dingxi-brand-image-sop.md`.
6. Read `skills/dingxi-brand-image/SKILL.md`.
7. Run `git status --short --branch`.

### Update prompt patterns

1. Read `docs/dingxi-brand-image-sop.md`.
2. Read `skills/dingxi-brand-image/references/prompt-patterns.md`.
3. Select the output type: LINE card, meeting notice, announcement card, poster, slide cover, formal deck, or dense infographic.
4. Choose the crest strategy before writing the prompt.
5. Include mascot integrity rules when mascots appear.
6. Add context-pollution guards when prior project context could leak.
7. If a fixed crest overlay is used, select one of the four corners, record it, and keep it fixed for the whole task.
8. If mascots appear, attach the official reference in the same request and include the selected character identity blocks from `skills/dingxi-brand-image/references/mascot-prompt-rules.md`.

Validation:

- Prompt states target ratio and visible text constraints.
- Prompt forbids fake crest/logo/seal/QR/URL/page number when appropriate.
- Prompt does not include private data.
- Prompt uses output-specific mascot prominence rather than a universal percentage limit.
- Prompt records one crest corner and preserves it across same-task revisions when overlay mode is used.

### Update the skill source

1. Edit `skills/dingxi-brand-image/SKILL.md`.
2. Keep trigger wording aligned with README and SOP.
3. Keep asset routing explicit.
4. Keep tool-choice boundaries with `cbs-workflows`, `cdp-tools`, and `browser-automation-workflow`.

Validation:

- Skill does not instruct agents to commit or publish official brand files.
- Skill asks for user confirmation when mascot selection affects design.
- Skill keeps browser execution outside this repo.

### Check public repo safety

Before committing, search for forbidden asset names and generated artifacts:

```powershell
$official = @(
  'dingxi-crest.png',
  'four-mascots-reference.png',
  'crest-and-four-mascots-reference.png',
  'four-mascots-design-intent.md',
  'AI-usage-guide.md'
)
foreach ($name in $official) {
  Get-ChildItem -Recurse -File -Filter $name -ErrorAction SilentlyContinue
}
```

Also inspect `git status --short --branch` and stage only intended text/source files.

Escalation:

- Stop if official assets, generated outputs, or private materials appear in the staged diff.

## Incident diagnosis

| Symptom | First checks | Next action |
|---|---|---|
| Internal path unavailable | Network/auth state | Ask user to open UNC path in File Explorer; do not guess credentials. |
| Fake crest appears | Chosen mode and prompt restrictions | Switch to overlay mode or regenerate with stricter native reference instructions. |
| Mascot identity or anatomy drift | Prompt describes only generic color/limb counts, reference was not attached, or action requires changed anatomy | Verify the attachment, use the exact character identity block, and choose a different action without redesigning the character. |
| Prompt includes unrelated themes | Prior chat/project context | Start fresh and add context-pollution guard. |
| Generated outputs appear in repo | Git status and artifact paths | Do not commit unless intentionally documented reusable examples and user approved. |
| Browser setup logic appears in repo | File scope | Move/keep in browser automation repos. |

## Maintenance

Update this runbook when the SOP, prompt patterns, skill source, asset-routing path, crest strategy, mascot integrity rules, or repo boundaries change. Record major dated changes in `docs/OPERATIONS_LOG.md` and durable decisions in `docs/PROJECT_MEMORY.md`.
