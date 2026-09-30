### What is a Runner?

- A **runner** is the machine that executes a GitHub Actions job.
- Every job uses `runs-on` to define where it runs.

Example:

```yaml
runs-on: ubuntu-latest
```

This means the job runs on a GitHub Ubuntu machine.

### 1. GitHub-Hosted Runners

- GitHub provides and manages the runner.
- A fresh virtual machine is created for each job.
- The machine is removed after the job finishes.
- No server maintenance is required.
- Common tools are already installed.

Common examples:

```yaml
ubuntu-latest
windows-latest
macos-latest
```

### Why use GitHub-hosted runners?

- Easy to use.
- No infrastructure management.
- Fresh environment for every run.
- Common development tools are pre-installed.

### 2. Self-Hosted Runners

- You provide and manage the machine.
- It can be an AWS EC2 instance, Azure VM, physical server, or Kubernetes-based runner.
- You control the hardware, software, networking, and security.

Example:

```yaml
runs-on: [self-hosted, linux, x64]
```

### Why use Self-Hosted Runners?

Use them when you need:

- Access to private networks.
- Access to internal servers or databases.
- Special hardware such as GPUs.
- More CPU or memory.
- Custom software.
- Persistent storage or local caching.

### GitHub-Hosted vs Self-Hosted

| GitHub-Hosted | Self-Hosted |
|---|---|
| Managed by GitHub | Managed by you |
| Fresh VM for each job | Machine may stay available |
| Easy setup | More setup required |
| Good for normal CI/CD | Good for private/custom environments |
| Limited customization | Full customization |

### Easy Memory Tip

```text
Runner = Where the job runs
```

```text
GitHub-Hosted
GitHub manages it

Self-Hosted
You manage it
```

**Key Point:** Use GitHub-hosted runners for simple CI/CD. Use self-hosted runners when you need private network access, custom hardware, or more control.


How to execute it:
1. Relocate the File: Copy runners-demo.yml into your repository's .github/workflows/ path.
2. Commit and Push:
git add .github/workflows/runners-demo.yml
git commit -m "Add runners-demo.yml "
git push origin main 