# ORIGYM Content Writing & Layout Skill

面向 Codex 的 ORIGYM 小红书内容生产 Skill。用户选题优先，健康 Obsidian、每日情报和网络检索负责补充；随后完成去 AI 味文案、最新视觉生图、3×2 中文卡片排版、贯穿式复核和 Z 盘交付。

当前版本：`v0.6.0`。

## 当前唯一流程

1. 意图确定；
2. 选题信息补充；
3. 小红书文案与 hashtags；
4. `awesome-gpt-image-2` 构图参考＋`imagegen` 生图；
5. 最新 3×2 中文卡片排版；
6. 受众、来源、人体和器械持续复核；
7. Z 盘 review/final 素材管理。

公众号、独立漫画、旧通用小红书 renderer、固定 1080×1440、Signal Poster、Studio Journal 和外部协作 Skill 均不在默认路由中。

## 最新视觉

- 半写实人物＋轻插画质感；
- 米白、炭黑、砖红；
- ORIGYM 专业健身房；
- 3×2 六宫格和真实中文；
- 成年中国女性、无标鸭舌帽、舒适合体运动背心、运动短裤和包头训练鞋；
- 松弛自洽的本命感、健康有力的力量感、坦荡进取的少女野心；
- 不使用白瘦幼、幼态大眼、媚态摆拍、夸张腰臀、解剖图、虚影或身材/年龄焦虑；
- 保留原生画布，不拉伸、裁切或放大。

## 当前本地入口

- 健康 Obsidian：`/home/ethan/CHI-Papers/04-健康情报`
- 每日健康任务：`/home/ethan/projects/daily-arrangement/automation/health-obsidian-prompt.md`
- 内容项目：`/home/ethan/projects/content-creation-workflow`
- Z 盘：`/mnt/z/内容产出输出`
- 图片：`awesome-gpt-image-2` ＋ `imagegen`
- 排版：每个主题基于固定六宫格建立原生 HTML/CSS renderer
- QA：Playwright、原图目视检查和 SHA-256

详细入口见 `references/local-tools-and-files.md`。

## 运行模式

- `radar-only`：没有确定主题时只生成候选。
- `develop-lead`：完成用户已定主题的小红书评审包，停在 `FINAL_APPROVAL_REQUIRED`。
- `release-current`：只封装已明确批准的当前绑定，不登录或发布。

## 核心边界

- 用户的主题、模板和修改意见优先；搜索不能另起方向。
- 研究、专业解读、社区讨论、品牌事实和编辑判断保持分类。
- 不虚构人物、经历、数字、效果、账号表现或门店能力。
- 人体、动作或器械结构错误必须重做图片，不能用裁切和文字遮盖。
- 任何来源、文案、图片、模板或 renderer 变化都使旧批准失效。
- Skill 不拥有 SQLite 状态，不登录、不上传、不发布。

## 安装

```bash
npx skills add cyz646471-hub/origym-content-writing-layout-skill --skill origym-content-writing-layout -g
```

本机维护源：`/home/ethan/projects/origym-content-writing-layout-skill/skills/origym-content-writing-layout`
安装副本：`/home/ethan/.codex/skills/origym-content-writing-layout`

修改后同步两者并运行 Skill 验证。

## 目录

```text
skills/origym-content-writing-layout/
├── SKILL.md
└── references/
    ├── chinese-copy.md
    ├── daily-health-radar.md
    ├── editorial-taste.md
    ├── full-content-workflow.md
    ├── image-prompts.md
    ├── local-tools-and-files.md
    ├── reader-reflection.md
    └── xiaohongshu.md
```

## 版本与校验

- `VERSION` 保存语义版本；
- `CHECKSUMS.sha256` 固定 Skill 和参考文件；
- `v0.6.0` 停用旧工作流，将生产范围收束为最新视觉下的小红书单平台，并补充本命感、力量感和少女野心人物规范。

规则变化后更新版本、重新生成校验值，并运行 `quick_validate.py`。
