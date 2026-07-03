# dingxi-brand-image-workflow

Reusable Dingxi Elementary School brand-image generation workflow, documentation, prompt patterns, and Codex skill source.

## Purpose

This repository is the shared home and source of truth for Dingxi Elementary School brand-identity image generation work that should not be trapped inside any one deck, poster, notification project, local skill install, or browser automation script.

It is intended to centralize:

- brand-image SOPs
- routing rules for internal brand reference assets
- prompt patterns across multiple output types
- Codex skill source for Dingxi brand image work
- decision rules for when to use native model generation versus fixed overlays
- cross-output guidance for slide covers, formal decks, posters, LINE cards, and notice images

This repo is not the browser automation foundation and not a single deck project.

## Install The Skill

In Codex, ask:

```text
請從 GitHub repo chianwu-hash/dingxi-brand-image-workflow 安裝 dingxi-brand-image skill，skill 路徑是 skills/dingxi-brand-image。
```

Manual fallback: copy `skills/dingxi-brand-image/` into `%USERPROFILE%\.codex\skills\dingxi-brand-image\`.

After installation, a user can trigger the workflow with natural language such as:

```text
頂溪國小品牌識別生圖，幫我做一張家長代表大會 LINE 小卡
```

The skill does not ship official brand image files. It expects Dingxi staff to access the internal network AI work-assets folder and copy the needed files locally during the workflow.

## Internal Brand Material Split

The core brand-image source package is intentionally limited to the internal network AI work-assets folder:

```text
\\10.235.72.5\0-1學校共用資料--行政資料區\00學校徽圖、校歌、校旗、獎狀\AI工作素材
```

That internal folder contains:

- official Dingxi school crest
- four Dingxi mascots
- four-mascot design intent notes
- AI usage guide and asset manifest

The public GitHub repo intentionally does not include the actual image files.

Integrated crest-plus-mascot references, DX marks, school-name title images, banners, themed variants, flags, calligraphy, certificates, and past production references belong to the extended material layer unless explicitly promoted later.

## Production Modes

This repo preserves two valid strategies:

- `Precision Overlay Mode`
  Use for multi-page generation, complex batches, recurring templates, page-numbered presentations, and outputs where exact crest consistency is required. The generated image leaves the crest area blank, then `dingxi-crest.png` is added afterward.
- `Native Integrated Brand Mode`
  Use for one or a few finished images where visual cohesion matters and the result will be QA'd. This is useful for meeting notice cards, posters, door signs, one-shot covers, LINE cards, and announcement visuals.

The 2026-06-16 parent-meeting cover test found that directly uploading the combined `crest + four mascots` brand reference can reduce crest drift for native small-batch generation. That finding supports meeting notice cards, posters, and one-shot covers; it does not replace fixed crest overlays as the safest default for multi-page deck production.

That combined reference is a derived convenience asset for Native Integrated Brand Mode, not part of the core source package.

## Relationship To Other Repos

- `browser-automation-workflow`
  Owns reusable ChatGPT / Gemini browser automation and batch-generation execution.
- `cbs-workflows`
  Owns browser session setup, login reuse, and CDP readiness flows.
- `slidecraft-lab`
  Owns deck-specific prompts, exports, and presentation project implementation.

In short:

- `cbs-workflows` = browser/session foundation
- `browser-automation-workflow` = image-run execution layer
- `dingxi-brand-image-workflow` = Dingxi brand-image knowledge layer
- `slidecraft-lab` = presentation project layer

## Current Structure

- `docs/`
  central SOPs and repo-level guidance
- `prompts/`
  reusable prompt examples grouped by output type
- `skills/dingxi-brand-image/`
  repo-owned source for the Codex skill
- `references/`
  source-mapping notes and future supporting references

## Current Focus

The first consolidated topic in this repo is Dingxi brand-identity image generation across:

- slide covers
- posters
- LINE notice cards
- meeting announcement visuals

The main SOP is:

- [docs/dingxi-brand-image-sop.md](docs/dingxi-brand-image-sop.md)

The current skill source is:

- [skills/dingxi-brand-image/SKILL.md](skills/dingxi-brand-image/SKILL.md)

Seed prompt examples currently include:

- `prompts/slide-covers/parent-meeting-cover-4x3-native-brand-reference.txt`
- `prompts/slide-covers/generic-16x9-precision-overlay-cover.txt`
- `prompts/line-cards/generic-9x16-native-brand-reference.txt`
- `prompts/posters/generic-door-sign-native-brand-reference.txt`
