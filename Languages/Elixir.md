# Elixir Roadmap: From Zero to Concurrent Systems, OTP and Phoenix — Windows, Linux and macOS

*60 sessions | 10 weeks | approximately 190 hours | Elixir, Erlang/OTP, Mix, ExUnit, Ecto, Phoenix and LiveView*

This roadmap starts from **no programming experience**, teaches the Elixir language and its immutable, functional style, then uses Erlang/OTP processes and supervision to build fault-tolerant programs. Finish by publishing a tested **Phoenix** web application with live updates and persistence. Elixir is built on the Erlang VM (BEAM); it does not require learning Erlang first. Every session has a learn/build/pass condition, and every sixth session is a larger review project.

**Platforms:** Core Elixir programs, Mix projects, ExUnit tests and OTP work on supported **native Windows, Linux and macOS** installations. Windows is **not merely a WSL option**; official installers and setup instructions exist. Phoenix, Ecto and their external toolchains (database/asset tools) can introduce platform-specific setup. On Windows, choose either native development following the official Phoenix instructions or WSL for a Linux-like environment; do not mix the dependency and executable paths of the two. PostgreSQL is common, but the guide offers supported **SQLite** for a lighter starting database if the current generator supports it.

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

## Start here — setup (about 60–90 minutes)

1. Install Erlang/OTP and a **compatible** recent stable Elixir from <https://elixir-lang.org/install.html>. Follow the OS-specific steps: **Windows** offers installers/PowerShell scripts or supported package managers, **Linux** has distro packages/install scripts/version managers, and **macOS** has Homebrew or install scripts. Elixir and OTP versions must be compatible. Verify `elixir --version`, `mix --version`, `erl` and `git --version`.
2. Install **VS Code + ElixirLS** (or a maintained Elixir editor integration). Start `iex` for the interactive Elixir shell; type `1 + 1`, then exit with `Ctrl+C` twice.
3. Make `elixir-roadmap/`, add `journal.md`, weekly subfolders, and `git init`. After fundamentals, create projects with `mix new task_tracker`; inspect the generated test files and `mix.exs`.
4. Run `mix local.hex` and `mix local.rebar` when your dependencies require package/build tools; consult the official prompts. For the Phoenix stage, check its own version-specific installation page and follow its database instructions.

| Host | Native setup notes | Before Phoenix week |
|---|---|---|
| Windows | Run `elixir.bat`/`iex.bat` if launchers require it; use PowerShell/CMD and correct OTP+Elixir installers. | Confirm database tooling and asset tool compatibility; WSL is optional. |
| Linux | Use supported distribution packages or install scripts; old distro Elixir may be incompatible. | Verify database service and any required compilers. |
| macOS | Homebrew or official script with a compatible OTP. | Verify database service and asset tooling. |

**Daily gate:** `mix test` must pass once a Mix project exists. Avoid running external scripts as administrator and never put real credentials into `config/*.exs` files committed to Git. Use environment variables for secrets.

## First program

Save `hello.exs`, run `elixir hello.exs`:

```elixir
name = "Elixir"
scores = [4, 7, 9]
IO.puts("Learning #{name}: #{Enum.sum(scores)} points")
```

`iex` runs expressions interactively, `.exs` is handy for scripts, and a Mix project is best for larger programs. Learn the distinction before using Phoenix.

---

## Part 1 — Functional programming from the ground up

### Week 1 — First expressions and control flow (sessions 1–6)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **1** | Program execution, `.ex` vs `.exs`, `IO.puts`, IEx, comments and basic `mix`. | Print greetings and ask for two inputs. | Run with `elixir` and explain IEx vs script execution. |
| **2** | Numbers, strings, Booleans, atoms, immutable binding, interpolation. | Tip/tax calculator with formatted messages. | Predict results of integer vs float arithmetic. |
| **3** | Pattern matching using `=`, tuples, destructuring, comparisons. | Extract values from a simulated order. | Correct and failed matches are explained. |
| **4** | `if`, `unless`, `cond`, `case`, guards and simple validation. | Grade selector and access-code checker. | Every valid branch and rejection is tested. |
| **5** | Lists, ranges, `Enum` introductions and `for` comprehensions. | FizzBuzz, multiples and a numeric summary. | Results correct for empty and boundary values. |
| **6** | **Project and review:** control flow and user input. | A repeatable quiz or budget calculator script. | Handles unexpected input gracefully and is committed. |

**Break it this week:** Attempt a pattern match that fails; compare it with a normal assignment in another language.

### Week 2 — Collections, functions and pipelines (sessions 7–12)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **7** | Tuples, keyword lists, maps and structs preview. | Store a catalog and search by SKU. | Missing keys handled explicitly. |
| **8** | Functions, arity, multiple clauses and guards. | Reusable `price/2`, `discount/2` and `is_prime/1`. | Clause errors are avoided for documented inputs. |
| **9** | Anonymous functions, captures and passing functions to `Enum`. | Summarize and sort mock orders. | No repeated logic across report formats. |
| **10** | Pipelines using the pipe operator, `Enum.map/filter/reduce`, immutability. | Build a multi-step text-cleaning pipeline. | Explain each stage and test empty input. |
| **11** | Recursion, tail recursion intuition, `Enum` vs hand recursion. | Recursive sum and list flatten exercise. | Compare iterative and recursive approaches. |
| **12** | **Project and review:** collections. | Invoice reporter with grouped totals and filtering. | 10 cases produce the expected output from deterministic fixtures. |

### Week 3 — Modules, errors and testing (sessions 13–18)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **13** | Modules, `def` vs `defp`, aliases, imports and documentation. | Split invoice tools into three modules. | Public API small and examples documented. |
| **14** | Maps and structs in depth, `@enforce_keys`, type specs. | Model `Invoice`, `LineItem` and status structs. | Required values cannot be omitted silently. |
| **15** | `{:ok, value}` and `{:error, reason}`, `with`, `case`. | Validate line items and report all failure paths. | No success path accepts negative quantity. |
| **16** | Exceptions, `rescue`, `try`, and when not to raise. | Parse a file without crashing the CLI on bad input. | Error messages are understandable. |
| **17** | Mix projects, `ExUnit`, doctests and assertions. | Write 15 tests for invoice modules. | `mix test` passes and a planted error fails. |
| **18** | **Checkpoint 0:** build from memory. | Tested CLI spending tracker with modules and structs. | Run with Mix, at least 15 tests, tag `elixir-p1`. |

## Part 2 — Reliable applications and concurrency

### Week 4 — Files, processes and message passing (sessions 19–24)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **19** | File APIs, streams, UTF-8 and safe JSON parsing with a suitable package. | Save/load the spending tracker. | Restart preserves data; malformed file is rejected. |
| **20** | Processes with `spawn`, `self`, `send`, `receive`, mailboxes. | Two processes exchanging messages. | Explain process identities and receive order. |
| **21** | Recursion as a process loop, selective receives, timeouts. | Counter process that handles stop and bad requests. | Stops cleanly without hanging tests. |
| **22** | `Task` and `Task.async_stream`, concurrency vs parallelism. | Run bounded concurrent data fetches. | Report failures and total runtime. |
| **23** | State ownership, process isolation and failure propagation. | Replace mutable global counter with message-driven state. | Parallel calls do not lose updates. |
| **24** | **Project and review:** concurrent worker. | Bounded task queue with result aggregation and errors. | Handles 100 tasks with no forgotten results. |

**Break it this week:** Have a process receive an unexpected message and make the timeout visible; add a catch-all handler.

### Week 5 — GenServer, supervision and OTP (sessions 25–30)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **25** | `GenServer` callbacks, `start_link`, `call`, `cast` and state. | Convert counter process into a GenServer. | State survives multiple client calls and validation works. |
| **26** | Applications, `Application.start`, supervision trees. | Supervise a worker in a Mix application. | Crashing worker restarts and other workers remain healthy. |
| **27** | Supervisor strategies, transient vs permanent workers. | Create two supervised jobs and inspect restart behavior. | Explain chosen restart policy. |
| **28** | Registry, dynamic supervisors and naming processes. | Start one per-user session worker. | Duplicate names rejected safely. |
| **29** | Timers, `Process.monitor`, `Task.Supervisor`, telemetry basics. | Add tracked timeout jobs and retry policy. | Failing jobs cannot stall unrelated work. |
| **30** | **Checkpoint 1:** OTP core. | Supervised background job runner with tests. | Restart works under injected failure; tag `elixir-p2`. |

**Break it this week:** Crash a child process in a *test* environment and inspect the supervisor restart count.

### Week 6 — Testing, APIs and operational basics (sessions 31–36)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **31** | Testing async code, Mox/fakes concepts, `ExUnit.Case`. | Add 20 focused tests to job runner. | Deterministic tests do not rely on arbitrary `sleep`. |
| **32** | Property-based testing idea (StreamData optional), data invariants. | Generate random valid tasks and rejection cases. | Counter invariant holds across many seeds. |
| **33** | HTTP fundamentals, external requests with a maintained library. | Fetch and parse JSON from a test endpoint. | Timeouts, status failures and invalid JSON handled. |
| **34** | Environment configuration, secrets, logging and telemetry. | Make a configurable job polling interval. | Logging excludes tokens and identifying user data. |
| **35** | Dialyzer/`dialyxir` optional, Credo, code formatting. | Format and inspect the project. | `mix format --check-formatted` and tests pass. |
| **36** | **Project and review:** service boundary. | Small poller that gathers simulated health statuses. | Backoff and bad-response tests pass. |

## Part 3 — Data and web applications

### Week 7 — Databases and Ecto (sessions 37–42)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **37** | Relational modeling, SQL tables, keys and joins. | Draw tasks/users/jobs schema; run 10 SQL queries. | Foreign keys and unique constraints justified. |
| **38** | Ecto `Repo`, schemas, changesets, validations. | Model `Task` and `User` with changesets. | Invalid data rejected before DB insert. |
| **39** | Database setup with SQLite adapter or PostgreSQL, Ecto migrations. | Create tasks table and add a unique index. | Fresh DB migrates successfully. |
| **40** | CRUD queries, associations, changeset errors and transactions. | Implement task storage repository. | A failed multi-step write rolls back. |
| **41** | Factory fixtures, sandbox/isolation and integration tests. | Add repository tests and a migration test. | Repeatable tests leave no data behind. |
| **42** | **Project and review:** data-backed tasks. | CLI task manager with Ecto persistence and OTP worker. | Records survive a restart; tests run on fresh DB. |

### Week 8 — Phoenix and LiveView (sessions 43–48)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **43** | Phoenix generator setup, router, controllers and endpoint. | Generate a Phoenix app using current official docs. | `mix phx.server` works on selected host. |
| **44** | Routes, controllers, rendering, request parameters. | Build an index and task-detail page or JSON endpoints. | Missing resource returns appropriate status. |
| **45** | Phoenix contexts and forms/changesets. | Create/edit/delete tasks via browser. | Invalid form displays actionable feedback. |
| **46** | LiveView lifecycle, assigns, events and LiveComponents basics. | Convert task list into interactive LiveView. | Updates appear without a manual refresh. |
| **47** | Authorization fundamentals, sessions, CSRF and safe handling of secrets. | Restrict edits to task owners with tests. | One user cannot modify another user's data. |
| **48** | **Project and review:** live app beta. | Live task board backed by Ecto. | End-to-end add/edit/delete flows pass. |

**Break it this week:** Submit unauthorized LiveView events and malformed form data; verify boundary enforcement.

### Week 9 — Fault tolerance, security and deployment (sessions 49–54)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **49** | PubSub and server-rendered real-time updates. | Broadcast task updates to two browser sessions. | Both views show the correct state. |
| **50** | Background jobs and supervision in the web app. | Run a scheduled reminder through supervised workers. | Restart and error behavior logged. |
| **51** | Security: password hashing, SQL injection, file uploads, rate limits. | Test bad form data and unauthorized requests. | No direct string-concatenated SQL or plaintext passwords. |
| **52** | Performance: telemetry and DB query inspection. | Fix one deliberate N+1 query or slow render. | Baseline and comparison recorded. |
| **53** | Releases, `mix release`, environment config and hosting basics. | Produce release candidate and deployment README. | Launch outside the editor with required config. |
| **54** | **Checkpoint 2:** production candidate. | Task board with login boundary, background work and live updates. | CI green, 30+ tests, `elixir-p3` tag. |

## Part 4 — Capstone and deployment

### Week 10 — Capstone: a fault-tolerant Phoenix app (sessions 55–60)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **55** | Scope and acceptance criteria. | Sketch a team task board or mini booking system and schema. | Five user stories with errors and access rules. |
| **56** | Build domain and database with tests. | Implement contexts, migrations and validation. | Isolated test database produces green tests. |
| **57** | Build Phoenix interface and LiveView updates. | Implement lists, filters and edit workflow. | Two clients stay in sync after an update. |
| **58** | Integrate a supervised background task and observability. | Add reminder job with crash/restart test. | Failure does not terminate the website. |
| **59** | Polish security, accessibility, performance and docs. | Add invalid-input tests, README, seed data and release notes. | New tester can navigate the app and understand failures. |
| **60** | **Final review and release:** test, demo, publish. | Record demo, run CI and deploy or package a release, tag `elixir-v1`. | Fresh clone setup succeeds; real-time and recovery features demonstrated. |

---

## Checkpoints — do not move forward with gaps

| Gate | Session | Pass condition | If you miss it |
|---|---:|---|---|
| Checkpoint 0 | 18 | Elixir CLI project with modules, structs and 15 ExUnit tests. | Repeat weeks 2–3 and redo the CLI. |
| Checkpoint 1 | 30 | A supervised GenServer/Task application recovers from a controlled failure. | Redo message passing and supervision exercises. |
| Checkpoint 2 | 54 | Phoenix task board with Ecto, login boundary, live updates, background work, 30+ tests. | Work a focused extra week on weakest component. |
| Capstone | 60 | Clean clone, repeatable migrations, README, release/demo and `elixir-v1` tag. | Fix onboarding, tests or recovery before shipping. |

## Final capstone specification

Build an **OTP-supervised Phoenix task board** with user-owned tasks, validation, database migrations, **Phoenix LiveView** updates across connected clients and a supervised asynchronous reminder/notification worker. Use Ecto changesets for untrusted inputs and make failure handling deliberate: a crashed worker should not bring down the web app. Keep email/SMS delivery mocked unless you intentionally add and secure an external provider.

**Minimum acceptance test:** start clean → migrate DB → run test suite → sign in as User A → add and edit task → second session sees update → User B cannot edit A's task → trigger a controlled background-worker failure and show supervision recovery. Document required environment variables and release steps. Hosting a public instance is optional if paid infrastructure is required; a reproducible release and demo are mandatory.

**Optional after day 60:** Nerves for embedded Elixir (requires suitable board/toolchain), distributed Erlang, Oban job processing or deeper LiveView state management. These are not assumed to work on all desktop operating systems without extra tooling.

## Resources (prefer the current matching versions)

| Resource | Use it for | Cost |
|---|---|---|
| [Elixir installation](https://elixir-lang.org/install.html) | Compatible Elixir and Erlang/OTP installs on each OS. | Free |
| [Elixir getting started](https://elixir-lang.org/getting-started/introduction.html) | Functions, pattern matching, modules and syntax. | Free |
| [Elixir HexDocs](https://hexdocs.pm/elixir/) | Standard library, processes and Mix. | Free |
| [ExUnit documentation](https://hexdocs.pm/ex_unit/ExUnit.html) | Testing techniques. | Free |
| [Ecto](https://hexdocs.pm/ecto/Ecto.html) | Schemas, changesets and data access. | Free |
| [Phoenix guides](https://hexdocs.pm/phoenix/overview.html) | Routing, authentication and web app structure. | Free |
| [Phoenix LiveView](https://hexdocs.pm/phoenix_live_view/) | Stateful real-time pages. | Free |
| [Erlang/OTP design principles](https://www.erlang.org/doc/system/design_principles.html) | Supervision and fault-tolerance mental model. | Free |

**Compatibility:** choose the Elixir/OTP pair from the official installer, then use matching Phoenix/Ecto guide versions; third-party blog posts often show earlier APIs.

## What you can do next

You can create Elixir applications with reliable error results, supervised processes, Ecto data models, tested web requests and LiveView interfaces. For higher-scale work, learn deployment/release operations, distributed node trade-offs, telemetry, queueing and database tuning. Practise by writing a small `GenServer` library without Phoenix, then reusing it in a Phoenix app.

