# Rust Roadmap: From Zero to Safe, Fast Systems Code

This roadmap takes you from your first variable to shipping fast, safe Rust programs in 66 sessions (11 weeks, about 210 hours). It assumes you have never programmed, and it starts at the basics. Be warned: Rust has the steepest learning curve of the languages here, because its compiler makes you prove your code is memory-safe before it will run. That is also why Rust programs are fast and rarely crash. Expect to fight the compiler in weeks 2-4 and then feel the payoff. It stands alone. By the end you can build command-line tools, web back ends and concurrent programs, and read systems code.

## Start here

**How Rust works.** You write `.rs` files and the compiler turns them into a fast native program, with no garbage collector. **Cargo** is the build tool and package manager: `cargo new`, `cargo run`, `cargo test`.

**Setup (30 minutes, once):**

1. Install **Rust** with `rustup` from rust-lang.org/tools/install. Check `rustc --version` and `cargo --version`. On Windows you may be asked to install C++ build tools; do it, or use WSL2.
2. Install **VS Code** with the **rust-analyzer** extension.
3. Run `cargo new hello` and `cd hello && cargo run`. If it prints "Hello, world!", you are set up.
4. Make a folder `rust-roadmap` with one Cargo project per day. Run `git init` and commit at the end of every session.
5. Turn on `cargo clippy` (a linter) and `cargo fmt` (a formatter) from day 1.

**How to survive the compiler.** Rust error messages are among the best of any language, but they are long. Read from the top, read the `help:` lines, and fix one error at a time. Do **Rustlings** (small broken programs you fix) alongside the daily plan, from day 7.

**How one session works (about 3 hours):**

| Minutes | Step | What you do |
| --- | --- | --- |
| 10 | Start | Re-type from memory one snippet from last session. |
| 40 | Learn | Read the listed source, typing every example. |
| 90 | Build | Write the day's program without copying. |
| 30 | Break it | Cause compile errors on purpose and read each message fully. |
| 10 | Save | `git commit` and write 3 journal lines. |

The 6th session each week is a 4-hour project and review. A session is done only when `cargo clippy` has no warnings you do not understand, the program runs, it is committed, and you can explain it line by line.

## Part 1 (weeks 1-3, days 1-18): the basics and ownership

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 1 | What programming is. `fn main`, `println!`, `cargo new`, `cargo run`, `cargo build`, comments. | Hello World, then your name, age and a joke. | You can say what `cargo` does that `rustc` alone does not. |
| 2 | Variables: `let`, `mut`, shadowing, constants. Types: integers (`i32`, `u8`), floats, `bool`, `char`. | A tip calculator and a temperature converter. | You can explain why variables are immutable by default. |
| 3 | Operators, `if`/`else`, `loop`, `while`, `for` with ranges, `break` with a value. | FizzBuzz and a multiplication table. | You can trace a loop on paper. |
| 4 | Functions: parameters, return values, expressions vs statements, the unit type `()`. | Reusable `is_prime`, `factorial`, `max`. | No logic is repeated in `main`. |
| 5 | Tuples, arrays, a first look at `String` vs `&str`, formatting with `{}` and `{:?}`. | A string-report printer. | You can say what each string type is for. |
| 6 | **Project and review.** Reading input with `std::io::stdin`, adding a crate (`rand`). | A number-guessing game. | Bad input does not crash it. Committed. |
| 7 | **Ownership 1:** stack and heap, moves, `Clone` and `Copy`. Start **Rustlings** (exercises on variables, functions, `if`). | Rustlings: finish the first 20 exercises. | You can say what happens to a `String` when it is moved. |
| 8 | **Ownership 2:** references and borrowing, `&` and `&mut`, the rule "one writer or many readers". | Write functions that borrow, not take, a value. | You can predict compile errors before running. |
| 9 | **Ownership 3:** slices, dangling references, reading borrow-checker errors. Rustlings: move semantics and borrowing. | Fix 10 deliberately broken programs. | You can fix each without guessing. |
| 10 | Structs, `impl` blocks, methods, associated functions (`new`), tuple structs. | A `Student` struct with methods. | `&self` and `&mut self` are used correctly. |
| 11 | Enums, `Option<T>`, `Result<T, E>`, `match`, `if let`, `let else`. | A `Shape` enum with an `area` function. | There are no `null`s, and you can say why. |
| 12 | **Project and review.** | A console bank or inventory system using structs, enums and `Option`. | About 150 lines, `clippy` clean. |
| 13 | `Vec`, `HashMap`, `HashSet`, iterating, `String` building. | A word-frequency counter. | You can say when to use `Vec` vs `HashMap`. |
| 14 | Error handling: `Result`, the `?` operator, custom error enums, `panic!` vs recoverable errors, why to avoid `unwrap` in real code. | Make the bank system return proper errors. | No `unwrap` on user input. |
| 15 | Modules and packages: `mod`, `use`, `pub`, splitting code into files, crates, `Cargo.toml`. | Split day 12's project into 3 files. | Private by default, and you can say why. |
| 16 | Pattern matching in depth: destructuring, match guards, `while let`, ranges, bindings. | Write a tiny command interpreter with `match`. | The compiler tells you if you miss a case. |
| 17 | Files and the environment: `std::fs`, `std::env::args`, `BufRead`, reading a file line by line. | A line counter that takes a file name argument. | It handles a missing file with a clear message. |
| 18 | **Checkpoint 0 and project.** | A command-line to-do app saving to a file. | About 200 lines, no copying, `clippy` clean, tag `rust-p1`. |

**Break it (daily):** use a value after moving it, borrow mutably twice, return a reference to a local variable, forget a `match` arm, then read every line of each error.

## Part 2 (weeks 4-6, days 19-36): traits, lifetimes and idiomatic Rust

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 19 | Generics: generic functions, structs and enums. | Your own generic `Stack<T>` and `Pair<A, B>`. | One type works for any element, with no casts. |
| 20 | **Traits 1:** defining traits, implementing them, default methods, the orphan rule. | A `Shape` trait with `Circle` and `Rectangle`. | You can say how a trait differs from an interface in Java. |
| 21 | Traits 2: trait bounds, `impl Trait`, `dyn Trait` (trait objects), `#[derive(Debug, Clone, PartialEq)]`, the standard traits (`Display`, `From`, `Default`). | A plugin-style list of `Box<dyn Shape>`. | You can say when to use generics and when `dyn`. |
| 22 | **Lifetimes 1:** why they exist, annotations in functions (`'a`), the longest-string example. | Write 5 functions that return references. | You can explain what a lifetime annotation promises. |
| 23 | Lifetimes 2: in structs, elision rules, `'static`. | A struct that holds a `&str` slice of a larger text. | You can fix lifetime errors by reasoning, not guessing. |
| 24 | **Project and review.** | A mini `grep`: search a file for a word with case options. | Uses a `struct`, `Result`, lifetimes and tests. |
| 25 | Closures: capturing, `Fn`, `FnMut`, `FnOnce`, `move`. | A `retry(n, f)` helper. | You can say which closure trait fits a case. |
| 26 | Iterators: `iter`, `map`, `filter`, `fold`, `collect`, `zip`, `enumerate`, writing your own `Iterator`. | Statistics on 100 records with iterators only. | No index loops where an iterator fits. |
| 27 | More collections: `VecDeque`, `BTreeMap`, `BinaryHeap`, sorting, `binary_search`, entry API. | A task scheduler on a `BinaryHeap`. | You can say the cost of each operation. |
| 28 | **Smart pointers:** `Box`, `Rc`, `RefCell`, `Weak`, interior mutability. | A tree with parent links. | You can say when you need `Rc<RefCell<T>>`, and when you do not. |
| 29 | **Project and review.** Recursive data. | A linked list and a binary search tree. | Insert, search and delete are tested. |
| 30 | **Project and review.** Parsing. | An arithmetic expression parser and evaluator using enums. | `3 + 4 * (2 - 1)` evaluates correctly. |
| 31 | Errors in real projects: `thiserror`, `anyhow`, `Option` combinators (`map`, `and_then`, `ok_or`). | Refactor the parser's errors. | Errors tell the user what went wrong and where. |
| 32 | Data formats: **serde**, JSON and TOML, logging with **tracing**. | A config-file loader and a JSON exporter. | Round trip: save, load, compare. |
| 33 | Testing: unit tests, integration tests, doc tests, `cargo test`, test organisation; a first look at property testing. | 20 tests across your projects. | `cargo test` passes, and one broken test fails. |
| 34 | Tooling: `clippy`, `rustfmt`, `cargo doc`, `cargo audit`, benchmarks with **criterion** (intro). | Run all four on your parser and fix the warnings. | `cargo clippy -- -D warnings` passes. |
| 35 | Macros: using derive macros, writing a small `macro_rules!`, the difference between macros and functions. | A `hashmap!` macro. | You can say why `println!` is a macro. |
| 36 | **Checkpoint 1 and project.** | A key-value store with an in-memory map and a file log, with tests, in 5 hours. | Tests pass, `clippy` clean. Tag `rust-p2`. |

**Break it (daily):** drop a lifetime annotation, hold a `RefCell` borrow twice and watch it panic, return a trait object by value, implement a trait twice.

## Part 3 (weeks 7-9, days 37-54): concurrency, async and web back ends

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 37 | Threads: `thread::spawn`, `join`, `move` closures, why Rust stops data races at compile time. | 4 threads that each sum a slice. | The total is correct. |
| 38 | Message passing: `mpsc` channels, producers and consumers. | A worker pool that processes 100 jobs. | No worker is left waiting forever. |
| 39 | Shared state: `Arc`, `Mutex`, `RwLock`, atomics, the `Send` and `Sync` traits. | A counter updated by 100 threads. | You can say why `Rc` will not compile across threads. |
| 40 | **Project and review.** **Rayon** for easy parallelism. | A parallel file hasher or word counter. | It is measurably faster on many files. |
| 41 | Async: futures, `async`/`await`, the **Tokio** runtime, `#[tokio::main]`. | 3 timers running at once. | You can say the difference between a thread and a task. |
| 42 | Async tasks: `tokio::spawn`, `select!`, timeouts, async channels, cancellation. | A task that times out a slow job. | The timeout really cancels the work. |
| 43 | **Project and review.** HTTP client with **reqwest**. | An async website link checker. | Checks 50 URLs at once with a limit. |
| 44 | Web servers with **Axum**: routing, handlers, extractors, JSON with serde. | A `/hello/{name}` and `/items` API. | Each route returns the right status code. |
| 45 | Axum in depth: shared state, middleware with **tower**, error handling with `IntoResponse`, validation. | A notes API in memory. | Bad input returns 400 with a clear message. |
| 46 | SQL (tables, keys, `JOIN`), **sqlx** with PostgreSQL or SQLite, migrations, connection pools. | Store the notes in a database. | Data survives a restart. |
| 47 | **Project and review.** | A notes API with users, tags and pagination. | Documented endpoints, committed. |
| 48 | Auth: password hashing (**argon2**), sessions or **JWT**, protecting routes, user-owned data. | Sign up, log in and a protected route. | User A cannot read user B's notes. |
| 49 | Testing the API: unit and integration tests, `tower::ServiceExt` to call the app without a network. | 15 API tests. | Tests pass against a clean database each time. |
| 50 | Operations: configuration, structured logs with `tracing`, graceful shutdown, health checks. | Settings from environment variables. | No secret is in Git. |
| 51 | Packaging: a multi-stage **Docker** build with a small final image, `cargo` caching, **GitHub Actions** running `fmt`, `clippy` and `test`. | `docker compose up` for app and database. | CI is green on every push. |
| 52 | Performance: `--release` builds, **flamegraph** profiling, criterion benchmarks, avoiding needless allocation and cloning. | Profile one slow function and speed it up. | A benchmark shows the improvement. |
| 53 | Rate limiting and caching: a token-bucket limiter, an in-memory cache with expiry. | Add both to your API. | Over-limit requests get 429. |
| 54 | **Checkpoint 2 and project.** | A multi-user task API with logins and tests, in 5 hours. | Tests pass, `clippy` clean. Tag `rust-p3`. |

**Break it (daily):** lock a mutex twice, hold a lock across an `.await`, send non-`Send` data to a thread, panic inside a task, flood your server.

## Part 4 (weeks 10-11, days 55-66): tools, systems topics and a capstone

| Day | Learn or do | Done when |
| --- | --- | --- |
| 55 | Command-line tools with **clap**: subcommands, flags, colours, exit codes, shell completions. | A `notes` CLI with 4 subcommands. |
| 56 | Workspaces, Cargo features, documentation comments, versioning, how publishing to crates.io works (practise with a dry run). | `cargo doc --open` shows clean docs for your library crate. |
| 57 | **Unsafe Rust:** what `unsafe` allows, raw pointers, the rules you must uphold, why safe wrappers matter. | You wrote one tiny safe wrapper around unsafe code and tested it. |
| 58 | FFI: calling a C function from Rust, exposing a Rust function to C, `bindgen` and `cbindgen` (introduction). | A Rust program calls `libc` or a small C library you wrote. |
| 59 | Memory and bytes: struct layout, `std::mem`, bit operations, parsing a binary file format (for example a BMP header) with safe code. | A tool that prints the header of a BMP or PNG file. |
| 60 | Optional: **WebAssembly** with `wasm-pack`, running a Rust function in a web page. | A Rust function called from JavaScript in the browser. |
| 61 | **Capstone plan:** pick one (see below), write 8 user stories, sketch the architecture, set up the repo, CI and README skeleton. | A plan and a project that builds, committed. |
| 62 | Capstone: build the core with tests first. | Core logic passes its tests. |
| 63 | Capstone: add features, error handling and logging. | Every user story works by hand. |
| 64 | Capstone: documentation, benchmarks, `clippy` clean, a `--release` build, tests for the edge cases. | `cargo clippy -- -D warnings` and `cargo test` pass. |
| 65 | Release: build binaries for your platform (and cross-build if you can), a GitHub release, an install guide, a Docker image if it is a service. | A stranger can install and run it from the README. |
| 66 | **Review.** Ask a friend or a forum to review the code and try the tool. Fix the top 3 problems. Tag `rust-v1`. | The review notes are addressed. |

**Capstone ideas (choose one):** a fast file search or duplicate-finder CLI, a Markdown-to-HTML converter, a chat server with Tokio, a key-value database with a write-ahead log, a small HTTP load tester, or a text-based game engine.

**Break it (daily):** run your tool on a huge input, a broken file and a missing file; run it under a profiler; send random bytes to your parser.

## Checkpoints and what comes next

Do not move on until you pass each gate. If you fail, redo the weak days, not the whole part. Failing the ownership gate once is normal in Rust.

- **Checkpoint 0 (day 18).** In 3 hours, with no notes, write a program with a struct, an enum, `Option`, `Result` and a `Vec`, and explain out loud why each borrow-checker error you hit was an error. Pass: `clippy` clean and it runs after at most 5 fixes.
- **Checkpoint 1 (day 36).** Explain, out loud, a trait, a trait object vs a generic, a lifetime and `Rc<RefCell<T>>`. Then build a small tested library crate. Pass: you do both without searching.
- **Checkpoint 2 (day 54).** Build a REST API with a database, async handlers and 10 tests in 4 hours. Pass: tests pass, and you can say why holding a lock across `.await` is a problem.
- **Capstone (day 66).** Passes when a stranger can install it from your README and CI is green.

**What you can do now.** Build fast command-line tools, web back ends and concurrent programs in Rust, and read most Rust code. Rust jobs are fewer than Java, Python or JavaScript jobs, but they are growing in systems, infrastructure, blockchain and security tooling. Not covered yet: embedded Rust, game development with Bevy, and deeper async internals. I can add roadmaps for those.

## Resources

I have not opened these links this session, so check each before relying on it.

| Resource | Use it for | Cost |
| --- | --- | --- |
| [The Rust Programming Language ("the Book")](https://doc.rust-lang.org/book/) | The official, free, full-length text. Read it alongside the plan. | Free |
| [Rustlings](https://github.com/rust-lang/rustlings) | Small exercises that teach ownership and the compiler. | Free |
| [Rust by Example](https://doc.rust-lang.org/rust-by-example/) | Short runnable examples of every feature. | Free |
| [Comprehensive Rust (Google)](https://google.github.io/comprehensive-rust/) | A fast course with exercises. | Free |
| [Rust standard library docs](https://doc.rust-lang.org/std/) | The reference. | Free |
| [Tokio tutorial](https://tokio.rs/tokio/tutorial) | Days 41-43. | Free |
| [Axum docs](https://docs.rs/axum/latest/axum/) | Days 44-50. | Free |
| [The Cargo Book](https://doc.rust-lang.org/cargo/) | Days 15, 34, 56. | Free |
| [Exercism Rust track](https://exercism.org/tracks/rust) | Extra practice with feedback. | Free |
