---
name: skill-selector
description: Preview and select available skills for a task in an interactive chat menu, with relevance explanations and the option to add skills. Use when the user asks which skills apply, wants to choose or toggle skills, or invokes skill-selector.
---

# Skill selector

Use the current session's skill catalog to propose relevant skills for the task. Include skills explicitly requested and skills required by higher-priority instructions. For each, give a concise, task-specific explanation of its relevance; do not present a speculative choice as a guaranteed execution plan.

When the user wants to choose skills before execution, show an interactive selector directly in the conversation using the available in-chat visualization workflow. Read its skill instructions and use its supported follow-up messaging API. Do not open a browser tab or start a server. Present proposed skills as initially selected, each with its relevance, and include a searchable list of all skills in the current session catalog with selectable checkboxes so users can add skills directly. Show each skill description or a concise task-specific relevance; never invent ratings. Keep proposed and additional choices visually distinct. A clearly labeled action sends a follow-up containing the selected names, deselected names, and any selected additions. Preserve the original task in the follow-up. Wait for the user's submitted choices before starting the task.

After submission, verify added skill names against the actual session catalog, explain each added skill's relevance to the task, and do not invent unavailable skills. If an added name is ambiguous or unavailable, ask the user to clarify. Apply ON and OFF selections for this task when higher-priority instructions permit. Explain any higher-priority required skill that cannot be switched off; do not pretend it was disabled. If further skills become necessary later, disclose them and offer a choice where permitted.

If the in-chat interactive surface or its follow-up messaging is unavailable, present the choices with relevance in chat and let the user respond with `on <skill>`, `off <skill>`, `add <skill>`, or `continue`. If the user provides selections together with the task, apply them directly. A preview-only request does not authorize executing the underlying task. Choices apply to the current task unless the user specifies otherwise; do not change global settings.

A skill cannot intercept every prompt or guarantee automatic activation. The menu appears when this skill is invoked or selected, not as a system-wide hook. Do not suppress higher-priority instructions.

