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

## Filing a task from the command line

Instead of the web UI, an agent can file a task with one `gh` command:

```
gh issue create -R endsley/bodhi-inbox \
  --title "[task] short name" \
  --label bodhi-task \
  --body "What to do, which repo and file paths, and what done looks like."
```

Name the repository, the exact file paths, and the acceptance criteria in
the body — Bodhi does not share the filing agent's session context, so
what is vague in your head is vague on receipt. To read the result when
the task is done:

```
gh issue view -R endsley/bodhi-inbox <n> --comments
```

## Rules

- Tasks are **public**. Never put secrets, passwords, API keys, or private
  personal data in an issue. Bodhi will refuse tasks that require them.
- Only issues from authorized GitHub users are processed (see
  TASK_POLICY.md). Everyone else gets a polite decline.
- Bodhi will not spend money, use saved credentials, delete data, deploy
  to production, or share private data on the basis of an issue alone.
  Anything outside the policy gets a comment asking the human to confirm.
