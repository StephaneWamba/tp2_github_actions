# CI/CD Pipeline Documentation

## Overview
This directory contains GitHub Actions workflows for continuous integration and deployment of the application.

## Workflows

### Main CI Pipeline (`main.yml`)
- **Purpose**: Basic continuous integration pipeline
- **Triggers**: 
  - Push to `main` and `develop` branches
  - Pull requests to `main` and `develop` branches
- **Jobs**:
  - `test-backend`: Builds and tests the backend application
    - Uses JDK 21
    - Runs Maven build and tests
    - Includes testcontainers for database testing

## Security
- Docker Hub credentials are stored as GitHub Secrets
- SonarCloud token is stored as a GitHub Secret
- No sensitive information is exposed in workflow files

## Pipeline Phases
1. **Basic CI** (Current)
   - Maven build and test
   - Testcontainers integration

2. **Docker Integration** (Planned)
   - Docker image building
   - Docker Hub publishing
   - Conditional pushes based on branch

3. **Quality Gate** (Planned)
   - SonarCloud integration
   - Code quality analysis
   - Quality gate enforcement

4. **Pipeline Optimization** (Planned)
   - Workflow separation
   - Branch-specific configurations
   - Workflow dependencies

## Questions and Answers

### What are testcontainers?
Testcontainers are Java libraries that enable running Docker containers during testing. They provide:
- Isolated test environments
- Automatic container lifecycle management
- Easy integration with testing frameworks
- Support for various databases and services

### Why use secured variables?
Secured variables (GitHub Secrets) are used to:
- Protect sensitive information (credentials, tokens)
- Prevent exposure of secrets in logs or code
- Enable secure access to external services
- Follow security best practices

### Why use needs: build-and-test-backend?
The `needs` keyword ensures that:
- Docker build jobs only run after successful tests
- Prevents building images from failing code
- Maintains pipeline integrity
- Saves resources by not building on failed tests

### Why push Docker images?
Docker images are pushed to:
- Make the application easily deployable
- Enable consistent environments across deployments
- Facilitate version control of the application
- Support container orchestration
- Enable easy rollbacks if needed

## Troubleshooting
Common issues and solutions will be added as they are encountered during implementation.

# CI (Phase 1) Checkpoint: GitHub Actions Workflow

## Overview

This folder contains the GitHub Actions workflow (main.yml) for our CI pipeline. In Phase 1, the workflow is triggered on every push (or pull request) to the main and develop branches. It checks out the code, sets up JDK 21 (using Temurin), and then runs a Maven build (with "mvn clean verify") on the simple-api module (using the pom.xml located in ./simple-api).

## Workflow (main.yml)

- **Trigger:** Push (or pull request) on branches "main" and "develop".
- **Job (test-backend):**
  - Runs on ubuntu-24.04.
  - Steps:
    1. Checkout (using actions/checkout@v4).
    2. Set up JDK 21 (using actions/setup-java@v4, Temurin distribution).
    3. Build and test (using "mvn clean verify --file ./simple-api/pom.xml").
- **Note:** In later phases (e.g. Phase 3), SonarCloud analysis (and Docker integration) will be added.

## Checkpoint (Phase 1)

- **Commit:** "Initial commit: Integrate GitHub Actions CI (Phase 1)" (or equivalent) was pushed to the GitHub repository.
- **Verification:** The workflow (main.yml) is now live and (if green) confirms that our backend (simple-api) builds and passes all tests (including integration tests via testcontainers).

---

*This README is updated as part of our CI (Phase 1) checkpoint.* 