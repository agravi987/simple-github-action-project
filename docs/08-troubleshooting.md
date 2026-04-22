# Troubleshooting

Use this guide when something fails locally or in GitHub Actions.

## `npm ci` Fails

Possible causes:

- `package-lock.json` is missing.
- `package.json` and `package-lock.json` do not match.
- Node.js version is incompatible.

Fix:

```bash
rm -rf node_modules package-lock.json
npm install
npm ci
```

PowerShell alternative:

```powershell
Remove-Item -Recurse -Force node_modules
Remove-Item -Force package-lock.json
npm install
npm ci
```

## `npm run lint` Fails

Common causes:

- Missing semicolon.
- Single quotes used instead of double quotes.

Example fix:

```js
const message = "hello";
```

## `npm test` Fails

Check:

- Is `src/app.js` exporting the app?
- Did the endpoint path change?
- Did the expected response body change?

Run:

```bash
npm test
```

Read the failed test name and compare it with the API code.

## Port 3000 Already in Use

The app defaults to port `3000`.

Run on another port:

```bash
PORT=4000 npm start
```

PowerShell:

```powershell
$env:PORT=4000
npm start
```

Then test:

```bash
curl http://localhost:4000/health
```

## Docker Build Fails

Run:

```bash
docker build -t student-api:local .
```

Check:

- Docker Desktop is running.
- `package-lock.json` exists.
- The Dockerfile is named exactly `Dockerfile`.
- You are running the command from the project root.

## Docker Container Starts but API Does Not Respond

Check that the port mapping is correct:

```bash
docker run --rm -p 3000:3000 student-api:local
```

The first `3000` is your computer's port.

The second `3000` is the container's port.

## GitHub Actions Cannot Login to Docker Hub

Check repository secrets:

- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`

Also check:

- The Docker Hub token was copied correctly.
- The token has not expired.
- The secret names match the workflow exactly.

## Docker Image Is Not Pushed for Pull Requests

This is expected.

The workflow has this condition:

```yaml
if: github.event_name == 'push'
```

Docker login and image push happen only when code is pushed to `main`.

## GitHub Actions Workflow Does Not Start

Check:

- The workflow file is inside `.github/workflows/`.
- The file extension is `.yml` or `.yaml`.
- You pushed to `main` or opened a pull request to `main`.
- The repository has GitHub Actions enabled.

