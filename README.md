# Personal Agent Workflow

在 Codex、Claude Code 和 Cursor 中使用同一套个人工作流。遇到需要规划或实现的新需求，先复述目标、范围和预期结果，等用户确认，再写计划、实现和验证。需求有实质变化时重新确认。普通问答和只读查询可以直接处理。

流程使用 [Agent Skills 格式](https://agentskills.io/specification)，入口是 [SKILL.md](skills/personal-agent-workflow/SKILL.md)。需求复述和交付验证所用的 pstack 参考随技能目录一同安装。

## 安装

克隆仓库，然后将 `skills/personal-agent-workflow/` 整个目录复制到所用工具的技能目录。

```sh
git clone https://github.com/LiuL0703/personal-agent-workflow.git
cd personal-agent-workflow
```

| 工具 | 个人技能目录 | 项目技能目录 | 手动调用 |
| --- | --- | --- | --- |
| Codex | `~/.agents/skills/` | `.agents/skills/` | `$personal-agent-workflow` |
| Claude Code | `~/.claude/skills/` | `.claude/skills/` | `/personal-agent-workflow` |
| Cursor | `~/.agents/skills/` 或 `~/.cursor/skills/` | `.agents/skills/` 或 `.cursor/skills/` | `/personal-agent-workflow` |

本机的 Codex 和 Cursor 可共用 `~/.agents/skills/` 中的同一份技能。使用 Claude Code 时，再复制到它的个人技能目录。

```sh
mkdir -p ~/.agents/skills ~/.claude/skills
cp -R skills/personal-agent-workflow ~/.agents/skills/
cp -R skills/personal-agent-workflow ~/.claude/skills/
```

[Codex 技能文档](https://learn.chatgpt.com/docs/build-skills) · [Claude Code 技能文档](https://code.claude.com/docs/en/skills) · [Cursor 技能文档](https://cursor.com/docs/skills)

## 使用

在需求消息中选择对应的技能，例如在 Codex 输入 `$personal-agent-workflow 给任务列表加一个仅看待处理的筛选，刷新后保留选择`。等助手复述后，回复确认或指出需要修正的地方。

如果希望每次提出新需求时都自动进入这个流程，将下面这条规则加入个人指令。Codex 放在 `~/.codex/AGENTS.md`，Claude Code 放在 `~/.claude/CLAUDE.md`，Cursor 放在 **Customize → Rules → User Rules**。已有等效规则时，可用这条替换它。

```text
遇到需要规划或实现的新需求，先加载并遵循 personal-agent-workflow 技能。复述需求后等待我明确确认，再开始设计、写计划或实现。单纯问答和只读查询可以直接处理。
```

## 上游参考

以下文件按原文收录自 [pstack `c3464c1`](https://github.com/backnotprop/pstack/tree/c3464c11c60b1352d5e8f5f0428a3a6943837568)，随目录提供 [MIT 许可](skills/personal-agent-workflow/references/pstack/LICENSE)。

| 参考 | 使用时机 |
| --- | --- |
| [`in-your-own-words`](skills/personal-agent-workflow/references/pstack/in-your-own-words.md) | 首次复述或重新确认需求 |
| [`principle-prove-it-works`](skills/personal-agent-workflow/references/pstack/principle-prove-it-works.md) | 汇报前验证实际交付结果 |

安装整个 `skills/personal-agent-workflow/` 目录后，调用 `personal-agent-workflow` 即可。两份参考由主技能按阶段读取。
