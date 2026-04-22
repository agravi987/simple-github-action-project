# Application Code Walkthrough

This page explains the Express API in plain language. The main file is:

```text
src/app.js
```

## What This File Is Responsible For

| Responsibility | Where It Happens |
| --- | --- |
| Create Express app | `const app = express()` |
| Accept JSON | `app.use(express.json())` |
| Expose health route | `GET /health` |
| Expose student route | `GET /students` |
| Start server | `app.listen(...)` |
| Support tests | `module.exports = app` |

## Complete Code

```js
const express = require("express");

const app = express();
app.use(express.json());

app.get("/health", (req, res) => {
  res.status(200).json({ status: "ok" });
});

app.get("/students", (req, res) => {
  res.status(200).json([
    { id: 1, name: "Ravi", dept: "CSE" },
    { id: 2, name: "Anu", dept: "ECE" },
  ]);
});

if (require.main === module) {
  const PORT = process.env.PORT || 3000;
  app.listen(PORT, () => {
    console.log(`Server is running on port ${PORT}`);
  });
} else {
  console.log("App module loaded");
}

module.exports = app;
```

## Walkthrough

### Import Express

```js
const express = require("express");
```

This imports the Express package.

Express gives us a simple way to define API routes like `/health` and `/students`.

### Create the App

```js
const app = express();
app.use(express.json());
```

This creates an Express application and allows it to read JSON request bodies.

### Health Endpoint

```js
app.get("/health", (req, res) => {
  res.status(200).json({ status: "ok" });
});
```

This endpoint is useful for health checks. It confirms that the application is running.

Try it:

```bash
curl http://localhost:3000/health
```

### Students Endpoint

```js
app.get("/students", (req, res) => {
  res.status(200).json([
    { id: 1, name: "Ravi", dept: "CSE" },
    { id: 2, name: "Anu", dept: "ECE" },
  ]);
});
```

This endpoint returns sample student data.

Try it:

```bash
curl http://localhost:3000/students
```

### Start Server Only When Needed

```js
if (require.main === module) {
  const PORT = process.env.PORT || 3000;
  app.listen(PORT, () => {
    console.log(`Server is running on port ${PORT}`);
  });
}
```

This starts the server when you run:

```bash
npm start
```

The `PORT` value can come from an environment variable. If no value is provided, the app uses port `3000`.

> [!NOTE]
> This pattern keeps the app testable. Tests can import the app without accidentally starting a real server.

### Export App for Tests

```js
module.exports = app;
```

This allows the test file to import the Express app directly.

This is important because Supertest can test the API without needing a separate manual server process.

## Run It Locally

```bash
npm start
```

Expected output:

```text
Server is running on port 3000
```

## Verify It

Open another terminal:

```bash
curl http://localhost:3000/health
curl http://localhost:3000/students
```

## What Good Looks Like

| Command | Expected Result |
| --- | --- |
| `curl http://localhost:3000/health` | JSON response with `status` equal to `ok` |
| `curl http://localhost:3000/students` | JSON array containing student records |
