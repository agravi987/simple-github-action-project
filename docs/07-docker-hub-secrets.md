# Docker Hub Secrets

The GitHub Actions workflow needs Docker Hub credentials to push images.

Never write Docker Hub passwords or tokens directly inside workflow files.

Use GitHub repository secrets instead.

## Required Secrets

| Secret Name | Value |
| --- | --- |
| `DOCKERHUB_USERNAME` | Your Docker Hub username |
| `DOCKERHUB_TOKEN` | A Docker Hub access token |

## Create a Docker Hub Access Token

1. Log in to Docker Hub.
2. Go to account settings.
3. Open security settings.
4. Create a new access token.
5. Copy the token value.

Use an access token instead of your Docker Hub account password.

## Add Secrets to GitHub

1. Open your GitHub repository.
2. Click `Settings`.
3. Click `Secrets and variables`.
4. Click `Actions`.
5. Click `New repository secret`.
6. Add `DOCKERHUB_USERNAME`.
7. Add `DOCKERHUB_TOKEN`.

## Confirm Image Name

The workflow pushes images using this format:

```text
<dockerhub-username>/student-api:latest
<dockerhub-username>/student-api:<git-commit-sha>
```

Example:

```text
mydockeruser/student-api:latest
mydockeruser/student-api:abc123...
```

## Verify Image on Docker Hub

After pushing to `main`:

1. Open Docker Hub.
2. Go to your repositories.
3. Open `student-api`.
4. Check the `Tags` section.

You should see:

- `latest`
- A commit SHA based tag

## Pull and Run Published Image

Replace `<dockerhub-username>` with your Docker Hub username:

```bash
docker pull <dockerhub-username>/student-api:latest
docker run --rm -p 3000:3000 <dockerhub-username>/student-api:latest
```

Test it:

```bash
curl http://localhost:3000/health
```

