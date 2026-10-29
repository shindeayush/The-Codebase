# pandas (Python) Roadmap: From Zero to Data Cleaning, Analysis and Reproducible Pipelines

*Created: 29 October 2026 · 9 weeks · 54 sessions · ~171 guided hours*

## Start here

Go from Series and DataFrames to reliable ingestion, joins, groupby, time series, missing-data reasoning, efficient pipelines and checked analytical reports.

**Prerequisites:** Python, dictionaries, functions, NumPy basics, CSV files and elementary descriptive statistics. NumPy roadmap is helpful but not mandatory.

**By the end you will have:** a Git repository containing each session, weekly project demos, a journal, documented checkpoint results, tests or quality checks, and a polished capstone with setup steps that another learner can follow.

### Platform setup (Windows, Linux and macOS)

| Platform | Environment creation | Activation | Verify |
|---|---|---|---|
| Windows (PowerShell) | `py -m venv .venv` | `.\.venv\Scripts\Activate.ps1` | `python --version` |
| Linux | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |
| macOS | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |

Run package installations **after activation**, from the guide's project root. On Windows, use the Windows Python launcher (`py`) to create the environment if `python` is not yet configured. For restricted PowerShell execution policies, use Command Prompt with `.venv\Scripts\activate.bat` rather than changing system-wide policy. Confirm that `python -m pip --version` points to the virtual environment. Keep `.venv/` and secrets out of Git. For incompatible versions, consult the official project's install matrix and select a supported Python version; do not silently install an older runtime-wide package.

On Windows, Linux or macOS, create a virtual environment and run:
```bash
python -m pip install pandas numpy matplotlib pytest pyarrow openpyxl
python -c "import pandas as pd; print(pd.__version__); print(pd.DataFrame({'x':[1,2]}))"
```
`pyarrow` and `openpyxl` enable optional Parquet and Excel lessons. Prefer public/synthetic datasets, preserve raw input and document dependencies. Avoid relying on deprecated `inplace` behavior or obsolete version-specific recipes.

### Optional preflight sessions (not part of the numbered roadmap)

| Prep | What to practise | Evidence |
|---|---|---|
| P1 | Python or HTML/CSS basics relevant to this framework | Write a tiny script/page from memory and explain each statement. |
| P2 | Terminal, folders, interpreter/runtime and dependency manager | Create isolated project and check runtime/package versions. |
| P3 | Git, README, editor/debugger and error messages | Make a commit and resolve a deliberately introduced error. |
| P4 | Domain fundamentals: HTTP / SQL / statistics / algebra / testing / quantum ideas | Complete three small written examples before starting Day 1. |

If prerequisites are already familiar, skip the bridge. These guides do not replace a full Python or front-end language roadmap.

### Session rhythm

A **Day** is a study session, not necessarily a calendar day. Five sessions each week are about **3 hours**; the sixth is a **4-hour project/review**. The schedule is flexible if you study multiple frameworks at once.

| Minutes | Stage | Required action |
|---:|---|---|
| 10 | Recall | Re-type one concept from last session without looking. |
| 40 | Learn | Read the official reference and type small examples yourself. |
| 90 | Build | Implement the listed task without copying a finished solution. |
| 30 | Break/debug | Deliberately create a bug or edge case and diagnose the root cause. |
| 10 | Save | Run checks; `git add`, `git commit`; record learned/confused/next in `journal.md`. |

On review day, reserve four hours for the mini-project, manual negative-case tests, code cleanup, and a brief demo. A day is done only when **the stated acceptance check is shown**, relevant tests pass, code is committed, and you can explain the implementation. If stuck, note the smallest failing case and use the docs or a debugger. **Do not skip failed checkpoints.**

## Complete session roadmap

### Week 1: Days 1–6 — Tabular fundamentals

**Weekly deliverable:** Small orders DataFrame report.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Series vs DataFrame, indices and dtypes | Create products and orders frames with explicit types | Print schema, index and row count with explanation |
| 2 | loc/iloc and selection | Extract and update targeted subsets safely | Selection uses label vs position intentionally |
| 3 | Filtering and boolean masks | Filter paid orders by amount and date | Cross-check selection against hand-counted rows |
| 4 | Assign, rename and sorting | Add derived revenue and priority columns | No unintended mutation and stable sort shown |
| 5 | Reading/writing CSV and JSON | Round-trip small files with appropriate types | Dates/IDs survive export and import predictably |
| 6 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Small orders DataFrame report**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 1 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 2: Days 7–12 — Cleaning messy data

**Weekly deliverable:** Reproducible messy-orders cleaning script.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Missing data and pd.NA | Diagnose blanks, nulls and missing-by-column | Missing policy written down before filling |
| 8 | String normalization | Clean case, whitespace and category aliases | Distinct dirty labels collapse as intended |
| 9 | Datetime parsing and time zones | Parse mixed dates and normalize to chosen zone | Invalid dates reported and time zones not silently dropped |
| 10 | Duplicates and keys | Deduplicate with explicit composite key rule | Duplicate counts logged; legitimate repeated events preserved |
| 11 | astype, nullable types and errors | Convert amounts and integer IDs with validation | Bad values surfaced, not silently coerced |
| 12 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Reproducible messy-orders cleaning script**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 2 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 3: Days 13–18 — Joins and relationships

**Weekly deliverable:** Customer + orders relational report.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | merge and join keys | Join orders to customers with `validate=` | Unexpected one-to-many relationship raises an error |
| 14 | Outer/inner/left join semantics | Compare reconciliation counts for each join | Matched/unmatched rows explained |
| 15 | concat and schema consistency | Combine monthly files with consistent columns | Unexpected new column flagged in tests |
| 16 | pivot and melt | Convert wide sales to tidy long and back | Reversible example keeps the original totals |
| 17 | MultiIndex and index design | Build region/product aggregation with MultiIndex | Slice for region and reset_index correctly |
| 18 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Customer + orders relational report**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 3 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 4: Days 19–24 — Aggregation and grouped transforms

**Weekly deliverable:** Department-level KPI report.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | groupby aggregation | Compute counts, sums, means and median per category | Totals reconcile to source data |
| 20 | agg vs transform | Add within-group normalized sales values | New column preserves original row count |
| 21 | Named aggregation | Create readable KPI table with explicit names | No ambiguous duplicate column labels |
| 22 | Group-wise missing handling | Fill subgroup median only where defensible | Group distributions before/after are reported |
| 23 | Categoricals and ordered categories | Model priority levels and sort meaningfully | Category order remains business meaningful |
| 24 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Department-level KPI report**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 4 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 5: Days 25–30 — Time series and rolling analysis

**Weekly deliverable:** Monthly trend and anomaly report.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | DatetimeIndex and resampling | Convert transaction records to monthly totals | Monthly sum equals original sum |
| 26 | Rolling and expanding | Add 7-day average and cumulative revenue | Boundary windows handled and labeled |
| 27 | Shifts and percent change | Compute week-over-week change with missing periods | No accidental divide-by-zero treated as valid growth |
| 28 | Time zones and DST | Convert timestamps while preserving event instant | DST edge case tested and documented |
| 29 | Time-based joins | Use `merge_asof` to attach nearest prior rate | No future information leaks into historical join |
| 30 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Monthly trend and anomaly report**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 5 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 6: Days 31–36 — Performance, quality and safety

**Weekly deliverable:** Tested ETL cleaning pipeline.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Memory and dtype choices | Compare string/category/nullable memory usage | Measure memory with `memory_usage(deep=True)` |
| 32 | Vectorization vs apply | Refactor row loop to vectorized transform | Same results with before/after timing |
| 33 | Chunked reading and Parquet | Process large CSV in chunks and store Parquet | Memory stays bounded and rows reconcile |
| 34 | Assertions and invariants | Add checks for ID uniqueness, range, dates and revenue | Deliberate corrupted file fails loudly |
| 35 | Chained assignment and copies | Rewrite ambiguous chained assignment to `.loc` | No warning and intended frame definitely changes |
| 36 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Tested ETL cleaning pipeline**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 6 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 7: Days 37–42 — Exploratory analysis and communication

**Weekly deliverable:** Auditable analysis notebook + summary.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | describe and custom percentiles | Create distribution summary for key columns | Clear treatment of outliers and missingness |
| 38 | Cross-tabulation and pivot_table | Produce region/category cross-tab | Margin totals agree with raw data |
| 39 | DataFrame plotting | Render meaningful sales and retention charts with Matplotlib | Units, labels, and missing periods visible |
| 40 | Simple hypothesis/uncertainty | Compare two groups without causal overclaim | Limitations and possible confounders written down |
| 41 | Notebook to script conversion | Refactor analysis into functions and a reproducible entry point | Pipeline runs non-interactively from raw input |
| 42 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Auditable analysis notebook + summary**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 7 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 8: Days 43–48 — Production data workflows

**Weekly deliverable:** Incremental, versioned analysis pipeline.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Data contracts and schema drift | Detect missing, added or renamed columns | Pipeline stops or explicitly maps known change |
| 44 | Idempotent transformations | Rerun pipeline on same data without duplicates | Output checksums or totals remain stable |
| 45 | Incremental updates | Load new daily partition and update outputs | Processing avoids redoing all historical rows |
| 46 | Testing data transformations | Add fixture-based tests for joins, nulls and times | Every major transformation has positive/negative tests |
| 47 | Documentation and provenance | Record source, license, cleaning assumptions, versions | Another analyst can trace a result to source rows |
| 48 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Incremental, versioned analysis pipeline**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 8 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 9: Days 49–54 — Capstone

**Weekly deliverable:** Auditable sales analytics and automated reporting pipeline.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Problem and dataset specification | Define KPIs, grain, filters and quality thresholds | No undefined denominator or ambiguous metrics |
| 50 | Implement robust ingestion/cleaning | Read CSV/Parquet, validate and normalize | Messy fixture produces defined errors and cleaned data |
| 51 | Build join and analysis layer | Compute weekly and regional metrics | Group totals reconcile and business definitions match |
| 52 | Create report and tests | Generate plots and markdown summary with tests | Main assertions, charts and limitations recorded |
| 53 | Release reusable pipeline | Add README, CLI, data dictionary and reproducibility instructions | Peer can regenerate report from sample data |
| 54 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Auditable sales analytics and automated reporting pipeline**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 9 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

## Checkpoints: stop and demonstrate competence

| Checkpoint | When | Required proof | If you cannot pass |
|---|---|---|---|
| Checkpoint 0 | Day 18 | From a clean setup, demonstrate **customer + orders relational report**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Checkpoint 1 | Day 36 | From a clean setup, demonstrate **tested etl cleaning pipeline**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Final capstone | Day 54 | Give a short working demo of **auditable sales analytics and automated reporting pipeline**, rerun all checks, show README/limitations, and tag a release. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |

## Daily deliberate-debug checklist

- Force one invalid input or unexpected shape and observe the actual error; write down the cause and fix.
- Try a different operating system path, empty dataset, zero-length list, failed network call or wrong credentials **where applicable**.
- Write a small regression test or fixed fixture for the bug instead of only changing code.
- Run a project-level check before committing, and never hide warnings you do not understand.

## Capstone handoff checklist

- [ ] A fresh environment can install dependencies and run the main program.
- [ ] README includes prerequisites, commands, input examples, expected results and limitations.
- [ ] Automated tests or rigorous repeatable checks cover normal, boundary and failure cases.
- [ ] No passwords, API keys, private data, huge datasets or virtual environments are committed.
- [ ] Results and performance claims include the environment, versions and reproducibility method.
- [ ] A peer can follow the documentation without the author present.

## Domain-specific cautions

**Quality rule:** Data cleaning choices are analytic assumptions. Record original row counts, rejected records, join cardinality and units. Avoid treating missing values as zero unless it is justified.

## Official learning resources

| Resource | Link |
|---|---|
| pandas getting started | https://pandas.pydata.org/docs/getting_started/index.html |
| User guide | https://pandas.pydata.org/docs/user_guide/index.html |
| Missing data | https://pandas.pydata.org/docs/user_guide/missing_data.html |
| Merge/join | https://pandas.pydata.org/docs/user_guide/merging.html |
| Time series | https://pandas.pydata.org/docs/user_guide/timeseries.html |

**Resource/version policy:** These are official reference links checked while planning; dependencies and documentation evolve. Use the versions actually installed and verify release-specific API changes before copying an old example. Most resources are free; hosted cloud services or external infrastructure may have costs.

## What comes next

Extend the capstone with one feature, contribute a documentation fix or test to an open-source project, and revisit difficult checkpoints with no notes.

---
*This guide is a practical learning plan, not a credential or a guarantee of proficiency. Adapt the schedule to your pace; passing checkpoints matters more than calendar speed.*
