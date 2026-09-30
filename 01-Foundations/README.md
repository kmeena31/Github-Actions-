

What is CI/CD?
CI/CD automates building, testing, and deploying code.

CI (Continuous Integration): Automatically merges and tests code changes. It helps find bugs early.

CD (Continuous Delivery/Deployment): Automatically prepares and deploys tested code to staging or production.

What is GitHub Actions?
**GitHub Actions** is GitHub’s built-in CI/CD and automation tool.

- It automates software development tasks.
- It works directly with GitHub repositories.
- **Actions** are individual reusable tasks.
- **Workflows** combine multiple actions and steps.
- Workflows can start from events like a **push**, **pull request**, or **manual trigger**.

Core components:
1. **Workflow:** The complete automated process. It is written in a YAML file.

2. **Event:** The trigger that starts the workflow. Example: `push`, `pull_request`, or `workflow_dispatch`.

3. **Job:** A group of steps that run on the same runner. Jobs usually run in parallel.

4. **Step:** A single task inside a job. Steps run one after another.

5. **Action:** A reusable task. Example: checkout code or log in to AWS.

6. **Runner:** The machine that runs the workflow. It can be Ubuntu, Windows, macOS, or self-hosted.

How to execute it:
1. copy 01-Foundations/Foundations to ./github/workflows/

2. add files to git and push it 
git add .github/workflows/foundations-demo.yml
git commit -m "Add foundations demo workflow"
git push origin main

