# FastAPI (Python) Roadmap: From Zero to Type-Safe APIs and Async Services

*Created: 29 October 2026 · 10 weeks · 60 sessions · ~190 guided hours*

## Start here

Start from HTTP and Python typing, progress through Pydantic validation, async I/O, SQL persistence, authentication, background tasks and deployment, and ship an API with tests.

**Prerequisites:** Python functions, dictionaries, classes, imports, exceptions, virtual environments and basic `async`/`await` help. Optional preparation covers missing Python/HTTP basics.

**By the end you will have:** a Git repository containing each session, weekly project demos, a journal, documented checkpoint results, tests or quality checks, and a polished capstone with setup steps that another learner can follow.

### Platform setup (Windows, Linux and macOS)

| Platform | Environment creation | Activation | Verify |
|---|---|---|---|
| Windows (PowerShell) | `py -m venv .venv` | `.\.venv\Scripts\Activate.ps1` | `python --version` |
| Linux | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |
| macOS | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |

Run package installations **after activation**, from the guide's project root. On Windows, use the Windows Python launcher (`py`) to create the environment if `python` is not yet configured. For restricted PowerShell execution policies, use Command Prompt with `.venv\Scripts\activate.bat` rather than changing system-wide policy. Confirm that `python -m pip --version` points to the virtual environment. Keep `.venv/` and secrets out of Git. For incompatible versions, consult the official project's install matrix and select a supported Python version; do not silently install an older runtime-wide package.

Install a **currently supported CPython version**, Git and an editor on Windows, Linux or macOS. Create a virtual environment and activate it using the shared OS table below:
```bash
python -m pip install "fastapi[standard]" pytest httpx sqlalchemy
```
Create `main.py`:
```python
from fastapi import FastAPI
app = FastAPI()
@app.get('/health')
def health():
    return {'status': 'ok'}
```
Run `fastapi dev main.py`; visit `/health` and `/docs`. The development server is not a production deployment command. The official guide also documents `uv` as a reproducible project/dependency workflow.

### Optional preflight sessions (not part of the numbered roadmap)

| Prep | What to practise | Evidence |
|---|---|---|
| P1 | Python or HTML/CSS basics relevant to this framework | Write a tiny script/page from memory and explain each statement. |
| P2 | Terminal, folders, interpreter/runtime and dependency manager | Create isolated project and check runtime/package versions. |
| P3 | Git, README, editor/debugger and error messages | Make a commit and resolve a deliberately introduced error. |
| P4 | Domain fundamentals: HTTP / SQL / statistics / algebra / testing / quantum ideas | Complete three small written examples before starting Day 1. |

If prerequisites are already familiar, skip the bridge. These guides do not replace a full Python or front-end language roadmap.

### Session rhythm

A **Day** is a study session, not necessarily a calendar day. Five sessions each week are about **3 hours**; the sixth is a **4-hour project/review**. The schedule is flexible if you study multiple frameworks at once.

| Minutes | Stage | Required action |
|---:|---|---|
| 10 | Recall | Re-type one concept from last session without looking. |
| 40 | Learn | Read the official reference and type small examples yourself. |
| 90 | Build | Implement the listed task without copying a finished solution. |
| 30 | Break/debug | Deliberately create a bug or edge case and diagnose the root cause. |
| 10 | Save | Run checks; `git add`, `git commit`; record learned/confused/next in `journal.md`. |

On review day, reserve four hours for the mini-project, manual negative-case tests, code cleanup, and a brief demo. A day is done only when **the stated acceptance check is shown**, relevant tests pass, code is committed, and you can explain the implementation. If stuck, note the smallest failing case and use the docs or a debugger. **Do not skip failed checkpoints.**

## Complete session roadmap

### Week 1: Days 1–6 — HTTP and FastAPI fundamentals

**Weekly deliverable:** Working notes API prototype with public OpenAPI docs.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Request/response anatomy and status codes | Write a GET health endpoint and inspect headers using curl | 200 and JSON content type match expectations |
| 2 | Path and query parameters | Implement `GET /notes/{id}` with optional search filter | Missing and invalid identifiers return suitable errors |
| 3 | Python type hints and Pydantic models | Define NoteCreate and NoteRead schemas | Invalid request bodies return structured 422 errors |
| 4 | POST, PUT, PATCH and DELETE semantics | Add memory-backed CRUD endpoints | All operations use proper status and method semantics |
| 5 | Response models and documentation | Add tags, descriptions and examples to API routes | `/docs` and `/openapi.json` document accurate contracts |
| 6 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Working notes API prototype with public OpenAPI docs**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 1 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 2: Days 7–12 — Input boundaries and application architecture

**Weekly deliverable:** Well-structured API with robust validation.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Nested models, enums and constraints | Validate note tags, content length and priority | Boundary values and wrong types are rejected consistently |
| 8 | Dependency injection with Depends | Separate a fake repository from route functions | Routes can swap repository with a test override |
| 9 | APIRouter and project layout | Split health, notes and users routes into modules | No circular imports and paths remain unchanged |
| 10 | Custom exceptions and error handlers | Make a unified 404 and domain-error format | Client receives safe messages without internal stack traces |
| 11 | Configuration and environment variables | Load local settings with a typed settings approach | Missing required config fails early without leaking secrets |
| 12 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Well-structured API with robust validation**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 2 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 3: Days 13–18 — Testing and data persistence

**Weekly deliverable:** SQLite CRUD service with migrations and tests.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | TestClient and pytest fixtures | Test all CRUD routes and invalid request cases | 15 tests run with isolated state |
| 14 | SQL tables, keys and constraints | Design users, notes and tags schema | Foreign keys and uniqueness are explained |
| 15 | SQLAlchemy 2 style sessions | Implement repository queries with session-per-request | Create/list/update/delete persists after restart |
| 16 | Alembic migration basics | Create and apply two migrations | A clean database can be created from migrations |
| 17 | Transactions and rollback | Test a failing multi-row transaction | Failure leaves data consistent without partial writes |
| 18 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **SQLite CRUD service with migrations and tests**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 3 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 4: Days 19–24 — Async, concurrency and external I/O

**Weekly deliverable:** API aggregator with resilient timeouts.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Sync vs async route execution | Compare blocking and nonblocking I/O under a toy load | Explain why CPU-heavy work does not benefit from `async` alone |
| 20 | Async HTTP clients and timeouts | Fetch two external endpoints with `httpx.AsyncClient` | Timeout produces a controlled error response |
| 21 | Lifespan management | Initialize and close a shared service during lifespan | Resource shutdown is demonstrated in tests |
| 22 | Streaming and uploads | Upload a small text file with MIME and size checks | Oversized/invalid input receives a clear rejection |
| 23 | BackgroundTasks and task boundaries | Queue a short post-response notification | Understand why durable jobs need a real queue |
| 24 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **API aggregator with resilient timeouts**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 4 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 5: Days 25–30 — Authentication and permissions

**Weekly deliverable:** User-owned protected notes API.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Password hashing and signup policy | Store hashed passwords, never plaintext | Login verifies hash and duplicate signup fails safely |
| 26 | OAuth2 bearer basics and tokens | Issue an expiring bearer token for a demo account | Invalid and expired tokens are rejected |
| 27 | Authorization and ownership checks | Restrict note access to its owner | User A cannot read or modify User B records |
| 28 | CORS, headers and rate limits | Configure an explicit CORS allowlist and review abuse limits | Wildcard credentials are not enabled and error behavior documented |
| 29 | Logging and observability | Add structured request logs and request IDs | Sensitive tokens never appear in logs |
| 30 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **User-owned protected notes API**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 5 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 6: Days 31–36 — API design and delivery mechanics

**Weekly deliverable:** Versioned API with pagination and docs.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Pagination, filtering and deterministic sorting | Add cursor or page-based note listing | No duplicates or missing items between test pages |
| 32 | Idempotency and retries | Implement replay-safe create flow for a simulated client | Duplicate retry does not create two charges/records |
| 33 | OpenAPI contract review | Generate schema and check it in an API client | Examples match real responses on happy/error paths |
| 34 | Performance and caching fundamentals | Measure slow routes then add a safe cache to read-only data | Before/after timings captured without stale private data |
| 35 | Container basics | Write Dockerfile and healthcheck for API | Container starts with non-root settings where possible |
| 36 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Versioned API with pagination and docs**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 6 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 7: Days 37–42 — Production reliability

**Weekly deliverable:** Continuous integration and recovery-ready service.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | PostgreSQL setup and pooling | Run data layer against a temporary PostgreSQL instance | Tests pass with bounded database connections |
| 38 | Integration test isolation | Build disposable DB fixtures and clean up on failure | Full suite can run repeatedly in any order |
| 39 | Secrets and deployment configuration | Set runtime secrets, allowed origins and trusted proxies | No secret committed; config documented |
| 40 | CI pipeline | Run format, type check, tests and container build in CI | Fresh checkout passes automatically |
| 41 | Monitoring and graceful shutdown | Test health/readiness, signal handling and clean exit | No in-flight task hangs indefinitely in the tested case |
| 42 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Continuous integration and recovery-ready service**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 7 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 8: Days 43–48 — Advanced service patterns

**Weekly deliverable:** Event-driven prototype with reliable boundaries.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | WebSockets and connection lifecycle | Build a small authenticated status stream | Closed sockets release connections |
| 44 | Job queues and scheduling concepts | Prototype durable job states with retries | Duplicate retry is handled idempotently |
| 45 | Dependency overrides and fakes | Swap third-party API and clock during tests | Tests remain deterministic offline |
| 46 | Schema evolution and compatibility | Add optional API field without breaking clients | Old request bodies still work |
| 47 | Threat modeling and load limits | Document resource limits, injection boundaries and DoS concerns | Attack simulation does not expose sensitive records |
| 48 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Event-driven prototype with reliable boundaries**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 8 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 9: Days 49–54 — Capstone build

**Weekly deliverable:** Deployable team task API with accounts and audit history.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Scope, entities and access matrix | Define tasks, projects, members and permissions | All role/action combinations are specified |
| 50 | Data and API implementation | Build team CRUD with search and pagination | Schema migrations recreate data model from scratch |
| 51 | Auth and business rules | Enforce ownership, member permissions and task transitions | Cross-team access is denied in tests |
| 52 | Tests and review | Add integration and negative tests plus meaningful logs | At least 35 tests pass including permission failures |
| 53 | Deployment readiness | Prepare Docker, CI, example environment file and API guide | A tester can run API with supplied instructions |
| 54 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Deployable team task API with accounts and audit history**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 9 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 10: Days 55–60 — Capstone release and handoff

**Weekly deliverable:** Demonstrable production-style FastAPI service.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Deploy to an appropriate host | Configure process, DB and secrets on a host | Live API returns expected health/docs without debug exposure |
| 56 | Security review | Check SQL injection, auth bypass, upload limits and CORS | Findings and fixes documented |
| 57 | Latency and failure drill | Simulate DB outage and 20 concurrent requests | Graceful failures and measurements recorded |
| 58 | README, architecture and examples | Write setup, curl examples and diagram | Another developer can use API without explanation |
| 59 | Final review and tag | Record demo, tag release and reflect on trade-offs | End-to-end acceptance checklist and CI pass |
| 60 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Demonstrable production-style FastAPI service**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 10 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

## Checkpoints: stop and demonstrate competence

| Checkpoint | When | Required proof | If you cannot pass |
|---|---|---|---|
| Checkpoint 0 | Day 18 | From a clean setup, demonstrate **sqlite crud service with migrations and tests**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Checkpoint 1 | Day 36 | From a clean setup, demonstrate **versioned api with pagination and docs**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Final capstone | Day 60 | Give a short working demo of **demonstrable production-style fastapi service**, rerun all checks, show README/limitations, and tag a release. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |

## Daily deliberate-debug checklist

- Force one invalid input or unexpected shape and observe the actual error; write down the cause and fix.
- Try a different operating system path, empty dataset, zero-length list, failed network call or wrong credentials **where applicable**.
- Write a small regression test or fixed fixture for the bug instead of only changing code.
- Run a project-level check before committing, and never hide warnings you do not understand.

## Capstone handoff checklist

- [ ] A fresh environment can install dependencies and run the main program.
- [ ] README includes prerequisites, commands, input examples, expected results and limitations.
- [ ] Automated tests or rigorous repeatable checks cover normal, boundary and failure cases.
- [ ] No passwords, API keys, private data, huge datasets or virtual environments are committed.
- [ ] Results and performance claims include the environment, versions and reproducibility method.
- [ ] A peer can follow the documentation without the author present.

## Domain-specific cautions

**Security:** Do not invent your own cryptography. Use supported password-hashing and token libraries; store secrets outside source control. For long-lived jobs use a durable queue rather than relying on in-process `BackgroundTasks`.

## Official learning resources

| Resource | Link |
|---|---|
| FastAPI tutorial | https://fastapi.tiangolo.com/tutorial/ |
| Dependencies | https://fastapi.tiangolo.com/tutorial/dependencies/ |
| SQL databases | https://fastapi.tiangolo.com/tutorial/sql-databases/ |
| Testing | https://fastapi.tiangolo.com/tutorial/testing/ |
| Deployment | https://fastapi.tiangolo.com/deployment/ |

**Resource/version policy:** These are official reference links checked while planning; dependencies and documentation evolve. Use the versions actually installed and verify release-specific API changes before copying an old example. Most resources are free; hosted cloud services or external infrastructure may have costs.

## What comes next

Extend the capstone with one feature, contribute a documentation fix or test to an open-source project, and revisit difficult checkpoints with no notes.

---
*This guide is a practical learning plan, not a credential or a guarantee of proficiency. Adapt the schedule to your pace; passing checkpoints matters more than calendar speed.*
