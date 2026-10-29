# Django (Python) Roadmap: From Zero to Database-Driven Web Apps and Secure Administration

*Created: 29 October 2026 · 12 weeks · 72 sessions · ~228 guided hours*

## Start here

Learn Django templates, forms, ORM, migrations, authentication, security, testing and deployment. Finish a production-style multi-user publication and workflow app.

**Prerequisites:** Python basics, HTML, HTTP, functions/classes, imports, SQL basics and Git; optional preparation sessions bridge these gaps.

**By the end you will have:** a Git repository containing each session, weekly project demos, a journal, documented checkpoint results, tests or quality checks, and a polished capstone with setup steps that another learner can follow.

### Platform setup (Windows, Linux and macOS)

| Platform | Environment creation | Activation | Verify |
|---|---|---|---|
| Windows (PowerShell) | `py -m venv .venv` | `.\.venv\Scripts\Activate.ps1` | `python --version` |
| Linux | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |
| macOS | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |

Run package installations **after activation**, from the guide's project root. On Windows, use the Windows Python launcher (`py`) to create the environment if `python` is not yet configured. For restricted PowerShell execution policies, use Command Prompt with `.venv\Scripts\activate.bat` rather than changing system-wide policy. Confirm that `python -m pip --version` points to the virtual environment. Keep `.venv/` and secrets out of Git. For incompatible versions, consult the official project's install matrix and select a supported Python version; do not silently install an older runtime-wide package.

Install a CPython version supported by your selected **Django release** (check the official compatibility matrix). Use a virtual environment on Windows, Linux or macOS:
```bash
python -m pip install django pytest
python -m django --version
mkdir django-roadmap
cd django-roadmap
python -m django startproject config .
python manage.py migrate
python manage.py runserver
```
This uses SQLite for local learning. Follow your installed Django release's documentation, not a tutorial for a different release. **`runserver` is development-only.**

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

### Week 1: Days 1–6 — Project and request cycle

**Weekly deliverable:** Tiny content site with templates and routes.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Project vs app and manage.py | Create project, `pages` app and first view | Server starts and URL returns expected HTML |
| 2 | URLs, path converters and reverse | Add article slug routes and named URL patterns | Reversing URLs does not hardcode paths |
| 3 | Templates, inheritance and tags | Build base.html and 3 child templates | Shared layout updates in one place |
| 4 | Static files and app structure | Add styles and images without hardcoded paths | `static` references resolve in development |
| 5 | Request, response and 404 handling | Return custom 404 for an unknown article | Existing and missing content are distinguishable |
| 6 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Tiny content site with templates and routes**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 1 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 2: Days 7–12 — Models, ORM and migrations

**Weekly deliverable:** Database-backed publication catalog.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Models, field types and relationships | Define Author, Article and Category with foreign keys | Schema matches drawn entity relationships |
| 8 | Migrations and data evolution | Create model migration then alter field safely | Fresh database migrates to final shape |
| 9 | ORM create, retrieve, update and delete | Implement article repository queries in shell/views | Records survive process restart |
| 10 | Filtering, ordering and aggregates | Add archive and popular-category views | Query results match expected fixture data |
| 11 | Admin customization | Register models with list filters and search | Authorized admin can find and edit records efficiently |
| 12 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Database-backed publication catalog**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 2 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 3: Days 13–18 — Forms, validation and messages

**Weekly deliverable:** Editorial submission workflow.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Forms and ModelForm | Implement create/edit article form with correct widgets | Invalid submissions display field errors |
| 14 | Custom clean methods and constraints | Enforce article status transition and unique slug | Both model/database and form boundaries reject bad data |
| 15 | POST-redirect-GET and CSRF | Make create flow with CSRF protection and redirect | Refresh after save does not duplicate entry |
| 16 | File/media upload safety | Add avatar upload with validation and storage separation | Unsupported file types/oversized payloads are denied |
| 17 | Messages and feedback | Add success/error announcements after actions | Feedback persists through redirect and is accessible |
| 18 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Editorial submission workflow**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 3 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 4: Days 19–24 — Authentication and permissions

**Weekly deliverable:** Role-based author and editor experience.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Django users and login flows | Add signup, login and logout routes | Session persists correctly and logout invalidates it |
| 20 | Authorization vs authentication | Restrict edits to article owner or editor | Guest and non-owner get correct denial |
| 21 | Groups and permissions | Model writer and editor roles | Permission matrix tested for each role |
| 22 | Custom user model decision | Document when to use custom User early in a fresh project | Design choice explained before adding migrations |
| 23 | Password reset and session settings | Build password reset flow with console email backend | Token is single-use or expires as expected |
| 24 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Role-based author and editor experience**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 4 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 5: Days 25–30 — Class-based views and querying

**Weekly deliverable:** Efficient browse/search interface.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Generic class-based views | Replace list/detail boilerplate with ListView/DetailView | Behavior preserved with less duplication |
| 26 | Pagination and filters | Paginate search results with stable ordering | Navigation never repeats or skips rows |
| 27 | N+1 queries and select_related | Profile slow article page and optimize queries | Query-count test records improvement |
| 28 | Prefetching and annotations | Show categories with related authors and counts | Database hits remain bounded |
| 29 | Transactions and concurrent edits | Guard multi-step publish workflow in atomic block | Failure rolls back all dependent changes |
| 30 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Efficient browse/search interface**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 5 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 6: Days 31–36 — Testing and professional habits

**Weekly deliverable:** Tested application with isolated fixtures.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Django TestCase and client | Test routes, redirects and context | 20 useful tests pass against isolated test database |
| 32 | Model validations and constraints tests | Test forbidden duplicates and invalid transitions | Invalid state rejected at suitable layer |
| 33 | Authentication/permission tests | Exercise guest, writer and editor actions | Every restricted view has negative-case tests |
| 34 | Form and upload tests | Test invalid submission and safe file handling | No unexpected 500 or unsafe save |
| 35 | Settings modules and environment | Split dev/prod secrets and debug settings | `DEBUG` disabled in production config |
| 36 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Tested application with isolated fixtures**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 6 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 7: Days 37–42 — Security and production architecture

**Weekly deliverable:** Security-reviewed web application.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Django security checklist | Run `check --deploy` on production settings | Warnings reviewed, fixed or explained |
| 38 | HTTPS cookies, CSRF and XSS | Verify template escaping and cookie flags | Test payload prints safely not executable script |
| 39 | Host headers, proxies and CORS boundary | Configure `ALLOWED_HOSTS`, trusted proxies correctly | Untrusted host rejected and proxy assumptions documented |
| 40 | Static and media storage | Run `collectstatic` and plan media serving | Static assets resolve from built deployment |
| 41 | Caching fundamentals | Cache safe public page or query | Authenticated/private results never leak across users |
| 42 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Security-reviewed web application**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 7 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 8: Days 43–48 — Background work and integration

**Weekly deliverable:** Event and notification flow.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Email templates and notifications | Send publication confirmation through safe mail backend | Message generated without sending real mail in tests |
| 44 | External APIs and robust HTTP requests | Add optional third-party metadata lookup | Timeout/error produces a controlled fallback |
| 45 | Background job architecture | Prototype queued thumbnail or digest task boundary | Request does not assume task completed synchronously |
| 46 | Signals vs explicit service functions | Refactor business rule out of incidental signal | Behavior stays visible and testable |
| 47 | Data import/export | Build CSV import with dry-run and validation | Bad rows reported without corrupting existing data |
| 48 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Event and notification flow**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 8 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 9: Days 49–54 — PostgreSQL and deployment

**Weekly deliverable:** Production-ready service config.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | PostgreSQL backend | Migrate from SQLite to a local PostgreSQL dev DB | Tests and queries run consistently |
| 50 | Schema and index strategy | Add appropriate uniqueness and indexes | Explain query plan for largest query |
| 51 | WSGI/ASGI server concepts | Run app with compatible production server locally | Development `runserver` is not used for release |
| 52 | Deployment files and CI | Add environment template, migrations step and tests workflow | Fresh checkout can build and test automatically |
| 53 | Logging, monitoring and backups | Define backup, restore and audit strategy | Restore drill works with sample data |
| 54 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Production-ready service config**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 9 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 10: Days 55–60 — Advanced workflows

**Weekly deliverable:** Multi-tenant-ish project publishing prototype.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Authorization matrix expansion | Add organization and membership model | Users cannot see unrelated organizations |
| 56 | API layer design choices | Add small JSON endpoints with safe serializers | API never exposes private fields by accident |
| 57 | Concurrency and select_for_update | Protect critical publish or quota operation where DB supports it | Concurrent tests preserve invariants |
| 58 | Full-text search vs LIKE | Compare supported DB search options for articles | Search performance and limitations documented |
| 59 | Accessibility and UX audit | Check templates, forms, navigation and error messages | Key workflows work with keyboard and zoom |
| 60 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Multi-tenant-ish project publishing prototype**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 10 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 11: Days 61–66 — Capstone construction

**Weekly deliverable:** Publication and approval system.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 61 | Feature specification and wireframe | Define writers, reviewers and moderation states | Written acceptance test list covers role cases |
| 62 | Implement publication workflow | Add draft, submit, approve, reject and publish actions | Invalid transitions blocked |
| 63 | Add dashboard, filters, export | Build writer/editor dashboards with status filters | Each role sees only appropriate data |
| 64 | Test security and business rules | Write 40+ tests with fixtures and permission matrix | Unauthorized access and invalid edits fail safely |
| 65 | Create deploy and backup runbook | Document setup, migrations, static and restore | Peer can run locally from README |
| 66 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Publication and approval system**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 11 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 12: Days 67–72 — Capstone release

**Weekly deliverable:** Deployed, documented Django application.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 67 | Deploy with database and safe settings | Publish app with HTTPS and migrations | Homepage, login and workflow live without debug mode |
| 68 | User acceptance drill | Ask tester to complete writer-to-editor sequence | Main happy path works without explanation |
| 69 | Failure and recovery drill | Simulate invalid upload and database failure | App fails safely and recovery process recorded |
| 70 | Performance and accessibility review | Audit query count, mobile layout and semantic HTML | Critical issues fixed, results documented |
| 71 | Release notes and reflection | Tag final version, record demo, add architecture and known limits | Rebuild and tests pass from clean checkout |
| 72 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Deployed, documented Django application**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 12 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

## Checkpoints: stop and demonstrate competence

| Checkpoint | When | Required proof | If you cannot pass |
|---|---|---|---|
| Checkpoint 0 | Day 18 | From a clean setup, demonstrate **editorial submission workflow**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Checkpoint 1 | Day 36 | From a clean setup, demonstrate **tested application with isolated fixtures**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Final capstone | Day 72 | Give a short working demo of **deployed, documented django application**, rerun all checks, show README/limitations, and tag a release. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |

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

**Version rule:** Django releases have strict supported Python ranges. Check before installation, then read the matching versioned docs. SQLite is fine for the early weeks; PostgreSQL is the later deployment track. Never expose `DEBUG=True` or the development server publicly.

## Official learning resources

| Resource | Link |
|---|---|
| Django docs | https://docs.djangoproject.com/en/stable/ |
| Official tutorial | https://docs.djangoproject.com/en/stable/intro/tutorial01/ |
| Security | https://docs.djangoproject.com/en/stable/topics/security/ |
| Deployment checklist | https://docs.djangoproject.com/en/stable/howto/deployment/checklist/ |
| Testing | https://docs.djangoproject.com/en/stable/topics/testing/ |

**Resource/version policy:** These are official reference links checked while planning; dependencies and documentation evolve. Use the versions actually installed and verify release-specific API changes before copying an old example. Most resources are free; hosted cloud services or external infrastructure may have costs.

## What comes next

Extend the capstone with one feature, contribute a documentation fix or test to an open-source project, and revisit difficult checkpoints with no notes.

---
*This guide is a practical learning plan, not a credential or a guarantee of proficiency. Adapt the schedule to your pace; passing checkpoints matters more than calendar speed.*
