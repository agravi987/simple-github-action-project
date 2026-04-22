# Documentation Home

Welcome to the project handbook. These docs are written for beginner DevOps engineers who want to understand not just what to run, but why each step exists.

## Recommended Reading Path

| Order | Document | Outcome |
| --- | --- | --- |
| 1 | [Project Overview](00-project-overview.md) | Understand the full system |
| 2 | [Prerequisites](01-prerequisites.md) | Prepare your machine and accounts |
| 3 | [Create From Scratch](02-create-project-from-scratch.md) | Rebuild the project manually |
| 4 | [Application Code](03-application-code-walkthrough.md) | Understand the API |
| 5 | [Testing and Linting](04-testing-and-linting.md) | Validate code quality |
| 6 | [Docker Guide](05-docker-guide.md) | Build and run a container |
| 7 | [GitHub Actions CI/CD](06-github-actions-cicd.md) | Automate the pipeline |
| 8 | [Docker Hub Secrets](07-docker-hub-secrets.md) | Configure secure publishing |
| 9 | [Troubleshooting](08-troubleshooting.md) | Fix common problems |
| 10 | [Final Checklist](09-final-checklist.md) | Confirm end-to-end success |

## Learning Milestones

By the end, you should be able to explain:

- How a Node.js API is structured.
- How automated API tests work.
- Why linting belongs in CI.
- How Docker builds a repeatable image.
- How GitHub Actions runs on pull requests and pushes.
- Why secrets are used for Docker Hub credentials.

## Fast Validation Commands

```bash
npm ci
npm run lint
npm test
docker build -t student-api:local .
```

If these commands pass locally, you are ready to push and let GitHub Actions do the same checks online.

