# Laravel Roadmap: From Zero to Modern PHP Web Applications and APIs

**60 sessions | 10 study weeks | approximately 190 hours | created October 29, 2026**

This roadmap is a standalone, project-based guide to Laravel. Each “Day” below is a **study session**, not necessarily a calendar day. The finish line is **Creator marketplace** with products, creators, purchases, permissions, image uploads, queued receipts, search, tests, management dashboard, production deployment and verified restore procedure.

## Start here

**Prerequisites and the beginner bridge.** PHP 8+ fundamentals, OOP basics, HTML forms and SQL ideas; the first week revisits essentials. Select a PHP version explicitly supported by the installed Laravel major version.

**Operating systems.** Linux and macOS: local PHP/Composer with official installer or Laravel Herd where supported. Windows: PHP+Composer or Laravel Herd, or Laravel Sail through WSL2/Docker. The exercises are portable; shell-specific startup may differ.

**Installation.** Install PHP matching Laravel 13 requirements, Composer, Git and Node.js/npm for Vite assets; verify `php -v` and `composer --version`. Use `laravel new` after installing the Laravel installer or `composer create-project laravel/laravel` for a new app. Choose SQLite first, PostgreSQL later. Use `php artisan about` to inspect versions.

### First run

```bash
composer global require laravel/installer
laravel new laravel-roadmap
cd laravel-roadmap
php artisan about
# Follow the generated README for frontend assets and local server.
# Common local development command: composer run dev
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
laravel-roadmap/
  README.md
  journal.md
  week-01/
  week-02/
  ...
  capstone/
```

Keep one Git commit per session, a runnable example for every topic, short notes on bugs and fixes, and a README in each weekly project. Use version control; never commit passwords, credentials or production database files.

## Week 1: PHP and Laravel orientation

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | PHP classes, arrays, nullable types and Composer | Build a Product class and helper | Correct type errors handled |
| 2 | Request life cycle, Laravel application structure | Identify routes/controllers/models | Trace a browser request end-to-end |
| 3 | Artisan commands and local app | Generate fresh app and run server | Landing page works on all supported hosts |
| 4 | Routes, closures and named paths | Add public /products and /about routes | Link generation uses named routes |
| 5 | Controllers, requests and responses | Create ProductController index/show | 404 generated correctly |
| 6 | Project: static storefront | Build catalog pages with route params | Navigation and empty state function |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 2: Blade and forms

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Blade templates and layouts | Implement shared header/footer | No duplicated layout markup |
| 8 | Components, slots and escaping | Build product card component | User text escaped by default |
| 9 | Form requests and validation | Add create-product form | Field errors shown and invalid input rejected |
| 10 | CSRF and flash sessions | Add success message and safe submission | Forged POST is rejected |
| 11 | Assets and Vite integration | Style catalog with CSS | Dev/build assets both load |
| 12 | Project: catalog admin forms | Create/edit/delete in temporary store | Usable from keyboard and mobile |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 12

- From a clean checkout, run the week 2 project and its tests with no undocumented steps.
- Explain three concepts from weeks 1–2 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 3: Eloquent and migrations

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Schema builder and migrations | Design creators/products/purchases | Clean migrate creates constraints |
| 14 | Eloquent models and CRUD | Persist products and creators | Restart leaves data intact |
| 15 | Relationships and eager loading | Show creator and products | Avoids N+1 query count growth |
| 16 | Factories, seeders and database testing | Seed 100 fixtures | Test suite remains isolated |
| 17 | Transactions and guarded mass assignment | Create purchase and items atomically | Invalid operation rolls back |
| 18 | Project: real storefront backend | Replace temporary store with database | Catalog and admin work after migration |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 4: Testing and debugging

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | HTTP feature tests | Test catalog and validation routes | 15 boundary cases green |
| 20 | Unit tests on business rules | Model discount, tax and availability | Deterministic result across edge values |
| 21 | DB refresh patterns and test isolation | Test creator/product relationships | No shared test data leak |
| 22 | Laravel debugger, logs and queries | Diagnose 3 seeded N+1/errors | Root causes written |
| 23 | Quality scripts, Pint and CI | Configure format and test tasks | Pull request job green |
| 24 | Checkpoint 1: CRUD marketplace | Build creator CRUD plus relational tests | 20+ meaningful assertions pass |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 24

- From a clean checkout, run the week 4 project and its tests with no undocumented steps.
- Explain three concepts from weeks 3–4 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 5: Identity and permissions

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Starter kits and auth concepts | Add signup/login/logout via supported scaffold | Passwords stored with strong hashes |
| 26 | Policies and gates | Restrict product edits to creator | Unauthorized response tested |
| 27 | Middleware and rate limiting | Protect admin and auth endpoints | Login brute-force throttled |
| 28 | Email verification and password reset | Use fake transport in tests | Expired reset links rejected |
| 29 | Security of file uploads and HTML | Limit media MIME/size and sanitize URLs | Invalid file rejected |
| 30 | Project: multi-user marketplace | Creator and buyer roles | Cross-account edit attempts blocked |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 6: APIs and integrations

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | API resources and JSON serialization | Add product index API | Internal fields hidden |
| 32 | Sanctum or session authentication | Protect purchase API | Auth strategy documented |
| 33 | Filtering, search and pagination | Implement catalog filters | Stable ordering and bounded page size |
| 34 | HTTP client with timeouts | Query fake shipment service | Graceful timeout without corrupting order |
| 35 | Storage disks and uploads | Add product images and cleanup | Broken file does not corrupt listing |
| 36 | Project: storefront + API | Expose catalog and create purchases | E2E browser/API flow works |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 36

- From a clean checkout, run the week 6 project and its tests with no undocumented steps.
- Explain three concepts from weeks 5–6 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 7: Events, queues and schedules

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Events/listeners and lifecycle | Dispatch purchase event | Receipt sent outside controller |
| 38 | Queued jobs and failed-job handling | Process email receipts with fake mail | Retry does not double-charge |
| 39 | Scheduling and idempotency | Expire unpaid purchases | Simulated duplicate job harmless |
| 40 | Notifications and mail templates | Create buyer order notification | Snapshot test includes safe URLs |
| 41 | Caching and invalidation | Cache product catalog categories | Product update invalidates cache |
| 42 | Checkpoint 2: resilient purchases | Replay purchase events and payment failures | Counts and state stay correct |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 8: Real-time and operational concerns

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Broadcasting and server-sent updates options | Notify creator of new purchase | Unauthorized client cannot subscribe |
| 44 | Search and database indexing | Improve catalog search | Query plan and latency compared |
| 45 | Localization and timezone | Add localized price/date UI | Correct currency/time formatting |
| 46 | Accessible UX and performance | Audit forms with keyboard | No blocked focus and basic page-speed budget |
| 47 | Observability and health checks | Add safe metrics and log IDs | Incident reproduced from trace ID |
| 48 | Project: creator analytics dashboard | Build sales view and export | Totals match known fixtures |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 48

- From a clean checkout, run the week 8 project and its tests with no undocumented steps.
- Explain three concepts from weeks 7–8 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 9: Deployment and hardening

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Environment secrets and config caching | Move env values to deployment config | No secrets in repository |
| 50 | Storage, queue worker and cron deployment | Deploy web/worker/scheduler components | Jobs process after restart |
| 51 | Deployment migrations and downtime planning | Run safe migration in staging | Existing data remains valid |
| 52 | CI tests and static checks | Add pipeline with DB service | All tests execute from clean checkout |
| 53 | Threat model and backup/restore | Test bad roles, uploads, CSRF and restore | Document evidence of protections |
| 54 | Project: staging marketplace | Deploy and run smoke checklist | Buyer can order and creator sees sale |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 10: Capstone release

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Define seller/buyer user stories and schema | Write 12 acceptance scenarios | Scope and permissions unambiguous |
| 56 | Complete catalog, creator profiles and uploads | Build core views and storage | Functional and accessible |
| 57 | Complete checkout simulation and queue flow | Add purchase transactions/events | Idempotency tests green |
| 58 | Complete reporting, auth and API surface | Implement dashboard and JSON endpoints | Roles and data scopes enforced |
| 59 | Finish CI, logs and backup/runbook | Publish reproducible deployment | Restore rehearsed successfully |
| 60 | Final capstone review | Demo public marketplace and admin | New tester can register, list and purchase from README |

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

Laravel 13 docs are the version spine; do not mix route, bootstrap, or starter-kit instructions from other major versions. Never store payment card numbers or implement real card processing as an exercise. Use a sandbox/mock payment provider only.

## Official learning resources

| Resource | Link |
|---|---|
| Laravel 13 installation | <https://laravel.com/docs/13.x/installation> |
| Routing | <https://laravel.com/docs/13.x/routing> |
| Eloquent ORM | <https://laravel.com/docs/13.x/eloquent> |
| Authentication | <https://laravel.com/docs/13.x/authentication> |
| Queues | <https://laravel.com/docs/13.x/queues> |
| Testing | <https://laravel.com/docs/13.x/testing> |
| Deployment | <https://laravel.com/docs/13.x/deployment> |

**Version check:** framework releases and developer tools change. Before installing or copying commands from this guide, check the official documentation above against the versions currently available on your computer.
