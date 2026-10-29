# NumPy (Python) Roadmap: From Zero to Arrays, Numerical Computing and Performance

*Created: 29 October 2026 · 8 weeks · 48 sessions · ~152 guided hours*

## Start here

Master ndarrays, shapes, indexing, broadcasting, numerical algorithms, stable computation, random generators and vectorized performance; build a tested scientific computation toolkit.

**Prerequisites:** Python functions, loops, lists, slicing and basic algebra. Optional prep reviews functions, list comprehensions, floats, plotting and Git.

**By the end you will have:** a Git repository containing each session, weekly project demos, a journal, documented checkpoint results, tests or quality checks, and a polished capstone with setup steps that another learner can follow.

### Platform setup (Windows, Linux and macOS)

| Platform | Environment creation | Activation | Verify |
|---|---|---|---|
| Windows (PowerShell) | `py -m venv .venv` | `.\.venv\Scripts\Activate.ps1` | `python --version` |
| Linux | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |
| macOS | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |

Run package installations **after activation**, from the guide's project root. On Windows, use the Windows Python launcher (`py`) to create the environment if `python` is not yet configured. For restricted PowerShell execution policies, use Command Prompt with `.venv\Scripts\activate.bat` rather than changing system-wide policy. Confirm that `python -m pip --version` points to the virtual environment. Keep `.venv/` and secrets out of Git. For incompatible versions, consult the official project's install matrix and select a supported Python version; do not silently install an older runtime-wide package.

Create and activate a Python virtual environment on Windows, Linux or macOS (commands below), then:
```bash
python -m pip install numpy pytest matplotlib
python -c "import numpy as np; print(np.__version__); print(np.arange(6).reshape(2,3))"
```
Use standard NumPy (`import numpy as np`) and `np.random.default_rng(seed)` for seeded examples. A GPU is not needed. Check the compatible Python/NumPy pair before installing.

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

### Week 1: Days 1–6 — Arrays and shape thinking

**Weekly deliverable:** Matrix exercise pack with test cases.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | ndarray creation, dtype and shape | Create vectors, matrices and 3D tensors from lists/arange/zeros | Explain `shape`, `ndim`, `size`, `dtype` on each |
| 2 | Indexing, slices and negative indices | Extract columns, rectangular blocks and reverse views | Index outputs match paper predictions |
| 3 | Reshape, transpose and axes | Change 12 values between 1D, 2D and 3D safely | Reshape preserves element count or fails explicitly |
| 4 | Elementwise operations and comparisons | Write threshold classification and arithmetic on arrays | Results match hand calculations for 5 cases |
| 5 | Reductions and axis semantics | Compute per-row/per-column statistics | Correct axis labels and no accidental full-array reduction |
| 6 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Matrix exercise pack with test cases**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 1 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 2: Days 7–12 — Broadcasting, masking and views

**Weekly deliverable:** Vectorized image-filter mini-project.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Broadcasting rules | Normalize columns by a vector of scales | Can write the aligned shapes on paper before run |
| 8 | Boolean masks | Remove out-of-range readings from sensor arrays | No incorrect indices and result size checked |
| 9 | Fancy indexing vs slicing | Compare copies and views with deliberate mutation | Explain which operations alter original array |
| 10 | Strides, memory layout and contiguous arrays | Inspect `strides` and C/F order | Predict effect of transpose and slicing on contiguity |
| 11 | Structured arrays and dtype conversions | Store readings with timestamps and controlled cast | Overflow/precision loss measured and documented |
| 12 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Vectorized image-filter mini-project**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 2 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 3: Days 13–18 — Randomness and simulation

**Weekly deliverable:** Reproducible Monte Carlo estimation notebook.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Generator API and seed control | Sample reproducible rolls and compare histograms | Same seed gives same samples, different seed different values |
| 14 | Distributions and summary stats | Simulate normal/exponential samples | Sample mean/variance approach expected values with sample size |
| 15 | Monte Carlo integration | Estimate pi or area with confidence discussion | Error declines as sample count increases in repeated trials |
| 16 | Shuffling and permutations | Split dataset reproducibly by index permutation | No index duplication and split sizes exact |
| 17 | Numerical error and floating point | Demonstrate cancellation, rounding and tolerance | Explain why `==` is unsafe for approximate floats |
| 18 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Reproducible Monte Carlo estimation notebook**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 3 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 4: Days 19–24 — Linear algebra fundamentals

**Weekly deliverable:** Tested regression and matrix toolkit.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Dot, matmul and vectorization | Implement vector projection and matrix product | Compare with manual small example |
| 20 | Norms, distance and similarity | Build distance matrix for 50 points | Diagonal zero and symmetry pass tests |
| 21 | Solve vs inverse | Solve Ax=b using `np.linalg.solve` and compare residual | Residual small and no explicit inverse used |
| 22 | Eigenvalues and singular value decomposition | Reconstruct a small matrix from SVD | Reconstruction error reported numerically |
| 23 | Least-squares fitting | Fit line to noisy points via `lstsq` | Parameters within tolerance of known generating values |
| 24 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Tested regression and matrix toolkit**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 4 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 5: Days 25–30 — Numerical algorithms

**Weekly deliverable:** Reusable finite-difference and signal operations.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Vectorized finite differences | Compute derivative approximation over a grid | Error compared with known derivative |
| 26 | Integration and cumulative sums | Approximate area using trapezoids and `np.trapezoid` where supported | Refining grid reduces error |
| 27 | Convolution idea and sliding windows | Implement moving average for a time series | Edges handled deliberately and tests cover them |
| 28 | Missing values and NaN propagation | Compute summary with `nanmean`, mask and explicit policy | Undefined/empty cases handled with documented rule |
| 29 | FFT and spectral representation | Detect dominant frequency in synthetic signal | Peak location within known signal frequency tolerance |
| 30 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Reusable finite-difference and signal operations**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 5 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 6: Days 31–36 — Performance and testing

**Weekly deliverable:** Benchmarked data-transform library.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Time and memory benchmarking | Compare Python loop and vectorized transformation | Benchmarks use repeat runs and same inputs |
| 32 | Avoiding temporary arrays | Rewrite large computation using `out=` where appropriate | Peak allocation reduced or tradeoff explained |
| 33 | Broadcasting pitfalls and giant intermediates | Measure pairwise distance memory risk | Choose chunking for larger input and no OOM |
| 34 | pytest/numpy.testing assertions | Build 20 tests for vector/matrix operations | Tolerances appropriate to numeric scale |
| 35 | Input shape and dtype contracts | Validate arrays in toolkit public functions | Clear errors on wrong dimensions and nonnumeric types |
| 36 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Benchmarked data-transform library**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 6 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 7: Days 37–42 — Scientific pipelines

**Weekly deliverable:** Dataset processing from raw arrays to features.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | File I/O and memory maps | Save/load `.npy` and `.npz`, explore `memmap` | Round trip exact and no unintended full-file copy |
| 38 | Sorting, unique and search | Build category encoding, top-k and sorted searches | Outputs correct under duplicate and empty input |
| 39 | Multidimensional statistics | Compute covariance and correlations | Symmetry and numerical values match reference |
| 40 | Advanced indexing and `einsum` | Compute batched dot products two ways | Both methods return same shapes and numbers |
| 41 | API and reproducibility | Add CLI to transform arrays given seed and file path | Two runs with same inputs yield matching outputs |
| 42 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Dataset processing from raw arrays to features**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 7 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 8: Days 43–48 — Capstone

**Weekly deliverable:** Documented numerical toolkit and simulation report.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Choose project and mathematical assumptions | Define simulation objective, data and error targets | Every formula linked to a testable expectation |
| 44 | Implement data preparation and core algorithm | Write typed, documented NumPy functions for project | Shape and dtype assumptions validated |
| 45 | Numerical correctness tests | Compare 5 toy cases to exact or independent reference | Relative/absolute errors recorded within bounds |
| 46 | Performance and memory report | Benchmark vectorized and naïve versions with repeated trials | Fair comparison includes time and memory notes |
| 47 | Package demo and review | Provide notebook/script, README, seed and benchmark table | Peer can reproduce results from clean environment |
| 48 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Documented numerical toolkit and simulation report**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 8 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

## Checkpoints: stop and demonstrate competence

| Checkpoint | When | Required proof | If you cannot pass |
|---|---|---|---|
| Checkpoint 0 | Day 18 | From a clean setup, demonstrate **reproducible monte carlo estimation notebook**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Checkpoint 1 | Day 36 | From a clean setup, demonstrate **benchmarked data-transform library**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Final capstone | Day 48 | Give a short working demo of **documented numerical toolkit and simulation report**, rerun all checks, show README/limitations, and tag a release. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |

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

**Numerical hygiene:** Keep units clear, distinguish shape from meaning, use deterministic seeds, and document floating-point tolerances. NumPy arrays typically reside in CPU memory; this roadmap does not assume GPU execution.

## Official learning resources

| Resource | Link |
|---|---|
| NumPy user guide | https://numpy.org/doc/stable/user/ |
| NumPy absolute beginners | https://numpy.org/doc/stable/user/absolute_beginners.html |
| Broadcasting | https://numpy.org/doc/stable/user/basics.broadcasting.html |
| Linear algebra | https://numpy.org/doc/stable/reference/routines.linalg.html |
| Random | https://numpy.org/doc/stable/reference/random/index.html |

**Resource/version policy:** These are official reference links checked while planning; dependencies and documentation evolve. Use the versions actually installed and verify release-specific API changes before copying an old example. Most resources are free; hosted cloud services or external infrastructure may have costs.

## What comes next

Extend the capstone with one feature, contribute a documentation fix or test to an open-source project, and revisit difficult checkpoints with no notes.

---
*This guide is a practical learning plan, not a credential or a guarantee of proficiency. Adapt the schedule to your pace; passing checkpoints matters more than calendar speed.*
