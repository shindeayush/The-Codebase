# Java Roadmap: From Zero to Backend Systems and Apps

This roadmap takes you from your first variable to a deployed Spring Boot back end in 60 sessions (10 weeks, about 190 hours). It assumes you have never programmed. Java is one of the most widely used languages for company back ends, banking and large systems, and for Android's older code. It is strict and verbose, which makes it a good teacher of object-oriented design. It stands alone and starts from zero. By the end you can build a REST API with a real database, logins and tests, and run it in Docker.

## Start here

**How Java works.** You write `.java` files, the compiler turns them into bytecode (`.class` files), and the Java Virtual Machine (JVM) runs that bytecode on any operating system. The **JDK** (Java Development Kit) contains the compiler and the JVM.

**Setup (45 minutes, once):**

1. Install a **JDK 21 or newer** (the current long-term-support release is the safe choice). Eclipse Temurin from adoptium.net is a good free build. Check `java -version` and `javac -version`.
2. Install **IntelliJ IDEA Community Edition** (free). It runs, debugs and refactors for you.
3. Make a folder `java-roadmap`, create one IntelliJ project in it, and add one package per day. Run `git init` and commit at the end of every session.
4. Learn `jshell`, the built-in Java console. Type `2 + 2` into it.

**How one session works (about 3 hours):**

| Minutes | Step | What you do |
| --- | --- | --- |
| 10 | Start | Re-type from memory one snippet from last session. |
| 40 | Learn | Read the listed source, typing every example. |
| 90 | Build | Write the day's program without copying. |
| 30 | Break it | Cause compile errors and exceptions on purpose and read each message. |
| 10 | Save | `git commit` and write 3 journal lines. |

The 6th session each week is a 4-hour project and review. A session is done only when the program compiles with no warnings you do not understand, runs, is committed, and you can explain it line by line.

## Part 1 (weeks 1-3, days 1-18): the language and object-oriented programming

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 1 | What programming is. The compile and run cycle, `public static void main`, `System.out.println`, comments. | Hello World, then a program printing your name, age and a joke. | You can explain what `javac` and `java` each do. |
| 2 | Variables and types: `int`, `long`, `double`, `boolean`, `char`, `String`, `var`, constants with `final`. Casting and type conversion. Reading input with `Scanner`. | A temperature converter that asks the user for a number. | It handles integers and decimals correctly. |
| 3 | Operators (arithmetic, comparison, logical), integer division and overflow, `if`/`else if`/`else`, `switch` expressions. | A grade calculator and a leap-year checker. | Edge cases (0, negatives) behave as planned. |
| 4 | Loops: `for`, enhanced `for`, `while`, `do...while`, `break`, `continue`, nested loops. | FizzBuzz, a multiplication table and a number-guessing game. | You can trace a loop on paper. |
| 5 | Methods: parameters, return types, `void`, overloading, scope, call stack. | Reusable `isPrime`, `factorial`, `max` methods. | No logic is repeated in `main`. |
| 6 | **Project and review.** | A console menu calculator with a loop and methods. | Handles bad input without crashing, committed. |
| 7 | Arrays: creating, indexing, loops over arrays, 2D arrays, `Arrays.sort`, `Arrays.toString`, copying. | Find min, max and average of an array, and a tic-tac-toe board. | You can name the cause of `ArrayIndexOutOfBoundsException`. |
| 8 | Strings in depth: immutability, methods (`substring`, `split`, `equals`, `compareTo`), `StringBuilder`, text blocks, `String.format`. | A palindrome checker and a word counter. | You use `.equals`, not `==`, for strings, and can say why. |
| 9 | Classes and objects: fields, constructors, `this`, instance methods, object references vs primitives. | A `Student` class and a program that stores 5 students. | You can draw objects on the heap on paper. |
| 10 | Encapsulation: `private`, getters and setters, validation in setters, `static` fields and methods, `final`. | A `BankAccount` that cannot go negative. | The balance cannot be changed from outside. |
| 11 | Inheritance: `extends`, `super`, method overriding, `@Override`, polymorphism, `instanceof`. | A `Shape` base class with `Circle` and `Rectangle` subclasses. | One loop calls `area()` on all shapes. |
| 12 | **Project and review.** | A library system: books, members, lending, with 4 classes. | Rules (no double lending) live in the classes. |
| 13 | Abstract classes, interfaces, default methods, "composition over inheritance". | A `Payment` interface with card and cash implementations. | You can say when to pick an interface over a base class. |
| 14 | Enums, records, immutability, `equals`, `hashCode`, `toString`. | A `Money` record and a `Day` enum with behaviour. | Two equal records compare equal. |
| 15 | Packages and imports, access levels, project layout, the IntelliJ debugger: breakpoints, step in, step over, watches. | Fix a 60-line buggy program using only the debugger. | You used breakpoints, not just `println`. |
| 16 | The `Object` class, `Comparable` and `Comparator`, sorting your own objects, nested and inner classes. | Sort students by grade then name. | Changing the sort order is one line. |
| 17 | Recursion, simple search and sort algorithms by hand (linear and binary search, bubble sort), Big-O in plain words. | Factorial, Fibonacci, binary search. | You can trace recursion on paper. |
| 18 | **Checkpoint 0 and project.** | A console bank or inventory system with inheritance, an interface, an enum and sorting. | About 250 lines, no copying, tag `java-p1`. |

**Break it (daily):** call a method on a `null` reference, divide by zero, mix up `==` and `.equals`, forget a `return`, then read each error.

## Part 2 (weeks 4-6, days 19-36): the standard library and professional habits

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 19 | Exceptions: `try`/`catch`/`finally`, checked vs unchecked, `throw`, custom exceptions, try-with-resources. | Make the day 18 system reject bad input with custom exceptions. | No stack trace reaches the user. |
| 20 | Generics: generic classes and methods, bounded types, a first look at wildcards. | Your own `Box<T>` and `Pair<A, B>`. | One class works for any type with no casts. |
| 21 | Collections part 1: `List`, `ArrayList`, `LinkedList`, iteration, the `Iterator`. | A to-do list manager. | You can say when `LinkedList` is a bad choice. |
| 22 | Collections part 2: `Set`, `HashSet`, `TreeSet`, `Map`, `HashMap`, `TreeMap`. How hashing works. | A word-frequency counter. | You can explain what `hashCode` is for. |
| 23 | Collections part 3: `Queue`, `Deque`, `PriorityQueue`, the `Collections` helper class, choosing the right collection. | A task scheduler using a priority queue. | Each collection choice has a one-line reason. |
| 24 | **Project and review.** | A contact manager with search, sort and duplicate checks. | Uses at least a `Map` and a `List`. |
| 25 | Lambdas, functional interfaces (`Function`, `Predicate`, `Consumer`, `Supplier`), method references. | Replace loops and comparators in earlier code with lambdas. | Code is shorter and still readable. |
| 26 | Streams: `filter`, `map`, `sorted`, `reduce`, `collect`, `Collectors.groupingBy`, `flatMap`. | Statistics on a list of 100 employees. | You can say when a plain loop is clearer. |
| 27 | Modern Java: `Optional`, `var`, records and sealed classes with pattern matching in `switch`, text blocks. | Model a `Shape` hierarchy with sealed types. | The compiler checks that `switch` covers every case. |
| 28 | Files and input/output: `Path`, `Files`, reading and writing text, `BufferedReader`, try-with-resources, JSON with **Jackson**. | Save and load your contact manager as JSON. | Data survives a restart, with errors handled. |
| 29 | Dates and text: `java.time` (`LocalDate`, `Duration`), formatting, regular expressions. | A birthday-reminder program. | No old `Date` class used. |
| 30 | **Project and review.** | A log-file analyser using streams. | Handles a 100 MB file without running out of memory. |
| 31 | Testing with **JUnit 5**: `@Test`, assertions, `@BeforeEach`, testing exceptions, parameterised tests. | 15 tests for your contact manager. | Tests pass, and one broken test fails. |
| 32 | Build tools: **Maven** (`pom.xml`, dependencies, lifecycle `compile`/`test`/`package`), a look at Gradle. | Convert a project to Maven and build a runnable JAR. | `java -jar` runs your app. |
| 33 | Clean code: naming, small methods, the SOLID principles in plain words, code review checklists. | Refactor a messy 150-line class. | Tests still pass after the refactor. |
| 34 | Design patterns, lightly: strategy, factory, builder, observer. | Use two patterns in your expense tracker. | You can say what problem each pattern solves. |
| 35 | Mini-project with tests first (TDD): write the test, make it pass, refactor. | A parking-lot or ATM simulation. | Every public method has a test. |
| 36 | **Checkpoint 1 and project.** | A command-line expense tracker with file storage, streams, tests and Maven, in 5 hours. | Builds with `mvn package` and has 20 or more tests. Tag `java-p2`. |

**Break it (daily):** change a test to fail on purpose, read the stack trace from the bottom up, feed a stream an empty list, and break `hashCode` and watch a `HashMap` misbehave.

## Part 3 (weeks 7-9, days 37-54): databases, concurrency and Spring Boot

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 37 | Databases: tables, rows, keys. SQL basics: `CREATE TABLE`, `INSERT`, `SELECT`, `WHERE`, `UPDATE`, `DELETE`. Use **PostgreSQL** (or SQLite to start). | A `students` table and 10 queries in a SQL shell. | You can write each query without help. |
| 38 | SQL part 2: `JOIN`, foreign keys, `GROUP BY`, indexes, designing one-to-many tables. | A schema for a library with a join query. | You can explain why an index speeds up a query. |
| 39 | **JDBC**: connections, `PreparedStatement` (never concatenate SQL), result sets, transactions. | Read and write rows from Java. | A malicious input string cannot break your query. |
| 40 | **Project and review.** A repository layer with tests. | A `BookRepository` with CRUD and tests. | Tests run against a clean database each time. |
| 41 | Concurrency part 1: threads, `Runnable`, `ExecutorService`, `join`. | Download 5 files in parallel. | The main thread waits for all workers. |
| 42 | Concurrency part 2: race conditions, `synchronized`, locks, `AtomicInteger`, `ConcurrentHashMap`, deadlock. | A bank transfer that stays correct under 100 threads. | The total balance never changes. |
| 43 | Concurrency part 3: `CompletableFuture`, virtual threads (Java 21), when to use which. | Fetch 3 APIs at once and merge the results. | You can say why virtual threads suit many waiting tasks. |
| 44 | HTTP and REST: methods, status codes, JSON, REST design, `java.net.http.HttpClient`. | A client that calls a public API. | Handles timeouts and non-200 replies. |
| 45 | **Spring Boot** basics: start.spring.io, `@RestController`, `@GetMapping`, inversion of control and dependency injection, project layout. | A `/hello` and `/items` API. | You can explain what a Spring bean is. |
| 46 | Spring MVC: path variables, request bodies, validation with Jakarta Validation, `@ControllerAdvice` error handling, DTOs. | A notes API with validation. | Bad input returns 400 with a clear message. |
| 47 | **Spring Data JPA**: entities, repositories, relationships, schema migrations with **Flyway**, the N+1 problem. | Put the notes in PostgreSQL. | Data survives a restart, and migrations are in version control. |
| 48 | **Project and review.** | A notes API with users, tags and pagination. | Documented endpoints, committed. |
| 49 | Testing Spring apps: `@SpringBootTest`, `MockMvc`, **Mockito**, **Testcontainers** (intro). | 15 tests for the notes API. | Tests pass with a real throwaway database. |
| 50 | Security: **Spring Security** basics, password hashing with BCrypt, sessions vs **JWT**, protecting routes, roles. | Sign up, log in and a protected route. | A user cannot read another user's notes. |
| 51 | Configuration and operations: profiles, environment variables, SLF4J logging, **Actuator** health checks. | Separate dev and prod settings. | No secret is committed to Git. |
| 52 | Performance and caching: pagination, indexes, `@Cacheable`, measuring with simple timings. | Cache a slow endpoint and measure it. | The second call is measurably faster. |
| 53 | Background work: `@Scheduled`, `@Async`, and the idea of message queues (Kafka and RabbitMQ, concepts only). | A nightly cleanup job. | The job runs on schedule and logs its result. |
| 54 | **Checkpoint 2 and project.** | A multi-user task API with logins, permissions and tests, in 5 hours. | Tests pass and a security checklist is complete. Tag `java-p3`. |

**Break it (daily):** try SQL injection on a deliberately unsafe method (your own code, your own machine) and then fix it; remove a transaction and watch data corrupt; start 1000 threads.

## Part 4 (week 10, days 55-60): ship it

Build one API of your own choice end to end. Good choices: a habit tracker, an expense splitter, a library system, a ticket-booking API, or a quiz platform.

| Day | Do | Done when |
| --- | --- | --- |
| 55 | Plan: write 8 user stories, list endpoints and tables, draw the database on paper. Set up the Maven project, Flyway migrations and a README skeleton. | The plan and an empty project that builds are committed. |
| 56 | Build the data layer and core endpoints with validation and error handling. | Core routes work in Postman or `curl`. |
| 57 | Add logins, permissions, pagination and tests for every endpoint. | Another user cannot touch your data. |
| 58 | **Docker:** a multi-stage `Dockerfile`, `docker-compose.yml` for the app and PostgreSQL, health checks. | A fresh clone runs with `docker compose up`. |
| 59 | CI and deploy: a **GitHub Actions** workflow that builds and tests on every push, then deploy to a free host with a Docker option. | A public URL and a green CI badge. |
| 60 | **Review.** Ask a friend to try it with Postman for 15 minutes and fix the top 3 problems. Finish the README with endpoints and a `curl` example. Tag `java-v1`. | A stranger can use your live API from the README alone. |

## Checkpoints and what comes next

Do not move on until you pass each gate. If you fail, redo the weak days, not the whole part.

- **Checkpoint 0 (day 18).** In 3 hours, with no notes, write a program with an abstract class or interface, two subclasses, an enum and a sorted list of objects. Pass: it compiles and runs after at most 3 fixes.
- **Checkpoint 1 (day 36).** Explain, out loud, `equals` and `hashCode`, a `HashMap`, a stream pipeline and checked vs unchecked exceptions. Then build a small tested Maven project. Pass: you do both without searching.
- **Checkpoint 2 (day 54).** Build a REST API with 4 endpoints, validation, a database and 10 tests in 4 hours. Pass: all tests pass, and you can explain dependency injection.
- **Capstone (day 60).** Passes when a stranger can use your live link and CI is green.

**What you can do now.** Build and ship Java back ends, read most enterprise Java, and move to Kotlin quickly (the Kotlin roadmap shares the JVM). Not covered yet: microservices and cloud services in depth, a front-end framework, and system design for large scale. I can add roadmaps for those.

## Resources

I have not opened these links this session, so check each before relying on it.

| Resource | Use it for | Cost |
| --- | --- | --- |
| [MOOC.fi Java Programming I and II](https://java-programming.mooc.fi/) | A free, exercise-heavy university course from zero. The best companion to this plan. | Free |
| [Dev.java](https://dev.java/learn/) | The official Oracle learning hub. | Free |
| [Oracle Java Tutorials](https://docs.oracle.com/javase/tutorial/) | The reference for core language features. | Free |
| [Spring Boot docs and guides](https://spring.io/guides) | Step-by-step guides for days 45-54. | Free |
| [Baeldung](https://www.baeldung.com/) | Short articles on almost any Java or Spring topic. | Free |
| [JUnit 5 user guide](https://junit.org/junit5/docs/current/user-guide/) | Day 31. | Free |
| [SQLBolt](https://sqlbolt.com/) | SQL practice for days 37-38. | Free |
| [Docker Get Started](https://docs.docker.com/get-started/) | Day 58. | Free |
| [Exercism Java track](https://exercism.org/tracks/java) | Extra practice with feedback. | Free |
