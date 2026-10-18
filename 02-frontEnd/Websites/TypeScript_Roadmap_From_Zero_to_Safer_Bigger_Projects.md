# TypeScript Roadmap: From Zero to Safer, Bigger Projects

This roadmap takes you from zero to writing safer, larger programs in TypeScript in 24 sessions (4 weeks, about 75 hours). TypeScript is JavaScript plus types: you describe what shape your data has, and the compiler catches mistakes before the code runs. It stands alone: the first 4 sessions are a compact JavaScript primer, so you do not need the JavaScript roadmap first. If you already did that roadmap, skim days 1-4 and start properly at day 5. By the end you can build a typed command-line tool and a typed web API, and you can read the TypeScript used in most modern web projects.

## Start here

**Why TypeScript.** In JavaScript, "5" \* 2 quietly gives 10 and user.nmae quietly gives undefined. TypeScript flags both before you run anything. It does not run in the browser or Node directly: the compiler (tsc) turns .ts files into plain .js files.

**Setup (30 minutes, once):**

1.  Install **VS Code**.

2.  Install **Node.js** (LTS) from nodejs.org and check node -v and npm -v in a terminal.

3.  Make a folder ts-roadmap, then run npm init -y, npm install --save-dev typescript tsx and npx tsc --init.

4.  Run a file with npx tsx day01.ts. Check types with npx tsc --noEmit.

5.  In tsconfig.json, make sure "strict": true is on. Keep it on for the whole roadmap.

6.  Run git init and commit at the end of every session.

**How one session works (about 3 hours):**

| Minutes | Step     | What you do                                                                 |
|---------|----------|-----------------------------------------------------------------------------|
| 10      | Start    | Re-type from memory one snippet from last session.                          |
| 40      | Learn    | Read the listed source, typing every example.                               |
| 90      | Build    | Write the day's program.                                                    |
| 30      | Break it | Write a type error on purpose and read the message until you understand it. |
| 10      | Save     | git commit and write 3 journal lines.                                       |

A session is done only when npx tsc --noEmit reports zero errors, the program runs, and it is committed. The 6th session of each week is a 4-hour project and review.

## Part 1 (weeks 1-2, days 1-12): JavaScript primer, then the type system

| Day | Learn                                                                                                                                | Build                                                                 | Done when                                               |
|-----|--------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------|---------------------------------------------------------|
| 1   | Programming basics: variables (let, const), values and operators, console.log, template strings.                                     | A profile card and a tip calculator.                                  | They run with tsx.                                      |
| 2   | Conditions (if, switch, ternary) and loops (for, while, for...of).                                                                   | FizzBuzz and a multiplication table.                                  | You can trace each loop on paper.                       |
| 3   | Functions (declaration and arrow), arrays and their methods (map, filter, reduce), objects.                                          | Grade statistics for an array of student objects.                     | You use map or filter in place of one loop.             |
| 4   | Primer wrap-up: strings, Map, Set, destructuring, spread, try/catch, JSON. **Project.**                                              | A console contact book storing data in an array of objects.           | It runs with no crash on bad input.                     |
| 5   | First types: string, number, boolean, null, undefined, annotations (let age: number), inference, any (and why to avoid it), unknown. | Add types to day 1 and 2 programs.                                    | tsc reports zero errors and you used no any.            |
| 6   | **Project and review.** Typing functions: parameter and return types, optional and default parameters, void, never.                  | Type every function in your contact book.                             | Passing a wrong argument is a compile error.            |
| 7   | Arrays and tuples, readonly, object types, optional properties (?), type aliases (type).                                             | A typed Student and a function that returns the top student.          | Misspelling a property is an error.                     |
| 8   | Interfaces, interface vs type, extending interfaces, index signatures.                                                               | An Employee hierarchy of interfaces.                                  | You can say when you prefer each of interface and type. |
| 9   | Union types (string \| number), literal types ("north" \| "south"), enums vs literal unions.                                         | A function that accepts number \| string and a typed direction mover. | An invalid direction is rejected at compile time.       |
| 10  | Narrowing: typeof, in, instanceof, equality checks, truthiness, discriminated unions.                                                | A Shape union (circle, square) with an area function.                 | The compiler knows the type inside each branch.         |
| 11  | Type assertions (as), non-null ! (and why to avoid it), unknown with narrowing, errors in catch.                                     | Parse unknown JSON safely into a typed object.                        | No as used where a check would do.                      |
| 12  | **Checkpoint 0 and project.**                                                                                                        | A typed inventory manager with unions, interfaces and narrowing.      | About 150 lines, strict mode, zero errors, tag ts-p1.   |

**Break it (daily):** assign a string to a number, forget a required property, call a method on a value that might be undefined. Read each compiler message fully.

## Part 2 (week 3, days 13-18): generics, classes and modules

| Day | Learn                                                                                                                                        | Build                                                                     | Done when                                                               |
|-----|----------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|-------------------------------------------------------------------------|
| 13  | Generics: function first\<T\>(arr: T\[\]): T, generic interfaces, constraints (extends).                                                     | A generic Stack\<T\> and Queue\<T\>.                                      | One class works for numbers and strings, with no any.                   |
| 14  | Utility types: Partial, Required, Readonly, Pick, Omit, Record. keyof, typeof, indexed access.                                               | An updateUser(user, changes: Partial\<User\>) function.                   | You can build a new type from an old one in one line.                   |
| 15  | Classes: properties, constructors, public/private/protected, readonly, implements, abstract classes.                                         | A BankAccount class that cannot go negative.                              | Private fields cannot be touched from outside (the compiler stops you). |
| 16  | Modules: import/export, export type, project structure, tsconfig options (target, module, outDir, strict, noUncheckedIndexedAccess).         | Split the inventory manager into 3 files.                                 | tsc builds to dist/ and node dist/index.js runs.                        |
| 17  | Async types: Promise\<T\>, async/await, typing a fetch response, handling errors with unknown. Types for libraries: @types/..., .d.ts files. | A typed fetch of a public API with a result type.                         | A wrong field name is a compile error.                                  |
| 18  | **Checkpoint 1 and project.**                                                                                                                | A typed library system: books, members, loans, with generics and classes. | 200 lines, strict, zero errors, tag ts-p2.                              |

**Break it (daily):** use any everywhere and then remove it one place at a time; pass the wrong generic type; try to read a private field.

## Part 3 (week 4, days 19-24): a real typed project

| Day | Do                                                                                                                                                                                                          | Done when                                                         |
|-----|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
| 19  | Set up a proper project: package.json scripts, tsconfig, folder layout (src/, dist/), **ESLint** with typescript-eslint, **Prettier**. Plan a typed **task API** (users, tasks, status as a literal union). | npm run lint and npm run build both pass on an empty project.     |
| 20  | Build the types first: Task, User, request and response shapes, and a Result\<T, E\> union for success or error.                                                                                            | Types compile and read like documentation.                        |
| 21  | Build an **Express** server in TypeScript with typed routes and in-memory storage. Validate input with a schema library such as **Zod** and infer types from it.                                            | POST /tasks rejects bad input and returns a typed response.       |
| 22  | Tests with **Vitest**: unit tests for logic and API tests. Aim for the key paths, not 100 percent.                                                                                                          | npm test passes, with at least 10 tests.                          |
| 23  | Add a small typed client (a Node script or a page) that calls your API with shared types. Fix every any.                                                                                                    | Changing a type in one place breaks the code that needs updating. |
| 24  | **Capstone review.** Write a README, add npm run build, push to GitHub, and ask someone to run it from a fresh clone. Tag ts-v1.                                                                            | A fresh clone runs with npm install, npm test, npm start.         |

**Break it (daily):** change a field type and let the compiler list everything that breaks; send malformed JSON to the server.

## Checkpoints and what comes next

Do not move on until you pass each gate. If you fail, redo the weak days, not the whole part.

- **Checkpoint 0 (day 12).** In 3 hours, with no notes, write a typed program using an interface, a union, narrowing and a function returning an array of objects. Pass: zero strict-mode errors and no any.

- **Checkpoint 1 (day 18).** Explain, out loud, what a generic is, what Partial\<T\> does, and why unknown is safer than any. Then write a generic Stack\<T\> from memory. Pass: you do all of it without searching.

- **Capstone (day 24).** Passes when a fresh clone builds, lints and passes its tests.

**What you can do now.** Read and write TypeScript in real projects. The natural next steps are a front-end framework (React with TypeScript), a real database (SQL with Prisma or Drizzle), and authentication. Those are not in these roadmaps yet; I can add them.

## Resources

I have not opened these links this session, so check each before relying on it.

| Resource                                                                                   | Use it for                                                | Cost          |
|--------------------------------------------------------------------------------------------|-----------------------------------------------------------|---------------|
| [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)             | The official guide for every type feature.                | Free          |
| [TypeScript Playground](https://www.typescriptlang.org/play)                               | Try code and see the compiled JavaScript in the browser.  | Free          |
| [Total TypeScript (Matt Pocock) free tutorials](https://www.totaltypescript.com/tutorials) | Short exercises on narrowing, generics and utility types. | Free          |
| [Execute Program: TypeScript](https://www.executeprogram.com/)                             | Interactive lessons (partly paid).                        | Free and paid |
| [javascript.info](https://javascript.info/)                                                | The JavaScript primer for days 1-4.                       | Free          |
| [Zod docs](https://zod.dev/)                                                               | Runtime validation for day 21.                            | Free          |
| [Vitest docs](https://vitest.dev/)                                                         | Testing on day 22.                                        | Free          |
