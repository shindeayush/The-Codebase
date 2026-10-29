# Spring Boot Roadmap: From Zero to Production Java and Kotlin Services

**72 sessions | 12 study weeks | approximately 228 hours | created October 29, 2026**

This roadmap is a standalone, project-based guide to Spring Boot. Each “Day” below is a **study session**, not necessarily a calendar day. The finish line is **Order fulfillment service** with customers, products, orders, stocks, transaction integrity, roles, observability, API contracts, integration tests, migrations, CI and deployment; optional Kotlin port of one module.

## Start here

**Prerequisites and the beginner bridge.** Comfort with Java or Kotlin syntax, classes, collections and exceptions; basic HTTP and SQL. A Java-to-Spring warm-up is built into the first week.

**Operating systems.** Windows, macOS and Linux supported. Choose Java as primary language; equivalent Kotlin examples/exercises are offered as an optional alternative throughout.

**Installation.** Install a supported JDK (17 minimum for Spring Boot 4; prefer current LTS supported by the release), IntelliJ IDEA, Git and Docker if available. Generate a project from Spring Initializr with Web MVC, Validation, Actuator, Spring Data JPA, PostgreSQL and Test dependencies. Use the latest compatible Boot release shown at start.spring.io; avoid mixing Boot 3 and Boot 4 tutorial imports.

### First run

```text
Visit https://start.spring.io/
Project: Maven • Language: Java (or Kotlin) • Packaging: Jar
Dependencies: Spring Web MVC, Validation, Spring Data JPA,
PostgreSQL Driver, Actuator, Spring Boot Starter Test
Download → unzip → open in IDE
Windows: .\mvnw.cmd spring-boot:run
Linux/macOS: ./mvnw spring-boot:run
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
spring-boot-roadmap/
  README.md
  journal.md
  week-01/
  week-02/
  ...
  capstone/
```

Keep one Git commit per session, a runnable example for every topic, short notes on bugs and fixes, and a README in each weekly project. Use version control; never commit passwords, credentials or production database files.

## Week 1: Spring and JVM basics

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | JVM, JDK and Maven/Gradle wrapper | Run plain Java service and wrapper build | Can explain compiled class and managed dependency |
| 2 | HTTP, REST and JSON mapping | Write REST endpoint contract on paper | Knows 200, 201, 400, 404, 409 |
| 3 | Spring IoC and dependency injection | Create service injected into controller | No manual service new in controller |
| 4 | Spring Initializr and app configuration | Generate and boot project | Build and test commands run on platform |
| 5 | @GetMapping/@PostMapping and response types | Build products GET/POST | curl output/status correct |
| 6 | Project: product catalog | Build product list/create/update/delete in memory | Five endpoints behave and tests pass |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 2: Domain modeling and validation

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Records/data classes vs entities and DTOs | Create ProductRequest/ProductResponse | Persistence fields do not leak into API |
| 8 | Validation annotations and @Valid | Reject negative prices and blank names | Field errors include actionable messages |
| 9 | Service-layer validation and exceptions | Add product SKU uniqueness rule | Conflict returns 409 |
| 10 | @RestControllerAdvice exception handling | Build consistent error body | No stack trace leaks |
| 11 | Profiles and properties/environment variables | Run dev/test profiles | DB secrets never committed |
| 12 | Project: catalog v2 | Add categories, validation and typed errors | 12 HTTP tests cover invalid input |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 12

- From a clean checkout, run the week 2 project and its tests with no undocumented steps.
- Explain three concepts from weeks 1–2 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 3: Data persistence

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Relational modeling and JPA entities | Design product/inventory/order tables | Keys and constraints recorded |
| 14 | Spring Data repositories and transactions | Persist product with JPA | Rows remain after restart |
| 15 | JPQL/derived queries and pagination | Query products by category, stock | Stable pagination on ties |
| 16 | @Transaction boundaries and rollback | Deduct stock and place order atomically | Failure preserves original inventory |
| 17 | Flyway migrations and seed data | Create schema history and fixtures | Clean DB bootstraps one-command |
| 18 | Project: catalog with PostgreSQL | Add migrations and persistent CRUD | Restart + migration verification passes |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 4: Integration testing

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | JUnit assertions and test design | Test price and SKU rules | Boundary inputs covered |
| 20 | Spring Boot test slices and MockMvc | Test controller without full service network | Response/status tests deterministic |
| 21 | Database integration tests with isolated data | Test product repository with test DB | No tests rely on execution order |
| 22 | Mocking third-party clients | Simulate payment approval/refusal | Failure path observable without real payment |
| 23 | Debugging exceptions and SQL logs | Investigate N+1 query and validation error | Written root causes |
| 24 | Checkpoint 1: persistence & tests | Implement inventory CRUD from blank module | 20 passing tests and clean schema |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 24

- From a clean checkout, run the week 4 project and its tests with no undocumented steps.
- Explain three concepts from weeks 3–4 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 5: Security and identities

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Authentication concepts, password encoders | Add accounts and safe hashes | No plaintext credentials stored |
| 26 | Spring Security filter chain | Protect order endpoints | Anonymous requests get 401 |
| 27 | Authorization method rules and roles | Admin-only stock corrections | User cannot escalate roles |
| 28 | CSRF vs token strategy and cookies | Explain browser vs API auth | Chosen configuration is threat-modeled |
| 29 | CORS, headers and secret management | Lock origins and error data | No public wildcard with credentials |
| 30 | Project: secure order API | Test owner and admin authorization | Matrix of at least 12 cases passes |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 6: Advanced persistence

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Entity relationships, fetch plans | Order with line items | Serialization avoids recursive entity graphs |
| 32 | Optimistic locking and race conditions | Simulate two concurrent stock updates | Never oversell item |
| 33 | Database indexes and query plans | Compare order lookup plan | Query metrics documented |
| 34 | Read models and projections | Make lightweight order history response | Reduces unnecessary loaded fields |
| 35 | Validation and idempotency keys | Retry create-order safely | Replayed request does not duplicate order |
| 36 | Project: reliable order placement | Cover concurrent checkouts and rollback | Stock never negative in tests |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 36

- From a clean checkout, run the week 6 project and its tests with no undocumented steps.
- Explain three concepts from weeks 5–6 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 7: Service integration

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | HTTP clients with timeouts | Wrap mock shipping API | Timeouts return recoverable status |
| 38 | Retries, circuit breakers and bulkheads concepts | Simulate remote outage | Retry policy does not duplicate charge |
| 39 | Events and application listeners | Publish order-created event | Side effect decoupled from controller |
| 40 | Email or message broker background worker | Send fake receipt asynchronously | Order placement remains responsive |
| 41 | Scheduled jobs and cleanup | Expire reserved stock | Test uses controlled clock |
| 42 | Checkpoint 2: robust ordering | Kill integration during transaction | No inconsistent database state |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 8: Operations and delivery

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Actuator health/readiness/metrics | Expose safe endpoints | Sensitive actuator routes restricted |
| 44 | Structured logs and trace IDs | Correlate request with payment mock | No payment detail leaks |
| 45 | Spring configuration for containerized DB | Run Docker Compose local stack | Rebuild works on clean machine |
| 46 | Graceful shutdown and thread pool settings | Simulate SIGTERM under load | Existing requests complete within timeout |
| 47 | CI with mvnw tests and dependency scanning | Set GitHub Actions job | Failing tests block release |
| 48 | Project: staging release | Publish app on test host | New user can complete test order |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 48

- From a clean checkout, run the week 8 project and its tests with no undocumented steps.
- Explain three concepts from weeks 7–8 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 9: Kotlin and optional alternatives

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Kotlin null-safety and data classes | Port ProductResponse to Kotlin | Correct null behavior tested |
| 50 | Spring Kotlin constructor binding | Build Kotlin configuration module | Required props checked at startup |
| 51 | Coroutines vs threads caveats in server code | Compare blocking and suspend semantics | No thread-blocking hidden on event loop |
| 52 | Caching with invalidation | Cache products and invalidate on writes | No stale product after update |
| 53 | API documentation with OpenAPI tooling | Publish documented order routes | Docs match tests |
| 54 | Project: mixed-language optional track | Port one module or write equivalent Java improvement | Same contract tests pass |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 10: Architecture and performance

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Layered package organization and modularity | Separate order, catalog, identity | Dependencies one-way |
| 56 | Contract/version compatibility | Introduce /v2 response field | Existing consumer contract passes |
| 57 | Performance profiling, SQL and memory | Run controlled load tests | p95 before/after reproducible |
| 58 | Resilience and observability review | Simulate database down and slow client | Graceful failure visible in logs |
| 59 | Production readiness checklist | Audit secrets, backups, migrations | Restore drill documented |
| 60 | Checkpoint 3: production API | Release tag and recovery plan | Test host survives controlled failures |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 60

- From a clean checkout, run the week 10 project and its tests with no undocumented steps.
- Explain three concepts from weeks 9–10 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 11: Capstone construction

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 61 | Write functional spec and schema | Choose order states and constraints | 10 user stories with acceptance tests |
| 62 | Implement customer and catalog bounded modules | Add DTOs/services/repositories | Unit + HTTP tests green |
| 63 | Implement order/payment/inventory workflows | Transactional state machine | Concurrent order tests pass |
| 64 | Implement security roles and auditing | Add least-privilege constraints | Unauthorized operations blocked |
| 65 | Add migration, API spec and telemetry | Generate release candidate | CI and docs green |
| 66 | Project: full dress rehearsal | Fresh environment deployment | End-to-end order from new account succeeds |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 12: Capstone ship and review

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 67 | Add staging-to-prod configuration discipline | Reconcile env template and secrets | No secret in repo or logs |
| 68 | Add complete automated test strategy | Unit, slice, integration and security tests | Failures have clear diagnostics |
| 69 | Profile hot paths and indexes | Record query/p95 benchmarks | Tradeoffs documented |
| 70 | Make deployment reproducible and recoverable | Produce images and backup script | Restore verified separately |
| 71 | Publish architecture and runbook | Diagram transactions, failure modes and health | Teammate can operate service |
| 72 | Final capstone: fulfillment API | Demo full flow and optional Kotlin module | Stranger can deploy and order from README |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 72

- From a clean checkout, run the week 12 project and its tests with no undocumented steps.
- Explain three concepts from weeks 11–12 without notes and identify one failure path you tested.
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

Spring Boot 4 may change dependency names and package namespaces relative to Boot 3. Read your generated project and installed dependency versions before following third-party samples. Use database transactions for invariants; never assume JVM process locks coordinate separate server instances.

## Official learning resources

| Resource | Link |
|---|---|
| Spring Boot docs | <https://docs.spring.io/spring-boot/index.html> |
| Spring Initializr | <https://start.spring.io/> |
| Spring Boot requirements | <https://docs.spring.io/spring-boot/system-requirements.html> |
| Spring Guides | <https://spring.io/guides> |
| Spring Security | <https://docs.spring.io/spring-security/reference/> |
| Spring Data JPA | <https://docs.spring.io/spring-data/jpa/reference/> |

**Version check:** framework releases and developer tools change. Before installing or copying commands from this guide, check the official documentation above against the versions currently available on your computer.
