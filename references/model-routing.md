# Model and execution routing

Read this reference before proposing or submitting image or video generation. Verify current tool documentation because model availability, limits, pricing, and supported resolutions change.

## Still-image routes

### Host-native image generation

Prefer this for ordinary concept generation and reference-guided edits when exact model and pixel controls are not required.

State clearly:

- whether the host exposes a model name;
- whether exact pixel dimensions can be selected;
- where outputs are saved by default;
- whether local reference files can be passed directly or must first be imported.

### Explicit API or CLI model path

Offer this when the user requires an exact model, quality setting, pixel size, mask, or output format and the environment provides a supported workflow. Do not create an ad-hoc SDK script when an official helper exists. Never request that the user paste a secret key into chat.

### Prompt-only versus reference-guided

- **Prompt-only:** more creative freedom and lower risk of copying the source layout; weaker style fidelity.
- **Reference-guided:** stronger control of palette, geometry, lighting, and rendering; explicitly limit references to style/composition roles.
- **Edit approved still:** best for focused corrections; repeat invariants and save a new version.

## Video routes

Choose by required capability, not by model popularity.

| Need | Prefer a model that supports |
|---|---|
| Seamless or near-seamless loop | exact first and last frames |
| Preserve an approved still | first-frame or first/last-frame image-to-video |
| Delivery-quality phone wallpaper | `9:16` and the requested verified resolution |
| Cheap motion test | lower-cost draft model, with an explicit warning that a final rerun can differ |
| Localized change to an existing clip | video edit/continuation rather than full regeneration |

When the same image is used as both boundary frames, describe a cyclic motion rather than an action that must reverse abruptly.

Do not silently choose a lower resolution. For example, if the current documentation says a “mini” or “fast” model is capped below the requested resolution, either use the full model or ask the user to accept the cap.

## Approval card

Before generation, show:

```text
Model/tool:
Generation mode: prompt-only / references / edit / first+last frame
Source assets:
Duration and aspect ratio:
Requested resolution and actual supported resolution:
Output format:
Destination path:
Cost/speed note:
Known limitation:
Recommendation:
```

Wait for the user's choice when routes materially differ or credits will be consumed.

## Cross-host fallback

If the active agent environment lacks an image or video generator:

1. complete the style analysis and prompt package;
2. state which capability is missing;
3. provide exact portable prompts and input roles;
4. do not report media as generated;
5. resume verification after the user returns an output.
