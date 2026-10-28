# Svelte Roadmap: From Zero to SvelteKit Web Applications

*Updated: 29 October 2026 · 9 weeks · 54 sessions · approximately 171 guided hours*

## Start here

Learn modern Svelte 5 reactivity and use SvelteKit to deliver a progressive-enhanced, secure, tested and deployed full-stack app.

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

### Start a SvelteKit project

```bash
npx sv create svelte-roadmap
cd svelte-roadmap
npm install
npm run dev
```

Select **TypeScript** and convenient lint/test tools at the prompts; if the exact CLI questions change, follow the [official setup guide](https://svelte.dev/docs/kit/creating-a-project). This roadmap uses **Svelte 5 runes** (`$state`, `$derived`, `$props`, `$effect`) instead of treating legacy `$:` syntax as the default. SvelteKit is used for routes/server features, not confused with the Svelte component compiler.

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

**Weekly outcome:** Build add/edit/delete/filter with local component state.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 1 | JS/TS fundamentals; Svelte compiler vs runtime rendering. | Create plain JS button and compare with a Svelte component. | Explain component compilation and browser updates. |
| 2 | Svelte project via `sv`, `.svelte` file anatomy. | Scaffold TypeScript-enabled project and replace starter. | Dev and production builds complete. |
| 3 | Markup expressions, events and component styles. | Build accessible counter and notification panel. | Buttons work and styles remain isolated. |
| 4 | Svelte 5 `$state` and reactive updates. | Create editable shopping list with `$state`. | Mutations update UI without manual DOM changes. |
| 5 | `$derived` and pure computed state. | Compute subtotal, filtering and low-stock count. | Derived values stay correct with every edit. |
| 6 | Week 1 mini-project: shopping list. | Build add/edit/delete/filter with local component state. | Empty and large lists work, committed. |

**Week 1 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 2: sessions 7–12

**Weekly outcome:** Build form, card, dropdown and list demos.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 7 | `$props` and typed component APIs. | Build reusable ItemRow and Badge components. | Type errors appear for wrong props. |
| 8 | Event callbacks and component communication in Svelte 5. | Lift cart changes to parent with callback props. | One source of truth controls total and rows. |
| 9 | Conditional, keyed each blocks and transitions. | Animate adding/removing cards with stable keys. | No incorrect preserved state on reorder. |
| 10 | Bindings, forms, focus and validation. | Create interactive settings form with linked errors. | Input, error and keyboard behaviour are correct. |
| 11 | Snippets and component composition. | Build configurable panel with reusable content snippets. | No duplicated card structure across views. |
| 12 | Week 2 mini-project: component showcase. | Build form, card, dropdown and list demos. | Props, callback events and keyboard states documented. |

**Week 2 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 3: sessions 13–18

**Weekly outcome:** Build editable directory with clean reactive data ownership.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 13 | `$effect` for genuine side effects and cleanup. | Sync theme preference to local storage. | No state-propagation feedback loop. |
| 14 | State modules, `.svelte.ts` and shared state boundaries. | Extract a typed cart state helper. | State works in two components without global leaks. |
| 15 | Lifecycle/browser-only logic and SSR awareness. | Add resize observation with cleanup. | No browser-global access during server rendering. |
| 16 | Async requests and loading/errors. | Fetch list with cancellation and retry. | Rapid changes cannot show stale results. |
| 17 | TypeScript, stores vs runes and migration awareness. | Convert a small legacy store example to runes. | Explain when stores remain useful. |
| 18 | Week 3 mini-project: remote directory. | Build editable directory with clean reactive data ownership. | Loading, empty, error and success states all tested. |

**Week 3 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 4: sessions 19–24

**Weekly outcome:** Build three routes with loading, params and SEO metadata.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 19 | SvelteKit file routing, layouts and link navigation. | Make home, product and contact pages. | Direct URLs and browser history work. |
| 20 | Dynamic routes, params and 404 pages. | Implement `/products/[slug]` detail and unknown state. | Missing product shows valid 404. |
| 21 | Universal and server `load` functions: data boundaries. | Fetch public catalog in load function. | Secrets not exposed to browser. |
| 22 | Server-side rendering and hydration behaviour. | Compare rendered HTML and client interaction. | Page remains useful before hydration where appropriate. |
| 23 | Error pages, loading patterns and navigation hooks. | Add safe error displays and pending indicators. | Failures do not blank whole site. |
| 24 | Week 4 mini-project: public product catalog. | Build three routes with loading, params and SEO metadata. | Build and direct navigation succeed. |

**Week 4 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 5: sessions 25–30

**Weekly outcome:** Add server-backed create/edit with sessions.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 25 | SvelteKit form actions and progressive enhancement. | Add create-item form with server validation. | Basic form still works without client JavaScript. |
| 26 | Enhance form pending, errors and success UI. | Add optimistic feedback only when safe. | Server validation remains authoritative. |
| 27 | Server endpoints and HTTP methods. | Build a `/api/items` GET endpoint with proper statuses. | Invalid calls have clear JSON errors. |
| 28 | Cookies, sessions, auth vs authorization. | Build demo session-protected area (no production auth yet). | Server denies access without session. |
| 29 | Input validation, escaping and secret isolation. | Validate route parameters and form data. | Attempted invalid inputs do not reach persistence. |
| 30 | Week 5 mini-project: notes app with form actions. | Add server-backed create/edit with sessions. | Works with JavaScript on and off for main form. |

**Week 5 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 6: sessions 31–36

**Weekly outcome:** Integrate routes, auth, DB and validated forms.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 31 | SQL schema and local database integration. | Create notes/users schema and indexes. | Recreate data using migrations. |
| 32 | Server-only data access, transactions and parameters. | Add notes repository with prepared queries. | Invalid characters cannot change SQL structure. |
| 33 | Ownership rules and role checks. | Enforce user-owned notes in each action. | User B cannot view or edit user A's note. |
| 34 | Pagination and search parameters. | Add paginated notes with URL state. | Large dataset loads in predictable chunks. |
| 35 | Error monitoring and safe database failure messages. | Simulate unavailable database and friendly errors. | No credentials or traces exposed to visitor. |
| 36 | Week 6 checkpoint: multi-user notes app. | Integrate routes, auth, DB and validated forms. | 12+ tests, isolation checks and repeatable migrations. |

**Week 6 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 7: sessions 37–42

**Weekly outcome:** Add CI for typecheck, lint, test and build.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Vitest unit tests for helpers/state. | Test 15 pure functions and state transitions. | Deliberate regression causes failure. |
| 38 | Component tests with Testing Library. | Test form errors and keyboard interactions. | Tests assert accessible names and messages. |
| 39 | SvelteKit integration tests for server endpoints/actions. | Cover invalid submissions and forbidden access. | No cross-user leaks in tests. |
| 40 | Playwright browser journeys. | Cover sign-in, create/edit note and search. | Runs from clean test data. |
| 41 | Accessibility and semantic audit. | Fix modal navigation, labels, heading hierarchy, contrast. | Keyboard-only notes flow works. |
| 42 | Week 7 quality gate. | Add CI for typecheck, lint, test and build. | All checks pass in clean environment. |

**Week 7 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 8: sessions 43–48

**Weekly outcome:** Deploy, smoke test and document main flows.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Deployment adapters: static vs Node vs edge tradeoffs. | Choose adapter appropriate to server actions and DB. | Deployment strategy matches runtime needs. |
| 44 | Performance: SSR, code splitting, asset and image budgets. | Measure page weight and optimize one bottleneck. | Before/after result and rationale committed. |
| 45 | SEO, metadata, sitemap and social sharing. | Add metadata for public content route. | Correct source tags and canonical URL appear. |
| 46 | Security: headers, session cookies and CSRF protections. | Audit protected pages and server handlers. | Known attack attempts are denied in tests. |
| 47 | Operational readiness: env vars, logs, backups and CI. | Write restore plan, release instructions and error runbook. | Reproducible deployment with no hardcoded secrets. |
| 48 | Week 8 mini-project: live notes application. | Deploy, smoke test and document main flows. | Public HTTPS URL plus healthy CI and database. |

**Week 8 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 9: sessions 49–54

**Weekly outcome:** Have tester complete five tasks, fix top three bugs, tag `svelte-v1`.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Capstone scope: knowledge-base app with public/private pages. | List five goals, roles, data model and UI screens. | Plan covers SSR, forms, data and security. |
| 50 | Capstone: route structure and reusable UI. | Implement public article listing/detail and editor area. | Deep links and layout render correctly. |
| 51 | Capstone: forms, session and persistent data. | Add safe write actions, search and ownership. | Unauthorized user denied and writes survive restart. |
| 52 | Capstone: automated tests, accessibility and performance. | Build 20 tests and four E2E journeys. | CI green, keyboard accessible. |
| 53 | Capstone: deployment and onboarding. | Release app with screenshots, migrations and README. | Stranger can run or use the service. |
| 54 | Final checkpoint and retrospective. | Have tester complete five tasks, fix top three bugs, tag `svelte-v1`. | Live app, tests and docs are complete. |

**Week 9 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

## Checkpoints: do not skip the gates

If a gate fails, repeat only the weak exercises. Do not move to more advanced dependencies with untested fundamentals.

| Gate | After session | Evidence required | If missing |
|---|---:|---|---|
| Checkpoint 0 | 6 | Build add/edit/delete/filter with local component state. **Pass:** Empty and large lists work, committed. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 1 | 18 | Build editable directory with clean reactive data ownership. **Pass:** Loading, empty, error and success states all tested. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 2 | 36 | Integrate routes, auth, DB and validated forms. **Pass:** 12+ tests, isolation checks and repeatable migrations. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 3 | 42 | Add CI for typecheck, lint, test and build. **Pass:** All checks pass in clean environment. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 4 | 48 | Deploy, smoke test and document main flows. **Pass:** Public HTTPS URL plus healthy CI and database. | Rebuild the weakest feature and repeat the tests or demo. |
| Capstone | 54 | Have tester complete five tasks, fix top three bugs, tag `svelte-v1`. **Pass:** Live app, tests and docs are complete. | Rebuild the weakest feature and repeat the tests or demo. |

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

After the capstone: build **static sites with an adapter**; create an **accessible component library**; or work on **advanced streaming, form actions and edge deployment**.

## Reference resources (official-first)

These are starting points, not a promise that every heading or command stays unchanged. Prefer the documentation version matching the installed packages. Checked against official references in October 2026.

| Resource | URL |
|---|---|
| Svelte Tutorial | https://svelte.dev/tutorial/svelte/welcome-to-svelte |
| Svelte Docs | https://svelte.dev/docs/svelte/overview |
| SvelteKit Docs | https://svelte.dev/docs/kit/introduction |
| SvelteKit Creating Project | https://svelte.dev/docs/kit/creating-a-project |
| Svelte runes | https://svelte.dev/docs/svelte/what-are-runes |
| SvelteKit Form Actions | https://svelte.dev/docs/kit/form-actions |
| SvelteKit Testing | https://svelte.dev/docs/kit/testing |
| Playwright | https://playwright.dev/docs/intro |

## Final self-assessment

- [ ] I can set up the project on my own OS from a clean folder.
- [ ] I can explain the main component model and how data changes affect rendering.
- [ ] I can trace errors from user action to state, data layer and output.
- [ ] I know which data must remain trusted/server-side/privileged (where applicable).
- [ ] I can demonstrate accessibility and failure recovery, not only the happy path.
- [ ] I can reproduce tests and a production build or package without copy-pasting a tutorial.
- [ ] Another person can use my final project from its README and release instructions.
