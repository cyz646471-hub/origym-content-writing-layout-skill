# ORIGYM Content Writing & Layout Skill

一个面向 Codex 的健身健康内容 Skill。它把每日选题雷达、证据分级、来源约束、自然中文、平台原生改写、读者反思、移动端排版判断和低颗粒配图提示词放在同一个 advisory 适配层中。

当前固定版本：`v0.3.0`。

## 适用场景

- 每日检索过去 24 小时内值得进入内容池的健身、健康、饮食、健身房故事、会员与行业信号。
- 对研究、专业解读、社区故事和行业材料分级，形成可追溯候选，并在明确选题后继续生成双平台评审稿。
- 把已确认的研究、媒体观察、社区故事或品牌事实写成微信公众号长文。
- 把同一母题重组为小红书 1080×1440 图文，而不是机械缩写公众号正文。
- 审阅中文稿件中的模板化 AI 表达、翻译腔、机械排比和假口语。
- 以目标读者处境反思平台初稿，记录可能感受、理解断点与行动阻力，并审慎采纳合适建议。
- 规划或审阅健康、训练与饮食内容的配图提示词，避免全局颗粒、旧印刷和塑料感。
- 对现有公众号 HTML、小红书逐页稿或移动端截图提供 advisory QA。

## 核心规则

1. 每日自动化默认使用 `radar-only`：只收集、分级、去重和排序，不为了日更凑数，也不为全部候选批量生成正文。
2. 人物、数字、经历、结果和品牌能力必须来自当前来源；未知信息保持 `null` 或进入人工核对项。
3. 研究证据、媒体观察、社区故事、品牌事实和编辑判断保持分类，公开帖子不能改写成品牌用户反馈。
4. 中文表达优先具体名词、动作和自然节奏，不靠“先说结论”“不是 A 而是 B”或网络热梗制造人味。
5. 平台初稿后从目标读者角度检查信任、理解、相关性和行动阻力；建议必须记录采纳、部分采纳或不采纳及理由。
6. 公众号和小红书共享事实与边界，但分别设计标题、开头、结构、视觉任务和行动。
7. 食物、器械和空间优先自然编辑摄影；抽象机制使用当代数字编辑插画。同组图片不混用媒介，不继承旧图的全局颗粒。
8. Skill 只提供 advisory。它不拥有内容状态、SQLite、审批、renderer、导出、登录或发布权限。

## 安装

使用 Agent Skills CLI：

```bash
npx skills add cyz646471-hub/origym-content-writing-layout-skill --skill origym-content-writing-layout -g
```

也可以手动安装：

```bash
git clone https://github.com/cyz646471-hub/origym-content-writing-layout-skill.git
mkdir -p ~/.codex/skills
cp -R origym-content-writing-layout-skill/skills/origym-content-writing-layout ~/.codex/skills/
```

重新打开 Codex 会话后即可调用。

## 使用示例

```text
使用 $origym-content-writing-layout，以 radar-only 模式检索过去 24 小时的健身健康、饮食、健身房故事和会员信号；研究与社区故事分开，不要为了凑数纳入弱内容。
```

```text
使用 $origym-content-writing-layout，把今日雷达中选定的候选以 develop-lead 模式继续做成公众号和小红书评审稿；完成读者反思，但不要批准、导出或发布。
```

```text
使用 $origym-content-writing-layout，把这份证据表写成公众号文章，并检查来源边界和中文 AI 味。
```

```text
使用 $origym-content-writing-layout，把当前正文改成小红书 3:4 图文。标题、封面和第一页不要重复；人物、数字、经历和结果不得超出来源。
```

```text
使用 $origym-content-writing-layout，为这篇健康科普规划三张配图提示词。不要全局颗粒、纸张噪点、复古印刷或 CGI 塑料感。
```

## 目录

```text
skills/origym-content-writing-layout/
├── SKILL.md
└── references/
    ├── chinese-copy.md
    ├── daily-health-radar.md
    ├── editorial-taste.md
    ├── image-prompts.md
    ├── reader-reflection.md
    ├── wechat.md
    └── xiaohongshu.md
```

`SKILL.md` 负责路由和权限边界；详细写作、视觉和平台规范按任务逐步加载。

## 可选协作 Skill

- [`self-media-platform-copywriting`](https://github.com/yanhua1010/self-media-content-workflow) 可作为平台初稿协作者，但不接入其总状态编排、delivery 或 publisher。
- [`xiaohongshu-title`](https://github.com/mengke-wang/xiaohongshu-ai-workbench) 只用于标题诊断和方向发散，不采用强制数量、人称或数字公式。

外部 Skill 的结果仍须通过本 Skill 的来源回归、自然中文与平台 QA。

## 版本与校验

- `VERSION` 保存当前语义版本。
- `CHECKSUMS.sha256` 固定 Skill 和参考文件。
- Git tag `v0.1.0` 对应首个冻结版本；`v0.2.0` 加入读者视角反思与建议采纳门；`v0.3.0` 将每日健身健康选题雷达与候选后的双平台 advisory 流程纳入 Skill。

任何规则变化都应更新版本、重新生成校验值，并重新运行 Skill 验证。
