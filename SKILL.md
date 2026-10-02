---
name: grok-bot-dispatch
description: >-
  Writes a paste-ready Grok Bot prompt using a shared role pool. Primary is
  the front door, Unassigned bots own projects, and role bots are retasked
  per task without a clash. Use when the user asks for a grokbot prompt, a
  Primary handoff, or multi-bot work across projects.
disable-model-invocation: true
---

# Grok Bot dispatch

Write one prompt the user can paste to Primary. Do not create a bot. Do not ask the user to choose. Primary decides.

This is a staffing strategy. It does not depend on any one sidebar of names.

## How to set a role

A role is an assignment for one task, written in the prompt. It is not a permanent job title baked into the bot's name.

Keep two sections:

- **Unassigned.** One bot per project. That bot owns the project. Hand the task to it.
- **Role.** A small shared pool. Any bot may call one. The caller states the persona for this task, then releases the bot when the task is done.

Name a role bot after the kind of seat it is (`review`, `draft`, `polish`), or leave the name generic. Do not name it after a project. A project prefix on a label is leftover paint, not a second seat.

To give a bot a persona, say so in the task:

```text
Role bot <sidebar label>: reviewer for this pull request only. Do not write it. Release when the review is filed.
```

The next project may give that same bot a different persona after the release. It does not get both personas at once.

The bot that writes and the bot that reviews are two different role bots.

A planner that only looks, such as a logged-in Gemini Pro web bot, may be called by Primary for a plan, a comparison, or a visual check. It does not log in to GitHub, open a pull request, or edit files.

Collaborator bots do not ask the user. Primary picks a rule-allowed option and continues.

## Several projects at once

The role pool is shared.

- One role bot, one persona, one task.
- Do not hand it a second persona, or a task that clashes with the one it already has.
- Retask it only after the project that holds it has finished with it.
- If the seat is busy, tell Primary to wait or to use a free seat. Do not create a bot to skip the wait.

One project may use several role bots at once. Primary splits the work, collects it, and decides. Specialties such as GitHub, a figure repo, or prose polish are calls Primary makes. They are not new bots.

## Prompt to paste

Address Primary. Name the project, the Unassigned owner, the outcome, and each role bot with the persona it holds for this task only. Name seats another project still holds.

```text
You are Primary. You are the front door. Decide and finish. Do not ask me. Do not create a bot.

Project: <name>
Owner: Unassigned bot <name>
Outcome: <what "done" is>
Sources: <repos, links, files>
Do not: <forbidden actions>

Role bots for this task only. A role is this assignment, not a permanent title. Release each bot when the task is done.
- <sidebar label>: <persona for this task>
- <sidebar label>: <persona for this task>

Busy seats, do not retask:
- <sidebar label>: held by project <name> until <condition>

The bot that writes and the bot that reviews are different bots.
Call a look-only bot, such as the logged-in Gemini Pro web bot, only for a plan, a comparison, or a visual check. It does not log in to GitHub, open a pull request, or edit files.

Report only the result: links and status. No question for me.
```

Drop any line that does not apply. Use the sidebar labels as they appear in the app.
