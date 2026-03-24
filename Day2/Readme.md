 ✅ Task 1: Trigger Configuration
on:
  pull_request:
    branches:
      - main
  workflow_dispatch:

✔ Runs on Pull Request
✔ Allows manual run

✅ Task 2: Job Dependency Design (Build → Test)
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Build step
        run: echo "Building application..."

  test:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Test step
        run: echo "Running tests..."

✔ needs: build → ensures test runs after build

✅ Task 3: Using GitHub Context Variables
- name: Print Branch and Commit
  run: |
    echo "Branch Name: ${{ github.ref }}"
    echo "Commit ID: ${{ github.sha }}"

✔ ${{ github.ref }} → branch
✔ ${{ github.sha }} → commit ID

✅ Task 4: Pull Request Workflow (Full Example)
name: PR Workflow

on:
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Build
        run: echo "Building project..."

  test:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Test
        run: echo "Testing project..."

✔ Trigger → Pull Request
✔ Build → Test (dependency)

✅ Task 5: Docker Build & Push
- name: Build, Tag and Push Docker Image
  env:
    REGISTRY: docker.io
    REPOSITORY: my-username/my-app
    IMAGE_TAG: latest

  run: |
    echo "Building Docker image..."
    docker build --build-arg ENV=dev -t $REGISTRY/$REPOSITORY:$IMAGE_TAG .

    echo "Pushing image..."
    docker push $REGISTRY/$REPOSITORY:$IMAGE_TAG

    echo "Removing local image..."
    docker rmi $REGISTRY/$REPOSITORY:$IMAGE_TAG

✔ --build-arg ENV=dev → pass environment
✔ tagging → using env variables
✔ push → to registry
✔ cleanup → remove local image
.
