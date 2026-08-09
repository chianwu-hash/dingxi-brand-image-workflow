---
name: dingxi-brand-image
description: Use when the user asks for Dingxi Elementary School branded AI image generation, including triggers such as「頂溪國小品牌識別生圖」、「頂溪四精靈生圖」、「頂溪 LINE 小卡」、「用頂溪四精靈做小卡」, or requests Dingxi meeting notice cards, LINE cards, announcement images, posters, slide covers, or school administrative graphics that need internal brand asset routing, four-mascot theme selection, mascot integrity checks, or crest overlay guidance.
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
- `dingxi-crest.png`: official crest for post-production overlay only.
- `crest-and-four-mascots-reference.png`: integrated atmosphere reference only when explicitly needed.

Do not commit, upload to a public repo, or publish these files.

## Tool Choice

When the user asks for ChatGPT/Gemini/工作瀏覽器 generation or uses「頂溪國小品牌識別生圖」, prefer the ChatGPT or Gemini work-browser route. Do not switch to built-in `imagegen` unless the user explicitly asks for Codex built-in image generation.

Use:

- `cbs-workflows` / `cdp-tools` for work-browser setup.
- `browser-automation-workflow` for ChatGPT/Gemini image execution.
- this skill for Dingxi brand rules, prompt routing, and QA.

## Workflow

1. Identify output type: LINE card, meeting notice, announcement card, poster, slide cover, formal deck, or other.
2. Copy needed internal assets locally. For Unit 7-style LINE cards without crest overlay, copy only:
   - `four-mascots-reference.png`
   - `four-mascots-design-intent.md`
   - `AI-usage-guide.md`
   For outputs that need school identity through the crest, also copy `dingxi-crest.png`.
3. Write or confirm visible text first. Keep cards sparse and phone-readable.
4. Read `four-mascots-design-intent.md` before choosing mascots.
5. Select mascots by theme. Explain the choice and wait for user confirmation before generating when the mascot choice affects the design.
6. Use the single crest workflow for any output that needs school identity: generate a base image without the crest, reserve a clean crest zone, then overlay `dingxi-crest.png` afterward.
7. Generate with the work browser if requested or implied.
8. Save both files when practical:
   - `<purpose>-base`: generated base image without crest.
   - `<purpose>-final`: final image after official crest overlay.
9. QA text, mascot anatomy, brand balance, false logos, crest zone, official crest overlay, and publishing suitability.

## Mascot Theme Selection

Use the notice topic to choose 1-2 mascots. Do not put all four mascots on ordinary administrative cards.

- 火精靈: learning, training, co-planning, curriculum, exploration, hands-on practice, new tools. Represents 學習火, 探索家, enthusiasm, motivation, curiosity.
- 光精靈: character, gratitude, blessing, team warmth, creativity, kind reminders. Represents 品德光, 創藝家, brightness, virtue, good future.
- 海精靈: reading, sharing, briefing, information exchange, presentations, outcomes. Represents 閱讀海, 分享家, broad knowledge, communication.
- 樹精靈: service, volunteers, environment, sustainability, campus cleanup, practical action. Represents 服務樹, 實踐家, service and action.

Use all four only for mascot introductions, school anniversary, complete brand-identity visuals, or when the user explicitly asks for all four.

## Mascot Integrity Rules

Include these rules whenever mascots appear:

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

Mascots must support the message. Keep them at the bottom or side edge for small cards, away from dates, times, locations, QR codes, tables, and action items.

## Crest Rules

Do not ask the image model to freely generate, redraw, imitate, modify, or merge the official Dingxi crest.

For every output that needs school identity through the crest, generate the background/card/poster without the crest, leave a clean crest zone, then overlay `dingxi-crest.png` by code or manual post-production. This is the only standard crest workflow.

Use a crest zone that fits the composition. Default to an upper corner, but do not hard-code top-right if another clean area is more natural. Keep the zone free of text, mascots, faces, key objects, charts, QR codes, borders, and decorative clutter. Record the intended crest position and keep the base image so the overlay can be adjusted later.

Do not use web images, old poster screenshots, or AI-generated crest-like marks as the official crest. Do not commit, upload, or publish the official crest source file.

Prompt reminder:

```text
Do not generate any school crest, logo, seal, stamp, official emblem, watermark, QR code, URL, phone number, or page number.
Leave a clean area for post-production official crest overlay.
Do not place text, mascots, faces, key objects, icons, charts, QR codes, borders, or dense decoration in that area.
```

Optional exploration note: if the user explicitly wants to see an AI-native integrated composition, you may mention that AI can be asked to compose naturally with a crest-like element, but it will redraw the crest. Whether such output is usable must be judged case by case by the user; it is not the standard workflow and must not replace the official crest overlay for school-identity outputs.

## Reference Prompts

When drafting reusable prompts, read:

- `references/prompt-patterns.md`

Use the Unit 7 pattern for「頂溪國小品牌識別生圖」LINE cards and meeting notice cards with theme-selected mascots. Use the activity poster pattern for Unit 8-style posters: organize activity data, choose or ask AI to suggest a style, generate a base image with a clean crest zone, then overlay the official crest.

## QA Checklist

Reject or revise outputs with:

- wrong event text, date, time, location, or target audience
- unreadable, misspelled, or non-Traditional-Chinese text
- fake crest, fake logo, seal, stamp, badge, watermark, URL, QR code, or phone number
- mascot anatomy errors, including extra/missing hands, feet, eyes, wings, tails, horns, ears, fins, or claws
- mascots covering text or becoming the main subject when not requested
- wrong aspect ratio for the intended channel
- formal identity elements generated by the model instead of added as fixed overlay
- missing clean crest zone when school identity is required
- official crest overlay covering text, mascots, faces, QR codes, or key visuals
- final publishing file missing the official crest when the user asked for school identity
- base/final files not distinguishable when a post-production crest overlay is used
