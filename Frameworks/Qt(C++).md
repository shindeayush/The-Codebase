# Qt Roadmap: From Zero to Cross-Platform C++ Desktop Applications

**72 sessions | 12 study weeks | approximately 228 hours | created October 29, 2026**

This roadmap is a standalone, project-based guide to Qt. Each “Day” below is a **study session**, not necessarily a calendar day. The finish line is **Cross-platform inventory desktop app** with editable model/view table, SQLite persistence, import/export, asynchronous work, settings, search, accessibility, automated Qt Test checks and packages for at least the host OS.

## Start here

**Prerequisites and the beginner bridge.** C++ fundamentals including classes, RAII, references, standard containers and lambdas, plus basic CMake. First week bridges core C++ to Qt.

**Operating systems.** Windows, Linux, macOS supported. Windows: match installed Qt kits with MSVC or MinGW compiler; macOS: install Xcode Command Line Tools; Linux: use compatible GCC/Clang plus X11/Wayland development libraries as required by packages.

**Installation.** Use Qt Online Installer and Qt Creator with a supported Qt 6 kit. Choose Qt Widgets + CMake for the main track, plus a Qt Quick/QML exploration week later. Run Hello World using the IDE Run button; `cmake --build` from a properly configured build directory for CLI builds.

### First run

```text
Qt Online Installer → install Qt 6 + matching compiler kit + Qt Creator
Qt Creator → File → New Project → Application → Qt Widgets Application
Build system: CMake
Select supported Desktop Qt kit → Build → Run
Terminal (after CMake configuration, platform-specific):
  cmake --build build
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
qt-roadmap/
  README.md
  journal.md
  week-01/
  week-02/
  ...
  capstone/
```

Keep one Git commit per session, a runnable example for every topic, short notes on bugs and fixes, and a README in each weekly project. Use version control; never commit passwords, credentials or production database files.

## Week 1: C++ to Qt basics

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Modern C++ ownership and signals overview | Rebuild small Item data class | RAII and tests clean |
| 2 | Qt Creator, kits, Qt modules and CMake | Create Widgets project | Build runs on host desktop |
| 3 | QApplication, QWidget, QMainWindow | Display main window with status bar | Window resizes without crash |
| 4 | QString, QVariant and QVector basics | Convert and format inventory entry | Unicode item names round-trip |
| 5 | QObject parent/child lifetime | Allocate widgets with parent ownership | No double delete or leak |
| 6 | Project: inventory main shell | Build menu/toolbar/status layout | GUI launches and closes cleanly |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 2: Widgets and layouts

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | QVBoxLayout/QHBoxLayout/QGridLayout | Build responsive entry form | Fields resize sensibly |
| 8 | QLineEdit/QSpinBox/QComboBox validation | Create input form for SKU/quantity | Bad SKU rejected |
| 9 | QAction, toolbar, shortcuts | Add New/Open/Save actions | Keyboard shortcuts work |
| 10 | Signals/slots, typed connect syntax | Connect add/remove buttons | Changes emitted exactly once |
| 11 | QDialog and message boxes | Implement edit item modal | Cancel leaves state unchanged |
| 12 | Project: in-memory inventory UI | Add/edit/delete 50 items | Mouse and keyboard workflows usable |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 12

- From a clean checkout, run the week 2 project and its tests with no undocumented steps.
- Explain three concepts from weeks 1–2 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 3: Model/View programming

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | QAbstractItemModel basics and separation | Map items to QTableView | Sorting not tied to storage order |
| 14 | QAbstractTableModel data/rowCount/columnCount | Implement 5-column table | Correct display and header labels |
| 15 | QSortFilterProxyModel | Add text search and sort | All rows stable through edits |
| 16 | Model mutation beginInsertRows/endInsertRows | Insert/delete without resetting model | View and selection correct |
| 17 | Delegates and editable cells | Edit quantity with validation | Invalid edit does not corrupt row |
| 18 | Project: searchable inventory grid | Replace ad-hoc widget list with model | 500 items scroll without UI lag |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 4: Persistence and tests

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | QStandardPaths and file system paths | Save app settings under correct directory | No hardcoded home paths |
| 20 | QSettings and app preferences | Store window size and columns | Relaunch restores layout |
| 21 | Qt SQL with SQLite and prepared queries | Save items to database | Inputs cannot alter SQL statement |
| 22 | Database migrations and transactions | Add categories + stock log | Rollback tested |
| 23 | Qt Test for model and signals | Test 15 model operations | Headless tests deterministic |
| 24 | Checkpoint 1: desktop inventory | Build UI+SQLite from requirements | Restart and test suite pass |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 24

- From a clean checkout, run the week 4 project and its tests with no undocumented steps.
- Explain three concepts from weeks 3–4 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 5: Graphics and richer UI

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | QPainter and custom QWidget | Draw low-stock indicator | High-DPI rendering looks sharp |
| 26 | QIcon, resources .qrc and fonts | Add scalable application icons | Assets available after packaging |
| 27 | Drag-and-drop with MIME | Reorder categories | Unsupported data type rejected |
| 28 | Clipboard and keyboard UX | Copy selected SKU/table cells | Clipboard output correct |
| 29 | Accessibility names, labels and focus | Audit tab order and screen reader labels | Complete inventory creation keyboard-only |
| 30 | Project: polished inventory UI | Add iconography and responsive pane | Good font scaling and focus order |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 6: Async work and network

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Event loop and queued signals | Explain UI thread and background tasks | UI stays responsive during work |
| 32 | QThread vs QThreadPool/QtConcurrent | Move CSV processing off main thread | No GUI access from worker |
| 33 | Cancellation and progress reporting | Import 10k rows with progress | Cancel leaves consistent state |
| 34 | QNetworkAccessManager and async replies | Fetch optional product metadata mock | Timeout/error state displayed |
| 35 | JSON parsing with QJsonDocument/QJsonObject | Validate remote payload | Malformed records skipped with error list |
| 36 | Project: bulk CSV import/export | Add background progress and rollback | Handles 100k rows without freezing UI |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 36

- From a clean checkout, run the week 6 project and its tests with no undocumented steps.
- Explain three concepts from weeks 5–6 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 7: Robust app architecture

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Repository/service separation | Move SQL and validation out of view | Logic covered by headless tests |
| 38 | Undo/redo with QUndoStack | Undo item rename/quantity update | Undo never loses data |
| 39 | Logging categories and diagnostics | Add log captures with request/item ID | Failure can be traced |
| 40 | Internationalization with tr()/Qt Linguist | Localize 2 key screens | Translation switched successfully |
| 41 | Theme and stylesheets tradeoffs | Offer light/dark palettes | Contrast passes manual check |
| 42 | Checkpoint 2: maintainable desktop app | Test undo, imports and settings | 25+ tests green |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 8: Qt Quick and alternative UI

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Qt Quick scene graph vs QWidget | Compare architecture for same layout | Explain tradeoff without mixing layers |
| 44 | QML Item, Rectangle, Text and anchors | Create small stock overview QML page | No binding loops |
| 45 | QML properties, bindings and signals | Add QML counter | Reactive binding updates correctly |
| 46 | Expose C++ model to QML safely | Render same stock stats in QML | One source of truth |
| 47 | Qt Quick Controls style choices | Build settings screen prototype | Works with keyboard |
| 48 | Project: Qt Quick prototype | Replicate inventory dashboard view | Document Widgets vs QML decision |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 48

- From a clean checkout, run the week 8 project and its tests with no undocumented steps.
- Explain three concepts from weeks 7–8 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 9: Cross-platform and security

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Windows/macOS/Linux path separators and platform APIs | Test app data paths | No platform-specific absolute path |
| 50 | File picker, sandboxing and permissions | Import through dialog | Invalid path denied without crash |
| 51 | Untrusted files and resource limits | Fuzz malformed CSV/JSON test inputs | Parser fails gracefully |
| 52 | Cross-platform CI with supported runners | Build and test two host OS targets | Both jobs green or documented blockers |
| 53 | Dependency licenses and Qt licensing options | Inventory modules/plugins/license obligations | Distribution plan legally reviewed |
| 54 | Project: two-OS build | Build app on second OS or CI runner | UI smoke tests documented |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 10: Profiling, packaging and delivery

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Qt Creator profiler and event loop delays | Measure slow filter operation | Fixed bottleneck with before/after |
| 56 | SQLite indexing and memory usage | Optimize 100k-row search | Query plan and latency recorded |
| 57 | Windows windeployqt, macOS macdeployqt, Linux deployment | Create host-native package | Runs without developer IDE on test machine |
| 58 | Installer signing, permissions and update policy | Write release checklist | Dependencies included and provenance clear |
| 59 | Crash reporting and privacy | Create safe diagnostic report | Personal SKU notes not logged |
| 60 | Checkpoint 3: release candidate | Package binary and demo on clean user profile | No missing plugin/platform errors |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 60

- From a clean checkout, run the week 10 project and its tests with no undocumented steps.
- Explain three concepts from weeks 9–10 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 11: Capstone: full inventory system

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 61 | Define domain fields, import format and acceptance tests | Create 12 user journeys | Business constraints measurable |
| 62 | Build repository, model and transactional editing | Finish SQLite backend | Model/repository tests green |
| 63 | Build responsive UI, search and action/undo | Finish daily workflows | Keyboard-only tests pass |
| 64 | Build import/export async pipeline | Process large file and cancel | Data invariant and responsiveness maintained |
| 65 | Finish settings, resources, localization and packages | Produce release candidate | Installs and launches on host OS |
| 66 | Project: beta test with another user | Observe complete inventory flow | Three usability issues fixed |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 12: Capstone quality and extension

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 67 | Audit model/view and memory ownership | Remove unnecessary resets and raw pointers | No lifetime crash under repeated open/close |
| 68 | Automate packaging on host and CI | Produce signed or appropriately labeled unsigned artifact | Builds traceable to git tag |
| 69 | Run crash, corrupt-file and low-disk simulations | Recover with explanatory errors | Original database remains consistent |
| 70 | Measure performance on realistic file sizes | Benchmark import and filtering | Results included in README |
| 71 | Create architecture diagram and support manual | Document Qt kit, CMake, DB and licensing | Developer reproduces build |
| 72 | Final capstone release and review | Publish installable app, screenshots and tests | Stranger can run with no Qt Creator installed |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 72

- From a clean checkout, run the week 12 project and its tests with no undocumented steps.
- Explain three concepts from weeks 11–12 without notes and identify one failure path you tested.
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

Qt Widgets/C++ is the primary track. Qt Quick/QML is a distinct UI option, not a requirement for all Qt apps. CMake kits, Qt plugins and compiler ABIs must match. For distribution, consult Qt license obligations and platform-specific deployment tooling before shipping.

## Official learning resources

| Resource | Link |
|---|---|
| Qt getting started | <https://doc.qt.io/qt-6/gettingstarted.html> |
| Qt installation | <https://doc.qt.io/qt-6/get-and-install-qt.html> |
| Qt with CMake | <https://doc.qt.io/qt-6/cmake-get-started.html> |
| Qt Widgets | <https://doc.qt.io/qt-6/qtwidgets-index.html> |
| Qt Core | <https://doc.qt.io/qt-6/qtcore-index.html> |
| Qt Quick/QML | <https://doc.qt.io/qt-6/qtquick-index.html> |
| Qt Test | <https://doc.qt.io/qt-6/qtest-overview.html> |

**Version check:** framework releases and developer tools change. Before installing or copying commands from this guide, check the official documentation above against the versions currently available on your computer.
