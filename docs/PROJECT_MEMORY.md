# Project Memory

Last reviewed: 2026-08-12

## Project identity

- Project name: `dingxi-brand-image-workflow`
- Repository: `https://github.com/chianwu-hash/dingxi-brand-image-workflow`
- Main local path: `D:\projects\dingxi-brand-image-workflow`
- Main branch: `main`
- Project type: public Dingxi brand-image workflow, prompt-pattern, SOP, and Codex skill source repo.

## Source-of-truth order

1. Current repo files and Git state.
2. `AGENTS.md`, `README.md`, and `docs/dingxi-brand-image-sop.md`.
3. `skills/dingxi-brand-image/SKILL.md` and `skills/dingxi-brand-image/references/prompt-patterns.md`.
4. `docs/PROJECT_MEMORY.md`, `docs/RUNBOOK.md`, and `docs/OPERATIONS_LOG.md` for orientation.
5. Nowledge Memory for cross-tool recall only.
6. Raw Threads as unverified evidence only.

## Current project shape

This repo is the shared Dingxi Elementary brand-image knowledge layer. It centralizes brand-image SOPs, internal asset routing rules, reusable prompt patterns, Codex skill source, crest strategy decisions, mascot integrity, and QA rules.

It is not the browser automation foundation, a logged-in browser/session repo, a deck-specific production repo, or a place to store official brand image files or generated one-off outputs.

## Active decisions

### 2026-08-09 Official brand files stay out of this public repo

Status: active
Scope: repo contents and public sharing
Source: `AGENTS.md`, `README.md`, `docs/dingxi-brand-image-sop.md`, `skills/dingxi-brand-image/SKILL.md`

Decision:

- This repo may document the internal AI work-assets folder path and expected filenames.
- It must not commit, upload, or publish the official crest, mascot image files, scan outputs, source Illustrator/PSD/PDF brand assets, contact sheets, or temporary generated images.
- Copy only needed internal files locally for an authorized workflow.

Reason:

- The repo is public workflow/source text, not a distribution channel for official school assets.

### 2026-08-09 Choose crest strategy before prompt writing

Status: active
Scope: Dingxi branded visual generation
Source: `docs/dingxi-brand-image-sop.md`

Decision:

- Use Precision Overlay Mode for multi-page decks, repeatable templates, complex batches, page-numbered presentations, or exact crest fidelity.
- Use Native Integrated Brand Mode for one-off or small-batch visuals when cohesive generation matters and visual QA is required.
- Do not let image models freely invent or redesign official crest-like marks.

Reason:

- Fake or drifted crests are a predictable failure mode.
- Exact identity and cohesive native composition have different risk profiles.

### 2026-08-10 Use low-interference crest landing spots for posters/cards

Status: active
Scope: Precision overlay mode for posters, LINE cards, announcement images, and other visually composed single-image outputs
Source: `skills/dingxi-brand-image/SKILL.md`, `skills/dingxi-brand-image/references/prompt-patterns.md`, `docs/dingxi-brand-image-sop.md`

Decision:

- The official crest remains a fixed post-production overlay when exact fidelity matters.
- For posters/cards, prompts should not ask the image model to reserve a large blank corner or special logo box.
- Ask for a low-interference crest landing spot instead: natural background may continue through the area, but avoid text, faces, mascot faces, main characters, QR codes, and key visuals.
- Formal decks, recurring templates, and dense administrative graphics may still use stricter overlay safe zones when needed, but the safe zone should remain visually modest.

Reason:

- Tests showed that asking for a clean blank crest zone can make the whole poster composition shift away from the crest corner.
- The crest is a school identifier, not the main design driver.

### 2026-08-09 Mascots support the message and require integrity QA

Status: active
Scope: Dingxi mascot use
Source: `docs/dingxi-brand-image-sop.md`, `skills/dingxi-brand-image/SKILL.md`

Decision:

- Choose 1-2 mascots by theme for ordinary administrative cards.
- Use all four only for mascot introductions, school anniversary, complete brand-identity visuals, or explicit user request.
- QA anatomy, colors, silhouettes, limbs, wings, eyes, tails, and props before use.

Reason:

- Mascot drift and clutter can damage readability and brand trust.

### 2026-08-12 Preserve immutable mascot identity while allowing free action

Status: active
Scope: mascot prompts, reference handling, sizing, and QA
Source: user review of the 2026-08-27 meeting notice card; `skills/dingxi-brand-image/references/mascot-prompt-rules.md`

Decision:

- The model may freely choose mascot pose, motion, expression, direction, and interaction.
- Every selected mascot must preserve its immutable silhouette, proportions, face, colors, outline style, anatomy, markings, and character-specific symbol or prop.
- Treat the mascot as the same established official character, not a new elemental mascot inspired by the reference.
- Use output-specific prominence: small or absent on dense formal slides, moderately prominent on LINE cards/posters, and potentially primary on mascot-led visuals.
- Verify that the official reference attachment is actually present in the same request. A one-mascot crop may be added as reference but must not be pasted into the final art.
- Regenerate failed mascot art instead of repairing it with a stiff cutout overlay.

Reason:

- Limb counts alone do not preserve facial construction, proportions, props, or overall character identity.
- A universal 10% size limit is inappropriate across formal slides, LINE cards, posters, and mascot-led visuals.

### 2026-08-12 Choose one crest corner per task and keep it fixed

Status: active
Scope: precision overlay mode and same-task visual consistency
Source: user instruction

Decision:

- Before generation, the AI chooses the best available corner from top-left, top-right, bottom-left, or bottom-right.
- Record the corner and keep it fixed across the base, final overlay, revisions, and every image in the same task or series.
- Avoid conflicts with page numbers and other fixed elements. Explicit user placement overrides automatic selection.

Reason:

- Crest placement should respond to composition without drifting between related outputs.

### 2026-08-09 Browser and deck execution stay in owning repos

Status: active
Scope: repo boundaries
Source: `README.md`, `docs/dingxi-brand-image-sop.md`

Decision:

- Use `cbs-workflows` / `cdp-tools` for work-browser setup.
- Use `browser-automation-workflow` for ChatGPT/Gemini image execution.
- Use `slidecraft-lab` for deck-specific prompts, exports, and presentation projects.
- Keep this repo focused on brand-image rules, prompt patterns, source mapping, and skill source.

Reason:

- Prevents mixing browser/session infrastructure, brand rules, and one-off production artifacts.

## Internal asset routing

Internal source:

```text
\\10.235.72.5\0-1學校共用資料--行政資料區\00學校徽圖、校歌、校旗、獎狀\AI工作素材
```

Expected local working destination:

```text
D:\AI工作素材\頂溪品牌素材\
```

Do not scan parent folders, guess credentials, or copy the whole brand folder.

## Known failure modes

| Issue | Root cause | Fix or first response |
|---|---|---|
| Fake or drifted crest | Model asked to generate official crest natively without enough constraints | Switch to Precision Overlay Mode or restart with integrated reference and strict QA. |
| Poster composition shifts away from crest corner | Prompt asks for a large clean/blank crest zone | Use a low-interference crest landing spot and let the background continue naturally. |
| Mascot identity or anatomy error | Prompt underconstrained, reference not attached, or action requires changed anatomy | Verify the attachment, use the exact character identity block, and choose another action without redesigning the mascot. |
| Wrong aspect ratio | Generated in one ratio then cropped | Regenerate in native target ratio. |
| Theme drift | Prior project context leaks into prompt | Start a fresh conversation and use context-pollution guard. |
| Repo boundary drift | Execution artifacts or browser logic moved here | Move browser execution to `browser-automation-workflow` and deck exports to owning project. |
| Sensitive/internal assets staged | Internal working files copied into repo | Unstage/remove before commit; keep only workflow text and prompt patterns. |

## User preferences for this project

- Use Traditional Chinese when communicating.
- Keep official school identity protected.
- Prefer exact fixed overlays when output scale or formality makes crest fidelity important.
- Keep prompt patterns reusable and source-controlled, but keep generated one-off outputs out of this repo.
