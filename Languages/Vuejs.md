# Vue Roadmap: From Zero to Reactive Web Applications

*Updated: 29 October 2026 · 9 weeks · 54 sessions · approximately 171 guided hours*

## Start here

Build a reactive, typed Vue 3 SPA using Single-File Components, Composition API, Vue Router, Pinia, automated testing and deployment.

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

### Start a Vue project

```bash
npm create vue@latest
# Enter project name: vue-roadmap
cd vue-roadmap
npm install
npm run dev
```

At the prompts, select **TypeScript**, **Vue Router**, **Pinia**, **Vitest**, and a suitable end-to-end testing option (for example Playwright). You may add features incrementally if overwhelmed. The primary syntax in this guide is **Composition API with `<script setup>`**; learn the Options API later to read older code.

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

**Weekly outcome:** Build accessible grid, filters and item counter.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Modern JavaScript, templates and reactive UI overview. | Make a plain JavaScript product grid to compare approaches. | Explain what Vue automates compared with manual DOM updates. |
| 2 | Create Vue app, `.vue` single-file components and `<script setup>`. | Generate project and replace starter with a profile card. | Dev server and production build work. |
| 3 | Template expressions and directives `v-if`, `v-for`, `v-bind`. | Render product cards with stock and category labels. | Every branch and empty list behaves correctly. |
| 4 | Events with `v-on`, modifiers and handlers. | Build counter, dismissible banner and dropdown. | Events do not unexpectedly bubble or reload page. |
| 5 | `ref`, `.value`, `computed` and template unwrapping. | Add live search and computed filtered results. | Results update without manual DOM mutation. |
| 6 | Week 1 mini-project: catalog. | Build accessible grid, filters and item counter. | Reusable SFCs, stable list keys and committed demo. |

**Week 1 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 2: sessions 7–12

**Weekly outcome:** Add/edit/archive items with calculated totals.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 7 | `reactive` vs `ref` and mutation patterns. | Compare nested form state with ref-backed primitives. | You can explain when `.value` is required. |
| 8 | Computed vs watchers: side effects and cleanup. | Replace inappropriate watchers with computed derivations. | No duplicated derived state or infinite loops. |
| 9 | `watch`, `watchEffect` and async cleanup. | Fetch dependent records when a filter changes. | Fast filter changes never show stale response. |
| 10 | Forms with `v-model` and modifiers. | Build edit-product form and validation warnings. | Inputs reflect state and errors are linked to labels. |
| 11 | Lifecycle hooks and DOM template refs. | Implement focus after mounting an edit panel. | No stale subscription after unmount. |
| 12 | Week 2 mini-project: inventory editor. | Add/edit/archive items with calculated totals. | Validation catches bad inputs and state remains coherent. |

**Week 2 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 3: sessions 13–18

**Weekly outcome:** Build five reusable accessible primitives in demo app.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Props, typing, defaults and one-way data flow. | Build configurable alert and item row components. | Parent owns source of truth; no prop mutation. |
| 14 | Emits and custom component `v-model`. | Implement SearchBox and RatingInput components. | Two-way interface is explicit and typed. |
| 15 | Slots, named slots and component composition. | Create CardLayout with title/actions/content slots. | Consumers customize layout without copying markup. |
| 16 | Provide/inject for scoped shared dependencies. | Provide settings in a nested feature subtree. | Configuration changes flow without global singleton. |
| 17 | Reusable composables and refactoring. | Extract `usePagination` and `useLocalStorage`. | Unit tests cover composable behaviour separately. |
| 18 | Week 3 mini-project: component library. | Build five reusable accessible primitives in demo app. | Variants, slots, emits and focus behaviour documented. |

**Week 3 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 4: sessions 19–24

**Weekly outcome:** Add create/edit pages and query-string search.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Vue Router fundamentals, links and route params. | Create catalog, item detail and dashboard pages. | Direct URLs and browser back work. |
| 20 | Nested routes, guards and route query parameters. | Persist search and page number in URL. | Sharing a URL recreates the same view. |
| 21 | Forms and schema validation. | Implement new-item flow with server-like validation rules. | Invalid values cannot be persisted. |
| 22 | Accessibility and keyboard navigation. | Build dialog with focus return and error announcements. | Major flows usable without mouse. |
| 23 | Responsive styling and CSS scoped styles. | Adjust layout to mobile and desktop widths. | No overflow and focus indicators remain visible. |
| 24 | Week 4 mini-project: routed management interface. | Add create/edit pages and query-string search. | Refresh, routes, form and mobile views tested. |

**Week 4 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 5: sessions 25–30

**Weekly outcome:** Integrate Pinia, router, remote data and editing.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Pinia stores: state, getters, actions and store boundaries. | Move cart and favourites to focused stores. | Store logic is reusable and components stay simple. |
| 26 | Store composition, async actions and persistence tradeoffs. | Make store load and save cart from local storage. | Reset and reload behave predictably. |
| 27 | Fetch APIs with loading, error, empty and retry states. | Create fake API-backed products service. | Network failures don't leave UI in loading forever. |
| 28 | Request deduplication/caching and stale data strategies. | Implement caching or use a query library if useful. | Cached data refreshed intentionally after edits. |
| 29 | Error handling, validation and safe rendering. | Audit untrusted strings and external URLs. | No use of unsafe HTML for arbitrary user content. |
| 30 | Week 5 mini-project: shopping admin panel. | Integrate Pinia, router, remote data and editing. | Cross-page updates and failure recovery demonstrated. |

**Week 5 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 6: sessions 31–36

**Weekly outcome:** Add checks to CI and improve existing mini-project.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Vitest unit tests for functions/composables/stores. | Write 15 tests for cart totals and pagination. | A broken expectation fails immediately. |
| 32 | Vue Test Utils and component interaction tests. | Test custom inputs, emits and error messages. | Tests assert user-visible behaviour. |
| 33 | Mocked network and async race tests. | Reproduce request cancellation and retry. | Latest request wins; failures recover. |
| 34 | Playwright browser testing. | Cover routes, add/edit flow and keyboard navigation. | All browser tests pass from a clean state. |
| 35 | Manual accessibility and performance audit. | Inspect semantic labels, contrast and bundle output. | All critical issues recorded and fixed. |
| 36 | Week 6 quality gate. | Add checks to CI and improve existing mini-project. | Lint, typecheck, build and tested flows pass. |

**Week 6 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 7: sessions 37–42

**Weekly outcome:** Build charts, filters and a large virtualized or paginated list.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 37 | TypeScript for SFCs, typed props and emits. | Convert complex components and store actions. | Wrong event payloads trigger type errors. |
| 38 | Advanced composables: generic data and dependency injection. | Create reusable typed `useResource` helper. | Helper works for two result types safely. |
| 39 | Vue reactivity traps: destructuring, deep watchers, effect scope. | Build small demonstrations and fix an actual bug. | Explain why destructured reactive values can lose tracking. |
| 40 | Lazy routes, async components and Suspense caveats. | Lazy-load an analytics page. | Build shows route split and fallback works. |
| 41 | Profiling and computed performance. | Profile 1,000-item filter, improve if necessary. | Before/after measurement documents an actual gain. |
| 42 | Week 7 mini-project: analytics frontend. | Build charts, filters and a large virtualized or paginated list. | Usable on midrange device; perf results recorded. |

**Week 7 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 8: sessions 43–48

**Weekly outcome:** Release production-ready inventory app.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Production configuration and runtime vs build-time env values. | Create `.env.example` and build release assets. | No credentials appear in browser bundle. |
| 44 | Deploy SPA and configure history-route fallback. | Publish a hosted build and test nested URL refresh. | Deep link loads correctly over HTTPS. |
| 45 | Security and privacy: auth boundary and permission awareness. | Write threats and fake role-specific screens. | You explicitly state server must enforce authorization. |
| 46 | Documentation, component API, maintenance and upgrade plan. | Write architecture and dependency map. | New contributor can locate store, route and service layers. |
| 47 | CI, logs and release checklist. | Add GitHub Actions and run clean build/test. | Broken test blocks release. |
| 48 | Week 8 deployment review. | Release production-ready inventory app. | Live link, green CI, README and known-issues list. |

**Week 8 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 9: sessions 49–54

**Weekly outcome:** Invite outside user to perform five tasks, fix three issues, tag `vue-v1`.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Capstone specification: multi-page inventory workspace. | Define five user tasks and screen sketches. | Small scoped requirements and accessibility criteria. |
| 50 | Capstone implementation: components, router and forms. | Implement list/detail/edit and shared UI primitives. | Users finish creation/editing without broken links. |
| 51 | Capstone implementation: stores, API simulation and errors. | Implement reliable persistence, loading states and retry. | Data survives reload and controlled failures. |
| 52 | Capstone verification: 20+ tests and user journeys. | Run unit, component and browser tests plus keyboard audit. | Passes locally and in CI. |
| 53 | Capstone performance, polish and deployment. | Profile, optimize only bottlenecks, publish and document. | Live usable app with architecture diagram and README. |
| 54 | Final checkpoint. | Invite outside user to perform five tasks, fix three issues, tag `vue-v1`. | App can be run and understood from README alone. |

**Week 9 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

## Checkpoints: do not skip the gates

If a gate fails, repeat only the weak exercises. Do not move to more advanced dependencies with untested fundamentals.

| Gate | After session | Evidence required | If missing |
|---|---:|---|---|
| Checkpoint 0 | 6 | Build accessible grid, filters and item counter. **Pass:** Reusable SFCs, stable list keys and committed demo. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 1 | 18 | Build five reusable accessible primitives in demo app. **Pass:** Variants, slots, emits and focus behaviour documented. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 2 | 30 | Integrate Pinia, router, remote data and editing. **Pass:** Cross-page updates and failure recovery demonstrated. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 3 | 36 | Add checks to CI and improve existing mini-project. **Pass:** Lint, typecheck, build and tested flows pass. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 4 | 48 | Release production-ready inventory app. **Pass:** Live link, green CI, README and known-issues list. | Rebuild the weakest feature and repeat the tests or demo. |
| Capstone | 54 | Invite outside user to perform five tasks, fix three issues, tag `vue-v1`. **Pass:** App can be run and understood from README alone. | Rebuild the weakest feature and repeat the tests or demo. |

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

After the capstone: learn **Nuxt** for SSR/full-stack Vue; build a **Vue component library**; or explore **Vue for progressive enhancement** inside an existing site.

## Reference resources (official-first)

These are starting points, not a promise that every heading or command stays unchanged. Prefer the documentation version matching the installed packages. Checked against official references in October 2026.

| Resource | URL |
|---|---|
| Vue Guide | https://vuejs.org/guide/introduction.html |
| Vue Quick Start | https://vuejs.org/guide/quick-start.html |
| Vue Reactivity | https://vuejs.org/guide/essentials/reactivity-fundamentals.html |
| Vue Router | https://router.vuejs.org/ |
| Pinia | https://pinia.vuejs.org/ |
| Vue Test Utils | https://test-utils.vuejs.org/ |
| Vitest | https://vitest.dev/guide/ |
| Nuxt | https://nuxt.com/docs |

## Final self-assessment

- [ ] I can set up the project on my own OS from a clean folder.
- [ ] I can explain the main component model and how data changes affect rendering.
- [ ] I can trace errors from user action to state, data layer and output.
- [ ] I know which data must remain trusted/server-side/privileged (where applicable).
- [ ] I can demonstrate accessibility and failure recovery, not only the happy path.
- [ ] I can reproduce tests and a production build or package without copy-pasting a tutorial.
- [ ] Another person can use my final project from its README and release instructions.
