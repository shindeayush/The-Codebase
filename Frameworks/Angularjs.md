# Angular Roadmap: From Zero to Enterprise Web Applications

*Updated: 29 October 2026 · 12 weeks · 72 sessions · approximately 228 guided hours*

## Start here

Build and deploy a large, typed Angular application using standalone components, signals, RxJS, routing, forms, services, testing and optional SSR.

This is a **standalone framework-learning guide** modeled on the earlier language roadmaps. You will build something in every session, deliberately debug failures, and verify completion against a concrete standard. The schedule assumes six study sessions per week; take longer when needed.

### What you will finish

- **One repository** with 72 named session folders or commits, a learning journal and milestone tags.
- **Weekly mini-projects** that progressively reuse concepts rather than disconnected tutorials.
- **A finished capstone** with tests, README, evidence of accessibility/security review, and delivery appropriate to this framework.

### Common prerequisites (Windows, Linux and macOS)

1. Install a current **Node.js LTS** that satisfies the chosen framework's official compatibility requirements; check `node --version` and `npm --version`. Avoid assuming that an older LTS is supported by every newly generated project.
2. Install Git and a code editor (VS Code is convenient); check `git --version`.
3. Know a little **HTML, CSS, modern JavaScript, modules, promises, `fetch`, npm, Git and browser DevTools**. Each guide includes a refresher, but a framework is not a substitute for learning those basics.
4. On **Windows**, use PowerShell or Windows Terminal; on **Linux/macOS**, use a normal shell. The npm commands below work on all three. Windows users do **not** need WSL.
5. Keep one Git repository for the roadmap and commit at the end of every session. Record three journal notes: *learned*, *confused*, *next action*.

### Start an Angular workspace

```bash
npm install -g @angular/cli
ng new angular-roadmap --routing --style=scss
cd angular-roadmap
ng serve --open
```

Follow the CLI prompts for optional settings; default Angular projects use **standalone components** and newer **signals** APIs. On Windows PowerShell, a restrictive script-execution policy can block global CLI launchers; use the official Angular setup guidance rather than changing security settings blindly. Use an **Angular-supported Node LTS version**, not just any recent Node release.

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

**Weekly outcome:** Build responsive catalog with cards and filter.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 1 | HTML/CSS/TypeScript refresher: interfaces, classes, modules, strictness. | Write typed item model and collection filters. | Types catch wrong fields and nullable values. |
| 2 | Angular CLI, workspace, standalone components and file layout. | Generate and run Angular app with routing. | `ng serve`, `ng build` work. |
| 3 | Components, templates, interpolation, event binding. | Build dashboard and status card components. | Template reflects state and responds to events. |
| 4 | Property/attribute/class/style binding. | Build reusable progress indicator and variant button. | DOM attributes and classes reflect state. |
| 5 | Modern template control flow `@if`, `@for`, `@switch`. | Build inventory list with empty/loading states. | Stable tracking keys and correct branches. |
| 6 | Week 1 mini-project: basic dashboard. | Build responsive catalog with cards and filter. | Lint/build pass and every UI state demonstrable. |

**Week 1 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 2: sessions 7–12

**Weekly outcome:** Build item selection, editing, totals and preferences.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Writable `signal`, `.set` and `.update`. | Build cart quantity and selection signals. | Updates are immutable where needed and visible. |
| 8 | `computed` signals and derived state. | Calculate item total, count and filtered list. | No manual duplicate-value synchronization. |
| 9 | Inputs and outputs for component interaction. | Create typed editor and reusable summary widget. | Parent-child contract works without direct mutation. |
| 10 | `effect` for imperative integrations only. | Sync one preference with local storage. | Derived data uses `computed`, not effect loops. |
| 11 | Template references, view queries and focus. | Focus editor after opening panel. | No focus lost and keyboard navigation works. |
| 12 | Week 2 mini-project: reactive inventory panel. | Build item selection, editing, totals and preferences. | Signals manage view without stale duplicate state. |

**Week 2 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 3: sessions 13–18

**Weekly outcome:** Build five typed reusable UI elements with demos.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Dependency injection: `inject`, providers and service lifetimes. | Create inventory service and mock implementation. | Components depend on contract, not global variables. |
| 14 | Component lifecycle and teardown. | Start/stop a live status feed safely. | No listener left active after navigation. |
| 15 | Directives and pipes: built-in and custom uses. | Create currency/summary formatting and status directive. | Behaviour reusable and independently tested. |
| 16 | Content projection, templates and reuse. | Create a generic card with projected header/actions. | Consumers can add custom content without inheritance. |
| 17 | Feature organization, naming and component responsibilities. | Split large dashboard into standalone feature components. | No 500-line all-in-one component. |
| 18 | Week 3 mini-project: component library. | Build five typed reusable UI elements with demos. | Inputs/outputs, focus and documentation complete. |

**Week 3 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 4: sessions 19–24

**Weekly outcome:** Add nested routed admin and detail pages.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Router: routes, router outlet and links. | Add Home, Items and Settings pages. | Deep links navigate without full reload. |
| 20 | Route parameters, query parameters and URL state. | Add searchable item detail pages and filter state. | Refresh preserves current filter and item. |
| 21 | Nested routes, lazy loading and route guards. | Create admin area and lazy-load its feature. | Bundles split and routes resolve correctly. |
| 22 | Guards vs real authorization security boundary. | Simulate restricted navigation plus server check design. | Explain why guards alone do not protect data. |
| 23 | Router resolvers and route error/loading patterns. | Load item detail and handle missing IDs. | Invalid route has intentional error state. |
| 24 | Week 4 mini-project: multi-page item workspace. | Add nested routed admin and detail pages. | Back, deep-link refresh and invalid routes tested. |

**Week 4 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 5: sessions 25–30

**Weekly outcome:** Build multi-section product editor with tests.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Reactive Forms: `FormControl`, groups and validators. | Build typed new-item form. | Invalid fields block submission with associated errors. |
| 26 | Cross-field validators and custom validation. | Add date range/quantity consistency rules. | Every rule covered by positive and negative examples. |
| 27 | Form arrays and dynamic controls. | Add editable list of item variants. | Add/remove does not confuse input values. |
| 28 | Signal Forms overview (optional, if stable per docs). | Compare supported forms approaches with tiny prototype. | Choose based on documented stability and requirements. |
| 29 | Async submit states, server validation, accessible errors. | Prevent duplicate requests and show rejection. | Form remains usable on slow or failed submit. |
| 30 | Week 5 mini-project: structured form workflow. | Build multi-section product editor with tests. | Validation, focus and draft recovery work. |

**Week 5 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 6: sessions 31–36

**Weekly outcome:** Add search, editor and server-style persistence.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 31 | HttpClient setup, request/response types and errors. | Fetch remote catalog and render states. | Network failure does not crash dashboard. |
| 32 | RxJS essentials: Observable, subscribe, map, switchMap. | Search API with cancellation/debounce. | Outdated requests never overwrite current query. |
| 33 | Interop: signals and observables. | Model server stream and view state appropriately. | Cleanup is correct; explain signal vs Observable. |
| 34 | HTTP interceptors and request metadata. | Add correlation ID and safe error mapping. | No private data logged or copied to UI. |
| 35 | Service contracts, mock back end and retries. | Implement typed CRUD service with controlled retry. | Retry only safe operations or explicitly justified writes. |
| 36 | Week 6 checkpoint: API-backed management app. | Add search, editor and server-style persistence. | 12 tests and manual network-failure demonstration. |

**Week 6 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 7: sessions 37–42

**Weekly outcome:** Add reusable state service and robust persistence.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Feature-local state vs shared service state. | Diagram state ownership for current app. | No duplicated source of truth between components. |
| 38 | Signal-based state services and computed selectors. | Implement cart store service with focused actions. | Unit tests cover state transitions. |
| 39 | Async state and caching; avoiding race conditions. | Add stale-data indicator and manual refresh. | Data becomes fresh deliberately after save. |
| 40 | Advanced RxJS: `combineLatest`, `catchError`, `shareReplay` tradeoffs. | Combine filter, sort and server response. | Errors recovered and no accidental repeated requests. |
| 41 | Optimistic update strategy and rollback. | Update one item optimistically with rejection handling. | Failed save restores correct data with notice. |
| 42 | Week 7 mini-project: shared state dashboard. | Add reusable state service and robust persistence. | Cross-page totals consistent with server responses. |

**Week 7 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 8: sessions 43–48

**Weekly outcome:** Add CI for build, tests and E2E as feasible.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Unit tests with CLI default runner and TestBed. | Test signals, services and validators. | 15 tests run in clean environment. |
| 44 | Component tests with mocked providers. | Test item editor and error messages. | User-visible behaviour asserted, not internals. |
| 45 | HttpTestingController / HTTP tests per current Angular docs. | Test requests, invalid data and retries. | No real internet required during tests. |
| 46 | Playwright end-to-end setup for Angular. | Automate add/edit/search and route refresh. | Browser flows pass with seeded test data. |
| 47 | Accessibility audit: focus, labels, semantics and ARIA. | Fix keyboard issues across forms and dialogs. | Main workflow works without mouse. |
| 48 | Week 8 quality checkpoint. | Add CI for build, tests and E2E as feasible. | CI red on deliberately failed test, green when fixed. |

**Week 8 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 9: sessions 49–54

**Weekly outcome:** Build secured-looking workspace with i18n and reusable UI.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Security basics: XSS protection, safe templates and trusted values. | Audit innerHTML and user-provided strings. | Arbitrary user HTML is not trusted. |
| 50 | Auth flow, interceptors and server-side permission checks. | Add mock authenticated state and route policy. | State alone cannot authorize sensitive requests. |
| 51 | Lazy-loaded features and standalone route architecture. | Split admin feature into chunks. | Lazy chunk not loaded on landing page. |
| 52 | Libraries, workspaces and design-system organization. | Extract reusable library or standalone components folder. | New feature imports stable public interfaces. |
| 53 | Internationalization, locale-aware date and number formatting. | Add a second locale to reports view. | Dates/currency format correctly for both locales. |
| 54 | Week 9 mini-project: enterprise feature area. | Build secured-looking workspace with i18n and reusable UI. | Requirements and security boundaries documented. |

**Week 9 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 10: sessions 55–60

**Weekly outcome:** Publish preview with SSR where appropriate and budgets.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Rendering modes: SPA, SSR and prerender choices. | Compare project under client and server render strategies. | Explain SEO and hydration tradeoffs. |
| 56 | Angular SSR setup per current CLI and hydration. | Add SSR to an appropriate public landing page. | No `window`/document access during SSR. |
| 57 | Performance: OnPush concepts, signal granularity, profiling. | Profile large table and reduce unnecessary work. | Before/after evidence of improvement. |
| 58 | Deferrable views and lazy media where applicable. | Defer analytics widget outside initial viewport. | Initial load excludes heavy widget. |
| 59 | SEO metadata, images and caching. | Add title and description plus optimized image assets. | Metadata and largest visual render correctly. |
| 60 | Week 10 mini-project: performant public dashboard. | Publish preview with SSR where appropriate and budgets. | Demonstrate budget checks and browser hydration. |

**Week 10 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 11: sessions 61–66

**Weekly outcome:** Produce documented release candidate with tests.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 61 | Architecture patterns: domain feature boundaries and dependencies. | Refactor service and route boundaries. | Feature modules do not import each other's internals. |
| 62 | State decision guide: signals vs RxJS vs larger state libraries. | Write decision matrix for two apps. | Every state tool has a specific justified role. |
| 63 | Production error handling and logging hygiene. | Add error boundary strategy and privacy-conscious diagnostics. | No credentials or personally sensitive content in logs. |
| 64 | Deployment, configuration and CI/CD. | Publish app and verify direct-route support. | HTTPS URL works and CI green. |
| 65 | Maintenance: dependency upgrades, migration notes and versioning. | Simulate updating one library in feature branch. | Tests, build, changelog and rollback steps preserved. |
| 66 | Week 11 architecture checkpoint. | Produce documented release candidate with tests. | Outside reviewer can navigate code and build app. |

**Week 11 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 12: sessions 67–72

**Weekly outcome:** Deploy, have tester perform tasks, fix top three bugs, tag `angular-v1`.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 67 | Final capstone scope: enterprise project management portal. | Define roles, entities, routes, forms, search and metrics. | One-page spec, design, six acceptance criteria. |
| 68 | Capstone feature build: routing, components and shared design. | Implement project listing, detail and staff views. | All key deep links and UI controls work. |
| 69 | Capstone data build: services, forms, state and security design. | Integrate CRUD, filtering, validation and permission checks. | Server rules enforced where a real backend exists. |
| 70 | Capstone advanced: SSR/performance, loading and errors. | Optimize key public page and harden failure states. | Measured load result plus error recovery. |
| 71 | Capstone QA and docs: 25 tests, four browser flows and CI. | Build release README, architecture map and user guide. | All critical flows and accessibility checks pass. |
| 72 | Final checkpoint: publish and user-test. | Deploy, have tester perform tasks, fix top three bugs, tag `angular-v1`. | Clean repo builds and real user completes core workflows. |

**Week 12 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

## Checkpoints: do not skip the gates

If a gate fails, repeat only the weak exercises. Do not move to more advanced dependencies with untested fundamentals.

| Gate | After session | Evidence required | If missing |
|---|---:|---|---|
| Checkpoint 0 | 6 | Build responsive catalog with cards and filter. **Pass:** Lint/build pass and every UI state demonstrable. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 1 | 18 | Build five typed reusable UI elements with demos. **Pass:** Inputs/outputs, focus and documentation complete. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 2 | 36 | Add search, editor and server-style persistence. **Pass:** 12 tests and manual network-failure demonstration. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 3 | 48 | Add CI for build, tests and E2E as feasible. **Pass:** CI red on deliberately failed test, green when fixed. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 4 | 60 | Publish preview with SSR where appropriate and budgets. **Pass:** Demonstrate budget checks and browser hydration. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 5 | 66 | Produce documented release candidate with tests. **Pass:** Outside reviewer can navigate code and build app. | Rebuild the weakest feature and repeat the tests or demo. |
| Capstone | 72 | Deploy, have tester perform tasks, fix top three bugs, tag `angular-v1`. **Pass:** Clean repo builds and real user completes core workflows. | Rebuild the weakest feature and repeat the tests or demo. |

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

After the capstone: study **Nx/monorepos**, **state architecture at scale**, **Angular libraries/design systems**, or **advanced SSR and performance**. Learn legacy NgModule patterns as maintenance knowledge, not as the default new-project architecture.

## Reference resources (official-first)

These are starting points, not a promise that every heading or command stays unchanged. Prefer the documentation version matching the installed packages. Checked against official references in October 2026.

| Resource | URL |
|---|---|
| Angular Introduction | https://angular.dev/overview |
| Angular Installation | https://angular.dev/installation |
| Angular CLI | https://angular.dev/tools/cli |
| Angular Signals | https://angular.dev/guide/signals |
| Angular Router | https://angular.dev/guide/routing |
| Angular Forms | https://angular.dev/guide/forms |
| Angular HTTP Client | https://angular.dev/guide/http |
| Angular Testing | https://angular.dev/guide/testing |
| Angular SSR | https://angular.dev/guide/ssr |

## Final self-assessment

- [ ] I can set up the project on my own OS from a clean folder.
- [ ] I can explain the main component model and how data changes affect rendering.
- [ ] I can trace errors from user action to state, data layer and output.
- [ ] I know which data must remain trusted/server-side/privileged (where applicable).
- [ ] I can demonstrate accessibility and failure recovery, not only the happy path.
- [ ] I can reproduce tests and a production build or package without copy-pasting a tutorial.
- [ ] Another person can use my final project from its README and release instructions.
