# Personal Agent Workflow

[中文](#中文) · [English](#english)

## 中文

在 Codex、Claude Code 和 Cursor 中使用同一套个人工作流。遇到需要规划或实现的新需求，先复述目标、范围和预期结果，等用户确认，再写计划、实现和验证。需求有实质变化时重新确认。普通问答和只读查询可以直接处理。

流程使用 [Agent Skills 格式](https://agentskills.io/specification)，入口是 [SKILL.md](skills/personal-agent-workflow/SKILL.md)。需求复述和交付验证所用的 pstack 参考随技能目录一同安装。

### 安装

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

### 使用

在需求消息中选择对应的技能，例如在 Codex 输入 `$personal-agent-workflow 给任务列表加一个仅看待处理的筛选，刷新后保留选择`。等助手复述后，回复确认或指出需要修正的地方。

如果希望每次提出新需求时都自动进入这个流程，将下面这条规则加入个人指令。Codex 放在 `~/.codex/AGENTS.md`，Claude Code 放在 `~/.claude/CLAUDE.md`，Cursor 放在 **Customize → Rules → User Rules**。已有等效规则时，可用这条替换它。

```text
遇到需要规划或实现的新需求，先加载并遵循 personal-agent-workflow 技能。复述需求后等待我明确确认，再开始设计、写计划或实现。单纯问答和只读查询可以直接处理。
```

### 上游参考

以下文件按原文收录自 [pstack `c3464c1`](https://github.com/backnotprop/pstack/tree/c3464c11c60b1352d5e8f5f0428a3a6943837568)，随目录提供 [MIT 许可](skills/personal-agent-workflow/references/pstack/LICENSE)。

| 参考 | 使用时机 |
| --- | --- |
| [`in-your-own-words`](skills/personal-agent-workflow/references/pstack/in-your-own-words.md) | 首次复述或重新确认需求 |
| [`principle-prove-it-works`](skills/personal-agent-workflow/references/pstack/principle-prove-it-works.md) | 汇报前验证实际交付结果 |

安装整个 `skills/personal-agent-workflow/` 目录后，调用 `personal-agent-workflow` 即可。两份参考由主技能按阶段读取。

## English

Use the same personal workflow in Codex, Claude Code, and Cursor. For a new request that needs planning or implementation, restate the goal, scope, and expected outcome. Wait for the user to confirm before planning, implementing, and verifying the change. Ask for confirmation again if the scope changes materially. You can answer standalone questions and read-only requests directly.

The workflow uses the [Agent Skills format](https://agentskills.io/specification). Its entry point is [SKILL.md](skills/personal-agent-workflow/SKILL.md). The skill directory includes the pstack references for restating requests and verifying deliverables.

### Installation

Clone the repository and copy the entire `skills/personal-agent-workflow/` directory into your tool’s skills directory.

```sh
git clone https://github.com/LiuL0703/personal-agent-workflow.git
cd personal-agent-workflow
```

| Tool | Personal skills directory | Project skills directory | Manual invocation |
| --- | --- | --- | --- |
| Codex | `~/.agents/skills/` | `.agents/skills/` | `$personal-agent-workflow` |
| Claude Code | `~/.claude/skills/` | `.claude/skills/` | `/personal-agent-workflow` |
| Cursor | `~/.agents/skills/` or `~/.cursor/skills/` | `.agents/skills/` or `.cursor/skills/` | `/personal-agent-workflow` |

Codex and Cursor can share one local copy in `~/.agents/skills/`. For Claude Code, copy the skill into its personal skills directory as well.

```sh
mkdir -p ~/.agents/skills ~/.claude/skills
cp -R skills/personal-agent-workflow ~/.agents/skills/
cp -R skills/personal-agent-workflow ~/.claude/skills/
```

[Codex skills docs](https://learn.chatgpt.com/docs/build-skills) · [Claude Code skills docs](https://code.claude.com/docs/en/skills) · [Cursor skills docs](https://cursor.com/docs/skills)

### Usage

Select the skill in the same message as your request. In Codex, for example, enter `$personal-agent-workflow Add a pending-only filter to the task list and keep the selection after a refresh`. Once the agent restates the request, confirm it or explain what needs to change.

To use this workflow automatically for every new request, add the rule below to your personal instructions. For Codex, use `~/.codex/AGENTS.md`. For Claude Code, use `~/.claude/CLAUDE.md`. For Cursor, use **Customize → Rules → User Rules**. If you already have an equivalent rule, you can replace it with this one.

```text
For a new request that needs planning or implementation, load and follow the personal-agent-workflow skill. Restate the request and wait for my explicit confirmation before designing, writing a plan, or implementing. Answer standalone questions and read-only requests directly.
```

### Upstream references

The following files come verbatim from [pstack `c3464c1`](https://github.com/backnotprop/pstack/tree/c3464c11c60b1352d5e8f5f0428a3a6943837568). The [MIT license](skills/personal-agent-workflow/references/pstack/LICENSE) is included in the skill directory.

| Reference | When to use it |
| --- | --- |
| [`in-your-own-words`](skills/personal-agent-workflow/references/pstack/in-your-own-words.md) | When first restating a request or asking for confirmation again |
| [`principle-prove-it-works`](skills/personal-agent-workflow/references/pstack/principle-prove-it-works.md) | When verifying the actual deliverable before reporting completion |

Install the entire `skills/personal-agent-workflow/` directory and invoke `personal-agent-workflow`. The main skill reads each reference at the relevant stage.
