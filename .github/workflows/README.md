# CI (Phase 1) Checkpoint: "First CI with backend test"

## Overview

This folder contains the GitHub Actions workflow (main.yml) for our CI pipeline. In Phase 1, the workflow is triggered on every push (or pull request) to the "main" and "develop" branches. It checks out the code, sets up JDK 21 (using Temurin), and then runs a Maven build (with "mvn clean verify") on the "simple-api" module (using the pom.xml located in ./simple-api).

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