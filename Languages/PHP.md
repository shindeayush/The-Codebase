# PHP Roadmap: From Zero to Dynamic Websites and Laravel Apps

This roadmap takes you from your first variable to a deployed Laravel web app in 42 sessions (7 weeks, about 130 hours). It assumes you have never programmed. PHP runs a large share of the web (WordPress, many company sites and Laravel apps), it is easy to get started with, and jobs for it are plentiful, especially in freelance and agency work. It stands alone: a short HTML primer is included. By the end you can build a database-driven website with logins, forms and tests, and put it on a server.

## Start here

**How PHP works.** A browser asks a server for a page. The server runs your `.php` file, and whatever it prints becomes the HTML the browser receives. The browser never sees your PHP code.

**HTML primer (10 minutes).** HTML is the content of a page. You need only this to start:

```html
<!DOCTYPE html>
<html>
<body>
  <h1>Hello</h1>
  <p>My first page.</p>
  <form method="post">
    <input name="city">
    <button>Send</button>
  </form>
</body>
</html>
```

Tags like `<h1>` and `<p>` mark up content. A `<form>` sends what the user types to the server, which is where PHP comes in. Save any such file as `.php` and PHP can put values into it.

**Setup (45 minutes, once):**

1. Install **PHP 8.3 or newer**. On Windows, use XAMPP or Laragon; on Mac, Homebrew or Herd; on Linux or WSL2, your package manager. Check `php -v`.
2. Install **VS Code** with the **PHP Intelephense** extension.
3. In a folder, run `php -S localhost:8000` and open `http://localhost:8000` in a browser. This built-in server is all you need for parts 1 and 2.
4. Install **MySQL or MariaDB** (XAMPP and Laragon include it) before day 13, plus a tool like phpMyAdmin or DBeaver.
5. Make a folder `php-roadmap` with one folder per day. Run `git init` and commit at the end of every session.

**How one session works (about 3 hours):**

| Minutes | Step | What you do |
| --- | --- | --- |
| 10 | Start | Re-type from memory one snippet from last session. |
| 40 | Learn | Read the listed source, typing every example. |
| 90 | Build | Write the day's program without copying. |
| 30 | Break it | Cause errors on purpose and read each message. |
| 10 | Save | `git commit` and write 3 journal lines. |

The 6th session each week is a 4-hour project and review. A session is done only when the page runs with no warnings, is committed, and you can explain it line by line.

## Part 1 (weeks 1-2, days 1-12): the language, forms and OOP

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 1 | How PHP works. `<?php ... ?>`, `echo`, mixing PHP into HTML, comments, running the built-in server. | A page that shows your name and today's date. | It runs via `php -S` and the page source shows only HTML. |
| 2 | Variables (`$name`), types (`string`, `int`, `float`, `bool`, `null`), operators, string interpolation, `var_dump`, `declare(strict_types=1)`. | A tip calculator page. | You can say which type each value is. |
| 3 | Conditions (`if`, `match`, ternary), loops (`for`, `while`, `foreach`). | FizzBuzz and a multiplication table as an HTML table. | You can trace each loop on paper. |
| 4 | Functions (parameters, return types, defaults, scope), arrays (indexed and associative), array functions (`array_map`, `array_filter`, `usort`). | A function that finds top students in an array. | Functions have type declarations. |
| 5 | Forms: `$_GET`, `$_POST`, `htmlspecialchars`, validating and sanitising input, redirects. **Never trust user input.** | A sign-up form that shows errors above each field. | Typing `<script>` into a field shows as text, not code. |
| 6 | **Project and review.** | A guestbook that saves messages to a text or JSON file. | Handles empty and very long input. Committed. |
| 7 | `include` and `require`, header and footer templates, separating logic from HTML, file handling (`file_put_contents`, `fopen`). | Convert the guestbook to use shared templates. | Changing the header changes every page. |
| 8 | OOP part 1: classes, objects, constructors (with property promotion), properties, methods, visibility. | A `Product` and a `Cart` class. | The cart total is calculated inside the class. |
| 9 | OOP part 2: inheritance, interfaces, abstract classes, traits, `static`, namespaces, **enums**, `readonly` properties. | A `Payment` interface with two implementations. | You can say when an interface beats inheritance. |
| 10 | Errors and debugging: error reporting, exceptions (`try`, `catch`, `throw`), `var_dump` and **Xdebug** (a first look), logging with `error_log`. | Make the guestbook reject bad input with exceptions. | No raw error text reaches the user. |
| 11 | Dates and times (`DateTimeImmutable`), JSON (`json_encode`, `json_decode`), cookies, file uploads (with size and type checks), regular expressions. | A guestbook with a photo upload. | A 50 MB file or a `.php` file is rejected. |
| 12 | **Checkpoint 0 and project.** | A to-do web app with classes and file storage. | About 200 lines, no copying, tag `php-p1`. |

**Break it (daily):** type `<b>` and quotes into forms, leave a field empty, divide by zero, call a method on `null`, include a missing file.

## Part 2 (weeks 3-4, days 13-24): databases, logins, security and Composer

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 13 | Databases: tables, rows, keys. SQL basics: `CREATE TABLE`, `INSERT`, `SELECT`, `WHERE`, `UPDATE`, `DELETE` in **MySQL or MariaDB**. | A `users` and a `posts` table and 10 queries in phpMyAdmin or the SQL shell. | You can write each query without help. |
| 14 | SQL part 2: `JOIN`, foreign keys, `GROUP BY`, indexes, designing one-to-many tables. | A blog schema with a join query. | You can explain why an index speeds up a query. |
| 15 | **PDO**: connecting, **prepared statements**, fetching rows, transactions. Why string-built SQL is dangerous (SQL injection). | Read and write posts from PHP. | A malicious input string cannot break your query. |
| 16 | CRUD without a framework: list, show, create, edit, delete pages. | A notes app backed by MySQL. | All four operations work from the browser. |
| 17 | Sessions and cookies: `session_start`, login state, logout, the "remember me" idea. | A login-protected page. | Logging out really ends the session. |
| 18 | **Project and review.** Accounts: `password_hash`, `password_verify`, sign-up and log-in. | A user system with registration and login. | No password is ever stored or shown in plain text. |
| 19 | Security: XSS and `htmlspecialchars`, **CSRF tokens**, session fixation, safe uploads, the OWASP Top 10 in plain words. | Harden your user system with a checklist. | You can say what each protection is for. |
| 20 | **Composer**: `composer.json`, installing packages, autoloading with PSR-4, `vendor/`. | Install a package (for example `vlucas/phpdotenv`) and use it. | Your own classes load with no `require` lines. |
| 21 | Structure: a front controller (`index.php`), a tiny router, controllers and views, the MVC idea, environment variables with `.env`. | Refactor the notes app into a mini MVC. | Every request goes through `index.php`. |
| 22 | Quality: **PHPUnit** tests, **PHPStan** static analysis, a code formatter (Pint or PHP-CS-Fixer), Git branches. | 10 tests and a clean PHPStan run. | `composer test` passes, and one broken test fails. |
| 23 | HTTP and APIs: calling APIs with **Guzzle** or `curl`, returning JSON from PHP, REST design, status codes. | A page that shows weather from a public API. | Handles failures and timeouts. |
| 24 | **Checkpoint 1 and project.** | A blog with accounts, posts, comments and tests, in 5 hours. | Tests pass, and the security checklist is done. Tag `php-p2`. |

**Break it (daily):** try SQL injection and XSS on a deliberately unsafe page (your own code, your own machine) and then fix it; submit a form twice; log in from two browsers.

## Part 3 (weeks 5-6, days 25-36): Laravel

Laravel is the most popular PHP framework. It does for you what you built by hand in part 2, so you will understand what it is doing.

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 25 | Install Laravel (via Composer, Laravel Herd, or Laravel Sail), project structure, `php artisan serve`, routes, controllers. | A `/hello` route and a controller. | You can find any file the framework uses. |
| 26 | **Blade** templates: layouts, `@foreach`, components, escaping, assets with Vite. | A page layout shared by 3 pages. | Output is escaped by default, and you know why. |
| 27 | Migrations, **Eloquent** models, factories and seeders, `php artisan tinker`. | A `Post` model with 50 fake posts. | `php artisan migrate:fresh --seed` rebuilds it. |
| 28 | Resource controllers: CRUD, forms, **Form Request** validation, flash messages, route model binding. | Create, edit and delete posts. | Bad input shows errors next to each field. |
| 29 | **Project and review.** | A notes or blog app with a clean UI. | Works with 100 records, committed. |
| 30 | Relationships: `hasMany`, `belongsTo`, many-to-many, eager loading and the N+1 problem. | Posts with comments and tags. | Page load uses a small, fixed number of queries. |
| 31 | Authentication with **Laravel Breeze**, middleware, authorisation with policies and gates. | Users can only edit their own posts. | User A gets 403 on user B's post. |
| 32 | File uploads and storage, mail (log driver), queues and jobs (a first look), events. | Post images and a welcome email. | A 50 MB file is rejected cleanly. |
| 33 | Testing: feature tests, `RefreshDatabase`, factories, **Pest** or PHPUnit. | 15 tests for your app. | `php artisan test` passes. |
| 34 | Performance and config: caching, pagination, `config/` and `.env`, database indexes, `php artisan optimize`. | Paginate and cache a slow page. | The second load is measurably faster. |
| 35 | APIs: API routes, API resources, **Sanctum** tokens, rate limiting. | A JSON API for your posts. | `curl` with a token works; without it you get 401. |
| 36 | **Checkpoint 2 and project.** | A multi-user task manager with logins, permissions and tests, in 5 hours. | Tests pass, and no query runs in a loop. Tag `php-p3`. |

**Break it (daily):** edit another user's record by changing an ID in the URL, submit invalid data, delete a related record, run an N+1 query on purpose and look at the debug bar.

## Part 4 (week 7, days 37-42): ship it

Build one app of your own choice end to end. Good choices: a booking system for a small business, a job board, a recipe site with accounts, a quiz platform, or an inventory tracker.

| Day | Do | Done when |
| --- | --- | --- |
| 37 | Plan: write 8 user stories, sketch 4 screens on paper, list the tables and draw the database. Create the Laravel project, repo and a README skeleton. | The plan and an empty project that runs are committed. |
| 38 | Build the data layer: migrations, models, relationships, seeders. | `migrate:fresh --seed` gives a realistic database. |
| 39 | Build the pages: routes, controllers, Blade views, validation, flash messages. | Every user story works by hand. |
| 40 | Add logins, policies, an API route or two with Sanctum, and tests for every feature. | Another user cannot touch your data, and tests pass. |
| 41 | **Deploy.** Learn the options (shared hosting, a VPS, or a free-tier host with a Docker option), set `APP_ENV=production`, `APP_DEBUG=false`, run migrations on the server, set up HTTPS. Add a **GitHub Actions** workflow that runs the tests. | A public URL with HTTPS and a green CI badge. |
| 42 | **Review.** Ask a friend to use it for 15 minutes without help and fix the top 3 problems. Finish the README with screenshots and setup steps. Tag `php-v1`. | A stranger can use your live app. |

## Checkpoints and what comes next

Do not move on until you pass each gate. If you fail, redo the weak days, not the whole part.

- **Checkpoint 0 (day 12).** In 3 hours, with no notes, build a form page that validates input, saves to a file, and uses one class with a constructor and two methods. Pass: it runs after at most 3 fixes, and `<script>` input shows as text.
- **Checkpoint 1 (day 24).** Explain, out loud, a prepared statement, `password_hash`, a CSRF token and how Composer autoloading works. Then build a small login-protected CRUD app. Pass: you do both without searching.
- **Checkpoint 2 (day 36).** Build a Laravel app with 3 models, relationships, validation, policies and 10 tests in 4 hours. Pass: tests pass, and users cannot see each other's data.
- **Capstone (day 42).** Passes when a stranger can use your live link and CI is green.

**What you can do now.** Build and ship database-driven websites and APIs in Laravel, and read most PHP code you meet. Not covered yet: WordPress theme and plugin work, Symfony, a front-end framework like Vue or React, and performance at large scale. I can add roadmaps for those.

## Resources

I have not opened these links this session, so check each before relying on it.

| Resource | Use it for | Cost |
| --- | --- | --- |
| [PHP: The Right Way](https://phptherightway.com/) | Modern PHP practice, short and free. | Free |
| [PHP Manual](https://www.php.net/manual/en/) | The reference for every function. | Free |
| [Laravel documentation](https://laravel.com/docs) | Part 3, and very well written. | Free |
| [Laracasts: PHP for Beginners](https://laracasts.com/series/php-for-beginners-2023-edition) | Video lessons (some free, some paid). | Free and paid |
| [Laravel Bootcamp](https://bootcamp.laravel.com/) | A guided build of a first app. | Free |
| [PHP Security (OWASP cheat sheets)](https://cheatsheetseries.owasp.org/) | Day 19. | Free |
| [SQLBolt](https://sqlbolt.com/) | SQL practice for days 13-14. | Free |
| [Exercism PHP track](https://exercism.org/tracks/php) | Extra practice with feedback. | Free |
