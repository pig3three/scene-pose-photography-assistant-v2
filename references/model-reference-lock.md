# Model reference lock

Inspect only visible, photographically relevant attributes. Do not identify the person or infer ethnicity, health, personality, occupation, or other sensitive traits.

## Lock table

```text
图片角色：MODEL REFERENCE
授权状态：用户提供／用户确认授权
年龄类别：儿童／明确成年／老年／不明确
面部与身份：保持可识别性；不描述身份
身形比例：仅记录可见轮廓和拍摄约束
发型与发色：
上装：款式、颜色、材质、袖长
下装／连衣裙：款式、颜色、长度、轮廓
鞋履：款式、颜色、跟高；不可见则写“未锁定”
配饰：
遮挡或不可见项：
允许改变：姿势、站位、表情、视线、动作、机位
禁止改变：身份、年龄、身形、发型、服装、鞋履、配饰
```

## Fidelity rules

- Preserve visible face geometry, age, skin tone, body proportions, hair, garment construction, colors, materials, shoes, and accessories.
- Do not slim, enlarge, lengthen legs, change height, lighten skin, replace clothing, change hairstyle, or add makeup unless requested.
- Adapt pose mechanics to the outfit: limit stride in narrow skirts, avoid seated poses that distort structured garments, and respect heels or slippery footwear.
- If an attribute is not visible, mark it unlocked rather than inventing it.