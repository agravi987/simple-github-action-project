# Docker Guide

This project includes a Dockerfile so the API can run inside a container.

## Dockerfile

The Dockerfile is:

```text
Dockerfile
```

## Complete Dockerfile

```dockerfile
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

RUN npm ci --omit=dev

COPY src ./src

EXPOSE 3000

CMD [ "node", "src/app.js" ]
```

## Dockerfile Explanation

| Line | Purpose |
| --- | --- |
| `FROM node:20-alpine` | Uses a lightweight Node.js 20 image |
| `WORKDIR /app` | Sets `/app` as the working directory inside the container |
| `COPY package*.json ./` | Copies dependency files first for better Docker layer caching |
| `RUN npm ci --omit=dev` | Installs only production dependencies |
| `COPY src ./src` | Copies application source code |
| `EXPOSE 3000` | Documents that the app listens on port 3000 |
| `CMD [ "node", "src/app.js" ]` | Starts the app when the container runs |

## .dockerignore

The `.dockerignore` file prevents unnecessary files from being copied into the Docker image.

Current content:

```text
node_modules
npm-debug.log
.git
.github
Dockerfile
coverage
```

## Build Docker Image Locally

```bash
docker build -t student-api:local .
```

## Run Docker Container Locally

```bash
docker run --rm -p 3000:3000 student-api:local
```

This maps:

```text
host port 3000 -> container port 3000
```

## Test the Running Container

Open another terminal:

```bash
curl http://localhost:3000/health
curl http://localhost:3000/students
```

Expected health response:

```json
{
  "status": "ok"
}
```

## Stop the Container

If you used `docker run --rm -p 3000:3000 student-api:local`, press:

```text
Ctrl + C
```

## List Local Images

```bash
docker images
```

## Remove Local Image

```bash
docker rmi student-api:local
```

