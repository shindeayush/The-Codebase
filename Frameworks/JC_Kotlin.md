# Jetpack Compose Roadmap: From Zero to Modern Android Interfaces with Kotlin

**60 sessions | 10 study weeks | approximately 190 hours | created October 29, 2026**

This roadmap is a standalone, project-based guide to Jetpack Compose. Each “Day” below is a **study session**, not necessarily a calendar day. The finish line is **Offline-first habit tracker Android app** with accessible Material 3 UI, navigation, local database, reminder notifications, network sync simulation, UI tests, release build and a documented app demo.

## Start here

**Prerequisites and the beginner bridge.** Kotlin basics (functions, nullability, collections, classes) and introductory Android concepts. Week 1 provides the Android/Compose bridge.

**Operating systems.** Android Studio and Android development work on Windows, Linux and macOS. Use an Android emulator if the host supports hardware acceleration or a physical Android device with USB debugging. Jetpack Compose here targets Android; Compose Multiplatform is a different optional direction.

**Installation.** Install current stable Android Studio and Android SDK. New Project → Empty Activity with Kotlin and Compose enabled. Use the project-generated Kotlin/Gradle and Compose BOM/compiler plugin versions together; avoid pinning stale versions copied from old blog posts. Run first in emulator/device.

### First run

```text
Android Studio → New Project → Empty Activity
Language: Kotlin • Use project-generated Compose setup
Open MainActivity.kt → run ▶ on an Android emulator or device
To run tests: Gradle tool window → verification tasks
or terminal: ./gradlew test (Windows: gradlew.bat test)
```

## How each study session works

| Minutes | Block | Method |
|---:|---|---|
| 10 | Recall | From memory, rewrite a concept from the previous session. |
| 40 | Learn | Read the relevant official documentation; take brief handwritten notes. |
| 90 | Build | Implement the day’s exercise yourself. Do not paste an AI-generated solution. |
| 30 | Break and debug | Create at least one deliberate failure and investigate the tool output. |
| 10 | Save | Commit code, record learned/confused/next step in `journal.md`. |

Sessions 6, 12, 18, … are **four-hour project/review sessions**; normal sessions are about three hours. If you fall behind, complete the current session before progressing. A session is finished only when the exercise runs, the stated check is demonstrated, and the code is committed.

## Build habits and repository layout

```text
jetpack-compose-roadmap/
  README.md
  journal.md
  week-01/
  week-02/
  ...
  capstone/
```

Keep one Git commit per session, a runnable example for every topic, short notes on bugs and fixes, and a README in each weekly project. Use version control; never commit passwords, credentials or production database files.

## Week 1: Kotlin-to-Compose first steps

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Kotlin lambdas, data classes and nullable types | Implement Habit class and simple helper functions | Unit tests cover null and empty inputs |
| 2 | Android Studio project and Gradle structure | Run Empty Activity on emulator | Can locate manifest, resources and app module |
| 3 | @Composable functions and Preview | Build HelloHabit composable | Preview and emulator show same content |
| 4 | Text, Button, Icon and modifier order | Design first habit card | Buttons react without layout clipping |
| 5 | Rows, Columns, Box and spacing | Build stacked dashboard | Layout adapts to narrow and wide screens |
| 6 | Project: static dashboard | Create attractive non-interactive tracker UI | Pass 3 device/screen-size checks |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 2: State and recomposition

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | remember and mutableStateOf basics | Add incrementing completion counter | UI refreshes after input |
| 8 | State hoisting and unidirectional data flow | Extract stateless HabitRow | Parent controls all state |
| 9 | rememberSaveable and process recreation | Preserve draft input across rotation | State survives expected recreation |
| 10 | Derived state and snapshot behavior | Compute progress summary | No redundant duplicated mutable state |
| 11 | Side effects LaunchedEffect and disposable resources | Add timer preview with cleanup | Rotation causes no duplicate jobs |
| 12 | Project: interactive daily tracker | Add/remove/toggle habits | State transitions reproducible |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 12

- From a clean checkout, run the week 2 project and its tests with no undocumented steps.
- Explain three concepts from weeks 1–2 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 3: Material 3 and responsive layouts

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | MaterialTheme, color scheme and typography | Create branded theme | Both light/dark remain readable |
| 14 | Scaffold, top bars and FAB | Build complete app shell | Insets handled and buttons visible |
| 15 | LazyColumn keys and lists | Render 1000 habit entries | Scroll stays stable on insertion |
| 16 | Constraint/layout responsiveness and window sizes | Create tablet dashboard variation | No hardcoded screen width assumptions |
| 17 | Accessibility semantics, touch targets and labels | Enable TalkBack walkthrough | Every interactive element named |
| 18 | Project: production-quality tracker UI | Finish small/large display design | Accessibility audit documented |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 4: Navigation and screen patterns

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Navigation Compose routes and destinations | Add home/details/settings | Back button correct from each screen |
| 20 | Pass IDs instead of large objects | Navigate to habit details | Reloads data using ID |
| 21 | ViewModel lifecycle and saved state | Move UI state from Activity | Rotation doesn't discard state |
| 22 | UI events and state modeling | Expose Loading/Empty/Content/Error state | All four previewed and tested |
| 23 | Form validation and keyboard actions | Create Add Habit screen | Invalid habit rejected with message |
| 24 | Checkpoint 1: Compose fundamentals | Build 3-screen tracker from spec | UI tests of navigation and state pass |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 24

- From a clean checkout, run the week 4 project and its tests with no undocumented steps.
- Explain three concepts from weeks 3–4 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 5: Storage and offline-first design

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Room entities, DAO and migrations | Persist habit table | Data survives app restart |
| 26 | Repository interfaces and test fakes | Hide Room access behind repository | Can substitute fake |
| 27 | Flow collection with lifecycle awareness | Render habits from database stream | Writes update screen automatically |
| 28 | Coroutines, dispatchers and cancellation | Fetch tasks asynchronously | No blocking UI operations |
| 29 | Date/time and timezone boundaries | Define daily habit completion model | Tomorrow/daylight boundaries tested |
| 30 | Project: persistent offline tracker | Build add/edit/delete and check-ins | Cold restart preserves all data |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 6: Networking and sync

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | HTTP client and JSON parsing | Fetch mock public suggestions | Network failure shows retry |
| 32 | Repository offline caching | Store remote suggestion list | Airplane mode displays last data |
| 33 | Sync states and conflict policy | Define server revision and local pending edits | Conflict handling deterministic |
| 34 | WorkManager scheduled sync | Queue background synchronization | Retries obey constraints |
| 35 | Error surfaces and user messaging | Distinguish offline vs server failure | UI avoids infinite spinner |
| 36 | Project: offline-to-online sync simulation | Toggle network in tests | No check-ins lost or duplicated |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 36

- From a clean checkout, run the week 6 project and its tests with no undocumented steps.
- Explain three concepts from weeks 5–6 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 7: Testing and debugging

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Pure Kotlin unit tests | Test streak calculation | At least 15 cases green |
| 38 | Compose test rule, semantics and finders | Test toggle and add flow | UI automation stable |
| 39 | Fake repositories and controlled dispatcher | Simulate slow loading | Test avoids arbitrary sleeps |
| 40 | Layout Inspector and recomposition diagnostics | Find 2 wasteful recompositions | Before/after notes written |
| 41 | Accessibility tests, font scaling and contrast | Test at 200% font | No clipped crucial controls |
| 42 | Checkpoint 2: reliability suite | Run unit and UI tests from clean checkout | Green and documented |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 8: Device integrations

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Permissions and notification channels | Add opt-in daily reminders | App works when permission denied |
| 44 | Alarm scheduling choices and WorkManager | Pick policy appropriate to reminder accuracy | Behavior documented for background limits |
| 45 | System pickers and sharing intents | Export CSV through share sheet | Recipient gets valid content |
| 46 | Deep links and safe argument parsing | Open habit details from app link | Invalid ID handled safely |
| 47 | Localization resources and plural rules | Add second locale strings | Counters and dates formatted correctly |
| 48 | Project: device-ready tracker | Add reminders, export and deep link | Demo on emulator and physical device if available |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 48

- From a clean checkout, run the week 8 project and its tests with no undocumented steps.
- Explain three concepts from weeks 7–8 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 9: Performance, release and privacy

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Baseline performance and startup observation | Measure cold start | Reproducible measurement written |
| 50 | App bundle, release signing concepts and versioning | Create release build | Artifact installs on test device |
| 51 | Privacy and data minimization | Inventory stored data and logs | No sensitive habits in debug logs |
| 52 | App architecture review and package cleanup | Split UI/domain/data packages | UI has no direct database reference |
| 53 | CI Gradle test and lint | Add pipeline checks | Checks run without local IDE UI |
| 54 | Project: release candidate | Run smoke and accessibility testing | No critical issue on supported devices |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 10: Capstone delivery

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Write capstone user flows and acceptance tests | Specify 5 complete journeys | Priority, edge cases and screenshots listed |
| 56 | Build polished multi-screen tracker | Implement navigation, themes and state | Responsive and accessible UI |
| 57 | Finish Room persistence and streak logic | Cover tricky date boundaries | 20+ pure tests passing |
| 58 | Finish offline sync and reminder handling | Run simulated outage | User can recover safely |
| 59 | Build signed release variant and documentation | Create APK/AAB per distribution plan | Setup and limitations in README |
| 60 | Final capstone review | Demo habit creation, offline use and reminders | New tester completes journeys unassisted |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 60

- From a clean checkout, run the week 10 project and its tests with no undocumented steps.
- Explain three concepts from weeks 9–10 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Capstone evaluation rubric

| Area | Passing evidence |
|---|---|
| Functionality | All acceptance scenarios pass from a clean state. |
| Correctness | Automated unit/integration/UI tests target both normal and failure paths. |
| Security and reliability | Invalid input, secret handling, access boundaries and recovery have documented tests. |
| Design | Clear layer boundaries and sensible domain modeling; no unnecessary framework complexity. |
| Deployment | A new developer can install, build and run the project from `README.md`. |
| Portfolio | Repository, architecture diagram, screenshots/demo, decisions, known limitations and release tag. |

## End-of-roadmap portfolio checklist

- [ ] Every weekly project is committed and independently runnable.
- [ ] All checkpoints have dated evidence (notes/tests/screenshots).
- [ ] Capstone builds from a fresh clone without secrets or private files.
- [ ] README includes prerequisites, platform-specific commands, configuration template, testing, troubleshooting and deployment.
- [ ] Automated tests and manual accessibility/security checks are reported accurately.
- [ ] A five-minute demo and a versioned release or deployable artifact exist.

## Important scope and platform notes

Jetpack Compose is an Android UI toolkit, not an iOS UI toolkit. A Windows/Linux machine can build Android Compose apps. For iOS UI development use SwiftUI on macOS, or research Compose Multiplatform separately; do not assume Android UI components run on iOS.

## Official learning resources

| Resource | Link |
|---|---|
| Compose quick start | <https://developer.android.com/develop/ui/compose/setup> |
| Compose learning | <https://developer.android.com/courses/jetpack-compose/course> |
| Compose state | <https://developer.android.com/develop/ui/compose/state> |
| Compose navigation | <https://developer.android.com/develop/ui/compose/navigation> |
| Compose testing | <https://developer.android.com/develop/ui/compose/testing> |
| Android app architecture | <https://developer.android.com/topic/architecture> |

**Version check:** framework releases and developer tools change. Before installing or copying commands from this guide, check the official documentation above against the versions currently available on your computer.
