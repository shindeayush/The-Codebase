# React Roadmap: From Zero to Interactive Web Applications

*Updated: 29 October 2026 · 9 weeks · 54 sessions · approximately 171 guided hours*

## Start here

Build a tested, accessible and deployed client-side React/TypeScript app, understand state and effects, and be ready for Next.js.

This is a **standalone framework-learning guide** modeled on the earlier language roadmaps. You will build something in every session, deliberately debug failures, and verify completion against a concrete standard. The schedule assumes six study sessions per week; take longer when needed.

### What you will finish

- **One repository** with 54 named session folders or commits, a learning journal and milestone tags.
- **Weekly mini-projects** that progressively reuse concepts rather than disconnected tutorials.
- **A finished capstone** with tests, README, evidence of accessibility/security review, and delivery appropriate to this framework.

### Common prerequisites (Windows, Linux and macOS)

1. Install a current **Node.js LTS** that satisfies the chosen framework's official compatibility requirements; check `node --version` and `npm --version`. Avoid assuming that an older LTS is supported by every newly generated project.
2. Install Git and a code editor (VS Code is convenient); check `git --version`.
3. Know a little **HTML, CSS, modern JavaScript, modules, promises, `fetch`, npm, Git and browser DevTools**. Each guide includes a refresher, but a framework is not a substitute for learning those basics.
4. On **Windows**, use PowerShell or Windows Terminal; on **Linux/macOS**, use a normal shell. The npm commands below work on all three. Windows users do **not** need WSL.
5. Keep one Git repository for the roadmap and commit at the end of every session. Record three journal notes: *learned*, *confused*, *next action*.

### Start a React + TypeScript project

```bash
npm create vite@latest react-roadmap -- --template react-ts
cd react-roadmap
npm install
npm run dev
```

Use Vite here **to learn the React library directly**. Official React guidance recommends a framework for many production apps; the standalone Vite path deliberately teaches how routing, data fetching and deployment choices fit together. Avoid the obsolete Create React App workflow.

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

**Weekly outcome:** Build a catalog with filters, empty states and a cart count.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 1 | JavaScript/TypeScript refresher: `const`, arrays, objects, modules, arrow functions, promises. | Implement a searchable array-of-products script in TypeScript. | TypeScript catches a wrong property name before execution. |
| 2 | React as a UI library; Vite, `createRoot`, JSX, component files. | Replace Vite's starter with a heading, status card and three product cards. | App boots, hot reload works and every card is a component. |
| 3 | JSX rules, props, compositional UI, keys. | Build a reusable ProductCard receiving typed props. | Cards show distinct data and list items have stable keys. |
| 4 | Conditional rendering, list rendering, pure render logic. | Add empty-state, stock badge and filtered product grid. | Empty and populated lists render without crashes. |
| 5 | Events and local state with `useState`. | Add quantity buttons and an interactive favourites toggle. | Each click changes only the intended state. |
| 6 | Week 1 mini-project: interactive catalog. | Build a catalog with filters, empty states and a cart count. | Demo five interactions, commit and explain props vs state. |

**Week 1 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 2: sessions 7–12

**Weekly outcome:** Build editable cart, totals, filters and an accessible form.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 7 | State update patterns: immutable objects and arrays. | Add/remove cart lines and update quantities without mutation. | React rerenders correctly, including zero quantity. |
| 8 | Controlled inputs, form submission and validation. | Build a product-request form with inline errors. | Invalid values cannot submit; form is keyboard usable. |
| 9 | Sharing state: lifting state and callback props. | Synchronize search bar, filter chips and results count. | One source of truth controls all three views. |
| 10 | Component identity, keys, preservation and resetting state. | Reset an editor on product selection using a stable key. | Switching items never leaks the previous item's draft. |
| 11 | `useReducer` for nontrivial transitions. | Move cart behaviour into a reducer with explicit actions. | Each action is predictable and testable without React. |
| 12 | Week 2 mini-project: shopping-list app. | Build editable cart, totals, filters and an accessible form. | Reducer tests cover add, edit, remove and reset. |

**Week 2 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 3: sessions 13–18

**Weekly outcome:** Implement request lifecycle, search, detail panel and retry.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Effects vs render-time derivation; when you do NOT need an effect. | Remove unnecessary effects from earlier components. | No loops or redundant state synchronization remain. |
| 14 | `useEffect`: lifecycle, cleanup, dependencies and stale closures. | Build a clock/subscription that cleans up on unmount. | No stale listener or duplicated timer remains. |
| 15 | Fetch requests and async error/loading/empty states. | Retrieve public JSON with cancellation/abort logic. | Slow/error responses display helpful states. |
| 16 | Custom hooks and shared behaviour. | Extract `useLocalStorage` or `useDebouncedValue` with tests. | Two components reuse the hook without copied logic. |
| 17 | Refs and DOM interactions; `useRef` and focus. | Build a modal with initial focus and close behaviour. | Focus is managed and keyboard navigation works. |
| 18 | Week 3 mini-project: searchable remote directory. | Implement request lifecycle, search, detail panel and retry. | Network failures are recoverable; components clean up. |

**Week 3 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 4: sessions 19–24

**Weekly outcome:** Ship three pages, data forms and query-string filtering.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Client-side routing with React Router: routes, links, params. | Add Home, Catalog, Detail and Not Found routes. | Deep-link refresh works when hosting rewrite is configured. |
| 20 | Nested routes and URL query parameters. | Keep filter and sort state in the URL. | Shareable URLs restore the same catalog view. |
| 21 | Forms at scale: validation, accessible messages, submission status. | Make an edit form with field errors and save state. | Error text is associated with fields; double-submit blocked. |
| 22 | CSS architecture, responsive layout and component boundaries. | Implement mobile navigation and responsive cards. | No horizontal overflow at narrow widths. |
| 23 | Composition patterns: children, slots via props, avoidance of prop drilling. | Refactor a dashboard layout into flexible primitives. | New panel type needs no large conditional branch. |
| 24 | Week 4 mini-project: routed admin dashboard. | Ship three pages, data forms and query-string filtering. | Refresh, browser back and direct links all work. |

**Week 4 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 5: sessions 25–30

**Weekly outcome:** Build a small CRUD board with theme, persistence and rollback.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Context: appropriate use for theme and session metadata. | Build theme switcher with Context. | Components update without threading props through five layers. |
| 26 | State alternatives: local, URL, Context and server state. | Diagram data ownership for the dashboard. | Each value has a justified owner and update path. |
| 27 | Server-state fetching with a dedicated query library (optional). | Cache, refetch and invalidate a resources list. | Duplicate views do not trigger avoidable repeated fetches. |
| 28 | Optimistic UI and rollback design. | Optimistically mark a task complete, roll back on simulated failure. | Failure returns UI to correct state with a message. |
| 29 | Reusable design system: primitives, variants and accessibility. | Create Button, Dialog, Input and Alert components. | Each handles disabled/error/focus cases. |
| 30 | Week 5 mini-project: task board. | Build a small CRUD board with theme, persistence and rollback. | Add/edit/delete survives reload and failure handling is visible. |

**Week 5 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 6: sessions 31–36

**Weekly outcome:** Audit the task board and add tests for major flows.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Unit testing with Vitest and Testing Library. | Test counters, reducers and form behaviour. | At least 12 meaningful tests pass; one deliberately broken test fails. |
| 32 | Integration testing: network mocks and user interactions. | Test request errors and retry with mocked responses. | Tests validate behaviour, not component implementation details. |
| 33 | End-to-end testing with Playwright. | Cover add-to-cart, search, and deep links in a browser. | E2E tests work from a clean install and test environment. |
| 34 | Accessibility: semantics, labels, focus, contrast, screen readers. | Audit and fix keyboard-only navigation. | Major flows require no mouse and have clear focus. |
| 35 | Security basics: escaping, untrusted data, safe links and secrets. | Review user-rendered HTML, URLs and build variables. | No unsafe HTML injection; no client-side secrets. |
| 36 | Week 6 quality gate. | Audit the task board and add tests for major flows. | Unit/integration/E2E green and accessibility issues logged/fixed. |

**Week 6 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 7: sessions 37–42

**Weekly outcome:** Build a filterable report with lazy routes and typed data.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 37 | TypeScript props, unions, generics and narrowing. | Type component variants and API result states. | No `any` is needed in core feature code. |
| 38 | Performance: profiling before optimization; React DevTools. | Locate an avoidable rerender in a large list. | Record a before/after profile with a measured improvement. |
| 39 | Memoization: `memo`, `useMemo`, `useCallback` when justified. | Optimize just one measured bottleneck. | No blanket memoization; explain why this helps. |
| 40 | Code splitting with dynamic imports and lazy loading. | Lazy-load a report page with proper fallback. | Initial bundle excludes report module; fallback appears. |
| 41 | Error boundaries and resilient UI architecture. | Add an error boundary around a problematic panel. | A broken panel does not blank the whole application. |
| 42 | Week 7 mini-project: data-heavy UI. | Build a filterable report with lazy routes and typed data. | Profile and test an interaction with 500+ rows. |

**Week 7 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 8: sessions 43–48

**Weekly outcome:** Refactor and deploy report app with CI and accessibility checks.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Production builds, environment configuration, and static hosting. | Run `npm run build` and preview the built app. | The built app loads and no secret is embedded in it. |
| 44 | Deploy a client-only app with SPA fallback and HTTPS. | Publish a preview and test deep-link reload. | Shared URLs render correctly over HTTPS. |
| 45 | CI workflow for lint/type/test/build. | Add GitHub Actions for checks on pull requests. | A broken test causes red CI. |
| 46 | Release readiness: error reporting, analytics privacy, docs. | Add non-sensitive error logging and README instructions. | New user can install and run the app from README. |
| 47 | Review and architecture: optional Next.js comparison. | Write what React does and what full-stack frameworks add. | Explain routing/data/rendering/deployment tradeoffs. |
| 48 | Week 8 mini-project: production hardening. | Refactor and deploy report app with CI and accessibility checks. | Working URL, build output and release notes. |

**Week 8 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 9: sessions 49–54

**Weekly outcome:** Ask someone to try five tasks, fix top three bugs, tag `react-v1`.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Capstone plan: specify users, entities, pages, interactions, risks. | Scope a product management SPA with 5 measurable outcomes. | One-page spec and wireframes committed. |
| 50 | Capstone core: routes, navigation and design system. | Implement home, list, detail and create/edit flows. | Pages navigate and accept realistic data. |
| 51 | Capstone state, remote data and resilience. | Add persistence, loading/error states and reliable mutations. | All CRUD flows tolerate offline/error simulation. |
| 52 | Capstone tests, accessibility and performance. | Add 20+ tests and 3 browser flows, profile main screen. | Quality checks pass and keyboard use is demonstrated. |
| 53 | Capstone delivery: CI, hosting, documentation. | Publish app, record screenshots and architecture note. | Live URL plus reproducible README in repository. |
| 54 | Final checkpoint: user acceptance and retrospective. | Ask someone to try five tasks, fix top three bugs, tag `react-v1`. | Stranger completes core tasks with README and live app. |

**Week 9 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

## Checkpoints: do not skip the gates

If a gate fails, repeat only the weak exercises. Do not move to more advanced dependencies with untested fundamentals.

| Gate | After session | Evidence required | If missing |
|---|---:|---|---|
| Checkpoint 0 | 6 | Build a catalog with filters, empty states and a cart count. **Pass:** Demo five interactions, commit and explain props vs state. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 1 | 18 | Implement request lifecycle, search, detail panel and retry. **Pass:** Network failures are recoverable; components clean up. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 2 | 36 | Audit the task board and add tests for major flows. **Pass:** Unit/integration/E2E green and accessibility issues logged/fixed. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 3 | 48 | Refactor and deploy report app with CI and accessibility checks. **Pass:** Working URL, build output and release notes. | Rebuild the weakest feature and repeat the tests or demo. |
| Capstone | 54 | Ask someone to try five tasks, fix top three bugs, tag `react-v1`. **Pass:** Stranger completes core tasks with README and live app. | Rebuild the weakest feature and repeat the tests or demo. |

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

After the capstone: learn **Next.js** for server rendering and full-stack features; **React Native / Expo** for mobile; or a mature React Router framework for integrated data and routing.

## Reference resources (official-first)

These are starting points, not a promise that every heading or command stays unchanged. Prefer the documentation version matching the installed packages. Checked against official references in October 2026.

| Resource | URL |
|---|---|
| React Learn | https://react.dev/learn |
| React: build an app from scratch | https://react.dev/learn/build-a-react-app-from-scratch |
| Vite | https://vite.dev/guide/ |
| React Router | https://reactrouter.com/ |
| React Testing Library | https://testing-library.com/docs/react-testing-library/intro/ |
| Vitest | https://vitest.dev/guide/ |
| Playwright | https://playwright.dev/docs/intro |
| TypeScript Handbook | https://www.typescriptlang.org/docs/handbook/intro.html |

## Final self-assessment

- [ ] I can set up the project on my own OS from a clean folder.
- [ ] I can explain the main component model and how data changes affect rendering.
- [ ] I can trace errors from user action to state, data layer and output.
- [ ] I know which data must remain trusted/server-side/privileged (where applicable).
- [ ] I can demonstrate accessibility and failure recovery, not only the happy path.
- [ ] I can reproduce tests and a production build or package without copy-pasting a tutorial.
- [ ] Another person can use my final project from its README and release instructions.
