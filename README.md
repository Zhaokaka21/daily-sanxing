# daily-sanxing 日三省

> **吾日三省吾身** — *I daily examine myself on three points* (Zengzi, *The Analects*, Book 1 — Xue'er)
>
> 注音：**省读 xǐng（反省），不读 shěng**——项目名 `sanxing` 即取「三省吾身」之音。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![CI lint](https://github.com/Zhaokaka21/daily-sanxing/actions/workflows/lint.yml/badge.svg)](https://github.com/Zhaokaka21/daily-sanxing/actions/workflows/lint.yml)
[![GitHub stars](https://img.shields.io/github/stars/Zhaokaka21/daily-sanxing)](https://github.com/Zhaokaka21/daily-sanxing)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-ready-8A2BE2)](docs/install-claude-code.md)
[![DeepSeek Harness](https://img.shields.io/badge/DSH-ready-4D6BFE)](docs/install-dsh.md)

**日结 · 日启 · 反思** — 一套经过长期实战打磨的个人日常三件套：归档、启动、复盘，闭环驱动个人与工作流进化。

A battle-tested personal daily workflow trio: **Close · Start · Reflect** — journal your work, boot your day, and continuously improve your system.

[中文](#中文) · [English](#english)

---

## 中文

### 为什么叫「日三省」

《论语·学而》：「**吾日三省吾身**——为人谋而不忠乎？与朋友交而不信乎？传不习乎？」这句话出自**曾子**（曾参，孔子弟子），不是孔子本人的话。曾子每天从三个问题反省自己。

这套工具把「三省」现代化成三个日常追问，由 AI 助手替你执行：

| 追问 | 命令 | 频率 |
|------|------|------|
| **今天做什么？** | 日启 `daily-start` | 每天开工 |
| **今天做了什么？** | 日结 `daily-close` | 每天收工 |
| **系统哪里该改进？** | 反思 `daily-reflect` | 每周一次 |

三个命令形成**闭环**：日启从行动板出发 → 工作 → 日结归档并更新行动板 → 反思从 14 天日志里找出系统瓶颈 → 优化建议回到行动板。

### 这是什么

`daily-sanxing`（日三省）是一套**个人工作流自动化**方案，同一份内容同时支持 **Claude Code**（slash command）和 **DeepSeek Harness / DSH**（skill，自然语言触发）：

| 命令 | 触发词 | 作用 |
|------|--------|------|
| **日结** (`daily-close`) | 「日结」「归档今天」 | 把一天的工作归档到**领域自适应**的日志，并更新行动板 |
| **日启** (`daily-start`) | 「日启」「开工」 | 30 秒开工简报：行动板优先 + 中断点 + 今日建议 |
| **反思** (`daily-reflect`) | 「反思」「周反思」 | 14 天日志模式分析 + 每周外部学习，找出系统瓶颈 |

### 特性亮点

1. **领域自适应归档** — 日志按领域自动路由，新领域自动创建目录，不依赖手工分类；
2. **多会话自动合并** — 同一天多个会话自动合并进同一篇日志，不会碎片化；
3. **行动板状态机** — `Now / Waiting / Next / Parked` 四级状态驱动每日建议（日志是证据库，行动板才是任务真源）；
4. **系统级反思** — 14 天日志模式分析：重复模式 / 时间陷阱 / 积压任务 / 指南健康 / Token 审计，每个发现都引用具体日志，不靠感觉；
5. **每周外部学习** — 每周从 GitHub / 网络抓新工具，映射回学习主线与工作线，带「已落地 / 未落地」跟踪列闭环；
6. **双平台一套内容** — Claude Code 命令与 DSH skill 共用同一套配置约定和工作区规范；
7. **双工作区非侵入** — 可选跨区扫描（如日常 + 学术），跨区发现只挂账一行指针，不越区改文件。

### 与日记工具的区别

| 特性 | daily-sanxing | 典型日记工具 |
|------|---------------|-------------|
| 领域自适应归档 | ✅ 自动匹配/新建领域目录 | ❌ 单一日记文件 |
| 多会话合并 | ✅ 同日多会话自动合并 | ❌ 每次一条 |
| 行动板状态机 | ✅ Now/Waiting/Next/Parked 驱动每日建议 | ❌ 无任务源 |
| 系统级反思 | ✅ 14 天日志模式分析（重复/时间/积压/健康度） | ❌ 只有记录 |
| 每周外部学习 | ✅ GitHub/网络抓新工具 → 闭环落地跟踪 | ❌ 只向内 |
| 双平台 | ✅ Claude Code 命令 + DSH skill | 通常单一平台 |
| 双工作区 | ✅ 可选跨区扫描（如日常+学术） | ❌ 单区 |

**一句话**：日记工具记录"发生了什么"；daily-sanxing 回答"今天做什么"（日启）、"今天做了什么"（日结）、"系统哪里该改进"（反思）——三个命令形成闭环。

### 快速开始

```bash
git clone https://github.com/Zhaokaka21/daily-sanxing.git
cd daily-sanxing

# Claude Code：复制三个命令到全局命令目录
cp commands/daily-start.md  ~/.claude/commands/日启.md
cp commands/daily-close.md  ~/.claude/commands/日结.md
cp commands/daily-reflect.md ~/.claude/commands/反思.md

# 或 DeepSeek Harness（DSH）：复制 skill 到技能目录
mkdir -p ~/.dsh/skills
cp -r skill/daily-routine ~/.dsh/skills/
```

详细安装与验证：见 [docs/install-claude-code.md](docs/install-claude-code.md) 和 [docs/install-dsh.md](docs/install-dsh.md)。
配置你的路径与领域：见 [docs/configuration.md](docs/configuration.md)。

### 输出示例

**日启（30 秒开工简报）**——只读操作，行动板优先：

```
🎯 当前行动板
Now: 《思考，快与慢》第 4 章阅读（昨天中断点）
Waiting: 无

📍 上次进度
• 读书: 3/38 章读完，锚定效应概念没吃透，12 张卡片已整理
• 运动: 5 公里跑 28 分钟完成，下周目标 27 分

💡 今日建议
先读第 4 章（约 40 分钟），读后套卡片模板做卡，顺便把锚定效应的例子补上。

🔴 待办提醒
- [ ] 重读"锚定效应"章节
- [ ] 用卡片模板补第 4 章
```

**日结（领域自适应归档）**——归档日志 + 更新行动板，同一天多会话自动合并：

```
# 📚 读书 工作日志 — 2026年01月15日

## 📌 今日总览
> 读完《思考，快与慢》第 1-3 章并完成章节笔记；下午把笔记整理成 12 张知识卡片……

## 🔄 会话 #1 — 14:30
### 1. 本次状态（3句话）
> 读完第 1-3 章（系统 1/系统 2、认知放松、确认偏误）。卡在"锚定效应"没完全理解。
### 4. 待办事项
#### 🔴 高优先级
- [ ] 重读"锚定效应"章节 — 概念没吃透
```

**反思（14 天模式分析 + 每周外部学习）**——每个发现都引用具体日志：

```
## 🔄 发现的重复模式
1. **[「下次读」从未被读]** — 读书日志 3 次标了"下次读第 X 章"，但下一次会话都从别处开始。
   - 出现次数：3 次（1/12、1/14、1/16）
   - 建议：在行动板 Now 固化"下一章 = 待办"，日启时优先推。

## 🌐 每周外部学习
1. [Polars 2.0] — 大数据处理提速 3-5 倍 — 🎯 主线（Phase 1）
   - 优先级：🔴 马上试 ｜ 落地跟踪：下周验证
```

完整示例见 [examples/](examples/)（`daily-start-example.md` / `daily-close-example.md` / `daily-reflect-example.md`）。

### 工作原理

```
                     ┌─────────────────────────────────────┐
                     │           ACTIVE_BOARD.md           │
                     │     Now / Waiting / Next / Parked   │
                     └──────▲──────────────────▲───────────┘
                            │ 读取             │ 更新
  日启 daily-start          │                  │        日结 daily-close
  30 秒开工简报 ─────────────┘                  └──────────── 领域日志归档
  (只读)                                          (归档+合并+更新行动板)
                            ▲
                            │ 建议回写
  反思 daily-reflect ───────┘
  14 天日志模式分析 + 每周外部学习
```

- **日启**：读行动板 + 各领域最新日志的标题和中断点 → 输出 30 秒简报（不写任何文件）；
- **日结**：按领域路由归档当前会话 → 追加/合并到当日日志 → 更新行动板状态；
- **反思**：扫 14 天日志 → 模式识别（重复/时间/积压/健康度）→ 每周外部学习 → Top 3 建议回写行动板。

### 目录结构

```
daily-sanxing/
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
├── examples/                 # 三个命令的真实输出示例
└── .github/workflows/lint.yml # CI：frontmatter + 内部链接检查
```

### 常见问题

**Q: 「日启」没反应？**
Claude Code 版检查文件是否在 `~/.claude/commands/` 且重启会话；DSH 版确认 `skill/daily-routine/SKILL.md` 存在且重启 DSH。

**Q: 命令不触发？**
SKILL.md / 命令文件的 `description` 定义了触发词，默认覆盖「日结」「日启」「反思」「归档今天」「开工」等；想加触发词直接编辑 description。

**Q: 路径不对？**
所有路径配置在各命令文件顶部的「配置」表和 [docs/configuration.md](docs/configuration.md)，改成你的实际路径即可，不需要改工作流逻辑。

**Q: 想用英文命令名？**
复制时用英文文件名即可（`daily-start.md`），触发 `/daily-start`。

**Q: 会误删我的日志吗？**
不会。日结只追加/合并，日启只读，反思只生成报告。卸载命令只删三个命令文件，日志和行动板不受影响。

### 贡献

欢迎 Issue 和 PR！本项目很小，改动前请先开 Issue 讨论。CI（lint）会检查命令 frontmatter 和内部链接，提交前本地跑一下：

```bash
# 本地模拟 lint（需 bash 环境）
for f in commands/*.md skill/daily-routine/SKILL.md; do
  head -1 "$f" | grep -q '^---$' && grep -q '^description:' "$f" && echo "OK: $f"
done
```

### License

[MIT](LICENSE) © daily-sanxing contributors

---

## English

### What is this

`daily-sanxing` (日三省) is a personal workflow automation kit for **Claude Code** and **DeepSeek Harness** (DSH). The name comes from *The Analects* (Book 1, *Xue'er*), where **Zengzi** (Zeng Shen, a disciple of Confucius) says: "I daily examine myself on three points" (吾日三省吾身). Note the character 省 is pronounced **xǐng** (self-examination), hence the spelling *sanxing*.

Three commands form a closed loop:

| Command | Trigger | What it does |
|---------|---------|--------------|
| **daily-close** (日结) | "日结" / "archive today" | Archive today's work into domain-aware journals, update the action board |
| **daily-start** (日启) | "日启" / "start work" | 30-second morning brief: action board first + breakpoints + today's suggestion |
| **daily-reflect** (反思) | "反思" / "weekly reflect" | 14-day journal pattern analysis + weekly external learning to find system bottlenecks |

### Highlights

- **Domain-aware routing** — journals organize into domains automatically (new domains are created on the fly), not one flat file
- **Multi-session merge** — multiple sessions on the same day merge into one entry
- **Action-board state machine** — Now/Waiting/Next/Parked drives daily suggestions (journals are evidence, the board is the source of truth)
- **System-level reflection** — 14-day pattern analysis (repetition / time traps / backlog / config health) with every finding cited to real logs
- **Weekly external learning** — pulls new tools from GitHub/web, tracks adoption to closure
- **Two platforms, one config** — Claude Code commands + DSH skill sharing the same workspace conventions
- **Optional dual-workspace** — cross-workspace scanning (e.g. daily + research) with non-invasive handoff

### Quick start

```bash
git clone https://github.com/Zhaokaka21/daily-sanxing.git
cd daily-sanxing

# Claude Code
cp commands/daily-start.md  ~/.claude/commands/日启.md
cp commands/daily-close.md  ~/.claude/commands/日结.md
cp commands/daily-reflect.md ~/.claude/commands/反思.md

# or DeepSeek Harness (DSH)
mkdir -p ~/.dsh/skills
cp -r skill/daily-routine ~/.dsh/skills/
```

Docs: [install-claude-code](docs/install-claude-code.md) · [install-dsh](docs/install-dsh.md) · [configuration](docs/configuration.md)
Examples: [examples/](examples/)

### Contributing

Issues and PRs welcome. Open an issue first for non-trivial changes — the lint CI checks command frontmatter and internal links.

### License

[MIT](LICENSE) © daily-sanxing contributors
