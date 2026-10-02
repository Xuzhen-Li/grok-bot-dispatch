# grok-bot-dispatch

Cursor skill for writing a prompt to [Grok Bot](https://x.ai/bot) when Primary is the front door.

Unassigned bots own projects. The role section has 16 shared bots. Other bots may call them and change their roles. When several projects run at once, one role bot is not given two conflicting roles or two clashing tasks.

The skill does not create bots and does not log in to the Grok Bot app.

## Install

```bash
git clone https://github.com/Xuzhen-Li/grok-bot-dispatch.git
mkdir -p ~/.cursor/skills
ln -sfn "$(pwd)/grok-bot-dispatch" ~/.cursor/skills/grok-bot-dispatch
```

This skill is not auto-attached. The agent must read `SKILL.md` first.

## Use

```text
Read grok-bot-dispatch/SKILL.md and write a Primary prompt.
Project: paper-viz. Owner: the Unassigned bot for that repo.
Outcome: one pull request that fixes the gallery badge.
Role: 文档员 writes, 审查员 reviews. 维修员 is busy on another project.
```

The agent returns one block to paste into Primary. A two-project case is in [examples/two-projects.md](examples/two-projects.md).

## License

MIT
