# Swift Roadmap: From Zero to Apps, Automation and Safe Concurrent Systems — macOS, Windows and Linux

*72 sessions (choose one final track) | 12 weeks | approximately 228 hours | Swift 6.x, Swift Package Manager and Swift Testing*

Learn **Swift from no programming experience**, then ship a complete project. Like the Java, Go, C++, R, Ruby, Dart and Assembly guides, this roadmap has a repeatable daily routine, a **Learn → Build → Done when** table for every session, deliberate debugging, weekly projects, checkpoints and a capstone that a second person can run. A “day” means a **study session**, not necessarily a calendar day.

**The platform promise is precise:**

- **Windows 10/11:** write, compile, debug and test native Swift command-line applications and compatible Swift packages using the official Windows toolchain. This is real Windows development, **not WSL**.
- **Linux:** write and run Swift CLI apps, libraries and supported server programs using the native Linux toolchain.
- **macOS:** do all shared Swift exercises, plus **SwiftUI and Xcode** for apps targeting iPhone, iPad and Mac.
- **What is not cross-platform:** Apple **SwiftUI/UIKit/AppKit** are Apple-platform frameworks. A Windows or Linux Swift compiler does *not* by itself build iOS apps. Use the **Track B** capstone if you don't have a Mac; use **Track A** if you want Apple apps and have macOS + Xcode.

The core **days 1–48** are deliberately platform-neutral. For **days 49–72**, choose **one** capstone track:

| Path | Requirements | End result |
|---|---|---|
| **Track A — SwiftUI app development** | macOS with Xcode; iOS Simulator or Mac app target | A usable iOS/macOS personal-planner app with local storage, a network feature, accessibility and tests. |
| **Track B — cross-platform Swift tooling** | Windows, Linux or macOS with Swift toolchain | A polished native CLI data-management/automation tool with subcommands, imports, exports, tests, concurrency and packaging. |

If you want both, finish one track and complete the other as an additional four-week sequence. An **optional server-side Swift extension** is included at the end, with its own platform cautions.

## How one session works

Sessions 1–5 of each week take about **3 hours**; session 6 takes **4 hours** for project work and review. Total: 12 × (5 × 3 + 4) = **228 hours** for a single full path.

| Minutes | Block | What you do |
|---:|---|---|
| 10 | Recall | Re-create one snippet from memory and say what it does. |
| 40 | Learn | Read only today's topics; type the examples yourself. |
| 90 | Build | Build the exercise independently. Predict outputs before running. |
| 30 | Break it | Introduce a bug, read diagnostics, reproduce it in a test or debugger and fix it. |
| 10 | Save | Run tests, commit in Git and write 3 journal lines: learned / confused / next first step. |

**Done for a normal session:** code compiles, the happy path and important edge cases run, you understand all diagnostics, any relevant tests pass, the work is committed, and you can explain the program line by line. After week 4, `swift test` passing is a standard gate. Be patient with version-specific Swift compiler warnings; understand and resolve the warning rather than suppressing it blindly.

**Time rule:** if you get stuck for 20 minutes, write your expectation and actual result, make a minimal reproduction, then consult documentation or ask a targeted question. Do not skip an exercise because the next day's topic looks more interesting.

## Start here: choose your operating system

Read only your primary platform's setup subsection. Use a **current stable Swift 6.x toolchain**, not a development snapshot, unless a specific lesson calls for an experimental feature. Swift.org installation pages are the source of truth because packages and system requirements can change.

### Path W — Windows native Swift (not WSL)

1. Open the official instructions: <https://www.swift.org/install/windows/>. Windows Swift requires the appropriate **Visual Studio C++ build tools and Windows SDK**, in addition to the Swift toolchain. Follow the installation page for your Windows version and architecture. The official current WinGet route is:

   ```powershell
   winget install --id Microsoft.VisualStudio.2022.Community --exact --force --custom "--add Microsoft.VisualStudio.Component.Windows11SDK.22621 --add Microsoft.VisualStudio.Component.VC.Tools.x86.x64 --add Microsoft.VisualStudio.Component.VC.Tools.ARM64" --source winget
   winget install --id Swift.Toolchain -e --source winget
   ```

   These may require administrator privileges and significant disk space. If the Swift.org page has changed since this guide was written, use its updated commands instead.
2. Install **VS Code** and the **Swift extension**; install **Git**. Start from a fresh terminal after setup, with the required compiler tools discoverable.
3. Verify `swift --version`, `swift package --help` and `git --version`. If a linker error occurs, check Visual Studio build tools and SDK first, before changing your Swift code.
4. Create and run a *native* Windows executable package:

   ```powershell
   mkdir SwiftRoadmap
   cd SwiftRoadmap
   mkdir HelloSwift
   cd HelloSwift
   swift package init --name HelloSwift --type executable
   swift run HelloSwift
   swift build -c release
   ```

   Swift produces a native Windows executable (`.exe`) for this host platform. Use PowerShell or the recommended Visual Studio developer shell for your installed setup.

**Windows specifics to learn later:** `\\` path escaping, drive letters, case-insensitive file paths, UTF-8, PowerShell quoting, `.exe` distribution and Windows-specific permissions. Avoid examples that assume Unix-only tools such as `chmod`, `grep` or `fork`.

### Path L — native Linux Swift

1. Open <https://www.swift.org/install/linux/> and select your distribution/version. Swiftly is the recommended toolchain manager. For a supported Bash-based Linux setup, its published installer flow is:

   ```bash
   curl -O "https://download.swift.org/swiftly/linux/swiftly-$(uname -m).tar.gz"
   tar zxf "swiftly-$(uname -m).tar.gz"
   ./swiftly init --quiet-shell-followup
   . "${SWIFTLY_HOME_DIR:-$HOME/.local/share/swiftly}/env.sh"
   hash -r
   ```

   Swiftly may tell you to install system dependencies. Use the current Swift.org page for those details.
2. Install **VS Code with Swift extension** (optional), Git, and the debugger provided with your Swift toolchain. Verify `swift --version` and `git --version`.
3. Create an executable Swift package:

   ```bash
   mkdir -p swift-roadmap/HelloSwift
   cd swift-roadmap/HelloSwift
   swift package init --name HelloSwift --type executable
   swift run HelloSwift
   swift build -c release
   ```

**Linux specifics:** POSIX file permissions, forward-slash paths, shell quoting and Linux-only dependencies. These don't change Swift's basic syntax, but they matter when you distribute a tool.

### Path M — macOS Swift, plus Apple app development

1. For **Swift language/CLI** work, use the Swift toolchain included with **Xcode**, or follow <https://www.swift.org/install/macos/> for the current Swift.org toolchain.
2. If you want Track A, install **Xcode** from Apple's supported distribution channel and confirm `xcodebuild -version`, `swift --version` and that an iOS Simulator runtime is available in Xcode.
3. Install Git and optionally VS Code with the Swift extension. Create an executable package as above and run `swift test` when tests are added.
4. A **Mac is required for the SwiftUI/Xcode path in this guide**. Simulator builds do not require purchasing an iPhone. App Store/TestFlight distribution may require an Apple Developer Program membership and compliance with current rules.

### Repository and commands for all three operating systems

```text
swift-roadmap/
├── README.md
├── journal.md
├── week-01/ ... week-08/         # shared language curriculum
├── shared/                       # reusable pure Swift model and logic
├── tests/                        # portable unit tests and fixtures
├── track-a-swiftui/              # choose with a Mac
├── track-b-cross-platform-cli/   # choose on Windows/Linux/macOS
└── docs/                         # checkpoints, bug notes, screenshots
```

Use one Git repository and commit after every session. A package created by `swift package init --type executable` is the starting point; keep exercise folders independent when package names or dependencies would conflict.

| Command | Purpose |
|---|---|
| `swift --version` | Display the Swift toolchain version. |
| `swift package init --name MyTool --type executable` | Start an executable Swift package in the current directory. |
| `swift run MyTool` | Build and run a named executable product. |
| `swift build` / `swift build -c release` | Debug / optimized builds. |
| `swift test` | Run the package tests. |
| `swift package --help` | Explore Swift Package Manager commands. |
| `git status` / `git add .` / `git commit -m "..."` | Save a reproducible session. |

### Your very first Swift program

Save to `hello.swift` and run it with `swift hello.swift`, or put the equivalent content into your executable package's entry point and use `swift run`.

```swift
let language = "Swift"
let sessions = 72
print("I'm learning \(language) in \(sessions) sessions.")

let scores = [5, 7, 9]
let total = scores.reduce(0, +)
print("Total score: \(total)")
```

You will soon learn why `let` usually beats `var`, how `Array` stores values, what closures are, and what type inference means.

---
## Part 1 — The language and problem solving

### Week 1 — First programs, values and control flow (days 1–6)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **1** | What programming is; Swift source, compiler vs `swift run`, `print()`, comments, expressions and `let`. | Greeting program and a three-question CLI questionnaire. | Run from a fresh terminal; explain execution and `let` vs `var`. |
| **2** | Variables, `Int`, `Double`, `Bool`, `String`, interpolation, explicit conversion and integer division. | Tip calculator and Celsius/Fahrenheit converter. | Test zero, negatives and decimals; no silent integer truncation. |
| **3** | Operators, comparisons, `if`/`else`, `switch`, ranges and pattern-based switch cases. | Shipping-cost selector and grade calculator. | Boundary values produce correct output and all branches run. |
| **4** | `for-in`, `while`, `repeat-while`, `stride`, `break`, `continue`; avoid infinite loops. | FizzBuzz, times tables, number-guessing game. | Trace loop state on paper and handle an invalid guess. |
| **5** | Functions: labels, parameters, defaults, return values, tuples and local scope. | `isPrime`, `maxOfThree`, currency and temperature helpers. | Each function has at least three manually verified calls. |
| **6** | Project and review: organizing small functions; first Git commit. | Menu-driven budget calculator with add/list/total/reset. | Can use for five minutes without crash; committed `swift-w1`. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

### Week 2 — Collections, text and safe optionals (days 7–12)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **7** | Arrays: literals, indexing, append/remove, loops, `first`, slices and bounds checks. | Score tracker with min, max, mean and remove-by-index. | Empty arrays and invalid indices are handled without a trap. |
| **8** | Dictionaries and Sets: keys, lookup, uniqueness, iteration and sorting. | Word-frequency program and duplicate contact detector. | Explain why dictionary lookup returns an optional. |
| **9** | Strings and Unicode: interpolation, `String.Index`, characters, split/join and trimming. | Palindrome checker with accented and emoji samples. | No assumption that string indices are integer offsets. |
| **10** | Optionals: `Int?`, `if let`, `guard let`, `??`, optional chaining and `!` risks. | Safe parser that accepts or rejects name, age and email. | Malformed input never crashes; no unjustified force unwraps. |
| **11** | Closures, trailing closures; `map`, `filter`, `reduce`, `sorted`. | Transform a CSV-like list into filtered purchase reports. | Can rewrite one transformation as a plain loop and compare. |
| **12** | Checkpoint 0: build without notes, test edge cases. | Interactive contact book using arrays, sets, dictionaries and optionals. | Runs 20 use cases; 30-minute memory quiz; tag `swift-p1`. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

## Part 2 — Swift's type system and safety

### Week 3 — Value types, models and contracts (days 13–18)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **13** | Structs: stored/computed properties, initializers, methods, `mutating`; value semantics. | `Product`, `Cart`, `LineItem` with valid price/quantity rules. | Copies of cart data don't silently mutate the original. |
| **14** | Enums: cases with associated/raw values, `switch` exhaustiveness, `CaseIterable`. | Model order status and payment result, print reports. | Every enum case has deliberate behavior and tests. |
| **15** | Classes, identity, reference semantics, `init`, `deinit`; choose struct vs class. | Compare `struct Account` and `class Account` mutation behavior. | Explain copying, aliasing and object lifetime aloud. |
| **16** | Protocols, extensions, protocol composition and default implementations. | `DiscountRule` with two independent implementations. | Adding a new discount never edits the checkout algorithm. |
| **17** | Generics, type constraints, `Equatable`, `Hashable`, `Comparable`, `Identifiable`. | Generic `ResultBox<T>` plus comparable sorting of `Task` models. | Type errors fail at compile time and equality is meaningful. |
| **18** | Project/review: domain modeling and refactoring. | Inventory core with structs, enums, protocols and sorted reports. | All rules live in model layer; demonstrate two value-copy cases. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

### Week 4 — Errors, memory and testing (days 19–24)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **19** | `throw`, `throws`, `do`/`try`/`catch`, `try?`, error types and `defer`. | Robust order importer with explicit input errors. | Malformed record yields actionable message, not an app crash. |
| **20** | ARC, strong/weak/unowned references, closure capture lists and retain cycles. | Make a small retain-cycle example; then fix it using `weak`. | Explain the ownership graph; `deinit` runs after release. |
| **21** | Access control: `private`, `fileprivate`, `internal`, `public`; API naming. | Convert inventory core into a cleanly separated module. | Illegal state changes cannot be made by a consumer. |
| **22** | Swift Package Manager: `Package.swift`, targets, products and dependencies. | Create a reusable inventory library and CLI executable. | Fresh clone builds with a documented single command. |
| **23** | Swift Testing: `import Testing`, `@Test`, `#expect`, parameterized tests, fixtures. | Write at least 15 model and error-path tests. | A deliberately broken assertion fails in `swift test`. |
| **24** | Checkpoint 1: packaged app with persistent data and tests. | Inventory CLI with JSON save/load and 20 passing tests. | Clean rebuild/test on the home OS; tag `swift-p2`. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

## Part 3 — Foundation, concurrency and engineering habits

### Week 5 — Files, JSON, networking and packages (days 25–30)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **25** | Foundation basics: `Date`, `Calendar`, `UUID`, `URL`, `FileManager`, `Data`. | Timestamped expense records with stable identifiers. | Date/time formatting tested for at least two locales. |
| **26** | `Codable`, `JSONEncoder`/`JSONDecoder`, stable schemas and migrations. | Save/load inventory with a version field and bad-file detection. | Data survives restart; unknown fields handled intentionally. |
| **27** | Text files, structured input, UTF-8, path handling and cross-platform paths. | Cross-platform CSV reader with quoted-fields test fixtures. | Works with Windows-style CRLF and Unix LF; handles bad rows. |
| **28** | HTTP basics, `URLSession`, status codes, retries/timeouts; async API. | Read public sample JSON or locally hosted mock data. | Validates response status, handles offline and malformed JSON. |
| **29** | Dependency injection and separating networking, decoding and business rules. | Fake URL/data service for offline deterministic tests. | Tests never require access to a live external website. |
| **30** | Project/review: import/export tool. | CLI that loads expenses from CSV, saves JSON and prints reports. | Round-trip tests and error cases pass on two fixture files. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

### Week 6 — Swift concurrency without data races (days 31–36)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **31** | `async`/`await`, throwing async methods, suspension points and structured tasks. | Async mock importer with three delayed data sources. | Explain why async is not identical to parallel. |
| **32** | `async let` and task groups, failure propagation, cancellation. | Fetch 10 sample documents concurrently with a limit. | Cancellation stops unnecessary work; results are accounted for. |
| **33** | Actors, actor isolation and protecting shared mutable state. | Thread-safe `InventoryStore` actor used by parallel clients. | Concurrent changes maintain documented invariants. |
| **34** | `Sendable`, `@Sendable`, Swift 6 language mode and isolation diagnostics. | Fix an intentional shared-state compiler diagnostic. | No unexplained data-race or Sendable diagnostics remain. |
| **35** | `AsyncSequence`/`AsyncStream`, producer-consumer flow and backpressure concept. | Stream progress events for import of 1,000 records. | Consumer receives completion/cancellation as designed. |
| **36** | Checkpoint 2: async data pipeline. | Concurrent CSV-to-JSON transformer with actor-isolated state. | At least 20 tests and clear cancel/failure reports; tag `swift-p3`. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

## Part 4 — Building professional Swift systems

### Week 7 — Algorithmic thinking and reusable design (days 37–42)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **37** | Complexity: Big-O, linear/binary search, sorting; correct benchmarks. | Benchmark searching and sorting 10,000 inventory records. | Record repeatable timing with input sizes and caveats. |
| **38** | Data structures as choices: arrays, sets, dictionaries, queues and heaps conceptually. | Priority scheduler using a simple queue; compare strategies. | Explain the data structure choice, not just performance. |
| **39** | Protocols vs generics, dependency inversion, mocking and cohesion. | Split input adapters from import rules and output formatters. | Swap a real data source for a fake without editing core logic. |
| **40** | Diagnostics and LLDB: breakpoints, stepping, variables, call stacks. | Debug a planted fault in a 100-line program without print spam. | Record root cause, reproduction, and the exact fix. |
| **41** | Testing strategy: boundaries, property-style cases, regression tests, coverage. | Add 15 focused tests to the importer and scheduler. | A prior regression stays fixed after refactor. |
| **42** | Project/review: library API quality. | Release first version of `SwiftDataCore` as a reusable package. | README example works from a fresh folder; tag `swift-w7`. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

### Week 8 — Packaging, security and core checkpoint (days 43–48)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **43** | Robust CLI I/O: stdin, stdout, stderr, exit codes, helpful `--help`. | Make an inspect/import/export tool with meaningful exit codes. | Shell scripts can distinguish success from failure. |
| **44** | ArgumentParser package and commands/options/flags; dependency pinning. | Add `list`, `add`, `import` and `report` subcommands. | Unknown args receive useful help; options are validated. |
| **45** | Security basics: validate untrusted input, redact secrets, avoid shell injection. | Refactor file import and error logging for hostile inputs. | No command string assembled from user-controlled data. |
| **46** | Reproducible builds, CI across operating systems, release notes and licensing. | GitHub Actions matrix for Windows/Linux/macOS if available. | Every chosen OS has a clean build and package tests. |
| **47** | Capstone planning: user stories, test plan, README, issue list, time budget. | Write two alternative one-page proposals for Track A and B. | Pick one with five measurable acceptance criteria. |
| **48** | Checkpoint 3: independent shared-core deliverable. | Build a reusable, tested Swift package and complete CLI feature. | 30+ tests, one clean release build and `swift-core` tag. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.


---

## Part 5A — Choose Track A: SwiftUI apps (macOS + Xcode only)

**Track rule:** Days 49–72 below are the **SwiftUI** version of your last four weeks. Do not attempt SwiftUI exercises on a Windows-only or Linux-only toolchain. Keep your portable shared model code; import it into the Xcode app.

### Week 9 — SwiftUI views and reactive state (Mac + Xcode only) (days 49–54)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **49** | Xcode project layout, SwiftUI `App`, `Scene`, `View`, Preview and simulator. | Create native personal-planner app and two simple screens. | Launches on a supported simulator or as a macOS app. |
| **50** | Declarative layout: `VStack`, `HStack`, `ZStack`, `List`, `ScrollView`, modifiers. | Dashboard with task rows and empty-state design. | Layout works at two screen sizes and long titles. |
| **51** | State ownership: `@State`, `@Binding`, observable models and redraw rules. | Editable task list with add/toggle/delete. | Updates instantly and a single source owns the state. |
| **52** | Forms, `TextField`, `Toggle`, `Picker`, validation and keyboard UX. | Task editor with due date and priority fields. | Invalid forms cannot be saved; errors are readable. |
| **53** | Reusable views, previews, environment and navigation fundamentals. | Task detail view, priority badge and basic navigation. | Can navigate without breaking state or accessibility. |
| **54** | Project/review: first usable SwiftUI vertical slice. | A two-screen planner with editable in-memory tasks. | A test user completes add/edit/delete in five minutes. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

### Week 10 — App architecture, storage and networking (days 55–60)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **55** | `NavigationStack`, routing and view identity; state restoration concept. | List/detail/settings navigation with deep hierarchy. | Back navigation preserves expected task state. |
| **56** | Separating views, domain model and repositories; observable state injection. | Connect the shared `SwiftDataCore` package to the UI. | Business rules have no SwiftUI dependencies. |
| **57** | Persistence options: JSON documents, `UserDefaults` settings; intro to SwiftData. | Save tasks and a theme preference locally. | Data survives app relaunch; corrupt data fails gracefully. |
| **58** | Async UI state: loading/error/success and network request cancellation. | Pull a public sample feed or mock suggestions into a view. | No main-thread blocking; offline state is explicit. |
| **59** | Images, basic animation, SF Symbols and adaptable light/dark appearance. | Polish row interactions and theme behavior. | Reduce Motion and both color schemes remain usable. |
| **60** | Project/review: persisted, network-aware app. | Planner with offline tasks and optional suggestion feed. | Core works without internet; error states manually tested. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

### Week 11 — Accessibility, testing and reliability (days 61–66)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **61** | Accessibility labels, traits, VoiceOver, large text and touch targets. | Audit the planner with Accessibility Inspector/VoiceOver. | Primary actions can be discovered by assistive technology. |
| **62** | Unit testing state and model logic with Swift Testing. | 25 state/model tests with fake persistence. | Test suite runs with no network or clock dependency. |
| **63** | UI tests, launch arguments, deterministic seed data and screenshots. | Automated add/toggle/delete smoke test. | UI test passes twice consecutively from clean state. |
| **64** | Profiling with Instruments and Xcode debugger; memory and performance basics. | Profile 1,000 task rows and remove largest bottleneck. | Before/after metrics and device/simulator recorded. |
| **65** | Privacy, permissions, secrets, network rules and platform deployment targets. | Write privacy checklist and ensure no secrets in source. | Permission rejection or offline state is handled. |
| **66** | Project/review: release candidate. | Polished planner with tests, accessibility and documented limitations. | A second person completes top three tasks without help. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

### Week 12 — Track A capstone: ship the Apple app (days 67–72)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **67** | Write user stories and freeze must-have scope. | Finalize 5 acceptance criteria and repository structure. | Acceptance criteria are verifiable, not just visual. |
| **68** | Implement reliable task models, filters and deadlines. | Complete planner core, categories and search. | Core workflows work with empty and large datasets. |
| **69** | Finish persistence, import/export or optional network integration. | Make an export path and offline mode. | Exported data can be re-imported or audited. |
| **70** | Accessibility, edge cases, test sweep and performance pass. | Add tests, improve VoiceOver and fix bugs. | At least 30 tests; no known crash in acceptance paths. |
| **71** | Release preparation: icons, README, screenshots and local distributable build. | Build for the selected simulator / macOS target. | New developer can build it from documented steps. |
| **72** | **Final capstone review**: demo, user feedback, Git tag. | Record a two-minute demo and collect one user review. | All 5 criteria pass; tag `swift-swiftui-v1`. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.


---

## Part 5B — Choose Track B: cross-platform CLI and automation (Windows / Linux / macOS)

**Track rule:** These are alternative days **49–72**. Complete them instead of Part 5A if your goal is native tools or your computer does not run Xcode. Keep the core standard-library/Foundation-based so your tool remains easy to port.

### Week 9 — Professional native command-line tools (all three OSs) (days 49–54)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **49** | Swift ArgumentParser: `@main`, commands, options, arguments and flags. | Create `taskctl` with `add`, `list`, `done`, `remove`. | `--help` and invalid options behave predictably. |
| **50** | Structured CLI errors, exit codes, logging and standard streams. | Return meaningful errors for missing files and bad commands. | A calling shell distinguishes usage error vs data error. |
| **51** | File paths and portability: URL/FileManager, CRLF, Unicode, drive letters. | Load shared fixtures correctly on Windows and Linux. | No hard-coded `/tmp` or `C:\` paths in domain logic. |
| **52** | Data encoding, schema versions and forward-compatible JSON. | Versioned local task store and export format. | Old sample schema migrates with a tested policy. |
| **53** | CLI command architecture and reusable library targets. | Separate `taskctl` UI from `TaskCore` library. | Model tests don't import ArgumentParser. |
| **54** | Project/review: portable task manager. | Task manager with five subcommands and persisted data. | Works from a clean checkout on the chosen native OS. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

### Week 10 — Batch processing and reliable I/O (days 55–60)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **55** | Data pipelines: streaming vs loading full files; input validation. | Import 100,000 synthetic events in chunks. | Memory growth is bounded and measured. |
| **56** | CSV/JSON imports, field mapping and invalid-record reports. | Build `taskctl import` with dry-run mode. | Bad rows reported with source line numbers. |
| **57** | Atomic file-update concept, temp files, recoverable backups and crash safety. | Implement safe-write strategy with backup and failure simulation. | Interrupted write never silently destroys last good data. |
| **58** | Structured output: machine-readable JSON and human-readable tables. | Add `--format json\|table` with deterministic ordering. | JSON output is parseable and stable in tests. |
| **59** | Regex/search/filter/sort/pagination; Big-O for bulk workloads. | Query tasks by dates, tags and free text. | Stable results with 10,000 records and repeatable timings. |
| **60** | Project/review: import/report utility. | Release usable `taskctl import` and `report` subcommands. | Fixture tests cover empty, invalid and 100k-input files. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

### Week 11 — Async tools, robustness and cross-platform verification (days 61–66)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **61** | `URLSession` on supported hosts; conditional module imports where needed. | Optional `sync` command backed by a local HTTP test server. | Fails cleanly when offline and never loses local records. |
| **62** | Async concurrency, bounded task groups and actor-based shared state. | Parallel metadata validator with cancellation. | Predictable output order and no data races. |
| **63** | Configuration, environment variables, secret hygiene and logging. | Add optional config file and redact sensitive values. | No credentials in Git or verbose logs. |
| **64** | Test architecture: Swift Testing, golden files and time/FS injection. | Reach 40 tests covering platform path and error cases. | Tests are deterministic and can run without internet. |
| **65** | Build/release/CI on Windows, Linux and macOS; native binaries differ. | Set up GitHub Actions OS matrix or manual validation checklist. | Build logs prove every **claimed** target platform works. |
| **66** | Project/review: cross-platform release candidate. | Bundle README, version/help output and example datasets. | Another user runs two commands without coaching. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.

### Week 12 — Track B capstone: ship the cross-platform tool (days 67–72)

| **Day** | **Learn** | **Build** | **Done when** |
|---:|---|---|---|
| **67** | Scope and acceptance criteria for the final workflow. | Specify five scenarios for `taskctl` including failure cases. | Each scenario has command + expected exit/output. |
| **68** | Complete core implementation: CRUD, labels, search, analytics. | Finish features with typed core model and tests. | No command can silently leave invalid task state. |
| **69** | Complete importer/exporter and optional sync with cancellation. | Round-trip 10,000 records; handle malformed files. | Data survives restart and rejected input is explained. |
| **70** | Reliability tests, memory/batch benchmark and performance note. | Raise test count to 50; measure 100k record import. | Measured results and test scope listed in README. |
| **71** | Reproducible native release: version, license, changelog and archives. | Publish local Windows/Linux/macOS artifacts for tested hosts. | Fresh user can install and run from README alone. |
| **72** | **Final capstone review**: user trial, issue fixes and tag. | Record two-minute CLI demo and receive independent feedback. | All criteria pass, CI green for tested platforms; tag `swift-cli-v1`. |

**Review:** Demo the project; explain one piece from memory, record a bug and its fix, then commit.


---


## Break-it exercises: bugs you should deliberately cause

Do these on **your own programs** and record the message, the cause and the corrected code in `journal.md`.

| Sessions | Deliberate failure | What to learn |
|---|---|---|
| 1–6 | Divide integers expecting a decimal; break a `switch` branch | Types and branch coverage. |
| 7–12 | Read an out-of-bounds array element; force-unwrap `nil` in a throwaway sample | Array safety and optionals. |
| 13–18 | Assume a struct and class copy behave identically | Value vs reference semantics. |
| 19–24 | Decode malformed JSON; cause a test to fail intentionally | Error surfaces and red/green tests. |
| 25–30 | Lose network connection; load an invalid CSV row; use CRLF | Platform-neutral I/O and error handling. |
| 31–36 | Create a shared mutable state race in a throwaway exercise | Actor isolation and compiler diagnostics. |
| 37–42 | Break dependency boundary; introduce a slow algorithm | Testability and real performance checks. |
| 43–48 | Run the CLI with invalid options; inject a bad path | Usable errors, exit codes and resilience. |
| 49–72A | Use empty lists, huge text, offline mode and interrupted saves | Production-like app reliability. |
| 49–72B | Interrupt writes, corrupt input, remove permissions and cancel tasks | Durable, automation-safe command-line tools. |

## Checkpoints — do not skip a failed gate

| Gate | After | Required evidence | If missed |
|---|---:|---|---|
| **Checkpoint 0 — syntax and collections** | 12 | Write a contact book from memory using functions, collections and optionals; demonstrate 20 cases. | Repeat days 7–12 with a smaller task. |
| **Checkpoint 1 — types and testing** | 24 | Build inventory package with models, custom errors, persistence and **20 passing tests**. | Review structs/protocols/testing before async code. |
| **Checkpoint 2 — async safety** | 36 | Concurrency-safe importer with actor store, task cancellation and tests. | Repeat actor isolation and cancellation exercises. |
| **Checkpoint 3 — shared core** | 48 | Swift package + documented CLI, **30+ tests**, release build and a planned specialization. | Repair CLI/package/tests before track choice. |
| **Track A final** | 72A | SwiftUI app with offline tasks, accessibility checks, **30+ tests**, a demo and a reproducible build. | Rework missing acceptance criteria; don't claim App Store release. |
| **Track B final** | 72B | Native CLI with **50+ tests**, imports/exports, help, exit codes, a demo and verified OS builds. | Test each claimed OS and missing failure paths. |

**One deliberately harder memory test at day 48:** in 45 minutes, implement a small `Codable` model, a function that parses one record, an enum representing errors, and two tests. Then explain optionals, ARC, protocols, `async`/`await`, actors and `Sendable` out loud without notes.

## Portfolio you should have at the end

- A Swift basics repository with 48 shared sessions, Git history and a journal of debugging findings.
- A typed model package showing value semantics, protocols, generics, error handling, `Codable` and tests.
- An actor-protected async import/data pipeline with cancellation and deterministic tests.
- **Track A:** a SwiftUI planner app with screen recordings, accessibility notes, reproducible Xcode build and tested repository.
- **Track B:** a portable native CLI with subcommands, useful help, predictable exit codes, import/report workflows and tested OS artifacts.
- A final README with prerequisites, installation, examples, tests, platform support, limitations and at least one external user review.

## Optional extension after day 72 (not included in the 228 hours)

**Server-side Swift (usually Linux or macOS):** learn HTTP routing, JSON validation, a relational database, authentication, environment-based configuration, health checks, structured logging, Docker and CI. A framework such as **Vapor** has official macOS/Linux setup documentation: <https://docs.vapor.codes/>. Verify each framework and package's **Windows compatibility separately**; having a Windows Swift compiler does **not** imply a server framework's complete stack works on Windows. If Windows is your sole machine, use the native cross-platform CLI capstone first and, if needed, a separate Linux environment for supported server frameworks.

**Further choices:** performance profiling and C interoperability; developing Swift packages for other projects; bridging Swift and Objective-C on Apple platforms; UIKit/AppKit once you've learned SwiftUI; Android Swift SDK, Embedded Swift, and WebAssembly (these involve additional tooling and varying support levels and are **not** assumed in the base roadmap).

## Reference shelf

Use these as a *reading spine*. Open the latest version when studying; command syntax, platform dependencies and Apple SDK requirements evolve.

| Resource | Use in this roadmap | URL |
|---|---|---|
| **The Swift Programming Language** (official book) | Days 1–36: syntax, collections, OOP, error handling, concurrency. | <https://docs.swift.org/swift-book/documentation/the-swift-programming-language/> |
| **Swift platform support** | Supported toolchain hosts and deployment targets. | <https://www.swift.org/platform-support/> |
| **Swift install: Windows** | Native Windows toolchain prerequisites and WinGet instructions. | <https://www.swift.org/install/windows/> |
| **Swift install: Linux** | Swiftly, supported distributions, native toolchains. | <https://www.swift.org/install/linux/> |
| **Swift install: macOS** | Xcode/toolchain installation paths. | <https://www.swift.org/install/macos/> |
| **Swift Package Manager** | Packages, dependencies, builds, tests. | <https://docs.swift.org/package-manager/documentation/packagemanagerdocs/> |
| **Swift Testing** | `@Test`, `#expect`, parameterized tests and SwiftPM integration. | <https://developer.apple.com/documentation/testing> |
| **Swift Argument Parser** | Track B CLI commands, options and help. | <https://www.swift.org/get-started/command-line-tools/> |
| **Swift 6 concurrency** | Async tasks, task groups, actors and isolation. | <https://docs.swift.org/swift-book/documentation/the-swift-programming-language/concurrency/> |
| **SwiftUI learning** (Mac required) | Track A views, state and navigation. | <https://developer.apple.com/tutorials/develop-in-swift/welcome-to-swiftui> |
| **Apple SwiftUI documentation** | SwiftUI API design and Apple-platform integration. | <https://developer.apple.com/documentation/swiftui> |
| **Vapor documentation** (optional) | Server Swift after the shared/CLI course. | <https://docs.vapor.codes/> |

### Reading and development discipline

1. **Use the book, then the exercise:** read today's language concept in the official Swift book, type a 5-line example, then close the tab and write the build task.
2. **Treat compiler diagnostics as instruction:** Swift's strong type system and concurrency diagnostics teach ownership and isolation. Record one diagnostic a day.
3. **Choose portable dependencies deliberately:** build the shared core with the Swift standard library and cross-platform Foundation APIs; isolate platform-specific code behind a protocol or conditional compilation.
4. **Verify each claimed OS:** your primary platform is your daily workspace; CI or a second machine is your evidence for any extra operating system. macOS/Xcode is mandatory only for Track A.
5. **Do not confuse running with shipping:** the final capstone needs tests, docs, a fresh-install check and a user trial, not just an IDE screenshot.

---

*About this guide: This is an original Swift-specific roadmap modeled on the structure of the user's Java, Go, C++, R, Ruby, Dart and Assembly study guides. It keeps their beginner entry, short daily lessons, build tasks, "Done when" gates, project reviews, milestones and shipped capstones. Platform/toolchain details were checked against official Swift.org and Apple documentation in October 2026; follow current installation pages if they change.*
