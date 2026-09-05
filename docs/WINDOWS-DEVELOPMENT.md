# Windows 原生开发

2026-09-05 起，本项目的唯一日常开发目录为 `Z:/Projects/origym-content-writing-layout-skill`。从此目录运行、测试、提交和推送；迁移前的 Windows/WSL 目录不再作为开发入口。

Node.js 使用已安装的 Windows Node；Python 使用 `Z:/Tools/Python312/python.exe`，项目虚拟环境位于本项目内。Git 分支以当前检出和任务依据为准，不自动切回旧 main。

```powershell
Set-Location -LiteralPath 'Z:/Projects/origym-content-writing-layout-skill'
# Skill 维护源：skills/origym-content-writing-layout；安装到 Windows CODEX_HOME/skills。
```

迁移前状态集中保存在 `Z:/Project-Backups/origym-content-writing-layout-skill/previous-20260905`。Git 历史继续保留；业务数据库、凭据和运行数据不作为源码上传。旧报告中的路径是当时记录，当前路径以本文件为准。
