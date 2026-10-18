# Node.js Roadmap: From Zero to Your Own Servers and APIs

This roadmap takes you from zero to building and deploying your own servers and APIs with Node.js in 42 sessions (7 weeks, about 130 hours). Node.js lets JavaScript run outside the browser: on your computer as tools and scripts, and on a server as the back end of apps. It stands alone: the first 4 sessions are a compact JavaScript primer, so you do not need the JavaScript roadmap first (if you did it, skim days 1-4). By the end you can build a REST API with a real database, logins, tests and Docker, and put it on the internet.

## Start here

**What Node.js is.** A browser can run JavaScript but cannot read your files or listen for network requests. Node.js is a program that runs JavaScript on its own, with those abilities. You write `server.js`, run `node server.js`, and your computer becomes a server.

**Setup (30 minutes, once):**

1. Install **VS Code**.
2. Install **Node.js** (the LTS version) from nodejs.org. In a terminal, check `node -v` and `npm -v`.
3. Learn five terminal commands: `cd`, `ls` (or `dir`), `mkdir`, `pwd`, and `clear`. On Windows, use WSL2 or Git Bash if you can.
4. Make a folder `node-roadmap` with one folder per day. Run `git init` and commit at the end of every session.
5. Install **Postman** or the VS Code extension **REST Client**, for testing APIs from day 14 on.

**How one session works (about 3 hours):**

| Minutes | Step | What you do |
| --- | --- | --- |
| 10 | Start | Re-type from memory one snippet from last session. |
| 40 | Learn | Read the listed source, typing every example. |
| 90 | Build | Write the day's program without copying. |
| 30 | Break it | Cause errors on purpose (wrong path, bad JSON, crashed server) and read each error. |
| 10 | Save | `git commit` and write 3 journal lines. |

The 6th session each week is a 4-hour project and review. A session is done only when the program runs with no errors, is committed, and you can explain it line by line.

## Part 1 (weeks 1-2, days 1-12): JavaScript primer and the Node runtime

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 1 | Programming basics: variables (`let`, `const`), values (string, number, boolean), operators, `console.log`, template strings. Run a file with `node file.js`. | A profile card and a tip calculator. | They run from the terminal. |
| 2 | Conditions (`if`, `switch`, ternary) and loops (`for`, `while`, `for...of`). | FizzBuzz and a multiplication table. | You can trace each loop on paper. |
| 3 | Functions (declaration and arrow), arrays and array methods (`map`, `filter`, `reduce`), objects. | Statistics on an array of student objects. | You replaced a loop with `map` or `filter`. |
| 4 | Primer wrap-up: strings, destructuring, spread, `try`/`catch`, JSON (`JSON.parse`, `JSON.stringify`). **Project.** | A contact book kept in an array and printed to the console. | It handles bad input without crashing. |
| 5 | The Node runtime: what V8 is, the event loop in plain words, `process`, `process.argv`, `process.env`, exit codes. Modules: ES modules (`import`/`export`) vs CommonJS (`require`). | A script that greets the name you pass on the command line. | You can explain the two module styles. |
| 6 | **Project and review.** | A command-line unit converter (`node convert.js 10 km mi`). | Prints a usage message when arguments are wrong. |
| 7 | npm: `package.json`, `npm init`, installing packages, `dependencies` vs `devDependencies`, scripts (`npm start`), `node_modules`, `.gitignore`, semantic versions, `package-lock.json`. | Install `chalk` and `nanoid` and use them in a script. | A fresh clone runs after `npm install`. |
| 8 | Built-in modules: `fs` (read, write, append, `readdir`), `path`, `os`, `url`. Paths that work on every OS. | A script that lists a folder's files with sizes. | It runs on any folder without hard-coded paths. |
| 9 | Asynchronous Node: callbacks, promises, `async`/`await`, `fs/promises`, `Promise.all`, error handling in async code. | A script that reads 5 JSON files in parallel and merges them. | Failures in one file are reported but do not crash the rest. |
| 10 | Events and streams: `EventEmitter`, `Buffer`, readable and writable streams, `pipeline`, reading a large file line by line. | A log analyser that counts errors in a 100 MB log file. | Memory use stays low on a large file. |
| 11 | Command-line tools: `readline`, the `commander` package, colours, exit codes, a `bin` entry in `package.json`. | A `todo` CLI with `add`, `list`, `done`, saved to a JSON file. | `npm link` lets you run `todo` from any folder. |
| 12 | **Checkpoint 0 and project.** | A note-taking CLI with search, tags and export to Markdown. | About 200 lines, tests by hand, tag `node-p1`. |

**Break it (daily):** read a file that does not exist, pass invalid JSON, forget `await`, throw inside a callback and see what Node prints.

## Part 2 (weeks 3-4, days 13-24): HTTP, Express and REST APIs

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 13 | How the web works under the hood: client and server, HTTP requests and responses, methods (GET, POST, PUT, PATCH, DELETE), status codes, headers, JSON bodies. The built-in `http` module. | A bare `http.createServer` that returns JSON and a 404 page. | You can read a raw request in the terminal. |
| 14 | **Express** basics: install, `app.get`, `app.post`, route parameters, query strings, `res.json`, `res.status`. Test with Postman or REST Client. | A `/hello/:name` API and a `/add?a=1&b=2` endpoint. | Each route returns the right status code. |
| 15 | Middleware: how `app.use` works, `express.json()`, writing your own logger, order of middleware, `next()`. | A request-logging middleware and a simple API-key check. | Changing the order of middleware changes behaviour, and you can say why. |
| 16 | REST design: resources, nouns not verbs, CRUD routes, plural names, pagination, filtering, versioning (`/api/v1`). | Sketch the routes for a notes API on paper. | Every route is a noun and a method. |
| 17 | Routers and project structure: `express.Router`, splitting into routes, controllers and services. | Refactor the day 14 app into folders. | No file longer than about 100 lines. |
| 18 | **Project and review.** | A notes API (create, read, update, delete) with in-memory storage. | Tested with at least 12 requests. |
| 19 | Validation: never trust input. **Zod** schemas for body, params and query, and sensible error messages. | Add Zod validation to the notes API. | Bad input returns 400 with a clear message. |
| 20 | Error handling: error-handling middleware, async errors, custom error classes, not leaking stack traces. | A central error handler with 404, 400 and 500 cases. | The server never crashes on bad input. |
| 21 | Configuration: environment variables, `dotenv` (or Node's `--env-file`), `.env.example`, never committing secrets, CORS. | Move port and settings to `.env`. | `.env` is in `.gitignore`, and `.env.example` is committed. |
| 22 | Testing APIs: **Vitest** (or the built-in `node:test`) with **supertest**, test structure, testing happy and failure paths. | 15 tests for the notes API. | `npm test` passes, and one deliberately broken test fails. |
| 23 | Logging and developer experience: **pino** logs, `nodemon` or `--watch`, ESLint, Prettier, API docs with a simple OpenAPI (Swagger) file. | Add logging and an OpenAPI page. | You can find any failed request in the logs. |
| 24 | **Checkpoint 1 and project.** | A bookmarks API from scratch in 4 hours: validation, errors, tests. | Passes its tests, committed with tag `node-p2`. |

**Break it (daily):** send an empty body, a huge body, wrong content type, a missing parameter, and a request that triggers a thrown error.

## Part 3 (weeks 5-6, days 25-36): databases, logins, security and real-time

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 25 | Databases: why files are not enough. Tables, rows, primary keys. SQL basics: `CREATE TABLE`, `INSERT`, `SELECT`, `WHERE`, `UPDATE`, `DELETE`. Use **SQLite** first. | Create a `notes` table and run 10 queries in a SQL shell. | You can write each query without help. |
| 26 | SQL part 2: `ORDER BY`, `LIMIT`, `JOIN`, foreign keys, `GROUP BY`, indexes (the idea). One-to-many design. | A `users` and `notes` schema with a join query. | You can explain why an index speeds up a query. |
| 27 | Use a database from Node: **better-sqlite3** or the `pg` driver for PostgreSQL, parameterised queries (never string-concatenate SQL), migrations. | Replace the in-memory notes store with SQL. | Data survives a server restart. |
| 28 | An ORM or query builder: **Drizzle** or **Prisma** (pick one). Schema, migrations, relations. | Port the notes API to the ORM. | You can add a column and migrate safely. |
| 29 | **Project and review.** Transactions and seeding data. | A bookmarks API with users and tags in the database. | Deleting a user deletes their notes, by design. |
| 30 | Authentication: password hashing with **argon2** or **bcrypt**, sign up and log in, sessions vs **JWT**, cookies (`httpOnly`, `secure`, `sameSite`). | `POST /signup` and `POST /login`. | No plain-text password is ever stored or logged. |
| 31 | Authorisation: protected routes, user-owned data, roles, middleware that checks `req.user`. | Users can read and edit only their own notes. | User A gets 403 or 404 on user B's notes. |
| 32 | Security basics: **helmet**, CORS configuration, rate limiting, input size limits, the OWASP Top 10 in plain words (injection, broken access control, secrets in code), dependency checks with `npm audit`. | Harden your API with a checklist. | You can say what each protection is for. |
| 33 | File uploads: **multer**, size and type limits, storing files, serving static files, streaming downloads. | Notes with image attachments. | A 50 MB file is rejected cleanly. |
| 34 | Real-time: WebSockets with **ws** or **Socket.IO**, rooms, broadcast, when to use polling or Server-Sent Events instead. | A live chat room. | Two browser tabs chat in real time. |
| 35 | Background work and caching: scheduled jobs (`node-cron`), a queue (the idea, **BullMQ** and Redis intro), caching with an in-memory map, then Redis (intro). | A nightly job that cleans expired data, and a cached `/stats` endpoint. | The second call to `/stats` is measurably faster. |
| 36 | **Checkpoint 2 and project.** | A multi-user task API with logins, permissions and tests in 5 hours. | Passes tests and security checklist. Tag `node-p3`. |

**Break it (daily):** try a SQL injection on a deliberately unsafe endpoint (your own, on your own machine) and then fix it; try to read another user's data; send 1000 requests in a loop and watch the rate limit.

## Part 4 (week 7, days 37-42): ship it

Build one API of your own choice end to end. Good choices: a habit tracker, an expense splitter, a mini URL shortener with stats, a recipe API, or a library system.

| Day | Do | Done when |
| --- | --- | --- |
| 37 | Plan: write 8 user stories, list routes and tables, draw the database tables on paper. Set up the repo, linting, `.env.example`, and a README skeleton. | The plan and an empty project that builds are committed. |
| 38 | Build the database layer and the core routes with validation. | Core routes work in Postman. |
| 39 | Add logins, permissions, rate limiting and a few tests per route. | Another user cannot touch your data. |
| 40 | **Docker:** write a `Dockerfile` and `docker-compose.yml` (app and database), `.dockerignore`, environment handling. Run the whole thing with `docker compose up`. | A fresh clone runs with one command. |
| 41 | CI and deploy: a **GitHub Actions** workflow that runs lint and tests on every push, then deploy to a free host (Render, Railway or Fly.io, whichever has a free tier when you do this). Health-check route, structured logs. | The API has a public URL and a green CI badge. |
| 42 | **Review.** Ask a friend to try it with Postman or a tiny front end for 15 minutes. Fix the top 3 problems. Finish the README with endpoints and a curl example. Tag `node-v1`. | A stranger can use your live API from the README alone. |

## Checkpoints and what comes next

Do not move on until you pass each gate. If you fail, redo the weak days, not the whole part.

- **Checkpoint 0 (day 12).** In 3 hours, with no notes, write a CLI that reads a JSON file with `fs/promises`, filters it, and writes a result file, with error handling for missing files. Pass: it works with at most 3 fixes.
- **Checkpoint 1 (day 24).** In 4 hours build a REST API with 4 routes, Zod validation, an error handler and 10 tests. Pass: all tests pass, and you can explain middleware order.
- **Checkpoint 2 (day 36).** Explain, out loud, how password hashing, sessions or JWTs, and parameterised queries each protect users. Then build a small API with a login. Pass: you do both without searching.
- **Capstone (day 42).** Passes when a stranger can use your live link and CI is green.

**What you can do now.** Build and ship back ends for web or mobile apps, write command-line tools, and read most Node code you meet. It is a strong pair with the JavaScript and TypeScript roadmaps; do TypeScript next, since most Node jobs use it. Not covered yet: a front-end framework like React, microservices and cloud services in depth, and system design for large scale. I can add roadmaps for those.

## Resources

I have not opened these links this session, so check each before relying on it.

| Resource | Use it for | Cost |
| --- | --- | --- |
| [Node.js Learn](https://nodejs.org/en/learn) | The official guides on modules, `fs`, streams, the event loop. | Free |
| [Node.js API docs](https://nodejs.org/api/) | The reference for every built-in module. | Free |
| [Express docs](https://expressjs.com/) | Routing and middleware. | Free |
| [The Odin Project: NodeJS](https://www.theodinproject.com/paths/full-stack-javascript/courses/nodejs) | A project-based back-end path. | Free |
| [freeCodeCamp Back End Development and APIs](https://www.freecodecamp.org/learn) | Guided practice. | Free |
| [SQLBolt](https://sqlbolt.com/) and [SQLite Tutorial](https://www.sqlitetutorial.net/) | SQL practice for days 25-26. | Free |
| [OWASP Top 10](https://owasp.org/www-project-top-ten/) | The security checklist for day 32. | Free |
| [Docker Get Started](https://docs.docker.com/get-started/) | Day 40. | Free |
| [javascript.info](https://javascript.info/) | The JavaScript primer for days 1-4. | Free |
