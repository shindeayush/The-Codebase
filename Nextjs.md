# Next.js Roadmap: From Zero to Full-Stack React Applications

*Updated: 29 October 2026 · 10 weeks · 60 sessions · approximately 190 guided hours*

## Start here

Build and deploy a multi-user, database-backed full-stack app using the Next.js App Router, Server Components, secure mutations, auth and tests.

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

### Start an App Router project

```bash
npx create-next-app@latest next-roadmap
cd next-roadmap
npm run dev
```

When prompted, choose **TypeScript**, **App Router**, and **ESLint**. Keep the CLI-selected defaults for the bundler and CSS until you know why you want to change them. Do not follow outdated Pages Router-only tutorials unless you specifically need legacy code. React fundamentals are reviewed first; React is still a prerequisite for real fluency.

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

**Weekly outcome:** Build catalog, dynamic pages, shared layouts and filter UI.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 1 | React review, create App Router project in TypeScript and learn folder structure. | Generate app, sketch server/client boundaries and replace starter landing page. | Dev server and `npm run build` succeed. |
| 2 | Routes: `page`, nested segments, layouts and navigation. | Build Home, Articles and About with shared layout. | Direct URLs, navigation and refresh work. |
| 3 | Dynamic routes, route params and not-found handling. | Add article detail using a dynamic segment. | Unknown article returns not-found UI. |
| 4 | Server and Client Components; `use client` boundary and serialization. | Build read-only server list with an interactive client filter. | No server-only secret enters client bundle. |
| 5 | Loading and error boundaries, suspense and streaming basics. | Add route loading skeleton and local error recovery. | Slow route shows fallback and can retry after failure. |
| 6 | Week 1 mini-project: article library. | Build catalog, dynamic pages, shared layouts and filter UI. | Deep links, error views and build all work. |

**Week 1 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 2: sessions 7–12

**Weekly outcome:** Ship public pages with intentional caching and fallbacks.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Server fetching and async route components. | Fetch and render a list on server, inspect HTML. | Data loads without an unnecessary browser effect. |
| 8 | Data freshness and Next.js caching rules. | Compare fresh and cached resource screens. | You can explain which data is cached and why. |
| 9 | Cache Components and route rendering strategies (as documented). | Build a page combining stable and fresh sections. | Explain request-time vs prerendered work from observation. |
| 10 | Streaming and nested Suspense boundaries. | Display slow related-items independently of main article. | Header appears before slower content. |
| 11 | `generateStaticParams` and static rendering use cases. | Prebuild selected public detail pages. | Build output confirms selected paths are generated. |
| 12 | Week 2 mini-project: content catalog. | Ship public pages with intentional caching and fallbacks. | Document observed cache behaviour with screenshots/logs. |

**Week 2 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 3: sessions 13–18

**Weekly outcome:** Add/create/edit/list issues with validation and revalidation.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Server Functions/Actions and mutation boundaries. | Add a server-side create-item operation with form. | Form writes data; action does not expose secrets. |
| 14 | FormData validation and safe schemas. | Reject blank, too-long and malformed fields server-side. | Invalid direct POST is rejected, not just UI click. |
| 15 | Pending, optimistic and success/error form states. | Implement submit feedback and duplicate-submit protection. | Poor connection still shows correct status. |
| 16 | Revalidation after mutations and stale view correction. | Update item and refresh affected routes/cache. | List reflects a successful edit immediately. |
| 17 | Route Handlers, method semantics and JSON responses. | Create a small GET/POST endpoint for public items. | Returns appropriate status for valid and invalid requests. |
| 18 | Week 3 mini-project: issue tracker mutations. | Add/create/edit/list issues with validation and revalidation. | Edits persist and list/detail stay consistent. |

**Week 3 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 4: sessions 19–24

**Weekly outcome:** Run issue tracker from a clean database and tests.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Relational database fundamentals and schema planning. | Design users, projects, issues and indexes. | Explain primary, foreign keys and uniqueness rules. |
| 20 | Database client, server-only modules and safe environment variables. | Connect local SQLite/PostgreSQL via supported driver/ORM. | Credentials never appear in client assets. |
| 21 | Migrations and seed data. | Create migration and repeatable dev seeding command. | New database can be recreated from scratch. |
| 22 | CRUD repositories and transactions. | Implement issue repository with consistent errors. | Failed multi-write operation rolls back. |
| 23 | Pagination, filtering and query parameters. | Add page size, status filter and search with limits. | Large lists avoid loading every record. |
| 24 | Week 4 checkpoint: database-backed dashboard. | Run issue tracker from a clean database and tests. | 10+ integration assertions plus repeatable migrations. |

**Week 4 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 5: sessions 25–30

**Weekly outcome:** Add user accounts and a protected workspace.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Authentication fundamentals: identity vs authorization, cookies. | Diagram login/logout, sessions and access rules. | Explain why UI checks alone are not security. |
| 26 | Use maintained authentication solution, password/session security. | Implement sign-up/login with a supported auth library. | Passwords are not stored in plaintext. |
| 27 | Protected server pages and per-record access checks. | Make users see only their own projects. | User B cannot read or edit User A's data by URL changes. |
| 28 | CSRF, validation, rate limiting and secret handling. | Threat-model form endpoints and harden their checks. | Unauthorized and malformed requests have tests. |
| 29 | Role-based authorization and least privilege. | Add viewer/editor distinction enforced on server. | Viewer is denied editor-only changes. |
| 30 | Week 5 mini-project: multi-user issue tracker. | Add user accounts and a protected workspace. | Two accounts are isolated in manual and automated tests. |

**Week 5 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 6: sessions 31–36

**Weekly outcome:** Integrate media, SEO, accessibility and boundaries.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Metadata API, sitemaps and social previews. | Add titles, descriptions and share preview for public pages. | Page source shows expected metadata. |
| 32 | Image and font optimization; responsive media. | Use `next/image` with correct sizing, handle alt text. | No oversized hero image on mobile. |
| 33 | Accessibility, focus, semantic forms and route changes. | Make modal and all forms keyboard usable. | Navigation and submission work without mouse. |
| 34 | Error handling: route error UI, expected errors and logs. | Distinguish user input errors vs unexpected failures. | Failures show safe message, logs contain useful trace. |
| 35 | Performance and bundle analysis: client JS budgets. | Remove a bulky client dependency or move work server-side. | Report bundle reduction and behaviour retained. |
| 36 | Week 6 mini-project: polished public/private portal. | Integrate media, SEO, accessibility and boundaries. | Lighthouse/perf notes and accessibility checklist committed. |

**Week 6 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 7: sessions 37–42

**Weekly outcome:** Set up CI for typecheck/lint/test/build/e2e where feasible.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Unit tests of helpers and validation. | Write 15 Vitest tests for validation and permissions. | Tests fail on intentionally incorrect rule. |
| 38 | Component tests and deterministic mocks. | Test client form loading/error/success states. | No network access needed for tests. |
| 39 | Integration tests for Route Handlers and database. | Test CRUD, transactions and ownership. | Data is isolated between tests. |
| 40 | Playwright E2E and test database lifecycle. | Test login, new issue, edit issue and sign-out. | Repeatable browser run from clean setup. |
| 41 | Security regression tests and accessibility automation. | Test forbidden cross-user access and run axe checks. | No critical issues or unauthorized access. |
| 42 | Week 7 quality gate. | Set up CI for typecheck/lint/test/build/e2e where feasible. | CI catches broken auth or route changes. |

**Week 7 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 8: sessions 43–48

**Weekly outcome:** Publish secure tracker and record deployment notes.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Production environments, secrets and connection pooling. | Document `.env.example`, preview vs production setup. | No secrets committed or printed in browser. |
| 44 | Deploying Next.js: Node host, managed host, Docker tradeoffs. | Deploy working app using a supported platform. | Public HTTPS URL loads and mutations persist. |
| 45 | Observability: structured errors, slow routes, health checks. | Add privacy-aware monitoring and one health route. | Failure can be diagnosed without exposing user data. |
| 46 | Caching in production and invalidation testing. | Verify updated records reflect after deployment. | No stale user-owned records shown to another user. |
| 47 | Backups, migrations and rollback plans. | Write upgrade checklist and simulate restoration locally. | Database recovery steps are documented and demonstrated. |
| 48 | Week 8 mini-project: production release. | Publish secure tracker and record deployment notes. | Live app, green CI, backup/rollback runbook. |

**Week 8 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 9: sessions 49–54

**Weekly outcome:** Rebuild a small module cleanly from requirements.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Server/client architecture review and dependency boundaries. | Refactor duplicated server fetch logic into modules. | No server module imports into client component. |
| 50 | Data security: minimizing serialized payloads. | Remove private fields from views and API responses. | Only intended fields cross to client. |
| 51 | Edge vs Node runtime capabilities and restrictions. | Compare runtime requirements for one route. | Runtime selected based on APIs and deployment. |
| 52 | Scale: cursor pagination, index review, cache rules. | Profile slow query and test pagination with seed data. | Query plan and measurable improvement documented. |
| 53 | Documentation and API contracts. | Write architecture map and route/use-case documentation. | New contributor can find every main feature. |
| 54 | Week 9 architecture checkpoint. | Rebuild a small module cleanly from requirements. | Tests pass; design choices explained in a short ADR. |

**Week 9 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

### Week 10: sessions 55–60

**Weekly outcome:** Ask tester to complete five tasks, fix top three bugs, tag `next-v1`.

| Session | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Final capstone scope: publishable team workspace. | Define users, roles, records, audit and measurable goals. | One-page spec, risks and wireframes. |
| 56 | Capstone build: server rendering, routing and state. | Implement polished dashboard with public landing area. | Every route and loading state has meaning. |
| 57 | Capstone build: database/auth/permissions. | Integrate seeded data, migrations and isolated records. | Cross-user access blocked across all routes/actions. |
| 58 | Capstone quality: tests, a11y, performance and security. | Reach 20+ tests and 4 browser flows, audit payloads. | CI green and no high-severity errors. |
| 59 | Capstone delivery: deployment and operating docs. | Publish, produce screenshots, README and rollback notes. | Stranger deploys from documented setup. |
| 60 | Final user test and tag. | Ask tester to complete five tasks, fix top three bugs, tag `next-v1`. | Live app works end-to-end and docs are sufficient. |

**Week 10 review:** Show your project in a 3-minute demo; identify one failure case, one accessibility or security issue, and one design choice you changed. Run the available build/test/typecheck commands, record the output in `journal.md`, and commit.

## Checkpoints: do not skip the gates

If a gate fails, repeat only the weak exercises. Do not move to more advanced dependencies with untested fundamentals.

| Gate | After session | Evidence required | If missing |
|---|---:|---|---|
| Checkpoint 0 | 6 | Build catalog, dynamic pages, shared layouts and filter UI. **Pass:** Deep links, error views and build all work. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 1 | 24 | Run issue tracker from a clean database and tests. **Pass:** 10+ integration assertions plus repeatable migrations. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 2 | 36 | Integrate media, SEO, accessibility and boundaries. **Pass:** Lighthouse/perf notes and accessibility checklist committed. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 3 | 48 | Publish secure tracker and record deployment notes. **Pass:** Live app, green CI, backup/rollback runbook. | Rebuild the weakest feature and repeat the tests or demo. |
| Checkpoint 4 | 54 | Rebuild a small module cleanly from requirements. **Pass:** Tests pass; design choices explained in a short ADR. | Rebuild the weakest feature and repeat the tests or demo. |
| Capstone | 60 | Ask tester to complete five tasks, fix top three bugs, tag `next-v1`. **Pass:** Live app works end-to-end and docs are sufficient. | Rebuild the weakest feature and repeat the tests or demo. |

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

After the capstone: add a **background jobs/queues** track; **large-scale caching and observability**; or **self-hosting with Docker**. Learn the Pages Router only if maintaining existing applications.

## Reference resources (official-first)

These are starting points, not a promise that every heading or command stays unchanged. Prefer the documentation version matching the installed packages. Checked against official references in October 2026.

| Resource | URL |
|---|---|
| Next.js docs | https://nextjs.org/docs |
| Next App Router | https://nextjs.org/docs/app |
| Next Getting Started | https://nextjs.org/docs/app/getting-started |
| Next Testing | https://nextjs.org/docs/app/guides/testing |
| Next Authentication | https://nextjs.org/docs/app/guides/authentication |
| React Learn | https://react.dev/learn |
| OWASP Cheat Sheet Series | https://cheatsheetseries.owasp.org/ |
| Playwright | https://playwright.dev/docs/intro |

## Final self-assessment

- [ ] I can set up the project on my own OS from a clean folder.
- [ ] I can explain the main component model and how data changes affect rendering.
- [ ] I can trace errors from user action to state, data layer and output.
- [ ] I know which data must remain trusted/server-side/privileged (where applicable).
- [ ] I can demonstrate accessibility and failure recovery, not only the happy path.
- [ ] I can reproduce tests and a production build or package without copy-pasting a tutorial.
- [ ] Another person can use my final project from its README and release instructions.
