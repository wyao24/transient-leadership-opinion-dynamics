# Transient Leadership and Popularity-Adaptive Kinetic Opinion Dynamics

This repository contains simulation code, experiment artifacts, and report materials for **kinetic/mean-field models of opinion formation under selective leader control**. The project is built for applied mathematics and quantitative social-dynamics research (not machine-learning benchmarking).

## 1) Research Framing (Quantitative Focus)

The central research question is:

> How do **opinion control** and **contact/popularity control** applied to leader subsets change macroscopic opinion distributions, concentration/fragmentation, and long-time regime structure?

The implementation operationalizes this with:
- binary-interaction Monte Carlo particle dynamics;
- coupled opinion-contact state variables;
- leader/follower population structure with selective controls;
- scenario comparisons across single-leader, two-leader, and extended transient-leadership settings.

## 2) Mathematical and Computational Model

Each particle has at least:
- opinion \(v \in [-1,1]\),
- contact/popularity \(c \ge 0\),
- group label (mass/follower, leader A, leader B).

The code follows the standard kinetic modeling pipeline:
1. microscopic binary interactions;
2. Boltzmann-type aggregate interpretation;
3. quasi-invariant scaling linkage to Fokker-Planck drift/diffusion regimes;
4. selective controls in opinion/contact channels for designated leader groups.

### Key implemented components
- **Compromise kernel with contact-weighted influence** (`compromise_terms`).
- **Contact dynamics modulation** (`psi_eps`, `phi_v`, `Rc`, `Hc_from_rho`).
- **Opinion diffusion** via \(D(v)=1-v^2\) and stochastic perturbations.
- **Local mass estimator** for neighborhood-density terms (`LocalMassEstimator`).
- **Histogram-based density reconstruction** for joint and marginal diagnostics.

## 3) Parameterization

Baseline model parameters are encoded in `table1_params()` and represent the canonical setup used by the reproduction script.

### Table 1 parameter set (implemented defaults)
- Contacts: `beta=1.0`, `mu=0.0`, `c_bar=200.0`, `theta=2.0`, `delta_phi=0.1`, `nu=0.1`
- Contact control: `gamma_c=1.0`, `lam=1.0`, `alpha_R=0.1`, `alpha_H=0.1`, `r=0.7`, `rho_star=0.5`, `c_min=100.0`
- Opinion dynamics: `alpha=1.0`, `delta=0.8`, `p=3.0`, `v_tilde=0.5`, `sigma=0.1`
- Opinion control: `gamma_v=10.0`

For figure matching, `params_for_test(..., variant="figure")` additionally calibrates:
- Test 2: `theta=0.2`
- Test 3: `theta=0.05`

This split (paper vs figure) is explicit to support both faithful baseline runs and visual panel matching.

## 4) Runtime Regimes and Numerical Cost

`make_runtime(test_id, mode)` supports three computational regimes:
- `fast`: qualitative, development-friendly;
- `balanced`: lower Monte Carlo noise, still practical;
- `paper`: high-fidelity and expensive (`dt=1e-3`, `Ns=1_000_000`).

Default horizon by test family:
- Test 1/2: `T=50`
- Test 3: `T=150`

This makes sensitivity studies feasible: start with `fast`, validate trends in `balanced`, and only then escalate to `paper` runs.

## 5) Experiment Suite

All scripted experiments live in `src/albi2025_reproduction_v2.py`.

### Test 1 — Single-leader control comparison (`run_test1`)
Scenarios:
1. no control,
2. contact-only control,
3. opinion-only control,
4. joint contact+opinion control.

Primary outputs:
- density snapshots,
- marginal distributions,
- mean trajectories.

Figures:
- `results/figures/single-leader/test1_snapshots.png`
- `results/figures/control-comparisons/test1_means.png`

### Test 2 — Two-leader competition (`run_test2`)
Scenarios:
1. no control,
2. symmetric opinion control,
3. non-symmetric opinion control.

Primary outputs:
- snapshot panels comparing polarization and concentration patterns.

Figure:
- `results/figures/two-leader/test2_snapshots.png`

### Test 3 — Extended transient leadership (`run_test3`)
Scenarios:
1. opinion control on both leader groups,
2. opinion control on both + contact control on one group,
3. joint contact+opinion on both groups.

Primary outputs:
- long-horizon snapshots and marginal structures under richer control architectures.

Figures:
- `results/figures/transient-leadership/test3_config1.png`
- `results/figures/transient-leadership/test3_config2.png`
- `results/figures/transient-leadership/test3_config3.png`

### Exploratory notebook study
- Radical vs Populist analysis:
  - notebook: `notebooks/radical_vs_populist.ipynb`
  - figures: `results/figures/radical-vs-populist/rad_pop_main.png`, `rad_pop_w.png`

## 6) Quantitative Diagnostics You Can Extract

The current code and outputs are well-suited for quantitative reporting beyond visual inspection. Recommended metrics:
- opinion mean/variance by group over time,
- contact mean/variance by group,
- peak count and peak separation in opinion marginals (fragmentation proxy),
- Wasserstein or total-variation distance between scenario distributions,
- time-to-consensus / time-to-stationarity thresholds,
- control-effort proxies (integrated control intensity by channel and group).

These are not all prepackaged as CSV outputs yet, but can be computed from particle states and histogram arrays generated in the script.

## 7) Reproducibility Workflow

1. Create environment and install dependencies:
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt
   ```
2. Run experiment families via Python entrypoints (`run_test1`, `run_test2`, `run_test3`).
3. Generate figures with plotting helpers (`plot_test1_all`, `plot_test2_all`, `plot_test3_all`).
4. Store run artifacts under:
   - `results/figures/<family>/...`
   - `results/experiments/<experiment>/<timestamp-or-tag>/...`

`results/experiments/` is intentionally reserved for structured manifests (seed, mode, parameter profile, runtime, commit hash, derived metrics).

## 8) Repository Layout

- `src/` — core simulation/reproduction implementation.
- `notebooks/` — exploratory analyses and iterative workflows.
- `reports/` — project PDFs and presentation deck.
- `docs/` — structured narrative docs (overview, methods, experiments).
- `results/figures/` — generated visual outputs organized by test family.
- `results/experiments/` — structured run outputs/metadata (recommended target).
- `archive/` — references, templates, and superseded code.
- `INVENTORY.md` — repository audit notes.

## 9) Current Gaps and High-Value Next Steps

To better support quantitative-research pipelines, the next engineering priorities are:
- add a canonical CLI/batch runner for all test families;
- emit machine-readable run manifests (`json/yaml`) with seeds and parameter deltas;
- save time-series metrics (`csv/parquet`) alongside figures;
- include confidence/sensitivity runs over seed ensembles;
- standardize figure-to-scenario naming and metadata links to reports.

---

If you are using this repository for a paper or technical report, treat it as a **reproducible kinetic-simulation framework** with clear scenario structure, explicit parameterization, and extensible quantitative diagnostics.
