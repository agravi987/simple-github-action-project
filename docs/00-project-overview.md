# Project Overview

## Goal

The goal of this project is to demonstrate a complete beginner DevOps workflow using a simple Node.js API.

By the end, you should understand how source code moves through this path:

```text
Developer writes code
        |
        v
Code is pushed to GitHub
        |
        v
GitHub Actions runs lint and tests
        |
        v
Docker image is built
        |
        v
Docker image is pushed to Docker Hub
```

## Technology Stack

| Area | Tool |
| --- | --- |
| Runtime | Node.js 20 |
| Web framework | Express |
| Testing | Jest and Supertest |
| Linting | ESLint |
| Containerization | Docker |
| CI/CD | GitHub Actions |
| Image registry | Docker Hub |

## Current Repository Structure

```text
simple-github-action-project/
  .github/
    workflows/
      ci.yml
  docs/
  src/
    app.js
  test/
    app.test.js
  .dockerignore
  .gitignore
  Dockerfile
  eslint.config.js
  package-lock.json
  package.json
  README.md
```

## What the API Does

The API exposes two endpoints:

| Method | Endpoint | Purpose |
| --- | --- | --- |
| GET | `/health` | Confirms the API is running |
| GET | `/students` | Returns a sample student list |

Example response from `/health`:

```json
{
  "status": "ok"
}
```

Example response from `/students`:

```json
[
  {
    "id": 1,
    "name": "Ravi",
    "dept": "CSE"
  },
  {
    "id": 2,
    "name": "Anu",
    "dept": "ECE"
  }
]
```

## CI/CD Behavior

The workflow file is located at:

```text
.github/workflows/ci.yml
```

It runs when:

- Code is pushed to the `main` branch.
- A pull request is opened against the `main` branch.

For pull requests, it runs:

- Checkout
- Node.js setup
- Dependency installation
- Linting
- Tests
- Docker build setup

For pushes to `main`, it also:

- Logs in to Docker Hub.
- Builds the Docker image.
- Pushes Docker image tags to Docker Hub.

