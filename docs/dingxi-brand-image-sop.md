# Dingxi Brand Image SOP

Last updated: 2026-08-10

## Goal

Use this repo as the single source of truth for Dingxi Elementary School brand-identity image generation across slide covers, formal decks, posters, LINE cards, notice images, and other school administrative visuals.

This SOP owns the brand-image decision rules. It does not own browser login, CDP launch, batch execution, deck insertion, or one-off project exports.

## Core Principle

Brand identity supports the message. It should create recognition, warmth, and continuity, but it must not overwhelm the event information, administrative content, workflow, data, or required text.

The core source package is limited to the official Dingxi crest and the four Dingxi mascots. Integrated brand reference images, school-name marks, DX marks, themed variants, event artwork, flags, calligraphy, and past production references are extended or derived assets. Use them only when they help the specific output.

First judge the task's complexity and consistency risk. Multi-page or repeatable outputs should keep fixed identity elements out of the generated image and add them afterward. Small-batch outputs such as meeting notice cards, posters, and single slide covers can let the image model generate the crest natively when the result will be visually checked.

When exact identity matters across many pages, use fixed overlays. When the product is only one or a few images and a cohesive visual matters, use native integrated generation with QA.

## Strategy Router

Choose the mode before writing the prompt.

| Need | Default Mode | Reference Asset | Crest Handling |
| --- | --- | --- | --- |
| Multi-page deck or complex batch | Precision Overlay Mode | `four-mascots-reference.png`, only if mascots help | Keep a modest overlay-safe crest area and add `dingxi-crest.png` after generation |
| Recurring template or page-numbered deck | Precision Overlay Mode | `four-mascots-reference.png`, optional | Add crest/page numbers after generation |
| One-shot slide cover | Usually Native Integrated Brand Mode; use Precision Overlay Mode if exact crest matters | `crest-and-four-mascots-reference.png` for native mode | Generated crest is allowed but must be QA'd |
| Poster, door sign, welcome visual | Native Integrated Brand Mode | `crest-and-four-mascots-reference.png` | Generated crest is acceptable after QA |
| LINE card, meeting notice card, or announcement image | Native Integrated Brand Mode by default for small-batch products; use Precision Overlay Mode only if exact crest is required | `crest-and-four-mascots-reference.png` for native mode | Keep text sparse and phone-readable; QA crest before use |
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
- Keep a modest overlay-safe zone for later overlays. For posters, cards, and announcement images, prefer a low-interference natural background area instead of a large blank patch.
- Add `dingxi-crest.png` afterward by code or manual post-production.
- Add page numbers afterward when the output is a deck.
- Upload `four-mascots-reference.png` only when mascots help the message.
- Keep mascots optional, small, and away from the main content.

Recommended deck safe zones:

- top-right: official crest overlay
- bottom-left: page-number badge

Prompt block:

```text
Do not generate any school crest, logo, seal, stamp, official emblem, watermark, or page number.
Keep the top-right corner low-interference for the official crest overlay.
Leave the bottom-left corner clean and empty for the page-number badge.
Do not place text, icons, metrics, mascots, charts, or important objects in those two corners.
Do not create a large blank patch, visible box, frame, spotlight, label, or special logo area for the crest unless the deck template explicitly needs a fixed safe zone.
```

Mascot reference block:

```text
Use the uploaded image only as Dingxi Elementary four-mascot character reference.
It does not contain the school crest.
Do not generate any school crest, logo, seal, stamp, official emblem, or school badge anywhere in the image.
```

## Mode 2: Native Integrated Brand Mode

Use this when the output is one or a few images, benefits from one cohesive generated scene, and limited crest drift is acceptable after visual QA.

Typical cases:

- meeting notice card
- poster or door sign
- single cover image
- welcome visual
- event announcement main visual
- LINE card or notice card where overall warmth matters more than pixel-perfect crest fidelity

Rules:

- Start a fresh ChatGPT conversation when practical.
- Upload `crest-and-four-mascots-reference.png` as the primary brand reference.
- Tell the model the uploaded image is one integrated Dingxi brand identity reference.
- Make crest preservation a highest-priority instruction.
- Ask for a native image in the final target aspect ratio; do not generate 16:9 and crop to 4:3 or 9:16 later.
- Warn that exact crest fidelity is not guaranteed.
- QA the crest, text, and mascot anatomy before use.

Highest-priority prompt block:

```text
The uploaded brand reference image contains the official Dingxi school crest and the four Dingxi mascots.
Use this uploaded image as one integrated Dingxi Elementary brand identity reference.
Use the crest from the uploaded brand reference as the strict reference for the school crest.
Do not redraw, redesign, simplify, stylize, modernize, reinterpret, replace, rotate, crop, warp, or invent any part of the crest.
Do not create any alternate triangle logo, fake school emblem, extra seal, stamp, badge, watermark, QR code, URL, or page number.
If exact crest reproduction is difficult, make the crest smaller and simpler in placement, but do not change its design.
```

## 2026-06-16 Practical Finding

For native integrated brand generation, directly uploading the combined `crest + four mascots` brand reference reduced crest drift in the parent-meeting cover test compared with uploading separate crest and mascot files or mixing in old cover references.

Observed pattern:

- Separate crest and mascot references made the model more likely to invent a simplified or fake triangle-like crest.
- One integrated brand reference helped the model treat the crest and mascots as one Dingxi identity system.
- Native mascot actions worked better when the mascots were generated as part of the scene rather than pasted as stiff stickers.

Scope of this finding:

- Applies to meeting notice cards, one-shot covers, posters, door signs, and other small-batch main visuals.
- Does not replace Precision Overlay Mode for multi-page decks, complex batches, recurring templates, or outputs where crest fidelity must be exact across many pages.
- Generated crest results still require visual QA and may need rejection.

## Output-Type Guidance

### Formal Decks

Use Precision Overlay Mode by default, especially for multi-page generation.

- Generate each slide as a clean background/content image.
- Keep the top-right and bottom-left overlay zones empty.
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

- Use the integrated brand reference image.
- Keep text large and sparse.
- Put mascots near edges, lower corners, or simple environmental props.
- Reject fake crests, extra badges, QR codes, URLs, or invented school marks.

### LINE Cards And Notice Images

Choose the mode by batch size and crest precision.

- For one or a few meeting notice cards, use Native Integrated Brand Mode by default.
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

Use when the official crest must be exact.

- overlay source for formal decks
- overlay source for official notices
- visual source for QA

Do not rely on native generation when this exact file fidelity is required.

### `four-mascots-reference.png`

Use when the model should learn only mascot character shapes and colors.

- multi-page deck raw generation
- mascot-only support accents
- outputs where the crest will be overlaid later

Do not ask the model to generate the school crest in this mode.

### `crest-and-four-mascots-reference.png`

Use when native integrated brand generation is intentionally selected.

- posters
- one-shot covers
- door signs
- warm single-image announcement visuals

This asset can reduce crest drift for all-in-one generation, but it does not guarantee exact crest fidelity.

This is a derived convenience reference assembled from the core crest and four-mascot sources. It belongs to the extended/reference layer, not the core source package.

## Mascot Integrity Rules

Use these rules whenever a prompt asks for Dingxi mascots:

```text
Use the uploaded image only as Dingxi Elementary four-mascot character reference.
Keep original colors and silhouettes.
Do not invent new mascot species, substitute animals, or merge mascots together.
Never add or remove arms, hands, legs, feet, eyes, wings, tails, horns, ears, fins, claws, or extra body parts.
Props must be held by existing hands only.
If a pose is hard, simplify the pose or make the mascot smaller; do not change mascot anatomy.
Light mascot: yellow round body, one glowing antenna, exactly two arms/hands, exactly two legs/feet, exactly one pair of yellow wings, no tail.
Fire mascot: orange-red flame body, exactly two arms/hands, exactly two legs/feet, two front teeth, no wings, no tail.
Water mascot: blue water-drop body, exactly one eye, exactly two arms/hands, exactly two legs/feet, no wings, no tail.
Tree mascot: orange trunk body with green tree crown, exactly two arms/hands, exactly two legs/feet; leaves, birds, or fruit are decoration, not extra limbs.
```

Sizing guidance:

- Small LINE cards: 0 to 2 mascots.
- Posters and covers: 0 to 4 mascots if they support the scene.
- Formal dense slides: mascots may be omitted.
- Do not place mascots at the center unless the output is explicitly mascot-led.

## Prompt Rules

- State the output type clearly: formal slide, cover, poster, LINE card, notice image, door sign.
- State the exact aspect ratio and orientation.
- State visible text exactly.
- Use Traditional Chinese only when text is present.
- Keep visible text sparse, especially for LINE cards and posters.
- Exclude unrelated project themes when context pollution is likely.
- Ask for one standalone image, not a collage, contact sheet, grid, or multi-panel set.
- For native crest generation, explicitly forbid redesign, simplification, reinterpretation, fake emblems, and alternate triangle logos.

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
- For native output, restart with a fresh conversation and upload only `crest-and-four-mascots-reference.png`.
- Make the crest smaller and simpler in placement.
- Strengthen the "do not redesign" prompt block.

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

- Make mascots smaller.
- Simplify actions.
- Reduce mascot count.
- Reuse the full mascot integrity rules.

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
- crest fidelity or correct crest safe zone
- no fake crest, fake seal, extra badge, watermark, URL, or QR code
- mascot anatomy fidelity
- mascot size and placement
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
