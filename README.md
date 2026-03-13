# Java CI/CD Pipeline with GitHub Actions

A Java Gradle project with a fully automated CI/CD pipeline built with GitHub Actions.

## Pipeline Overview

Every push or pull request to `main` triggers the following:
```
push to main
  ├── build (ubuntu + macOS)       → compiles and tests the app
  ├── dependency-submission        → scans dependencies for vulnerabilities
  └── build-and-push-docker        → builds Docker image and pushes to Docker Hub
```

## What I Learned

- Workflow YAML structure (`on`, `jobs`, `steps`)
- Runners and how each job gets a fresh virtual machine
- `uses` vs `run` in workflow steps
- Build matrix to test across multiple operating systems
- GitHub Secrets for storing sensitive credentials
- Docker image build and push via GitHub Actions

## Tech Stack

- Java + Gradle
- GitHub Actions
- Docker / Docker Hub
- Ubuntu & macOS runners

## Secrets Required

| Secret | Description |
|--------|-------------|
| `DOCKERHUB_USERNAME` | Docker Hub username |
| `DOCKERHUB_TOKEN` | Docker Hub access token |

## Local Development

##### Build the project
    ./gradlew build

##### Build Docker image
    docker build -t java-app .

##### Push image to repo
    docker tag java-app demo-app:java-1.0
