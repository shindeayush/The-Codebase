# scikit-learn (Python) Roadmap: From Zero to Classical Machine Learning and Model Evaluation

*Created: 29 October 2026 · 10 weeks · 60 sessions · ~190 guided hours*

## Start here

Learn train/test discipline, preprocessing pipelines, regression, classification, cross-validation, feature engineering, clustering, tuning, fairness and reproducible deployment.

**Prerequisites:** Python, NumPy, pandas, Matplotlib, basic algebra and probability; the guide begins with a short statistics refresher, not a full mathematics course.

**By the end you will have:** a Git repository containing each session, weekly project demos, a journal, documented checkpoint results, tests or quality checks, and a polished capstone with setup steps that another learner can follow.

### Platform setup (Windows, Linux and macOS)

| Platform | Environment creation | Activation | Verify |
|---|---|---|---|
| Windows (PowerShell) | `py -m venv .venv` | `.\.venv\Scripts\Activate.ps1` | `python --version` |
| Linux | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |
| macOS | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |

Run package installations **after activation**, from the guide's project root. On Windows, use the Windows Python launcher (`py`) to create the environment if `python` is not yet configured. For restricted PowerShell execution policies, use Command Prompt with `.venv\Scripts\activate.bat` rather than changing system-wide policy. Confirm that `python -m pip --version` points to the virtual environment. Keep `.venv/` and secrets out of Git. For incompatible versions, consult the official project's install matrix and select a supported Python version; do not silently install an older runtime-wide package.

Create a supported Python environment on Windows, Linux or macOS:
```bash
python -m pip install scikit-learn numpy pandas matplotlib joblib pytest
python -c "import sklearn; sklearn.show_versions()"
```
Use public or synthetic datasets with a documented label and split strategy. Keep transformations inside `Pipeline`/`ColumnTransformer` when they learn statistics from training data.

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

### Week 1: Days 1–6 — ML workflow and first estimators

**Weekly deliverable:** Baseline classification notebook with untouched test split.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Targets, features and types of ML | Choose a tabular dataset and identify leakage candidates | Target and possible prediction-time features clearly distinguished |
| 2 | Train/test splits and random_state | Implement stratified split before inspecting outcomes | No row overlap and stratification reported |
| 3 | Estimator API fit/predict/score | Fit dummy and logistic models | Baseline and non-baseline evaluated on holdout |
| 4 | Metrics and confusion matrix | Compute accuracy, precision, recall and F1 | Explain what each fails to capture |
| 5 | Cross-validation concept | Compare k-fold CV vs one holdout result | CV uses only training data for selection |
| 6 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Baseline classification notebook with untouched test split**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 1 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 2: Days 7–12 — Preprocessing and reliable pipelines

**Weekly deliverable:** Preprocessing + estimator pipeline.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Missing values and imputation | Impute numeric and categorical fields in Pipeline | Imputation stats fit on training fold only |
| 8 | Scaling and normalization | Compare scaled/unscaled distance-based models | Scaling choice justified by algorithm |
| 9 | Categorical encoders | Use OneHotEncoder with unknown categories handled | Unseen category does not crash prediction |
| 10 | ColumnTransformer | Apply per-column preprocessing to mixed frame | Model accepts raw typed feature table |
| 11 | Pipeline serialization | Persist and reload complete preprocessing+model | Same test inputs yield same predictions |
| 12 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Preprocessing + estimator pipeline**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 2 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 3: Days 13–18 — Regression and residuals

**Weekly deliverable:** Demand forecast baseline with uncertainty caveats.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Linear regression and coefficient meaning | Fit price or demand baseline with sklearn LinearRegression | Residual plot reveals model limitations |
| 14 | Regularization Ridge/Lasso | Compare training/validation curves as alpha varies | Selected regularization chosen via CV only |
| 15 | MAE, RMSE and R2 | Evaluate three baselines against same split | Metric units and large-error sensitivity explained |
| 16 | Polynomial features and overfitting | Build polynomial pipeline of varying degree | Validation behavior shows overfitting |
| 17 | Time-aware validation | Evaluate chronological split for sales forecast | Future observations never train past prediction |
| 18 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Demand forecast baseline with uncertainty caveats**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 3 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 4: Days 19–24 — Classification and evaluation

**Weekly deliverable:** Imbalanced classification report.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Logistic regression and decision boundaries | Classify synthetic data with normalized features | Boundaries plotted and explained |
| 20 | Decision trees and ensembles | Train tree, random forest, gradient boosting baseline | Train/validation differences documented |
| 21 | Imbalanced data and threshold choice | Tune threshold on validation data only | Precision-recall tradeoff quantified |
| 22 | ROC-AUC vs PR-AUC | Report ROC and precision-recall curves | Metric selection justified by positive class frequency |
| 23 | Calibration and reliability | Generate calibration curve and Brier score | Probability reliability discussed not just accuracy |
| 24 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Imbalanced classification report**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 4 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 5: Days 25–30 — Hyperparameter search and features

**Weekly deliverable:** Tuned pipeline with defensible validation.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | GridSearchCV and RandomizedSearchCV | Compare 2 parameter spaces on pipeline | Only train folds used for selection |
| 26 | Nested CV concept | Implement small nested CV evaluation | Selection and evaluation folds distinguished |
| 27 | Feature selection | Add select-k or model-based selection inside pipeline | Selection leakage avoided |
| 28 | Permutation importance and interpretation | Compute importance on held-out data | Correlated-feature caveat written down |
| 29 | Learning curves and data size | Measure validation score with sample size | Under/overfit diagnosis grounded in curves |
| 30 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Tuned pipeline with defensible validation**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 5 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 6: Days 31–36 — Unsupervised learning

**Weekly deliverable:** Cluster and anomaly analysis study.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | KMeans and scaling | Cluster numeric features with normalization | Scores and sample profiles reported |
| 32 | DBSCAN and density patterns | Compare KMeans with DBSCAN on non-convex shapes | Noise points handled and differences explained |
| 33 | PCA for visualization | Plot first two PCA components with variance ratios | PCA fit to training set for predictive use |
| 34 | Anomaly detection basics | Use IsolationForest on a synthetic anomaly dataset | Precision/false alarms discussed with labels if available |
| 35 | Clustering evaluation caution | Compare silhouette with real domain interpretation | No invented ground-truth labels for unlabeled samples |
| 36 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Cluster and anomaly analysis study**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 6 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 7: Days 37–42 — Experimental discipline

**Weekly deliverable:** Reproducible ML experiment suite.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Data leakage through preprocessing | Break and fix an intentionally leaky pipeline | Demonstrate score inflation in controlled example |
| 38 | Group-aware and time-aware cross-validation | Evaluate patient/user/group style data with GroupKFold | Same entity never appears in both sides of a split |
| 39 | Multiple metrics and scoring | Configure cross_validate to record metrics and durations | Results table includes mean/spread over folds |
| 40 | Statistical uncertainty and bootstrapping | Bootstrap holdout prediction metric carefully | Interval and assumptions explained |
| 41 | Randomness, reproducibility and version pinning | Run model twice with fixed seeds and environment | Results close/identical with caveat documented |
| 42 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Reproducible ML experiment suite**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 7 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 8: Days 43–48 — Deployment and model risk

**Weekly deliverable:** Simple inference service with validation.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Train/inference feature schema | Validate types and missing values at prediction time | Inference rejects unseen columns rather than silent misalignment |
| 44 | joblib/pickle trust risks | Document trusted-only loading and alternate export formats | Never unpickle untrusted artifacts |
| 45 | Batch vs online inference | Add CLI batch scoring and simple request handler | Same pipeline used for both modes |
| 46 | Fairness slices and error analysis | Report subgroup metrics with careful sample sizes | Disparities and limitations transparent |
| 47 | Model cards and monitoring | Draft data, performance, failure and drift notes | Known blind spots recorded before release |
| 48 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Simple inference service with validation**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 8 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 9: Days 49–54 — Applied capstone design

**Weekly deliverable:** Candidate models and final untouched test set.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Choose realistic prediction task | Select dataset, target and decision metric | Problem framing specifies misuse risks |
| 50 | Create robust splits and baselines | Define leakage-safe train/validation/test strategy | Holdout never touched during selection |
| 51 | Train comparison models | Evaluate 3 models in common pipeline interface | Shared CV, metrics and compute budget |
| 52 | Error analysis and threshold policy | Inspect failures and choose intervention threshold | Decision threshold justified on validation only |
| 53 | Record experiment artifacts | Store config, seeds, metrics, plots and data provenance | Experiment runs reproducibly on fresh machine |
| 54 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Candidate models and final untouched test set**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 9 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 10: Days 55–60 — Capstone release

**Weekly deliverable:** Documented model and reproducible inference application.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Select model and refit responsibly | Freeze hyperparameters then fit intended training data | No post-test hyperparameter tuning |
| 56 | Final evaluation | Evaluate untouched test only once for final claim | Full metrics with uncertainty/limitations recorded |
| 57 | Prediction interface and tests | Add robust batch prediction with input validation | Both normal and malformed inputs covered |
| 58 | Security and model card | Document data source, fairness, domain and trust limits | Unsafe use cases explicitly excluded |
| 59 | Publish repo and demo | Tag version, add environment, README and CI | Another learner can reproduce evaluation and demo |
| 60 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Documented model and reproducible inference application**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 10 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

## Checkpoints: stop and demonstrate competence

| Checkpoint | When | Required proof | If you cannot pass |
|---|---|---|---|
| Checkpoint 0 | Day 18 | From a clean setup, demonstrate **demand forecast baseline with uncertainty caveats**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Checkpoint 1 | Day 36 | From a clean setup, demonstrate **cluster and anomaly analysis study**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Final capstone | Day 60 | Give a short working demo of **documented model and reproducible inference application**, rerun all checks, show README/limitations, and tag a release. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |

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

**Non-negotiable ML rule:** Split before learning preprocessing statistics, never select on the final test set, and be alert to group/time leakage. Cross-validation estimates vary by problem; do not interpret the test result as a guarantee of real-world performance.

## Official learning resources

| Resource | Link |
|---|---|
| Getting started | https://scikit-learn.org/stable/getting_started.html |
| Cross-validation | https://scikit-learn.org/stable/modules/cross_validation.html |
| Pipelines | https://scikit-learn.org/stable/modules/compose.html |
| Model evaluation | https://scikit-learn.org/stable/modules/model_evaluation.html |
| Common pitfalls | https://scikit-learn.org/stable/common_pitfalls.html |

**Resource/version policy:** These are official reference links checked while planning; dependencies and documentation evolve. Use the versions actually installed and verify release-specific API changes before copying an old example. Most resources are free; hosted cloud services or external infrastructure may have costs.

## What comes next

Extend the capstone with one feature, contribute a documentation fix or test to an open-source project, and revisit difficult checkpoints with no notes.

---
*This guide is a practical learning plan, not a credential or a guarantee of proficiency. Adapt the schedule to your pace; passing checkpoints matters more than calendar speed.*
