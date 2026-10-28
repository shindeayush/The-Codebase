# Dart Roadmap: From Zero to Flutter Apps

*60 sessions | 10 weeks | about 190 hours*

Learn the Dart language first: types, sound null safety, object-oriented design, async code and packages. Then use Flutter to build responsive, accessible, tested applications with navigation, state, networking, persistence and a shareable release. Assumes no prior programming.

## Start here

**How Dart works.** Dart source is written in .dart files and can run in the Dart VM during development or be compiled for deployment. Flutter uses Dart to build apps from reusable widgets. The Flutter SDK includes Dart, so separate SDK installation is not required for a Flutter-first setup.

**Setup (once, about 45–90 minutes):**

1.  Install the stable Flutter SDK using https://docs.flutter.dev/install (it includes Dart). For Dart-only study see https://dart.dev/get-dart.

2.  Install VS Code with Dart and Flutter extensions, or Android Studio. Set up at least one target: Chrome, desktop or Android emulator/device.

3.  Run flutter doctor and resolve the warnings relevant to your chosen target; verify dart --version and flutter --version.

4.  Create dart-roadmap with week-01 through week-10 folders and journal.md; use dart create for console projects and flutter create for apps. Initialize Git.

5.  From day 1 run dart format . and dart analyze; for Flutter apps use flutter analyze and flutter test. Never commit signing keys or API secrets.

## How each study session works

| **Minutes** | **Block** | **What you do**                                                               |
|-------------|-----------|-------------------------------------------------------------------------------|
| 10          | Start     | Re-type yesterday’s snippet from memory; review your journal’s next step.     |
| 40          | Learn     | Work through just today’s topic; reproduce examples while taking short notes. |
| 90          | Build     | Write the exercise yourself, without copying generated solutions.             |
| 30          | Break it  | Deliberately introduce a bug, reproduce it, inspect the error and fix it.     |
| 10          | Save      | Run checks, commit, and write: learned / confused / next first step.          |

Days are study sessions, not calendar days. Sessions 1–5 each week last about 3 hours; the sixth is a 4-hour project and review. At every checkpoint, repeat weak topics before moving forward.

**Definition of done.** dart analyze / flutter analyze is clean, automated tests pass where available, format is clean, the app runs and the code is committed.

Study rule: do not race a calendar. If an exercise needs another session, complete it before proceeding. Keep a journal and a Git commit after every working session.

## Part 1 — Dart language foundations

### Week 1 — Dart syntax and functions (days 1–6)

| **Day** | **Learn**                                                                            | **Build**                                          | **Done when**                                       |
|---------|--------------------------------------------------------------------------------------|----------------------------------------------------|-----------------------------------------------------|
| **1**   | What Dart is: VM/JIT and AOT at a high level; dart run, main(), print(), DartPad.    | hello.dart and a five-line command-line greeting.  | dart run works and you can explain the entry point. |
| **2**   | var, final, const; int, double, num, String, bool; type inference and interpolation. | Tip calculator and temperature converter.          | Conversions and constants behave correctly.         |
| **3**   | Operators, if/else, switch expressions, comparisons, logical operations.             | Grade calculator and configurable shipping rule.   | Every branch including boundaries is covered.       |
| **4**   | for, for-in, while, do-while; break, continue and collection-for.                    | FizzBuzz, guessing game and filtered list builder. | You can trace and explain each loop.                |
| **5**   | Functions: parameters, named/optional, arrow syntax, closures and scope.             | Write four reusable validators/converters.         | Functions work on good and bad inputs.              |
| **6**   | Project / review, Git and dart format.                                               | A menu-driven Dart CLI quiz with scores.           | dart analyze is clean; project committed dart-w1.   |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 2 — Collections, null safety and objects (days 7–12)

| **Day** | **Learn**                                                                      | **Build**                                                       | **Done when**                                           |
|---------|--------------------------------------------------------------------------------|-----------------------------------------------------------------|---------------------------------------------------------|
| **7**   | List, Set, Map; literals, generics, spreads, collection-if and collection-for. | Build a contact registry and duplicate detector.                | Each collection has a reason for being chosen.          |
| **8**   | String operations, RegExp, DateTime, Duration and parsing.                     | Parse task due dates and normalize usernames.                   | Malformed dates receive clear errors.                   |
| **9**   | Sound null safety: ? types, ?, !, ??, ??=, late; promotion and required.       | Turn a nullable profile model into safe display output.         | No force-unwrap used without a justified invariant.     |
| **10**  | Classes: fields, constructors, named constructors, getters/setters, toString.  | Model Product and Cart with validation.                         | Cart totals cannot become invalid.                      |
| **11**  | Inheritance, abstract classes, interfaces, mixins, enums and composition.      | Model discount rules using a shared contract.                   | Adding a discount does not change Cart internals.       |
| **12**  | Checkpoint 0: independent console project.                                     | CLI inventory system with save/load in JSON and a domain model. | Runs from a clean checkout; analyze clean; tag dart-p1. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Assign null to non-nullable field; change const data; make an off-by-one loop; cause a FormatException and handle it.

## Part 2 — Async Dart and maintainable packages

### Week 3 — Asynchronous Dart and modern types (days 13–18)

| **Day** | **Learn**                                                                 | **Build**                                                   | **Done when**                                                     |
|---------|---------------------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------|
| **13**  | Error handling: try/on/catch/finally; FormatException; custom exceptions. | Handle bad JSON, missing fields and invalid menu input.     | Failures return errors without crashing core workflow.            |
| **14**  | Records, destructuring, pattern matching and switch patterns.             | Parse typed responses and match success/error records.      | All variants are handled intentionally.                           |
| **15**  | Generics, extension methods and typedef; avoiding needless abstractions.  | Create a generic Result\<T\> and two useful extensions.     | Typed tests cover strings and integers.                           |
| **16**  | Futures, async/await, Future.wait and exception propagation.              | Fetch three simulated resources concurrently.               | Timeout and failure paths are visible.                            |
| **17**  | Streams and async\*; subscriptions; cancellation and memory hygiene.      | Stream simulated sensor events and stop them cleanly.       | No events arrive after cancellation.                              |
| **18**  | Project / review: async command-line tool.                                | JSON-based CLI data fetcher with retry rules and summaries. | Tests cover timeout, malformed response and success; tag dart-w3. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 4 — Packages, HTTP and automated tests (days 19–24)

| **Day** | **Learn**                                                                         | **Build**                                                              | **Done when**                                  |
|---------|-----------------------------------------------------------------------------------|------------------------------------------------------------------------|------------------------------------------------|
| **19**  | Dart packages: pubspec.yaml, dart pub add/get, semantic versions, package layout. | Convert validators into a reusable local package.                      | Consumer project resolves package predictably. |
| **20**  | Testing: package:test, groups, setUp, matchers and parameterized cases.           | Write 15 unit tests for inventory and validation.                      | A deliberately failing test is caught.         |
| **21**  | Linting, dart analyze, dart format, doc comments and API design.                  | Refactor package and document its public API.                          | Analyzer clean; public API is understandable.  |
| **22**  | JSON encode/decode, typed parsing, HTTP concepts; package:http.                   | Fetch and parse public sample JSON into a model.                       | Missing or renamed fields fail informatively.  |
| **23**  | Layering: data source, repository, domain; dependency injection by constructor.   | Decouple network interface from application logic.                     | Fake data source supports deterministic tests. |
| **24**  | Checkpoint 1: tested reusable Dart code.                                          | Release a CLI package with HTTP or offline fixture, JSON and 20 tests. | dart test/analyze/format pass; tag dart-p2.    |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Forget to await a Future; leave a StreamSubscription running; send malformed JSON; introduce a non-exhaustive pattern case.

## Part 3 — Flutter layout, state and navigation

### Week 5 — Flutter widgets and first app (days 25–30)

| **Day** | **Learn**                                                                       | **Build**                                              | **Done when**                                                            |
|---------|---------------------------------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------------------------------|
| **25**  | Flutter install: flutter doctor, devices/emulators; widgets and run/hot reload. | Create Flutter starter app with Text, Icon and theme.  | App launches on one supported target.                                    |
| **26**  | Widget tree, StatelessWidget, Scaffold, MaterialApp and basic layout.           | Build a profile screen with Column, Row and Padding.   | No overflow on narrow viewport.                                          |
| **27**  | StatefulWidget, setState, rebuilding and widget lifecycle.                      | Counter and selectable favorites screen.               | UI always represents current state.                                      |
| **28**  | Layout: Expanded, Flexible, ListView, GridView, constraints and scroll.         | Responsive catalog grid/list.                          | Works at phone and tablet-like widths.                                   |
| **29**  | User input: TextField, Form, validators, Focus, buttons and error text.         | Product editor form with validation.                   | Cannot submit incomplete data; errors accessible.                        |
| **30**  | Project / review: first functional Flutter app.                                 | Offline grocery list with add/edit/delete and filters. | Runs without overflows; critical interactions demonstrated; tag dart-w5. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 6 — Navigation, state and accessible layouts (days 31–36)

| **Day** | **Learn**                                                                      | **Build**                                             | **Done when**                                                     |
|---------|--------------------------------------------------------------------------------|-------------------------------------------------------|-------------------------------------------------------------------|
| **31**  | Navigation: Navigator, routes, arguments, back behavior; deep links overview.  | Add list, detail and edit screens.                    | Back stack returns to expected screen.                            |
| **32**  | Themes, Material 3, color scheme, typography and responsive principles.        | Apply consistent light/dark theme and spacing.        | Text remains readable at larger font settings.                    |
| **33**  | State management: inherited/state lifting and ChangeNotifier or ValueNotifier. | Share cart state between listing and checkout.        | No duplicated source of truth.                                    |
| **34**  | Architecture: UI vs state vs data, model/repository/service boundaries.        | Refactor grocery list to separate persistence and UI. | Widget tests can use fake repository.                             |
| **35**  | Accessibility: semantics, contrast, tap targets and localization basics.       | Add labels and screen-reader-friendly controls.       | All primary actions have semantic labels.                         |
| **36**  | Checkpoint 2: Flutter fundamentals.                                            | Two-screen shopping list with theme and shared state. | Widget tests pass on navigation and form validation; tag dart-p3. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Build a layout wider than device constraints; invoke setState after disposal; use bad route args; test empty forms.

## Part 4 — Data, tests and reliability

### Week 7 — Networking and local persistence (days 37–42)

| **Day** | **Learn**                                                                                | **Build**                                                    | **Done when**                                         |
|---------|------------------------------------------------------------------------------------------|--------------------------------------------------------------|-------------------------------------------------------|
| **37**  | Networking in Flutter: http package; FutureBuilder; loading, empty and error states.     | Display a feed from a sample JSON API.                       | Offline/timeout yields a recoverable state.           |
| **38**  | REST operations; JSON serialization; repository methods, request cancellation awareness. | Add create/update/delete against a test or mock API.         | HTTP errors are visible and tests cover them.         |
| **39**  | Local storage options: shared_preferences for small settings; SQLite for records.        | Persist tasks locally using a suitable store.                | Tasks survive full app restart.                       |
| **40**  | Caching and offline-first data flow; synchronization and conflict decisions.             | Show cached list first, then refresh when online.            | Bad network does not erase local edits.               |
| **41**  | Secure handling of credentials; tokens; HTTPS; no embedded API secrets.                  | Design a mock login with fake token storage interface.       | Secrets absent from repo; 401 clears invalid session. |
| **42**  | Project / review: data-connected app.                                                    | Build task manager using API repository + local persistence. | Can add/edit offline; tests pass; tag dart-w7.        |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 8 — Testing, debugging and performance (days 43–48)

| **Day** | **Learn**                                                                     | **Build**                                                           | **Done when**                                                     |
|---------|-------------------------------------------------------------------------------|---------------------------------------------------------------------|-------------------------------------------------------------------|
| **43**  | Flutter tests: unit, widget and integration testing distinctions.             | Write unit tests for domain rules and three widget tests.           | Tests verify behavior rather than screenshots alone.              |
| **44**  | Mocking/fakes, network fixtures and deterministic clock/data.                 | Replace real API in tests with a fake service.                      | Tests run offline and produce same results.                       |
| **45**  | Debugging: breakpoints, Flutter DevTools, layout inspector and logs.          | Diagnose a deliberately introduced layout and async bug.            | Root cause explained, not just patched.                           |
| **46**  | Performance: rebuilds, const widgets, lazy lists and image loading.           | Profile a long list and reduce unnecessary rebuilds.                | Before/after measurement saved.                                   |
| **47**  | Platform concerns: permissions, app lifecycle, web versus mobile differences. | Handle app resume and a denied permission path safely.              | App remains usable when permission is denied.                     |
| **48**  | Checkpoint 3: test and performance review.                                    | Expand task app with 25 tests, profiling note and offline handling. | flutter analyze/test pass; no known uncaught errors; tag dart-p4. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Disconnect the network, delete local data, reject a permission and open app with large text; verify graceful behavior.

## Part 5 — Release and capstone

### Week 9 — Release engineering and distribution (days 49–54)

| **Day** | **Learn**                                                                              | **Build**                                                              | **Done when**                                              |
|---------|----------------------------------------------------------------------------------------|------------------------------------------------------------------------|------------------------------------------------------------|
| **49**  | Release builds: Android/web/desktop targets, app IDs, versioning and signing overview. | Prepare non-secret release config and an app icon.                     | App name and version are intentional.                      |
| **50**  | CI: GitHub Actions for flutter analyze, test and build on supported target.            | Create repeatable CI checks.                                           | A failed test blocks green status.                         |
| **51**  | Distribution: web hosting or test Android build; privacy policy considerations.        | Publish a demo web build or distribute a test build privately.         | Another user can launch it from the instructions.          |
| **52**  | Deep links, notifications and backend choices as optional extensions.                  | Implement one optional extension using a test backend.                 | The core app still works without that service.             |
| **53**  | Polish UX: error boundaries, empty states, accessibility and localization.             | Run a usability test with a friend; fix top three issues.              | No dead-end screens in main flow.                          |
| **54**  | Project / review: releasable app.                                                      | Document install, screens, privacy, tests, known limits and changelog. | Release artifact exists; README reproducible; tag dart-w9. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 10 — Flutter application capstone (days 55–60)

| **Day** | **Learn**                                                              | **Build**                                                                 | **Done when**                                                               |
|---------|------------------------------------------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| **55**  | Capstone scope and wireframes: select habit, expense or study planner. | Write five acceptance criteria and sketch three app screens.              | Scope fits 6 sessions and defines offline behavior.                         |
| **56**  | Data model and local persistence.                                      | Build model, repository, migrations/versioning policy and tests.          | Records survive restart and corrupt data is handled.                        |
| **57**  | UI and state flow.                                                     | Build list/detail/edit screens with state management.                     | Create/edit/delete routes stay in sync.                                     |
| **58**  | Network integration and offline state.                                 | Connect optional public/test API with loading and error handling.         | Airplane-mode user can still do core work.                                  |
| **59**  | Testing, performance, accessibility and release.                       | Reach 30 tests, write README and produce a release build.                 | analyze/test green and accessibility review documented.                     |
| **60**  | Final capstone review and demo.                                        | Record a two-minute walkthrough, collect one user review and tag dart-v1. | Another person installs/opens app and completes every acceptance criterion. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Disconnect the network, delete local data, reject a permission and open app with large text; verify graceful behavior.

## Checkpoints and what comes next

These are gates, not optional homework. If you cannot complete a gate without copying, review the relevant sessions and repeat the project. Document what failed and what changed.

| **Gate**                     | **What you must show**                                                             |
|------------------------------|------------------------------------------------------------------------------------|
| **Day 12 · Foundations**     | Console inventory app demonstrating null-safe models, collections and persistence. |
| **Day 24 · Core Dart**       | A packaged CLI or library with HTTP parsing, 20 tests and clean analysis.          |
| **Day 36 · Flutter core**    | A responsive, accessible two-screen app with navigation and tested state.          |
| **Day 48 · App reliability** | Offline-capable data app with 25 tests, network failures and profiling note.       |
| **Day 60 · Capstone**        | Release build, full README, 30 passing tests and user demonstration.               |

## Your portfolio at the end

- Null-safe Dart CLI inventory app and reusable tested package

- Accessible responsive Flutter grocery list with navigation

- Offline-aware Flutter capstone app with API integration, tests and release build

## After the last session

Go deeper in advanced state management, animations, Firebase, platform channels, desktop apps or Dart back ends. Choose packages by maintenance quality and platform support.

## Reference shelf

Start with these official and established resources; read the current version of documentation if commands or package interfaces change. All listed resources have free online documentation.

<table>
<colgroup>
<col style="width: 30%" />
<col style="width: 69%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Resource</strong></th>
<th><strong>Use and link</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Dart language guide</strong></td>
<td>Types, patterns, OOP and async<br />
https://dart.dev/language</td>
</tr>
<tr class="even">
<td><strong>Dart null safety</strong></td>
<td>Non-nullable defaults and safe handling<br />
https://dart.dev/null-safety</td>
</tr>
<tr class="odd">
<td><strong>Dart packages</strong></td>
<td>Pub and package structure<br />
https://dart.dev/tools/pub/packages</td>
</tr>
<tr class="even">
<td><strong>Flutter install</strong></td>
<td>SDK setup and supported targets<br />
https://docs.flutter.dev/install</td>
</tr>
<tr class="odd">
<td><strong>Flutter learning path</strong></td>
<td>Beginner-first Flutter progression<br />
https://docs.flutter.dev/learn</td>
</tr>
<tr class="even">
<td><strong>Flutter networking</strong></td>
<td>HTTP, errors and JSON recipes<br />
https://docs.flutter.dev/cookbook/networking</td>
</tr>
<tr class="odd">
<td><strong>Flutter testing</strong></td>
<td>Unit, widget and integration tests<br />
https://docs.flutter.dev/testing</td>
</tr>
</tbody>
</table>

**About this guide.** Structure adapted from the three supplied learning roadmaps (Java, Go and C++): independent beginner entry, a repeatable study rhythm, day-by-day Learn / Build / Done when tables, project reviews, checkpoints and a shipped capstone. Language-specific topics and exercises here are newly authored; the guides are not translations of those documents.
