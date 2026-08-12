---
name: dingxi-brand-image
description: Use when the user asks for Dingxi Elementary School branded AI image generation, including triggers such as「頂溪國小品牌識別生圖」、「頂溪四精靈生圖」、「頂溪 LINE 小卡」、「用頂溪四精靈做小卡」, or requests Dingxi meeting notice cards, LINE cards, announcement images, posters, slide covers, or school administrative graphics that need internal brand asset routing, four-mascot identity checks, AI-native crest redraw for standalone images, or precision crest overlays for decks and image series.
---

# Dingxi Brand Image

Use this skill to create Dingxi Elementary branded visuals without exposing official brand files in a public repo.

## Core Rule

The repo only contains workflow instructions. Official crest and mascot image files must come from the Dingxi internal network AI work-assets folder:

```text
\\10.235.72.5\0-1學校共用資料--行政資料區\00學校徽圖、校歌、校旗、獎狀\AI工作素材
```

Copy only needed files to:

```text
D:\AI工作素材\頂溪品牌素材\
```

If the internal folder is unreachable, stop and ask the user to open the path in Windows File Explorer and complete school network authentication. Do not scan parent folders, guess credentials, or copy the whole brand folder.

## Required Asset Files

Use these files from the internal AI work-assets folder as needed:

- `four-mascots-reference.png`: mascot appearance reference.
- `four-mascots-design-intent.md`: mascot story, educational meaning, and theme mapping.
- `AI-usage-guide.md`: local usage boundaries and QA rules.
- `dingxi-crest.png`: official crest reference for AI-native single-image composition, or the exact source for fixed post-production overlay.
- `crest-and-four-mascots-reference.png`: integrated atmosphere reference only when explicitly needed.

Do not commit or upload these source files to a public repo, and do not publish or distribute them as standalone source assets. They may be embedded in authorized final school outputs according to the selected crest workflow.

## Token Budget And Routing

Treat image-generation routing as a hard cost boundary, not a convenience preference.

- On this user's setup, ChatGPT web image generation and Codex consume different subscription usage pools.
- Built-in Codex `imagegen` consumes Codex tokens heavily. Preserve Codex tokens for orchestration, prompt preparation, file work, compositing, and QA.
- Route Dingxi brand image generation to the ChatGPT work browser by default. Use Gemini only when the user requests it or the task has already selected that route.
- Never silently fall back to built-in `imagegen` because browser automation is slow, unavailable, or unsuccessful. Retry and escalate according to the work-browser skill, then report the blocked generation if it still fails.
- Use built-in `imagegen` only when the user explicitly asks for Codex built-in image generation and thereby accepts the Codex-token cost.

## Tool Choice

When the user asks for ChatGPT/Gemini/工作瀏覽器 generation or uses「頂溪國小品牌識別生圖」, prefer the ChatGPT or Gemini work-browser route. Do not switch to built-in `imagegen` unless the user explicitly asks for Codex built-in image generation.

Use:

- `cbs-workflows` / `cdp-tools` for work-browser setup.
- `browser-automation-workflow` for ChatGPT/Gemini image execution.
- this skill for Dingxi brand rules, prompt routing, and QA.

## Workflow

1. Identify output type: LINE card, meeting notice, announcement card, poster, slide cover, formal deck, or other.
2. Copy only the assets needed for the selected output:
   - Crest in either mode: `dingxi-crest.png`.
   - Mascots: `four-mascots-reference.png`, `four-mascots-design-intent.md`, and `AI-usage-guide.md`.
   - Optional combined atmosphere reference: `crest-and-four-mascots-reference.png` only when it materially helps native integration.
3. Write or confirm visible text first. Keep cards sparse and phone-readable.
4. Read `AI-usage-guide.md` before using brand assets. When mascots appear, also read `four-mascots-design-intent.md` before choosing them.
5. Select mascots by theme. Explain the choice and wait for user confirmation before generating when the mascot choice affects the design.
6. Read `references/mascot-prompt-rules.md` whenever mascots appear. Attach the official reference in the same request and verify its thumbnail before sending. For one-mascot work, also use a temporary crop of that mascot as model reference when practical; never paste that crop into the final art.
7. Select the crest workflow before generation:
   - **Single-image native integration**: default for one standalone LINE card, meeting notice, announcement image, or poster. Attach `dingxi-crest.png` in the same request and ask the model to redraw it as an integrated part of the composition.
   - **Series precision overlay**: default for decks, multi-image series, recurring templates, or any output requiring exact crest fidelity. Generate a natural low-interference landing spot and overlay `dingxi-crest.png` afterward.
   - Explicit user instructions override these defaults. Formal documents, certificates, awards, and legally or institutionally sensitive identity uses always use precision overlay unless the user explicitly approves an AI-redrawn exploratory version.
8. Generate with the work browser if requested or implied. Use an output-specific prompt; do not rely on a generic batch runner to inject brand, mascot-size, crest-mode, or deck-layout rules.
9. Save artifacts according to the selected crest workflow:
   - Native integration: save the generated final image and record that the crest was AI-redrawn from the official reference.
   - Precision overlay: save `<purpose>-base` without the crest and `<purpose>-final` with the exact crest overlay.
10. QA text, immutable mascot identity, anatomy, crest fidelity appropriate to the selected mode, brand balance, and publishing suitability.

## Mascot Theme Selection

Use the notice topic to choose 1-2 mascots. Do not put all four mascots on ordinary administrative cards.

- 火精靈: learning, training, co-planning, curriculum, exploration, hands-on practice, new tools. Represents 學習火, 探索家, enthusiasm, motivation, curiosity.
- 光精靈: character, gratitude, blessing, team warmth, creativity, kind reminders. Represents 品德光, 創藝家, brightness, virtue, good future.
- 海精靈: reading, sharing, briefing, information exchange, presentations, outcomes. Represents 閱讀海, 分享家, broad knowledge, communication.
- 樹精靈: service, volunteers, environment, sustainability, campus cleanup, practical action. Represents 服務樹, 實踐家, service and action.

Use all four only for mascot introductions, school anniversary, complete brand-identity visuals, or when the user explicitly asks for all four.

## Mascot Integrity Rules

Read and use [references/mascot-prompt-rules.md](references/mascot-prompt-rules.md) whenever mascots appear. Include the core block plus the exact identity block for each selected mascot.

Apply these non-negotiable principles:

```text
Generate the same established official Dingxi mascot shown in the uploaded reference, not a new mascot inspired by it.
The AI may freely choose pose, gesture, movement, direction, expression, and interaction to suit the scene.
Movement may change; character identity may not.
Preserve immutable silhouette, proportions, facial construction, colors, outline style, anatomy, limb count, distinctive markings, and character-specific symbols or props.
If an action would require changing anatomy or an immutable feature, choose another action instead.
```

Choose mascot prominence by output type instead of applying one universal size limit. Formal or dense slides usually need small supporting mascots or none; LINE cards and posters may use a more prominent mascot; mascot introductions and brand-led visuals may make mascots the main subjects. Keep approved text and required information readable in every case.

Within one task or series, keep character proportions, palette, outline treatment, and rendering style consistent. Poses may change. Identity treatment may not.

## Crest Rules

Choose one of the following crest workflows before generation. Do not mix workflows silently within a task.

### Single-Image Native Integration

Use this by default for one standalone LINE card, meeting notice, announcement image, or poster when holistic composition and visual balance matter more than pixel-exact crest reproduction.

- Attach `dingxi-crest.png` in the same generation request and verify its thumbnail before sending.
- Tell the model to redraw the same Dingxi crest as an integrated part of the composition, not invent a new logo.
- Preserve the green three-direction outer silhouette, central green ring, white inner field, red `頂溪` core lettering, red-green palette, and overall proportions.
- Let the model choose a balanced location and scale unless the user specifies them.
- Require natural surrounding background and forbid a visible box, backing plate, slot, label, spotlight, or artificial logo reservation.
- Record the result as `AI-redrawn from the official crest reference`; never describe it as the untouched official crest file.
- Compare the generated crest side by side with the official reference. Reject and regenerate if `頂溪` is unreadable, the three-direction silhouette or central ring is lost, the red-green-white identity drifts materially, the crest becomes another badge or shield, or extra lettering appears. Ask the user to confirm borderline redraws before treating them as final.

Prompt reminder:

```text
Use the uploaded official Dingxi crest image as the strict visual reference.
Redraw the same crest as a naturally integrated part of this single composition; do not paste it as a sticker or invent a new logo.
Preserve the green three-direction outer silhouette, central green ring, white inner field, red 頂溪 core lettering, red-green palette, and overall proportions.
Balance the full composition around the crest.
Do not create a visible box, backing plate, slot, label, spotlight, circular badge area, or artificial blank reservation behind it.
Do not add English, a year, ribbon, shield, seal, watermark, or other lettering to the crest.
```

### Series Precision Overlay

Use this by default for decks, multi-image series, recurring templates, page-numbered layouts, formal documents, certificates, awards, and any output requiring an exact or consistently placed crest.

Generate the background without a crest, choose the best low-interference corner from top-left, top-right, bottom-left, or bottom-right, and overlay the original `dingxi-crest.png` afterward. Record that corner and keep its position, size, and treatment fixed across every revision and image in the task unless the user explicitly changes it.

The crest is a small brand identifier, not a main design constraint. Do not reserve a large blank patch, box, frame, spotlight, label, or special logo area. Let the background continue naturally, but keep the selected corner away from text, mascot faces, human faces, key objects, charts, QR codes, borders, and dense decoration. Keep the base image so the overlay can be adjusted later without regenerating the series.

Prompt reminder:

```text
Do not generate any school crest, logo, seal, stamp, official emblem, watermark, QR code, URL, phone number, or page number.
Selected official crest corner for this task: <top-left / top-right / bottom-left / bottom-right>.
Keep this same corner across every revision and image in the task.
Keep that corner low-interference for post-production official crest overlay.
Do not reserve a large blank corner, empty patch, visible box, frame, spotlight, label, or special logo area.
Let the background continue naturally, but avoid text, human faces, mascot faces, main characters, key objects, icons, charts, QR codes, borders, or dense decoration in that area.
```

### Shared Boundaries

Do not use web images or old poster screenshots as crest references. Do not commit or upload the official crest source file to a public repo, and do not publish or distribute it separately from an authorized final school output. An explicit user request may switch either default workflow, but record the selected mode and apply its QA rules consistently.

## Reference Prompts

When drafting reusable prompts, read:

- `references/prompt-patterns.md`

Use the Unit 7 pattern for「頂溪國小品牌識別生圖」LINE cards and meeting notice cards with theme-selected mascots. Use the activity poster pattern for Unit 8-style posters. Both default to single-image native crest integration; use the precision-overlay pattern when the output is a series or needs exact crest fidelity.

## QA Checklist

Reject or revise outputs with:

- wrong event text, date, time, location, or target audience
- unreadable, misspelled, or non-Traditional-Chinese text
- unrequested fake logo, seal, stamp, badge, watermark, URL, QR code, or phone number
- mascot identity drift, including changed silhouette, proportions, face, color, outline style, symbols, or character-specific props
- mascot anatomy errors, including extra/missing hands, feet, eyes, mouths, teeth, tongues, antennae, wing-shaped appendages, tails, horns, ears, fins, or claws
- cropped, blocked, fused, or anatomically ambiguous mascots
- inconsistent mascot proportions or rendering style within the same task
- mascots covering text or becoming the main subject when not requested
- wrong aspect ratio for the intended channel
- native-integration crest with unreadable `頂溪`, materially wrong silhouette or colors, extra lettering, or a visible box/backing plate/logo slot
- native-integration result incorrectly recorded or described as the untouched official crest
- precision-overlay output with a model-generated crest, missing recorded corner, switched placement, inconsistent size, or overlay covering text, mascots, faces, QR codes, or key visuals
- final publishing file missing the crest when the user asked for school identity
- precision-overlay base/final files not distinguishable
