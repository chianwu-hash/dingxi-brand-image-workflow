# Dingxi Brand Image SOP

Last updated: 2026-08-12

## Goal

Use this repo as the single source of truth for Dingxi Elementary School brand-identity image generation across slide covers, formal decks, posters, LINE cards, notice images, and other school administrative visuals.

This SOP owns the brand-image decision rules. It does not own browser login, CDP launch, batch execution, deck insertion, or one-off project exports.

## Core Principle

Brand identity supports the message. It should create recognition, warmth, and continuity, but it must not overwhelm the event information, administrative content, workflow, data, or required text.

The core source package is limited to the official Dingxi crest and the four Dingxi mascots. Integrated brand reference images, school-name marks, DX marks, themed variants, event artwork, flags, calligraphy, and past production references are extended or derived assets. Use them only when they help the specific output.

First judge the task's complexity and consistency risk. Multi-page or repeatable outputs should keep fixed identity elements out of the generated image and add them afterward. One standalone meeting notice card, poster, announcement image, or one-shot cover should let the image model redraw the crest from an uploaded official reference so it can balance the whole composition, provided the result receives visual QA.

When exact identity matters across many pages, use fixed overlays. When the product is only one or a few images and a cohesive visual matters, use native integrated generation with QA.

## Strategy Router

Choose the mode before writing the prompt.

| Need | Default Mode | Reference Asset | Crest Handling |
| --- | --- | --- | --- |
| Multi-page deck or complex batch | Precision Overlay Mode | `four-mascots-reference.png`, only if mascots help | Keep a modest overlay-safe crest area and add `dingxi-crest.png` after generation |
| Recurring template or page-numbered deck | Precision Overlay Mode | `four-mascots-reference.png`, optional | Add crest/page numbers after generation |
| One-shot slide cover | Native Integrated Brand Mode; use Precision Overlay Mode if it belongs to a deck or exact crest matters | `dingxi-crest.png` plus mascot references as needed | AI-redrawn crest is allowed but must be QA'd and recorded |
| Poster, door sign, welcome visual | Native Integrated Brand Mode | `dingxi-crest.png` plus mascot references as needed | AI-redrawn crest is acceptable after QA and recordkeeping |
| One LINE card, meeting notice card, or announcement image | Native Integrated Brand Mode; use Precision Overlay Mode for a repeatable set or exact crest requirement | `dingxi-crest.png` plus mascot references as needed | Keep text sparse and phone-readable; QA and record the AI-redrawn crest |
| Dense information graphic | Precision Overlay Mode or no mascots | `four-mascots-reference.png`, optional | Avoid generated crest and excess brand marks |

If the output is a multi-page deck, complex batch, or repeatable template, choose Precision Overlay Mode unless the user explicitly accepts generated-crest risk.

## Mode 1: Precision Overlay Mode

Use this when the task is complex, multi-page, repeatable, or when crest fidelity and layout consistency matter more than a fully native generated composition.

Typical cases:

- multi-page decks
- complex slide batches
- recurring slide templates
- page-numbered presentations
- administrative proposals with dense content
- outputs where a fake crest would be unacceptable across many pages

Rules:

- Do not ask the model to generate the official school crest, seal, logo, stamp, page number, or watermark.
- Before generation, choose one low-interference crest corner from top-left, top-right, bottom-left, or bottom-right. Record it and keep it fixed across every revision and image in the same task.
- Keep a modest overlay-safe zone in the selected corner. For posters, cards, and announcement images, prefer a low-interference natural background area instead of a large blank patch.
- Add `dingxi-crest.png` afterward by code or manual post-production.
- Add page numbers afterward when the output is a deck.
- Upload `four-mascots-reference.png` only when mascots help the message.
- Keep mascots optional, small, and away from the main content.

Recommended deck overlay planning:

- Choose one available corner for the official crest overlay and keep it fixed throughout the deck.
- If a page-number badge or another fixed element occupies a corner, choose another corner for the crest.
- An explicit task template or user placement overrides automatic corner selection.

Prompt block:

```text
Do not generate any school crest, logo, seal, stamp, official emblem, watermark, or page number.
Selected official crest corner for this task: <top-left / top-right / bottom-left / bottom-right>.
Keep this same corner across every revision and image in the task.
Keep the selected corner low-interference for the official crest overlay.
Leave the bottom-left corner clean and empty for the page-number badge.
If bottom-left is selected for the crest, move the page-number badge to another recorded location.
Do not place text, icons, metrics, mascots, charts, or important objects in the recorded overlay areas.
Do not create a large blank patch, visible box, frame, spotlight, label, or special logo area for the crest unless the deck template explicitly needs a fixed safe zone.
```

Mascot reference block:

```text
Use the uploaded image only as Dingxi Elementary four-mascot character reference.
It does not contain the school crest.
Do not generate any school crest, logo, seal, stamp, official emblem, or school badge anywhere in the image.
```

## Mode 2: Native Integrated Brand Mode

Use this by default when the output is one standalone image, benefits from one cohesive generated scene, and limited crest drift is acceptable after visual QA. A small set may also use this mode only when each image can be reviewed independently and cross-image crest consistency is not required.

Typical cases:

- meeting notice card
- poster or door sign
- single cover image
- welcome visual
- event announcement main visual
- LINE card or notice card where overall warmth matters more than pixel-perfect crest fidelity

Rules:

- Start a fresh ChatGPT conversation when practical.
- Upload `dingxi-crest.png` as the strict crest reference. Also upload `four-mascots-reference.png` and a one-mascot crop when mascots appear.
- Verify every attachment thumbnail before sending.
- Tell the model to redraw the same crest as an integrated part of this one composition, not paste it as a sticker or invent a new logo.
- Make crest preservation and whole-composition balance highest-priority instructions.
- Forbid a visible box, backing plate, slot, label, spotlight, circular badge area, or artificial blank reservation behind the crest.
- Ask for a native image in the final target aspect ratio; do not generate 16:9 and crop to 4:3 or 9:16 later.
- Warn that exact crest fidelity is not guaranteed.
- QA the crest, text, and mascot anatomy before use, and record that the crest was AI-redrawn from the official reference.

Highest-priority prompt block:

```text
Use the uploaded official Dingxi crest image as the strict visual reference.
Redraw the same crest as a naturally integrated part of this single composition; do not paste it as a sticker or invent a new logo.
Preserve the green three-direction outer silhouette, central green ring, white inner field, red 頂溪 core lettering, red-green palette, and overall proportions.
Balance the full composition around the crest.
Do not create a visible box, backing plate, slot, label, spotlight, circular badge area, or artificial blank reservation behind it.
Do not add English, a year, ribbon, shield, seal, watermark, or other lettering to the crest.
```

## 2026-06-16 Practical Finding

An earlier native-generation test found that the combined `crest + four mascots` reference could reduce crest drift compared with loosely constrained separate files. The 2026-08-27 meeting-card test then showed that a strict official crest reference plus explicit redraw and no-container rules can produce a better-balanced single-image composition than reserving a post-production landing spot.

Observed pattern:

- Separate references without explicit attachment verification and identity blocks made the model more likely to invent a simplified crest or generic mascot.
- An integrated reference can help the model treat the crest and mascots as one identity system; separate official references can also work when every thumbnail is verified and the prompt strictly constrains the crest and each mascot.
- Native mascot actions worked better when the mascots were generated as part of the scene rather than pasted as stiff stickers.
- A post-production crest landing spot can distort a single-card layout or create a visible box; native redraw lets the model rebalance the whole upper composition.

Scope of this finding:

- Applies to meeting notice cards, one-shot covers, posters, door signs, and other small-batch main visuals.
- Does not replace Precision Overlay Mode for multi-page decks, complex batches, recurring templates, or outputs where crest fidelity must be exact across many pages.
- Generated crest results still require visual QA and may need rejection.
- Record accepted native results as AI-redrawn from the official reference, not as the untouched official crest.

## Output-Type Guidance

### Formal Decks

Use Precision Overlay Mode by default, especially for multi-page generation.

- Generate each slide as a clean background/content image.
- Select one crest corner for the task and keep it fixed throughout the deck. Keep any page-number location fixed separately without overlap.
- Add crest and page numbers after generation.
- Use 0 to 4 tiny mascots only when they do not interfere with the slide message.
- Omit mascots on dense workflow, table, data, or procurement slides.

### Slide Covers

Choose based on the purpose.

- For a cover generated as part of a multi-page deck, use Precision Overlay Mode so it matches the deck's overlay strategy.
- For a one-shot meeting cover where a warm cohesive scene matters, Native Integrated Brand Mode is the normal first pass.
- Always request the native target ratio, such as 4:3 or 16:9.
- Keep the crest separated from mascots and keep the title area uncluttered.

### Posters And Door Signs

Native Integrated Brand Mode is usually the better first pass.

- Upload the official crest reference and mascot references needed for the specific design.
- Keep text large and sparse.
- Put mascots near edges, lower corners, or simple environmental props.
- Require natural crest integration without a box or sticker effect. Reject unreadable `頂溪`, drifted silhouettes or colors, extra badges, QR codes, URLs, or invented school marks.

### LINE Cards And Notice Images

Choose the mode by batch size and crest precision.

- For one standalone meeting notice card, use Native Integrated Brand Mode by default.
- If the card belongs to a larger repeatable set or the crest must be exact, generate without the crest and overlay `dingxi-crest.png`.
- Keep text short, high-contrast, and phone-readable.
- Prefer 0 to 2 mascots on small cards.
- Do not let mascots compete with dates, times, locations, or action items.

### Dense Information Graphics

Use Precision Overlay Mode or no brand characters.

- Do not force mascots into tables, timelines, workflow diagrams, or metric-heavy layouts.
- Put brand elements at the edges only.
- If a mascot creates clutter, remove it.

## Reference Asset Strategy

This public repo does not ship official Dingxi image files. In school use, first copy the required files from the internal network AI work-assets folder to `D:\AI工作素材\頂溪品牌素材\`.

Internal source:

```text
\\10.235.72.5\0-1學校共用資料--行政資料區\00學校徽圖、校歌、校旗、獎狀\AI工作素材
```

### `dingxi-crest.png`

Use as the crest source in both modes.

- overlay source for formal decks
- overlay source for official notices
- strict visual reference for one-image native integration
- visual source for QA

Do not rely on native generation when exact file fidelity is required. In native mode, record that the accepted crest was AI-redrawn.

### `four-mascots-reference.png`

Use when the model should learn only mascot character shapes and colors.

- multi-page deck raw generation
- mascot-only support accents
- outputs where the crest will be overlaid later

Do not ask the model to generate the school crest in this mode.

### `crest-and-four-mascots-reference.png`

Use as an optional integrated atmosphere reference when it helps native generation.

- posters
- one-shot covers
- door signs
- warm single-image announcement visuals

This asset can reduce crest drift for all-in-one generation, but it does not replace the official `dingxi-crest.png` strict reference or exact mascot identity references when those are available.

This is a derived convenience reference assembled from the core crest and four-mascot sources. It belongs to the extended/reference layer, not the core source package.

## Mascot Integrity Rules

Use the detailed skill reference `skills/dingxi-brand-image/references/mascot-prompt-rules.md` whenever a prompt asks for Dingxi mascots. The official image remains authoritative.

Core rules:

```text
Use the uploaded image as the strict appearance reference for Dingxi Elementary's established official mascot characters.
Generate the same official character in the new scene, not a newly invented mascot inspired by the reference.
The AI may freely choose pose, gesture, movement, direction, expression, and interaction to suit the scene.
Movement may change; character identity may not.
Preserve immutable silhouette, proportions, facial construction, colors, outline style, anatomy, limb count, distinctive markings, and character-specific symbols or props.
If an action would require changing anatomy or an immutable feature, choose another action instead.
```

Reference handling:

- Attach the official reference in the same request and verify the visible attachment thumbnail before sending.
- For a one-mascot task, also attach a temporary crop of the selected mascot when practical. Use it only as model reference, not as a pasted final layer.

Adaptive sizing guidance:

- Formal or information-dense slides: small supporting mascots or none; about 6–12% of image height is a common guideline, not a hard limit.
- Administrative LINE cards and friendly notices: one selected mascot may commonly occupy about 15–25% of image height when text remains clear.
- Posters and activity visuals: mascots may commonly occupy about 15–30% of image height.
- Mascot introductions, anniversaries, and brand-led visuals: mascots may be the main subjects without a fixed percentage cap.
- Do not shrink a mascot until identity features become unreadable or enlarge it until required information is obstructed.

## Prompt Rules

- State the output type clearly: formal slide, cover, poster, LINE card, notice image, door sign.
- State the exact aspect ratio and orientation.
- State visible text exactly.
- Use Traditional Chinese only when text is present.
- Keep visible text sparse, especially for LINE cards and posters.
- Exclude unrelated project themes when context pollution is likely.
- Ask for one standalone image, not a collage, contact sheet, grid, or multi-panel set.
- For native crest generation, explicitly require a redraw of the same referenced crest, whole-composition balance, no backing container, and no alternate emblem or added lettering.

Context-pollution guard:

```text
This output is only for the stated Dingxi Elementary event or notice.
Do not mention or imply unrelated themes such as AI workbench, platform, system, workshop, product, technology, or any other previous project context.
```

## Failure Patterns And Recovery

### Fake Or Drifted Crest

Symptoms:

- simplified triangle logo
- wrong colors
- missing red Chinese characters
- invented school mark
- multiple extra crests or seals

Recovery:

- For multi-page or complex output, switch to Precision Overlay Mode.
- For native output, restart with a fresh conversation and reattach `dingxi-crest.png` plus only the mascot references needed.
- Verify the attachment thumbnails.
- Strengthen the identity, readable `頂溪`, no-container, and no-extra-lettering blocks.
- Let the model rebalance location and scale; do not repair a failed crest with a stiff cutout unless switching the whole task to Precision Overlay Mode.

### Wrong Aspect Ratio

Symptoms:

- 16:9 generated then cropped to 4:3
- important content near cut edges
- poster/card layout squeezed into slide proportions

Recovery:

- Regenerate in the native target ratio.
- Explicitly say "do not create a different ratio and crop it."

### Mascot Anatomy Errors

Symptoms:

- extra arms, legs, eyes, wings, tails, horns, or fins
- mascots merged into a new species
- props held by invented limbs

Recovery:

- Reuse the exact selected-character identity block from `mascot-prompt-rules.md`.
- Verify that the official reference attachment was actually sent with the prompt.
- Choose another action if the current action requires changed anatomy; action freedom does not permit identity drift.
- Reduce mascot count only when characters are merging or becoming anatomically ambiguous.
- Regenerate the mascot as part of the scene; do not repair it by pasting a stiff cutout into the final image.

### Theme Drift

Symptoms:

- old deck topic appears in a meeting cover
- AI/workbench/platform language leaks into parent or school notices
- fake QR codes, URLs, English filler, or tech UI appears

Recovery:

- Start a fresh conversation.
- State the event or notice purpose at the top.
- Add the context-pollution guard.

## QA Checklist

Check every generated output for:

- correct mode choice for the output type
- correct aspect ratio and orientation
- native crest identity and integration, or correct precision-overlay safe zone
- no fake crest, fake seal, extra badge, watermark, URL, or QR code
- mascot anatomy fidelity
- mascot immutable-identity fidelity, including face, proportions, colors, outline, symbols, and props
- mascot size and placement
- same-task mascot style consistency; fixed crest-corner and size consistency when using Precision Overlay Mode
- Traditional Chinese text accuracy
- date, school year, event name, location, and action item accuracy
- no unrelated project theme
- readability at intended display size
- no important content inside overlay safe zones when using Precision Overlay Mode

For deck insertion or document production, perform separate deck/PPTX QA in the project that owns that output.

## Repo Boundaries

- Use `cbs-workflows` to prepare logged-in browser sessions and shared CDP readiness.
- Use `browser-automation-workflow` to upload references and run ChatGPT or Gemini image batches.
- Use this repo to store Dingxi brand-image rules, prompt patterns, source mapping, and skill source.
- Use `slidecraft-lab` only when the work becomes a specific presentation project.
- Keep one-off generated outputs out of this repo unless they are intentionally documented as reusable examples.
