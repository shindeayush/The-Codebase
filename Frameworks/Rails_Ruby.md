# Rails Roadmap: From Zero to Convention-Driven Ruby Web Applications

**60 sessions | 10 study weeks | approximately 190 hours | created October 29, 2026**

This roadmap is a standalone, project-based guide to Rails. Each “Day” below is a **study session**, not necessarily a calendar day. The finish line is **Community events web app** with organizers, event listings, registrations, role policy, email confirmations, Turbo/Stimulus interactivity, Active Record data, automated tests and a deployed release.

## Start here

**Prerequisites and the beginner bridge.** Ruby basics (blocks, classes, symbols, hashes), MVC, HTTP and SQL. The first week refreshes essentials; works independently of earlier Ruby roadmap.

**Operating systems.** macOS and Linux are strong native development hosts. On Windows, official Rails installation guidance commonly recommends WSL2 for Unix-compatible development; avoid treating native Windows packaging as identical to Linux/macOS. Browser output works everywhere.

**Installation.** Install a Rails-supported Ruby using a version manager (e.g. mise or rbenv), RubyGems/Bundler, Git and database. Follow current Rails install guide for your OS; `gem install rails` then `rails new` for a fresh project. Use the app’s `bin/rails` to avoid invoking a different global version.

### First run

```bash
ruby --version
bundle --version
gem install rails
rails new rails-roadmap
cd rails-roadmap
bin/rails db:prepare
bin/rails server
# Open http://localhost:3000
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
rails-roadmap/
  README.md
  journal.md
  week-01/
  week-02/
  ...
  capstone/
```

Keep one Git commit per session, a runnable example for every topic, short notes on bugs and fixes, and a README in each weekly project. Use version control; never commit passwords, credentials or production database files.

## Week 1: Ruby and Rails foundations

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Ruby enumerables, blocks and hash basics | Filter simple event collection | Code idiomatic and 5 tests pass |
| 2 | Rails MVC, directory structure and conventions | Trace root route to controller/view | Explain what Active Record does |
| 3 | Rails installation, CLI and project boot | Generate project and run server | Browser displays home page |
| 4 | Routes and RESTful resources | Create events routes | rake/rails routes matches expectation |
| 5 | Controllers, actions and params | Build events index/show | Unknown ID handled gracefully |
| 6 | Project: static events bulletin | List and detail events with layout | Works without database errors |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 2: Views and forms

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | ERB, partials and layout | Create reusable event card | HTML escaped correctly |
| 8 | Form builders and strong parameters | Add event form | Extra unpermitted fields ignored |
| 9 | Flash, redirects and validation errors | Show inline form feedback | Rejected event does not persist |
| 10 | CSS asset pipeline and responsive UI | Design mobile events page | Navigation/contrast verified |
| 11 | Helper methods and presentation logic | Extract date formatter | No business rules in views |
| 12 | Project: browser CRUD events | Add edit/create/delete forms | Manual flow and controller tests pass |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 12

- From a clean checkout, run the week 2 project and its tests with no undocumented steps.
- Explain three concepts from weeks 1–2 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 3: Database and Active Record

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Schema migrations and models | Create events/organizers/registrations | Foreign keys and indexes explicit |
| 14 | Active Record validations | Reject duplicate event slug and past end time | Invalid row blocked |
| 15 | Associations and inverse relationships | Connect users and registrations | Related records load correctly |
| 16 | Scopes and queries | Filter by venue/month | No SQL injection through filters |
| 17 | Seeding and factories/fixtures | Create 100 realistic events | Seed works from empty DB |
| 18 | Project: searchable event directory | Add filters and persistence | DB reset/reseed reproducible |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 4: Testing and diagnosis

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Minitest or preferred supported Rails test stack | Test event model constraints | 15 cases cover boundaries |
| 20 | Integration tests for signed-in flows | Test registration lifecycle | Correct redirects and permissions |
| 21 | System tests with browser | Click through event registration | UI flow works from clean DB |
| 22 | Logging, debugger, N+1 diagnostics | Diagnose expensive index | Query count reduced and measured |
| 23 | Rails console and runner safety | Inspect app data on development fixture | No destructive production experimentation |
| 24 | Checkpoint 1: events CRUD | Build venue module with tests | Clean tests and valid schema |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 24

- From a clean checkout, run the week 4 project and its tests with no undocumented steps.
- Explain three concepts from weeks 3–4 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 5: Authentication and authorization

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Rails authentication generator or supported approach | Add account signup/signin | Password hash only |
| 26 | Sessions, cookies and CSRF | Verify POST protections | Forged form rejected |
| 27 | Authorization policies and scoping | Organizer edits only own event | Cross-account request denied |
| 28 | Privacy and untrusted HTML | Escape descriptions, control redirects | XSS probe fails safely |
| 29 | Email verification and password recovery concepts | Send fake reset message in test | Tokens expire and only one use |
| 30 | Project: community role system | Add organizer and attendee roles | Role matrix acceptance tests green |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 6: Hotwire UI and jobs

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Turbo Drive and Frames | Update registration count without full reload | Back button and state correct |
| 32 | Turbo Streams for shared updates | Stream new registration row | No duplicate display |
| 33 | Stimulus controllers and progressive enhancement | Add venue filter UI | Form still works without JavaScript |
| 34 | Active Job and queue adapter | Enqueue registration email | Web response independent of job execution |
| 35 | Action Mailer and safe preview | Build confirmation mail | Email includes correct event link |
| 36 | Project: interactive RSVP app | Add live registration feedback | Works keyboard/mobile and with JS disabled |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 36

- From a clean checkout, run the week 6 project and its tests with no undocumented steps.
- Explain three concepts from weeks 5–6 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 7: Advanced data and integrations

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Optimistic locking and DB transactions | Enforce event capacity | Concurrent RSVP does not overbook |
| 38 | Active Storage uploads | Add event cover image | MIME/size controlled |
| 39 | REST/JSON endpoints and serializers | Add public events JSON | No private attendee data leaked |
| 40 | External API calls and timeouts | Pull fictional weather data | Offline failure recoverable |
| 41 | Caching and invalidation | Cache venue event count | Update reflects new registration |
| 42 | Checkpoint 2: capacity-safe tickets | Simulate competing registrations | At most capacity successes recorded |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 8: Operations and application design

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Service objects and boundaries | Extract registration action | Controller stays small |
| 44 | Internationalization and localization | Provide two locale files | Dates/plurals translate |
| 45 | Background email idempotency | Retry confirmation safely | No duplicate RSVP state |
| 46 | Request performance and index plans | Benchmark filter query | Before/after results recorded |
| 47 | Structured errors and production secrets | Handle failures and secret keys | No private data in logs |
| 48 | Project: organizer dashboard | Add metrics and attendee export | Counts reconcile with DB |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

### Checkpoint after session 48

- From a clean checkout, run the week 8 project and its tests with no undocumented steps.
- Explain three concepts from weeks 7–8 without notes and identify one failure path you tested.
- Rebuild one previously studied component from memory; commit fixes and write one paragraph describing what was difficult.

## Week 9: Deployment and security

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Production assets, environments and credentials | Build in production mode | No development secret reused |
| 50 | PostgreSQL deployment and migrations | Deploy using chosen host | Schema matches local migrations |
| 51 | Kamal or host-specific deployment workflow | Record reproducible deploy plan | Clean deploy works end-to-end |
| 52 | CI tests and Brakeman security scan | Add automated gate | Failing test blocks release |
| 53 | Backup/restore rehearsal | Restore event DB into isolated env | Rows/checksums match fixture |
| 54 | Project: live RSVP staging | Share a demo and feedback form | Tester registers and cancels successfully |

**Break it this week:** deliberately try an invalid input, a failed dependency, and a test that should fail. Read the resulting trace/log before fixing it.

## Week 10: Capstone delivery

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Plan events domain and user journeys | Define 12 acceptance criteria | Role and capacity flows specified |
| 56 | Complete organizer CRUD and public discovery | Build polished site | Search and listing tests green |
| 57 | Complete RSVP, jobs and notifications | Build asynchronous confirmations | Conflict and retry tests green |
| 58 | Complete Turbo, accessibility and localization | Add dynamic experience | Core works without JS |
| 59 | Finish CI, deployment, recovery runbook | Publish release and test report | Restore dry run complete |
| 60 | Final capstone review | Demo deployed app and test suite | New user can host and operate from README |

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

Rails conventions speed delivery, but they do not replace authorization, careful transactions, or DB constraints. The current Rails guides emphasize `bin/rails` inside a project. Windows users should plan WSL2 when Rails/native Ruby gems require Unix tooling.

## Official learning resources

| Resource | Link |
|---|---|
| Rails install guide | <https://guides.rubyonrails.org/install_ruby_on_rails.html> |
| Getting Started | <https://guides.rubyonrails.org/getting_started.html> |
| Active Record | <https://guides.rubyonrails.org/active_record_basics.html> |
| Rails routing | <https://guides.rubyonrails.org/routing.html> |
| Rails security | <https://guides.rubyonrails.org/security.html> |
| Testing | <https://guides.rubyonrails.org/testing.html> |
| Rails deployment | <https://guides.rubyonrails.org/tuning_performance_for_deployment.html> |

**Version check:** framework releases and developer tools change. Before installing or copying commands from this guide, check the official documentation above against the versions currently available on your computer.
