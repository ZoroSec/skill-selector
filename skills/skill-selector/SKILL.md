---
name: skill-selector
description: Preview and select available skills for a task, with relevance explanations and the option to add skills. Use when the user wants to review or choose skills before a task.
---

# Skill selector

Identify skills available to the current agent using its session catalog or supported discovery tools. If the catalog is incomplete, say what you can see; never invent skill names. Propose skills relevant to the user's task and explain each choice briefly. Include explicitly requested skills and any required by higher-priority instructions. These are proposed choices, not a guaranteed execution plan.

When the user wants to choose skills before execution, show the proposed choices as on and let them switch choices off or add available skills. Where the host provides an in-chat interactive selection surface that can submit choices back to the agent, use its documented workflow to show selectable suggestions and a searchable list of available skills. Do not open a browser or start a server solely for selection. If such a surface is unavailable, list the skills and reasons in chat and ask the user to reply with `on <skill>`, `off <skill>`, `add <skill>`, or `continue`. Do not start the underlying task until choices are submitted.

Verify added names against the skills available to the current session and explain their relevance before using them. If a name is ambiguous or unavailable, ask for clarification. Respect the selected choices for this task where higher-priority instructions permit. Explain any required skill that cannot be disabled; never pretend it was disabled. If another skill becomes necessary later, disclose it and offer a choice where permitted.

If the user provides selections together with the task, apply them directly. A preview-only request does not authorize executing the task. Choices apply to the current task unless the user specifies otherwise; do not modify global settings. This skill does not guarantee automatic invocation on every prompt or control the host's skill system.
