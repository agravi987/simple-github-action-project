# Application Code Walkthrough

The main application file is:

```text
src/app.js
```

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

## Line-by-Line Explanation

### Import Express

```js
const express = require("express");
```

This imports the Express package.

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

Test it locally:

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

Test it locally:

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

### Export App for Tests

```js
module.exports = app;
```

This allows the test file to import the Express app directly.

This is important because Supertest can test the API without needing a separate manual server process.

## Run the App

```bash
npm start
```

Expected output:

```text
Server is running on port 3000
```

## Verify the App

Open another terminal:

```bash
curl http://localhost:3000/health
curl http://localhost:3000/students
```

