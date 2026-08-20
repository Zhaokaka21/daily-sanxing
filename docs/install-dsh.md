# 安装指南 — DeepSeek Harness（DSH）

daily-sanxing 以 **skill** 形式安装到 DSH，支持自然语言触发：直接说「日启」「日结」「反思」即可。

## 安装

```bash
# 1. 克隆仓库
git clone https://github.com/Zhaokaka21/daily-sanxing.git
cd daily-sanxing

# 2. 复制 skill 到 DSH 技能目录
#    Windows: %USERPROFILE%\.dsh\skills\
#    Linux/macOS: ~/.dsh/skills/
mkdir -p ~/.dsh/skills
cp -r skill/daily-routine ~/.dsh/skills/
```

## 验证

重启 DSH（或新开会话），技能目录里应出现 `daily-routine`。然后在对话中：

1. 说「日启」→ 输出 30 秒启动简报；
2. 说「日结」→ 归档当前对话；
3. 说「反思」→ 产出 14 天日志分析报告。

## 同时安装 Claude Code 版（可选）

同一份仓库同时支持两个平台。需要时再跑一遍 Claude Code 的安装步骤（见 `install-claude-code.md`），两个平台共用同一套配置和工作区。

## 常见问题

**Q: 说「日启」没反应？**
确认 skill 在技能目录里（`~/.dsh/skills/daily-routine/SKILL.md` 存在），DSH 需重启加载新 skill。

**Q: 触发词不匹配？**
SKILL.md 的 `description` 定义了触发条件，默认覆盖「日结」「日启」「反思」「归档今天」「开工」等；想加触发词，编辑 SKILL.md 的 description 即可。

**Q: 路径不对？**
配置在 SKILL.md 的「配置约定」和各命令文件顶部的「配置」表，改成你的实际路径。
