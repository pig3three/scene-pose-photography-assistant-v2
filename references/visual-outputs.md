# Visual outputs

Generate only after text pose IDs are final.

## Pose boards

- 8 poses: Board A `P01–P04`, Board B `P05–P08`.
- 16 poses: Board A `P01–P04`, B `P05–P08`, C `P09–P12`, D `P13–P16`.
- Use a vertical 3:4 2×2 editorial guidance layout for each board.
- Include both the model and scene references in every call.
- Repeat: same real model identity, proportions, hair, outfit, shoes, accessories, scene geometry, light direction, and fixed pose IDs.
- Favor full-body readability when pose mechanics matter. Use tighter crops only when the locked plan calls for them.
- Allow only exact pose IDs and 2–4 word labels inside images.

## Scene map

Create one simplified elevated or overhead map based on the scene reference. Mark `P01–P08` or `P01–P16`, camera zones `C1–C4` as needed, subject-facing arrows, camera directions, key light, movement paths, and avoided zones. For 16 poses, use four colors keyed to chapters A–D to prevent clutter.

## Prompt invariant block

```text
MODEL LOCK: preserve the authorized reference person's recognizable face, age, skin tone, body proportions, hair, exact outfit silhouette/colors/materials, footwear, and accessories; no beautification or body reshaping.
SCENE LOCK: preserve the location geometry, surfaces, architecture, paths, anchors, and light direction; no invented furniture, props, rails, stairs, or buildings.
CONSISTENCY: same person, wardrobe, scene, lighting, pose IDs, realistic joints and hands, no extra people, no watermark.
```

If image generation is unavailable, return one fenced prompt per requested deliverable.