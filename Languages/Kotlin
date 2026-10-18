# Kotlin Roadmap: From Zero to Android Apps and Backends

This roadmap takes you from your first variable to a published-quality Android app and a Kotlin back end in 42 sessions (7 weeks, about 130 hours). It assumes you have never programmed. Kotlin is Google's preferred language for Android, and it also runs on servers (it works with Java libraries). It is concise and safer than Java, so it is a friendly first language. It stands alone and starts from zero. By the end you can build an Android app with a local database and network calls, plus a small API that it talks to.

## Start here

**How Kotlin works.** You write `.kt` files, the compiler turns them into JVM bytecode (or native code, or JavaScript), and the program runs. For Android, Gradle builds it into an app.

**Setup (1 hour, once):**

1. Install a **JDK 21 or newer** (Eclipse Temurin from adoptium.net is free). Check `java -version`.
2. Install **IntelliJ IDEA Community Edition** for parts 1, 2 and 4. It has Kotlin built in.
3. Install **Android Studio** before day 25. It needs about 8 GB of RAM and 10 GB of disk; a real phone with USB debugging can replace the slow emulator.
4. For the first days you can also use the free [Kotlin Playground](https://play.kotlinlang.org/) in the browser.
5. Make a folder `kotlin-roadmap` with one package per day. Run `git init` and commit at the end of every session.

**How one session works (about 3 hours):**

| Minutes | Step | What you do |
| --- | --- | --- |
| 10 | Start | Re-type from memory one snippet from last session. |
| 40 | Learn | Read the listed source, typing every example. |
| 90 | Build | Write the day's program without copying. |
| 30 | Break it | Cause compile errors on purpose and read each message. |
| 10 | Save | `git commit` and write 3 journal lines. |

The 6th session each week is a 4-hour project and review. A session is done only when the program builds with no warnings you do not understand, runs, is committed, and you can explain it line by line.

## Part 1 (weeks 1-2, days 1-12): the language

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 1 | What programming is. `fun main()`, `println`, comments, running in IntelliJ and the Playground. | Print your name, age and a joke. | It runs in IntelliJ. |
| 2 | Variables: `val` (cannot change) vs `var`, basic types (`Int`, `Double`, `Boolean`, `String`, `Char`), type inference, string templates (`"Hi $name"`), `readln()`. | A tip calculator and a temperature converter. | You can say why you chose `val` or `var` each time. |
| 3 | Operators, `if` as an expression, `when`, ranges (`1..10`). | A grade calculator and a leap-year checker. | Edge cases (0, negatives) behave as planned. |
| 4 | Loops: `for`, `while`, `do...while`, `step`, `downTo`, `break`, `continue`. | FizzBuzz, a multiplication table, a number-guessing game. | You can trace a loop on paper. |
| 5 | Functions: parameters, default and named arguments, single-expression functions, `Unit`. | Reusable `isPrime`, `factorial`, `max`. | No logic is repeated in `main`. |
| 6 | **Project and review.** | A menu-driven console quiz with a score. | Bad input does not crash it. Committed. |
| 7 | Null safety: nullable types (`String?`), `?.`, `?:`, `!!` (and why to avoid it), `let`, smart casts. | A user-input parser that never throws a null error. | You can explain what Kotlin does that Java cannot. |
| 8 | Classes: constructors, properties, `init`, visibility, **data classes**, `copy`, `toString`. | A `Student` data class and a list of students. | Two equal data classes compare equal. |
| 9 | Inheritance: `open`, `override`, abstract classes, interfaces, `object`, `companion object`. | A `Shape` interface with `Circle` and `Rectangle`. | One loop calls `area()` on all shapes. |
| 10 | Enums, **sealed classes** and `when` as an exhaustive check, extension functions. | An `Expression` sealed class that evaluates itself. | The compiler warns if you miss a case. |
| 11 | Exceptions: `try` as an expression, `throw`, custom exceptions, `Result`, `require` and `check`. | Make the day 6 quiz reject bad input with checks. | No stack trace reaches the user. |
| 12 | **Checkpoint 0 and project.** | A console bank or inventory system with a sealed class, an interface and a data class. | About 200 lines, no copying, tag `kotlin-p1`. |

**Break it (daily):** assign `null` to a non-null type, change a `val`, forget an `else` in `when`, then read each message.

## Part 2 (weeks 3-4, days 13-24): collections, lambdas and coroutines

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 13 | Collections: `List`, `Set`, `Map`, read-only vs mutable (`mutableListOf`), iteration. | A shopping-list manager. | You can say why most collections should be read-only. |
| 14 | Lambdas and higher-order functions: function types, `it`, passing functions as arguments, returning functions. | A `repeat(n, action)` helper and a custom `filter`. | You can read `(Int) -> Boolean` aloud. |
| 15 | Collection operations: `map`, `filter`, `groupBy`, `fold`, `sortedBy`, `associate`, `zip`, sequences. | Statistics on a list of 100 employees. | You replaced every loop with an operation. |
| 16 | Scope functions (`let`, `run`, `apply`, `also`, `with`), `by lazy`, delegation, destructuring. | Tidy up earlier code with scope functions. | You can say when a plain variable is clearer. |
| 17 | Generics: type parameters, constraints, `in` and `out` variance (a light look). | Your own `Stack<T>` and `Result<T>`. | One class works for any type with no casts. |
| 18 | **Project and review.** | A contact manager with search, sort and groupings. | Uses a `Map`, a `List`, and 3 lambdas. |
| 19 | Testing and build: **Gradle** with Kotlin DSL (`build.gradle.kts`), dependencies, `kotlin.test` and JUnit 5. | 15 tests for your contact manager. | `./gradlew test` passes, and one broken test fails. |
| 20 | **Coroutines** part 1: `suspend` functions, `launch`, `runBlocking`, `delay`, structured concurrency. | A program that runs 3 slow tasks in parallel. | It takes 1 delay, not 3. |
| 21 | Coroutines part 2: `async`/`await`, dispatchers (`Main`, `IO`, `Default`), cancellation, exception handling. | Fetch two fake sources in parallel and merge. | Cancelling the scope stops all children. |
| 22 | **Flow**: cold flows, `collect`, `map`, `StateFlow` and `SharedFlow` basics. | A ticker flow that emits every second. | You can say how `StateFlow` differs from a plain flow. |
| 23 | Files, JSON and HTTP: `File` and `Path`, **kotlinx.serialization**, the **Ktor client** for HTTP calls. | Fetch a public API and save the result as JSON. | Handles a missing network with a clear message. |
| 24 | **Checkpoint 1 and project.** | A command-line app that fetches several APIs with coroutines, parses JSON and has tests, in 4 hours. | Tests pass. Tag `kotlin-p2`. |

**Break it (daily):** cancel a coroutine in the middle, throw inside `async`, block the main thread with a long task, call an API with no internet.

## Part 3 (weeks 5-6, days 25-36): Android apps with Jetpack Compose

Compose describes the screen as Kotlin functions. You never write XML layouts in this roadmap.

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 25 | Android Studio setup, emulator or phone, project structure, Gradle, your first `@Composable`: `Text`, `Column`, `Row`, `Button`. | A "Hello, name" app. | It runs on a phone or emulator. |
| 26 | Layouts and modifiers (`padding`, `fillMaxWidth`, `weight`), Material 3 theme, `LazyColumn` lists, images. | A scrolling list of contacts. | It scrolls smoothly with 1000 items. |
| 27 | State: `remember`, `mutableStateOf`, state hoisting, recomposition. | A counter and a text-input form. | You can explain why the screen updates when state changes. |
| 28 | **Project and review.** | A to-do list UI with add, tick and delete (in memory). | Rotating the phone does not lose data. |
| 29 | `ViewModel`, `StateFlow` with Compose, one-way data flow, the Android lifecycle. | Move the to-do state into a `ViewModel`. | The UI only displays state and sends events. |
| 30 | Navigation Compose: screens, routes, arguments, the back stack. | A 3-screen app: list, detail, add. | Back works as users expect. |
| 31 | **Project and review.** | A notes app with list, detail and edit screens (in memory). | Works with no crashes through 10 minutes of use. |
| 32 | **Room** database: entities, DAOs, `Flow` queries, migrations. | Save the notes to a database. | Notes survive killing the app. |
| 33 | Networking: **Retrofit** or Ktor client, JSON, loading, error and empty states, **Coil** for images. | A screen that loads items from a public API. | Offline shows an error, not a crash. |
| 34 | Structure: the repository pattern, dependency injection with **Hilt** (introduction), separating data, domain and UI. | Refactor the notes app into layers. | The `ViewModel` never touches the database directly. |
| 35 | Polish and quality: dark theme, accessibility labels, permissions, unit tests for `ViewModel`s, a UI test with Compose testing. | Add dark mode and 8 tests. | Tests pass, and the app is readable at large font sizes. |
| 36 | **Checkpoint 2 and project.** | A weather or expense app with Room and an API, in 5 hours. | Works offline with cached data. Tag `kotlin-p3`. |

**Break it (daily):** rotate the phone mid-action, turn on airplane mode, deny a permission, enlarge system fonts to the maximum.

## Part 4 (week 7, days 37-42): a back end and shipping

| Day | Do | Done when |
| --- | --- | --- |
| 37 | **Ktor server** (IntelliJ project from start.ktor.io): routing, JSON with `kotlinx.serialization`, plugins, status codes. | `GET` and `POST /notes` work in Postman or `curl`. |
| 38 | Add a database with **Exposed** (or plain JDBC), validation, error handling, and logins with password hashing and **JWT**. | Another user cannot read your notes. |
| 39 | Connect your Android app to your own Ktor API (use `10.0.2.2` from the emulator). Replace the fake data source with the network. | The app and server stay in sync. |
| 40 | Release basics: app signing, R8 shrinking, building an app bundle, the Play Console overview, privacy and permissions notes. A **Dockerfile** for the Ktor server. | `./gradlew bundleRelease` succeeds, and `docker compose up` runs the server. |
| 41 | Polish and docs: README with screenshots, empty and error states, crash logs, a basic CI workflow with **GitHub Actions** that runs tests. | CI is green on every push. |
| 42 | **Review.** Ask a friend to use the app for 10 minutes and fix the top 3 problems. Tag `kotlin-v1`. | A stranger can install and use it from your README. |

Publishing on Google Play needs a one-time registration fee and identity checks; treat it as optional.

## Checkpoints and what comes next

Do not move on until you pass each gate. If you fail, redo the weak days, not the whole part.

- **Checkpoint 0 (day 12).** In 3 hours, with no notes, write a program with a data class, an interface, a sealed class and a `when`. Pass: it compiles and runs after at most 3 fixes.
- **Checkpoint 1 (day 24).** Explain, out loud, null safety, a lambda, a suspend function and the difference between `launch` and `async`. Then build a small tested coroutine program. Pass: you do both without searching.
- **Checkpoint 2 (day 36).** Build a 3-screen Compose app with a `ViewModel` and a Room database in 5 hours. Pass: data survives closing the app, and it survives a rotation.
- **Capstone (day 42).** Passes when a stranger can run your app against your API and CI is green.

**What you can do now.** Build Android apps and small Kotlin back ends. Not covered yet: iOS (Kotlin Multiplatform is a path), Android internals like background work and widgets, and larger app architecture. I can add roadmaps for those.

## Resources

I have not opened these links this session, so check each before relying on it.

| Resource | Use it for | Cost |
| --- | --- | --- |
| [Kotlin Docs and Kotlin Koans-style tour](https://kotlinlang.org/docs/getting-started.html) | The official language guide and tour. | Free |
| [Kotlin Playground](https://play.kotlinlang.org/) | Running code in the browser. | Free |
| [Android Basics with Compose](https://developer.android.com/courses/android-basics-compose/course) | Google's free course for part 3. | Free |
| [Android Developers: Jetpack Compose](https://developer.android.com/develop/ui/compose) | Compose reference and samples. | Free |
| [Coroutines guide](https://kotlinlang.org/docs/coroutines-guide.html) | Days 20-22. | Free |
| [Ktor docs](https://ktor.io/docs/) | Days 37-38. | Free |
| [Room docs](https://developer.android.com/training/data-storage/room) | Day 32. | Free |
| [Exercism Kotlin track](https://exercism.org/tracks/kotlin) | Extra practice with feedback. | Free |
