# Scala Roadmap: From Zero to Functional Programming, JVM Services and Data Tools — Windows, Linux and macOS

*60 sessions | 10 weeks | approximately 190 hours | Scala 3, Scala CLI, sbt, MUnit, Cats Effect / HTTP*

Learn **Scala 3** from no previous programming experience. Start with variables and functions, then combine object-oriented and functional ideas, typed error handling, tests, SQL and an HTTP service. The final result is a tested, documented JVM application. Scala runs on the Java Virtual Machine for this course; it does **not** require you to learn Java first. The curriculum uses **Scala 3 indentation-based syntax** throughout. You may use the same exercises on Windows, Linux or macOS.

**Platform and scope:** All core sessions use the JVM and are intended to work on **native Windows**, **native Linux** and **macOS**; WSL is optional rather than required. A modern supported JDK is needed. Scala.js and Scala Native, Spark, Akka and Pekko are useful extensions but are **not** prerequisites; their deployments and ecosystems have additional requirements. The service capstone uses a library stack chosen from current official compatibility guides, rather than assuming old Scala 2 examples will work unchanged.

## How one session works

A **day** means one study session, not necessarily one calendar day. Sessions 1–5 of each week take about **3 hours**; the sixth is a **4-hour project and review**. Work in order within a language. If alternating languages, finish the current session before switching.

| Minutes | Block | What you do |
|---:|---|---|
| 10 | Recall | Rebuild a small piece of the previous session from memory. |
| 40 | Learn | Read the specific topic, type examples, explain them in your own words. |
| 90 | Build | Write today's program independently, with at least three test inputs. |
| 30 | Break it | Introduce one deliberate bug, reproduce it, diagnose it, then fix it. |
| 10 | Save | Run the available checks, commit the work, and write 3 journal lines: learned / confused / next step. |

**Completion rule:** do not check off a session merely for reading about a topic. The program must run on the intended platform, expected edge cases must behave correctly, tests or hardware checks must pass where relevant, and you must be able to explain your solution without copying. If stuck for 20 minutes, record what you expected and what happened, minimize the example, and consult the official docs. Hardware sessions can replace the 30-minute bug exercise with a safe fault-injection test; **never deliberately short a circuit or exceed a board's electrical limits**.

## Start here — install once (about 45–90 minutes)

1. Install Scala 3 and Java tools from the **official Coursier instructions** at <https://www.scala-lang.org/download/>. On Windows run the official installer for Windows (PowerShell or CMD) and reopen the terminal; on Linux or macOS follow the OS-specific `cs setup` steps. Coursier can install Scala CLI, sbt and a compatible JVM. Verify `scala -version`, `java -version`, `sbt --version` and `git --version`.
2. Choose **VS Code + Scala (Metals)** or IntelliJ IDEA with the Scala plugin. Install Git. Enable format-on-save only after you understand how to read formatted code.
3. Create `scala-roadmap/` with `journal.md`, one folder per week and a Git repository (`git init`). Set a project-specific Scala version via Scala CLI or `build.sbt` and commit the configuration; avoid floating dependencies during the final project.
4. Use **Scala CLI** for the first several weeks and **sbt** after learning packages, testing and multi-file builds. Start by checking `scala --help`, `scala run --help`, and `sbt --help`. `scala test .` is appropriate for a Scala CLI project configured with a test framework; it is not an automatic test suite for every folder.

| Host OS | What differs | What stays the same |
|---|---|---|
| Windows | PowerShell paths, drive letters, Java/Scala launcher location, Windows firewall. | Scala syntax, JVM bytecode, Scala CLI, sbt and language exercises. |
| Linux | Package libraries, permissions, Bash and terminal setup. | Scala and JVM tools and language exercises. |
| macOS | Homebrew is optional; JDK architecture must match the machine. | Scala and JVM tools and language exercises. |

**Workspace:** `scala-roadmap/week-01` through `week-10`, `docs/`, `journal.md`; keep API tokens and database secrets out of Git. The editor, JVM, Scala runner and terminal are four different pieces: know which one reports each error.

## Your first program

Save this as `hello.scala` and run `scala run hello.scala` (after completing the official setup):

```scala
@main def hello(): Unit =
  val language = "Scala"
  val scores = List(4, 7, 9)
  println(s"Learning $language: ${scores.sum} total points")
```

You will learn the meaning of `@main`, `Unit`, `val`, interpolated strings, and the collection method `sum` in the early sessions.

---

## Part 1 — Language fundamentals and problem solving

### Week 1 — First programs, types and decisions (sessions 1–6)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **1** | What a program is, source-to-JVM execution, `@main`, `println`, comments. | Print a greeting plus a mini interview with 3 hard-coded answers. | Run from a fresh terminal; explain compilation vs execution. |
| **2** | `val`, `var`, `Int`, `Long`, `Double`, `Boolean`, `String`, interpolation, conversion. | Tip calculator and C-to-F converter. | Zero, decimals and invalid numeric input are accounted for. |
| **3** | Arithmetic, comparisons, Boolean logic, `if` expressions, basic pattern `match`. | Shipping/grade decision program. | Test values on each boundary and explain expression results. |
| **4** | `while`, `for` comprehensions as iteration, ranges and `yield`. | Multiplication table, FizzBuzz and a guessing game. | Trace three loop iterations on paper. |
| **5** | Methods with `def`, parameters, results, recursion vs iteration, scope. | `isPrime`, `gcd`, `factorial` and test calls. | Methods are reusable without duplicating their logic. |
| **6** | **Project and review:** control flow + input parsing. | Console calculator with commands, validation and help. | Bad input has a clear message and does not crash; Git commit exists. |

**Break it this week:** Pass text where a number is required; use `==` where you meant assignment; test integer division and empty input.

### Week 2 — Collections and functional thinking (sessions 7–12)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **7** | `List`, `Vector`, `Array`, indexes and immutability. | Analyze a list of 20 scores. | Min, max, average and empty-list case are correct. |
| **8** | `Map`, `Set`, tuples and `Option` as a first look. | Unique-word and frequency counter. | Repeated, empty and missing words behave correctly. |
| **9** | Collection transformations: `map`, `filter`, `flatMap`, `foldLeft`. | Transform a catalog and compute totals. | No index-based mutation required in the final solution. |
| **10** | Anonymous functions, placeholders, higher-order methods, closures. | Create sorting and filtering functions for product records. | Both orderings tested and lambda behavior explained. |
| **11** | Strings, Unicode basics, `split`, regular expressions (lightly). | Text cleaner and basic log parser. | Empty input and Unicode text tested. |
| **12** | **Project and review:** collections + functions. | Command-line contact manager with search and categories. | Add, find, delete and duplicate scenarios pass. |

### Week 3 — Objects, types and program structure (sessions 13–18)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **13** | Classes, instances, constructors, `this`, `private`, `object`. | Bank account and transaction objects. | Invalid operations cannot bypass checks. |
| **14** | `case class`, generated equality, `copy`, immutable data models. | `Book` and `Member` records for a mini library. | Two equal records compare equal and copies preserve originals. |
| **15** | Traits, inheritance vs composition, method overrides and `enum`. | Notification system with two implementations. | Add a notifier without editing client logic. |
| **16** | Parametric types, generic functions and variance intuition. | Generic `Box[A]` and search helper. | Works on strings and numbers with no casts. |
| **17** | Packages, imports, multi-file layout, Scaladoc and REPL. | Split the library into packages and document public APIs. | New files compile without circular dependencies. |
| **18** | **Checkpoint 0:** build from memory. | Inventory CLI with case classes, collections, traits and parsing. | Run, explain and tag `scala-p1`; at least 10 automated assertions. |

## Part 2 — Reliable functional software

### Week 4 — Algebraic data types, errors and testing (sessions 19–24)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **19** | `Option`, `Some`, `None`, exhaustive pattern matching. | Find inventory records without nulls. | Missing IDs produce a typed absence, never a crash. |
| **20** | `Either`, `Try`, explicit error models and exception boundaries. | Validate a purchase with descriptive failures. | Every invalid state has a repeatable test. |
| **21** | Enums with parameters, sealed hierarchies and ADTs. | Model a payment workflow with legal state transitions. | A missing match case is flagged or addressed. |
| **22** | MUnit (or another current Scala 3 test framework), fixtures, assertion quality. | Add 15 tests to inventory code. | Green tests and one deliberately red test shown. |
| **23** | Refactoring pure functions, referential transparency, dependency injection basics. | Extract pricing logic from I/O code. | Pure logic tests without terminal or database. |
| **24** | **Project and review:** error-safe CLI. | Expense tracker with JSON-free in-memory core and tests. | No unchecked `.get`; errors explained; tag `scala-p2`. |

**Break it this week:** Call `.get` on `None` only in an isolated scratch example, then replace it with pattern matching or a safe combinator.

### Week 5 — Files, JSON and JVM interoperability (sessions 25–30)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **25** | Java file APIs through Scala, paths, streams and resource safety. | Import and export records as UTF-8 text. | Files close and failure cases preserve existing data. |
| **26** | JSON through a Scala 3-compatible library; encoding, decoding, validation. | Persist expense data as JSON. | Malformed JSON produces a clear validation error. |
| **27** | Scala CLI dependencies, sbt basics, `build.sbt`, tasks and `test`. | Move a project to sbt; pin library versions. | Fresh clone runs `sbt test` successfully. |
| **28** | Java interoperability, arrays and collections boundaries. | Call a small Java utility from Scala and wrap its result. | Java null is isolated at the boundary. |
| **29** | Logging, argument flags, configuration from environment. | Add CLI options and structured logs. | Secrets never appear in logs or Git history. |
| **30** | **Project and review:** persistent CLI. | Personal reading tracker with imports, exports and 20 tests. | Reload matches saved state; corrupted file handled. |

### Week 6 — Asynchronous and effectful programs (sessions 31–36)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **31** | Threads vs futures, `Future`, `ExecutionContext` and timeouts. | Fetch three simulated remote values concurrently. | Compare timings and catch failures. |
| **32** | Safe shared data: immutable results, synchronized state, queues. | Parallel task aggregator with no shared mutable counter. | Repeated runs produce identical totals. |
| **33** | `for` comprehensions with `Option`, `Either`, and `Future`. | Chain validations and dependent requests. | Explain which context each `for` uses. |
| **34** | Functional effects concept; `IO`/Cats Effect from matched official docs. | Refactor one effectful workflow to an `IO` value. | No work starts before the effect is evaluated. |
| **35** | Resource acquisition/release, retries, cancellation boundaries. | Mock remote client with timeout and resource cleanup. | Failure paths leave no handle open. |
| **36** | **Checkpoint 1:** concurrency and effects. | Concurrent feed combiner with tests and controlled failures. | Timeouts and errors are visible; tag `scala-p3`. |

**Break it this week:** Observe an unhandled failed future and a leaked external resource, then fix both.

## Part 3 — Data persistence and HTTP systems

### Week 7 — SQL and stateful boundaries (sessions 37–42)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **37** | Relational data, schema, keys and parameterized SQL. | Create SQLite tables for notes and tags. | Ten SELECT/JOIN/UPDATE queries checked. |
| **38** | Database access through a maintained Scala/JVM library. | CRUD repository using prepared statements. | Input cannot turn into SQL syntax. |
| **39** | Transactions, migrations and constraint design. | Save two linked records atomically. | Forced failure rolls back both writes. |
| **40** | Separating domain, repository and transport layers. | Stub a repository in unit tests. | Domain tests need no database. |
| **41** | Property-based testing basics (ScalaCheck or equivalent). | Generate invalid and valid payloads. | Hundreds of cases preserve an invariant. |
| **42** | **Project and review:** persistence. | Notes service core with SQLite and migration scripts. | Tests pass against a newly created database. |

### Week 8 — HTTP APIs and application design (sessions 43–48)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **43** | HTTP methods, status codes, REST resources and JSON contracts. | Draw `/notes`, `/notes/{id}` endpoint contract. | Define expected success and error responses. |
| **44** | Start an HTTP server using a compatible Scala 3 stack such as http4s/Cats Effect. | Implement GET `/health` and GET `/notes`. | `curl` receives correct status codes and JSON. |
| **45** | Validation, POST/PATCH/DELETE handlers and errors. | Complete CRUD routes. | Missing and invalid IDs use consistent responses. |
| **46** | HTTP client, `Resource`, middleware and request IDs. | Add request logging and a test client. | Response and resource lifecycles explained. |
| **47** | Authentication concepts, password hashing and access boundaries. | Add a development login flow and authorization tests. | User A cannot access user B's notes; no plain-text passwords. |
| **48** | **Project and review:** API beta. | Connect routes to SQLite and add endpoint tests. | Ten API tests pass with clean database fixtures. |

### Week 9 — Professional practices and deployment (sessions 49–54)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **49** | Configuration, environment variables, input limits and rate limiting. | Harden the API against oversized or malformed requests. | Test rejects bad input without a stack trace. |
| **50** | Observability: logs, metrics basics, exception mapping. | Trace one request from route to DB using IDs. | A failure is diagnosable from logs alone. |
| **51** | Performance: profiling, allocations, benchmarking and avoiding premature tuning. | Benchmark a slow transformation then improve it. | Baseline and repeatable comparison recorded. |
| **52** | Packaging the JVM app, executable JAR/assembly and Docker basics. | Produce a runnable artifact and a container build recipe. | Run outside your editor from documented steps. |
| **53** | Continuous integration with GitHub Actions, lint/format, test matrix. | CI workflow builds and tests on commit. | Clean clone and CI are green. |
| **54** | **Checkpoint 2:** feature complete. | Tested Notes API with DB, validation, logging and access rules. | 30+ tests, README and release candidate tag `scala-p4`. |

**Break it this week:** Send malformed JSON and a duplicate database key; inspect logs and response mapping.

## Part 4 — Capstone and shipping

### Week 10 — Capstone: a deliverable Scala service (sessions 55–60)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **55** | Choose and scope: notes, expense, reading or small inventory API. | One-page design with entities, routes and failure cases. | Five measurable acceptance criteria written. |
| **56** | Build domain rules first with tests. | Finish model, commands and validation. | Core invariants covered without I/O. |
| **57** | Implement persistence and migrations. | Database repository plus integration tests. | Fresh DB initializes and survives restart. |
| **58** | Implement routes, auth boundary and request validation. | Complete HTTP API and sample requests. | All required endpoints demo end-to-end. |
| **59** | Polish security, performance, docs and packaging. | Add failure tests, Docker instructions and example data. | Another computer or clean environment runs it. |
| **60** | **Final review and release:** demo and code walk-through. | Record a short demo, fix three issues, publish repo and tag `scala-v1`. | Stranger can run tests and start API from README in 15 minutes. |

---

## Checkpoints — do not move forward with gaps

| Gate | Session | Pass condition | If you miss it |
|---|---:|---|---|
| Checkpoint 0 | 18 | Inventory CLI with case classes, traits, collections and at least 10 tests; explain its types. | Repeat weakest topic from weeks 1–3. |
| Checkpoint 1 | 36 | Concurrent workflow that reports failures, releases resources and passes tests. | Redo effects and error-handling sessions. |
| Checkpoint 2 | 54 | Database-backed Notes API with access checks and 30+ tests, buildable from a fresh checkout. | Add a focused week on any missing layer. |
| Capstone | 60 | Clean clone, reproducible build, README, demo, tests and `scala-v1` tag. | Do not ship until a second person can run it. |

## Final capstone specification

Deliver an **authenticated personal notes / inventory REST API** (or a similarly scoped domain) with Scala 3, a stable HTTP library stack, typed errors, parameterized SQL, schema migrations, tests and a reproducible run command. Keep business logic in pure functions. Include sample data, test-user fixtures, a threat-notes paragraph, README, API examples and a CI workflow. **Never include real passwords, production keys or personal datasets.**

**Minimum acceptance test:** fresh clone → install stated JDK and Scala tools → create database → run tests → launch server → create/read/update/delete one record → demonstrate unauthorized access is blocked → restart and confirm persistence.

**Optional after core:** choose one 4–6-session extension: (A) Spark data processing with a version-compatible Scala build, (B) Scala.js user interface, (C) a streaming service, or (D) Scala Native experimentation. These are additional tracks, not included in the 60 sessions.

## Resources (official starting points)

| Resource | Use it for | Cost |
|---|---|---|
| [Install Scala](https://www.scala-lang.org/download/) | OS-specific Coursier/Scala 3 setup; verify versions before installation. | Free |
| [Scala 3 Book](https://docs.scala-lang.org/scala3/book/introduction.html) | Language concepts, examples and typed programming. | Free |
| [Tour of Scala](https://docs.scala-lang.org/tour/tour-of-scala.html) | Bite-sized explanations and syntax reference. | Free |
| [Scala CLI](https://scala-cli.virtuslab.org/) | Running and testing small Scala projects. | Free |
| [sbt](https://www.scala-sbt.org/) | Builds, dependencies and multi-file projects. | Free |
| [MUnit](https://scalameta.org/munit/) | Unit testing. | Free |
| [Typelevel](https://typelevel.org/) | Cats Effect, http4s ecosystem and examples. | Free |
| [Scala Exercises](https://www.scala-exercises.org/) | Additional interactive practice; check Scala-version compatibility. | Free |

**Version note:** project templates and libraries change. Use supported **Scala 3** examples and consistent versions documented by each library; many online snippets still target Scala 2.

## What you can do next

You can write idiomatic Scala 3 code, model programs with algebraic data types, test functional logic, talk to databases and ship a small JVM HTTP service. Keep practicing by contributing a bug fix to a Scala 3 library, reading source code and building a second API without following the guide. For big-data jobs study Spark; for advanced concurrent systems deepen Cats Effect and typed streams; for JVM-heavy teams learn interoperation and profiling.

