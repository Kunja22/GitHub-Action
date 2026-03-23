🚀 CI/CD (Continuous Integration & Continuous Deployment)

CI/CD is a DevOps practice that automates the process of building, testing, and deploying applications.

🔹 Continuous Integration (CI)
Developers push code to a repository (e.g., GitHub)
Code is automatically built and tested
Helps detect bugs early
🔹 Continuous Deployment (CD)
After successful testing, code is automatically deployed to server/cloud
Reduces manual work and speeds up delivery

❌ Task 1: Problems Without CI/CD
Without CI/CD, the software development process becomes slow, error-prone, and difficult to manage.
Manual Deployment – Deployments are done manually, increasing the risk of human errors.
Integration Issues – Merging code from multiple developers can cause conflicts and broken builds.
No Automated Testing – Bugs may go unnoticed and reach production.
Slow Releases – Delivery of new features is delayed due to manual processes.
Environment Inconsistency – Code may work in development but fail in production.
Difficult Rollbacks – Fixing failed deployments is complex and time-consuming.
Limited Visibility – Hard to track changes, errors, and deployment status.

⚙️ Task 2: Explore GitHub Actions in a Repository

GitHub Actions is a CI/CD tool used to automate workflows like build, test, and deployment directly from a GitHub repository.

🔹 Key Points
Workflows are defined in .github/workflows/ using YAML
Triggered by events like push and pull_request
Runs jobs on GitHub-hosted or self-hosted runners
🔹 Workflow Process
Code is pushed to the repository
Workflow is triggered automatically
Steps like install, build, and test are executed
Results are shown in the Actions tab
🔹 Example Workflow
name: CI Pipeline

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3
      - run: npm install
      - run: npm test

      🔄 Task 3: Arrange the CI/CD Pipeline Flow

# Task3 The CI/CD pipeline defines the automated steps from code commit to deployment.

🔹 Pipeline Flow
Code Commit
Developer pushes code to the GitHub repository
Trigger Workflow
GitHub Actions workflow is triggered on push
Build Stage
Application dependencies are installed and build is created
Test Stage
Automated tests are executed to ensure code quality
Docker Build (Optional)
Docker image is created for the application
Deployment Stage
Application is deployed to server (e.g., AWS EC2 / Kubernetes)
Monitoring & Feedback
Logs and results are checked for success or failure
