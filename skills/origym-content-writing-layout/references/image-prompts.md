# 配图生成与质感控制

## 工具顺序

1. 先冻结当前页面的视觉任务和用户约束。
2. 使用 `awesome-gpt-image-2` 选择一个最接近的构图或表现参考；记录参考名称、链接和实际采用的部分。它只提供灵感，不是生成器。
3. 使用 `imagegen` 生成或编辑。
4. 用原始项目文件逐张复核。需要读取本地图片时使用 `view_image`。
5. 失败时只调整对应提示词并重做失败资产，不顺手改变文案、人物或整组风格。

无法使用图片工具时，保存完整 prompts 并返回 `IMAGE_GENERATION_PENDING`，不得声称已经生成。

## 先写视觉判断

每张图生成前写一句：谁看、在哪里看、需要一眼读懂什么、采用什么媒介、情绪如何、哪些结构绝不能错。图片必须承担场景、动作或解释任务，不作无关填充。

多个页面可以并行生成，但每页仍要独立验收。同组保持人物、服装、媒介、色板、光线和器械空间一致。

## 唯一默认视觉

- 只使用最新摄影编辑首页／内页：暖白高留白页面、炭黑中文衬线大标题、浅米色圆角信息区、杏橙手绘标注和明亮自然的 ORIGYM 专业健身房实拍。
- 同组使用同一位成年中国女性：自然高马尾、白色圆领短袖训练上衣、浅灰训练长裤和包头训练鞋。
- 人物要同时可见本命感、力量感和少女野心：Softfit 式舒服自洽、先有性格再有风格；体态舒展但不摆拍，身形轻盈但有肌肉支撑，线条健康真实，目光坦荡进取。
- “少女野心”是成年女性的精神状态，不是生理年龄：明确成年，禁止未成年人、少女脸、幼态比例或儿童式大眼。
- 不使用旧 3×2 固定六宫格、半写实轻插画、鸭舌帽人物、夸张漫画、儿童卡通、3D 塑料渲染、医学解剖图或其他历史模板。只有用户对当前主题明确提出的新要求可以覆盖对应细节。
- 不迎合白瘦幼，不幼态化、媚态化或过度健美；不通过身材、体重和年龄焦虑塑造人物。

女生训练固定排版和禁改项以项目 `docs/ORIGYM-XIAOHONGSHU-COVER-INNER-TEMPLATE.zh-CN.md` 为准。

## 图与文字分工

文案锁定后，直接生成照片与中文排版一体的完整页面。提示词逐项列出页面全部文字并要求 verbatim；不允许额外文字、第三方品牌或水印。生成后逐字校对，错误时只重做或单点编辑失败页面。

## 训练动作提示词必填项

每个动作单独写清：

- 一名成年人物，固定服装与明确视角；
- 唯一动作和唯一静态阶段，不使用起止虚影；
- 头、胸廓、脊柱、骨盆、四肢和关节角度；
- 双手具体握住哪里，双脚或双膝具体落在哪里；
- 器械准确名称和必要结构：座椅、靠垫、胸垫、腿垫、握柄、横杆、钢索、滑轮、导轨、配重；
- 线缆和受力方向；
- 关键动作要领以及必须避免的代偿；
- 构图必须完整显示所有关键人体—器械接触点。

当器械几何容易出错时，先查第一方产品图片或说明，只把它作为结构参考，并在 prompt 中声明不复制品牌、文字、配色和广告视觉。

## 推荐提示词骨架

```text
Use case: infographic-diagram
Asset type: ORIGYM Xiaohongshu portrait page, integrated photography and typography
Information task: <读者一眼要看懂什么>
Scene: <ORIGYM 专业健身房区域与必要器械>
Subject: one adult Chinese woman, natural high ponytail,
plain white crew-neck short-sleeve training top, light-gray training leggings,
closed-toe training shoes; relaxed self-possession, healthy functional muscle lines,
an open and quietly ambitious gaze, mature natural proportions
Action state: <唯一静态动作阶段>
Body mechanics: <脊柱/骨盆/肩肘腕/髋膝踝关系>
Equipment geometry: <座椅/护垫/握柄/钢索/滑轮/导轨/配重连接>
Contacts: <双手、双脚、双膝、背/胸具体接触点>
Style/medium: bright natural professional gym photography integrated with restrained Chinese editorial layout
Color palette: warm off-white, charcoal, pale beige, restrained apricot orange, natural skin and fabric colors
Composition: <首页或内页；照片与信息区关系；原生竖版画幅；安全区>
Lighting: clean professional gym light, clear edges, readable equipment
Text (verbatim, and no other words): <列出全部标题、正文、数字、页码、TIP 与页脚>
Avoid: ghost poses, motion overlay, anatomical cutaway, highlighted muscles,
extra people, extra limbs, joint reversal, body/equipment penetration,
disconnected cable, mismatched machine parts, fisheye distortion,
anime eyes, youthful infantilization, male-gaze glamour pose, exaggerated waist-to-hip ratio,
body or age anxiety, extreme bodybuilding, fake Chinese, third-party brands, watermark,
CGI plastic skin, film grain, global paper texture
```

## 参考图规则

- 保留人物身份时才输入人物参考；保留器械结构时只输入经过核验的结构参考。
- 同一张参考存在人体、文字、颗粒或器械错误时，不把它作为强图像输入；只用文字提取可靠部分。
- 提示词明确列出“继承什么”和“不继承什么”。
- 使用 `awesome-gpt-image-2` 的可识别模板时，记录上游链接并遵守其许可与署名要求。

## 尺寸与后处理

- 记录请求画幅和工具实际返回的原生像素。
- 成品沿用实际原生画布；禁止为了所谓平台规格强制转成 1080×1440。
- 不二次拉伸、裁切或放大。若尺寸不满足阅读，需要重新生成合适构图，不用后处理牺牲质量。
- 每张逐页成图记录 SHA-256。

## 成图 QA

逐张检查：

- 人体比例、关节方向、动作阶段和关键接触点；
- 器械是同一台完整机器，钢索、滑轮、配重和护垫连接合理；
- 没有额外人物、肢体、穿模、伪字、其他品牌或水印；
- 高马尾、服装、人物身份、色板和健身房空间保持一致；
- 大面积背景干净，人物和器械边缘没有同频噪点、旧印刷颗粒或重度画布纹理；
- 全部中文、数字、标点和页码与锁定文案逐字一致，主体不会被标题或卡片裁掉。

任何关键人体或器械错误均为 blocker，必须重做。质感或构图问题按可读性判断为 blocker/important；不得用后期遮盖把失败图变成“通过”。
