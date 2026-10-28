# Julia Roadmap: From Zero to Scientific Computing, Data Analysis and Fast Numerical Code — Windows, Linux and macOS

*54 sessions | 9 weeks | approximately 171 hours | Julia 1.x, juliaup, Pkg, DataFrames, plotting, Test and BenchmarkTools*

This beginner-to-practical guide starts with Julia expressions and works toward **reproducible data analysis, numerical algorithms, statistical modeling and performance profiling**. Julia is a dynamic language designed for technical computing; you do **not** need Python, R, MATLAB or C++ beforehand. By the end, build a documented numerical-data project that somebody else can reproduce on Windows, Linux or macOS from a clean checkout.

**Platform coverage:** Use native Julia on **Windows, Linux or macOS**. The programming language, standard-library algorithms and general-purpose packages are largely portable, but package binaries, GPU drivers, file paths and plotting backends can differ. This guide is **CPU-first** and does not require a dedicated GPU. CUDA/ROCm, distributed clusters, specialized differential-equation solvers and optional Jupyter integrations are extensions, not hidden prerequisites.

## How one session works

A **day** means one study session, not necessarily one calendar day. Sessions 1–5 of each week take about **3 hours**; the sixth is a **4-hour project and review**. Work in order within a language. If alternating languages, finish the current session before switching.

| Minutes | Block | What you do |
|---:|---|---|
| 10 | Recall | Rebuild a small piece of the previous session from memory. |
| 40 | Learn | Read the specific topic, type examples, explain them in your own words. |
| 90 | Build | Write today's program independently, with at least three test inputs. |
| 30 | Break it | Introduce one deliberate bug, reproduce it, diagnose it, then fix it. |
| 10 | Save | Run the available checks, commit the work, and write 3 journal lines: learned / confused / next step. |

**Completion rule:** do not check off a session merely for reading about a topic. The program must run on the intended platform, expected edge cases must behave correctly, tests or hardware checks must pass where relevant, and you must be able to explain your solution without copying. If stuck for 20 minutes, record what you expected and what happened, minimize the example, and consult the official docs. Hardware sessions can replace the 30-minute bug exercise with a safe fault-injection test; **never deliberately short a circuit or exceed a board's electrical limits**.

## Start here — setup (about 45–75 minutes)

1. Install current stable Julia via **juliaup**, using the OS-specific directions at <https://julialang.org/downloads/>. **Windows:** follow the official Windows installer/Microsoft Store or WinGet flow. **macOS/Linux:** follow the official installation script or applicable package method. Do not use a command copied from an older guide without checking the official page. Verify `julia --version` and run the interactive `julia` REPL.
2. Install VS Code with the **Julia extension**; optionally use [Pluto.jl](https://plutojl.org/) for reactive notebooks beginning in week 4. Install Git and create `julia-roadmap/` with week folders and `journal.md`.
3. Learn two REPL modes: `]` opens package mode and `?` opens help mode. Use **project environments** (`Project.toml` and `Manifest.toml`) from week 3 onward so your exact dependency versions are repeatable. Julia's package installation is not pip, CRAN or npm.
4. Avoid overwriting Julia's built-in names (`sum`, `length`, `sqrt`, etc.). Keep datasets synthetic or publicly licensed, and record units and random seeds in each experiment.

| OS | Notes |
|---|---|
| Windows | Native Julia and VS Code; Windows paths often contain backslashes; use `joinpath` instead of joining raw path separators. |
| Linux | Native Julia works on supported distributions; system graphics dependencies may be needed for some plots. |
| macOS | Native Julia on supported Intel/Apple Silicon versions; check architecture for package binaries. |

**Suggested directory:** `julia-roadmap/week-01/` … `week-09/`, `datasets/` (synthetic or redistributable), `src/`, `test/`, `figures/`, `reports/`, `journal.md`. Do not commit large generated data files without a reason.

## First Julia program

Save `hello.jl` and run `julia hello.jl`:

```julia
language = "Julia"
scores = [4, 7, 9]
println("Learning $language: $(sum(scores)) total points")
```

Later, your projects should start with `julia --project=. script.jl`; the `--project` flag selects the local environment after you create one.

---

## Part 1 — Programming and numerical foundations

### Week 1 — Numbers, variables and decisions (sessions 1–6)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **1** | What Julia is, REPL, `println`, source files, expressions and comments. | Greeting plus a two-question computation script. | Run from terminal and explain REPL vs file. |
| **2** | Numeric types, promotion, integers vs floats, conversion and rounding. | Unit and temperature conversion program. | Predict type and result of six operations. |
| **3** | Comparisons, `if`/`elseif`/`else`, Boolean expressions, `missing` preview. | Grade and risk-category classifier. | Boundary values and missing cases documented. |
| **4** | `for`, `while`, ranges, `break`, comprehensions. | FizzBuzz, multiplication table and prime checker. | Results match hand calculations. |
| **5** | Functions, multiple methods, dispatch preview, keyword arguments. | Implement `mean_safe`, `clamp_value`, and `isprime_small`. | Explain function signatures and test zero-length input. |
| **6** | **Project and review:** beginner calculations. | Console savings/loan analyzer with input validation. | Run 10 fixed examples and write expected results. |

**Break it this week:** Try indexing an array at zero; compare `missing` with `nothing`; use an uninitialized variable and read the error.

### Week 2 — Arrays, strings and data structures (sessions 7–12)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **7** | Vectors, matrices, indexing starting at 1, bounds errors, `size`/`length`. | Matrix calculator and vector summary. | Explain why index 0 is invalid. |
| **8** | Slices, `view`, mutation vs copying, `push!` and `sort!`. | Modify a score list using copy and view. | Demonstrate which changes affect original data. |
| **9** | Broadcasting with `.`, elementwise operations and comprehensions. | Compute vectorized temperature and BMI data. | Explain `*` vs `.*` and array shapes. |
| **10** | Tuples, NamedTuples, dictionaries, sets and strings. | Word counts and catalog of records. | Unicode and empty string cases pass. |
| **11** | Multiple dispatch, parametric types and simple structs. | `Measurement` with units plus dispatch on scalar/vector. | Mis-matched inputs fail safely; explain selected method. |
| **12** | **Project and review:** data manipulation. | Analyze synthetic sensor readings with arrays and dictionaries. | Reproducible summaries plus error tests committed. |

### Week 3 — Package environments, files and testing (sessions 13–18)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **13** | Local environments, Pkg `activate`, `add`, `instantiate`, `status`. | Create project with Project.toml and dependencies. | New terminal reproduces environment. |
| **14** | Files, CSV concepts, `readlines`, open/close and safe paths. | Write/read sensor data as CSV. | Escape malformed rows and explain bad-file behavior. |
| **15** | `CSV.jl` and `DataFrames.jl` installation and tabular concepts. | Load a synthetic sales table and inspect schema. | Types and missing values understood. |
| **16** | DataFrames indexing, select/filter/transform/groupby/combine. | Weekly grouped sales report. | All expected aggregate totals verified. |
| **17** | `Test` standard library, `@test`, `@testset`, module layout. | Add 15 tests for data transforms. | Passing tests and one deliberately failing test shown. |
| **18** | **Checkpoint 0:** reproducible data workflow. | CSV-to-summary CLI using a local project environment. | Clean `Pkg.instantiate` works, 15 tests green, tag `julia-p1`. |

**Break it this week:** Introduce a malformed CSV row and a test that fails, then fix the parser and expected behavior.

## Part 2 — Applied data and scientific computing

### Week 4 — Visualization and statistical reasoning (sessions 19–24)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **19** | Descriptive stats, distributions, outliers, quantiles, standard deviation. | Summarize a 100-row synthetic dataset. | Distinguish sample vs population spread. |
| **20** | Plotting with a supported library (Plots.jl, Makie or CairoMakie). | Create line, bar, scatter and histogram plots. | Axes, units, labels and legends correct. |
| **21** | Correlation vs causation, confounding and misleading plots. | Analyze two related variables with a counterexample. | State what cannot be concluded from correlation. |
| **22** | Simple hypothesis tests, confidence intervals and assumptions. | Bootstrap a mean interval from seeded data. | Explain uncertainty and assumptions. |
| **23** | Pluto notebooks or script-driven markdown reporting. | Create a reproducible interactive analysis notebook. | Rerun produces same key figures. |
| **24** | **Project and review:** statistical mini-report. | Write report with 4 figures, sources and uncertainty notes. | Claims match data and plots are readable. |

### Week 5 — Linear algebra and numerical methods (sessions 25–30)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **25** | Vectors, matrices, transpose, multiplication, shape checks. | Build small linear-algebra examples. | Dimension mismatches caught and explained. |
| **26** | `LinearAlgebra`, dot products, norms, factorizations, linear systems. | Solve `Ax=b` using `A \ b` (not explicit inverse). | Residual `norm(A*x-b)` documented. |
| **27** | Floating point, precision limits, overflow, stability. | Compare naive and stable sums and finite differences. | Error growth shown with examples. |
| **28** | Root finding (bisection/Newton) and convergence criteria. | Solve a scalar nonlinear equation. | Both failure and convergence conditions tested. |
| **29** | Numerical integration and ODE intuition; Euler method. | Simulate a cooling curve with unit-aware steps. | Compare with known/analytic behavior. |
| **30** | **Project and review:** numerical solver kit. | Linear solve + root finder + integrator with tests. | Accuracy thresholds and convergence notes recorded. |

**Break it this week:** Use an ill-conditioned system and compare residuals; avoid claiming accuracy without tolerance.

### Week 6 — Type stability, benchmarking and performance (sessions 31–36)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **31** | Julia JIT and compilation latency, global-variable pitfalls. | Compare a top-level loop with a function. | Explain warm-up vs measured runtime. |
| **32** | `@time`, `@allocated`, BenchmarkTools `@btime`; benchmark hygiene. | Measure vector summation and allocations. | Timings reported across repeated runs after warm-up. |
| **33** | Type inference, `@code_warntype`, concrete fields and dispatch. | Refactor unstable numerical function. | Compare allocations and performance before/after. |
| **34** | Memory layout, views, in-place functions, `!` naming. | Optimize a 2D stencil or image-filter calculation. | Numerical output unchanged within tolerance. |
| **35** | Multithreading, tasks and race-free reductions. | Parallelize independent Monte Carlo experiments. | Deterministic seeded results within stated tolerance. |
| **36** | **Checkpoint 1:** performance discipline. | Benchmark a solver before and after two optimizations. | Validated results, test run and reproducible benchmark notes, tag `julia-p2`. |

**Break it this week:** Benchmark top-level code before warm-up, then repeat inside a function; explain why the first number misleads.

## Part 3 — Reproducible projects and specialization

### Week 7 — Modeling, fitting and scientific workflow (sessions 37–42)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **37** | Least squares, linear regression and held-out data. | Fit linear model to synthetic observations. | Training/test split and error metric recorded. |
| **38** | Optimization fundamentals, gradients and constrained search intuition. | Fit one parameter using optimization or manual gradient descent. | Optimization objective decreases and bounds respected. |
| **39** | Probabilistic simulation, seeded RNGs and Monte Carlo error. | Estimate a probability with sample-size study. | Error bars shrink with more samples. |
| **40** | Missingness, outliers, normalization and leakage. | Build a preprocessing pipeline on train-only statistics. | Held-out data never influences fitting steps. |
| **41** | Module/package organization, public APIs and documentation. | Package the model and solver into a Julia module. | Another script imports and tests it. |
| **42** | **Project and review:** fitted model study. | Synthetic physical or business process, baseline and model comparison. | Biases, limitations and held-out performance documented. |

### Week 8 — Reproducibility, interoperability and delivery (sessions 43–48)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **43** | Project vs Manifest, Git hygiene, seeds and environment capture. | Freeze environment and write reproduce instructions. | New environment runs with `Pkg.instantiate`. |
| **44** | Reading external tabular data, HTTP requests if needed, JSON formats. | Import a published non-sensitive dataset or synthetic JSON. | Errors handled and provenance documented. |
| **45** | Data validation, schema checking, assertions and units. | Validate a reusable data pipeline. | Invalid inputs return clear errors. |
| **46** | Profiling, memory allocations and scalability. | Profile a 10x larger dataset and fix bottleneck. | Optimization validated with correctness tests. |
| **47** | CI on Windows/Linux/macOS if package dependencies support all. | Write GitHub Actions workflow for `Pkg.test`. | CI runs tests on at least one target OS and matrix documented. |
| **48** | **Checkpoint 2:** analysis release candidate. | Reproducible report plus module/test suite and saved plots. | Data provenance and 25+ tests included, tag `julia-p3`. |

### Week 9 — Capstone: scientific analysis from source to result (sessions 49–54)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **49** | Choose a question: energy, retail, transit or simulation. | One-page scope with units, outcomes and exclusions. | Five measurable acceptance criteria. |
| **50** | Build data ingestion and validation. | Documented schema, fixtures, missing-value handling. | Clean load and failure-path tests. |
| **51** | Build numerical/analytic core. | Compute summaries, fit model or solve relevant equations. | Correctness checked on synthetic known examples. |
| **52** | Create explainable figures and narrative report. | At least four labeled plots with uncertainty notes. | A second reader can interpret each figure. |
| **53** | Optimize one measured hotspot and finalize CI. | Record baseline/warm timings and tests on clean environment. | Reproducible data and code produce consistent answers. |
| **54** | **Final review and release:** publish report and project. | README, provenance, tests, benchmark and short demo; tag `julia-v1`. | Another person regenerates all figures using documented commands. |

---

## Checkpoints — do not move forward with gaps

| Gate | Session | Pass condition | If you miss it |
|---|---:|---|---|
| Checkpoint 0 | 18 | Reproducible project environment, validated CSV summary and 15 tests. | Redo files, DataFrames and environment setup. |
| Checkpoint 1 | 36 | Correct numerical routine with documented benchmarking methodology. | Redo numerical stability and type-stability exercises. |
| Checkpoint 2 | 48 | Reproducible analysis report and module with 25+ tests and recorded provenance. | Finish missing validation or documentation. |
| Capstone | 54 | Fresh checkout regenerates plots and summary with pinned environment, tests and `julia-v1`. | Repair dependency setup and result reproducibility. |

## Final capstone specification

Build a **reproducible scientific/data-analysis project**, using a public or synthetic dataset. Include a Julia package or well-structured module, validation, at least one numerical method or statistical model, a baseline comparison, **four publication-quality plots**, a readable report/notebook, and at least 25 automated tests. Record assumptions, random seeds, units, dataset license/provenance and at least one carefully warmed benchmark.

**Minimum acceptance test:** clone repository → install Julia via official method → run `julia --project=. -e 'using Pkg; Pkg.instantiate()'` → run tests → generate tables/figures → compare key output numbers to reference results with stated tolerances. If the operating system needs a shell-specific quoting variant, document it.

**Optional specialization after session 54:** (A) scientific machine learning with Flux or Lux, (B) differential equations with SciML, (C) numerical optimization, or (D) distributed/HPC/GPU Julia. Install these only after the CPU version is fully reproducible.

## Resources

| Resource | Use it for | Cost |
|---|---|---|
| [Julia installation](https://julialang.org/downloads/) | Platform-specific `juliaup` and official releases. | Free |
| [Julia manual](https://docs.julialang.org/en/v1/) | Language, arrays, multiple dispatch and performance tips. | Free |
| [Pkg documentation](https://pkgdocs.julialang.org/) | Project environments and dependency reproducibility. | Free |
| [Julia Data Science](https://juliadatascience.io/) | Working with tables, data cleaning and graphics. | Free |
| [DataFrames.jl](https://dataframes.juliadata.org/stable/) | Data manipulation APIs. | Free |
| [BenchmarkTools.jl](https://juliaci.github.io/BenchmarkTools.jl/stable/) | Repeatable timing and allocation benchmarking. | Free |
| [Pluto.jl](https://plutojl.org/) | Reactive notebooks and reproducible explorations. | Free |
| [JuliaAcademy](https://juliaacademy.com/) | Supplementary lectures and examples. | Free |

**Version caution:** minor Julia or plotting-package versions change over time. Follow the current stable release and pin an environment for each project; don't infer that every GPU or system-library package works identically across all OSes.

## What you can do next

You can write tested Julia programs, use arrays and multiple dispatch, analyze data, implement basic numerical methods and benchmark Julia without confusing compilation latency with computation time. To specialize, learn the mathematical assumptions and verification practices of your chosen field before adding packages. A second project with real measured data and a public methodology is a good portfolio step.

