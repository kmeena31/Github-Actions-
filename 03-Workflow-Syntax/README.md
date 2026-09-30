## Module 3: Workflow Syntax

YAML is used to define GitHub Actions workflows.

- Indentation is very important in YAML.
- Wrong spacing can break the workflow.

### Important Keywords

1. **`name`**  
   Gives the workflow a name.

2. **`on`**  
   Defines when the workflow runs.

```yaml
on: push
```

Multiple events:

```yaml
on: [push, pull_request]
```

You can also filter by branch or path.

3. **`env`**  
   Defines environment variables.

```yaml
env:
  GLOBAL_VAR: "Hello"
```

4. **`jobs`**  
   Defines the work to be done.

- Jobs run in parallel by default.
- Each job needs a unique ID.

Example:

```yaml
jobs:
  build:
```

5. **`runs-on`**  
   Defines the runner machine.

```yaml
runs-on: ubuntu-latest
```

6. **`needs`**  
   Makes one job wait for another job.

Example:

```yaml
needs: build
```

This means the current job starts only after `build` finishes successfully.

7. **`steps`**  
   Defines tasks inside a job.

8. **`uses`**  
   Runs a reusable GitHub Action.

```yaml
uses: actions/checkout@v4
```

9. **`run`**  
   Runs a command or script.

```yaml
run: echo "Hello"
```

For multiple commands:

```yaml
run: |
  pwd
  ls -la
```

### Easy Structure to Remember

```text
Workflow
   ↓
Trigger
   ↓
Jobs
   ↓
Runner
   ↓
Steps
   ↓
Actions / Commands
```

### Basic Example

```yaml
name: CI Workflow

on: push

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Run command
        run: echo "Build started"
```

How to execute it:
1. Copy the syntax-demo.yml file to .github/workflows/
2. Commit and Push:
git add .github/workflows/syntax-demo.yml
git commit -m "Add syntax deep dive workflow"
git push origin main