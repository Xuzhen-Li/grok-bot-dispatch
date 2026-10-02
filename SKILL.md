---
name: grok-bot-dispatch
description: >-
  Writes a paste-ready prompt for Grok Bot when Primary is the front door,
  Unassigned bots own projects, and sixteen shared role bots must not clash.
  Use when the user asks for a grokbot prompt, a Primary Bot handoff, a
  multi-bot task, or dispatch across Unassigned and role.
disable-model-invocation: true
---

# Grok Bot dispatch

Write one prompt the user can paste to Primary. Do not create a bot. Do not ask the user to choose. Primary decides.

## Roster

Primary is the front door. Daily questions, coordination, and wrap-up go to Primary. For a specialty such as GitHub, paper-viz, or prose polish, Primary calls the matching bot.

Unassigned bots own projects. Hand the task to the Unassigned bot for that project.

Role has 16 bots. Any bot may call them, and their roles may be changed. A fixed persona is taken from role. A sidebar name is the current label, not a permanent job. A `paper-viz-` prefix does not make a second seat.

| # | Sidebar label | Usual persona |
|---|---------------|----------------|
| 1 | 流程图员 | draw.io and flow diagrams |
| 2 | 审查员 | Pull-request structure. Never reviews a pull request it wrote. |
| 3 | R绘图员 | Data figures |
| 4 | 语言润色-英文 | English prose |
| 5 | 语言润色-命令旁白 | Command-line narration |
| 6 | 设计-课堂路径 | Learning paths |
| 7 | 设计-信息架构 | Information structure of a document or repo |
| 8 | 语言润色-中文 | Chinese prose |
| 9 | 文档员 | README, skill docs, profile structure. Does not edit plot scripts. |
| 10 | 仓库管家 | Cross-repo links, placeholder repos, issues. Does not archive, rename, delete, or change visibility. |
| 11 | 维修员 | Actions, Pages, repo settings. No force-push. Older notes call this seat 运维员. |
| 12 | 体检员 | HTTP, gallery, catalog, links. Report only. Does not edit files. |
| 13 | 设计-图文节奏 | Type size, frame, spacing, readability of a preview |
| 14 | 两仓注释圆桌 | Annotation comparison across two repos |
| 15 | 两仓科学审阅 | Whether the science is right. Structure review stays with 审查员. |
| 16 | 遗传学专家 | Bioinformatics content. Not repo chores. |

The bot that writes and the bot that reviews must be two different bots.

A logged-in Gemini Pro web bot is called by Primary for a plan, a comparison, or a visual check. It does not log in to GitHub, open a pull request, or edit files.

Collaborator bots do not ask the user. If a choice is open, Primary picks a rule-allowed option and continues.

## Several projects at once

Role bots are shared. When more than one project is in progress:

- Do not give one role bot two different roles at the same time.
- Do not give one role bot two tasks that clash.
- Retask that bot for another project only after the first project has finished with it.
- If the needed seat is busy, say so in the prompt and tell Primary to wait, or to use a free seat. Do not create a bot to dodge the clash.

One project may use several role bots at once. Primary splits the work, collects it, and decides.

## Prompt to paste

Address Primary. Name the project, the Unassigned owner, the outcome, and each role bot with the persona it keeps for this task. State which seats stay untouched because another project holds them.

```text
You are Primary. You are the front door. Decide and finish. Do not ask me. Do not create a bot.

Project: <name>
Owner: Unassigned bot <name>
Outcome: <what "done" is>
Sources: <repos, links, files>
Do not: <forbidden actions>

Role bots for this task only. Release each one when the task is done.
- <sidebar label>: <persona for this task>
- <sidebar label>: <persona for this task>

Busy seats, do not retask:
- <sidebar label>: held by project <name> until <condition>

The bot that writes and the bot that reviews are different bots.
Call the logged-in Gemini Pro web bot only for a plan, a comparison, or a visual check. It does not log in to GitHub, open a pull request, or edit files.

Report only the result: links and status. No question for me.
```

Drop anything that does not apply. Keep the sidebar labels exactly as they appear in the app.
