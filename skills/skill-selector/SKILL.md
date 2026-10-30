---
name: skill-selector
description: Preview and select available skills for a task, with relevance explanations and the option to add skills. Use when the user wants to review or choose skills before a task.
---

# Skill selector

Identify skills available to the current agent using its session catalog or supported discovery tools. If the catalog is incomplete, say what you can see; never invent skill names. Propose skills relevant to the user's task and explain each choice briefly. Include explicitly requested skills and any required by higher-priority instructions. These are proposed choices, not a guaranteed execution plan.

When the user wants to choose skills before execution, show the proposed choices as on and let them switch choices off or add available skills. Prefer the host's own question or selection UI:

- In Codex, when the `visualize:visualize` skill is listed, read and follow it to render an in-chat interactive selector that submits choices as a follow-up.
- In Claude web or desktop chat, use the available interactive question or custom visual tool to present a skill selector. Offer selectable skills with relevance reasons, a way to add another available skill, and a submit action that sends the choices back to Claude. Use only the host's supported interaction APIs; never assume clicks automatically reach the conversation. If a visual cannot send choices back, display the selections for the user to copy into chat and wait for their message. If interactive tools are unavailable, use the text fallback below.
- In OpenCode, use its built-in `question` tool when it is available.
- In Antigravity, use its built-in `ask_question` tool when it is available.
- In other hosts, use their documented multiple-choice question or option-picker capability when it is available.

Show each suggested skill with a short relevance reason, let the user remove suggested skills, and include a write-in option for an available skill they want to add. Do not open a browser or start a server solely for selection. If the host has no selectable UI, list the skills and reasons in chat and ask the user to reply with `on <skill>`, `off <skill>`, `add <skill>`, or `continue`. Do not start the underlying task until choices are submitted.

Verify added names against the skills available to the current session and explain their relevance before using them. If a name is ambiguous or unavailable, ask for clarification. Respect the selected choices for this task where higher-priority instructions permit. Explain any required skill that cannot be disabled; never pretend it was disabled. If another skill becomes necessary later, disclose it and offer a choice where permitted.

If the user provides selections together with the task, apply them directly. A preview-only request does not authorize executing the task. Choices apply to the current task unless the user specifies otherwise; do not modify global settings. This skill does not guarantee automatic invocation on every prompt or control the host's skill system.
