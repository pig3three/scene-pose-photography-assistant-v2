# Camera and lens adaptation

Use this reference whenever the user supplies a camera body, lens, focal length, aperture, or asks for equipment-aware posing.

## Required normalization

```text
机身品牌与准确型号：
传感器画幅：全画幅／APS-C／M4/3／其他／未确认
裁切系数：
镜头准确型号：
物理焦距：至少必填
最大光圈：至少必填
等效视角：
防抖：机身／镜头／无／未确认
最近对焦距离：已知值／未确认
对焦能力或限制：
```

- Treat names such as `佳能R-50` as likely `Canon EOS R50`, but confirm when the exact model affects output or the name is not unique.
- If the exact lens model is unavailable, require at least focal length and maximum aperture, for example `50mm F1.8`.
- Do not infer zoom range, stabilization, minimum focusing distance, sensor format, or autofocus features from a partial name.
- When exact specifications matter and internet access is available, verify them against the camera or lens manufacturer's official product/manual page. Clearly label any conclusion derived from those specifications.

## Optical adaptation

- Calculate full-frame-equivalent angle of view as physical focal length × crop factor. Do not call this a change in physical focal length.
- A normal or short-tele equivalent view needs more photographer-to-subject distance and may be unsuitable for tight alleys or very wide environmental portraits.
- A wide equivalent view permits closer environmental framing but exaggerates near/far scale; keep faces and limbs away from frame edges and avoid close low-angle distortion.
- A telephoto equivalent view compresses background and favors quieter, smaller gestures, profile, half-body, and layered backgrounds; verify enough backing distance exists.
- Treat maximum aperture as a ceiling, not a mandatory setting. Use wider apertures for subject separation only when focus tolerance suits the pose. Stop down for full-body diagonals, moving subjects, hands near or far from the face, layered scene storytelling, or multiple people.
- Respect minimum focusing distance. Never recommend a close framing that the lens cannot focus at.

## Pose and camera adaptation

- Fixed prime lens: move the camera physically and organize poses into distance blocks to reduce constant back-and-forth.
- Tight space with a long equivalent view: favor half-body, three-quarter, profile, still poses, and shooting along the longest scene axis.
- Motion with a large-aperture prime: keep movement parallel to the focus plane when possible; for toward-camera walking, recommend a smaller aperture, continuous autofocus, burst mode, and an appropriate shutter floor.
- Low light or no stabilization: reduce pose speed, use stable stance, raise shutter speed for subject motion, and treat stabilization as ineffective against subject movement.
- APS-C body with 50mm: recognize the tighter short-tele field of view; prioritize portraits and compressed layers rather than pretending it behaves like a 50mm full-frame environmental view.

## Per-pose equipment output

For every pose add:

- actual focal length used
- approximate photographer-to-subject distance or a clearly labeled on-site estimate
- aperture recommendation within the lens limit
- shutter-speed floor based on subject motion
- autofocus mode and focus target when useful
- one sentence explaining why the pose suits the locked camera and lens

Do not present guessed distances or exposure as guaranteed measurements. Mark them as starting points and tell the photographer to confirm framing and exposure on site.