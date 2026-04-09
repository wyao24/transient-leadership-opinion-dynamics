# Results Organization

This folder stores generated outputs and is organized into:

- `figures/` — visual artifacts grouped by experiment family
  - `single-leader/`
  - `two-leader/`
  - `control-comparisons/`
  - `transient-leadership/`
  - `radical-vs-populist/`
- `experiments/` — structured run outputs (reserved for JSON/CSV/NPY manifests and logs)

## Current Status
The present commit reorganizes existing PNG outputs into thematic subfolders using best-effort mapping from filenames and script test families.

## Recommended convention for future runs
For each experiment run, store:
- parameter configuration,
- random seed,
- runtime mode,
- script/version reference,
- generated figure list,
- optional numerical summaries.

Place these under `results/experiments/<experiment-name>/<timestamp-or-tag>/`.
