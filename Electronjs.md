# Electron Roadmap: From Zero to Secure Cross-Platform Desktop Apps

*Updated: 29 October 2026 · 10 weeks · 60 sessions · approximately 190 guided hours*

## Start here

Build, test, package and distribute a secure offline-first desktop app for Windows, Linux and macOS, with a narrow preload API and correct OS integration.

This is a **standalone framework-learning guide** modeled on the earlier language roadmaps. You will build something in every session, deliberately debug failures, and verify completion against a concrete standard. The schedule assumes six study sessions per week; take longer when needed.

### What you will finish

- **One repository** with 60 named session folders or commits, a learning journal and milestone tags.
- **Weekly mini-projects** that progressively reuse concepts rather than disconnected tutorials.
- **A finished capstone** with tests, README, evidence of accessibility/security review, and delivery appropriate to this framework.

### Common prerequisites (Windows, Linux and macOS)

1. Install a current **Node.js LTS** that satisfies the chosen framework's official compatibility requirements; check `node --version` and `npm --version`. Avoid assuming that an older LTS is supported by every newly generated project.
2. Install Git and a code editor (VS Code is convenient); check `git --version`.
3. Know a little **HTML, CSS, modern JavaScript, modules, promises, `fetch`, npm, Git and browser DevTools**. Each guide includes a refresher, but a framework is not a substitute for learning those basics.
4. On **Windows**, use PowerShell or Windows Terminal; on **Linux/macOS**, use a normal shell. The npm commands below work on all three. Windows users do **not** need WSL.
5. Keep one Git repository for the roadmap and commit at the end of every session. Record three journal notes: *learned*, *confused*, *next action*.

### Start a native Electron Forge project

```bash
npx create-electron-app@latest electron-roadmap --template=vite-typescript
cd electron-roadmap
npm start
```

The official Forge guide documents this template; check its current options if the CLI changes. On Linux, some packages required for Electron and building native modules may need installing using your distro's package manager. **Native installers and signing are platform-specific**: you can develop on each OS, but do not assume one OS can correctly sign/package every other OS. **Never** enable unrestricted Node integration in a remote renderer merely to make an exercise easier.

## Before the first day

**Quick self-check:** Explain a JavaScript function, array `map`, an object, an ES module import, `async`/`await`, event handling, a CSS class, and a Git commit. If those are unfamiliar, spend 2–4 preparation sessions on JavaScript, HTML and CSS first. You can still start here, but the timeline will stretch.

### Optional Week 0 — JavaScript/TypeScript bridge (not included in the session total)

| Session | Learn | Build | Done when |
|---:|---|---|---|
| P1 | HTML & CSS | Create a semantic card, form with labels, responsive 2-column layout | Keyboard reaches all fields and layout works at 320px |
| P2 | JavaScript values/objects | Write add/update/remove functions for an array of records | Functions do not accidentally mutate caller-owned arrays |
| P3 | Modules/events/DOM | Split a page into modules and implement a form event | ES imports and event handlers work without global script state |
| P4 | Promises and fetch | Request sample JSON and show loading/error/empty states | Promise errors are handled and cancelled where relevant |
| P5 | TypeScript basics | Define union types/interfaces and narrow unknown data | Incorrect field access is caught by compiler |
| P6 | Node/npm/Git/devtools | Install dependency, debug one error, commit and revert change | You can reproduce setup with README and Git |

## How each session works

A **day means one learning session**, not necessarily a calendar day. Work through the sessions in order; if you study several technologies at once, resume from where you left off. Sessions 1–5 of each week take about **3 hours**; every sixth session is a **4-hour project and review**.

| Minutes | Phase | Action |
|---:|---|---|
| 10 | Recall | Rebuild a tiny idea from the previous session without notes. |
| 40 | Learn | Read the listed official reference, try examples, and take short notes. |
| 90 | Build | Implement the exercise without copying finished solutions. |
| 30 | Break and debug | Deliberately cause a bug; inspect DevTools, logs, errors and tests to explain it. |
| 10 | Save | Run checks, commit code, and write three lines in `journal.md`. |

The daily blocks total 180 minutes. On project/review days, reserve four hours for building, manual checks, tests and cleanup. A session is **done** when the stated criterion is demonstrated, checks pass, code is committed and you can explain the important lines. For accessibility and security tasks, do not mark them done merely because the UI appears to work.

**Rules:** Type the code yourself; ask for explanations rather than paste-ready solutions. Use current stable dependencies, keep secrets out of Git, follow the official docs if a CLI prompt changes, and keep project scope small enough to finish the review days. Fix failed checkpoints before progressing.

## The complete session roadmap

### Week 1: sessions 1–6

**Weekly outcome:** Build two-screen app showing OS and app version safely.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 1 | JavaScript/TypeScript and Node basics; desktop app architecture. | Diagram main, renderer and preload responsibilities. | Explain why renderer cannot have unrestricted filesystem access. |
| 2 | Electron Forge project, scripts, Chromium and Node. | Scaffold a native app and change title, icon placeholder and window. | Runs locally with one command on your OS. |
| 3 | BrowserWindow basics, app readiness and lifecycle. | Create one settings window with platform-appropriate close behaviour. | App exits/retains process appropriately by OS. |
| 4 | Preload script, contextBridge and isolated API. | Expose a safe `getAppVersion()` method to renderer. | `nodeIntegration` remains off; context isolation on. |
| 5 | Main/renderer DevTools and debugging. | Deliberately fail main and renderer code; inspect logs separately. | Identify origin and fix both errors. |
| 6 | Week 1 mini-project: desktop welcome app. | Build two-screen app showing OS and app version safely. | Works on host platform with no security warnings. |

**Week 1 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 2: sessions 7–12

**Weekly outcome:** Create file picker and settings panel via narrow bridge.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 7 | IPC one-way messages and event validation. | Send theme selection from renderer to main via dedicated channel. | Unrecognized messages are ignored safely. |
| 8 | IPC request/response with `invoke` and `handle`. | Implement safe `chooseFolder()` through native dialog. | Only expected return data reaches renderer. |
| 9 | Validate IPC sender and arguments; narrow channel surface. | Reject arbitrary paths and untrusted input. | Crafted invalid message is denied without crash. |
| 10 | Preload types with TypeScript and API contract. | Type `window.desktopAPI` and implement focused methods. | Typecheck catches wrong method signatures. |
| 11 | Async IPC and safe error handling. | Show progress/error for slow file operation. | App never freezes on recoverable failure. |
| 12 | Week 2 checkpoint: safe IPC utility. | Create file picker and settings panel via narrow bridge. | Security audit verifies isolation, sandbox and validation. |

**Week 2 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 3: sessions 13–18

**Weekly outcome:** Build local notes with open/save/autosave and recovery.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Node filesystem APIs in main process only. | Read a user-selected text file using safe main handler. | Renderer cannot directly call fs. |
| 14 | File save dialog, overwrite and cancellation semantics. | Add Save As for notes document. | Cancel does not create unintended file. |
| 15 | Structured storage vs files, schema versioning. | Build settings repository with versioned JSON data. | Corrupt settings recover safely with backup/error. |
| 16 | Autosave, debouncing and atomic writes. | Implement save-to-temp then rename for app data. | Simulated interruption does not corrupt last valid file. |
| 17 | App directories, `app.getPath` and OS differences. | Store settings in appropriate user-data directory. | No writes into installed app files. |
| 18 | Week 3 mini-project: offline notes editor. | Build local notes with open/save/autosave and recovery. | Data persists after relaunch; failure cases explained. |

**Week 3 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 4: sessions 19–24

**Weekly outcome:** Add native UX integrations to notes app.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Native menus, accelerators and keyboard commands. | Add Open, Save and Undo menu items. | Shortcuts match host conventions and disabled states. |
| 20 | System dialogs, confirmations and unsaved changes. | Prompt before destructive close, handle cancellation. | No unsaved data lost by normal close. |
| 21 | Clipboard and controlled shell integration. | Add Copy Link and safe external browser open. | Arbitrary untrusted URL is not launched. |
| 22 | Tray and notifications with permission awareness. | Create optional background tray and reminder. | Works where supported; unsupported mode degrades gracefully. |
| 23 | Deep links or custom protocols: input validation. | Handle one sanitized `myapp://note/id` link. | Invalid IDs and unexpected schemes are rejected. |
| 24 | Week 4 mini-project: desktop productivity app. | Add native UX integrations to notes app. | Open/save/menu/tray operations covered by manual test plan. |

**Week 4 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 5: sessions 25–30

**Weekly outcome:** Integrate preview, undo, menus and theme.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Renderer UI architecture: vanilla or React/Vue/Svelte optional. | Separate components, state and desktop API client. | Renderer remains a replaceable web UI layer. |
| 26 | State models, undo history and immutable data. | Implement undo/redo document actions. | Changes revert predictably across multiple edits. |
| 27 | Custom window management and multiwindow messages. | Add secondary preview window with controlled IPC. | Data shared without exposing Node APIs. |
| 28 | Accessibility for desktop windows. | Keyboard navigation, menus and announced errors. | Main workflow is fully keyboard operable. |
| 29 | CSS layouts, scaling, high DPI and theming. | Add responsive split-pane editor with dark/light modes. | Usable at 125–200% display scale. |
| 30 | Week 5 mini-project: polished offline editor. | Integrate preview, undo, menus and theme. | Test every workflow on at least two display sizes. |

**Week 5 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 6: sessions 31–36

**Weekly outcome:** Index large notes safely with cancellation/recovery.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Streams and large file handling. | Add chunked loading and show progress for large files. | UI remains responsive for a 50 MB test file. |
| 32 | Worker threads / utility processes for CPU work. | Move text indexing off renderer/main UI thread. | Main window stays responsive during indexing. |
| 33 | Cancellation, timeouts and process cleanup. | Let user cancel indexing, abort work safely. | No worker left alive after cancel/exit. |
| 34 | Crash handling, logging and private diagnostic data. | Add structured logs without document contents. | Crash has useful report and no leaked sensitive text. |
| 35 | Settings and release migration. | Migrate v1 settings to v2 schema with tests. | Old settings load and new settings remain valid. |
| 36 | Week 6 checkpoint: reliability benchmark. | Index large notes safely with cancellation/recovery. | Timing and memory data documented; 10+ tests. |

**Week 6 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 7: sessions 37–42

**Weekly outcome:** Conduct full Electron security checklist and tests.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Electron security model: renderer vs trusted main. | Threat model file import, links and IPC. | List trust boundaries and attack paths. |
| 38 | Content Security Policy and secure protocols. | Define restrictive CSP and validate local loading. | Avoid unnecessary permissive directives. |
| 39 | Navigation/window restrictions and permission handlers. | Block untrusted navigation, popups and permissions. | Malicious test URL cannot open privileged window. |
| 40 | Supply chain security, lockfiles and dependency review. | Audit dependencies and review install scripts. | Build reproducible from lockfile. |
| 41 | Safe handling of remote content and updates. | Keep external links in system browser and isolate untrusted content. | No remote web page can invoke desktop bridge. |
| 42 | Week 7 security gate. | Conduct full Electron security checklist and tests. | All critical checks pass; violations have evidence/fixes. |

**Week 7 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 8: sessions 43–48

**Weekly outcome:** Set up tests and GitHub Actions on available OS runners.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Unit testing main-process utilities and schema logic. | Add Vitest tests for validation, paths and migrations. | 20 tests pass in CI-friendly environment. |
| 44 | IPC contract tests with mock event senders. | Test sender verification and malformed payloads. | Every exposed IPC method has a denial test. |
| 45 | Renderer component and accessibility tests. | Test settings, editor and error UI. | Behaviour tests pass without starting Electron. |
| 46 | End-to-end Electron tests with Playwright Electron support. | Automate launch, open, edit, save and restart. | Tests run on chosen runner/platform. |
| 47 | Cross-platform test matrix: paths, keyboards and permissions. | Write a Windows/macOS/Linux compatibility checklist. | Platform assumptions documented; tested where possible. |
| 48 | Week 8 quality gate. | Set up tests and GitHub Actions on available OS runners. | Build and tests green on target platforms. |

**Week 8 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 9: sessions 49–54

**Weekly outcome:** Package and smoke-test notes app, write install instructions.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Forge packaging and artifact formats. | Build native package/installer for current OS. | Installed app launches outside dev directory. |
| 50 | Icons, resources, app metadata, licenses. | Add correct icons and About/license data. | Packaged app includes identifiers and credits. |
| 51 | Code signing and notarization concepts. | Plan Windows signing and macOS signing/notarization for distribution. | Requirements documented; not falsely claimed signed. |
| 52 | Auto-update strategy and release channels. | Create update trust model and release metadata plan. | User-approved update path with rollback described. |
| 53 | Release builds, CI artifacts, OS-specific packaging. | Produce artifacts on matching OS CI runners where possible. | Each artifact tested on its target OS or clearly labeled untested. |
| 54 | Week 9 release candidate. | Package and smoke-test notes app, write install instructions. | Installer opens, saves files, and can uninstall cleanly. |

**Week 9 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 10: sessions 55–60

**Weekly outcome:** Have tester do five tasks, fix top three failures, tag `electron-v1`.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Capstone definition: offline-first desktop research notebook. | Plan search, tabs, import/export, settings and recovery. | Five measurable goals and a threat model committed. |
| 56 | Capstone core UI and document model. | Implement workspace, tabs and document management. | Main tasks work end-to-end with clean typed APIs. |
| 57 | Capstone indexing, persistence and native integration. | Add import/export, safe IPC and cancellable search. | 100+ documents indexed without frozen UI. |
| 58 | Capstone tests, security and accessibility. | Run IPC attack tests, 20+ unit tests and E2E workflow. | No unsafe bridge; keyboard-only use works. |
| 59 | Capstone packaging, docs and screenshots. | Create installer, README, release notes and platform checklist. | Another tester installs and opens documents. |
| 60 | Final user acceptance and tag. | Have tester do five tasks, fix top three failures, tag `electron-v1`. | Installable documented application with passing checks. |

**Week 10 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

## Checkpoints: do not skip the gates

If a gate fails, repeat only the weak exercises. Do not move to more advanced dependencies with untested fundamentals.

| Gate | After session | Evidence required | If missing |
|---|---:|---|---|
| Checkpoint 0 | 6 | Build two-screen app showing OS and app version safely. **Pass:** Works on host platform with no security warnings. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 1 | 12 | Create file picker and settings panel via narrow bridge. **Pass:** Security audit verifies isolation, sandbox and validation. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 2 | 18 | Build local notes with open/save/autosave and recovery. **Pass:** Data persists after relaunch; failure cases explained. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 3 | 36 | Index large notes safely with cancellation/recovery. **Pass:** Timing and memory data documented; 10+ tests. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 4 | 42 | Conduct full Electron security checklist and tests. **Pass:** All critical checks pass; violations have evidence/fixes. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 5 | 48 | Set up tests and GitHub Actions on available OS runners. **Pass:** Build and tests green on target platforms. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 6 | 54 | Package and smoke-test notes app, write install instructions. **Pass:** Installer opens, saves files, and can uninstall cleanly. | Rebuild the weakest feature and repeat the tests or demo. |
| Capstone | 60 | Have tester do five tasks, fix top three failures, tag `electron-v1`. **Pass:** Installable documented application with passing checks. | Rebuild the weakest feature and repeat the tests or demo. |

## Deliberate debugging practice

- During early weeks, deliberately create a syntax error, a bad import, a missing prop/input, a wrong key or state reference. Explain the resulting message rather than deleting code until it works.
- During middle weeks, trigger an error response, a race between requests, an invalid form, an inaccessible control and a route that does not exist. Trace it end-to-end.
- During advanced weeks, test failed authorization, missing/expired credentials, unexpected large data, an unresponsive process or slow network, as relevant to the platform. Never test systems you do not own or have permission to test.
- At every checkpoint, confirm type checking, automated tests and a fresh production/package build, using commands supplied by the scaffold and installed tools.

## Your final portfolio evidence

- Source code and a README with setup, exact commands, screenshots and feature list.
- A short architecture overview: boundaries, state ownership, data flow, errors and security considerations.
- Tests and a CI workflow appropriate to the project, plus manual accessibility and error-handling checks.
- A release, live deployment or packaged installer as appropriate; if distribution is OS-specific, say exactly which systems you tested.
- At least one real user test: five tasks, issues found, fixes made, and a version tag.

## What comes next

After the capstone: focus on **updates and signed releases**, **native addons and OS integration**, or **advanced desktop security/reliability**. React/Vue/Svelte can power the renderer, but none replaces the process model.

## Reference resources (official-first)

These are starting points, not a promise that every heading or command stays unchanged. Prefer the documentation version matching the installed packages. Checked against official references in October 2026.

| Resource | URL |
|---|---|
| Electron Quick Start | https://www.electronjs.org/docs/latest/tutorial/quick-start |
| Electron Process Model | https://www.electronjs.org/docs/latest/tutorial/process-model |
| Electron Security | https://www.electronjs.org/docs/latest/tutorial/security |
| Electron IPC | https://www.electronjs.org/docs/latest/tutorial/ipc |
| Electron Context Isolation | https://www.electronjs.org/docs/latest/tutorial/context-isolation |
| Electron Forge | https://www.electronforge.io/ |
| Electron Testing | https://www.electronjs.org/docs/latest/tutorial/automated-testing |
| Playwright Electron | https://playwright.dev/docs/api/class-electron |

## Final self-assessment

- [ ] I can set up the project on my own OS from a clean folder.
- [ ] I can explain the main component model and how data changes affect rendering.
- [ ] I can trace errors from user action to state, data layer and output.
- [ ] I know which data must remain trusted/server-side/privileged (where applicable).
- [ ] I can demonstrate accessibility and failure recovery, not only the happy path.
- [ ] I can reproduce tests and a production build or package without copy-pasting a tutorial.
- [ ] Another person can use my final project from its README and release instructions.
