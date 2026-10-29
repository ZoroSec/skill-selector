# Skill Selector

Choose which agent skills to use before starting a task. Skill Selector proposes relevant skills, explains why they apply, and lets you turn them on or off or add other available skills.

Works with agents that support the [Agent Skills format](https://agentskills.io/), including Codex, Claude Code, Gemini CLI, and Cursor. A host with a suitable interactive chat surface can display a selection menu; otherwise the same workflow uses ordinary chat. Availability and automatic invocation depend on the host.

## Install

Clone the repository:

```sh
git clone https://github.com/ZoroSec/skill-selector.git
```

Copy the `skills/skill-selector` directory into your agent's personal skills directory. For project-only installation, use the project directory instead.

| Agent | Personal skills directory | Project skills directory |
| --- | --- | --- |
| Codex | `~/.codex/skills/` | `.agents/skills/` |
| Claude Code | `~/.claude/skills/` | `.claude/skills/` |
| Gemini CLI | `~/.gemini/skills/` | `.gemini/skills/` |
| Cursor | `~/.cursor/skills/` | `.cursor/skills/` |

For example, to install for Claude Code on macOS or Linux:

```sh
mkdir -p ~/.claude/skills
cp -R skill-selector/skills/skill-selector ~/.claude/skills/
```

On Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills" | Out-Null
Copy-Item -Recurse "skill-selector\skills\skill-selector" "$env:USERPROFILE\.claude\skills\"
```

Replace `.claude` with `.codex`, `.gemini`, or `.cursor` for the corresponding agent. The final file must be at `<skills-directory>/skill-selector/SKILL.md`. Restart the agent or refresh its skills list if the skill does not appear. For other Agent Skills-compatible hosts, copy the same folder to that host's documented skills directory.

## Use

Ask your agent:

> Use skill-selector to review the skills for: build a portfolio website.

Select the proposed skills or add skills that are available in your session. If no interactive menu is available, reply with choices such as `off frontend-design`, `add imagegen`, or `continue`.

Skill Selector offers per-task choices; it does not intercept every prompt, change global settings, or override higher-priority instructions. Available skills and selection controls vary by agent.

## Agent documentation

- [Claude Code skills](https://code.claude.com/docs/en/skills)
- [Gemini CLI skills](https://geminicli.com/docs/cli/using-agent-skills/)
- [Cursor skills](https://cursor.com/docs/skills)
- [Codex skills](https://developers.openai.com/codex/skills/)
