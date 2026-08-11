---
name: scene-pose-photography-assistant-v2
description: Combine an authorized model photo, a scenery/location photo, and optional camera-body and lens specifications to design 8 or 16 natural, shootable portrait poses. Use when the user wants identity- and wardrobe-aware scene placement, equipment-aware pose direction, working distance, framing, aperture, shutter, autofocus guidance, photographer callouts, pose-board images, or a numbered scene map for a real person in a real location.
---

# Scene Pose Photography Assistant V2

Use an authorized model photo and a separate location photo to build a scene-aware portrait sequence. Preserve the real model's visible identity, proportions, hair, clothing, shoes, and accessories while adapting only pose, placement, expression, gaze, and camera relationship.

## Required workflow

1. Identify image roles explicitly: `MODEL REFERENCE` and `SCENE REFERENCE`. Never guess from upload order when roles are ambiguous.
2. Inspect both images before planning. Read [references/model-reference-lock.md](references/model-reference-lock.md) and publish a concise lock table.
3. Read [references/scene-analysis.md](references/scene-analysis.md) and diagnose usable zones, light, depth, anchors, hazards, and camera access.
4. Read [references/subject-profiles.md](references/subject-profiles.md). Treat ambiguous youthful subjects as minors unless adulthood is explicit.
5. If camera or lens data is supplied, read [references/camera-lens-adaptation.md](references/camera-lens-adaptation.md), normalize the exact equipment, and publish an equipment lock. Require at least lens focal length and maximum aperture.
6. Read [references/pose-planning.md](references/pose-planning.md), [references/pose-components.md](references/pose-components.md), and [references/pose-counts.md](references/pose-counts.md). Generate exactly 8 or 16 poses; default to 8. Adapt placement, hand gesture, leg shape, weight, crop, motion, and camera distance to the subject, mood, scene, and locked equipment.
7. Read [references/photographer-directions.md](references/photographer-directions.md). Give one short, speakable Mandarin callout per pose when the user writes Chinese.
8. If images are requested, read [references/visual-outputs.md](references/visual-outputs.md), lock all pose IDs in text, then generate each board as a separate image using both references.
9. Audit identity, wardrobe, scene fidelity, equipment feasibility, physical feasibility, safety, pose diversity, and ID consistency.

## Input contract

Required:

- one clear model photo supplied by the user or otherwise authorized
- one scenery/location photo

Optional:

- portrait goal, mood, gesture style (`自然` / `俏皮` / `克制` / `混合`), mobility limits, pose count (`8` or `16`), aspect ratio, camera model, lens model, lens focal length, lens maximum aperture, and requested visual outputs

If one photo is missing, ask for it. If both are present but their roles are unclear, ask one concise role question. Do not proceed from a model photo that is too cropped or obscured to support requested full-body or footwear-aware guidance; state what is invisible and request a clearer reference or mark those attributes unlocked.

Camera and lens are optional as a pair. If the user requests equipment-aware guidance but provides an ambiguous body name, ask for the exact model. If a lens model is absent, require at least focal length and maximum aperture, such as `50mm F1.8`. Never silently substitute a different camera or lens.

## Defaults

- poses: 8
- mood: natural, relaxed, lived-in
- gesture style: mixed but natural; use playful signs only when compatible with the subject and brief
- output crop: vertical 3:4
- equipment when omitted: give focal-length categories rather than pretending a particular camera/lens is available
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
手势意图：自然／俏皮／克制／互动
头部与视线：
环境互动：
机位：
景别与焦段：
建议拍摄距离：
建议光圈：
快门与对焦：
拍摄时机：
摄影师现场口令：“……”
```

Describe left and right from the subject's perspective when needed. Keep actions compatible with visible clothing, footwear, proportions, and mobility. Do not reshape the body, redesign garments, change shoes, add props, or beautify the person into a different identity.

Treat hands, legs, and weight as three independent design decisions. Do not repeat generic relaxed arms or the same crossed-leg stance across the set. Include open palms, finger hearts, V signs, larger heart gestures, hair or garment interaction, wide or staggered stance, bent knee, crossed legs, heel lift, toe tap, and motion only when they fit the requested mood and subject profile. Never force playful gestures into a restrained portrait series.

When equipment is locked, do not recommend a focal length the photographer does not have. Distinguish optical capability from artistic choice: maximum aperture is a limit, not a mandatory setting. Prefer stopping down when full-body depth, multiple facial planes, movement, or scene readability requires it.

## Image-generation rules

- Treat the model photo as an identity/appearance reference and the scene photo as a geometry/light reference.
- For every generated board, include both references. Repeat the same model lock, outfit lock, scene lock, and pose-ID block.
- Use one image-generation call per board or map. Never request all distinct deliverables as variants of one image.
- Preserve recognizable face, age, skin tone, body proportions, hair, clothing silhouette, materials, colors, shoes, and accessories to the extent visible.
- Preserve scene geometry and visible environmental anchors. Do not invent seating, rails, stairs, props, or architecture.
- Keep exact instructions outside the image; inside boards use only pose IDs and very short labels.
- Make hands, fingers, feet, knee angles, and weight-bearing legs clearly readable in pose boards. Reject boards that collapse requested gestures into generic relaxed hands or repeat the same leg shape.
- If image generation is unavailable, return copy-ready prompts for each board and map.

## Safety and privacy

- Use real-person references only when user-supplied or authorized. Do not identify the person or infer sensitive traits.
- Never sexualize minors or ambiguous-age subjects. Use age-appropriate movement and framing.
- Do not recommend unsafe edges, traffic, water hazards, unstable structures, trespassing, or actions incompatible with footwear or mobility.
- Avoid body criticism. Describe visible constraints neutrally and only when they affect pose feasibility.

## Final response order

1. `图片角色与模特锁定`
2. `场景判断`
3. `器材锁定与拍摄约束`
4. `拍摄路线`
5. `8 个美姿` or `16 个美姿`
6. `现场执行建议`
7. generated pose boards
8. generated scene map