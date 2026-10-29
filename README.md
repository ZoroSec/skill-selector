# Skill Selector

A Codex skill for choosing which skills to use before a task. It presents a searchable selection menu in chat, explains why suggested skills are relevant, and lets you add other available skills.

## Install

Copy `skills/skill-selector` into your Codex skills directory (typically `~/.codex/skills/skill-selector`). Start a new chat if it does not appear immediately.

## Use

Ask Codex to use `$skill-selector` and describe your task. Select the skills you want to use; the selector checks added skills against the session's available catalog.

The menu depends on an available interactive visualization surface. When one is unavailable, the skill falls back to choices in chat. It does not intercept every prompt or change global Codex settings. Higher-priority instructions still apply.
