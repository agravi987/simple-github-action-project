# Simple GitHub Action Project

This repository is a beginner-friendly Node.js DevOps project. It contains a small Express API, automated tests, linting, a Dockerfile, and a GitHub Actions workflow that can build and push a Docker image to Docker Hub.

## What This Project Teaches

- How to create a simple Node.js API.
- How to test an API with Jest and Supertest.
- How to lint JavaScript code with ESLint.
- How to containerize the API with Docker.
- How to automate checks with GitHub Actions.
- How to publish Docker images from CI/CD using GitHub repository secrets.

## Project Documentation

Follow these files in order:

1. [Project Overview](docs/00-project-overview.md)
2. [Prerequisites](docs/01-prerequisites.md)
3. [Create the Project From Scratch](docs/02-create-project-from-scratch.md)
4. [Application Code Walkthrough](docs/03-application-code-walkthrough.md)
5. [Testing and Linting](docs/04-testing-and-linting.md)
6. [Docker Guide](docs/05-docker-guide.md)
7. [GitHub Actions CI/CD](docs/06-github-actions-cicd.md)
8. [Docker Hub Secrets](docs/07-docker-hub-secrets.md)
9. [Troubleshooting](docs/08-troubleshooting.md)
10. [Final Checklist](docs/09-final-checklist.md)

## Quick Start

```bash
npm ci
npm run lint
npm test
npm start
```

Open another terminal and test the API:

```bash
curl http://localhost:3000/health
curl http://localhost:3000/students
```

