# Experiments

## Overview
Experiment families are defined in `src/albi2025_reproduction_v2.py` as `run_test1`, `run_test2`, and `run_test3`, each with scenario variants and associated plotting utilities.

## Test 1 — Single-leader control comparison

### Purpose
Assess baseline and controlled dynamics in a single-leader setting.

### Scenarios
- (a) No control
- (b) Contact control on leaders
- (c) Opinion control on leaders
- (d) Joint contact + opinion control on leaders

### Typical outputs
- Joint density snapshots in opinion-contact space
- Marginal density panels
- Mean contact and mean opinion trajectories

### Related figures in repo
- `results/figures/single-leader/test1_snapshots.png`
- `results/figures/control-comparisons/test1_means.png`

## Test 2 — Two-leader competition

### Purpose
Compare symmetric vs non-symmetric opinion control in a competing two-leader setting.

### Scenarios
- (a) No control
- (b) Symmetric opinion control
- (c) Non-symmetric opinion control

### Typical outputs
- Joint density snapshots by scenario and time
- Marginal density panels

### Related figures in repo
- `results/figures/two-leader/test2_snapshots.png`

## Test 3 — Extended multi-control configurations

### Purpose
Explore richer control combinations on two leader groups over longer horizons.

### Scenarios
- (a) Opinion control on groups A and B
- (b) Opinion control on A/B plus contact control on A
- (c) Opinion + contact controls on both A and B

### Typical outputs
- Time snapshots of joint densities at extended horizons
- Marginal structures under each control configuration

### Related figures in repo
- `results/figures/transient-leadership/test3_config1.png`
- `results/figures/transient-leadership/test3_config2.png`
- `results/figures/transient-leadership/test3_config3.png`

## Radical vs Populist exploratory analysis

### Artifacts present
- Notebook: `notebooks/radical_vs_populist.ipynb`
- Figures: `results/figures/radical-vs-populist/rad_pop_main.png`, `results/figures/radical-vs-populist/rad_pop_w.png`

### Notes
This appears exploratory and complementary to the scripted test families above.

## Reproducibility Notes
The repository currently exposes function-level experiment entrypoints rather than a standardized CLI/script orchestration. A future improvement is to add reproducible batch-run scripts writing structured outputs under `results/experiments/`.
