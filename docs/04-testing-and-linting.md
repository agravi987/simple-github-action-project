# Testing and Linting

This project uses automated tests and linting to catch problems before code is merged or deployed.

## Test File

The test file is:

```text
test/app.test.js
```

## Complete Test Code

```js
const request = require("supertest");
const app = require("../src/app");

describe("Student API", () => {
  test("GET /health should return ok", async () => {
    const res = await request(app).get("/health");
    expect(res.statusCode).toBe(200);
    expect(res.body.status).toBe("ok");
  });

  test("GET /students should return student list", async () => {
    const res = await request(app).get("/students");
    expect(res.statusCode).toBe(200);
    expect(Array.isArray(res.body)).toBe(true);
    expect(res.body.length).toBeGreaterThan(0);
  });
});
```

## What the Tests Check

| Test | What It Verifies |
| --- | --- |
| `GET /health should return ok` | `/health` returns HTTP 200 and `{ "status": "ok" }` |
| `GET /students should return student list` | `/students` returns HTTP 200 and an array with data |

## Run Tests Locally

```bash
npm test
```

Expected result:

```text
PASS test/app.test.js
```

## Why `--runInBand` Is Used

The test script is:

```json
"test": "jest --runInBand"
```

`--runInBand` tells Jest to run tests in a single process. For a small project, this is simple and predictable, especially in CI.

## ESLint Configuration

The ESLint config file is:

```text
eslint.config.js
```

Current rules:

```js
module.exports = [
  {
    files: ["**/*.js"],
    languageOptions: {
      ecmaVersion: "latest",
      sourceType: "commonjs",
    },
    rules: {
      semi: ["error", "always"],
      quotes: ["error", "double"],
    },
  },
];
```

## What ESLint Checks

| Rule | Meaning |
| --- | --- |
| `semi` | JavaScript statements must end with semicolons |
| `quotes` | Strings must use double quotes |

## Run Lint Locally

```bash
npm run lint
```

If there are no lint errors, the command exits successfully.

## Recommended Local Validation Order

Before pushing code to GitHub, run:

```bash
npm ci
npm run lint
npm test
```

This is similar to what GitHub Actions does in CI.

