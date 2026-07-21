# ⚙️ GitHub Actions Fundamentals

## What is GitHub Actions?

GitHub Actions is GitHub's built-in automation platform that allows workflows to run automatically when specific events occur in a repository.

Instead of manually compiling, testing, or deploying an application after every code change, GitHub Actions performs these tasks automatically using predefined workflows.

A workflow is defined using a YAML (`.yml`) file stored inside:

```
.github/workflows/
```

Each workflow runs on a temporary virtual machine called a **runner**.

---

# CI vs CD vs Git

Understanding the distinction between Git, Continuous Integration (CI), and Continuous Delivery/Deployment (CD) is essential.

| Technology | Purpose |
|------------|---------|
| **Git** | Tracks and synchronizes source code between developers and GitHub. |
| **Continuous Integration (CI)** | Automatically builds, validates, and tests code whenever changes are pushed. |
| **Continuous Delivery / Deployment (CD)** | Automatically delivers or deploys validated code to another environment such as Azure or a production server. |

Relationship:

```
Git Push
      │
      ▼
Continuous Integration (CI)
      │
      ▼
Continuous Delivery / Deployment (CD)
```

Git only moves code.

CI checks whether the code can be successfully built.

CD deploys the verified application.

---

# How GitHub Actions Works

Every workflow begins with an event.

Example:

```
Developer

↓

git push

↓

GitHub Repository

↓

Workflow Trigger

↓

GitHub Runner (Ubuntu VM)

↓

Checkout Repository

↓

Setup Environment

↓

Build

↓

Run Tests

↓

Package Application

↓

(Optional) Deploy
```

Each workflow runs on a **fresh virtual machine**, meaning:

- No previous files exist.
- No dependencies are installed.
- No Docker cache exists.
- No databases are running.

Everything required must be installed or configured inside the workflow itself.

---

# Anatomy of a Workflow

A GitHub Actions workflow consists of several sections.

## 1. Workflow Name

```yaml
name: Backend CI
```

Provides the display name shown in the GitHub Actions tab.

---

## 2. Trigger

```yaml
on:
  push:
    branches:
      - main
```

Determines **when** the workflow executes.

Common triggers include:

- push
- pull_request
- schedule
- workflow_dispatch

A path filter can also be applied:

```yaml
paths:
  - 'backend/sos-backend/**'
```

This limits execution to changes within a specific folder.

---

## 3. Jobs

```yaml
jobs:
  build:
```

A workflow may contain one or more jobs.

Jobs may execute:

- Sequentially
- In parallel

Each job runs on its own runner.

---

## 4. Runner

```yaml
runs-on: ubuntu-latest
```

Specifies the operating system used for the job.

Examples:

- ubuntu-latest
- windows-latest
- macos-latest

---

## 5. Steps

Each job consists of multiple ordered steps.

Example:

```yaml
steps:
```

Each step performs one task.

---

## 6. Using Existing Actions

```yaml
uses: actions/checkout@v4
```

`uses` executes a reusable GitHub Action created by GitHub or the community.

Examples:

- Checkout repository
- Setup Java
- Login to Docker Hub
- Deploy to Azure

---

## 7. Executing Commands

```yaml
run:
```

Executes shell commands directly on the runner.

Example:

```yaml
run: mvn clean package
```

Multiple commands may be written using:

```yaml
run: |
```

---

# GitHub Runner

Every workflow executes on a temporary virtual machine called a **runner**.

Characteristics:

- Fresh operating system
- Completely isolated
- Automatically destroyed after execution
- No persistent files

If a workflow requires:

- Java
- Docker
- PostgreSQL
- Node.js

they must either be installed or started during the workflow.

---

# Workflow Badge

GitHub automatically generates a workflow badge indicating the current pipeline status.

Example:

```
🟢 Passing
🔴 Failing
```

The badge can be embedded inside the project README to display the latest CI status.

---


## Understanding Failed Workflows

A failed GitHub Actions workflow **does not** undo or remove a Git commit.

The sequence is:

```
git push
    ↓
Commit stored on GitHub
    ↓
GitHub Actions runs
    ↓
Build Success / Failure
```

If the workflow fails, the commit remains in the repository. GitHub simply reports the failure, allowing developers to identify and fix issues before deployment or before other team members continue working with the latest changes.

---

## Build Verification vs Runtime Verification

The current workflow only verifies that the project can be **built and containerized**.

It does **not** verify that the Docker container starts successfully or that the application functions correctly at runtime.

