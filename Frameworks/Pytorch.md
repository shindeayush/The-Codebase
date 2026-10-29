# PyTorch (Python) Roadmap: From Zero to Deep Learning, Autograd and Reliable Training

*Created: 29 October 2026 · 12 weeks · 72 sessions · ~228 guided hours*

## Start here

Learn tensors and autograd, build neural networks with `nn.Module`, construct data pipelines, train and evaluate models, then package a reproducible inference demo.

**Prerequisites:** Python, NumPy, basic matrix algebra and calculus intuition, plus introductory ML evaluation. Start CPU-first; a dedicated GPU is optional.

**By the end you will have:** a Git repository containing each session, weekly project demos, a journal, documented checkpoint results, tests or quality checks, and a polished capstone with setup steps that another learner can follow.

### Platform setup (Windows, Linux and macOS)

| Platform | Environment creation | Activation | Verify |
|---|---|---|---|
| Windows (PowerShell) | `py -m venv .venv` | `.\.venv\Scripts\Activate.ps1` | `python --version` |
| Linux | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |
| macOS | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |

Run package installations **after activation**, from the guide's project root. On Windows, use the Windows Python launcher (`py`) to create the environment if `python` is not yet configured. For restricted PowerShell execution policies, use Command Prompt with `.venv\Scripts\activate.bat` rather than changing system-wide policy. Confirm that `python -m pip --version` points to the virtual environment. Keep `.venv/` and secrets out of Git. For incompatible versions, consult the official project's install matrix and select a supported Python version; do not silently install an older runtime-wide package.

Create a supported Python environment on Windows, Linux or macOS. **Select your actual OS, package manager and compute platform** at https://pytorch.org/get-started/locally/ for the authoritative installation command. A common simple CPU-capable introduction is:
```bash
python -m pip install torch torchvision matplotlib numpy pytest
python -c "import torch; print(torch.__version__); print(torch.rand(2,3)); print(torch.cuda.is_available())"
```
Choose the official selector if you need CUDA/ROCm/CPU-only wheels. On Apple Silicon, check `torch.backends.mps.is_available()`; acceleration availability varies. All core exercises can be run with small CPU datasets.

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

### Week 1: Days 1–6 — Tensors and shapes

**Weekly deliverable:** Tensor operations and shape-test workbook.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Tensor construction, shape, dtype and device | Create image batches and tabular tensors | Shape/dtype expectations checked with asserts |
| 2 | Indexing, slicing, broadcasting | Implement batch-wise normalization and mask | Compare NumPy and torch outputs |
| 3 | Tensor arithmetic and matmul | Implement pairwise similarity on small batch | Numerical match to hand-computed example |
| 4 | Conversions and device transfer | Move arrays to tensors and back safely | `.detach().cpu().numpy()` used where required |
| 5 | Random seeds and reproducibility | Demonstrate seeded init and shuffle | Repeat runs explain deterministic limits |
| 6 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Tensor operations and shape-test workbook**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 1 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 2: Days 7–12 — Autograd and optimization

**Weekly deliverable:** Linear regression trained from scratch.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | Gradient tracking and computation graph | Differentiate quadratic and check result by hand | `.grad` agrees with expected derivative |
| 8 | Backprop through vector operations | Implement MSE loss on synthetic data | Gradients match finite-difference check |
| 9 | SGD and learning rate | Train two-parameter linear model manually | Loss decreases and coefficients approach truth |
| 10 | `torch.no_grad` and inference mode | Evaluate without recording gradients | Outputs same; graph not retained |
| 11 | Gradient pitfalls | Demonstrate accumulation and clearing grads | You can explain when `zero_grad` is required |
| 12 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Linear regression trained from scratch**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 2 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 3: Days 13–18 — Neural network modules

**Weekly deliverable:** Small multilayer perceptron trainer.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | nn.Module, parameters and forward | Implement two-layer classifier | Named parameters and output shapes correct |
| 14 | Common activations, losses | Compare ReLU/softmax logic and CrossEntropyLoss input rules | No accidental pre-softmax misuse for cross entropy |
| 15 | torch.optim and schedulers | Fit MLP with Adam or SGD and schedule | Training loss/log data recorded |
| 16 | Train/eval mode | Add Dropout and explain behavior | Eval mode stabilizes deterministic inference |
| 17 | Checkpoint saving and loading | Save/reload `state_dict` into same architecture | Prediction before/after matches within tolerance |
| 18 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Small multilayer perceptron trainer**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 3 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 4: Days 19–24 — Datasets and loaders

**Weekly deliverable:** Reproducible training experiment on small data.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Dataset and DataLoader | Wrap tabular or synthetic image data in Dataset | Shuffling/batch shape tested |
| 20 | Transforms and normalization | Build training and eval transform pipelines | Validation transform has no random augmentation |
| 21 | Train/validation/test separation | Create reproducible split by ID | No sample appears in two splits |
| 22 | Mini-batch training loop | Add epoch metrics, early stop and best checkpoint | Best validation epoch reproducibly selected |
| 23 | Class imbalance and sampling | Compare weighted loss and sampler options | No duplicated samples slip into evaluation unnoticed |
| 24 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Reproducible training experiment on small data**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 4 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 5: Days 25–30 — Convolution and image classification

**Weekly deliverable:** Simple CNN with controlled input size.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Convolutions, channels and kernels | Manually compute small conv and compare with torch | Output spatial dimensions correct |
| 26 | Pooling and feature maps | Build CNN block and inspect activation shapes | Shapes valid after multiple layers |
| 27 | Data augmentation | Add safe transforms for labeled sample images | Transforms do not change true label semantics |
| 28 | Evaluate image classifier | Train small CNN on CPU-friendly dataset | Confusion matrix and per-class F1 computed |
| 29 | Overfitting and regularization | Compare train/eval curves and tune dropout | Intervention justified by validation data |
| 30 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Simple CNN with controlled input size**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 5 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 6: Days 31–36 — NLP and sequential fundamentals

**Weekly deliverable:** Text classifier with embeddings.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Tokenization, vocab and padding | Build simple deterministic text tensorizer | OOV tokens and padding handled consistently |
| 32 | Embeddings and pooling | Implement average embedding classifier | Batched outputs shapes match labels |
| 33 | Sequence masking concept | Exclude padding tokens from pooled average | Padding length does not change prediction |
| 34 | Attention intuition | Implement tiny scaled dot-product attention example | Attention weights sum to 1 along correct axis |
| 35 | Compare simple baselines | Compare bag-of-words linear vs embedding classifier | Report what more complex model does or does not improve |
| 36 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Text classifier with embeddings**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 6 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 7: Days 37–42 — Training diagnostics and numerical stability

**Weekly deliverable:** Instrumented reproducible training loop.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Vanishing/exploding gradients | Log gradient norms and simulate unstable config | Failed run explained with evidence |
| 38 | Clipping and weight decay | Add gradient clipping and regularization to model | Norm thresholds honored and train script still converges |
| 39 | Mixed precision considerations | Test autocast only if backend supports it | FP32 fallback works and accuracy compared |
| 40 | Profiling model and input pipeline | Time data loading vs compute | Identify actual bottleneck before optimizing |
| 41 | Experiment logging and configs | Save hyperparameters, seed, epoch results to JSON | Model training reproducible from run config |
| 42 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Instrumented reproducible training loop**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 7 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 8: Days 43–48 — Transfer learning and careful evaluation

**Weekly deliverable:** Feature extractor/classifier with error analysis.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Pretrained weights and frozen features | Fine-tune last layer on small public dataset | Frozen parameter gradients remain off |
| 44 | Fine-tuning learning rates | Unfreeze selectively and compare validation | Chosen rate supported by validation curve |
| 45 | Class metrics and calibration | Report macro F1, per-class recall and uncertainty | Rare classes not hidden by overall accuracy |
| 46 | Adversarial and out-of-distribution caution | Test corrupted/noisy images for model robustness | Failure modes and non-guarantees stated |
| 47 | Data leakage and duplication | Detect near-duplicate train/eval examples | Clear split policy documented |
| 48 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Feature extractor/classifier with error analysis**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 8 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 9: Days 49–54 — Advanced device and data performance

**Weekly deliverable:** Faster, memory-aware training run.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | Pinned memory and workers | Benchmark DataLoader settings on chosen OS | Worker configuration verified (esp. Windows spawn) |
| 50 | Gradient accumulation | Emulate larger effective batch with accumulation | Optimization steps counted correctly |
| 51 | torch.compile overview | Compare eager vs compiled where supported | Fallback allowed and time/compatibility recorded |
| 52 | Distributed training concepts | Explain DDP, rank, data partition and all-reduce | Small design diagram without pretending multi-GPU exists |
| 53 | CPU/MPS/CUDA device selection | Make device-agnostic training script | CPU always works; optional accelerator checked |
| 54 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Faster, memory-aware training run**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 9 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 10: Days 55–60 — Packaging and inference

**Weekly deliverable:** Versioned inference command and model card.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Input pipeline parity | Use same preprocessing in train/infer paths | Identical sample predictions across both |
| 56 | Safe model artifacts | Save/load weights using safe approach and trusted files | Avoid arbitrary untrusted pickle loading |
| 57 | Batch inference with latency | Benchmark batch sizes for CPU and optional GPU | Throughput/latency table records device |
| 58 | Unit tests for network shapes | Test forward, loss, gradients and serialized predictions | Key assertions pass for 2 input sizes |
| 59 | Model card and deployment risks | Document dataset licenses, risks, biases and limits | Reader knows unsupported uses |
| 60 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Versioned inference command and model card**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 10 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 11: Days 61–66 — Capstone build

**Weekly deliverable:** End-to-end model with reproducible training pipeline.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 61 | Scope and dataset selection | Choose image or text classification task with data policy | Train/validation/test split recorded before tuning |
| 62 | Baseline and architecture | Compare simple model with deeper option | Both models trained under same evaluation protocol |
| 63 | Training, checkpoint and metrics | Build reproducible training and checkpoint pipeline | Best checkpoint chosen by validation only |
| 64 | Error analysis and robustness | Inspect misclassified cases, corruptions and subgroup slices | At least 3 failure modes documented |
| 65 | Inference user experience | Build CLI or small web demo that loads model | Malformed inputs rejected and predictions annotated |
| 66 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **End-to-end model with reproducible training pipeline**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 11 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 12: Days 67–72 — Capstone release

**Weekly deliverable:** Tested model demo, paper-style report and CI.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 67 | Final untouched-test evaluation | Evaluate once with fixed settings | Metrics and confusion matrix recorded transparently |
| 68 | Performance and memory study | Measure inference speed and peak memory on actual device | Hardware and batch size documented |
| 69 | Testing and CI | Run CPU-only unit tests plus format/check scripts | CI succeeds without expensive GPU |
| 70 | Documentation and model card | Write architecture, dataset, install and limitations | Peer reproduces training/inference on tiny sample |
| 71 | Final demo and version tag | Tag release, record 2-minute demo and reflect | Repository has code, tests, weights policy and evidence |
| 72 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Tested model demo, paper-style report and CI**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 12 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

## Checkpoints: stop and demonstrate competence

| Checkpoint | When | Required proof | If you cannot pass |
|---|---|---|---|
| Checkpoint 0 | Day 18 | From a clean setup, demonstrate **small multilayer perceptron trainer**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Checkpoint 1 | Day 36 | From a clean setup, demonstrate **text classifier with embeddings**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Final capstone | Day 72 | Give a short working demo of **tested model demo, paper-style report and ci**, rerun all checks, show README/limitations, and tag a release. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |

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

**Hardware caveat:** GPU support depends on OS, drivers, wheel and backend. Start CPU-first and verify device before training. Avoid loading model objects from unknown sources; prefer validated weight files and pinned dependency versions.

## Official learning resources

| Resource | Link |
|---|---|
| Start locally | https://pytorch.org/get-started/locally/ |
| Learn the basics | https://pytorch.org/tutorials/beginner/basics/intro.html |
| Autograd | https://pytorch.org/tutorials/beginner/basics/autogradqs_tutorial.html |
| Saving models | https://pytorch.org/tutorials/beginner/basics/saveloadrun_tutorial.html |
| PyTorch docs | https://pytorch.org/docs/stable/index.html |

**Resource/version policy:** These are official reference links checked while planning; dependencies and documentation evolve. Use the versions actually installed and verify release-specific API changes before copying an old example. Most resources are free; hosted cloud services or external infrastructure may have costs.

## What comes next

Extend the capstone with one feature, contribute a documentation fix or test to an open-source project, and revisit difficult checkpoints with no notes.

---
*This guide is a practical learning plan, not a credential or a guarantee of proficiency. Adapt the schedule to your pace; passing checkpoints matters more than calendar speed.*
