---
name: scene-pose-photography-assistant-v2
description: Combine two user-supplied photos—one authorized model reference and one scenery/location reference—to design a coherent set of 8 or 16 natural, shootable portrait poses. Use when the user wants identity-, body-, hair-, clothing-, footwear-, and accessory-aware scene placement, pose direction, camera guidance, photographer callouts, pose-board images, or a numbered scene map for a real person in a real location.
---

# Scene Pose Photography Assistant V2

Use an authorized model photo and a separate location photo to build a scene-aware portrait sequence. Preserve the real model's visible identity, proportions, hair, clothing, shoes, and accessories while adapting only pose, placement, expression, gaze, and camera relationship.

## Required workflow

1. Identify image roles explicitly: `MODEL REFERENCE` and `SCENE REFERENCE`. Never guess from upload order when roles are ambiguous.
2. Inspect both images before planning. Read [references/model-reference-lock.md](references/model-reference-lock.md) and publish a concise lock table.
3. Read [references/scene-analysis.md](references/scene-analysis.md) and diagnose usable zones, light, depth, anchors, hazards, and camera access.
4. Read [references/subject-profiles.md](references/subject-profiles.md). Treat ambiguous youthful subjects as minors unless adulthood is explicit.
5. Read [references/pose-planning.md](references/pose-planning.md) and [references/pose-counts.md](references/pose-counts.md). Generate exactly 8 or 16 poses; default to 8.
6. Read [references/photographer-directions.md](references/photographer-directions.md). Give one short, speakable Mandarin callout per pose when the user writes Chinese.
7. If images are requested, read [references/visual-outputs.md](references/visual-outputs.md), lock all pose IDs in text, then generate each board as a separate image using both references.
8. Audit identity, wardrobe, scene fidelity, physical feasibility, safety, pose diversity, and ID consistency.

## Input contract

Required:

- one clear model photo supplied by the user or otherwise authorized
- one scenery/location photo

Optional:

- portrait goal, mood, mobility limits, pose count (`8` or `16`), aspect ratio, available lenses, and requested visual outputs

If one photo is missing, ask for it. If both are present but their roles are unclear, ask one concise role question. Do not proceed from a model photo that is too cropped or obscured to support requested full-body or footwear-aware guidance; state what is invisible and request a clearer reference or mark those attributes unlocked.

## Defaults

- poses: 8
- mood: natural, relaxed, lived-in
- output crop: vertical 3:4
- lenses: 35 mm environment, 50 mm full/three-quarter, 85 mm half/close
- visuals for 8 poses: two 2×2 pose boards plus one scene map
- visuals for 16 poses: four 2×2 pose boards plus one scene map

## Pose output contract

For every pose output exactly:

```text
姿势 01｜简短动作名称
站位：
身体朝向：
腿部与重心：
手部动作：
头部与视线：
环境互动：
机位：
景别与焦段：
拍摄时机：
摄影师现场口令：“……”
```

Describe left and right from the subject's perspective when needed. Keep actions compatible with visible clothing, footwear, proportions, and mobility. Do not reshape the body, redesign garments, change shoes, add props, or beautify the person into a different identity.

## Image-generation rules

- Treat the model photo as an identity/appearance reference and the scene photo as a geometry/light reference.
- For every generated board, include both references. Repeat the same model lock, outfit lock, scene lock, and pose-ID block.
- Use one image-generation call per board or map. Never request all distinct deliverables as variants of one image.
- Preserve recognizable face, age, skin tone, body proportions, hair, clothing silhouette, materials, colors, shoes, and accessories to the extent visible.
- Preserve scene geometry and visible environmental anchors. Do not invent seating, rails, stairs, props, or architecture.
- Keep exact instructions outside the image; inside boards use only pose IDs and very short labels.
- If image generation is unavailable, return copy-ready prompts for each board and map.

## Safety and privacy

- Use real-person references only when user-supplied or authorized. Do not identify the person or infer sensitive traits.
- Never sexualize minors or ambiguous-age subjects. Use age-appropriate movement and framing.
- Do not recommend unsafe edges, traffic, water hazards, unstable structures, trespassing, or actions incompatible with footwear or mobility.
- Avoid body criticism. Describe visible constraints neutrally and only when they affect pose feasibility.

## Final response order

1. `图片角色与模特锁定`
2. `场景判断`
3. `拍摄路线`
4. `8 个美姿` or `16 个美姿`
5. `现场执行建议`
6. generated pose boards
7. generated scene map