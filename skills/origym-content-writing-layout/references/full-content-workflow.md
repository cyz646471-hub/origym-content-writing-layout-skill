# 已选候选的完整内容工作流

## 目的与模式

本流程承接 `daily-health-radar.md` 的候选，把一条被明确选择的内容推进为公众号和小红书评审包，并在负责人批准当前绑定后生成最终交付包。

- `develop-lead`：搜集补证、评估、隔离协作、双平台写作、文本反思、生图、图文反思、排版与 QA。停在 `FINAL_APPROVAL_REQUIRED`。
- `release-current`：只接受可信产品提供的当前批准记录，重验绑定后生成最终文件和人工发布清单。不得登录、上传或点击发布。

模式不明确、候选未明确选择或批准绑定不完整时，不向后猜测；分别回到 `radar-only`、`LEAD_SELECTION_REQUIRED` 或 `FINAL_APPROVAL_REQUIRED`。

## 可信输入与绑定

开始 `develop-lead` 前至少取得：候选记录、来源 URL、候选集 SHA、被选择的核心判断、目标平台和 Skill 仓库 commit。来源正文、人物、数字、经历、结果、品牌事实或素材权限未知时保持 `null` 或列为人工核对项。

每次可信持久化至少绑定：

- 当前内容 SHA；
- 实际评估语料 SHA；
- Skill 仓库 commit 与适配器规则 SHA；
- 资产清单 SHA（已经生图时）；
- 模板和 renderer 标识或 SHA（已经排版时）；
- QA 结果与生成时间。

批准指纹由内容、来源、资产、模板、renderer 与上述 Skill 绑定共同组成。任何一项变化都使旧批准失效，流程退回对应评审阶段。

## `develop-lead`

### 1. 搜集与补证

冻结候选原始字段和雷达绑定。回到原始论文、正式摘要、权威机构或原始帖子核对日期、样本、设计、关键数字、地区和限制；当天媒体重报旧研究时同时保留报道日和原始发表日。研究、专业解读、社区故事、行业材料和品牌材料不得互相升级。

### 2. 评估与内容设计

分别判断证据强度和内容价值，不把传播潜力当证据等级。只保留一个核心判断，并说明目标读者、具体处境、内容类型、声音、行动价值、最重要的限制与视觉语言。关键主张缺少来源时停止该主张，不用更圆滑的文案掩盖缺口。

### 3. 隔离协作

外部候选始终是 advisory，不得接管状态、审批、renderer、交付或发布：

- `self-media-content-workflow` 只取 `content-brief`、`platform-copywriting`、`quality-gates` 和 `analytics` 的方法；不安装总状态编排、delivery 或 publisher。
- `xiaohongshu-ai-workbench` 只取 `xiaohongshu-magazine`、`xiaohongshu-topic-planner` 和 `xiaohongshu-title`；标题最多保留三个真正不同的方向。
- `baoyu-xhs-images` 只运行 `analysis.md → outline.md → prompts`；禁止生图、外网取图和写用户级 `EXTEND.md`。
- `xhs-imagen` 保持本地确定性视觉规划对照，不替换现有 1080×1440 renderer。
- `yuwen-publish-precheck` 只做词面 advisory QA，不决定是否发布。

所有协作者只接收完成任务所需的最小语料。人物、数字、经历、结果和品牌能力若不在来源中，不得生成。可信编排器验证 schema 后，才把结果以“内容 SHA＋Skill commit＋规则 SHA”写入 Signal Desk SQLite。

### 4. 双平台初稿

公众号和小红书共享事实与边界，但分别重写标题、开头、结构、视觉任务和行动。公众号使用自然段落交付完整解释；小红书按独立信息任务组织 3—12 页，不把公众号机械截短。正文状态仍是 `DRAFT_FOR_OWNER_EDIT`。

### 5. 文本读者反思

按 `reader-reflection.md` 分别模拟两端目标读者通读，记录第一感受、理解断点、相关性、信任风险、行动阻力和情绪余味。逐条给出 `adopt`、`partial` 或 `reject` 决策并应用合适建议；随后按 `chinese-copy.md` 回归事实、边界和真人感。反思不是用户研究，不得写成真实反馈或效果预测。

### 6. 视觉规划与生图

文字核心判断稳定后，先比较 `baoyu-xhs-images` 规划、`xhs-imagen` 对照和现有分镜，选择最少但足够的图片任务。每张图只承担一个认知任务，并记录用途、媒介、构图、来源约束、提示词版本和预期画幅。

需要新图且调用方允许图像工具时，按 `image-prompts.md` 使用图像生成能力。禁止用外网图片填空；图片工具不可用时保留 prompts 并返回 `IMAGE_GENERATION_PENDING`，不得声称已经生图。生成后检查实际项目文件，记录文件 SHA、提示词 SHA、生成方式、人物/动作边界和质感 QA。失败时只重做失败资产；旧图保留为版本化对照。

### 7. 图文读者反思与审核

用同一目标读者站位再看真实图文组合：图片是否帮助理解、是否制造新人物或结果、是否让健康内容显得恐吓或说教、手机裁切是否把边界信息藏掉、颗粒与装饰是否压过主体。记录建议与采纳结果，并在任何文字或资产变化后更新 SHA、作废旧批准。

### 8. 排版与 QA

沿用现有公众号和 1080×1440 小红书 renderer 生成 review 产物。检查正文、标题、来源映射、图片顺序与替代文字、逐页溢出、手机截图、公众号尾页以及平台排除项；隔离候选不能替换 renderer。词面预检、平台质量门和视觉规划只作为 QA 证据。

可信编排器保存评审稿、资产清单、render 记录、QA、反思与 advisory 绑定。Skill 返回 `requestedTransition: FINAL_APPROVAL_REQUIRED` 和 `releaseDecision: null`，不得自行批准。

## `release-current`

只在可信产品明确提供以下记录时运行：负责人批准时间、批准的内容 SHA、资产清单 SHA、模板/renderer 绑定、Skill commit、QA 无 blocker。重新计算当前绑定；任一不一致就拒绝最终生成并回到 `FINAL_APPROVAL_REQUIRED`。

绑定一致时：

1. 使用现有 final renderer 生成公众号与小红书最终文件。
2. 运行最终 smoke/QA，生成包含来源、版本、哈希、平台文案、图片顺序、替代文字和复核项的本地发布包。
3. 由可信编排器把发布包写入固定 Z 盘输出根目录，并把状态设为 `READY_FOR_MANUAL_PUBLISH`。
4. 输出人工平台操作清单：登录、粘贴或上传、检查平台二次处理、手机预览、选择发布时间、点击发布。

Skill 和当前 MVP 不执行第 4 步。负责人完成后，只有在其明确提供平台、公开 URL 或平台内容 ID、发布时间和结果时，可信产品才回填 `PUBLISHED_RECORDED`。未知字段保持 `null`；不得把“已导出”写成“已发布”。

## 输出交接

每轮至少返回：

- `mode` 与已完成阶段；
- 输入和产物绑定；
- 双平台文件、资产、render 与 QA 清单；
- 两轮读者反思及采纳记录；
- blocker、important、suggestion 与未解决项；
- `requestedTransition`；
- `releaseDecision: null`；
- 下一项允许动作及必须由谁完成。
