# Dingxi Brand Image Prompt Patterns

Use these patterns when drafting prompts for ChatGPT or Gemini work-browser image generation.

## Unit 7 LINE Card With Theme-Selected Mascots

Use when the user says「頂溪國小品牌識別生圖」or asks for a Dingxi LINE notice card with four-mascot identity.

```text
Create one vertical 9:16 LINE meeting notice card for Dingxi Elementary School.

Use the uploaded image only as Dingxi Elementary four-mascot character reference.
Use only the mascots confirmed by the user:
<chosen mascots and reason>

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
- Place the selected mascot(s) as small supporting accents near the lower edge or side edge.
- Mascots must not cover or compete with the meeting information.

Mascot identity:
- Keep original colors and silhouettes from the uploaded reference.
- Do not invent new mascot species.
- Do not add or remove body parts.
- If a pose is difficult, make the mascot smaller or simpler.

Restrictions:
- Do not generate any school crest, logo, seal, stamp, badge, watermark, QR code, URL, phone number, meeting link, or page number.
- Do not include real personal data.
- Create exactly one standalone image.
```

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
Keep a low-interference area for post-production official crest overlay. Default to an upper corner unless the composition clearly has a better low-interference area.
Do not reserve a large blank corner, empty patch, visible box, frame, spotlight, label, or special logo area.
Let the background continue naturally, but avoid text, human faces, mascot faces, main characters, charts, icons, QR codes, borders, dense decoration, or important objects in that area.
Keep the base image without the crest. Add the official crest only afterward as a fixed overlay.
```

## Unit 8 Activity Poster With Official Crest Overlay

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

Stage 3: generate the base image without the crest.

```text
Create one <vertical/horizontal> Dingxi Elementary activity poster base image.

Visible text, exactly these lines only:
<approved poster text>

Visual direction:
<approved style direction>

Layout:
- Traditional Chinese only.
- Clear hierarchy: title, key information, reminder.
- Design for <LINE / bulletin board / school website / print>.
- Keep the whole poster composition balanced and natural.
- Do not push the main title, people, mascots, or focal point away from the crest corner just to make room for the crest.
- Keep a low-interference area for post-production official crest overlay. Default to an upper corner unless the composition clearly has a better low-interference area.
- Do not reserve a large blank corner, empty patch, visible box, frame, spotlight, label, or special logo area.
- Let the background continue naturally, but avoid text, human faces, mascot faces, main characters, charts, icons, QR codes, borders, dense decoration, or important objects in the crest area.

Restrictions:
- Do not generate any school crest, logo, seal, stamp, badge, watermark, QR code, URL, phone number, or page number.
- Do not add, remove, or rewrite the approved text.
- Create exactly one standalone base image without the crest.
```

Stage 4: post-production.

```text
Save the generated image as <purpose>-base.
Overlay the official dingxi-crest.png in the low-interference crest landing spot.
Save the result as <purpose>-final.
Check that the crest does not cover text, mascots, faces, QR codes, or key visuals.
```
