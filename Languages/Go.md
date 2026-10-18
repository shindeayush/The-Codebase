# Go Roadmap: From Zero to Fast Servers and Cloud Tools

This roadmap takes you from your first variable to a deployed, concurrent Go server in 42 sessions (7 weeks, about 130 hours). It assumes you have never programmed. Go was made at Google for fast, simple servers and cloud tools; Docker and Kubernetes are written in it. It has a small language, one obvious way to do most things, and very quick builds, so it is a pleasant first language. It stands alone and starts from zero. By the end you can build a REST API with a real database, logins and tests, plus command-line tools, and ship them as a single small binary.

## Start here

**How Go works.** You write `.go` files and `go build` compiles them straight to one executable for your operating system, with no runtime to install. `go run` compiles and runs in one step.

**Setup (30 minutes, once):**

1. Install **Go** (the latest stable release) from go.dev/dl. Check `go version`.
2. Install **VS Code** with the official **Go** extension (it installs `gopls` and the debugger), or use GoLand if you have it.
3. Make a folder `go-roadmap`, run `go mod init example.com/roadmap` inside it, and make one folder per day. Run `git init` and commit at the end of every session.
4. Learn the Go habits early: `gofmt` formats your code (the editor does it on save), and `go vet` finds suspicious code.
5. The free [Go Playground](https://go.dev/play/) runs code in the browser.

**How one session works (about 3 hours):**

| Minutes | Step | What you do |
| --- | --- | --- |
| 10 | Start | Re-type from memory one snippet from last session. |
| 40 | Learn | Read the listed source, typing every example. |
| 90 | Build | Write the day's program without copying. |
| 30 | Break it | Cause compile errors and panics on purpose and read each message. |
| 10 | Save | `git commit` and write 3 journal lines. |

The 6th session each week is a 4-hour project and review. A session is done only when `go vet ./...` is clean, the program runs, it is committed, and you can explain it line by line.

## Part 1 (weeks 1-2, days 1-12): the language

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 1 | What programming is. `package main`, `func main`, `fmt.Println`, `go run`, `go build`, modules. | Hello World, then a program printing your name, age and a joke. | You can build a binary and run it. |
| 2 | Variables: `var`, `:=`, basic types (`int`, `float64`, `string`, `bool`), zero values, constants, `fmt.Printf` verbs, reading input with `bufio`. | A tip calculator and a temperature converter. | Unused variables are a compile error, and you know why. |
| 3 | Operators, `if`/`else`, `switch` (no fall-through), `if` with an init statement. | A grade calculator and a leap-year checker. | Edge cases (0, negatives) behave as planned. |
| 4 | Loops: `for` is the only loop (classic, while-style, infinite), `range`, `break`, `continue`. | FizzBuzz, a multiplication table, a number-guessing game. | You can trace a loop on paper. |
| 5 | Functions: parameters, multiple return values, named returns, variadic functions, `defer`, functions as values. | Reusable `isPrime`, `divide` (returns a result and an error), `sum(...)`. | No logic is repeated in `main`. |
| 6 | **Project and review.** | A menu-driven CLI calculator or quiz. | Bad input does not crash it. Committed. |
| 7 | Arrays and **slices**: `append`, `len`, `cap`, slicing, `copy`, the idea of the backing array, 2D slices. | Remove an item from a slice, and a tic-tac-toe board. | You can explain why two slices can change the same data. |
| 8 | Maps, strings, bytes and runes, the `strings` and `strconv` packages. | A word-frequency counter. | Works with accented letters. |
| 9 | Structs, methods, **pointers**: value vs pointer receivers, `&` and `*`. | A `Student` struct with methods. | You can explain when a method changes the original. |
| 10 | Composition: struct embedding instead of inheritance, constructor functions (`NewStudent`), exported and unexported names. | A `Shape` set built from embedded structs. | Capitalised names are public, and you can say why. |
| 11 | **Errors are values:** `error`, `errors.New`, `fmt.Errorf` with `%w`, `errors.Is` and `errors.As`, `panic` and `recover` (and when not to use them). | Make day 6's program return proper errors. | No panics on bad input. |
| 12 | **Checkpoint 0 and project.** | A console bank or inventory system with structs, methods, a map and errors. | About 200 lines, `go vet` clean, no copying, tag `go-p1`. |

**Break it (daily):** index past the end of a slice, write to a nil map, ignore an error and watch what breaks later, shadow a variable by mistake.

## Part 2 (weeks 3-4, days 13-24): interfaces, testing and concurrency

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 13 | **Interfaces:** implicit satisfaction, small interfaces, `io.Reader` and `io.Writer`, `any`, type assertions, type switches. | A `Notifier` interface with email and SMS fakes. | You can say why Go interfaces need no `implements`. |
| 14 | Generics: type parameters, constraints, `comparable`, generic functions and types. | A generic `Map`, `Filter` and `Stack[T]`. | One function works for ints and strings, with no casts. |
| 15 | Packages and modules: project layout, exported names, `go.mod`, `go get`, `internal/`, splitting code into packages. | Split your day 12 project into 3 packages. | No package imports itself in a cycle. |
| 16 | **Testing:** `go test`, table-driven tests, subtests, benchmarks, coverage (`go test -cover`). | 15 tests for your day 12 project. | `go test ./...` passes, and one broken test fails. |
| 17 | Files and JSON: `os`, `bufio`, `encoding/json`, struct tags, `flag` package. | Save and load your bank data as JSON. | Data survives a restart. |
| 18 | **Project and review.** | A log analyser CLI with flags and tests. | Handles a 100 MB file without using much memory. |
| 19 | **Goroutines:** `go` keyword, `sync.WaitGroup`, how the scheduler works in plain words. | Fetch 5 slow tasks in parallel. | It takes the time of one task, not five. |
| 20 | **Channels:** buffered and unbuffered, `select`, closing, worker-pool pattern. | A worker pool that processes 100 jobs. | No goroutine is left waiting forever. |
| 21 | Shared state: `sync.Mutex`, `sync/atomic`, `sync.Once`, the **race detector** (`go test -race`), `errgroup`. | A counter updated by 100 goroutines. | The race detector reports nothing. |
| 22 | **`context`:** cancellation, timeouts and deadlines, passing `ctx` as the first argument. | Add timeouts to your parallel fetch. | A slow task is cancelled on time. |
| 23 | Patterns: pipelines, fan-out and fan-in, rate limiting with a ticker, graceful shutdown. | A 3-stage pipeline that reads, transforms and writes. | Ctrl+C stops it cleanly. |
| 24 | **Checkpoint 1 and project.** | A concurrent website-link checker CLI with a worker pool, timeouts and tests, in 4 hours. | Tests pass and `-race` is clean. Tag `go-p2`. |

**Break it (daily):** read and write a map from two goroutines, send on a closed channel, forget to close a channel, leak a goroutine, and watch what Go reports.

## Part 3 (weeks 5-6, days 25-36): web servers, databases and tools

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 25 | HTTP and `net/http`: handlers, `http.ServeMux` with method and path patterns, JSON responses, status codes. | A `/hello/{name}` and `/items` API. | Each route returns the right status code. |
| 26 | REST design: resources, nouns, CRUD, request validation, consistent JSON error bodies. | Design the routes for a notes API on paper, then build `GET` and `POST`. | Bad input returns 400 with a clear message. |
| 27 | Middleware: logging, panic recovery, request IDs, CORS, timeouts, graceful shutdown with `http.Server.Shutdown`. | A middleware chain around your API. | A panic in a handler does not kill the server. |
| 28 | **Project and review.** | A notes API (create, read, update, delete) with in-memory storage and tests with `httptest`. | At least 12 requests tested. |
| 29 | SQL: tables, keys, queries (`SELECT`, `INSERT`, `UPDATE`, `DELETE`, `JOIN`). `database/sql` with **PostgreSQL** (or SQLite), prepared statements, transactions. | Notes stored in a database. | Data survives a restart. |
| 30 | Migrations (**goose** or **golang-migrate**), connection pooling, the repository pattern. Optional: **sqlc** or **pgx**. | A repository package with its own tests. | The schema is versioned in Git. |
| 31 | **Project and review.** | A notes API with users, tags and pagination. | Documented endpoints, committed. |
| 32 | Auth: password hashing (**bcrypt** or **argon2**), sessions or **JWT**, protecting routes, user-owned data. | Sign up, log in and a protected route. | User A cannot read user B's notes. |
| 33 | Configuration and operations: environment variables, structured logs with `log/slog`, an HTTP client with timeouts, retries. | Move all settings to environment variables. | No secret is in Git. |
| 34 | Command-line tools: **cobra** (or `flag`), exit codes, cross-compiling (`GOOS`/`GOARCH`), embedding files. | A `notes` CLI that talks to your API. | You built binaries for Windows, Linux and macOS. |
| 35 | Testing in depth: `httptest`, fakes through interfaces, golden files, integration tests with **Testcontainers** (intro), fuzzing (a first look). | 20 tests across your API. | Tests pass, and you can run only the fast ones. |
| 36 | **Checkpoint 2 and project.** | A multi-user task API with logins, permissions and tests in 5 hours. | Tests pass with `-race`. Tag `go-p3`. |

**Break it (daily):** send malformed JSON, a huge body, and a request with a cancelled context; try SQL injection on a deliberately unsafe method (your own code, your own machine) and then fix it.

## Part 4 (week 7, days 37-42): ship it

Build one service of your own choice end to end. Good choices: a URL shortener with stats, a habit tracker API, a link-checker service, a chat server with WebSockets, or a small job queue.

| Day | Do | Done when |
| --- | --- | --- |
| 37 | Plan: write 8 user stories, list endpoints and tables, draw the database on paper. Set up the module, migrations and a README skeleton. | The plan and an empty project that builds are committed. |
| 38 | Build the data layer and core endpoints with validation and error handling. | Core routes work in `curl`. |
| 39 | Add logins, permissions, middleware and tests for every endpoint. | Another user cannot touch your data. |
| 40 | **Docker:** a multi-stage `Dockerfile` that produces a small image (distroless or `scratch`), `docker-compose.yml` for the app and PostgreSQL, a health-check route. | `docker compose up` runs the whole thing from a fresh clone. |
| 41 | CI and deploy: a **GitHub Actions** workflow running `go vet`, `go test -race` and a build, then deploy to a free host with a Docker option. | A public URL and a green CI badge. |
| 42 | **Review.** Ask a friend to try it with `curl` for 15 minutes and fix the top 3 problems. Finish the README with endpoints and a `curl` example. Tag `go-v1`. | A stranger can use your live API from the README alone. |

## Checkpoints and what comes next

Do not move on until you pass each gate. If you fail, redo the weak days, not the whole part.

- **Checkpoint 0 (day 12).** In 3 hours, with no notes, write a program with a struct, methods, a map, a slice and proper error handling. Pass: `go vet` is clean and it runs after at most 3 fixes.
- **Checkpoint 1 (day 24).** Explain, out loud, a slice vs an array, an interface, a goroutine, a channel and what `context` is for. Then build a small concurrent program with tests. Pass: you do both without searching, and `-race` is clean.
- **Checkpoint 2 (day 36).** Build a REST API with 4 routes, a database, middleware and 10 tests in 4 hours. Pass: tests pass, and you can explain a graceful shutdown.
- **Capstone (day 42).** Passes when a stranger can use your live link and CI is green.

**What you can do now.** Build and ship Go back ends, CLI tools and concurrent programs, and read most cloud-tool code. Not covered yet: gRPC and microservices, Kubernetes basics, and system design for large scale. I can add roadmaps for those.

## Resources

I have not opened these links this session, so check each before relying on it.

| Resource | Use it for | Cost |
| --- | --- | --- |
| [A Tour of Go](https://go.dev/tour/) | The official interactive intro; do it alongside part 1. | Free |
| [Go by Example](https://gobyexample.com/) | Short annotated programs for every feature. | Free |
| [Effective Go](https://go.dev/doc/effective_go) | How to write idiomatic Go. | Free |
| [Go standard library docs](https://pkg.go.dev/std) | The reference for every built-in package. | Free |
| [Learn Go with Tests](https://quii.gitbook.io/learn-go-with-tests) | Learning Go through test-driven development. | Free |
| [Let's Go (Alex Edwards)](https://lets-go.alexedwards.net/) | A web-application book for part 3 (paid). | Paid |
| [Go Concurrency Patterns talk (Rob Pike)](https://go.dev/blog/pipelines) | Days 19-23. | Free |
| [Exercism Go track](https://exercism.org/tracks/go) | Extra practice with feedback. | Free |
