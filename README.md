# grok-bot-dispatch

A Cursor skill for staffing [Grok Bot](https://x.ai/bot). Primary is the front door. Project bots live in Unassigned. Shared workers live in Role.

A role is an assignment for one task, written in the prompt. It is not a job title locked to a bot's name. When several projects run at once, one role bot keeps one persona and one task. Retask it after that project lets go.

The skill does not create bots and does not log in to the Grok Bot app. It does not assume a particular sidebar of names.

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
Project: gallery. Owner: the Unassigned bot for that repo.
Outcome: one pull request that fixes the badge.
Role: the draft seat writes, the review seat reviews.
The ops seat is busy on another project until that job finishes.
```

The agent returns one block to paste into Primary. A two-project case is in [examples/two-projects.md](examples/two-projects.md).

## License

MIT
