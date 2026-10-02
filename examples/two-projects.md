# Two projects, one shared role section

paper-viz needs a reviewer, and another project already needs that same seat afterward. Only one 审查员 exists. The prompt keeps the seat on paper-viz until that review is finished.

```text
You are Primary. You are the front door. Decide and finish. Do not ask me. Do not create a bot.

Project: paper-viz
Owner: Unassigned bot for paper-viz
Outcome: a pull request that updates the figures badge to the count in catalog.json. No other file changes.
Sources: https://github.com/Xuzhen-Li/paper-viz
Do not: force-push, edit plot scripts, or open a second workflow.

Role bots for this task only. Release each one when the task is done.
- 文档员: edit the badge line in the README
- 审查员: review that pull request. Do not write it.

Busy seats, do not retask:
- 审查员: after this review finishes, the other open project may use it. Do not start that review until this pull request is approved or closed.

The bot that writes and the bot that reviews are different bots.
Call the logged-in Gemini Pro web bot only if the badge change has a preview to look at. It does not log in to GitHub, open a pull request, or edit files.

Report only the pull request link and status. No question for me.
```
