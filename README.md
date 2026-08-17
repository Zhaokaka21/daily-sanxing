# daily-sansheng 日三省

> **吾日三省吾身** — *I daily examine myself on three points* (Confucius, *The Analects*)

**日结 · 日启 · 反思** — 一套经过长期实战打磨的个人日常三件套：归档、启动、复盘，闭环驱动个人与工作流进化。

A battle-tested personal daily workflow trio: **Close · Start · Reflect** — journal your work, boot your day, and continuously improve your system.

[English](#english) · [中文](#中文)

---

## 中文

### 这是什么

`daily-sansheng`（日三省）是一套**个人工作流自动化**方案，由三个 Claude Code / DeepSeek Harness 命令（skill）组成：

| 命令 | 触发词 | 作用 |
|------|--------|------|
| **日结** (`daily-close`) | 「日结」「归档今天」 | 把一天的工作归档到**领域自适应**的日志，并更新行动板 |
| **日启** (`daily-start`) | 「日启」「开工」 | 30 秒开工简报：行动板优先 + 中断点 + 今日建议 |
| **反思** (`daily-reflect`) | 「反思」「周反思」 | 14 天日志模式分析 + 每周外部学习，找出系统瓶颈 |

### 核心设计（与单日记类工具的区别）

| 特性 | daily-sansheng | 典型日记工具 |
|------|---------------|-------------|
| 领域自适应归档 | ✅ 自动匹配/新建领域目录 | ❌ 单一日记文件 |
| 多会话合并 | ✅ 同日多会话自动合并 | ❌ 每次一条 |
| 行动板状态机 | ✅ Now/Waiting/Next/Parked 驱动每日建议 | ❌ 无任务源 |
| 系统级反思 | ✅ 14 天日志模式分析（重复/时间/积压/健康度） | ❌ 只有记录 |
| 每周外部学习 | ✅ GitHub/网络抓新工具 → 闭环落地跟踪 | ❌ 只向内 |
| 双平台 | ✅ Claude Code 命令 + DSH skill | 通常单一平台 |
| 双工作区 | ✅ 可选跨区扫描（如日常+学术） | ❌ 单区 |

**一句话**：日记工具记录"发生了什么"；daily-sansheng 回答"今天做什么"（日启）、"今天做了什么"（日结）、"系统哪里该改进"（反思）——三个命令形成闭环。

### 快速开始

```bash
git clone https://github.com/<your-name>/daily-sansheng.git
cd daily-sansheng

# Claude Code
cp commands/*.md ~/.claude/commands/
# 或 DSH（DeepSeek Harness）
cp -r skill/daily-routine ~/.dsh/skills/
```

详细安装：见 [docs/install-claude-code.md](docs/install-claude-code.md) 和 [docs/install-dsh.md](docs/install-dsh.md)。

配置你的路径与领域：见 [docs/configuration.md](docs/configuration.md)。

### 目录结构

```
daily-sansheng/
├── commands/
│   ├── daily-start.md        # 日启：30 秒开工简报
│   ├── daily-close.md        # 日结：领域自适应归档 + 多会话合并
│   └── daily-reflect.md      # 反思：14 天模式分析 + 每周外部学习
├── skill/
│   └── daily-routine/        # DSH skill 版（自然语言触发）
├── templates/
│   └── daily-log-template.md # 日结归档模板
├── docs/
│   ├── install-claude-code.md
│   ├── install-dsh.md
│   └── configuration.md
└── examples/                 # 示例输出
```

### License

MIT

---

## English

### What is this

`daily-sansheng` is a personal workflow automation kit for **Claude Code** and **DeepSeek Harness** (DSH). The name comes from Confucius' *Analects*: "I daily examine myself on three points" (吾日三省吾身).

Three commands form a closed loop:

| Command | Trigger | What it does |
|---------|---------|--------------|
| **daily-close** (日结) | "日结" / "archive today" | Archive today's work into domain-aware journals, update the action board |
| **daily-start** (日启) | "日启" / "start work" | 30-second morning brief: action board first + breakpoints + today's suggestion |
| **daily-reflect** (反思) | "反思" / "weekly reflect" | 14-day journal pattern analysis + weekly external learning to find system bottlenecks |

### Why it's different from plain journaling tools

- **Domain-aware routing** — journals organize into domains automatically (new domains are created on the fly), not one flat file
- **Multi-session merge** — multiple sessions on the same day merge into one entry
- **Action-board state machine** — Now/Waiting/Next/Parked drives daily suggestions (journals are evidence, the board is the source of truth)
- **System-level reflection** — 14-day pattern analysis (repetition / time traps / backlog / config health) instead of just recording
- **Weekly external learning** — pulls new tools from GitHub/web, tracks adoption to closure
- **Two platforms, one config** — Claude Code commands + DSH skill sharing the same workspace conventions
- **Optional dual-workspace** — cross-workspace scanning (e.g. daily + research) with non-invasive handoff

### Quick start

```bash
git clone https://github.com/<your-name>/daily-sansheng.git
cd daily-sansheng

# Claude Code
cp commands/*.md ~/.claude/commands/
# or DeepSeek Harness (DSH)
cp -r skill/daily-routine ~/.dsh/skills/
```

Docs: [install-claude-code](docs/install-claude-code.md) · [install-dsh](docs/install-dsh.md) · [configuration](docs/configuration.md)

### License

MIT
