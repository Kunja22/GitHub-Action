# LAB NOTES – GitHub Actions CI/CD Project

---

# ✅ Task 1 – Hello GitHub Actions Workflow

## 🎯 Purpose:
To test basic GitHub Actions workflow setup and ensure CI pipeline is working.

## ⚙️ Key Configuration:
- Trigger: push event
- Runner: ubuntu-latest
- Simple echo command

## 🔐 Secrets Used:
None

## ✅ How to Verify:
- Go to GitHub Actions tab
- Check workflow run success
- Output: "Hello GitHub Actions!" in logs

---

# 🐳 Task 2 – Docker Build & Push

## 🎯 Purpose:
To automate Docker image build and push to Docker Hub.

## ⚙️ Key Configuration:
- Dockerfile created for application
- Multi-step workflow:
  - Checkout code
  - Login to DockerHub
  - Build Docker image
  - Tag image (latest + commit SHA)
  - Push to Docker Hub

## 🔐 Secrets Used:
- DOCKER_USERNAME → Docker Hub login username
- DOCKER_PASSWORD → Docker Hub access password/token

## ✅ How to Verify:
- Check GitHub Actions logs
- Verify Docker images in Docker Hub:
  - latest tag
  - commit SHA tag

---

# 🔁 Task 3 – Reusable Workflow (CI/CD)

## 🎯 Purpose:
To create centralized reusable workflow for Docker CI/CD pipeline.

## ⚙️ Key Configuration:
- workflow_call used for reusability
- Inputs:
  - image_name
  - tag
- Versioned using GitHub Release (v1.0.0)

## 🔐 Secrets Used:
- DOCKER_USERNAME
- DOCKER_PASSWORD

## ✅ How to Verify:
- Caller workflow triggers reusable workflow
- Images built for:
  - staging-<commit_sha>
  - prod-<version>
- Check Actions logs

---

# 🔒 Task 4 – Security & Notifications

## 🎯 Purpose:
To improve security and monitoring in CI/CD pipeline.

## ⚙️ Key Configuration:
- Trivy image scanner added
- Fails pipeline on HIGH/CRITICAL vulnerabilities
- Slack notifications added for success and failure events

## 🔐 Secrets Used:
- DOCKER_USERNAME
- DOCKER_PASSWORD
- SLACK_WEBHOOK_URL

## ✅ How to Verify:
- If vulnerability found → pipeline fails
- Slack receives notification:
  - Success message on build completion
  - Failure message on error

---

# 📦 Overall Deliverables

## App Repository Contains:
- .github/workflows/hello.yml
- Dockerfile
- .dockerignore
- Caller workflow (docker-ci.yml usage)
- LAB-NOTES.md

## Workflow Repository Contains:
- .github/workflows/docker-ci.yml
- GitHub Release v1.0.0

## Docker Hub:
- myapp:latest
- myapp:<commit_sha>
- staging-<commit_sha>
- prod-<version>

---

# 🚀 Final Outcome

This project demonstrates:
- CI (Continuous Integration)
- CD (Continuous Deployment)
- Reusable workflows
- Docker automation
- Security scanning
- Notification system
- Real-world DevOps pipeline design
