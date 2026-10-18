# JavaScript Roadmap: From Zero to Interactive Web Apps

This roadmap takes you from your first variable to a deployed, interactive web app in 48 sessions (8 weeks, about 150 hours). It assumes you have never programmed. JavaScript is the only language that runs in every browser, and with Node.js it also runs servers and tools, so it is the single most useful language for building apps people can open with a link. It stands alone: a small HTML and CSS primer is included, and nothing assumes another roadmap. By the end you can build a to-do app, a weather app, a quiz game and a small API-backed app, and you can read other people's JavaScript.

## Start here

**Setup (45 minutes, once):**

1.  Install **VS Code** and the extensions **Live Server** and **Prettier**.

2.  Use **Chrome**. Press F12 and open the **Console** tab: you can type JavaScript there right now. Try 2 + 2.

3.  Install **Node.js** (the LTS version) from nodejs.org. Check it in a terminal with node -v.

4.  Make a folder js-roadmap with one folder per day. Run git init and commit at the end of every session.

**HTML and CSS primer (15 minutes).** A web page has three layers: HTML is the content, CSS is the look, JavaScript is the behaviour. You need only this to start:

\<!DOCTYPE html\>  
\<html\>  
\<body\>  
\<h1 id="title"\>Hello\</h1\>  
\<button id="btn"\>Click me\</button\>  
\<script src="app.js"\>\</script\>  
\</body\>  
\</html\>

Tags like \<h1\> and \<button\> are elements. id="title" is a name JavaScript can find the element by. The \<script\> line loads your app.js file. In part 2 you will add small CSS rules too; the CSS and HTML roadmaps teach those in depth.

**How one session works (about 3 hours):**

| Minutes | Step     | What you do                                                        |
|---------|----------|--------------------------------------------------------------------|
| 10      | Start    | Re-type from memory one snippet from last session.                 |
| 40      | Learn    | Read the listed source, typing and changing every example.         |
| 90      | Build    | Write the day's program without copying.                           |
| 30      | Break it | Cause errors on purpose. Read each error message aloud and fix it. |
| 10      | Save     | git commit and write 3 journal lines.                              |

The 6th session each week is a 4-hour project and review. A session is done only when your code runs with no errors in the console, is committed, and you can explain it line by line.

## Part 1 (weeks 1-3, days 1-18): the language itself

You work in the console and in Node first, so nothing distracts you from the language.

| Day | Learn                                                                                                                        | Build                                                                                  | Done when                                                |
|-----|------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|----------------------------------------------------------|
| 1   | What programming is. Running JS in the console, in Node and in a page. console.log. Comments.                                | Print your name, age and a joke with console.log.                                      | The script runs in both Node and the browser.            |
| 2   | Variables: let, const, why not var. Naming. Data types: string, number, boolean, null, undefined. typeof.                    | A profile card printed from variables.                                                 | You can say which type each value is without running it. |
| 3   | Operators: arithmetic, assignment, comparison (=== vs ==), logical (&&, \|\|, !). Template strings. Type coercion surprises. | A tip and bill-splitting calculator.                                                   | You can explain why "5" + 1 and "5" - 1 differ.          |
| 4   | Conditions: if, else if, else, switch, the ternary, truthy and falsy values.                                                 | A grade calculator and a leap-year checker.                                            | Edge cases (0, empty string) behave as you planned.      |
| 5   | Loops: for, while, do...while, break, continue.                                                                              | FizzBuzz, a multiplication table, and a number-guessing loop with a fixed secret.      | You can trace a loop by hand on paper.                   |
| 6   | **Project and review.**                                                                                                      | A command-line quiz in Node using readline or prompt() in the browser.                 | Five questions, a running score, committed.              |
| 7   | Functions: declaration, parameters, return values, scope, arrow functions.                                                   | Reusable isPrime, celsiusToF, max(a, b).                                               | No global variables are changed inside functions.        |
| 8   | Functions part 2: default parameters, callbacks, functions as values, closures (intro).                                      | A repeat(n, fn) helper and a counter factory.                                          | You can explain what a closure remembers.                |
| 9   | Strings: methods (slice, split, includes, replace, trim, toUpperCase), escape characters.                                    | A palindrome checker and a word counter.                                               | Works on sentences with capitals and punctuation.        |
| 10  | Arrays: creating, indexing, push, pop, slice, splice, indexOf, includes, nested arrays.                                      | A shopping-list manager (add, remove, show).                                           | Removing the 1st and last items both work.               |
| 11  | Array methods: forEach, map, filter, reduce, find, sort, some, every.                                                        | Grade statistics: average, highest, passing students.                                  | You can rewrite a for loop as map or filter.             |
| 12  | **Project and review.**                                                                                                      | A contact book in the console: add, search, delete.                                    | Data lives in an array of objects. Committed.            |
| 13  | Objects: properties, methods, this, bracket vs dot notation, Object.keys/values/entries, nested objects.                     | A student object with a method that prints a report.                                   | You can say when this is the object.                     |
| 14  | Destructuring, spread and rest, optional chaining (?.), nullish coalescing (??), Map and Set.                                | Remove duplicates and merge two objects.                                               | No undefined crashes on missing fields.                  |
| 15  | Errors and debugging: try/catch/throw, reading stack traces, the browser debugger and breakpoints, console.table.            | Take a buggy 60-line program and fix every bug using breakpoints.                      | You used the debugger, not just console.log.             |
| 16  | Dates and JSON: Date, JSON.stringify, JSON.parse, regular expressions (intro).                                               | A birthday countdown and a JSON export of your contact book.                           | Round-trip: stringify then parse gives the same data.    |
| 17  | Algorithms warm-up: recursion, simple searching and sorting by hand, Big-O in plain words.                                   | Factorial, Fibonacci, binary search.                                                   | You can trace recursion on paper.                        |
| 18  | **Capstone of part 1 and Checkpoint 0.**                                                                                     | A text-based adventure or a console budget tracker with functions, arrays and objects. | About 150 lines, no copying, committed with tag js-p1.   |

**Break it (daily):** pass the wrong type to a function, access undefined.length, run a loop that never ends, then fix each from the error message.

## Part 2 (weeks 4-5, days 19-30): JavaScript in the browser

Now JavaScript changes a real page. Keep a tiny style.css per project; you only need basic rules for colour, spacing and display: flex.

| Day | Learn                                                                                                                                | Build                                                                 | Done when                                               |
|-----|--------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------|---------------------------------------------------------|
| 19  | The DOM: the page as a tree of objects. document.querySelector, querySelectorAll, textContent, innerHTML (and why it can be unsafe). | Change a heading and a paragraph from app.js.                         | You can find any element by selector.                   |
| 20  | Changing the page: createElement, append, remove, classList, setAttribute, style.                                                    | A page that adds list items from an array.                            | Items are created in JS, not typed in HTML.             |
| 21  | Events: addEventListener, click, input, keydown, the event object, event bubbling and delegation.                                    | A counter with buttons for plus, minus and reset.                     | One listener handles many buttons by delegation.        |
| 22  | Forms: submit, preventDefault, reading input values, simple validation messages.                                                     | A sign-up form with live validation.                                  | Bad input shows a message, good input is accepted.      |
| 23  | Project: **to-do app** (add, tick, delete, filter).                                                                                  | A to-do list with filter buttons.                                     | Works with 100 items, and no console errors.            |
| 24  | **Project and review.** localStorage: save and load data.                                                                            | Make the to-do app remember tasks after refresh.                      | Close the tab, reopen, tasks remain.                    |
| 25  | Timers and animation: setTimeout, setInterval, requestAnimationFrame, CSS class toggling for effects.                                | A stopwatch and a digital clock.                                      | The timer does not drift or run twice.                  |
| 26  | Project: **quiz game** with questions in an array of objects, a score and a result screen.                                           | A 10-question quiz.                                                   | Restarting resets all state.                            |
| 27  | Structuring a program: separating data, logic and display; state-driven rendering (a render() function).                             | Refactor the quiz into data, state and render().                      | Changing state and calling render() redraws everything. |
| 28  | Canvas basics: drawing shapes, a game loop, keyboard input.                                                                          | A bouncing ball, then a simple Snake or Pong.                         | 60 frames per second without flicker.                   |
| 29  | Accessibility and quality: keyboard use, aria-label, focus, DevTools Lighthouse, console and network panels.                         | Audit and fix your to-do app.                                         | Lighthouse accessibility 90 or more.                    |
| 30  | **Checkpoint 1 and project.**                                                                                                        | A memory-card game or expense tracker, built in 4 hours without help. | Works, saves data, committed with tag js-p2.            |

**Break it (daily):** select an element that does not exist, add two listeners to one button, store an object in localStorage without JSON.stringify.

## Part 3 (weeks 6-7, days 31-42): async, APIs, modules and tooling

| Day | Learn                                                                                                                | Build                                                                       | Done when                                                |
|-----|----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|----------------------------------------------------------|
| 31  | Asynchronous JavaScript: the event loop in plain words, callbacks, why callback pyramids hurt.                       | A picture of the event loop, drawn by hand, and 3 setTimeout order puzzles. | You can predict the output order of mixed timers.        |
| 32  | Promises: then, catch, finally, Promise.all.                                                                         | Wrap a timer in a promise and chain three steps.                            | Errors are caught in one place.                          |
| 33  | async and await, try/catch with async, sequential vs parallel awaits.                                                | Rewrite day 32's code with async/await.                                     | Parallel tasks use Promise.all.                          |
| 34  | HTTP and fetch: GET and POST, status codes, headers, JSON bodies. Free public APIs.                                  | A page that fetches and shows a list from a public API.                     | Handles loading, success and error states.               |
| 35  | Project: **weather app** using a free weather API and localStorage for recent cities.                                | A weather search page.                                                      | A bad city name shows a friendly error.                  |
| 36  | **Project and review.** Modules: import/export, splitting code into files, ES modules in the browser and in Node.    | Split the weather app into api.js, ui.js, main.js.                          | No file longer than about 100 lines.                     |
| 37  | Classes and OOP in JS: class, constructor, methods, extends, getters, private fields, prototypes (a quick look).     | A BankAccount and a Todo class.                                             | You can say when a plain object is enough.               |
| 38  | Node.js and npm: package.json, installing packages, scripts, node_modules, .gitignore. Read and write files with fs. | A command-line tool that reads a text file and counts words.                | A fresh clone runs with npm install then npm start.      |
| 39  | A tiny server in Node: the http module, then Express: routes, JSON responses, a simple in-memory API.                | A /todos API with GET and POST.                                             | curl or the browser can read and add items.              |
| 40  | Connect the front end to your own API with fetch. CORS in plain words.                                               | The to-do app now saves to your server.                                     | Tasks persist while the server runs.                     |
| 41  | Tooling and testing: Prettier, ESLint, Git branches, and tests with **Vitest** (test, expect).                       | Add 8 tests to your utility functions.                                      | npm test passes, and one deliberately broken test fails. |
| 42  | **Checkpoint 2.** Review week: re-do three earlier days from scratch with no notes.                                  | Rebuild the quiz game with modules and tests.                               | You finish in 3 hours. Tag js-p3.                        |

**Break it (daily):** unplug the internet and see what fetch does; send bad JSON to your API; forget await; remove a catch.

## Part 4 (week 8, days 43-48): capstone web app

Build one app of your own choice, end to end. Good choices: a habit tracker, a budget app, a recipe finder, a multiplayer-less quiz platform, or a notes app with search.

| Day | Do                                                                                                                                           | Done when                               |
|-----|----------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------|
| 43  | Plan: write 5 user stories, sketch 3 screens on paper, choose the data you need and which API (yours or public) it uses.                     | A one-page plan committed to the repo.  |
| 44  | Build the data layer: state, localStorage or your Express API, and tests for the logic.                                                      | The core logic passes tests with no UI. |
| 45  | Build the UI: render functions, events, forms, error and loading states.                                                                     | Every user story works by hand.         |
| 46  | Polish: responsive CSS, keyboard use, empty states, a favicon, no console errors.                                                            | Works at phone and laptop width.        |
| 47  | Deploy the front end free to GitHub Pages or Netlify (and the server to Render or similar if you have one). Write a README with screenshots. | A public link that opens on your phone. |
| 48  | **Review.** Ask a friend to use it for 10 minutes without help and note where they get stuck. Fix the top 3 problems. Tag js-v1.             | A friend finishes the main task alone.  |

## Checkpoints and what comes next

Do not move on until you pass each gate. If you fail, redo the weak days, not the whole part.

- **Checkpoint 0 (day 18).** In 2 hours, with no notes, write a console program that stores records in an array of objects, filters them with filter and map, and prints a summary. Pass: it runs first time after you fix at most 3 errors.

- **Checkpoint 1 (day 30).** In 4 hours build a small DOM app with a form, events, state and localStorage. Pass: no console errors, and it survives a refresh.

- **Checkpoint 2 (day 42).** Explain, out loud, async/await, a closure and an ES module. Then build a page that fetches from an API with error handling. Pass: you do both without searching.

- **Capstone (day 48).** Passes when a stranger can use your live link.

**What you can do now.** Build interactive websites and small full-stack apps, and read most JavaScript you meet. You are not yet job-ready on this alone: frameworks like React, a real database and authentication are the next layer. Do the TypeScript roadmap next; it makes JavaScript safer and is expected for most web jobs.

## Resources

I have not opened these links this session, so check each before relying on it.

| Resource                                                                                     | Use it for                                                                        | Cost |
|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|------|
| [javascript.info](https://javascript.info/)                                                  | The best free full-length text on the language. Follow it alongside the day plan. | Free |
| [MDN JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript)              | The reference for every function and method.                                      | Free |
| [freeCodeCamp JavaScript Algorithms and Data Structures](https://www.freecodecamp.org/learn) | Guided exercises in the browser.                                                  | Free |
| [The Odin Project: Foundations](https://www.theodinproject.com/)                             | A project-based web path with the same aims.                                      | Free |
| [Eloquent JavaScript](https://eloquentjavascript.net/)                                       | A free book for depth after each part.                                            | Free |
| [Node.js docs](https://nodejs.org/en/learn)                                                  | Node and npm lessons for part 3.                                                  | Free |
| [Exercism JavaScript track](https://exercism.org/tracks/javascript)                          | Extra practice with mentor-style feedback.                                        | Free |
| Chrome DevTools                                                                              | Console, debugger and network panels.                                             | Free |
