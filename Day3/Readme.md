# Shared CI Workflow Example

## Overview

This project demonstrates **how to create and reuse a shared CI workflow** using GitHub Actions.

- **Task 1:** Create a **Shared CI Quality Check Workflow** in a central repository (`shared-workflows`).
- **Task 2:** Call the **shared workflow** from another repository (`demo-project`).

---

## Task 1: Create a Shared CI Quality Check Workflow

### Steps:

1. **Create a central repository**  
   - Name it `shared-workflows`.

2. **Create workflow file**  
   - Path: `.github/workflows/shared-ci.yml`

3. **Add workflow content**:

```yaml
name: shared-ci-quality-check

on:
  workflow_call:

jobs:
  quality-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run Basic CI check
        run: echo "Running Shared CI Quality Check"
      - uses: actions/setup-node@v4
        with:
          node-version: 18
      - run: npm install
      - run: npm run lint    # Optional: remove if no lint script
      - run: npm test        # Optional: remove if no test script
Task 2: Call Shared Workflow from Another Repository
Steps:
Go to your project repository, e.g., demo-project.
Create workflow file: .github/workflows/ci.yml
Add this content:
name: Demo Project CI

on:
  push:
    branches:
      - main
  pull_request:

jobs:
  call-shared-ci:
    uses: <USERNAME_OR_ORG>/shared-workflows/.github/workflows/shared-ci.yml@main

Replace <USERNAME_OR_ORG> with your GitHub username or organization name.

Commit & push changes to demo-project.
How it works:
When you push to main or open a pull request, the workflow in demo-project calls the shared workflow in shared-workflows.
The shared workflow runs steps like checkout, CI checks, Node setup, npm install, lint, and tests.
