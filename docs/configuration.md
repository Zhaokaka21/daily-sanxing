# 配置指南

daily-sansheng 的三个命令 + skill 共用一套配置约定。所有配置都放在各命令文件顶部的「配置」表里，按你的环境修改即可，不需要改工作流逻辑。

## 路径配置

| 配置项 | 默认值 | 说明 |
|--------|--------|------|
| `LOG_ROOT` | `0-工作日志` | 领域日志根目录（相对工作区根） |
| `EXTRA_LOG_DIRS` | `运动日志` | 额外的扁平日志目录，多个用空格分隔；没有可留空 |
| `BOARD_FILE` | `ACTIVE_BOARD.md` | 行动板文件名（工作区根目录） |
| `REPORT_DIR` | `${LOG_ROOT}/复盘` | 反思报告与每周学习归档目录 |
| `CONFIG_FILE` | `CLAUDE.md` | 指南/路由配置文件（反思健康度检查对象） |
| `SECONDARY_WORKSPACE` | 空 | 可选：第二工作区绝对路径（如学术工作区），用于双区反思与任务引导 |
| `HANDOFF_FILE` | `CODEX_HANDOFF.md` | 可选：外部 Agent（如 Codex）交接文件 |

## 领域关键词表

`daily-close.md` 的 `DOMAIN_KEYWORDS` 决定"对话主题 → 领域目录"的路由。按你的领域修改：

```markdown
| 关键词 | → 领域目录 |
|--------|-----------|
| 运动、健身、跑步、减脂 | 运动日志/ |
| 投资、理财、记账 | 0-工作日志/ |
| 读书、笔记、书评 | 0-工作日志/读书/ |
```

规则：
- 匹配按**关键词命中**，多个关键词命中时取最具体的领域；
- 匹配不上 → 命令会询问用户新建领域，并提示把新关键词加进表里；
- 同一关键词不要映射到两个目录，避免路由歧义。

## 双区模式（可选）

适合有两个工作区（如日常 + 学术）的用户：

1. 在 `daily-reflect.md` 配置 `SECONDARY_WORKSPACE`（绝对路径，如 `D:/research`）；
2. 双区反思时用 `/daily-reflect 双区`，会追加扫描 `SECONDARY_WORKSPACE/日志/工作日志/*/`；
3. 跨区发现只**挂账**（在报告里列出，最多在对方区行动板写一行指针），不在本会话改对方区文件；
4. `daily-close.md` 配置同一路径后，属于该区的主题会自动引导去那边归档。

## 外部学习引擎（可选）

每周反思时扫 GitHub/网络找新工具。按需配置：

- `LEARNING_STATE_FILE`：你的学习计划状态文件（如 `.skill-state.json`），包含 `current_phase` 字段时，外部学习按主线定位关键词；不配置则只跑工作线快讯；
- `SEARCH_METHOD`：`web`（通用联网搜索）/ `github`（GitHub Trending）/ 自定义。

## Token 审计（可选）

- `SESSION_REPORT_DIR`：session-report 类 token 用量工具的目录。配置后反思会拉取 14 天量化数据；不配置则只做静态检查（指南行数、Agent 数、MCP 数等），不影响其他功能。

## 安装后自检清单

1. 三个命令文件已放入正确的命令目录（见 `install-claude-code.md` / `install-dsh.md`）；
2. 在真实工作区建好 `LOG_ROOT` 目录与 `BOARD_FILE`；
3. 跑一次 `/daily-start`：应输出行动板 + 上次进度简报；
4. 跑一次 `/daily-close`：应能归档当前对话到领域日志；
5. 跑一次 `/daily-reflect`：应产出反思报告（至少内部日志分析部分）。
