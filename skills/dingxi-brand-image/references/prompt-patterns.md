# Dingxi Brand Image Prompt Patterns

Use these patterns when drafting prompts for ChatGPT or Gemini work-browser image generation.

## Unit 7 LINE Card With Theme-Selected Mascots

Use when the user says「頂溪國小品牌識別生圖」or asks for a Dingxi LINE notice card with four-mascot identity.

```text
Create one vertical 9:16 LINE meeting notice card for Dingxi Elementary School.

Use the uploaded official Dingxi crest image as the strict crest reference, and use the uploaded mascot image only as Dingxi Elementary four-mascot character reference.
Use only the mascots confirmed by the user:
<chosen mascots and reason>
Insert the core prompt block and selected character identity blocks from mascot-prompt-rules.md.

Visible text, exactly these lines only:
頂溪國小
會議通知
<會議名稱>
<日期>
<時間>
<地點>

Design direction:
- Traditional Chinese only.
- Designed for LINE group sharing on a smartphone.
- Large readable text with generous spacing.
- Warm, clean, official-but-friendly elementary school administrative style.
- Dingxi deep green, warm cream, soft golden yellow, muted sky blue, fresh leaf green.
- Choose mascot size and prominence from this LINE-card purpose. A selected mascot may be moderately prominent and naturally integrated into the composition.
- Mascots must not cover or compete with the meeting information.
- Redraw the same Dingxi crest as a naturally integrated part of this single composition. Preserve its green three-direction outer silhouette, central green ring, white inner field, red 頂溪 core lettering, red-green palette, and overall proportions.
- Balance the whole composition around the crest. Do not paste it as a sticker or place it inside a visible box, backing plate, slot, label, spotlight, circular badge area, or artificial blank reservation.

Mascot identity:
- Generate the same established official Dingxi mascot shown in the uploaded reference, not a new mascot inspired by it.
- The AI may freely choose pose, movement, expression, and interaction to suit the scene.
- Movement may change; character identity may not.
- Preserve immutable silhouette, proportions, face, colors, outline style, anatomy, distinctive markings, and character-specific symbols or props.
- If an action would require changing anatomy or an immutable feature, choose another action instead.

Restrictions:
- Do not invent another logo, shield, seal, stamp, badge, watermark, QR code, URL, phone number, meeting link, or page number.
- Do not add English, a year, ribbon, or extra lettering to the crest.
- Do not include real personal data.
- Create exactly one standalone image.
```

Record the result as AI-redrawn from the official crest reference. Reject and regenerate if the crest lettering is unreadable or its defining silhouette and colors drift materially.

## Plain Meeting Notice Card

Use when the user wants a non-branded first draft before mascot styling.

```text
Generate one 16:9 horizontal meeting notice card image.

Create a warm, clean, official-but-friendly elementary school administrative notice card.

Visible text, exactly these lines only:
會議通知
<會議名稱>
<日期>
<時間>
<地點>

Visual direction:
- Traditional Chinese only.
- Text must be large and readable on a phone.
- Use clean meeting-related visuals such as calendar, clipboard, folder, pen, or checklist.
- Do not generate any school crest, logo, seal, stamp, watermark, QR code, URL, phone number, or page number.
```

## Precision Overlay Visual

Use when the final output needs an exact official crest.

```text
Generate the background/card without any school crest, logo, seal, stamp, watermark, QR code, URL, phone number, or page number.
Before generation, select one official crest corner for the task: top-left, top-right, bottom-left, or bottom-right.
Record the selected corner and keep it unchanged across every base image, final image, revision, and image in the same task.
Selected official crest corner for this task: <selected corner>.
Keep that corner low-interference for post-production official crest overlay.
Do not reserve a large blank corner, empty patch, visible box, frame, spotlight, label, or special logo area.
Let the background continue naturally, but avoid text, human faces, mascot faces, main characters, charts, icons, QR codes, borders, dense decoration, or important objects in that area.
Keep the base image without the crest. Add the official crest only afterward as a fixed overlay.
```

## Unit 8 Activity Poster With AI-Native Crest Integration

Use when creating Dingxi activity posters, announcement posters, campus event graphics, or other school-identity poster outputs.

Stage 1: organize the activity information before generating the image.

```text
Organize this activity information for a Dingxi Elementary poster.

Input:
- Activity name: <activity name>
- Date and time: <date/time>
- Location: <location>
- Audience: <students/parents/teachers/public>
- Registration or reminder: <registration/reminder>
- Posting channel: <LINE / bulletin board / school website / print>

Return:
- main title
- subtitle if needed
- short information rows
- reminder sentence
- lines that must appear exactly
Do not generate an image yet.
```

Stage 2: choose a style.

```text
Suggest two visual style directions for this activity poster, or follow this user-specified style:
<style direction>

Keep the style suitable for an elementary school administrative/activity poster.
Do not generate an image yet.
```

Stage 3: generate the complete poster with the crest integrated into the composition.

```text
Create one <vertical/horizontal> Dingxi Elementary activity poster.

Use the uploaded official Dingxi crest image as the strict crest reference.

Visible text, exactly these lines only:
<approved poster text>

Visual direction:
<approved style direction>

Layout:
- Traditional Chinese only.
- Clear hierarchy: title, key information, reminder.
- Design for <LINE / bulletin board / school website / print>.
- Keep the whole poster composition balanced and natural.
- Redraw the same Dingxi crest as a naturally integrated part of the poster. Preserve its green three-direction outer silhouette, central green ring, white inner field, red 頂溪 core lettering, red-green palette, and overall proportions.
- Choose a location and scale that balance the whole poster.
- Do not paste the crest as a sticker or create a visible box, backing plate, slot, label, spotlight, circular badge area, or artificial blank reservation behind it.

Restrictions:
- Do not invent another logo, shield, seal, stamp, badge, watermark, QR code, URL, phone number, or page number.
- Do not add English, a year, ribbon, or extra lettering to the crest.
- Do not add, remove, or rewrite the approved text.
- Create exactly one complete standalone image.
```

Stage 4: QA and recordkeeping.

```text
Save the generated image as <purpose>-final.
Check that the crest is readable, preserves the defining official silhouette and colors, has no added lettering, and integrates naturally without a box or sticker effect.
Record that the crest was AI-redrawn from the official crest reference.
```
