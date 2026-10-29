# Matplotlib (Python) Roadmap: From Zero to Publication-Quality Visualizations and Storytelling

*Created: 29 October 2026 · 7 weeks · 42 sessions · ~133 guided hours*

## Start here

Learn plots, Figures and Axes, chart selection, annotations, layouts, accessibility, export and reproducible graphics; produce a data-storytelling gallery.

**Prerequisites:** Python lists/functions and basic NumPy arrays. pandas familiarity is useful but not required.

**By the end you will have:** a Git repository containing each session, weekly project demos, a journal, documented checkpoint results, tests or quality checks, and a polished capstone with setup steps that another learner can follow.

### Platform setup (Windows, Linux and macOS)

| Platform | Environment creation | Activation | Verify |
|---|---|---|---|
| Windows (PowerShell) | `py -m venv .venv` | `.\.venv\Scripts\Activate.ps1` | `python --version` |
| Linux | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |
| macOS | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |

Run package installations **after activation**, from the guide's project root. On Windows, use the Windows Python launcher (`py`) to create the environment if `python` is not yet configured. For restricted PowerShell execution policies, use Command Prompt with `.venv\Scripts\activate.bat` rather than changing system-wide policy. Confirm that `python -m pip --version` points to the virtual environment. Keep `.venv/` and secrets out of Git. For incompatible versions, consult the official project's install matrix and select a supported Python version; do not silently install an older runtime-wide package.

In a Python virtual environment on Windows, Linux or macOS:
```bash
python -m pip install matplotlib numpy pandas pytest
python -c "import matplotlib; print(matplotlib.__version__)"
```
Prefer object-oriented plotting (`fig, ax = plt.subplots()`), explicitly close figures in batch scripts, and save outputs with chosen DPI. In headless CI use a non-interactive backend (e.g. `Agg`) when appropriate.

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

### Week 1: Days 1–6 — Plot architecture and core charts

**Weekly deliverable:** Chart gallery with readable axes and titles.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Figure, Axes, Artist and pyplot relationship | Create figure with one line plot using `fig, ax` | Explain difference between figure and axes |
| 2 | Line charts and scales | Plot a time series with clear labels and legend | Time axis correct and no clipped ticks |
| 3 | Bar vs horizontal bar | Compare category values without truncated baselines | Chart shows categories in meaningful order |
| 4 | Scatter plots and alpha | Show relationship with overlapping observations | Overplotting addressed visibly |
| 5 | Histograms, bins and density | Compare histograms under different bin choices | Interpretation notes explain change in visual story |
| 6 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Chart gallery with readable axes and titles**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 1 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 2: Days 7–12 — Axes control and layout

**Weekly deliverable:** Multi-panel exploratory report.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Titles, labels, ticks and units | Improve raw plots to a clear 3-chart report | Every displayed quantity has units and readable ticks |
| 8 | Limits and scales, log axes | Visualize values with skewed magnitude | Invalid log values handled consciously |
| 9 | Subplots, gridspec and constrained layout | Make 2x2 dashboard with readable panels | No title, legend or axis label overlaps |
| 10 | Legends and colorbars | Use legend for lines and colorbar for continuous data | Legend encodes actual series and colorbar has units |
| 11 | Annotations and reference lines | Highlight business target, median and anomaly | Highlight enhances data not obscures it |
| 12 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Multi-panel exploratory report**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 2 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 3: Days 13–18 — Statistics and uncertainty

**Weekly deliverable:** Distribution and uncertainty visualization pack.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Boxplots and violin plots | Compare groups and annotate sample sizes | Plots do not conceal small n |
| 14 | Errorbars and confidence intervals | Plot estimates with uncertainty bars | Explain uncertainty definition correctly |
| 15 | Empirical CDF and percentiles | Implement ECDF and show quartile thresholds | ECDF monotonically increases to 1 |
| 16 | Heatmaps and matrices | Visualize correlation with labeled axes | Values and color map limits are interpreted correctly |
| 17 | Paired and small multiples | Compare before/after values without misleading category ordering | Paired values can be followed across series |
| 18 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Distribution and uncertainty visualization pack**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 3 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 4: Days 19–24 — Styling, typography and accessibility

**Weekly deliverable:** Consistent report visual theme.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | rcParams and style sheets | Define small reusable house style | Four chart types share coherent type/spacing |
| 20 | Color theory and accessible palettes | Replace confusing rainbow palette with readable alternative | Grayscale and color-vision checks pass a manual review |
| 21 | Fonts, mathtext and Unicode | Label scientific values with superscripts/Greek symbols | Labels render across OS using available fonts |
| 22 | Formatters, dates and locators | Plot hourly data with tidy ticks | Tick density adapts to figure size |
| 23 | Text layout and storytelling | Design a chart caption with source and caveats | Context and limitation understandable without presentation |
| 24 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Consistent report visual theme**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 4 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 5: Days 25–30 — Advanced and specialized charts

**Weekly deliverable:** Reusable plotted scientific experiment.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Images and imshow | Plot synthetic image and correct coordinate origin | Pixel and coordinate conventions documented |
| 26 | Contour and surface concepts | Visualize 2D scalar field using contours | Contours align with known function levels |
| 27 | Polar plots and projections | Make polar response pattern | Angular units and radial origin correct |
| 28 | Twin axes pitfalls and alternatives | Compare dual-axis design against separate plots | Chosen plot avoids manufactured correlation |
| 29 | Event plots and timelines | Visualize event durations with category groups | Overlapping events visible and labels readable |
| 30 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Reusable plotted scientific experiment**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 5 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 6: Days 31–36 — Reuse, interactivity and export

**Weekly deliverable:** Figure-building Python package.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Writing reusable plot functions | Accept Axes as input and return Artists | Functions do not invoke global `show()` implicitly |
| 32 | Animations and simple interactions | Create 20-frame animation or interactive selector | Repeated frames do not leak duplicate artists |
| 33 | SVG/PDF/PNG export | Export print and web versions | Fonts/ticks legible and bounding boxes not clipped |
| 34 | Headless rendering and automated checks | Render to PNG in CI with Agg | Test suite can save figures without GUI display |
| 35 | Profiling heavy plots | Downsample million-point trace with rationale | Readable chart and measured speed improvement |
| 36 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Figure-building Python package**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 6 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 7: Days 37–42 — Capstone

**Weekly deliverable:** Publication-ready mini-report and chart library.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Define an audience and story | Choose credible dataset and 4 chart questions | Each chart has a decision-relevant purpose |
| 38 | Clean data and chart semantics | Validate series, missing values and units | Data checks agree with summary tables |
| 39 | Build a four-chart narrative | Create coherent multi-panel report with annotations | Layout readable at intended page and screen sizes |
| 40 | Accessibility and visual QA | Verify contrast, text, axes, misleading scales and alternatives | Each chart has meaningful alt-text style description |
| 41 | Package and share | Export PNG/SVG/PDF, README and code with seed | Peer reruns figures and inspects limitations |
| 42 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Publication-ready mini-report and chart library**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 7 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

## Checkpoints: stop and demonstrate competence

| Checkpoint | When | Required proof | If you cannot pass |
|---|---|---|---|
| Checkpoint 0 | Day 18 | From a clean setup, demonstrate **distribution and uncertainty visualization pack**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Checkpoint 1 | Day 36 | From a clean setup, demonstrate **figure-building python package**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Final capstone | Day 42 | Give a short working demo of **publication-ready mini-report and chart library**, rerun all checks, show README/limitations, and tag a release. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |

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

**Visual integrity:** Never hide inconvenient outliers, omit units, imply causation from correlation, or manipulate axes to exaggerate differences. Check charts at their actual publication size.

## Official learning resources

| Resource | Link |
|---|---|
| Matplotlib quick start | https://matplotlib.org/stable/users/explain/quick_start.html |
| Tutorials | https://matplotlib.org/stable/tutorials/index.html |
| Examples gallery | https://matplotlib.org/stable/gallery/index.html |
| Axes API | https://matplotlib.org/stable/api/axes_api.html |
| Constrained layout | https://matplotlib.org/stable/users/explain/axes/constrainedlayout_guide.html |

**Resource/version policy:** These are official reference links checked while planning; dependencies and documentation evolve. Use the versions actually installed and verify release-specific API changes before copying an old example. Most resources are free; hosted cloud services or external infrastructure may have costs.

## What comes next

Extend the capstone with one feature, contribute a documentation fix or test to an open-source project, and revisit difficult checkpoints with no notes.

---
*This guide is a practical learning plan, not a credential or a guarantee of proficiency. Adapt the schedule to your pace; passing checkpoints matters more than calendar speed.*
