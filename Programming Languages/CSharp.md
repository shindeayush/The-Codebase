# C# Roadmap: From Zero to Unity Games and Apps

Oct 13, 2026 · @aarhvee

## Start here

This roadmap takes you from never having programmed to building games, web apps, desktop apps and services in C#, starting with a Unity game that has an online leaderboard: 11 weeks, 66 sessions, about 210 hours. No earlier programming is needed, and it does not depend on the C, C++ or Python roadmaps. All four roadmaps start on the same day (suggested: Monday 19 October 2026), and you choose which one to do on each day.

### How the sessions work

- A "Day" in the tables is one study session, not a calendar day. Do them in order, one roadmap day at a time, whenever you choose to work on C#.

- Sessions 1-5 of each week are about 3 hours. Session 6 is a 4-hour project session that ends with a review.

- Every session has the same shape, shown below. Stuck for 20 minutes? Write down what you expected and what happened, then search or ask.

| Time   | Block    | What you do                                                                                      |
|--------|----------|--------------------------------------------------------------------------------------------------|
| 10 min | Start    | Read yesterday's journal line "next first step". Retype a snippet from last session from memory. |
| 40 min | Learn    | Read or watch only the topic in the table. Notes in your own words.                              |
| 90 min | Build    | Write the exercise by hand. Type every line yourself; no copy-paste and no AI-written code.      |
| 30 min | Break it | Add a deliberate mistake, read the error message, fix it.                                        |
| 10 min | End      | Save, commit to Git, and write 3 lines: learned, confused, next first step.                      |

A session is done only when the program runs, you can explain it, and it is committed.

### Setup (about 1 hour)

- The current long-term-support (LTS) release of the .NET SDK from dotnet.microsoft.com.

- VS Code with the C# Dev Kit extension. Visual Studio Community (Windows) also works.

- Git, and a free GitHub account for your journal and projects.

- Unity Hub and the current Unity LTS editor, installed at the start of week 4, not before. The Unity install is large, so check your free disk space (about 10 GB).

- One folder per week, and a journal.md file in it. Version numbers change, so use whatever the sites mark as LTS.

## The 36 sessions

The free spine is Microsoft Learn's C# material and Unity Learn. Resource names are in the last section.

### Week 1: C# basics

| Day | Start here (learn)                                                                                                        | Build                                                                                                                                           | Done when                                                               |
|-----|---------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| 1   | What .NET is. Microsoft Learn, "Get started with C#", first module. Install the .NET SDK and VS Code with the C# Dev Kit. | In a terminal, run dotnet new console -o hello, then dotnet run. Change the message and run it again.                                           | You can say what Program.cs and the .csproj file are for.               |
| 2   | Variables and data types: int, double, decimal, bool, char, string, var. String interpolation with \$"...".               | A profile-card program: read a name and age with Console.ReadLine(), convert with int.Parse, print with interpolation. Print 7 / 2 and 7 / 2.0. | You can explain int against double against decimal, and why 7 / 2 is 3. |
| 3   | Operators, if, else, switch, and &&, \|\|, !.                                                                             | A grade calculator that reads a mark and prints a grade. A leap-year checker.                                                                   | You test every branch at least once.                                    |
| 4   | Loops: for, while, foreach. Arrays and List\<T\>.                                                                         | Multiplication table, sum of a list, FizzBuzz, largest number in a list.                                                                        | You can trace each loop on paper.                                       |
| 5   | Methods: parameters, return values, optional parameters, scope.                                                           | Write IsPrime, Gcd and Power as methods and call them from Main.                                                                                | Each method is tested with 3 inputs.                                    |
| 6   | Project session, then review.                                                                                             | A console number-guessing game, then an in-memory to-do list with add, list, done and quit.                                                     | Both run without crashing on bad input.                                 |

### Week 2: object-oriented C# and collections

| Day | Start here (learn)                                                                             | Build                                                                                                          | Done when                                                           |
|-----|------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| 7   | Classes, objects, fields, properties, constructors.                                            | A Student class with properties and a method that returns the average mark.                                    | You can say what a property gives you that a public field does not. |
| 8   | Inheritance, virtual and override, abstract classes, interfaces.                               | An Entity base with Player and Enemy, called through a List\<Entity\>.                                         | Calling Update() on the list runs the right override for each item. |
| 9   | List\<T\>, Dictionary\<K,V\>, HashSet\<T\>, and what generics are.                             | A word-frequency counter using a dictionary.                                                                   | The counts match a manual count on a short text file.               |
| 10  | LINQ basics: Where, Select, OrderBy, Sum.                                                      | Query a list of students: top 3 by marks, average per class.                                                   | Each query is one expression, with no hand-written loop.            |
| 11  | Value types against reference types, the garbage collector, null and nullable reference types. | Show that copying a struct and copying a class variable behave differently.                                    | You can explain what the garbage collector does.                    |
| 12  | Project session, then review.                                                                  | A library app in the console: books, members, borrow and return, using classes, an interface, a list and LINQ. | 10 manual test cases pass.                                          |

### Week 3: robust code, files, async and tests

| Day | Start here (learn)                                                                               | Build                                                                                                                                      | Done when                                                      |
|-----|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| 13  | try, catch, finally. using and IDisposable, which make sure a resource such as a file is closed. | Read a file inside a using block. Throw and catch a custom exception.                                                                      | The file closes even when an exception is thrown.              |
| 14  | Files and JSON with System.IO and System.Text.Json.                                              | Save and load the library data from day 12 as a JSON file.                                                                                 | Data survives closing the app.                                 |
| 15  | record, enum, pattern matching and switch expressions.                                           | Refactor part of the library app using them.                                                                                               | The code is shorter and the app still works.                   |
| 16  | async, await, Task, and why blocking a thread is bad. HttpClient.                                | Download three web pages at once. Compare the time with downloading them one after another.                                                | The concurrent version is clearly faster, and you can say why. |
| 17  | Unit tests with xUnit and dotnet test.                                                           | Write 10 tests for the library app's logic.                                                                                                | dotnet test passes.                                            |
| 18  | Project session, then review.                                                                    | A command-line weather app using the free Open-Meteo web API: send a request, parse the JSON, print a forecast. Add tests for the parsing. | It works for 3 cities and handles no internet politely.        |

### Week 4: Unity basics

| Day | Start here (learn)                                                                                                             | Build                                                                                | Done when                                                                                                                                  |
|-----|--------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| 19  | Unity Learn, "Unity Essentials". Install Unity Hub and the LTS editor. Learn the Scene, Game, Hierarchy and Inspector windows. | Create a 2D project. Place a player sprite and some platforms. Press Play.           | You can say what a GameObject and a component are.                                                                                         |
| 20  | Scripts: MonoBehaviour, Start, Update, Time.deltaTime, Unity's Input System.                                                   | Move the player with the keyboard at a speed that does not depend on frame rate.     | You can explain why movement is multiplied by deltaTime: the game loop runs a different number of times per second on different computers. |
| 21  | Physics: Rigidbody2D, colliders, triggers, OnTriggerEnter2D.                                                                   | Add coins. Touching one removes it and raises the score.                             | The score is correct after 10 coins.                                                                                                       |
| 22  | Prefabs, Instantiate and Destroy.                                                                                              | Spawn coins and enemies from prefabs at random positions.                            | Enemies and coins appear and disappear without errors in the console.                                                                      |
| 23  | UI with Canvas and TextMeshPro. Game states: playing, game over.                                                               | Show score and lives. Add a game-over screen with a restart button.                  | Restart gives a clean new game.                                                                                                            |
| 24  | Project session, then review.                                                                                                  | A complete small 2D game, "Coin Collector", with menu, score, game over and restart. | 3 friends can play it for 5 minutes without a crash.                                                                                       |

### Week 5: Unity depth

| Day | Start here (learn)                                             | Build                                                                             | Done when                                                |
|-----|----------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------------------------------------|
| 25  | Scenes and scene loading. PlayerPrefs for saving a high score. | Add a main menu scene and a saved high score.                                     | The high score stays after closing the game.             |
| 26  | Sprite animation with the Animator. Audio sources.             | Animate the player (idle and run) and add sound effects and music.                | Animations switch correctly with movement.               |
| 27  | Simple enemy behaviour: patrol and chase.                      | Two enemy types written in C#, one that patrols and one that chases the player.   | The player can lose a life to either.                    |
| 28  | ScriptableObject for game data. C# events.                     | Define enemy types and level settings as ScriptableObjects.                       | You add a new enemy type without changing code.          |
| 29  | The Unity Profiler and making a build.                         | Profile one level, fix the biggest cost, and make a standalone build for your OS. | The build runs outside the editor.                       |
| 30  | Project session, then review.                                  | Extend the game to 3 levels, with a win screen.                                   | The full game can be played start to end from the build. |

### Week 6: apps, a web API and the final capstone

| Day | Start here (learn)                                                                                       | Build                                                                             | Done when                                                           |
|-----|----------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------------------|
| 31  | What a web API is: HTTP, JSON, GET and POST. Microsoft Learn, ASP.NET Core minimal API tutorial.         | dotnet new web. Add a /hello endpoint and a /scores endpoint that returns a list. | Your browser shows JSON from /scores.                               |
| 32  | Request and response models, a POST endpoint, in-memory storage.                                         | A POST endpoint that adds a score for a player.                                   | You can add a score with a tool such as curl and see it in /scores. |
| 33  | Database basics: tables, rows, SELECT, INSERT. SQLite with Entity Framework Core.                        | Store scores in a SQLite database instead of memory.                              | Scores survive restarting the API.                                  |
| 34  | UnityWebRequest in Unity.                                                                                | Your game posts its final score to the API and shows the top 10.                  | A score from the game appears in the top 10.                        |
| 35  | Polish and testing. Write API tests. Optionally try a small desktop app with WPF, WinForms or .NET MAUI. | Add input checks to the API and a README that explains how to run everything.     | A stranger can follow the README and run the API and the game.      |
| 36  | **Final capstone** (4 hours, then review).                                                               | Package the game, the leaderboard API, the README and a 2-minute demo video.      | Tagged final-v1.0 in Git.                                           |

## Part 2 (weeks 7-11): professional C# for any kind of app

Weeks 1-6 gave you C#, Unity and a first web API. This part makes you able to build the kinds of software companies actually ship: well-structured code, databases, full web apps, desktop apps, tests and deployment. Each topic starts from the basics. Days continue from 37.

### Week 7: deeper C# and clean design

| Day | Start here (learn)                                                                 | Build                                                                                     | Done when                                                           |
|-----|------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| 37  | Generics with constraints, delegates, events, Func and Action.                     | An event-based notification system: publishers raise events and subscribers react.        | Two subscribers react to the same event.                            |
| 38  | LINQ in depth: GroupBy, Join, deferred execution.                                  | Read a CSV of sales and produce a report by month and product with LINQ.                  | The totals match a spreadsheet's totals.                            |
| 39  | Interfaces and dependency injection with Microsoft.Extensions.DependencyInjection. | Refactor your library app so its parts depend on interfaces and are injected.             | You can swap the storage class without changing the rest.           |
| 40  | SOLID principles and four patterns: Strategy, Factory, Observer, Repository.       | Implement three of the patterns in small examples.                                        | You can say what problem each one solves.                           |
| 41  | Async in depth: Task.WhenAll, cancellation tokens, IAsyncEnumerable.               | Concurrent downloads that can be cancelled with a key press.                              | Cancelling stops the work and leaves no half-written files.         |
| 42  | Project session, then review.                                                      | A console expense manager using dependency injection, a repository class and xUnit tests. | 20 tests pass and storage can be swapped between a file and memory. |

### Week 8: databases and full web apps

| Day | Start here (learn)                                                                            | Build                                                           | Done when                                                                          |
|-----|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------------|------------------------------------------------------------------------------------|
| 43  | SQL basics (SQLBolt) and Entity Framework Core: DbContext, entities, migrations, with SQLite. | A notes database created by an EF Core migration.               | Notes persist and the schema comes from code.                                      |
| 44  | Relationships: one-to-many and many-to-many. LINQ to Entities.                                | A blog model with posts, comments and tags.                     | A query lists each post with its comment count.                                    |
| 45  | ASP.NET Core Razor Pages (or MVC): pages, forms, validation.                                  | List, create, edit and delete pages for posts.                  | Invalid input shows a clear message and nothing bad is saved.                      |
| 46  | Authentication and authorization with ASP.NET Core Identity. Why passwords are hashed.        | Register and log in, and restrict editing to the post's author. | A logged-out user cannot edit, and you never see a plain password in the database. |
| 47  | Web API good practice: DTOs, validation, error handling, OpenAPI (Swagger) docs.              | Refactor your leaderboard API from week 6 to follow them.       | The docs page lists every endpoint and error.                                      |
| 48  | Project session, then review.                                                                 | A full-stack blog with login, comments and tests.               | 15 tests pass and a friend can register and post.                                  |

### Week 9: desktop apps

| Day | Start here (learn)                                                                                                     | Build                                                                             | Done when                                          |
|-----|------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------------------------------|
| 49  | What a desktop UI framework is. The MVVM idea. Pick WPF (Windows only), Avalonia (Windows, macOS, Linux) or .NET MAUI. | A window with a button and a label.                                               | The window opens and the button changes the label. |
| 50  | Data binding, commands and MVVM.                                                                                       | A counter, then a to-do list built with MVVM.                                     | The UI code has no business logic in it.           |
| 51  | Lists, navigation, dialogs and file pickers.                                                                           | A notes app interface with a list, an editor and open and save dialogs.           | You can open, edit and save a file.                |
| 52  | Persistence and settings.                                                                                              | Store notes in SQLite and remember window size and last file.                     | Data and settings survive restarting.              |
| 53  | Background work and keeping the UI responsive with async.                                                              | Add a search that runs in the background with a progress bar.                     | The window stays responsive during a long search.  |
| 54  | Project session, then review.                                                                                          | A desktop to-do or notes app that syncs with your own API, with a packaged build. | A friend can install and run the build.            |

### Week 10: shipping software

| Day | Start here (learn)                                                                                      | Build                                                               | Done when                                          |
|-----|---------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|----------------------------------------------------|
| 55  | Logging with ILogger, configuration with appsettings.json, secrets with user-secrets.                   | Add logging and configuration to your blog or API.                  | No secret is in Git and logs show useful messages. |
| 56  | Testing in depth: xUnit, mocking with Moq or NSubstitute, integration tests with WebApplicationFactory. | 10 integration tests for your API.                                  | Tests pass in one command.                         |
| 57  | Docker for .NET apps.                                                                                   | A Dockerfile for your API.                                          | docker run starts it and you can use it.           |
| 58  | CI with GitHub Actions: build, test, publish.                                                           | A workflow that builds and tests every push.                        | The workflow is green on GitHub.                   |
| 59  | Deploying: HTTPS, environment settings, a free-tier host (check what is free now).                      | Deploy your API or blog.                                            | It works from your phone at a public address.      |
| 60  | Project session, then review.                                                                           | Add the CI workflow, logging and a README to your deployed project. | A stranger can understand and run it.              |

### Week 11: capstone

| Day | Start here (learn)             | Build                                                                                                                                                                                   | Done when                                |
|-----|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------|
| 61  | Capstone planning.             | Choose one: (A) a full-stack web app; (B) a desktop app; (C) a Unity game with saving and polish; (D) a command-line tool and a library published as a package. Write a one-page scope. | A scope with 5 measurable goals.         |
| 62  | Build session 1.               | Data model and core logic with tests.                                                                                                                                                   | The core works and is tested.            |
| 63  | Build session 2.               | The user interface or API.                                                                                                                                                              | You can use the main feature end to end. |
| 64  | Build session 3.               | Persistence, errors and logging.                                                                                                                                                        | Bad input and failures are handled.      |
| 65  | Build session 4.               | Polish, documentation and deployment or packaging.                                                                                                                                      | A build or live address exists.          |
| 66  | **Capstone review** (4 hours). | README, demo video, tests, tag csharp-v2 in Git.                                                                                                                                        | A stranger can run it from the README.   |

## Checkpoints and what comes next

| Gate        | After  | You must have                                             | If you miss it                                        |
|-------------|--------|-----------------------------------------------------------|-------------------------------------------------------|
| Basics      | Day 6  | The guessing game and to-do list, written without copying | Redo days 3-5 with new exercises                      |
| Objects     | Day 12 | The library app with classes, an interface and LINQ       | Repeat days 7-10                                      |
| Robust code | Day 18 | The weather app with tests                                | Repeat days 13-17                                     |
| First game  | Day 24 | Coin Collector, playable by friends                       | Repeat days 19-23                                     |
| Capstone    | Day 36 | Game plus leaderboard API, README, demo, tag final-v1.0   | Take extra sessions; shipping matters more than speed |

Gates for Part 2 (weeks 7-11):

- Day 42: an expense manager using dependency injection, a repository and 20 tests.

- Day 48: a full-stack blog with login, comments and tests.

- Day 54: a desktop app that syncs with your API and has a packaged build.

- Day 60: a deployed project with CI, logging and a README.

- Day 66: the capstone, tagged csharp-v2.

After day 36: make a second Unity game from scratch with a design you invent, add a login to the API, or try .NET MAUI for a mobile app.

## Resources

These come from my own knowledge of well-known material, not pages I opened while writing, so check each link before relying on it.

| Topic | Resource                                                                                                      | Cost |
|-------|---------------------------------------------------------------------------------------------------------------|------|
| C#    | [Microsoft Learn: C# documentation and Get started with C#](https://learn.microsoft.com/en-us/dotnet/csharp/) | Free |
| C#    | [.NET SDK download](https://dotnet.microsoft.com/download)                                                    | Free |
| Games | [Unity Learn](https://learn.unity.com/)                                                                       | Free |
| Apps  | [ASP.NET Core minimal API tutorial](https://learn.microsoft.com/en-us/aspnet/core/tutorials/min-web-api)      | Free |
| Apps  | [Open-Meteo, a free weather API](https://open-meteo.com/)                                                     | Free |
| Book  | The C# Player's Guide by RB Whitaker                                                                          | Paid |

Added for Part 2 (also from my own knowledge, so check the links):

| Topic     | Resource                                                                          | Cost |
|-----------|-----------------------------------------------------------------------------------|------|
| SQL       | [SQLBolt](https://sqlbolt.com/)                                                   | Free |
| Databases | [Entity Framework Core documentation](https://learn.microsoft.com/en-us/ef/core/) | Free |
| Web       | [ASP.NET Core documentation](https://learn.microsoft.com/en-us/aspnet/core/)      | Free |
| Desktop   | [Avalonia documentation](https://docs.avaloniaui.net/)                            | Free |
| Design    | [Refactoring Guru: design patterns](https://refactoring.guru/design-patterns)     | Free |
| Tools     | [Docker: Get started](https://docs.docker.com/get-started/)                       | Free |
