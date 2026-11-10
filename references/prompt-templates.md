# Prompt templates

Use only the templates relevant to the current stage. Replace every bracketed field.

## Reusable wallpaper prompt

```text
Use case: stylized-concept
Asset type: [PHONE / DESKTOP / TABLET] wallpaper

Primary request:
Create an original wallpaper themed around [SCENE_THEME]. Preserve the approved style system without reproducing any reference image's exact layout or unique content.

Scene and subject:
[SCENE_ELEMENTS_AND_RELATIONSHIPS]

Recurring motif:
[RECURRING_MOTIF, COUNT, DISTRIBUTION, AND SCREEN/CONTENT RULES]

Optional foreground anchor:
[FOREGROUND_ANCHOR OR NONE]. It occupies no more than [FRAME_SHARE] and serves only as [VISUAL_ROLE].

Style and medium:
[MEDIUM, ERA, GEOMETRY, MATERIALS, DETAIL LEVEL, RENDERING CHARACTER]

Composition:
[VIEWPOINT, FOCAL POINT, DEPTH LAYERS, LEADING LINES, NEGATIVE SPACE, SAFE ZONES]

Lighting and palette:
[TIME OF DAY, LIGHT QUALITY, SHADOW COLOR, DOMINANT COLORS, ACCENTS, SATURATION]

Mood:
[ATMOSPHERE]

Constraints:
[INVARIANTS, TEXT POLICY, BRAND POLICY, WATERMARK POLICY]

Avoid:
[NEGATIVE PROMPT]
```

## Reference-image role block

```text
Input-image roles:
- Image 1 is the edit target and structural base.
- Images 2–N are style and composition references only. Use them for [SPECIFIC STYLE RULES]. Do not copy their exact buildings, characters, signs, brands, or layout.
```

Name every input and give it one narrow role. Do not say only “use the references.”

## Focused iteration prompt

```text
Edit Image 1, the last user-approved wallpaper.

Change only:
[ONE FOCUSED CHANGE SET]

Preserve:
[COMPOSITION, SUBJECTS, PALETTE, LIGHTING, MATERIALS, MOTIFS, TEXT, AND OTHER INVARIANTS]

Reconstruct edited areas naturally. Do not add replacement objects unless requested. Save as a new version.
```

## Device adaptation prompt

```text
Create a true [TARGET_RATIO] [DEVICE] adaptation of Image 1. Recompose and extend the world for the new canvas; do not crop, stretch, rotate, letterbox, or paste the original image onto a background.

Keep [APPROVED STYLE, SUBJECT, FOCAL POINT, RECURRING MOTIF, PALETTE, AND MOOD]. Rebalance foreground scale, leading lines, skyline, negative space, and safe zones for [DEVICE]. Keep important objects away from system-crop edges.
```

## Subtle looping wallpaper prompt

```text
@Image1 is the exact first frame and defines the approved composition, architecture, object identities, palette, lighting, and camera.
@Image2 is the exact last frame and is identical to @Image1.

Use one fixed camera. Between the two frames, animate only [SCENE-NATIVE AMBIENT MOTIONS]. Keep movement slow, low-amplitude, continuous, and restorative: every moving element returns naturally to its starting state by the last frame.

Preserve all buildings, roads, screens, props, silhouettes, proportions, and screen graphics. No new objects, cuts, zooms, pans, aggressive parallax, melting geometry, duplicated elements, text mutation, flicker, subtitles, dialogue, music, or sound.
```

Use shorter prompts when the chosen model drops details. Preserve the subject, action, scene, lighting, camera, style, quality, and negative constraints in that order.
