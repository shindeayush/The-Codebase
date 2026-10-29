# NestJS Roadmap: From Zero to Structured TypeScript APIs and Services

**60 sessions | 10 study weeks | approximately 190 hours | created October 29, 2026**

This roadmap is a standalone, project-based guide to NestJS. Each “Day” below is a **study session**, not necessarily a calendar day. The finish line is **Support ticket platform API**: organizations, tickets, assignments, comments, roles, transactional persistence, background notifications, contract documentation, e2e tests, CI and deployed operations.

## Start here

**Prerequisites and the beginner bridge.** JavaScript/TypeScript, promises, classes and HTTP basics. Includes a compact TypeScript warm-up. Basic SQL helpful but not required.

**Operating systems.** Windows, Linux, macOS. Install a currently supported Node.js LTS release; Nest CLI has specific version prerequisites, so consult the latest First Steps page before installation.

**Installation.** Install Node.js LTS, VS Code, Git, and optional PostgreSQL. Use Nest CLI to generate an app. Select one module-system/test-runner option and use the generated scripts consistently; avoid forcing Jest if the starter uses Vitest.

### First run

```bash
npm install -g @nestjs/cli
nest new nest-roadmap
cd nest-roadmap
npm run start:dev
# Browser: http://localhost:3000
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
nestjs-roadmap/
  README.md
  journal.md
  week-01/
  week-02/
  ...
  capstone/
```

Keep one Git commit per session, a runnable example for every topic, short notes on bugs and fixes, and a README in each weekly project. Use version control; never commit passwords, credentials or production database files.

## Week 1: TypeScript and Nest fundamentals

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | TypeScript interfaces, types, unions and strict null checks | Type customer and ticket domain objects | Compiles without any and unsafe casts |
| 2 | Decorators, classes, dependency injection basics | Model service and constructor dependencies | Explain constructor injection |
| 3 | Nest CLI, project structure and bootstrap | Create app and inspect AppModule | Dev server starts without runtime errors |
| 4 | Controllers, route decorators, parameters and query | GET /tickets/:id and list endpoint | Correct status on missing item |
| 5 | Providers and service registration | Move ticket retrieval into TicketService | Controller has no storage logic |
| 6 | Project: in-memory ticket catalog | Create list/get/create/update/delete | Run and commit a documented five-route API |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 2: Modules, DTOs and validation

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Feature modules and exports/imports | Extract TicketsModule and UsersModule | Dependencies resolve without circular imports |
| 8 | DTOs and runtime validation pipes | Define CreateTicketDto and ValidationPipe | Unknown fields and invalid status rejected |
| 9 | Exception filters and standard HTTP exceptions | Map not-found and conflict errors | Error responses stable |
| 10 | Interceptors and response transformations | Add timing and serialization | Secrets omitted from returned user objects |
| 11 | Guards and middleware life cycle | Draw request pipeline from middleware to interceptor | Can predict order on a real request |
| 12 | Project: categorized tickets | Add labels and priorities with DTO tests | Feature isolated and validated |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 12

- From a clean checkout, run the week 2 project and its tests with no undocumented steps.
- Explain three concepts from weeks 1–2 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 3: Databases and clean architecture

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | PostgreSQL/SQLite and relational schema | Design ticket, user, comment relationships | Valid keys and constraints |
| 14 | ORM selection (TypeORM or Prisma) and generated clients | Connect one chosen ORM | 10 records persist across restart |
| 15 | Repository abstraction and service-layer invariants | Implement ticket repository | Can swap fake in tests |
| 16 | Transactions and rollback | Add comment and last-updated event atomically | Failure rolls back together |
| 17 | Migrations and development seed data | Migrate new database from zero | CI initializes schema automatically |
| 18 | Project: persistent ticket engine | Rework ticket features to database | REST behavior unchanged and repeatable |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 4: Testing and code quality

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Unit testing provider with mocked repository | Test priority state machine | At least 12 distinct assertions pass |
| 20 | Controller integration test and request simulation | Test validation + 404 paths | Malformed requests never reach service |
| 21 | End-to-end app bootstrap with isolated DB | Test lifecycle of ticket | e2e suite repeatable |
| 22 | Logging and debugging injection errors | Diagnose 3 provider/module mistakes | Written why/how fixes |
| 23 | Lint, format and test scripts | Wire checks to one script | CI runs identical commands |
| 24 | Checkpoint 1: maintainable Nest API | Build one extra module from memory | DTOs, DI and 20 tests green |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 24

- From a clean checkout, run the week 4 project and its tests with no undocumented steps.
- Explain three concepts from weeks 3–4 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 5: Authentication and authorization

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Credentials, password hashing, auth guard | Add login and protected route | Wrong user gets 401 consistently |
| 26 | JWT vs sessions and credential lifecycle | Build one approach with expiry | Expired credentials rejected |
| 27 | Role-based access with guards | Implement admin/agent/customer policy | Every role matrix case tested |
| 28 | Object-level authorization | Restrict customer to own org tickets | Cross-tenant access blocked |
| 29 | CORS, rate limits and error confidentiality | Audit API surface | No stack traces or secrets in responses |
| 30 | Project: secured helpdesk | Add owner and agent assignment | 15 authorization tests green |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 6: HTTP APIs and integrations

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | OpenAPI decorators and schema generation | Document ticket CRUD and DTOs | Docs match live validators |
| 32 | Pagination, filtering, sorting | Add cursor/offset choice with stable ordering | No repeated/skipped items on test data |
| 33 | HTTP client and timeout handling | Call a fake external notification endpoint | Timeouts and retry policy tested |
| 34 | Configuration service and startup validation | Centralize env settings | Bad config fails before binding port |
| 35 | File upload and scanning boundaries | Accept ticket attachments with strict limits | Malformed files fail safely |
| 36 | Project: documented integration API | Add tickets, comments and attachments | External tester completes 5 flows from spec |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 36

- From a clean checkout, run the week 6 project and its tests with no undocumented steps.
- Explain three concepts from weeks 5–6 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 7: Asynchronous work and events

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Event-driven service decoupling | Publish ticket-created events | Notification listener receives once |
| 38 | Queues and background jobs | Enqueue email task with fake worker | HTTP request returns before work completes |
| 39 | Idempotent processing and retries | Simulate duplicate delivery | No duplicate ticket notifications |
| 40 | Scheduling and cron workflows | Send overdue ticket reminders | Clock-based test verifies boundary |
| 41 | WebSockets or SSE update stream | Stream ticket state to client | Reconnect does not leak resources |
| 42 | Checkpoint 2: resilient async workflow | Run worker with forced failures | Successful replay and evidence of idempotency |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 8: Performance, security and observability

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Caching and invalidation | Cache organization summary | Mutation invalidates stale data |
| 44 | Request IDs, metrics and structured log | Add correlation across controllers and jobs | Debug one trace end-to-end |
| 45 | Database indexes and query profiles | Optimize slow ticket list | Before/after query plan documented |
| 46 | Graceful shutdown and resource lifecycle | Drain app & DB connections | Process exits after signal |
| 47 | Threat model and dependency audit | Check auth, file uploads, and SSRF risks | High-risk paths covered by tests |
| 48 | Project: operations dashboard endpoint | Add health, metrics and logs | Service diagnostics usable without private data |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 48

- From a clean checkout, run the week 8 project and its tests with no undocumented steps.
- Explain three concepts from weeks 7–8 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 9: Deployment and scaling

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Production build and environment separation | Build optimized artifact | Starts without dev dependencies |
| 50 | Docker and Compose database dev | Containerize app with DB | One-command environment reproducible |
| 51 | CI: unit/e2e/security checks | Add pipeline jobs | Unsafe commit blocks merge |
| 52 | API versioning and deprecation | Add /v1 and plan migration | Existing callers keep working |
| 53 | Scale pitfalls and stateless services | Audit sessions, queues and instances | Multi-instance assumptions explicit |
| 54 | Project: staging helpdesk | Deploy app and database | Remote e2e smoke test passes |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 10: Capstone: enterprise-ready helpdesk

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Define roles, acceptance criteria, DDL and API contract | Draft capstone spec and data diagram | 10 user stories actionable |
| 56 | Implement org, user, ticket and comment models | Add domain constraints | Tenant boundaries tested |
| 57 | Add async notices, assignment logic and pagination | Integrate queue/guards | Idempotency suite passes |
| 58 | Add OpenAPI, error policy and audit trails | Document all externally visible outcomes | API spec and tests agree |
| 59 | Harden CI, backup/restore rehearsal and deployment | Deploy and restore a sample database | Restore verified in isolated environment |
| 60 | Final capstone demo and review | Publish code, live endpoint, guide and test inventory | Stranger follows README and completes ticket flow |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 60

- From a clean checkout, run the week 10 project and its tests with no undocumented steps.
- Explain three concepts from weeks 9–10 without notes and identify one failure path you tested.
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

The current Nest CLI may generate either ESM/Vitest or CommonJS/Jest. Use its generated scripts and read the official version-sensitive setup instructions. Prefer constructor injection and runtime DTO validation over TypeScript-only types at HTTP boundaries.

## Official learning resources

| Resource | Link |
|---|---|
| Nest First Steps | <https://docs.nestjs.com/first-steps> |
| Nest Fundamentals | <https://docs.nestjs.com/modules> |
| Controllers | <https://docs.nestjs.com/controllers> |
| Providers | <https://docs.nestjs.com/providers> |
| Security | <https://docs.nestjs.com/security/authentication> |
| Testing | <https://docs.nestjs.com/fundamentals/testing> |
| OpenAPI | <https://docs.nestjs.com/openapi/introduction> |

**Version check:** framework releases and developer tools change. Before installing or copying commands from this guide, check the official documentation above against the versions currently available on your computer.
