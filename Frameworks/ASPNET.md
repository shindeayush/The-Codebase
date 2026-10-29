# ASP.NET Core Roadmap: From Zero to Modern C# Web APIs

**60 sessions | 10 study weeks | approximately 190 hours | created October 29, 2026**

This roadmap is a standalone, project-based guide to ASP.NET Core. Each “Day” below is a **study session**, not necessarily a calendar day. The finish line is **Multi-tenant booking API** with accounts, calendars, reservations, collision detection, EF Core, authorization, integration tests, telemetry, CI and deployed health checks.

## Start here

**Prerequisites and the beginner bridge.** C# basics, async Task, collections, LINQ and basic HTTP/SQL; introductory revision is provided.

**Operating systems.** Windows, macOS, Linux supported with a compatible .NET SDK. Windows: Visual Studio 2026 or VS Code; macOS/Linux: VS Code, Rider or terminal. Prefer a supported .NET LTS SDK, such as .NET 10.

**Installation.** Install .NET SDK and verify `dotnet --info`; install editor, Git and PostgreSQL/SQLite. Use a minimal Web API first, then controllers if you want a traditional MVC style. Keep CLI commands equivalent across platforms.

### First run

```bash
dotnet new web -n AspRoadmap
cd AspRoadmap
dotnet run
# Open URL printed by the application
# Tests later: dotnet test
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
asp.net-core-roadmap/
  README.md
  journal.md
  week-01/
  week-02/
  ...
  capstone/
```

Keep one Git commit per session, a runnable example for every topic, short notes on bugs and fixes, and a README in each weekly project. Use version control; never commit passwords, credentials or production database files.

## Week 1: C#, .NET and HTTP basics

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | C# record, nullable refs, async Task refresh | Write booking model and price helper | Tests compile with nullable enabled |
| 2 | .NET CLI, project templates and DI container | Run minimal API template | Explain app lifetime and service registration |
| 3 | HTTP pipeline and mapping GET/POST | Add /health and bookings routes | Expected JSON and status codes |
| 4 | Route constraints and typed results | Add GET by integer ID | Unknown/malformed IDs handled |
| 5 | JSON serialization and validation choices | Define CreateBookingRequest | Invalid dates give 400 with useful detail |
| 6 | Project: in-memory booking API | Implement CRUD for rooms | Six routes work from curl |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 2: Dependency injection and domain rules

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Singleton/scoped/transient lifetimes | Register repository and clock | No captive scoped dependency |
| 8 | Services and interfaces in C# | Move conflicts logic to BookingService | Endpoint is small and testable |
| 9 | Configuration and options pattern | Configure booking horizon | Invalid setting fails startup |
| 10 | Exceptions and ProblemDetails responses | Add centralized error handler | No internal stack traces emitted |
| 11 | Logging and correlation context | Add request ID and structured messages | One request traced across layers |
| 12 | Project: booking rules engine | Reject overlaps, bad dates and invalid rooms | All acceptance cases tested |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 12

- From a clean checkout, run the week 2 project and its tests with no undocumented steps.
- Explain three concepts from weeks 1–2 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 3: EF Core and migrations

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Entity and DbContext design | Model rooms/bookings/users | Keys and relationships correct |
| 14 | SQLite/PostgreSQL provider & connection strings | Persist booking rows | Restart retains bookings |
| 15 | Migrations and seed routines | Apply migration from clean DB | Versioned schema tracked |
| 16 | LINQ queries and no-tracking reads | Implement room availability query | Returns correct availability from fixtures |
| 17 | Concurrency tokens and transaction choice | Prevent two simultaneous bookings | Concurrency integration test passes |
| 18 | Project: persistent booking API | Replace memory repo with EF Core | CRUD and collision tests still pass |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 4: API testing

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | xUnit test organization and assertions | Test booking date calculations | 15 parameterized cases pass |
| 20 | WebApplicationFactory integration tests | Request API in-process | No actual public port needed |
| 21 | Test database isolation and reset | Test create/list/delete | Re-running suite gives same answers |
| 22 | Mockable system time and dependencies | Test DST/day-boundary condition | No flaky clock dependence |
| 23 | Debugger, logging scopes, exception trace | Fix seeded race and null bug | Root-cause notes recorded |
| 24 | Checkpoint 1: reliable API | Build room availability endpoint from blank file | 20 tests pass |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 24

- From a clean checkout, run the week 4 project and its tests with no undocumented steps.
- Explain three concepts from weeks 3–4 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 5: Identity and security

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | ASP.NET Core Identity vs custom authentication | Choose supported identity integration | Passwords hashed safely |
| 26 | Cookie auth vs JWT bearer API | Add signup/sign-in using one model | Unauthorized endpoints return 401 |
| 27 | Authorization policies and claims | Add manager/customer roles | Privileged operations blocked |
| 28 | Object ownership and tenant isolation | Users see only their reservations | Cross-tenant test fails safely |
| 29 | CSRF/cookie same-site, CORS, throttling | Threat model UI clients | Protections correspond to transport |
| 30 | Project: secure reservation service | Add roles and tenant checks | Matrix of 15 authorization tests passes |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 6: API design and validation

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | OpenAPI generation and request docs | Publish bookings contract | Responses match specification |
| 32 | Minimal API filters or middleware | Implement common request validation | Invalid request never reaches service |
| 33 | Pagination, filtering and stable sorting | List reservations by date | Consistent pages under ties |
| 34 | Versioning policy and deprecations | Add v2 availability response | v1 caller tests still green |
| 35 | File export and privacy | Generate per-user CSV download | Other user cannot retrieve export |
| 36 | Project: documented booking API | External tester creates, cancels and exports | No undocumented steps |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 36

- From a clean checkout, run the week 6 project and its tests with no undocumented steps.
- Explain three concepts from weeks 5–6 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 7: Async services and reliability

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Hosted services and BackgroundService | Create reservation expiry worker | Graceful cancellation supported |
| 38 | Message queue boundary concepts | Emulate notification outbox | Failed notification doesn't lose booking |
| 39 | Retries/timeouts for external services | Simulate payment API timeout | No duplicate reservations |
| 40 | Caching and cache invalidation | Cache room availability briefly | Writes invalidate related cache |
| 41 | Health/readiness endpoints and graceful shutdown | Separate live and ready | DB-down means not ready |
| 42 | Checkpoint 2: resilient service | Inject faults and run tests | Correct error statuses and no duplicate booking |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 8: Diagnostics and performance

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | OpenTelemetry traces and metrics concepts | Trace booking request | See DB and service spans |
| 44 | EF Core query performance | Identify and fix N+1 | Before/after SQL count documented |
| 45 | Load testing under contention | Simulate 50 same-room requests | Exactly one succeeds for exclusive slot |
| 46 | Memory allocations and streaming JSON | Compare bulk vs streamed export | Memory use recorded |
| 47 | Secrets management and deployment hardening | Externalize auth secrets and DB config | Production startup validates secrets |
| 48 | Project: measured booking service | Report latency/throughput under test | Findings and tradeoffs reproduced |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 48

- From a clean checkout, run the week 8 project and its tests with no undocumented steps.
- Explain three concepts from weeks 7–8 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 9: Deployment and CI

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | dotnet publish and environment modes | Publish Release build | Deployable without local source tree |
| 50 | Docker multi-stage image | Build API image | Runs with configured external DB |
| 51 | CI using dotnet test/build | Add pull-request workflow | Broken unit test blocks merge |
| 52 | Logs and error monitoring | Collect failure telemetry | No PII leaked |
| 53 | Backup/restore and migration plan | Restore booking DB to test env | Data integrity verified |
| 54 | Project: live booking API | Deploy with readiness endpoint | Curl walkthrough works remotely |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 10: Capstone: tenant booking platform

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Define room constraints and API contract | Write 10 acceptance stories | Conflict matrix includes boundary timestamps |
| 56 | Implement organizations, rooms, users | Add entities and migrations | Referential constraints tested |
| 57 | Implement reservations with concurrency control | Add transaction/unique overlap strategy | Parallel stress test passes |
| 58 | Implement auth, roles and event reminders | Protect every write | No cross-tenant leakage |
| 59 | Add integration tests, OpenAPI, CI | Run release pipeline | All gates green |
| 60 | Final demo, runbook and recovery test | Publish deployable project and README | Stranger provisions and uses platform |

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

Use supported modern .NET rather than legacy .NET Framework. ASP.NET Core can use Minimal APIs or controllers; this roadmap focuses on APIs, not Razor Pages/Blazor as the core capstone. For a database-backed booking conflict, application-only checks are insufficient under concurrency: prove correctness with transactions/locking and tests.

## Official learning resources

| Resource | Link |
|---|---|
| ASP.NET Core docs | <https://learn.microsoft.com/aspnet/core/> |
| Getting started | <https://learn.microsoft.com/aspnet/core/getting-started/> |
| .NET installation | <https://learn.microsoft.com/dotnet/core/install/> |
| Minimal APIs | <https://learn.microsoft.com/aspnet/core/fundamentals/minimal-apis/overview> |
| EF Core | <https://learn.microsoft.com/ef/core/> |
| ASP.NET security | <https://learn.microsoft.com/aspnet/core/security/> |

**Version check:** framework releases and developer tools change. Before installing or copying commands from this guide, check the official documentation above against the versions currently available on your computer.
