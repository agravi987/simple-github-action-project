# Create the Project From Scratch

This guide shows how to recreate this project step by step.

## Step 1: Create a New Folder

```bash
mkdir simple-github-action-project
cd simple-github-action-project
```

## Step 2: Initialize Git

```bash
git init
```

## Step 3: Initialize Node.js

```bash
npm init -y
```

This creates `package.json`.

## Step 4: Install Runtime Dependency

```bash
npm install express
```

Express is the web framework used to create API endpoints.

## Step 5: Install Development Dependencies

```bash
npm install --save-dev jest supertest eslint
```

These tools are used only during development and CI:

| Package | Purpose |
| --- | --- |
| `jest` | Runs automated tests |
| `supertest` | Tests HTTP endpoints without manually starting a server |
| `eslint` | Checks JavaScript code style and common mistakes |

## Step 6: Create Folder Structure

```bash
mkdir src
mkdir test
mkdir -p .github/workflows
```

On Windows PowerShell, use:

```powershell
New-Item -ItemType Directory -Force src
New-Item -ItemType Directory -Force test
New-Item -ItemType Directory -Force .github/workflows
```

## Step 7: Configure npm Scripts

Update `package.json` so the scripts section looks like this:

```json
{
  "scripts": {
    "start": "node src/app.js",
    "test": "jest --runInBand",
    "lint": "eslint"
  }
}
```

Script meaning:

| Script | Command | Purpose |
| --- | --- | --- |
| `npm start` | `node src/app.js` | Starts the API |
| `npm test` | `jest --runInBand` | Runs tests |
| `npm run lint` | `eslint` | Runs lint checks |

## Step 8: Add Application Code

Create `src/app.js`. The complete code is explained in [Application Code Walkthrough](03-application-code-walkthrough.md).

## Step 9: Add Tests

Create `test/app.test.js`. The complete test setup is explained in [Testing and Linting](04-testing-and-linting.md).

## Step 10: Add Docker Files

Create:

- `Dockerfile`
- `.dockerignore`

Docker setup is explained in [Docker Guide](05-docker-guide.md).

## Step 11: Add GitHub Actions Workflow

Create:

```text
.github/workflows/ci.yml
```

The workflow is explained in [GitHub Actions CI/CD](06-github-actions-cicd.md).

## Step 12: Commit the Project

```bash
git add .
git commit -m "Create simple Node.js CI Docker project"
```

## Step 13: Push to GitHub

Create an empty GitHub repository, then connect your local project:

```bash
git branch -M main
git remote add origin https://github.com/<your-username>/simple-github-action-project.git
git push -u origin main
```

Replace `<your-username>` with your GitHub username.

