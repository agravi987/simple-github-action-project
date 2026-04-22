# Docker Guide

Docker packages the app with everything it needs to run. Instead of saying "it works on my machine," we build an image that can run the same way in many places.

## What Docker Adds

| Without Docker | With Docker |
| --- | --- |
| You manually prepare Node.js and dependencies | The image contains the app setup |
| Environment differences can break the app | The container runs consistently |
| Deployment is harder to repeat | Image build and run steps are repeatable |

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

> [!NOTE]
> `EXPOSE 3000` is documentation inside the image. The actual port connection happens when you run `docker run -p 3000:3000`.

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

## Build the Image

```bash
docker build -t student-api:local .
```

The tag means:

```text
image name: student-api
image tag:  local
```

## Run the Container

```bash
docker run --rm -p 3000:3000 student-api:local
```

This maps:

```text
host port 3000 -> container port 3000
```

`--rm` removes the stopped container automatically.

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

## Stop It

If you used `docker run --rm -p 3000:3000 student-api:local`, press:

```text
Ctrl + C
```

## Useful Docker Commands

```bash
docker images
docker ps
docker ps -a
```

Remove the local image when you no longer need it:

```bash
docker rmi student-api:local
```
