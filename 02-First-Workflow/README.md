## Module 2: First Workflow

- GitHub Actions workflow files must be stored in:

```text
.github/workflows/
```

- If the YAML file is stored somewhere else, GitHub will not run it.

### Important Keywords

- **`name`**: Gives the workflow a name.
- **`run-name`**: Gives each workflow run a custom name.
- **`github` context**: Provides information about the workflow run.
- **`${{ github.actor }}`**: Shows the user who started the workflow.
- **`on`**: Defines when the workflow should run.

Example:

```yaml
on: [push, workflow_dispatch]
```

This means the workflow runs when:

- Code is pushed.
- The workflow is started manually.

### Simple Flow

```text
Push code / Manual Run
        ↓
GitHub detects workflow
        ↓
Workflow starts
        ↓
Runner executes the job
        ↓
Steps run
```
How to execute it:
1. Copy the first-pipeline.yml file to .github/workflows/
2. Commit and Push:
git add .github/workflows/first-pipeline.yml
git commit -m "Create my first GitHub Actions pipeline"
git push origin main