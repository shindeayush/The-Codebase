# R Roadmap: From Zero to Data Analysis, Models and Dashboards

*48 sessions | 8 weeks | about 152 hours*

A beginner-friendly route from variables and vectors to dependable data pipelines, statistical reasoning, reproducible Quarto reports and an interactive Shiny dashboard. R is a language for statistical computing and graphics. This course assumes no prior programming and uses a small, public or synthetic dataset throughout.

## Start here

**How R works.** You write .R scripts interpreted by the R engine. RStudio (or Positron) provides an editor, console, plots and project tools. R packages extend the language for wrangling, graphics, modeling and apps.

**Setup (once, about 45–90 minutes):**

1.  Install the current stable R from https://cran.r-project.org/; verify R --version or open the R console.

2.  Install RStudio Desktop (https://posit.co/download/rstudio-desktop/) or Positron; then install Git.

3.  Create r-roadmap as an RStudio Project. Make week-01 through week-08 folders and a journal.md; initialize Git.

4.  Install packages as they become relevant: install.packages(c("tidyverse", "testthat", "renv", "DBI", "RSQLite", "shiny")); install Quarto for report weeks.

5.  Keep data/raw/ untouched, data/processed/ generated, and code in scripts/. Do not commit credentials or real private data.

## How each study session works

| **Minutes** | **Block** | **What you do**                                                               |
|-------------|-----------|-------------------------------------------------------------------------------|
| 10          | Start     | Re-type yesterday’s snippet from memory; review your journal’s next step.     |
| 40          | Learn     | Work through just today’s topic; reproduce examples while taking short notes. |
| 90          | Build     | Write the exercise yourself, without copying generated solutions.             |
| 30          | Break it  | Deliberately introduce a bug, reproduce it, inspect the error and fix it.     |
| 10          | Save      | Run checks, commit, and write: learned / confused / next first step.          |

Days are study sessions, not calendar days. Sessions 1–5 each week last about 3 hours; the sixth is a 4-hour project and review. At every checkpoint, repeat weak topics before moving forward.

**Definition of done.** The script runs from a fresh session, produces the expected results, handles missing data explicitly, is committed and can be explained line by line.

Study rule: do not race a calendar. If an exercise needs another session, complete it before proceeding. Keep a journal and a Git commit after every working session.

## Part 1 — Think in R: values, vectors and data frames

### Week 1 — R language and vector thinking (days 1–6)

| **Day** | **Learn**                                                                                               | **Build**                                                                         | **Done when**                                                        |
|---------|---------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|----------------------------------------------------------------------|
| **1**   | What R does; scripts versus console; expressions; print(), cat(), help(), ? and RStudio panes.          | Run 10 expressions; create hello.R that prints a greeting and a numeric result.   | You can source a script and find help for a function.                |
| **2**   | Objects and \<-; numeric, integer, logical, character; class(), typeof(), coercion; NA, NaN, Inf, NULL. | A temperature converter with explicit handling for missing values.                | You predict types and distinguish missing from zero.                 |
| **3**   | Vectors: c(), :, seq(), rep(); vector arithmetic, recycling, length(), names(), indexing.               | A five-student marks calculator and a vector-based shopping budget.               | Subsets, sums and means are correct for five cases.                  |
| **4**   | Comparisons; & versus &&; \| versus \|\|; if / else; ifelse() and if_else() concept.                    | Pass/fail grader and leap-year checker with missing-input handling.               | Each branch is tested, including NA and boundaries.                  |
| **5**   | Functions: arguments, defaults, return values, local scope; stop() and validation.                      | mean_safe(), celsius_to_fahrenheit() and a grade function.                        | Each function handles valid and invalid inputs without hidden state. |
| **6**   | Project / review: build a menu-driven R console program; Git basics.                                    | A personal expense summary with input, categories, totals and a printable report. | Script runs from a fresh session; committed as r-w1.                 |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 2 — Structures, missingness and files (days 7–12)

| **Day** | **Learn**                                                                                     | **Build**                                                                   | **Done when**                                                              |
|---------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|----------------------------------------------------------------------------|
| **7**   | Matrices, arrays and lists; dimension, row/column operations, \[\[ \]\] versus \[ \].         | Create a mini student registry using a list of records.                     | You can retrieve one field and one complete record.                        |
| **8**   | Data frames and tibble basics; factor versus character; str(), summary(), head().             | Build a product table with prices, stock, categories and an ordered factor. | Every column has an intentional type.                                      |
| **9**   | Missing data: is.na(), complete.cases(), na.rm; duplicates, outliers and validation.          | Audit a deliberately messy CSV; count each problem type.                    | Nothing missing is silently treated as zero.                               |
| **10**  | Loops: for, while, next, break; vectorization; apply-family overview.                         | Simulate 100 dice rolls and compare a loop with vectorized code.            | You can explain when vectorization is easier and faster.                   |
| **11**  | Read and write: read.csv(), write.csv(), readr::read_csv(); paths and project-relative files. | Load inventory.csv, clean it and save clean_inventory.csv.                  | A new R session rebuilds the output from raw input.                        |
| **12**  | Checkpoint 0: basics from a blank R script, no copying.                                       | A CSV-backed gradebook with add, filter, totals and missing-value report.   | Handles bad input, uses three functions, and passes five checks; tag r-p1. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Confuse NA with 0; mix integer and character vectors; trigger recycling; index outside a vector and explain the result.

## Part 2 — Clean, explore and communicate data

### Week 3 — Tidy data and manipulation (days 13–18)

| **Day** | **Learn**                                                                                        | **Build**                                                            | **Done when**                                                       |
|---------|--------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|---------------------------------------------------------------------|
| **13**  | Packages with install.packages() and library(); tidyverse; dplyr::select(), filter(), arrange(). | Answer six questions from a small sales table.                       | Every filtered result has a known expected row count.               |
| **14**  | mutate(), case_when(), across(); group_by() and summarise(); counting.                           | Compute monthly sales by region and category.                        | Grouped totals reconcile with the grand total.                      |
| **15**  | Joins: left_join, inner_join, anti_join; keys; relationship cardinality.                         | Join orders, customers and products; find orphan rows.               | No accidental many-to-many row multiplication.                      |
| **16**  | tidyr: pivot_longer/wider, separate_wider_delim, unite; tidy-data rules.                         | Reformat a wide survey table for analysis.                           | Every variable occupies one column in final data.                   |
| **17**  | Dates with lubridate; strings with stringr; parsing and cleaning.                                | Standardize dates, names and region codes in a retail dataset.       | Parsing errors are counted and documented.                          |
| **18**  | Project / review: one end-to-end wrangling pipeline.                                             | Build an automated weekly sales-cleaning script and data dictionary. | Runs in a clean project, exports CSV and logs row counts; tag r-w3. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 4 — Plots, inference and reporting (days 19–24)

| **Day** | **Learn**                                                                        | **Build**                                                                       | **Done when**                                                            |
|---------|----------------------------------------------------------------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------|
| **19**  | ggplot2 grammar: data, aesthetics, geom, labels, themes; scatter and bar charts. | Draw two labeled charts answering concrete questions.                           | Legends, axes and units are understandable without narration.            |
| **20**  | Distributions: histogram, density, box plot; faceting, scales and color choices. | Compare product prices across three groups.                                     | Plots reveal spread, median and outliers appropriately.                  |
| **21**  | Statistical summaries: mean/median, sd, quantiles, correlation; sampling bias.   | Explore a built-in dataset and write five evidence-based findings.              | Statistics match manual spot checks.                                     |
| **22**  | Inference foundations: samples, confidence intervals, t-tests and assumptions.   | Compare two groups; calculate a confidence interval.                            | Interpret uncertainty without claiming causation.                        |
| **23**  | Reproducible reports in Quarto: .qmd, code chunks, parameters and citations.     | Create a 3-page HTML analysis with data, plots and conclusions.                 | quarto render works without manual clicking.                             |
| **24**  | Checkpoint 1: exploratory analysis from unfamiliar data.                         | Deliver a documented EDA report with four plots and one statistical comparison. | No unreported missing values; report renders from a clean run; tag r-p2. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Read a CSV with wrong types; break a join key; quietly lose rows with na.omit(); accidentally use a factor as a number.

## Part 3 — Model, automate and test

### Week 5 — Models and their limits (days 25–30)

| **Day** | **Learn**                                                                                    | **Build**                                                                 | **Done when**                                            |
|---------|----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|----------------------------------------------------------|
| **25**  | Statistical modeling: formula syntax; lm(), coefficients, residuals and training/test split. | Fit a price-prediction regression with three features.                    | Explain each coefficient and inspect residuals.          |
| **26**  | Model diagnostics: linearity, leverage, outliers, leakage and cross-validation intuition.    | Compare a baseline against a linear model on held-out data.               | No test-data leakage and an error metric is printed.     |
| **27**  | Classification: logistic regression with glm(family=binomial); probabilities and threshold.  | Predict a binary label from sample customer data.                         | Confusion matrix and precision/recall are correct.       |
| **28**  | Resampling and feature recipes using tidymodels (optional: base R alternative).              | Create reproducible folds and preprocess a numeric + categorical dataset. | Resamples preserve the target and use a fixed seed.      |
| **29**  | Communicating models: confidence versus prediction intervals; fairness and limits.           | Write a model card: data origin, metrics, limits, ethical caveats.        | Claims are supported by results, not only a score.       |
| **30**  | Project / review: basic end-to-end predictive analysis.                                      | Model customer behavior; compare baseline and two candidate models.       | Reproducible split, metrics table, model card; tag r-w5. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 6 — Databases, reusable code and tests (days 31–36)

| **Day** | **Learn**                                                                              | **Build**                                                                     | **Done when**                                                   |
|---------|----------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------|
| **31**  | SQL for analysts: SELECT, WHERE, GROUP BY, JOIN; DBI and dbplyr; SQLite database.      | Create a SQLite store from the cleaned sales data and query it.               | Query results match equivalent in-memory summaries.             |
| **32**  | Functional tools: purrr::map(), map_dfr(), anonymous functions and error-safe mapping. | Process 12 monthly CSV files into one verified table.                         | One malformed file is reported without hiding others.           |
| **33**  | Writing reusable functions; roxygen2 style documentation; simple package structure.    | Extract three reusable cleaning helpers with examples.                        | Functions are documented and work on new data.                  |
| **34**  | Testing with testthat; edge cases, fixtures, assertions and snapshot awareness.        | Write 15 tests for your cleaning and summary functions.                       | One intentional bug causes a red test; fixes turn it green.     |
| **35**  | Project reproducibility: renv; Git; logging; secrets and relative paths.               | Restore dependencies; add README, config and sample-data instructions.        | Another machine can recreate the environment from instructions. |
| **36**  | Checkpoint 2: reusable analysis pipeline.                                              | Process multiple inputs, query SQLite and produce a Quarto report with tests. | 15 tests pass and a clean restore/render succeeds; tag r-p3.    |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Plot a misleading truncated axis, change a model using test data, omit set.seed, and check why results differ.

## Part 4 — Build and ship a reproducible dashboard

### Week 7 — Interactive Shiny applications (days 37–42)

| **Day** | **Learn**                                                                                       | **Build**                                                                 | **Done when**                                                      |
|---------|-------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|--------------------------------------------------------------------|
| **37**  | Shiny basics: ui, server, inputs, outputs, renderPlot and renderTable.                          | Build a single-page sales app with selector and plot.                     | Controls update both plot and summary.                             |
| **38**  | Reactivity: reactive(), observeEvent(), req(), validate()/need(); avoiding circular logic.      | Add date filters and a reactive table with helpful empty-state messages.  | No error appears when filters return zero rows.                    |
| **39**  | Shiny modules and app organization; separation of data, UI and analysis.                        | Split a growing app into clean files/functions.                           | You can add a new chart without editing unrelated logic.           |
| **40**  | DT or native tables; file uploads/downloads; accessibility and privacy.                         | Add a CSV uploader, previews and download for filtered data.              | Wrong file schema gets a useful error; no private data exposed.    |
| **41**  | Performance and deployment: caching, reactive invalidation, shinyapps.io/Posit Connect options. | Profile the slowest calculation and deploy a demo with sample data.       | App runs through a shareable address or a repeatable local launch. |
| **42**  | Project / review: dashboard integration.                                                        | Interactive analytics dashboard with three KPIs, two charts and download. | A new user can complete three tasks without guidance; tag r-w7.    |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

### Week 8 — End-to-end data science capstone (days 43–48)

| **Day** | **Learn**                                                                      | **Build**                                                                   | **Done when**                                                      |
|---------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------|--------------------------------------------------------------------|
| **43**  | Capstone scope: audience, question, data provenance, success criteria, limits. | Write a one-page plan for a public-data analysis + Shiny dashboard.         | Plan names three measurable questions and the data license.        |
| **44**  | Data ingestion and quality gates.                                              | Implement raw-to-clean pipeline and a data dictionary.                      | Counts reconcile; failures are logged; data is reproducible.       |
| **45**  | Analysis and visual design.                                                    | Build four meaningful visuals and a model or statistical comparison.        | Each figure supports a named question with readable units.         |
| **46**  | Productize: connect dashboard, report and shared calculations.                 | Release one workflow: refresh data, render report, open dashboard.          | No duplicate business logic and inputs cannot crash the app.       |
| **47**  | Quality: test, review, accessibility, packaging, docs.                         | Add 20 tests, README, sample data, screenshots and privacy note.            | A fresh machine can follow README; tests pass.                     |
| **48**  | Final capstone review; tell the story responsibly.                             | Record a short demo, present findings and publish/deploy where appropriate. | A stranger can reproduce analysis and operate dashboard; tag r-v1. |

**Review:** Explain your code aloud, record one mistake and one fix, commit the week’s project.

**Break it this fortnight:** Give Shiny an empty input, an invalid upload, a slow reactive calculation and a failing file path.

## Checkpoints and what comes next

These are gates, not optional homework. If you cannot complete a gate without copying, review the relevant sessions and repeat the project. Document what failed and what changed.

| **Gate**                 | **What you must show**                                                                         |
|--------------------------|------------------------------------------------------------------------------------------------|
| **Day 12 · Foundations** | Build a gradebook from memory with functions, data structures, file I/O and explicit NA rules. |
| **Day 24 · Analysis**    | Reproduce a four-plot Quarto EDA from raw data; interpret a statistical comparison.            |
| **Day 36 · Engineering** | A reusable pipeline with database query, renv lockfile and at least 15 passing tests.          |
| **Day 48 · Capstone**    | A reproducible dashboard/report with a demo, documentation and transparent limitations.        |

## Your portfolio at the end

- CSV-backed analysis pipeline with data validation and tests

- Quarto report with four interpretable plots and statistical caveats

- Shiny app with filters, KPIs, file export and explanatory README

## After the last session

Go deeper in causal inference, survey analysis, time series, geospatial data, Bayesian modeling, or package development. Use only datasets you have rights to publish.

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
<td><strong>R manuals</strong></td>
<td>Base language, data structures, help system<br />
https://cran.r-project.org/manuals.html</td>
</tr>
<tr class="even">
<td><strong>R for Data Science (2e)</strong></td>
<td>Data import, cleaning, plotting and pipelines<br />
https://r4ds.hadley.nz/</td>
</tr>
<tr class="odd">
<td><strong>ggplot2 reference</strong></td>
<td>Chart grammar and examples<br />
https://ggplot2.tidyverse.org/</td>
</tr>
<tr class="even">
<td><strong>Quarto get started</strong></td>
<td>Reproducible HTML/PDF/Word reports<br />
https://quarto.org/docs/get-started/</td>
</tr>
<tr class="odd">
<td><strong>Shiny tutorials</strong></td>
<td>Dashboard UI and reactivity<br />
https://shiny.posit.co/r/getstarted/</td>
</tr>
<tr class="even">
<td><strong>tidymodels</strong></td>
<td>Modeling and resampling workflow<br />
https://www.tidymodels.org/start/</td>
</tr>
<tr class="odd">
<td><strong>testthat</strong></td>
<td>Automated testing in R<br />
https://testthat.r-lib.org/</td>
</tr>
</tbody>
</table>

**About this guide.** Structure adapted from the three supplied learning roadmaps (Java, Go and C++): independent beginner entry, a repeatable study rhythm, day-by-day Learn / Build / Done when tables, project reviews, checkpoints and a shipped capstone. Language-specific topics and exercises here are newly authored; the guides are not translations of those documents.
