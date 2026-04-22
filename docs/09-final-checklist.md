# Final Checklist

Use this page as your end-to-end completion report. When everything here is checked, the project is working from local development to Docker Hub publishing.

## Local Project Checklist

- [ ] `package.json` exists.
- [ ] `package-lock.json` exists.
- [ ] `src/app.js` exists.
- [ ] `test/app.test.js` exists.
- [ ] `eslint.config.js` exists.
- [ ] `Dockerfile` exists.
- [ ] `.dockerignore` exists.
- [ ] `.github/workflows/ci.yml` exists.

## Local Validation

Run these commands from the project root:

```bash
npm ci
npm run lint
npm test
docker build -t student-api:local .
docker run --rm -p 3000:3000 student-api:local
```

In another terminal:

```bash
curl http://localhost:3000/health
curl http://localhost:3000/students
```

Expected result:

- `/health` returns `{ "status": "ok" }`.
- `/students` returns a JSON array.

## GitHub Checklist

- [ ] Repository is pushed to GitHub.
- [ ] Default branch is `main`.
- [ ] GitHub Actions is enabled.
- [ ] Workflow appears in the `Actions` tab.
- [ ] Pull request checks run successfully.

## Docker Hub Checklist

- [ ] Docker Hub account exists.
- [ ] Docker Hub access token is created.
- [ ] GitHub secret `DOCKERHUB_USERNAME` is configured.
- [ ] GitHub secret `DOCKERHUB_TOKEN` is configured.
- [ ] Push to `main` creates Docker image tags.
- [ ] Docker Hub repository contains `student-api`.

## End-to-End Success Criteria

The project is working end to end when:

1. The app runs locally.
2. The API endpoints return expected JSON.
3. Lint passes locally.
4. Tests pass locally.
5. Docker image builds locally.
6. Docker container runs locally.
7. GitHub Actions passes on pull requests.
8. GitHub Actions pushes Docker image on `main`.
9. Docker Hub shows `latest` and commit SHA image tags.

## Final Confidence Check

| Question | Good Answer |
| --- | --- |
| Can a new developer run the app locally? | Yes |
| Can CI catch broken code? | Yes |
| Can the app be packaged as Docker image? | Yes |
| Can GitHub Actions publish the image? | Yes |
| Can someone follow the docs from zero? | Yes |
