# Dingxi Mascot Prompt Rules

Read this file whenever a generated image includes one or more Dingxi mascots. The official reference image remains authoritative; these words help the model preserve identity but do not replace visual comparison.

## Reference Handling

- Attach `four-mascots-reference.png` in the same ChatGPT/Gemini request as the prompt.
- Verify that the attachment thumbnail is visible before sending.
- For a one-mascot task, also attach a temporary crop of that mascot when practical. Use the crop only as model reference, never as a pasted final-art layer.
- Call the mascot an established official character, not a new design inspired by an element.
- Keep reference assets local and out of public repositories.

## Core Prompt Block

```text
Use the uploaded image as the strict appearance reference for Dingxi Elementary's established official mascot characters.
Generate the same official character in the new scene, not a newly invented mascot inspired by the reference.

The AI may freely choose each mascot's pose, gesture, movement, direction, expression, and interaction to suit the scene and communication purpose. The new pose does not need to stay close to the reference pose.

Movement may change; character identity may not. Preserve the immutable body silhouette, proportions, facial construction, colors, outline style, anatomy, limb count, distinctive markings, and character-specific symbols or props described below and shown in the uploaded reference.

Do not invent a new mascot species, substitute an animal, exchange features between mascots, or merge mascots together. Do not add or remove eyes, mouths, teeth, tongues, antennae, arms, hands, wing-shaped appendages, legs, feet, tails, horns, ears, fins, claws, or support limbs.

Props must be held with the character's existing anatomy. If a proposed action would require changing anatomy or an immutable appearance feature, choose another action instead.
```

## Immutable Character Identity

Use only the block for each selected mascot.

### Light Mascot / 光精靈 / Sparky

```text
Light Mascot (光精靈, Sparky): the same bright-yellow, round official character shown in the reference. Preserve the single tall loop-shaped antenna ending in one glowing white orb; two large round white eyes with black pupils; wide curved black smile with a small red tongue at the right; the circular peace emblem centered on the torso; exactly one pair of yellow wing-shaped side appendages; and exactly two short yellow legs with flat feet. The wing-shaped side appendages are the character's only side limbs: do not add a separate pair of arms or hands. No tail, ears, horns, or extra wings.
```

### Fire Mascot / 火精靈 / Blazy

```text
Fire Mascot (火精靈, Blazy): the same red-orange flame-bodied official character shown in the reference. Preserve the pointed multi-tip flame silhouette with yellow-orange inner edge; two large round white eyes with black pupils; curved black smile; exactly two small white front teeth; exactly two arms/hands; exactly two short legs with broad flat feet; and the blue magnifying glass as its character-specific exploration prop. No wings, tail, extra flame limbs, or additional teeth.
```

### Sea Mascot / 海精靈 / Splashy

```text
Sea Mascot (海精靈, Splashy): the exact same established official character shown in the reference, not a generic water-drop mascot. Preserve the tall blue water-drop body with thick black outline and light-cyan highlight along the left edge; exactly one very large round eye near the upper center; one huge open black mouth; exactly two white triangular upper fangs, one at each upper mouth corner; one red oval tongue inside the mouth; exactly two arms/hands; and exactly two short legs ending in broad, flat blue feet. Preserve the bright-green thick book held diagonally along the character's right side, including pale-yellow page edges and the large bite mark on the book's outer-right edge. No extra eyes, mouth, teeth, tongue, wings, tail, ears, horns, fins, claws, tentacles, or support limbs.
```

### Tree Mascot / 樹精靈 / Woody

```text
Tree Mascot (樹精靈, Woody): the same orange trunk-bodied official character shown in the reference. Preserve the tall rectangular orange trunk; large rounded green leafy crown; two tall oval white eyes with black pupils; small curved smile with two small white corner teeth; exactly two orange-yellow arms/hands; exactly two orange-yellow legs/feet; and the blue backpack as its character-specific service-and-action prop. Keep small birds and round fruit as crown decoration only, never as body parts or extra limbs. No tail, wings, branch arms, root legs, or additional faces.
```

## Multiple Mascots

```text
Keep every mascot as a separate, complete, recognizable character.
Do not exchange colors, faces, limbs, symbols, or props between mascots.
Do not fuse overlapping bodies or use one mascot's body part to complete another.
Interactions such as waving, reading together, carrying an object, or standing close are allowed only when every character's anatomy remains visually traceable.
```

## Adaptive Size And Prominence

Choose mascot prominence from the output type and communication purpose. These are guidelines, not universal hard limits:

- Formal or information-dense slides: use small supporting mascots, commonly about 6–12% of image height, or omit them.
- Administrative LINE cards and friendly notices: one selected mascot may commonly occupy about 15–25% of image height when text remains clear.
- Posters and activity visuals: mascots may commonly occupy about 15–30% of image height.
- Mascot introductions, anniversaries, and brand-led visuals: mascots may be the main subjects without a fixed percentage cap.

Do not shrink a mascot until its immutable features become unreadable. Do not enlarge it until it obstructs approved text or required information.

## Same-Task Consistency

Within one task or visual series, keep the same character proportions, palette, outline treatment, and rendering style across every version. Poses may change. Identity treatment may not.

## QA

Reject and regenerate when:

- the result resembles a new elemental mascot instead of the same official character
- an immutable feature is missing, added, exchanged, recolored, or reshaped
- a character-specific symbol or prop is missing or assigned to another mascot
- the pose creates hidden, fused, or anatomically ambiguous limbs
- the character is cropped at the canvas edge or a key facial feature is blocked
- multiple mascots merge visually
- a mascot covers approved text, dates, times, locations, QR codes, or action items
- style or proportions drift between images in the same task

Do not repair a failed mascot by pasting a stiff character cutout into the final image. Regenerate it with stronger identity constraints. Fixed post-production overlay remains the standard only for the official crest when exact crest fidelity is required.
