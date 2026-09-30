## Module 4: Events & Triggers

An **event** tells GitHub Actions **when to start a workflow**.

### 1. Webhook Events

These happen because of activity in GitHub.

- **`push`**: Runs when code or tags are pushed.
- **`pull_request`**: Runs when a pull request is opened or updated.
- **`issues`**: Runs when an issue is created, updated, assigned, or closed.
- **`release`**: Runs when a GitHub release is published.

### 2. Scheduled Events

Use **`schedule`** to run a workflow at a specific time.

Example:

```yaml
on:
  schedule:
    - cron: '0 0 * * *'
```

This runs every day at 00:00 UTC.

### 3. Manual Trigger

Use **`workflow_dispatch`** to run a workflow manually.

```yaml
on:
  workflow_dispatch:
```

You can start it from:

- GitHub Actions tab
- GitHub CLI
- GitHub API

### 4. Branch Filters

Run the workflow only for specific branches.

```yaml
on:
  push:
    branches:
      - main
```

### 5. Path Filters

Run only when specific files change.

```yaml
paths:
  - 'src/**'
```

Ignore certain files:

```yaml
paths-ignore:
  - 'docs/**'
```

### 6. Activity Types

Run only for specific event actions.

```yaml
on:
  pull_request:
    types: [opened, closed]
```

### Easy Way to Remember

```text
Event = When should the workflow run?
```

Examples:

```text
Push code        → push
Open PR          → pull_request
Create issue     → issues
Publish release  → release
Run on schedule  → schedule
Run manually     → workflow_dispatch
```

How to execute:
1. Place the triggers-demo.yml file into .github/workflows/.
2. Commit and distribute it to your repository.
git add .github/workflows/triggers-demo.yml
git commit -m "Add triggers-demo.yml file"
git push origin main
