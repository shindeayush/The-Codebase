# Express Roadmap: From Zero to Secure Node.js REST APIs

**48 sessions | 8 study weeks | approximately 152 hours | created October 29, 2026**

This roadmap is a standalone, project-based guide to Express. Each “Day” below is a **study session**, not necessarily a calendar day. The finish line is **Multi-user project tracker API**: teams, projects, tasks, role-based access, validation, relational database, pagination, structured logs, automated tests, CI and deployment with a reproducible README.

## Start here

**Prerequisites and the beginner bridge.** JavaScript fundamentals (functions, objects, promises and async/await), command line and basic HTTP; beginner refresher is included in week 1.

**Operating systems.** Windows PowerShell, macOS Terminal, Linux shell; all run current Node.js LTS. Use SQLite initially and PostgreSQL for production data.

**Installation.** Install current Node.js LTS from nodejs.org; verify `node --version` and `npm --version`. Install VS Code and Git; optionally install PostgreSQL and a REST client. Use Express 5 and follow its routing/migration docs.

### First run

```bash
mkdir express-roadmap && cd express-roadmap
npm init -y
npm install express@5
npm pkg set type=module
# create app.js using the example below, then:
node app.js
```
```js
import express from 'express';
const app = express();
app.use(express.json());
app.get('/health', (_req, res) => res.json({status: 'ok'}));
app.listen(3000, () => console.log('http://localhost:3000'));
```

## How each study session works

| Minutes | Block | Method |
|---:|---|---|
| 10 | Recall | From memory, rewrite a concept from the previous session. |
| 40 | Learn | Read the relevant official documentation; take brief handwritten notes. |
| 90 | Build | Implement the day’s exercise yourself. Do not paste an AI-generated solution. |
| 30 | Break and debug | Create at least one deliberate failure and investigate the tool output. |
| 10 | Save | Commit code, record learned/confused/next step in `journal.md`. |

Sessions 6, 12, 18, … are **four-hour project/review sessions**; normal sessions are about three hours. If you fall behind, complete the current session before progressing. A session is finished only when the exercise runs, the stated check is demonstrated, and the code is committed.

## Build habits and repository layout

```text
express-roadmap/
  README.md
  journal.md
  week-01/
  week-02/
  ...
  capstone/
```

Keep one Git commit per session, a runnable example for every topic, short notes on bugs and fixes, and a README in each weekly project. Use version control; never commit passwords, credentials or production database files.

## Week 1: Node.js, HTTP and first routes

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Node runtime, ESM imports, package.json and npm scripts | Create a hello script and two npm scripts | All scripts run from a clean terminal |
| 2 | JavaScript promises, async/await and exception basics | Fetch a public sample URL with native fetch | Both success and failure have deliberate handling |
| 3 | HTTP requests, methods, headers, JSON and status codes | Send GET/POST with curl or REST client | Explain 200 vs 201 vs 400 vs 404 |
| 4 | Express app, route callbacks and res.json | Implement /health and /hello/:name | Each returns expected status and JSON |
| 5 | JSON parsing, request params and query strings | Build /greet with validated query options | Missing and malformed values behave predictably |
| 6 | Project: mini quote API | Build a 5-route in-memory quote CRUD API | Works end-to-end and committed with README |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 2: Routing and middleware

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Router modules and route order | Split quote API into two routers | Routes remain readable and tests still work |
| 8 | Middleware execution order and next() | Add request ID middleware and demonstrate order | Trace shows expected execution for each request |
| 9 | Validation and normalization | Reject invalid task title and deadline | Invalid input returns useful 400 JSON |
| 10 | Centralized async error handling in Express 5 | Trigger rejected async routes and catch centrally | Response is safe and no server crash |
| 11 | Static files, security headers and CORS choices | Serve a minimal API reference page | Static files work; CORS not opened broadly |
| 12 | Project: inventory API v2 | Add routers, validation, errors and logger | All endpoints share consistent error schema |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 12

- From a clean checkout, run the week 2 project and its tests with no undocumented steps.
- Explain three concepts from weeks 1–2 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 3: Persistence and data design

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Relational modeling, keys and SQL queries | Diagram users, projects and tasks | Schema has correct foreign keys |
| 14 | SQLite development and prepared SQL queries | Persist tasks and list them | Reopening app preserves rows |
| 15 | CRUD repository layer | Move SQL out of HTTP route files | Routes call tested repository methods |
| 16 | Transactions and constraint failures | Create task plus audit entry atomically | Failure leaves no half-saved operation |
| 17 | Migrations and seed data | Version schema and seed 20 tasks | Fresh clone initializes with one command |
| 18 | Project: database-backed tracker | Rebuild in-memory API with SQLite | Passes create/read/update/delete restart test |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 4: Testing and debugging

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Node built-in test runner and assertions | Unit-test validation helpers | At least 10 cases and edge inputs pass |
| 20 | HTTP integration tests against a temporary server | Test 200/400/404/409/500 response cases | Test suite controls app lifecycle |
| 21 | Test database isolation | Reset database in each test | Test order never changes outcomes |
| 22 | Debugging with VS Code breakpoints and stack traces | Diagnose 3 seeded route defects | Each has root-cause note |
| 23 | Test coverage, linting and formatting | Configure scripts for test and style | CI-style one-command checks succeed |
| 24 | Checkpoint 1: API fundamentals | Build tasks CRUD and 15 tests from notes only | Tests pass and errors are consistent |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 24

- From a clean checkout, run the week 4 project and its tests with no undocumented steps.
- Explain three concepts from weeks 3–4 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 5: Identity and API security

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Password storage and hash verification | Add signup with approved password-hash library | Plain passwords never stored or logged |
| 26 | Sessions vs token authentication | Choose one strategy and implement sign-in/out | Invalid credentials have correct responses |
| 27 | Authorization and ownership | Prevent access to another user’s task | Two-user security test passes |
| 28 | Injection, input validation and XSS context | Test hostile inputs and prepared queries | Inputs are rejected or harmless |
| 29 | Rate limiting, CORS, CSRF and cookie options | Threat-model a browser/API client | Settings match chosen auth transport |
| 30 | Project: authenticated API | Restrict all project and task endpoints | Unauthenticated and cross-owner tests pass |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 6: Production architecture

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Service layer boundaries and dependency injection basics | Move task rules to services | Controllers contain no SQL or rule duplication |
| 32 | Pagination, filtering and sorting | Add GET /tasks?status=&page= | Stable ordering and input bounds verified |
| 33 | API documentation with OpenAPI | Document 8 routes and errors | Spec examples match live responses |
| 34 | Environment validation and secrets | Load per-environment config | Missing required env causes clear startup failure |
| 35 | File uploads and size/type controls | Add optional task attachment endpoint | Reject oversized and unsupported files |
| 36 | Checkpoint 2: multi-user tracker | Run security and persistence test suite | At least 25 meaningful passing tests |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 36

- From a clean checkout, run the week 6 project and its tests with no undocumented steps.
- Explain three concepts from weeks 5–6 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 7: Operations and observability

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Structured logging and correlation IDs | Connect log entries to requests | Errors include request ID but no secrets |
| 38 | Health vs readiness and shutdown signals | Add readiness and close DB on SIGTERM | In-flight requests finish or fail safely |
| 39 | Caching and invalidation basics | Add short-lived project summary cache | Updates invalidate cached summary |
| 40 | Load testing and bottleneck identification | Compare 1 vs 100 concurrent requests | Report p50/p95 and constraints honestly |
| 41 | Dockerfile and dependency lockfiles | Containerize HTTP service | Starts with documented environment and health check |
| 42 | Project: staging deployment | Deploy to a supported host with database | Remote smoke tests and logs accessible |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 8: Capstone ship and maintain

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Write capstone scope, schema and API contract | Define 8 user stories and acceptance tests | Scope is realistic and signed off in journal |
| 44 | Implement core teams/projects/tasks services | Build relational endpoints | Auth and CRUD tests green |
| 45 | Add role permissions and audit entries | Restrict admin/member operations | Every forbidden case covered |
| 46 | Add CI checks and deployment pipeline | Run tests/build on pull requests | Green build gates publication |
| 47 | Performance and accessibility of API docs | Add pagination, examples, error guide | Unfamiliar tester can use endpoints |
| 48 | Final capstone review | Demo deployed API; publish diagrams, README and test report | Stranger can run, test and use app in 15 minutes |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 48

- From a clean checkout, run the week 8 project and its tests with no undocumented steps.
- Explain three concepts from weeks 7–8 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Capstone evaluation rubric

| Area | Passing evidence |
|---|---|
| Functionality | All acceptance scenarios pass from a clean state. |
| Correctness | Automated unit/integration/UI tests target both normal and failure paths. |
| Security and reliability | Invalid input, secret handling, access boundaries and recovery have documented tests. |
| Design | Clear layer boundaries and sensible domain modeling; no unnecessary framework complexity. |
| Deployment | A new developer can install, build and run the project from `README.md`. |
| Portfolio | Repository, architecture diagram, screenshots/demo, decisions, known limitations and release tag. |

## End-of-roadmap portfolio checklist

- [ ] Every weekly project is committed and independently runnable.
- [ ] All checkpoints have dated evidence (notes/tests/screenshots).
- [ ] Capstone builds from a fresh clone without secrets or private files.
- [ ] README includes prerequisites, platform-specific commands, configuration template, testing, troubleshooting and deployment.
- [ ] Automated tests and manual accessibility/security checks are reported accurately.
- [ ] A five-minute demo and a versioned release or deployable artifact exist.

## Important scope and platform notes

Express 5 forwards rejected promises from async route handlers automatically. Do not copy older Express 4 error-wrapper habits without checking their purpose; understand the differing path patterns and error middleware signature.

## Official learning resources

| Resource | Link |
|---|---|
| Express installation | <https://expressjs.com/en/starter/installing/> |
| Express 5 migration | <https://expressjs.com/en/guide/migrating-5/> |
| Express API | <https://expressjs.com/en/5x/api.html> |
| Node.js learn | <https://nodejs.org/en/learn> |
| Node.js test runner | <https://nodejs.org/api/test.html> |
| OWASP API Security | <https://owasp.org/API-Security/> |

**Version check:** framework releases and developer tools change. Before installing or copying commands from this guide, check the official documentation above against the versions currently available on your computer.
