# Transient Leadership and Popularity-Adaptive Kinetic Opinion Dynamics

## Overview
This repository collects code and artifacts for kinetic/mean-field opinion dynamics with selective control. The focus is on two interacting mechanisms:
1. **Popularity-adaptive opinion dynamics**, where interaction intensity depends on social connectivity/contact variables.
2. **Transient leadership control**, where influence and control actions act on leader subsets and can be compared across control regimes.

The project is positioned as applied mathematics and computational modeling (kinetic equations, mean-field limits, Monte Carlo particle schemes), not as a machine-learning benchmark.

## Modeling Framework
At a high level, the implemented workflow is:
- **Microscopic agent/particle system**: each particle has at least opinion and contact variables, with follower/leader group labels.
- **Kinetic (Boltzmann-type) interactions**: binary interactions define compromise and contact updates, with stochastic perturbations.
- **Mean-field interpretation**: repeated binary interactions approximate the evolution of a density over opinion-contact space.
- **Fokker–Planck regime (conceptual/analytical link)**: small-interaction asymptotics motivate diffusion-drift PDE descriptions referenced by project materials.
- **Leader–follower control structure**: controls can be activated on selected groups for contact and/or opinion channels.
- **Transient leadership interpretation**: scenario families in the code represent changing influence structures and controlled competition between leadership groups.

## Numerical Methods
The main script (`src/albi2025_reproduction_v2.py`) implements:
- a **Nanbu-like asymptotic Monte Carlo particle scheme** for binary interactions;
- scenario-based controls (`no control`, `contact`, `opinion`, `joint` depending on test);
- histogram-based approximations of joint and marginal densities;
- figure reproduction utilities for test families corresponding to paper-style experiments.

The code includes runtime presets (`fast`, `balanced`, `paper`) and supports stochastic simulations with configurable seeds.

## Experiments
The repository currently supports the following experiment families (based on code + stored figures):
- **Single-leader control comparison (Test 1)**:
  - no control,
  - contact-only control,
  - opinion-only control,
  - joint contact + opinion control.
- **Two-leader competition (Test 2)**:
  - no control,
  - symmetric opinion control,
  - non-symmetric opinion control.
- **Extended multi-scenario leader control (Test 3)**:
  - opinion control on both leader groups,
  - mixed opinion/contact control,
  - joint controls on both groups.
- **Radical vs populist exploratory study**: represented by dedicated notebook and figures.

Echo-chamber behavior and fragmentation/concentration patterns are discussed qualitatively in notebooks/figures; exact quantitative claims are intentionally avoided here unless explicitly documented in source reports.

## Repository Structure
- `src/` — primary simulation and reproduction code.
- `notebooks/` — exploratory notebooks and iterative analysis artifacts.
- `reports/` — project PDFs and presentation slides.
- `docs/` — structured project documentation (overview, methods, experiments).
- `results/figures/` — generated visual outputs grouped by experiment family.
- `results/experiments/` — reserved for structured run outputs/metadata.
- `data/` — placeholder for external inputs (currently empty by design).
- `archive/` — conservative storage for references, templates, and superseded scripts.
- `INVENTORY.md` — audit and file-level curation notes.

## Results Summary (Qualitative)
From the currently tracked outputs and script scenarios:
- controlled scenarios generally alter convergence/dispersion behavior relative to uncontrolled baselines;
- contact-control and opinion-control channels exhibit distinct effects on trajectory and cluster structure;
- multi-leader scenarios show competition effects sensitive to control symmetry;
- radical/populist exploratory outputs indicate a tradeoff between broad reach and directional influence.

These are qualitative repository-level observations; consult the reports and source scripts for formal interpretation.

## Reproducibility
Current best-effort workflow:
1. Create a Python environment and install `requirements.txt`.
2. Run experiments by importing `src/albi2025_reproduction_v2.py` and invoking `run_test1`, `run_test2`, `run_test3`.
3. Build figures with `plot_test1_all`, `plot_test2_all`, `plot_test3_all`.
4. Save generated outputs under `results/experiments/` and `results/figures/`.

**Status note:** a single canonical CLI entrypoint is not yet defined. See TODOs below.

## Next Steps
- [ ] Add explicit runnable entrypoints (e.g., `python -m` scripts) for each test family.
- [ ] Add parameter/config files to avoid in-code scenario editing.
- [ ] Add experiment manifests (seed, mode, runtime, commit hash) in `results/experiments/`.
- [ ] Improve figure naming/metadata for direct mapping to report figures.
- [ ] Add a short parameter glossary (symbols, units, and default values).
