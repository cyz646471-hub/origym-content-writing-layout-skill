# 配图提示词与质感控制

## 默认适用范围

本规范是 ORIGYM 公众号与小红书配图的默认生成和重生成规则。每次先按内容任务选择媒介，再组装提示词；图片进入评审或最终配置前，必须完成文末质感 QA。除非负责人对当前内容明确指定另一种质感，不继承旧图的全局颗粒、纸纹或复古滤镜。

## 先确定视觉判断

生成前写一句视觉判断，并明确画面用途、读者、情绪、信息任务和表面质感。ORIGYM 健康科普默认清楚、克制、可信，不把“编辑感”固定成复古印刷品。

先选一种媒介，并在同组图片中保持一致：

- 食物、器械、空间或真实物件本身承担信息时，优先自然编辑摄影；要求真实相机质感和生活尺度，不做广告棚拍、CGI 或 3D 产品渲染。
- 机制、抽象关系或无法直接拍摄的概念承担信息时，使用清晰的当代数字编辑插画。

沿用三个设计参数：

- `DESIGN_VARIANCE` 控制构图变化，健康科普通常取 4-6。
- `MOTION_INTENSITY` 对静态图固定为 1。
- `VISUAL_DENSITY` 控制主体数量，手机内容通常取 2-4。

## 分开描述色板与质感

不要把“纸张纹理编辑风格”写成一个整体风格词。它会同时放大颗粒、斑驳、旧印刷和铅笔噪点。

提示词必须分别声明：

- `Style/medium`：明确写自然编辑摄影或当代数字编辑插画，不用含混的“杂志感”代替媒介选择。
- `Color palette`：暖白、炭黑、自然食物色和单一克制橙色强调。
- `Materials/textures`：只保留物体真实材质，例如木纹、陶瓷、食物表面和织物；不要全图纹理层。
- `Texture control`：大面积背景使用连续、干净的色块；主体边缘清楚；纸感如需出现，只能极轻地留在空白背景，不能覆盖人物、食物、器械或文字区域。

如果参考图带有不想继承的颗粒，不把它作为图像输入。只用文字提取它的色板、构图或线条特点。参考图一旦作为输入，其表面质感通常比负面词更强。

## 推荐提示词骨架

```text
Use case: stylized-concept
Asset type: <具体投放位置>
Primary request: <这张图只解释一个认知任务>
Scene/backdrop: <场景>
Subject: <主体与必要对象>
Style/medium: <natural editorial photography with real camera detail and no CGI, or clean contemporary digital editorial illustration; choose one>
Composition/framing: <画幅、视角、裁切余量>
Lighting/mood: <光线与情绪>
Color palette: warm off-white, charcoal, natural subject colors, one restrained ORIGYM orange accent
Materials/textures: realistic local material detail only; smooth background color fields; no global texture overlay
Texture control: crisp subject edges; clean gradients and shadows; paper tooth, if any, is barely visible only in empty background areas and never crosses the subject
Constraints: <来源、人物、数字、文字、品牌等约束>
Avoid: film grain, digital noise, speckles, stippling, halftone dots, crosshatching, distressed paper, aged print, rough canvas, mottled wash, heavy pencil texture, chromatic noise, vignette, global texture overlay
```

不要同时堆叠 `paper texture`、`editorial grain`、`vintage print`、`film look`、`gouache texture` 等近义风格词。摄影提示词额外排除 CGI、3D render、塑料感和过度锐化；插画提示词额外排除照片拟真与全局画布纹理。一个清楚的媒介判断加一组可观察的质感约束就够了。

## 参考图策略

- 需要保留人物或产品身份时才把原图作为强参考，并明确哪些表面不能继承。
- 只想保留色板、构图或情绪时，优先用文字描述，不输入有缺陷的旧图。
- 同组图片用同一媒介、色板、光线和边缘处理保持一致；场景和构图可以变化。

## 质感 QA

逐张检查最终项目文件，而不是只看缩略图：

- 空白墙面、盘子、皮肤或食物上是否出现同频率噪点。
- 颗粒是否跨越不同材质，像覆盖在全图上的滤镜。
- 主体轮廓、器械细线和食物边缘是否被噪点打散。
- 手机裁切后，纹理是否比信息主体更醒目。

任一项失败就重生成同一认知任务。只调整媒介、参考图和质感控制，不顺手改人物、数字、构图含义或内容结论。旧版保留为版本化对照，新版通过检查后再更新资产清单与评审渲染。
