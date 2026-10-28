# Ruby Roadmap: From Zero to Web Apps and Automation

*54 sessions | 9 weeks | about 171 hours*

From a first Ruby script to a tested, authenticated Ruby on Rails application. Learn Ruby as an expressive object-oriented language before adding packages, databases, HTTP, background tasks, security and deployment. No prior programming is required.

## Start here

**How Ruby works.** You write .rb files and run them with the Ruby interpreter (ruby file.rb); irb is the interactive console. Gems add libraries, Bundler locks dependencies, and Rails organizes complete web applications using models, views and controllers.

**Setup (once, about 45–90 minutes):**

1.  Install a supported current Ruby using the official instructions at https://www.ruby-lang.org/en/documentation/installation/; on Windows, use a recommended Windows-compatible installer or WSL setup.

2.  Verify ruby -v, gem -v and bundle -v; install VS Code with a Ruby language extension or RubyMine; install Git.

3.  Create ruby-roadmap with week-01 through week-09 folders, journal.md and Git history. Start with ruby hello.rb and irb.

4.  During week 4 use a Gemfile and Bundler. During week 5 install a Rails release compatible with your Ruby and database setup; follow the official Rails install guide rather than hardcoded version numbers.

5.  Keep secrets in environment variables or appropriate encrypted credentials, and never push them to Git.

## How each study session works

| **Minutes** | **Block** | **What you do**                                                               |
|-------------|-----------|-------------------------------------------------------------------------------|
| 10          | Start     | Re-type yesterday’s snippet from memory; review your journal’s next step.     |
| 40          | Learn     | Work through just today’s topic; reproduce examples while taking short notes. |
| 90          | Build     | Write the exercise yourself, without copying generated solutions.             |
| 30          | Break it  | Deliberately introduce a bug, reproduce it, inspect the error and fix it.     |
| 10          | Save      | Run checks, commit, and write: learned / confused / next first step.          |

Days are study sessions, not calendar days. Sessions 1–5 each week last about 3 hours; the sixth is a 4-hour project and review. At every checkpoint, repeat weak topics before moving forward.

**Definition of done.** The program runs, its tests are green, unexpected input has a safe outcome, it is committed and you can explain every method.

Study rule: do not race a calendar. If an exercise needs another session, complete it before proceeding. Keep a journal and a Git commit after every working session.

## Part 1 — Ruby syntax, collections and scripts

### Week 1 — First Ruby programs (days 1–6)

| **Day** | **Learn**                                                                     | **Build**                                                    | **Done when**                                                |
|---------|-------------------------------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------|
| **1**   | What Ruby is; interpreted scripts, irb, puts, p, comments, ruby -v.           | hello.rb, a greeting and three IRB experiments.              | You can run a file and explain output versus returned value. |
| **2**   | Variables, Integer, Float, String, Boolean, nil, symbols and conversions.     | Bill splitter with currency formatting and input validation. | Numbers and strings are not confused; nil is recognized.     |
| **3**   | Operators, comparisons, truthiness, if/elsif/else, unless, case.              | Grade calculator and shipping fee rules.                     | Every boundary and truthy/falsey case is tested.             |
| **4**   | while, until, times, upto, each; break and next.                              | Multiplication table, FizzBuzz and guessing game.            | You can trace the iteration without running it.              |
| **5**   | Methods, positional and keyword arguments, defaults, implicit returns, scope. | Reusable prime?, total_with_tax and currency methods.        | Method tests cover normal and wrong inputs.                  |
| **6**   | Project / review, Git init/add/commit.                                        | CLI unit converter with repeating menu and safe input.       | Runs from terminal, handles bad input, committed as ruby-w1. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 2 — Collections, blocks and persistence (days 7–12)

| **Day** | **Learn**                                                                     | **Build**                                                         | **Done when**                                         |
|---------|-------------------------------------------------------------------------------|-------------------------------------------------------------------|-------------------------------------------------------|
| **7**   | Arrays: indexing, slicing, push/pop, map, select, reject and each_with_index. | To-do list using Array with complete/due statuses.                | No logic depends on invalid indices.                  |
| **8**   | Hashes, symbols as keys, fetching defaults, nested structures.                | Inventory list indexed by SKU; search and stock update.           | Unknown SKUs are handled gracefully.                  |
| **9**   | Blocks, yield, Enumerable, select, reduce, group_by and sort_by.              | Report totals and categories from an array of transaction hashes. | You can rewrite two loops idiomatically.              |
| **10**  | Strings and Regex; interpolation, split, strip, gsub and captures.            | Normalize names and extract valid order codes.                    | Invalid strings are rejected, not partially accepted. |
| **11**  | Files, directories, Pathname, JSON and CSV; encoding, closing resources.      | Persist inventory in a JSON file; import a CSV.                   | A second run sees identical saved data.               |
| **12**  | Checkpoint 0: the language from memory.                                       | CLI contacts app with add/find/delete and JSON persistence.       | Five edge cases pass, no copied code; tag ruby-p1.    |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Send a string to an integer method; call a method on nil; use = instead of ==; forget end; handle input that is blank.

## Part 2 — Objects, packages and tested tools

### Week 3 — Objects and architecture (days 13–18)

| **Day** | **Learn**                                                                                 | **Build**                                                  | **Done when**                                              |
|---------|-------------------------------------------------------------------------------------------|------------------------------------------------------------|------------------------------------------------------------|
| **13**  | Classes, initialize, instance variables, readers/writers, public/private.                 | Model Account, Transaction and Ledger classes.             | Transactions cannot bypass validation.                     |
| **14**  | Inheritance, super, polymorphism and composition; when to avoid inheritance.              | PaymentMethod hierarchy and composable fee rules.          | Add a new payment type without editing call sites.         |
| **15**  | Modules, mixins, namespaces and constants; require/require_relative.                      | Split the ledger into modules and separate files.          | No global mutable variables; files load cleanly.           |
| **16**  | Errors: begin/rescue/ensure, custom exceptions, raise, retry caution.                     | Handle corrupt files and insufficient funds.               | Users see a useful error without a raw trace.              |
| **17**  | Ruby object model: self, everything is an object, method lookup, equality and mutability. | Explain a surprising object-sharing bug and fix it.        | You can distinguish ==, eql? and equal?.                   |
| **18**  | Project / review: domain model.                                                           | A testable, multi-file CLI budget manager with categories. | Rules live inside objects, not just the menu; tag ruby-w3. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 4 — Gems, testing and professional CLI tools (days 19–24)

| **Day** | **Learn**                                                                   | **Build**                                                     | **Done when**                                                  |
|---------|-----------------------------------------------------------------------------|---------------------------------------------------------------|----------------------------------------------------------------|
| **19**  | RubyGems, Bundler, Gemfile/Gemfile.lock; versions and dependency hygiene.   | Turn CLI project into a bundled app with one simple gem.      | bundle exec runs reproducibly.                                 |
| **20**  | Testing with Minitest (or RSpec): test cases, setup and assertions.         | Write 15 unit tests for budget rules.                         | An intentional regression is detected by the suite.            |
| **21**  | TDD, doubles/stubs, deterministic data and dependency injection.            | Test an email/notification adapter without network access.    | Tests never send a real message.                               |
| **22**  | CLI options with OptionParser; environment variables; safe configuration.   | Add --input, --format and --help to your tool.                | Invalid flags produce clear help rather than a stack trace.    |
| **23**  | Time/Date, sorting and querying, benchmark/measure; algorithmic complexity. | Add reports for a date range and benchmark a slow operation.  | Sorted results are correct and measurements recorded.          |
| **24**  | Checkpoint 1: clean Ruby, packages and tests.                               | Package and document a CLI finance tool with CSV/JSON import. | 20 tests pass; install and run instructions work; tag ruby-p2. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Modify a shared mutable object accidentally; cause missing-key errors; corrupt a JSON file; rescue the wrong exception.

## Part 3 — Rails, SQL and secure user data

### Week 5 — Rails and the web (days 25–30)

| **Day** | **Learn**                                                                        | **Build**                                               | **Done when**                                        |
|---------|----------------------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------|
| **25**  | Web basics: request/response, URL, HTML/CSS, forms, HTTP verbs and status codes. | Sketch a notes app: page layout and REST endpoints.     | Can explain GET versus POST versus PATCH and DELETE. |
| **26**  | Rails setup and structure: rails new, bin/rails, MVC, routing and generators.    | Create a small Rails notes app and its first page.      | Development server runs; a route resolves.           |
| **27**  | Active Record models, validations, migrations and SQLite development DB.         | Add Note and Tag models with validations.               | Invalid records cannot be persisted.                 |
| **28**  | Controllers, strong parameters, resource routes and CRUD.                        | Create, edit, show and delete notes.                    | Correct status/redirect behavior for each operation. |
| **29**  | Views, ERB, partials, forms, layouts, flash messages and basic accessibility.    | Build usable forms, validation messages and navigation. | Keyboard-only user can complete core workflow.       |
| **30**  | Project / review: Rails CRUD checkpoint.                                         | Working notes app with tags, filters and seed data.     | All CRUD actions work end to end; tag ruby-w5.       |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 6 — Databases, authentication and security (days 31–36)

| **Day** | **Learn**                                                                                              | **Build**                                                         | **Done when**                                          |
|---------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|--------------------------------------------------------|
| **31**  | Associations: belongs_to, has_many, dependent behavior; N+1 queries.                                   | Link notes to folders and display note counts efficiently.        | Deleting folders follows a documented rule.            |
| **32**  | SQL and database design: joins, indexes, unique constraints, transactions.                             | Add a database-level uniqueness rule and one transaction.         | Data stays consistent during a simulated failure.      |
| **33**  | Rails testing: model, request and system tests; fixtures or factories.                                 | Build 20 automated tests around the notes app.                    | All tests run in one command on a clean test DB.       |
| **34**  | Authentication: Rails-supported authentication generator or well-maintained library; password hashing. | Add sign-up/login and protected pages.                            | Anonymous visitors cannot view private notes.          |
| **35**  | Authorization and security: ownership checks, CSRF, XSS escaping, SQL injection.                       | Try to access another user’s note; prevent it.                    | Every read/update/delete is scoped to signed-in user.  |
| **36**  | Checkpoint 2: authenticated database-backed Rails app.                                                 | Deliver notes app with users, 20 tests and an authorization test. | A user cannot access another user’s data; tag ruby-p3. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Add a failing unit test, bypass a validation, create an N+1 query and try a user ID that belongs to someone else.

## Part 4 — APIs, operations and shipping

### Week 7 — API and production features (days 37–42)

| **Day** | **Learn**                                                                        | **Build**                                                   | **Done when**                                           |
|---------|----------------------------------------------------------------------------------|-------------------------------------------------------------|---------------------------------------------------------|
| **37**  | API mode versus full-stack Rails; JSON rendering, serializers, versioned routes. | Expose a read-only JSON endpoint for user-owned notes.      | Unauthorized requests return correct errors.            |
| **38**  | REST design: errors, pagination, filtering, rate-limit awareness.                | Add search and pagination to notes index.                   | Invalid parameters return predictable JSON/HTML errors. |
| **39**  | Background jobs: Active Job and job backends; idempotency.                       | Queue a reminder/notification with a fake delivery adapter. | Retrying a job does not duplicate a visible action.     |
| **40**  | Email, file uploads and storage: Action Mailer and Active Storage overview.      | Add optional attachment and send a preview-only mail.       | Bad file types are rejected; no secret appears in logs. |
| **41**  | Caching, logs, instrumentation, and basic query profiling.                       | Find and fix one N+1 query; add structured logs.            | Before/after query counts are documented.               |
| **42**  | Project / review: Rails product iteration.                                       | Add API, search, a queued task and one upload to your app.  | All features have request or system tests; tag ruby-w7. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 8 — Testing, hardening and deployment (days 43–48)

| **Day** | **Learn**                                                                    | **Build**                                                                        | **Done when**                                       |
|---------|------------------------------------------------------------------------------|----------------------------------------------------------------------------------|-----------------------------------------------------|
| **43**  | Deployment basics: production config, secrets, host/database, assets, HTTPS. | Write a deployment checklist for a chosen Rails-compatible host.                 | No credentials committed; env vars documented.      |
| **44**  | CI: GitHub Actions, bundle install, lint (RuboCop), tests, security scans.   | Create a workflow to run checks on every push.                                   | A broken test makes CI fail.                        |
| **45**  | Security hardening: Brakeman, dependency audits, session settings, limits.   | Run security checks and fix the highest-priority finding.                        | A scan and a written remediation note exist.        |
| **46**  | Docker/Kamal overview or host-native deploy; migrations and rollbacks.       | Deploy demo with seed data to chosen host or produce repeatable local container. | App launches from documented commands.              |
| **47**  | Observability and UX: error handling, performance, basic access logging.     | Add custom 404/500 pages and user-facing recovery.                               | A friend can report errors with reproducible steps. |
| **48**  | Checkpoint 3: ship a Rails application.                                      | Live (or reproducibly containerized) notes service, documented CI and demo.      | CI green, data safe, README complete; tag ruby-p4.  |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Remove a required env var, change a migration, return a 500 from a route, and verify CI blocks a regression.

## Part 5 — End-to-end Rails capstone

### Week 9 — Complete Rails product capstone (days 49–54)

| **Day** | **Learn**                                                                  | **Build**                                                              | **Done when**                                                    |
|---------|----------------------------------------------------------------------------|------------------------------------------------------------------------|------------------------------------------------------------------|
| **49**  | Capstone scope: choose a booking, inventory or project-tracking Rails app. | Plan entities, screens, roles and five measurable acceptance criteria. | Requirements fit the week and clarify what is out of scope.      |
| **50**  | Domain design and migrations; seed data and fixtures.                      | Implement models, relationships and validations.                       | Database constraints protect critical assumptions.               |
| **51**  | Application flow and forms/API.                                            | Implement two end-to-end workflows for distinct roles.                 | Happy and unhappy paths work with useful messages.               |
| **52**  | Authentication, authorization and background workflow.                     | Protect all owner-scoped records; add a queued feature.                | Cross-user access tests fail before fix and pass after.          |
| **53**  | Test, refactor, deploy and documentation.                                  | Add 30 tests, CI, screenshot walkthrough and troubleshooting.          | Deployment and test suite succeed from README.                   |
| **54**  | Final capstone review.                                                     | Release app, demo it, write retrospective and tag ruby-v1.             | A stranger can sign in, complete the workflow and run the tests. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

## Checkpoints and what comes next

These are gates, not optional homework. If you cannot complete a gate without copying, review the relevant sessions and repeat the project. Document what failed and what changed.

| **Gate**                      | **What you must show**                                                      |
|-------------------------------|-----------------------------------------------------------------------------|
| **Day 12 · Foundations**      | Create a robust contacts CLI from memory with Hash, Array and JSON storage. |
| **Day 24 · Ruby engineering** | Clean, documented CLI with 20 tests and repeatable Bundler installation.    |
| **Day 36 · Rails core**       | CRUD with database validation, user authentication and ownership tests.     |
| **Day 48 · Shipping**         | Tested Rails application with CI, scans and reproducible deployment.        |
| **Day 54 · Capstone**         | Role-aware production-style Rails project with demo and README.             |

## Your portfolio at the end

- Packaged Ruby command-line budget tool with tests

- Authenticated Rails notes app with CRUD and access controls

- Deployed or repeatably containerized Rails capstone with CI and API

## After the last session

Explore Hotwire, advanced Active Record optimization, queues, GraphQL, web sockets, Ruby internals or writing a publishable gem. Audit dependencies and permissions before shipping.

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
<td><strong>Ruby: 20-minute guide</strong></td>
<td>The first days of the Ruby language<br />
https://www.ruby-lang.org/en/documentation/quickstart/</td>
</tr>
<tr class="even">
<td><strong>Official Ruby docs</strong></td>
<td>Core classes, modules and syntax<br />
https://www.ruby-lang.org/en/documentation/</td>
</tr>
<tr class="odd">
<td><strong>RubyGems / Bundler</strong></td>
<td>Dependencies and Gemfile lockfiles<br />
https://guides.rubygems.org/getting_started/</td>
</tr>
<tr class="even">
<td><strong>Rails Getting Started</strong></td>
<td>MVC, Rails setup and CRUD<br />
https://guides.rubyonrails.org/getting_started.html</td>
</tr>
<tr class="odd">
<td><strong>Rails Security Guide</strong></td>
<td>Auth, sessions and Rails-specific risks<br />
https://guides.rubyonrails.org/security.html</td>
</tr>
<tr class="even">
<td><strong>Rails Testing Guide</strong></td>
<td>Model, request and system tests<br />
https://guides.rubyonrails.org/testing.html</td>
</tr>
<tr class="odd">
<td><strong>RuboCop</strong></td>
<td>Style and static analysis<br />
https://docs.rubocop.org/rubocop/</td>
</tr>
</tbody>
</table>

**About this guide.** Structure adapted from the three supplied learning roadmaps (Java, Go and C++): independent beginner entry, a repeatable study rhythm, day-by-day Learn / Build / Done when tables, project reviews, checkpoints and a shipped capstone. Language-specific topics and exercises here are newly authored; the guides are not translations of those documents.
