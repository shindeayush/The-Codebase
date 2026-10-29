# SwiftUI Roadmap: From Zero to Native Apple Platform Apps

**60 sessions | 10 study weeks | approximately 190 hours | created October 29, 2026**

This roadmap is a standalone, project-based guide to SwiftUI. Each “Day” below is a **study session**, not necessarily a calendar day. The finish line is **Personal reading journal for iPhone and iPad** with searchable book records, SwiftData persistence, sync-ready repository, accessible adaptive navigation, widgets or sharesheet (optional), tests and an archive-ready release build.

## Start here

**Prerequisites and the beginner bridge.** Swift fundamentals (structs, enums, optionals, protocols, closures, concurrency). Swift language refresh occupies week 1.

**Operating systems.** **macOS with Xcode is required** to develop, preview, simulator-test and package native SwiftUI apps for Apple platforms. Windows/Linux can study Swift language and model code, but cannot complete this SwiftUI UI track natively. A physical iPhone is optional for most lessons.

**Installation.** On a Mac, install current stable Xcode from Mac App Store, accept tool license, install target simulators, and create a new iOS App template (SwiftUI + Swift). Choose a simulator supported by the installed Xcode; verify canvas, run and test targets. Apple IDs/distribution memberships may be required for some device signing or App Store actions.

### First run

```text
Xcode → File → New → Project → iOS App
Interface: SwiftUI • Language: Swift
Run on a supported iPhone simulator using ▶
Add a Swift Testing / XCTest target (according to project template)
Start with:
  struct ContentView: View {
      var body: some View { Text("Hello SwiftUI") }
  }
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
swiftui-roadmap/
  README.md
  journal.md
  week-01/
  week-02/
  ...
  capstone/
```

Keep one Git commit per session, a runnable example for every topic, short notes on bugs and fixes, and a README in each weekly project. Use version control; never commit passwords, credentials or production database files.

## Week 1: Swift and SwiftUI quickstart

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Swift value types, optionals, enums and protocol review | Implement Book/ReadingStatus | Pure model code tests pass |
| 2 | Xcode, simulator, SwiftUI App lifecycle | Boot sample app | App launches in simulator without warnings |
| 3 | View and Text/Button primitives | Build book status tile | Preview and runtime match |
| 4 | VStack/HStack/ZStack and Spacer | Compose reading dashboard | Layout renders on small device |
| 5 | Modifiers and reusable view components | Extract BookCard | No duplicated layout code |
| 6 | Project: static reading dashboard | Build home, empty and detail previews | Fonts adapt to Dynamic Type |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 2: State and bindings

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | @State and view invalidation | Make reading goal stepper | Changes immediately visible |
| 8 | @Binding and extracted child controls | Create favorite toggle row | Parent remains source of truth |
| 9 | @Observable and observation model | Move bookshelf data to observable model | State updates work across screens |
| 10 | Computed values and derived state | Show reading progress percentage | No duplicated mutable value |
| 11 | Task and onChange lifecycle | Load sample books asynchronously | Avoid double calls on appearance |
| 12 | Project: interactive bookshelf | Add/remove/favorite book entries | State survives navigation while app runs |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 12

- From a clean checkout, run the week 2 project and its tests with no undocumented steps.
- Explain three concepts from weeks 1–2 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 3: Navigation and layout adaptation

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | NavigationStack and type-safe destinations | Add library and book detail navigation | Back navigation consistent |
| 14 | Sheets, dialogs and alerts | Add new-book form | Cancel leaves data unchanged |
| 15 | List/ForEach stable identity | Show 200 books with insertions | State/animation remains stable |
| 16 | Grid and adaptive layout | Create iPad split/grid variant | No content cut off in portrait/landscape |
| 17 | Toolbar, menus and search field | Add library search and filter | Keyboard and pointer navigation usable |
| 18 | Project: polished library browser | Combine adaptive navigation and search | Works iPhone and iPad simulators |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 4: Accessibility, design and testing

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Dynamic Type, VoiceOver, traits and labels | Audit book card and form | Every control discoverable with VoiceOver |
| 20 | Color schemes, materials, contrast | Design dark/light themes | Text remains legible |
| 21 | Swift Testing/XCTest unit tests | Test progress and sorting rules | 15 edge tests pass |
| 22 | UI tests, launch arguments and test data | Automate add/favorite/search | No dependence on network timing |
| 23 | Debug previews, state and instrument basics | Diagnose 3 UI glitches | Root-cause notes captured |
| 24 | Checkpoint 1: three-screen reader | Rebuild with state and accessibility | UI/unit suite green |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 24

- From a clean checkout, run the week 4 project and its tests with no undocumented steps.
- Explain three concepts from weeks 3–4 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 5: Persistence with SwiftData

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | @Model and model container | Define Book and ReadingSession | Data saved to store |
| 26 | @Query and model context changes | List filtered persisted books | Updates appear after save |
| 27 | Relationships, uniqueness and migrations | Add reading sessions to book | Migration plan written and verified |
| 28 | Repository isolation and preview sample data | Make in-memory preview storage | Previews never use real data |
| 29 | Persistence errors and user-facing recovery | Surface failed save | No silent data loss |
| 30 | Project: offline reading journal | Add book CRUD and sessions | Relaunch retains every entry |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 6: Networking and concurrency

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | URLSession async/await and Codable | Fetch optional public book metadata | Timeout and malformed JSON handled |
| 32 | MainActor and isolation concepts | Update UI after fetch | Thread sanitizer/issues avoided |
| 33 | Task cancellation and debounce | Search as user types | Old result never overrides new query |
| 34 | Cache/offline-first approach | Cache fetched metadata | Network-off mode remains usable |
| 35 | Credential/privacy boundaries | Avoid storing tokens in UserDefaults | Sensitive values kept in suitable secure storage |
| 36 | Project: online enrichment | Add optional search/import metadata | Core offline mode fully functional |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 36

- From a clean checkout, run the week 6 project and its tests with no undocumented steps.
- Explain three concepts from weeks 5–6 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 7: Rich interactions

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Animation and transitions | Animate reading progress | Reduced-motion honored |
| 38 | Gestures and drag/drop | Reorder reading queue | VoiceOver alternative remains |
| 39 | Charts overview (Apple Charts when available) | Show reading sessions over week | Labels readable by assistive tech |
| 40 | PhotosPicker or file import | Attach optional cover image | Permission cancellations safe |
| 41 | Sharing/export via ShareLink | Export reading summary | Shared text contains correct title and dates |
| 42 | Checkpoint 2: polished journal | Run interactions + export tests | 20+ targeted assertions green |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 8: System integration

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | App storage and preferences | Implement reading goal setting | Settings persist as intended |
| 44 | Notifications and authorization | Add opt-in reading reminder | Denied permission doesn't break app |
| 45 | Scene lifecycle and background behavior | Save in-progress form on scene change | Data available after resume |
| 46 | Deep links with validation | Open book ID from URL | Invalid IDs show safe fallback |
| 47 | Widgets or app intents optional introduction | Create compact reading statistic widget | No private info visible inadvertently |
| 48 | Project: device integrated journal | Test reminders, sharing and links | Verified on simulator; device if available |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 48

- From a clean checkout, run the week 8 project and its tests with no undocumented steps.
- Explain three concepts from weeks 7–8 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 9: Performance and release quality

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Instruments and runtime profiling | Find slow large-library render | Before/after timings recorded |
| 50 | Data migrations and test fixtures | Upgrade mock schema | Existing book history preserved |
| 51 | Localization and pluralization | Add second locale | Date/time and plurals correct |
| 52 | App privacy and accessibility audits | Validate data inventory and labels | Issues tracked and fixed |
| 53 | Release signing, archive and TestFlight concepts | Produce Archive build | Signing/release requirements documented |
| 54 | Project: release candidate | Create test-ready build and checklist | New tester navigates all flows |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 10: Capstone and portfolio

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Define personas, goals and functional spec | Write 10 journeys and wireframes | Scope accessible and realistic |
| 56 | Complete books, sessions and search | Finish data UI | Clean migration and edit tests |
| 57 | Complete network enrichment and offline fallback | Mock endpoint and cache | Failure modes tested |
| 58 | Complete adaptive layouts and accessibility | Audit iPhone/iPad + VoiceOver | All core operations reachable |
| 59 | Prepare archive, release notes and CI where possible | Publish source/test results and screenshots | Build reproducible on supported Xcode |
| 60 | Final capstone review | Demo journal from empty library to report | Teammate can open and run via README |

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

Use Apple’s current **Develop in Swift** tutorials; the old “Introducing SwiftUI” tutorial itself warns that its examples no longer reflect current practices. SwiftUI is not natively supported as a Windows/Linux UI development target; do not promise an iOS simulator on those systems.

## Official learning resources

| Resource | Link |
|---|---|
| Develop in Swift (current tutorials) | <https://developer.apple.com/tutorials/develop-in-swift/> |
| SwiftUI resources | <https://developer.apple.com/swiftui/resources/> |
| SwiftUI docs | <https://developer.apple.com/documentation/swiftui/> |
| Human Interface Guidelines | <https://developer.apple.com/design/human-interface-guidelines/> |
| Swift concurrency | <https://docs.swift.org/swift-book/documentation/the-swift-programming-language/concurrency/> |
| Swift Testing | <https://developer.apple.com/documentation/testing/> |

**Version check:** framework releases and developer tools change. Before installing or copying commands from this guide, check the official documentation above against the versions currently available on your computer.
