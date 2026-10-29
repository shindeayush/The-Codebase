# Flask (Python) Roadmap: From Zero to Small Web Apps, APIs and Production Practices

*Created: 29 October 2026 · 8 weeks · 48 sessions · ~152 guided hours*

## Start here

Understand the WSGI request cycle, templates, blueprints, application factories, database access, sessions, testing and secure deployment through a focused Flask app.

**Prerequisites:** Python functions, objects, packages, decorators, basic HTML/CSS, HTTP and Git; no earlier Django or FastAPI required.

**By the end you will have:** a Git repository containing each session, weekly project demos, a journal, documented checkpoint results, tests or quality checks, and a polished capstone with setup steps that another learner can follow.

### Platform setup (Windows, Linux and macOS)

| Platform | Environment creation | Activation | Verify |
|---|---|---|---|
| Windows (PowerShell) | `py -m venv .venv` | `.\.venv\Scripts\Activate.ps1` | `python --version` |
| Linux | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |
| macOS | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |

Run package installations **after activation**, from the guide's project root. On Windows, use the Windows Python launcher (`py`) to create the environment if `python` is not yet configured. For restricted PowerShell execution policies, use Command Prompt with `.venv\Scripts\activate.bat` rather than changing system-wide policy. Confirm that `python -m pip --version` points to the virtual environment. Keep `.venv/` and secrets out of Git. For incompatible versions, consult the official project's install matrix and select a supported Python version; do not silently install an older runtime-wide package.

With a supported Python installation and virtual environment on Windows, Linux or macOS, run:
```bash
python -m pip install flask pytest flask-sqlalchemy
```
Write `app.py`:
```python
from flask import Flask
app = Flask(__name__)
@app.get('/')
def index():
    return {'status': 'ok'}
```
Run `python -m flask --app app run --debug` **only on your local development machine**. Build a package/app factory later; do not deploy Flask's development server or debugger.

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

### Week 1: Days 1–6 — Flask and the web

**Weekly deliverable:** Multi-route guestbook prototype.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | WSGI, routes and requests | Create health, hello and notes routes | Correct status/body returned for each route |
| 2 | Path parameters and URL building | Add note detail with `url_for` and redirects | URLs are named and reversed rather than hardcoded |
| 3 | Methods, query and form data | Implement GET form and POST submit | Missing values are validated with a helpful response |
| 4 | Responses, JSON, errors and status | Implement 404 JSON and HTML variants | Content type and status correct for each client |
| 5 | Templates and autoescaping | Render guestbook with Jinja inheritance | Untrusted text is escaped in HTML |
| 6 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Multi-route guestbook prototype**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 1 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 2: Days 7–12 — Application organization

**Weekly deliverable:** Maintainable notes web app.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Static files and template inheritance | Implement shared layout and static CSS | Two views reuse layout and styles |
| 8 | Application factory pattern | Convert single file into `create_app` package | Multiple test app instances can be created |
| 9 | Blueprints and routing | Split auth, notes and health routes | No circular imports and URL behavior preserved |
| 10 | Configuration and env | Add development/test configs with secret setting | Test and production configs differ safely |
| 11 | Error handlers and logging | Add custom not-found and server-error pages | User sees safe details and server log has diagnosis |
| 12 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Maintainable notes web app**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 2 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 3: Days 13–18 — Persistence and data modeling

**Weekly deliverable:** SQLite-backed personal journal.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | SQLite schema and safe query parameters | Create notes table with constraints | SQL injection test cannot alter query meaning |
| 14 | SQLAlchemy ORM basics | Add Note/User models and scoped sessions | New notes persist after app restart |
| 15 | Database initialization and migration planning | Create migrations with a compatible migration tool | Clean DB reproducibly reaches latest schema |
| 16 | Transactions, commit and rollback | Perform two-step note update atomically | Failed step leaves original data unchanged |
| 17 | Pagination, filtering and indexes | Add category/date filters with stable pagination | Page results deterministic across runs |
| 18 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **SQLite-backed personal journal**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 3 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 4: Days 19–24 — Accounts, forms and security

**Weekly deliverable:** Private accounts and protected notes.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Sessions and signed cookies | Implement login session and logout | Session data never stores password or other secrets |
| 20 | Password hashing | Register users with a maintained password hash implementation | Plaintext password never written to DB |
| 21 | CSRF and form protection | Add CSRF defense for state-changing browser forms | Forged POST rejected in integration test |
| 22 | Authorization checks | Enforce owner-only note read/write | Different user cannot inspect note even by guessed ID |
| 23 | Safe file upload | Add profile avatar with size/type checks | Oversized and unsupported payload rejected |
| 24 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Private accounts and protected notes**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 4 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 5: Days 25–30 — Testing and API integration

**Weekly deliverable:** Testable modular web/API service.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | pytest and Flask test client | Exercise routes with isolated app/database fixture | At least 18 tests pass offline |
| 26 | Mocking external clients | Fake a weather or metadata API in test | Network failures cannot make tests flaky |
| 27 | JSON API and validation | Add versioned `/api/notes` routes | Invalid request bodies receive meaningful 4xx |
| 28 | Blueprint-level integration tests | Cover auth, notes and errors end to end | Every protected route has negative test |
| 29 | Performance profiling | Measure slow N+1 DB access then fix it | Query count decreases with recorded evidence |
| 30 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Testable modular web/API service**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 5 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 6: Days 31–36 — Architecture extensions

**Weekly deliverable:** Reliable reminder service prototype.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | CLI commands and Click | Add `flask` command to seed sample data | Command idempotent and returns useful exit status |
| 32 | Email/notification boundary | Send a simulated reminder via dependency function | Delivery failure does not corrupt request data |
| 33 | Caching and state | Cache safe public metadata, document invalidation | Private data never shared between users |
| 34 | Background tasks and queue design | Define durable retryable reminder job | A dropped process cannot silently lose tracked work |
| 35 | Authentication hardening | Review session expiry, cookie settings and rate limits | Relevant security tests verify config |
| 36 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Reliable reminder service prototype**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 6 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 7: Days 37–42 — Deployment and operations

**Weekly deliverable:** Repeatable production-like release.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Production WSGI server | Serve app with a compatible WSGI server or platform adapter | No use of Flask development server in production |
| 38 | Reverse proxy and HTTPS | Configure trusted host, HTTPS and headers in demo | No untrusted header assumptions |
| 39 | App logging and error reporting | Add request IDs and structured warnings | Tokens and passwords excluded from logs |
| 40 | Database backup and recovery | Snapshot and restore test database | Restored data matches sample dataset |
| 41 | CI, dependency audit and settings | Run tests, lint and dependency checks in pipeline | Clean checkout gets green build |
| 42 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Repeatable production-like release**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 7 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 8: Days 43–48 — Capstone

**Weekly deliverable:** Deployed personal journal with accounts and optional API.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Scope, schema and user stories | Specify journal CRUD, search, login and privacy constraints | 12 acceptance checks written |
| 44 | Build application | Implement views, filters, categories and notes API | Main workflows work with browser and curl |
| 45 | Security and tests | Cover CSRF, session behavior and cross-user access | At least 30 tests pass with negative cases |
| 46 | UX, accessibility and docs | Improve forms, flash messages, README and API examples | Tester completes tasks using keyboard |
| 47 | Deploy and final review | Package release, demo, tag and capture recovery instructions | Stranger can reproduce app from README and test it |
| 48 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Deployed personal journal with accounts and optional API**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 8 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

## Checkpoints: stop and demonstrate competence

| Checkpoint | When | Required proof | If you cannot pass |
|---|---|---|---|
| Checkpoint 0 | Day 18 | From a clean setup, demonstrate **sqlite-backed personal journal**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Checkpoint 1 | Day 36 | From a clean setup, demonstrate **reliable reminder service prototype**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Final capstone | Day 48 | Give a short working demo of **deployed personal journal with accounts and optional api**, rerun all checks, show README/limitations, and tag a release. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |

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

**Important:** The built-in debugger is a remote-code-execution risk if exposed publicly; it is strictly for local development. Flask does not give you a complete authentication/ORM/migration stack automatically—select and test extensions deliberately.

## Official learning resources

| Resource | Link |
|---|---|
| Flask quickstart | https://flask.palletsprojects.com/en/stable/quickstart/ |
| Flask tutorial | https://flask.palletsprojects.com/en/stable/tutorial/ |
| Flask testing | https://flask.palletsprojects.com/en/stable/testing/ |
| Flask security | https://flask.palletsprojects.com/en/stable/web-security/ |
| Deployment | https://flask.palletsprojects.com/en/stable/deploying/ |

**Resource/version policy:** These are official reference links checked while planning; dependencies and documentation evolve. Use the versions actually installed and verify release-specific API changes before copying an old example. Most resources are free; hosted cloud services or external infrastructure may have costs.

## What comes next

Extend the capstone with one feature, contribute a documentation fix or test to an open-source project, and revisit difficult checkpoints with no notes.

---
*This guide is a practical learning plan, not a credential or a guarantee of proficiency. Adapt the schedule to your pace; passing checkpoints matters more than calendar speed.*
