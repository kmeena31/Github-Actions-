### Jobs and Steps

- A **workflow** contains jobs.
- A **job** contains steps.

### Execution Rule

- **Jobs run in parallel** by default.
- **Steps run sequentially** inside a job.

### Jobs

- Each job usually runs on a separate runner.
- Jobs do not share local files directly.
- Use `needs` when one job depends on another.

Example:

```yaml
jobs:
  setup:
    runs-on: ubuntu-latest

  build:
    needs: setup
    runs-on: ubuntu-latest
```

Here, `build` waits for `setup` to finish successfully.

### Steps

- Steps run one after another.
- Steps in the same job use the same runner.
- They can share files and data on that runner.

Example:

```text
Step 1 → Build application
Step 2 → Run tests
Step 3 → Upload result
```

### Conditional Execution

Use `if` to control when a job or step runs.

```yaml
if: github.ref == 'refs/heads/main'
```

This runs only on the `main` branch.

### Status Functions

- `success()` → Runs when previous tasks succeed.
- `failure()` → Runs when a previous task fails.
- `always()` → Runs whether the workflow succeeds or fails.
- `cancelled()` → Runs when the workflow is cancelled.

### Sharing Data Between Jobs

Jobs run on different machines, so they cannot directly share local files.

Use:

- **Job Outputs** → for small values or text.
- **Artifacts** → for files.

Example:

```text
Job 1
  ↓
Creates output: hello
  ↓
Job 2
  ↓
Reads output from Job 1
```

### Easy Memory Tip

```text
Workflow
   ↓
Jobs → Parallel
   ↓
Steps → Sequential
```

**Key Point:** Use `needs` for job order, `if` for conditions, and outputs or artifacts to share data between jobs.

How to execute:
1. Relocate the File: Copy execution-flow-demo.yml into your repository's .github/workflows/ path.
2. Commit and Push:
git add .github/workflows/execution-flow-demo.yml
git commit -m "Add execution-flow-demo.yml "
git push origin main 