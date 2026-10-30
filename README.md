# Skill Selector

Make your coding agent ask **which skills to use** before it starts a new task.

Skills are small instruction packs. For example, one skill may help build a website, another may help write tests, and another may help create images. This skill shows the useful choices first, explains why they fit, and lets you turn choices on, off, or add another skill.

## What you get

- A short list of skills that match your request
- One plain-English reason for every suggestion
- A way to keep, remove, or add skills before work starts
- A menu in agents that support questions; a text fallback everywhere else

## Install

Open or download this folder:

**https://github.com/ZoroSec/skill-selector/tree/main/skills/skill-selector**

### Codex

Run this command:

```sh
python "$CODEX_HOME/skills/.system/skill-installer/scripts/install-skill-from-github.py" --url https://github.com/ZoroSec/skill-selector/tree/main/skills/skill-selector
```

### Claude web or Claude Desktop

1. Download [skill-selector-claude.zip](https://github.com/ZoroSec/skill-selector/releases/download/v1.1.0/skill-selector-claude.zip).
2. In Claude, open **Customize** (or **Plugins**) > **Skills**.
3. Click **+** > **Create skill** > **Upload a skill**.
4. Choose `skill-selector-claude.zip`, then turn it on.

Do not upload the ZIP in an ordinary chat and ask Claude to install it. Chat cannot change your account settings. You must use the Skills page. If you do not see Skills, turn on **Code execution and file creation** in Claude Settings > Capabilities first.

The uploaded skill also syncs to Claude Code when you sign in with the same Claude account. Start a new Claude Code session after uploading.

**Make Claude ask before each task:** Installing a skill alone does not make it run on every prompt. Open **Settings > Your Claude > Instructions** (or **Settings > Account > Instructions for Claude**) and add:

```text
Before starting a new substantive task, use the skill-selector skill to suggest relevant available skills and explain why each is useful. Wait for me to choose, remove, or add skills before starting. Do not repeat the selection for follow-up messages in the same task.
```

Start a new chat and test with: “Use skill-selector and show an interactive skill selection menu before creating a portfolio website.” Claude decides when to load skills and display interactive visuals, so the menu is not guaranteed. If the menu cannot submit choices to the conversation, copy the selected names into chat. If interactive visuals are unavailable, reply with skill names and `continue`.

### Claude Code, OpenCode, Antigravity, or another terminal agent

First download the repository:

```sh
git clone https://github.com/ZoroSec/skill-selector.git
```

Then copy the `skills/skill-selector` folder into the matching folder below. The final file must be named `skill-selector/SKILL.md`.

| Agent | Copy it here for all projects |
| --- | --- |
| Claude Code | `~/.claude/skills/` |
| OpenCode | `~/.config/opencode/skills/` |
| Antigravity app or IDE | `~/.gemini/config/skills/` |
| Antigravity CLI | `~/.gemini/antigravity-cli/skills/` |
| Codex | `~/.codex/skills/` |

Example for Claude Code on macOS or Linux:

```sh
mkdir -p ~/.claude/skills
cp -R skill-selector/skills/skill-selector ~/.claude/skills/
```

Example for Claude Code in Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
Copy-Item -Recurse "skill-selector\skills\skill-selector" "$HOME\.claude\skills\"
```

For a different agent, replace the destination folder with the one from the table. Restart the agent after installing.

## Use it once

Ask your agent:

> Use skill-selector before building my portfolio website.

It should suggest relevant skills, explain them, then wait for your choice. Pick the skills you want, remove ones you do not want, or add another available skill.

If your agent has no selection menu, reply in chat with one of these:

```text
on frontend-design
off imagegen
add ui-styling
continue
```

## Make it ask every time

Installing the skill makes it available. To make it appear before every new task, add this text to your agent's global instructions file:

```md
Before starting a new substantive task, use the `skill-selector` skill. Show relevant skills with a short reason for each one, then wait for my choices before starting work. Do not ask again for follow-up messages in the same task.
```

| Agent | Global instructions file |
| --- | --- |
| Codex | `~/.codex/AGENTS.md` |
| OpenCode | `~/.config/opencode/AGENTS.md` |
| Claude Code | `~/.claude/CLAUDE.md` |
| Antigravity | `~/.gemini/AGENTS.md` |

For an on-screen menu, tell the agent to use its built-in question tool when available. OpenCode uses `question`; Antigravity uses `ask_question`.

## Important

This skill does not control an agent by itself. It gives the agent instructions for offering skill choices. Your agent must support Agent Skills and follow its global instructions for the menu to appear automatically.

## Official docs

- [Codex skills](https://developers.openai.com/codex/skills/)
- [Claude Code skills](https://code.claude.com/docs/en/skills)
- [OpenCode skills](https://opencode.ai/docs/skills)
- [Antigravity skills](https://antigravity.google/docs/skills)
