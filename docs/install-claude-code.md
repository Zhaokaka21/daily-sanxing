# 安装指南 — Claude Code

daily-sansheng 以 **slash command** 形式安装到 Claude Code，两条命令就能用。

## 安装

```bash
# 1. 克隆仓库
git clone https://github.com/Zhaokaka21/daily-sansheng.git
cd daily-sansheng

# 2. 复制三个命令到 Claude Code 全局命令目录
mkdir -p ~/.claude/commands
cp commands/daily-start.md  ~/.claude/commands/日启.md
cp commands/daily-close.md  ~/.claude/commands/日结.md
cp commands/daily-reflect.md ~/.claude/commands/反思.md

# 3. （可选）复制模板
mkdir -p ~/.claude/skills/daily-routine
cp templates/daily-log-template.md ~/.claude/  # 或放到你工作区的日志目录
```

> 命令文件名可用中文（`日启.md`）或英文（`daily-start.md`），触发时输入 `/日启` 或 `/daily-start`。推荐中文名，和日常工作流语言一致。

## 初始化工作区

在你要使用的工作区根目录创建基础结构：

```bash
mkdir -p 0-工作日志 运动日志
touch ACTIVE_BOARD.md
```

`ACTIVE_BOARD.md` 初始内容：

```markdown
# 行动板

## Now（进行中）
- （空）

## Waiting（等待中）
- （空）

## Next（接下来）
- （空）

## Parked（暂缓）
- （空）
```

## 验证

在 Claude Code 会话中输入：

1. `/日启` → 应输出 30 秒启动简报（此时各领域无日志，输出"新领域/沉寂"状态即可）；
2. `/日结` → 应把当前对话归档到领域日志；
3. `/反思` → 应产出 14 天日志分析报告（初期日志少，报告会相应精简）。

## 可选：让新会话自动日启

在 `~/.claude/CLAUDE.md` 或工作区 `CLAUDE.md` 中加入：

```markdown
每次新会话开始，如果用户没有明确任务，先运行 /日启 获取上下文。
```

## 卸载

```bash
rm ~/.claude/commands/日启.md ~/.claude/commands/日结.md ~/.claude/commands/反思.md
```

工作区里已生成的日志和行动板不受影响。

## 常见问题

**Q: 命令不触发？**
确认文件在 `~/.claude/commands/` 下且扩展名是 `.md`；重启会话后生效。

**Q: 想用英文命令名？**
复制时用英文文件名即可（`daily-start.md`），触发 `/daily-start`。

**Q: 路径不对？**
所有路径配置在各命令文件顶部的「配置」表，改成你的实际路径。
