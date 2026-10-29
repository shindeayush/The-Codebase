# Qiskit (Python) Roadmap: From Zero to Quantum Circuits, Simulation and Noise-Aware Experiments

*Created: 29 October 2026 · 10 weeks · 60 sessions · ~190 guided hours*

## Start here

Learn qubit states, gates and measurement, then build circuits and local simulations in Qiskit, explore transpilation and noise, and present a defensible quantum experiment.

**Prerequisites:** Python and NumPy basics plus comfort with complex numbers, vectors, matrices and probability. No quantum hardware or IBM Cloud account needed for the main local track.

**By the end you will have:** a Git repository containing each session, weekly project demos, a journal, documented checkpoint results, tests or quality checks, and a polished capstone with setup steps that another learner can follow.

### Platform setup (Windows, Linux and macOS)

| Platform | Environment creation | Activation | Verify |
|---|---|---|---|
| Windows (PowerShell) | `py -m venv .venv` | `.\.venv\Scripts\Activate.ps1` | `python --version` |
| Linux | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |
| macOS | `python3 -m venv .venv` | `source .venv/bin/activate` | `python --version` |

Run package installations **after activation**, from the guide's project root. On Windows, use the Windows Python launcher (`py`) to create the environment if `python` is not yet configured. For restricted PowerShell execution policies, use Command Prompt with `.venv\Scripts\activate.bat` rather than changing system-wide policy. Confirm that `python -m pip --version` points to the virtual environment. Keep `.venv/` and secrets out of Git. For incompatible versions, consult the official project's install matrix and select a supported Python version; do not silently install an older runtime-wide package.

On **64-bit Windows, Linux or macOS** use a supported CPython version and virtual environment. Install local Qiskit and optional simulator:
```bash
python -m pip install qiskit qiskit-aer matplotlib numpy pytest
```
First local Bell-state example (uses Qiskit 2.x-style primitives):
```python
from qiskit import QuantumCircuit
from qiskit.primitives import StatevectorSampler
qc = QuantumCircuit(2)
qc.h(0)
qc.cx(0, 1)
qc.measure_all()
result = StatevectorSampler().run([qc], shots=1000).result()
print(result[0].data.meas.get_counts())
```
Counts should be mostly `00` and `11`, subject to statistical fluctuation. **Hardware access is optional** and may require a separate account, permission, credits and queue time. Avoid legacy `execute`, `BasicAer` or outdated provider-specific tutorials unless explicitly adapting old code.

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

### Week 1: Days 1–6 — Quantum intuition and first circuits

**Weekly deliverable:** One- and two-qubit circuits with measured outcomes.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 1 | Bits vs qubits, complex amplitudes and probabilities | Compute one-qubit measurement probabilities by hand | Normalization sum is 1 and notation explained |
| 2 | Qiskit QuantumCircuit and draw | Draw X, H and measurement circuits | Diagram matches gate order and measured outcome |
| 3 | X, Y, Z and Hadamard gates | Compare expected statevectors for simple gate sequences | Statevector result agrees with linear algebra |
| 4 | Measure and sample with StatevectorSampler | Sample H\|0> in Z basis over increasing shots | Frequencies approach 50/50 with sampling variation |
| 5 | Two-qubit registers and tensor products | Create product state and examine basis order | Register/bit ordering documented in outputs |
| 6 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **One- and two-qubit circuits with measured outcomes**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 1 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 2: Days 7–12 — Entanglement and interference

**Weekly deliverable:** Bell-state and correlation experiment.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 7 | CNOT, controlled operations and Bell states | Prepare four Bell states using gates | Distinguish states using statevector comparison |
| 8 | Entanglement vs classical correlation | Compare Bell measurements to separable mixtures | Correlations described without claiming superluminal signaling |
| 9 | Phase and interference | Make H-Z-H and compare with X effect | Measurement distribution matches interference prediction |
| 10 | Bloch sphere intuition | Visualize single-qubit states before/after rotations | Visual representation matches statevector up to global phase |
| 11 | Measurement bases | Measure in X basis using pre-rotations | Basis change explained and verified by counts |
| 12 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Bell-state and correlation experiment**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 2 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 3: Days 13–18 — Mathematical building blocks

**Weekly deliverable:** Parameterized circuit study with analytic references.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 13 | Unitary matrices and composition order | Multiply gates in NumPy and compare final state | Matrices and statevector agree within tolerance |
| 14 | Rotation gates RX/RY/RZ | Sweep angle theta and sample output | Probability curve agrees with sin/cos prediction |
| 15 | Relative vs global phase | Construct circuits differing by global phase | Same measurement probabilities explained |
| 16 | Observables and expectation values | Compute Pauli-Z expectation for parameterized circuit | Exact value matches analytic formula |
| 17 | Parameter and parameter binding | Build circuit once and evaluate multiple settings | No manual circuit copy needed for each angle |
| 18 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Parameterized circuit study with analytic references**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 3 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 4: Days 19–24 — Local simulation and noise

**Weekly deliverable:** Simulator comparison report.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 19 | Statevector vs shot-based sampling | Compare exact probabilities to finite-shot histograms | Shot noise quantified in table |
| 20 | Qiskit Aer simulator basics | Simulate ideal circuits with AerSimulator | Counts agree with statevector within expected error |
| 21 | Noise channel intuition | Model depolarizing or bit-flip channel in Aer | Noisy error trend increases with chosen noise |
| 22 | Measurement and readout error | Add readout error and compare distribution | Effects of hardware-like error explained |
| 23 | Reproducible experiments | Fix simulator seed and write experiment config | Same run produces stable counts under fixed config |
| 24 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Simulator comparison report**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 4 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 5: Days 25–30 — Transpilation and gate sets

**Weekly deliverable:** Transpilation cost experiment.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 25 | Circuit decomposition and basis gates | Transpile H, CX and rotations into chosen basis | Resulting circuit preserves behavior |
| 26 | Coupling maps and topology | Transpile same circuit under restricted connections | Routing adds gates or swaps as expected |
| 27 | Optimization levels and passes | Compare depth and gate counts across settings | Table includes both depth and 2q gate count |
| 28 | Circuit equivalence checks | Use statevector/operator compare on small circuits | Equivalent up to allowable global phase |
| 29 | Draw and report transpiled circuits | Produce before/after diagrams with metrics | Explain why lower depth may not always mean lower error |
| 30 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Transpilation cost experiment**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 5 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 6: Days 31–36 — Algorithms with realistic claims

**Weekly deliverable:** Tiny search and phase-estimation demonstration.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 31 | Deutsch-Jozsa oracle concepts | Construct balanced and constant oracles at small n | Output distinguishes chosen examples on simulator |
| 32 | Grover search concept | Build 2-qubit marked-state amplification | Target probability rises for suitable iteration count |
| 33 | Quantum Fourier Transform intuition | Compare QFT on basis state with reference | Amplitudes match manual/NumPy calculation |
| 34 | Phase estimation as concept | Simulate tiny phase-kickback example | Probability outcomes and limitations documented |
| 35 | Algorithmic complexity caveats | Compare circuit resource cost against classic tiny case | No claim of practical speedup from 2-4 qubits |
| 36 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Tiny search and phase-estimation demonstration**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 6 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 7: Days 37–42 — Variational algorithms and primitives

**Weekly deliverable:** Small variational optimization study.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 37 | Ansatz and classical optimizer | Make parameterized 2-qubit ansatz with cost | Loss/objective defined explicitly |
| 38 | Estimator primitive concept | Calculate expectation values via supported estimator APIs or statevector | Output matches analytic benchmark |
| 39 | VQE idea on toy Hamiltonian | Minimize a 2-qubit observable energy | Final energy compared with exact eigensolver |
| 40 | Optimization landscape and shots | Evaluate varying seeds and shot budgets | Variance and convergence behavior described |
| 41 | Barren plateaus and practical scaling | Explain why depth/noise/gradient cost matters | Written analysis distinguishes toy vs large systems |
| 42 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Small variational optimization study**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 7 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 8: Days 43–48 — Quantum error and validation

**Weekly deliverable:** Noise-aware experiment with checks.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 43 | Error mitigation vs error correction | Demonstrate simple readout calibration concept | Explicitly not claiming full error correction |
| 44 | Error-correcting codes concept | Draw 3-qubit bit-flip code and simulate one error | Logical recovery works for one chosen bit flip |
| 45 | Tomography limitations | Reconstruct simple state information from basis measurements | Sampling/measurement cost acknowledged |
| 46 | Property tests for circuits | Verify normalization, unitary property and conserved probabilities | At least 15 local tests pass |
| 47 | Scientific experimental design | Choose baseline, shots, repetitions and uncertainty report | Every plotted quantity is labelled and reproducible |
| 48 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Noise-aware experiment with checks**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 8 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 9: Days 49–54 — Optional cloud hardware and reproducibility

**Weekly deliverable:** Hardware-readiness and simulator fallback package.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 49 | IBM Runtime overview and access | Read cloud job/runtime prerequisites without storing credentials | No account required for local progress |
| 50 | Backends, calibration and job lifecycle | Design circuit execution flow with backend properties | QPU queue/credit constraints acknowledged |
| 51 | ISA circuits and transpilation | Prepare hardware-compatible mapped circuit | Conforms to chosen target basis/coupling |
| 52 | Simulator vs hardware caveats | Compare ideal, noisy simulator and optional hardware design | Discrepancy explanations avoid unwarranted claims |
| 53 | Credential hygiene and cost controls | Store tokens in environment and add budget guard | No token in Git, screenshot or report |
| 54 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Hardware-readiness and simulator fallback package**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 9 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

### Week 10: Days 55–60 — Capstone

**Weekly deliverable:** Reproducible entanglement, noise and circuit-cost report.

| Day | Learn | Build | Done when |
|---:|---|---|---|
| 55 | Define research question | Choose Bell inequality, noise sweep or small VQE toy study | Observable, baseline and hypothesis specified |
| 56 | Build exact and sampled simulations | Implement noiseless reference and finite-shot experiments | Difference measured with error bars or CIs |
| 57 | Noise/transpilation comparison | Vary noise, depth or coupling constraints systematically | Circuit metrics and outcome distributions recorded |
| 58 | Tests and limitations | Add analytic checks and discuss limitations | Model does not claim quantum advantage from toy simulation |
| 59 | Publish reproducible report | Provide notebook/script, configs, diagrams, README and demo | Peer reproduces figures and numeric conclusions locally |
| 60 | **Project and review**: integrate this week’s topics and revisit the weakest exercise. | **Reproducible entanglement, noise and circuit-cost report**. Keep a 3-minute demo, a journal note and a Git tag or review commit. | Demo core workflow, show one valid and one invalid case, run relevant checks, and explain the key design choices. |

**Week 10 review questions:** What changed in your mental model? Which bug took longest to diagnose? What would break under invalid input, missing files, slow services, or a different OS? What evidence supports the outcome?

## Checkpoints: stop and demonstrate competence

| Checkpoint | When | Required proof | If you cannot pass |
|---|---|---|---|
| Checkpoint 0 | Day 18 | From a clean setup, demonstrate **parameterized circuit study with analytic references**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Checkpoint 1 | Day 36 | From a clean setup, demonstrate **tiny search and phase-estimation demonstration**, plus boundary/error cases, an explanation of core concepts, and evidence of tests or quality checks. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |
| Final capstone | Day 60 | Give a short working demo of **reproducible entanglement, noise and circuit-cost report**, rerun all checks, show README/limitations, and tag a release. | Redo targeted sessions and repeat the checkpoint; do not push an unverified feature forward. |

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

**Scope and scientific honesty:** You do not need a quantum computer for this guide. Simulation does not demonstrate quantum advantage; shot sampling fluctuates. Hardware execution is optional, potentially billable, and requires credentials you must not put in source control. Avoid old `execute`/`Aer` import recipes that target incompatible older releases.

## Official learning resources

| Resource | Link |
|---|---|
| IBM Quantum quickstart | https://quantum.cloud.ibm.com/docs/en/guides/quick-start |
| Install Qiskit | https://quantum.cloud.ibm.com/docs/en/guides/install-qiskit |
| Qiskit tutorials | https://quantum.cloud.ibm.com/docs/en/tutorials |
| Qiskit API docs | https://quantum.cloud.ibm.com/docs/en/api/qiskit |
| Qiskit Aer docs | https://qiskit.github.io/qiskit-aer/ |

**Resource/version policy:** These are official reference links checked while planning; dependencies and documentation evolve. Use the versions actually installed and verify release-specific API changes before copying an old example. Most resources are free; hosted cloud services or external infrastructure may have costs.

## What comes next

Extend the capstone with one feature, contribute a documentation fix or test to an open-source project, and revisit difficult checkpoints with no notes.

---
*This guide is a practical learning plan, not a credential or a guarantee of proficiency. Adapt the schedule to your pace; passing checkpoints matters more than calendar speed.*
