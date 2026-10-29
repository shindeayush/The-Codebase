# pytest (Python) Roadmap: From Zero to Professional Testing, Fixtures and CI

*Created: 29 October 2026 · 8 weeks · 48 sessions · ~152 guided hours*

## Start here

Progress from `assert` and test discovery to parametrization, fixtures, mocks, property-based ideas, integration testing, CI, coverage and a tested Python package.

**Prerequisites:** Python functions, exceptions, packages, imports and a little OOP. No prior testing framework experience assumed.

**By the end you will have:** a Git repository containing each session, weekly project demos, a journal, documented checkpoint results, tests or quality checks, and a polished capstone with setup steps that another learner can follow.

### Platform setup (Windows, Linux and macOS)

| Platform | Environment creation | Activation | Verify |
|---|---|---|---|
| Windows (PowerShell) | `py -m venv .venv` | `.\.venv\Scripts\Activate.ps1` | `python --version` |
| Linux | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |
| macOS | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |

Run package installations **after activation**, from the guide's project root. On Windows, use the Windows Python launcher (`py`) to create the environment if `python` is not yet configured. For restricted PowerShell execution policies, use Command Prompt with `.venv\Scripts\activate.bat` rather than changing system-wide policy. Confirm that `python -m pip --version` points to the virtual environment. Keep `.venv/` and secrets out of Git. For incompatible versions, consult the official project's install matrix and select a supported Python version; do not silently install an older runtime-wide package.

Use a Python virtual environment on Windows, Linux or macOS:
```bash
python -m pip install -U pytest pytest-cov
python -m pytest --version
```
Create `test_sample.py`:
```python
def add(a, b):
    return a + b

def test_add():
    assert add(2, 3) == 5
```
Run `python -m pytest -q`. Organize production code under a package and tests under `tests/` as the guide progresses.

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

### Week 1: Days 1–6 — Testing mindset and first tests

**Weekly deliverable:** Pure-function utility package with focused unit tests.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Behavioral tests, assertions and discovery | Create three tests for `slugify` helper | `python -m pytest` discovers tests and reports clean results |
| 2 | Arrange-act-assert and naming | Test temperature converter with meaningful names | Each test expresses one behavior and failure is understandable |
| 3 | Boundary/invalid inputs | Add empty, negative and overflow-like cases to utility | At least one test initially exposes a bug |
| 4 | Exception assertions | Test invalid input using `pytest.raises` | Exact error behavior documented and checked |
| 5 | Test isolation and independence | Intentionally reorder tests and remove shared mutable state | Running individual or whole suite gives same outcomes |
| 6 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Pure-function utility package with focused unit tests**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 1 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 2: Days 7–12 — Parametrization and markers

**Weekly deliverable:** Comprehensive edge-case suite.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Parametrize input/output | Cover ten cases of parsing function in one parameterized test | Failing parameter ID points to case |
| 8 | Readable ids and edge-case matrix | Generate descriptive test IDs for invalid strings | Each case is unambiguous in report |
| 9 | pytest.approx and floating point | Test currency or geometry approximations with tolerances | Tolerance reflects scale and purpose |
| 10 | Markers and selection | Add slow/integration markers and configure registry | `-m 'not slow'` selects expected tests |
| 11 | Skip and expected failures | Represent unsupported platform feature with skip/xfail | Unexpected pass is noticed, not silently hidden |
| 12 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Comprehensive edge-case suite**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 2 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 3: Days 13–18 — Fixtures and lifecycle

**Weekly deliverable:** Temporary-file-backed tested notes service.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Fixtures and dependency injection | Provide sample records and temporary storage to tests | Each test receives fresh state |
| 14 | tmp_path and filesystem tests | Test writing, reloading and malformed file | No files leak outside test temp directory |
| 15 | Fixture scopes and yield teardown | Create managed resource with cleanup | Teardown executes after passing and failing test |
| 16 | conftest.py and fixture sharing | Share reusable test setup across two modules | Tests use fixtures without manual import hacks |
| 17 | Factory fixtures and parameterized fixtures | Generate users/records with configurable fields | Repeated test cases do not share mutable objects |
| 18 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Temporary-file-backed tested notes service**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 3 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 4: Days 19–24 — Mocks, fakes and dependency boundaries

**Weekly deliverable:** External-API-free integration test pack.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | monkeypatch and environment variables | Replace environment config during test | Changes are restored automatically |
| 20 | Fakes vs mocks | Fake network client that returns known data | No live network needed for tests |
| 21 | Mock calls and contracts | Verify notifier called once with appropriate payload | Test concerns behavior not incidental internals |
| 22 | Time and randomness control | Inject clock and random generator into logic | Repeated runs deterministic |
| 23 | Failure injection | Simulate disk error and service timeout | Error handling verified without external failure |
| 24 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **External-API-free integration test pack**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 4 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 5: Days 25–30 — Integration and database testing

**Weekly deliverable:** API + database integration suite.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Unit vs integration vs end-to-end | Draw test pyramid for a small app | Each test justified by boundary it covers |
| 26 | SQLite temporary DB fixtures | Create test schema and teardown after test | DB tests run in arbitrary order |
| 27 | HTTP test clients | Test Flask or FastAPI JSON request/response in memory | Status, content type and JSON shape checked |
| 28 | Contract tests | Check serializer/schema backward compatibility | Old request fixture still accepted intentionally |
| 29 | Test data management | Use small deterministic factories and cleanup | Failing test does not contaminate next test |
| 30 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **API + database integration suite**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 5 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 6: Days 31–36 — Coverage and quality of tests

**Weekly deliverable:** Test suite with measured effectiveness.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Coverage with pytest-cov | Capture statement/branch coverage | Report highlights specific untested behavior |
| 32 | Mutation testing concept | Manually change 3 code paths to wrong behavior | At least 2 corresponding tests fail for good reason |
| 33 | Anti-patterns: brittle mocks, time.sleep | Refactor flaky timing-based test into deterministic synchronization | Failing conditions reliably repeat |
| 34 | Parameterized scenario matrix | Cover auth/role/action grid with parametrization | Missing permissions detected clearly |
| 35 | Property-based thinking | Write invariants for sort/parse/serialize round trips | Randomized sample inputs respect documented property |
| 36 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Test suite with measured effectiveness**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 6 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 7: Days 37–42 — CI and larger suites

**Weekly deliverable:** Fast and cross-platform CI workflow.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | pyproject.toml pytest config | Set test paths, markers and warnings policies | Fresh checkout uses same pytest settings |
| 38 | Running subsets, keyword and markers | Define fast development vs full CI commands | Correct groups selected for each workflow |
| 39 | Parallel tests and resource conflicts | Test order/parallel-safety ideas, optionally use xdist | Isolation prevents port and temp-file collision |
| 40 | Windows/Linux/macOS matrix | Configure CI on multiple platforms where practical | Failures are visible for each OS |
| 41 | Debugging CI failures | Reproduce one intentionally failing test locally | Root cause documented with minimal reproduction |
| 42 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Fast and cross-platform CI workflow**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 7 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 8: Days 43–48 — Capstone and maintainability

**Weekly deliverable:** Published, tested Python package with CI.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Package skeleton and public API | Create reusable parser/validator package with README | `pip install -e .` and imports work |
| 44 | Build unit and integration suites | Add cases for valid, invalid and IO operations | At least 50 meaningful tests pass |
| 45 | Coverage and failure quality | Measure branch coverage and inject deliberate bug | Tests detect bug; uncovered critical code fixed |
| 46 | CI, environment and docs | Create workflow, sample pytest command and contribution guide | CI green from clean checkout |
| 47 | Release review and tag | Publish archive/repo, tag release and present short failure analysis | New developer can run checks with one command |
| 48 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Published, tested Python package with CI**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 8 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

## Checkpoints: stop and demonstrate competence

| Checkpoint | When | Required proof | If you cannot pass |
|---|---|---|---|
| Checkpoint 0 | Day 18 | From a clean setup, demonstrate **temporary-file-backed tested notes service**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Checkpoint 1 | Day 36 | From a clean setup, demonstrate **test suite with measured effectiveness**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Final capstone | Day 48 | Give a short working demo of **published, tested python package with ci**, rerun all checks, show README/limitations, and tag a release. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |

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

**Quality rule:** A high coverage percentage is not proof of useful tests. Prefer observable behaviors, isolated fixtures and negative cases. Never let a test rely on live third-party services unless it is a clearly labelled optional integration test.

## Official learning resources

| Resource | Link |
|---|---|
| pytest getting started | https://docs.pytest.org/en/stable/getting-started.html |
| Fixtures | https://docs.pytest.org/en/stable/how-to/fixtures.html |
| Parametrize | https://docs.pytest.org/en/stable/how-to/parametrize.html |
| Monkeypatch | https://docs.pytest.org/en/stable/how-to/monkeypatch.html |
| pytest-cov | https://pytest-cov.readthedocs.io/en/latest/ |

**Resource/version policy:** These are official reference links checked while planning; dependencies and documentation evolve. Use the versions actually installed and verify release-specific API changes before copying an old example. Most resources are free; hosted cloud services or external infrastructure may have costs.

## What comes next

Extend the capstone with one feature, contribute a documentation fix or test to an open-source project, and revisit difficult checkpoints with no notes.

---
*This guide is a practical learning plan, not a credential or a guarantee of proficiency. Adapt the schedule to your pace; passing checkpoints matters more than calendar speed.*
