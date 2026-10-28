# SQL Roadmap: From Zero to Designing and Querying Real Databases

This roadmap takes you from your first query to designing, tuning and securing real databases in 42 sessions (7 weeks, about 130 hours). It assumes you have never used a database. SQL is the language almost every app, report and data job uses to store and ask questions of data, and it changes slowly, so what you learn stays useful for decades. It stands alone and pairs with any programming roadmap. By the end you can design a database from a written spec, write complex queries including joins and window functions, make slow queries fast, and use SQL safely from code.

## Start here

**What a database is.** A relational database stores data in **tables**: each table has **columns** (the kinds of facts) and **rows** (one record each). **SQL** is the language you use to ask questions of tables and to change them. The program that stores and runs it is a **database management system** (DBMS), such as PostgreSQL.

**Which database.** This roadmap uses **PostgreSQL**: it is free, standards-friendly and used widely in industry. About 90 percent of what you learn works unchanged in MySQL, SQL Server, SQLite and Oracle. The roadmap flags the few places where they differ.

**Setup (45 minutes, once):**

1. Install **PostgreSQL** (version 16 or newer) from postgresql.org, or run it with Docker. Remember the password you set for the `postgres` user.
2. Install **DBeaver Community** (free) or use **pgAdmin**. You will write and run queries in it.
3. Load a practice database. Good free choices are **Pagila** (a DVD rental shop) and **Chinook** (a music store); both have PostgreSQL scripts on GitHub. Run the script, then `SELECT * FROM` each table to look around.
4. Make a folder `sql-roadmap` with one `.sql` file per day. Run `git init` and commit at the end of every session. Keep every query you write; they become your own cheat sheet.
5. Optional: install **SQLite** too (it is a single file with no server), which is handy for quick tests.

**How one session works (about 3 hours):**

| Minutes | Step | What you do |
| --- | --- | --- |
| 10 | Start | Re-type from memory one query from last session. |
| 40 | Learn | Read the listed source, running every example and changing it. |
| 90 | Build | Write the day's queries without copying. |
| 30 | Break it | Write wrong queries on purpose and read each error. Predict each result before you run it. |
| 10 | Save | `git commit` and write 3 journal lines. |

The 6th session each week is a 4-hour project and review. A session is done only when every query runs, you predicted what it returns before running it, and you can explain it line by line. Always run a `SELECT` with the same `WHERE` before an `UPDATE` or `DELETE`.

## Part 1 (weeks 1-2, days 1-12): reading and changing data

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 1 | What a database is, tables, rows and columns. Your first `SELECT * FROM table;`. Running queries in DBeaver. | Look at every table in your sample database. | You can name each table's columns and what a row means. |
| 2 | `SELECT` chosen columns, aliases (`AS`), `DISTINCT`, `LIMIT`, arithmetic in queries, comments (`--`). | 10 queries listing customers, products and prices. | You can say what `SELECT DISTINCT` removes. |
| 3 | `WHERE`: comparisons, `AND`, `OR`, `NOT`, `IN`, `BETWEEN`, pattern matching with `LIKE` and `ILIKE`. | 15 filters (for example, customers in one country with a name starting with A). | You can say why `AND` and `OR` need brackets together. |
| 4 | `NULL` (it means "unknown", not zero), `IS NULL`, `COALESCE`, `ORDER BY`, ascending and descending, `OFFSET` and pagination. | A paged product list sorted by price, with missing prices shown as "n/a". | You can say why `= NULL` never matches. |
| 5 | Aggregates: `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`. `GROUP BY`. | Sales per country and orders per customer. | Every non-aggregated column is in `GROUP BY`, and you can say why. |
| 6 | **Project and review.** | Answer 15 business questions about the sample store (top 10 customers, busiest month, and so on). | All 15 answers are saved as queries and committed. |
| 7 | `HAVING` vs `WHERE`, the logical order a query runs in (`FROM`, `WHERE`, `GROUP BY`, `HAVING`, `SELECT`, `ORDER BY`), `COUNT(DISTINCT ...)`. | Find customers who ordered more than 5 times. | You can recite the evaluation order. |
| 8 | Data types: `integer`, `numeric`, `text`, `varchar`, `date`, `timestamp`, `boolean`. Casting (`::`, `CAST`). String, date and number functions. | Clean and format a column of names and dates. | You can say why money is `numeric`, not `float`. |
| 9 | `CREATE TABLE`, primary keys, `NOT NULL`, `DEFAULT`, `UNIQUE`, `CHECK`, identity columns. | Create `students` and `courses` tables with sensible rules. | An invalid insert is rejected by the database itself. |
| 10 | `INSERT`, `UPDATE`, `DELETE`, `RETURNING`, `TRUNCATE`. **Always test the `WHERE` with a `SELECT` first.** A first look at `BEGIN` and `ROLLBACK`. | Insert 20 rows, update 5, delete 3. | You can undo a mistake with `ROLLBACK`. |
| 11 | Foreign keys, `ON DELETE` rules, `ALTER TABLE`, `DROP`, writing a schema script you can re-run. | Add an `enrolments` table linking students to courses. | You cannot enrol a student who does not exist. |
| 12 | **Checkpoint 0 and project.** | Create a small "college" database from scratch (4 tables), fill it with 50 rows, and answer 15 questions. | The whole thing rebuilds from one script. Tag `sql-p1`. |

**Break it (daily):** compare with `= NULL`, group by the wrong column, delete with no `WHERE` (inside a transaction, then roll back), insert a duplicate key, and read each error.

## Part 2 (weeks 3-4, days 13-24): joins, subqueries and window functions

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 13 | `INNER JOIN`, joining on keys, table aliases, `USING`. | Orders with customer names and products. | You can draw what a join does with two small tables on paper. |
| 14 | `LEFT`, `RIGHT` and `FULL JOIN`. Finding rows with no match (the anti-join: `LEFT JOIN ... WHERE b.id IS NULL`). | Customers who never ordered, and products never sold. | You can say when `INNER` and `LEFT` give different row counts. |
| 15 | Joins across 3-4 tables, `CROSS JOIN`, self joins, join pitfalls (duplicated rows, fan-out). | Employees with their managers; a full order report. | Totals match before and after joining. |
| 16 | **Project and review.** | 10 report queries over the sample store, each joining 3 or more tables. | You checked each total against a simple `COUNT` or `SUM`. |
| 17 | Subqueries: in `WHERE`, in `FROM`, scalar subqueries, `IN`, `EXISTS`, correlated subqueries. | Customers who spent more than the average. | You can rewrite a subquery as a join and the reverse. |
| 18 | **CTEs** (`WITH`): naming steps, readability, chaining CTEs, recursive CTEs (an introduction). | Rewrite your hardest query as 3 named steps. | Each step can be run and checked on its own. |
| 19 | Set operations: `UNION`, `UNION ALL`, `INTERSECT`, `EXCEPT`. `CASE WHEN` for conditional values. | Bucket customers into spending tiers. | You can say why `UNION ALL` is faster than `UNION`. |
| 20 | Functions: strings (`concat`, `substring`, `replace`), dates (`date_trunc`, `extract`, intervals, `age`), numbers (`round`, `ceil`), `FILTER`. | Monthly sales and age-of-account reports. | Dates group by month correctly across years. |
| 21 | **Window functions 1:** `OVER`, `PARTITION BY`, `ROW_NUMBER`, `RANK`, `DENSE_RANK`. | Top 3 products per category. | You can say how a window function differs from `GROUP BY`. |
| 22 | Window functions 2: running totals, `LAG` and `LEAD`, moving averages, `NTILE`, frames (`ROWS BETWEEN`). | Month-over-month growth and a 3-month moving average. | The first row of each series handles `NULL` correctly. |
| 23 | **Project and review.** | A sales analytics pack: top N per group, running totals, retention by sign-up month. | Every number is cross-checked with a second method. |
| 24 | **Checkpoint 1 and test.** | A 25-question timed test on a database you have not seen (do it in 4 hours). | At least 22 correct, tag `sql-p2`. |

**Break it (daily):** join without a condition and count the rows, join on a non-unique column, put a filter on the right table in a `LEFT JOIN`'s `WHERE`, and explain each surprising result.

## Part 3 (weeks 5-6, days 25-36): design, speed, safety and SQL from code

| Day | Learn | Build | Done when |
| --- | --- | --- | --- |
| 25 | Data modelling: entities, relationships, one-to-many and many-to-many, junction tables, ER diagrams (dbdiagram.io or draw.io). | An ER diagram for a library. | Every relationship has a key on the correct side. |
| 26 | Normalisation: first, second and third normal form, update and delete anomalies, when to denormalise on purpose. | Normalise a messy spreadsheet into 5 tables. | You can name the anomaly each rule prevents. |
| 27 | **Project and review.** Design from a written spec. | A schema for a booking or e-commerce app, with constraints. | The schema rejects every invalid case in the spec. |
| 28 | **Indexes:** B-tree, how they speed lookups, composite and unique indexes, partial indexes, the cost of writes. | Add indexes to three slow lookups. | You can say what an index cannot help with. |
| 29 | **Reading query plans:** `EXPLAIN` and `EXPLAIN ANALYZE`, sequential vs index scans, join types, spotting a bad plan. | Fix 5 slow queries. | Each fix is proven with timings before and after. |
| 30 | **Project and review.** Generate 1 million rows with `generate_series`, then measure. | A table with 1 million rows and 5 queries, tuned. | You can explain each speed-up in one sentence. |
| 31 | **Transactions:** ACID in plain words, `BEGIN`, `COMMIT`, `ROLLBACK`, isolation levels, locks, deadlocks. | A bank transfer that stays correct when two sessions run at once. | The total balance never changes. |
| 32 | Views and materialised views, functions (an introduction to PL/pgSQL), triggers, audit tables. | An audit trigger that logs every price change. | The log fills automatically, with no app code. |
| 33 | Security: roles and privileges (`GRANT`, `REVOKE`), least privilege, **SQL injection** and parameterised queries, backups with `pg_dump` and `pg_restore`. | A read-only reporting role and a backup you restore. | The report role cannot change data, and the restore matches the original. |
| 34 | Beyond tables: `JSONB`, arrays, full-text search, `COPY` for bulk loading, extensions. | Load a CSV of 100,000 rows and search it. | The load takes seconds, not minutes. |
| 35 | SQL from code: connect from Python (`psycopg`) or Node (`pg`), use parameters, pool connections, read about ORMs and migration tools (Flyway, Alembic, Prisma). | A small script that runs your reports from code. | Input is always passed as a parameter, never glued into the SQL. |
| 36 | **Checkpoint 2 and project.** | From a written spec, design the schema, add indexes, and answer 20 queries, in 5 hours. | Passes the spec and the plan checks. Tag `sql-p3`. |

**Break it (daily):** run two sessions that update the same row, drop an index and re-run the plan, try an injection string against a deliberately unsafe script (your own code on your own machine) and then fix it, restore a backup into an empty database.

## Part 4 (week 7, days 37-42): capstone

Pick one path. Both end with a database someone else can set up from your repository.

- **Path A, an app database.** Design and build the database for an app of your choice (a booking site, a store, a school system, a habit tracker), then a small program or API that uses it.
- **Path B, an analytics project.** Pick a public dataset (for example a government open-data table, a sports or film dataset, or a Kaggle CSV with a licence that allows use), load it, clean it, and answer 15 real questions with SQL.

| Day | Do | Done when |
| --- | --- | --- |
| 37 | Plan: write the questions or user stories, draw the ER diagram or the data flow, choose names and types. | A one-page plan and diagram are committed. |
| 38 | Build the schema (or load and clean the raw data into staging tables) in a re-runnable script. | `psql -f schema.sql` rebuilds everything from empty. |
| 39 | Fill it: seed data you generate (path A) or load the full dataset with `COPY` (path B), then check counts and constraints. | Row counts match the source, and no orphan rows exist. |
| 40 | Write the core queries (path A) or the 15 analysis queries (path B), using joins, CTEs and window functions. | Every query is saved with a comment saying what it answers. |
| 41 | Speed and safety: add indexes with proof from `EXPLAIN ANALYZE`, create a read-only role, take and test a backup. For path A, connect a small script or API with parameterised queries. | The slowest query is under a second at realistic size. |
| 42 | **Review.** Write the README (setup in 5 commands, schema diagram, example queries and results). Ask a friend to rebuild it from scratch and report problems. Tag `sql-v1`. | A stranger can recreate your database from the README alone. |

## Checkpoints and what comes next

Do not move on until you pass each gate. If you fail, redo the weak days, not the whole part.

- **Checkpoint 0 (day 12).** In 2 hours, with no notes, create 3 related tables with keys and constraints, insert data, and answer 10 questions using `WHERE`, `GROUP BY` and `ORDER BY`. Pass: at most 3 fixes.
- **Checkpoint 1 (day 24).** Explain, out loud, `INNER` vs `LEFT JOIN`, `WHERE` vs `HAVING`, a CTE and a window function. Then pass the 25-question test. Pass: 22 or more correct, without searching.
- **Checkpoint 2 (day 36).** Design a schema from a spec, add the right indexes, and explain a query plan. Pass: you can say why each index exists and what a transaction protects.
- **Capstone (day 42).** Passes when a stranger can rebuild your database from the README.

**What you can do now.** Design, query, tune and secure a relational database, and work with data in most jobs: back end, data analysis, QA and DevOps. Not covered yet: database administration in depth (replication, high availability, tuning at scale), data warehouses and tools like dbt, and NoSQL databases (MongoDB, Redis). I can add roadmaps for those. SQL pairs well with the Python, Node.js, Java, Go and PHP roadmaps, which each use a database in their later parts.

## Resources

I have not opened these links this session, so check each before relying on it.

| Resource | Use it for | Cost |
| --- | --- | --- |
| [PostgreSQL documentation: Tutorial](https://www.postgresql.org/docs/current/tutorial.html) | The official intro and the reference for every feature. | Free |
| [SQLBolt](https://sqlbolt.com/) | Short interactive lessons for part 1. | Free |
| [SQLZoo](https://sqlzoo.net/) | Practice questions with instant feedback. | Free |
| [Mode SQL Tutorial](https://mode.com/sql-tutorial/) | Analytics-focused lessons, including window functions. | Free |
| [PostgreSQL Exercises](https://pgexercises.com/) | Practice on a real schema, from simple to hard. | Free |
| [Use The Index, Luke](https://use-the-index-luke.com/) | The best free guide to indexes and query speed (days 28-30). | Free |
| [DB Fiddle](https://www.db-fiddle.com/) | Run SQL in the browser with no setup. | Free |
| [dbdiagram.io](https://dbdiagram.io/) | Drawing ER diagrams for days 25-27. | Free |
| [Pagila](https://github.com/devrimgunduz/pagila) and [Chinook](https://github.com/lerocha/chinook-database) | Sample databases for practice. | Free |
| [OWASP SQL Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html) | Day 33. | Free |
