✅ Task 1: Trigger Configuration
 on:
  pull_request:
    branches:
      - main
  workflow_dispatch:
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
✅ Task 3: Using GitHub Context Variables
  - name: Print Branch and Commit
  run: |
    echo "Branch Name: ${{ github.ref }}"
    echo "Commit ID: ${{ github.sha }}"
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
