# Personal Agent Workflow

[简体中文](README.zh-CN.md)

Use the same personal workflow in Codex, Claude Code, and Cursor. For a new request that needs planning or implementation, restate the goal, scope, and expected outcome. Wait for the user to confirm before planning, implementing, and verifying the change. Ask for confirmation again if the scope changes materially. You can answer standalone questions and read-only requests directly.

The workflow uses the [Agent Skills format](https://agentskills.io/specification). Its entry point is [SKILL.md](skills/personal-agent-workflow/SKILL.md). The skill directory includes the pstack references for restating requests and verifying deliverables.

## Installation

### One-command installation

With Node.js 22.20 or later, run this from the project where you want to install the skill. The command sets it up for Codex, Claude Code, and Cursor.

```sh
npx --yes skills add LiuL0703/personal-agent-workflow --skill personal-agent-workflow --agent codex claude-code cursor --yes
```

Add `--global` to make it available across your projects.

### Manual installation

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

## Usage

Select the skill in the same message as your request. In Codex, for example, enter `$personal-agent-workflow Add a pending-only filter to the task list and keep the selection after a refresh`. Once the agent restates the request, confirm it or explain what needs to change.

To use this workflow automatically for every new request, add the rule below to your personal instructions. For Codex, use `~/.codex/AGENTS.md`. For Claude Code, use `~/.claude/CLAUDE.md`. For Cursor, use **Customize → Rules → User Rules**. If you already have an equivalent rule, you can replace it with this one.

```text
For a new request that needs planning or implementation, load and follow the personal-agent-workflow skill. Restate the request and wait for my explicit confirmation before designing, writing a plan, or implementing. Answer standalone questions and read-only requests directly.
```

## Upstream references

The following files come verbatim from [pstack `c3464c1`](https://github.com/backnotprop/pstack/tree/c3464c11c60b1352d5e8f5f0428a3a6943837568). The [MIT license](skills/personal-agent-workflow/references/pstack/LICENSE) is included in the skill directory.

| Reference | When to use it |
| --- | --- |
| [`in-your-own-words`](skills/personal-agent-workflow/references/pstack/in-your-own-words.md) | When first restating a request or asking for confirmation again |
| [`principle-prove-it-works`](skills/personal-agent-workflow/references/pstack/principle-prove-it-works.md) | When verifying the actual deliverable before reporting completion |

Install the entire `skills/personal-agent-workflow/` directory and invoke `personal-agent-workflow`. The main skill reads each reference at the relevant stage.
