# Prerequisites

Before writing code, make sure your machine and accounts are ready. This avoids half the usual beginner setup problems.

## Required Tools

| Tool | Why It Is Needed |
| --- | --- |
| Git | To track source code and push to GitHub |
| Node.js 20 | To run the Express app and npm commands |
| npm | To install project dependencies |
| Docker Desktop | To build and run Docker containers locally |
| GitHub account | To host the repository and run GitHub Actions |
| Docker Hub account | To publish Docker images |

> [!IMPORTANT]
> Node.js 20 is the version used in the Dockerfile and GitHub Actions workflow. Using the same version locally keeps behavior consistent.

## Version Check

Run these commands in a terminal:

```bash
git --version
node --version
npm --version
docker --version
```

Expected examples:

```text
git version 2.x.x
v20.x.x
10.x.x
Docker version 2x.x.x
```

The exact patch versions can be different. The important part is that Node.js is version `20.x.x` or compatible.

## Recommended Editor

Visual Studio Code is a good choice for this project.

Helpful extensions:

- ESLint
- Docker
- GitHub Actions

## Accounts to Prepare

Create accounts here:

- GitHub: https://github.com
- Docker Hub: https://hub.docker.com

You need Docker Hub credentials later when configuring GitHub repository secrets.

## Ready Check

You are ready to continue when:

- `git --version` works.
- `node --version` shows Node.js 20 or compatible.
- `npm --version` works.
- `docker --version` works.
- You can log in to GitHub.
- You can log in to Docker Hub.
