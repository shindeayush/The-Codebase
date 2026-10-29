# TensorFlow (Python) Roadmap: From Zero to Keras Models and Deployable Machine Learning

*Created: 29 October 2026 · 12 weeks · 72 sessions · ~228 guided hours*

## Start here

Study tensors, TensorFlow ops and `tf.data`, train Keras models, evaluate responsibly, use callbacks and SavedModel export, and build a reliable inference workflow.

**Prerequisites:** Python, NumPy, elementary algebra, supervised-learning train/validation/test discipline. A GPU is optional; small models can train on CPU.

**By the end you will have:** a Git repository containing each session, weekly project demos, a journal, documented checkpoint results, tests or quality checks, and a polished capstone with setup steps that another learner can follow.

### Platform setup (Windows, Linux and macOS)

| Platform | Environment creation | Activation | Verify |
|---|---|---|---|
| Windows (PowerShell) | `py -m venv .venv` | `.\.venv\Scripts\Activate.ps1` | `python --version` |
| Linux | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |
| macOS | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |

Run package installations **after activation**, from the guide's project root. On Windows, use the Windows Python launcher (`py`) to create the environment if `python` is not yet configured. For restricted PowerShell execution policies, use Command Prompt with `.venv\Scripts\activate.bat` rather than changing system-wide policy. Confirm that `python -m pip --version` points to the virtual environment. Keep `.venv/` and secrets out of Git. For incompatible versions, consult the official project's install matrix and select a supported Python version; do not silently install an older runtime-wide package.

On Windows, Linux or macOS, use a supported Python/OS combination listed at https://www.tensorflow.org/install/pip. Create a fresh virtual environment, then install CPU-capable TensorFlow:
```bash
python -m pip install tensorflow matplotlib numpy pytest
python -c "import tensorflow as tf; print(tf.__version__); print(tf.reduce_sum(tf.ones((2,3))))"
```
For NVIDIA GPU use Linux or **Windows WSL2** and follow current `tensorflow[and-cuda]` instructions. **Native Windows TensorFlow 2.11+ does not support CUDA GPU**. The `tensorflow` CPU path can still be used on supported Windows configurations. Check Apple-specific acceleration separately; do not assume every GPU backend is officially supported.

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

### Week 1: Days 1–6 — TensorFlow fundamentals

**Weekly deliverable:** Tensor operations and introductory gradient notebook.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Tensor creation, shapes, dtype and eager execution | Create image and tabular tensors with shape assertions | Dtypes and rank documented, with scalar vs batch distinction |
| 2 | Broadcasting, reductions and matmul | Implement normalization and matrix transform | Results match NumPy within tolerance |
| 3 | Variables, GradientTape and derivatives | Differentiate small quadratic and linear loss | Computed gradients match analytic values |
| 4 | tf.function and tracing basics | Wrap function and inspect retracing on shape changes | Explain eager vs traced behavior with test |
| 5 | Random seeds and device visibility | Create reproducible synthetic dataset | Seeding and device limits explained accurately |
| 6 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Tensor operations and introductory gradient notebook**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 1 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 2: Days 7–12 — Keras sequential modeling

**Weekly deliverable:** First trained classifier with validation metrics.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Keras Sequential and Dense layers | Build 2-layer network and print model summary | Output shape and parameter count explainable |
| 8 | Losses, metrics and optimizers | Compile binary/multiclass model correctly | Final layer/loss pairing verified |
| 9 | fit/evaluate/predict lifecycle | Train on small toy dataset | Training and validation tracked separately |
| 10 | EarlyStopping and ModelCheckpoint | Save best model based on validation metric | Reloaded model gives comparable prediction |
| 11 | Train/validation/test split | Split before fitting transforms | Test labels unused for model selection |
| 12 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **First trained classifier with validation metrics**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 2 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 3: Days 13–18 — Functional API and custom layers

**Weekly deliverable:** Multi-input prediction model.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Functional model graphs | Build two-input network and concatenate features | Model summary shows intended graph |
| 14 | Subclassed models vs functional | Implement custom small model | Behavior matches simpler reference on same weights |
| 15 | Custom layers and serialization | Create normalizing layer with config | Saving and loading preserves layer behavior |
| 16 | Regularization and dropout | Compare model with/without weight regularization | Validation comparison documented |
| 17 | Loss weighting and metrics | Train on imbalanced synthetic categories with class weights | Per-class metrics exposed rather than just accuracy |
| 18 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Multi-input prediction model**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 3 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 4: Days 19–24 — tf.data ingestion and performance

**Weekly deliverable:** Data input pipeline with validation and repeatability.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | tf.data from tensors/generators | Build Dataset with map, shuffle and batch | Element specs and batch sizes checked |
| 20 | Map, cache, prefetch | Compare basic vs optimized input pipeline | Measured speed and memory tradeoff recorded |
| 21 | Parsing and augmentation | Apply image/text transform to training data only | Validation pipeline deterministic |
| 22 | Determinism and shuffling | Fix seeds where practical and record limitations | Repeatability test passes within tolerance |
| 23 | Data integrity and labels | Test malformed sample and label mismatch | Pipeline rejects or logs invalid examples |
| 24 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Data input pipeline with validation and repeatability**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 4 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 5: Days 25–30 — Image learning and CNNs

**Weekly deliverable:** CNN image classifier with error report.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Conv2D, pooling and padding | Build small CNN and predict output dimensions | Shapes match hand calculation |
| 26 | Image preprocessing and normalization | Implement consistent resized/scaled image pipeline | Same transform used for inference |
| 27 | Data augmentation and regularization | Train with label-preserving augmentation | Overfitting comparison with baseline reported |
| 28 | Transfer learning with Keras Applications | Freeze backbone and train head on small dataset | Frozen weights unchanged |
| 29 | Fine-tuning and evaluation | Unfreeze selected layers and compare validation | No use of final test set for tuning |
| 30 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **CNN image classifier with error report**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 5 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 6: Days 31–36 — Text and sequence fundamentals

**Weekly deliverable:** Sequence/text classification prototype.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | TextVectorization and vocabulary | Build text preprocessing layer and OOV logic | Text input produces valid fixed shapes |
| 32 | Embedding and sequence pooling | Train small sentiment-like synthetic classifier | Pad tokens handled appropriately |
| 33 | Recurrent layers (GRU/LSTM) | Fit short sequence classifier | Variable-length handling and masks verified |
| 34 | Attention concepts | Build toy attention calculation and compare with Keras layer | Weights and output shapes interpreted |
| 35 | Evaluation of text inputs | Test negation, typos and unseen words | Failures summarized without overclaiming reliability |
| 36 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Sequence/text classification prototype**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 6 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 7: Days 37–42 — Custom training and debugging

**Weekly deliverable:** Inspectable custom-fit training experiment.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | GradientTape custom training loop | Train mini-model manually with optimizer | Loss and gradients align with model.fit reference |
| 38 | Metric objects and reset_state | Implement per-epoch accuracy and loss tracking | Metrics not accidentally cumulative across epochs |
| 39 | Gradient clipping and stability | Demonstrate divergent run then fix with clipping/learning rate | Evidence shows stable objective |
| 40 | Distribution strategy overview | Run single-device strategy and draw replica concept | No unsupported multi-GPU claims |
| 41 | Profiler and TensorBoard | Inspect batch timings and learning curves | Performance claim tied to actual traces |
| 42 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Inspectable custom-fit training experiment**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 7 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 8: Days 43–48 — Evaluation and model reliability

**Weekly deliverable:** Robust benchmark and model card.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Metric selection and confusion matrices | Evaluate macro F1, precision/recall and confusion | Minority classes not hidden |
| 44 | Calibration and uncertainty concepts | Plot predicted confidence vs correctness | Overconfident errors identified |
| 45 | Bias, leakage and split integrity | Check duplicates/groups/time boundaries | Leakage pathways documented and corrected |
| 46 | Hyperparameter search discipline | Compare compact experiments using validation only | Test set untouched until final selection |
| 47 | Reproducible environments | Lock dependencies and record run configuration | Peer can reproduce training from fixed seed/data |
| 48 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Robust benchmark and model card**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 8 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 9: Days 49–54 — Serialization and serving

**Weekly deliverable:** Inference package with explicit input schema.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Keras `.keras` saving and loading | Save and reload trainable model for further training | Predictions compare within tolerance |
| 50 | SavedModel export and signatures | Export inference artifact with supported `model.export` workflow | Reloaded endpoint serves expected tensor signatures |
| 51 | Batch and online inference | Create validated batch-scoring script | Unknown shapes/types receive descriptive error |
| 52 | Performance and quantization concepts | Explore optional TFLite conversion on supported model | Accuracy and latency measured before/after |
| 53 | Production safety | Document request limits, PII and artifact trust policy | Untrusted input paths and secrets handled safely |
| 54 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Inference package with explicit input schema**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 9 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 10: Days 55–60 — Deployment and maintainability

**Weekly deliverable:** CI-verified inference application.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Serving tradeoffs | Compare simple Python service vs TensorFlow Serving use cases | Choice justified by operational complexity |
| 56 | CPU vs supported accelerators | Benchmark same batch across available devices | Device type and version recorded honestly |
| 57 | CI pipeline | Run inference smoke tests and small unit training | CI passes without GPU or large data |
| 58 | Monitoring data shift and drift | Simulate drifted input and track prediction statistics | Drift alert rule explained and tested |
| 59 | Versioning, rollback and model cards | Prepare release artifact plus rollback notes | Old model can be restored in test |
| 60 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **CI-verified inference application**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 10 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 11: Days 61–66 — Capstone implementation

**Weekly deliverable:** Trained and evaluated real-data model.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 61 | Select suitable dataset and metric | Write feature/label and split policy | Data license and leakage risks reviewed |
| 62 | Build preprocessing and model | Create reusable tf.data/Keras pipelines | Training/inference preprocessing consistent |
| 63 | Train with callbacks and compare baseline | Keep learning curves and best checkpoint | Best config chosen without test leakage |
| 64 | Error analysis | Inspect confusion, confidence and problematic cases | At least 3 failure modes described |
| 65 | Build inference endpoint or CLI | Implement validated prediction interface | Normal/bad requests covered by tests |
| 66 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Trained and evaluated real-data model**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 11 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 12: Days 67–72 — Capstone release

**Weekly deliverable:** Reproducible Keras model and deployment-ready inference demo.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 67 | Freeze final architecture and test | Run evaluation on untouched test | Main metrics and confidence caveats reported |
| 68 | Export and model signature tests | Export model and run inference from exported artifact | Same fixture gives comparable predictions |
| 69 | Performance and resource report | Measure latency, memory and throughput on available device | Clear CPU/GPU disclosures |
| 70 | Docs, CI and security review | Write model card, sample commands and CI | Fresh install follows README successfully |
| 71 | Record demo, tag and reflect | Release code, artifact policy, results and known limits | Peer can reproduce demo from clean environment |
| 72 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Reproducible Keras model and deployment-ready inference demo**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 12 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

## Checkpoints: stop and demonstrate competence

| Checkpoint | When | Required proof | If you cannot pass |
|---|---|---|---|
| Checkpoint 0 | Day 18 | From a clean setup, demonstrate **multi-input prediction model**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Checkpoint 1 | Day 36 | From a clean setup, demonstrate **sequence/text classification prototype**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Final capstone | Day 72 | Give a short working demo of **reproducible keras model and deployment-ready inference demo**, rerun all checks, show README/limitations, and tag a release. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |

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

**Important compatibility note:** New TensorFlow + native Windows CUDA GPU is not the supported path; use Linux or WSL2 for NVIDIA GPU according to current install docs. Model export APIs vary by Keras version: `.keras` for reloadable Keras models, `model.export()` for inference artifacts. Do not conflate them.

## Official learning resources

| Resource | Link |
|---|---|
| Install TensorFlow | https://www.tensorflow.org/install/pip |
| TensorFlow tutorials | https://www.tensorflow.org/tutorials |
| Keras guide | https://keras.io/guides/ |
| tf.data | https://www.tensorflow.org/guide/data |
| SavedModel | https://www.tensorflow.org/guide/saved_model |

**Resource/version policy:** These are official reference links checked while planning; dependencies and documentation evolve. Use the versions actually installed and verify release-specific API changes before copying an old example. Most resources are free; hosted cloud services or external infrastructure may have costs.

## What comes next

Extend the capstone with one feature, contribute a documentation fix or test to an open-source project, and revisit difficult checkpoints with no notes.

---
*This guide is a practical learning plan, not a credential or a guarantee of proficiency. Adapt the schedule to your pace; passing checkpoints matters more than calendar speed.*
