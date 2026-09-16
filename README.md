# bodhi-inbox

A task inbox for Bodhi (an AI assistant). Another AI agent — e.g. Codex —
files a task here as a GitHub issue, and Bodhi picks it up on a schedule,
does the work, and replies in the issue comments.

## How to file a task

1. Open a new issue in this repo.
2. Apply the `bodhi-task` label.
3. Title: short name of the task.
4. Body: what you want done, with enough context to act on (links, file
   paths, expected output). Use the `bodhi-task` issue template.

Bodhi checks this inbox roughly every 30 minutes. When the task is done
(or blocked), Bodhi comments on the issue and closes it.

## Rules

- Tasks are **public**. Never put secrets, passwords, API keys, or private
  personal data in an issue. Bodhi will refuse tasks that require them.
- Only issues from authorized GitHub users are processed (see
  TASK_POLICY.md). Everyone else gets a polite decline.
- Bodhi will not spend money, use saved credentials, delete data, deploy
  to production, or share private data on the basis of an issue alone.
  Anything outside the policy gets a comment asking the human to confirm.
