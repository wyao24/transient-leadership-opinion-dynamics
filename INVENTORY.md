# Repository Inventory and Audit

## 1) Code and Numerical Components

### Core simulation code
- `src/albi2025_reproduction_v2.py`
  - Comprehensive reproduction script implementing parameter sets, runtime presets, scenario control definitions, and three test suites.
  - Contains Nanbu-like particle interaction loop, density estimators, and figure-construction functions.

### Archived/superseded code
- `archive/src/albi2025_reproduction.py`
  - Earlier closely related version retained conservatively.
  - Archived to keep one primary active implementation in `src/` while preserving provenance.

### Numerical methods explicitly present in code
- Particle-based stochastic binary interaction simulation.
- Histogram-based joint/marginal density estimation with optional Gaussian smoothing.
- Scenario-wise controlled dynamics for contact and opinion channels.

## 2) Reports, Slides, and References

### Project outputs
- `reports/Kinetic Model - Ongoing.pdf`
- `reports/Opinion Dynamics - Transient Leader-Follower in Control (Math 266E).pdf`
- `reports/Opinion Dynamics - Transient Leader-Follower in Control (Math 266E).pptx`

### Archived references/templates
- `archive/Control of kinetic opinion dynamics in popularity-adaptive social networks.pdf`
- `archive/Mean-Field Selective Optimal Control via Transient Leadership.pdf`
- `archive/Template_Paper.pdf`
- `archive/Template_for_SIAM_Journals.pdf`

## 3) Figures and Outputs

Organized under `results/figures/`:
- `single-leader/`: single-leader snapshots.
- `two-leader/`: two-leader competition snapshots.
- `control-comparisons/`: mean trajectories/control comparison plots.
- `transient-leadership/`: extended scenario configurations.
- `radical-vs-populist/`: exploratory radical/populist figures.

`results/experiments/` is prepared for structured experiment outputs (metadata, arrays, logs).

## 4) Notebooks
- `notebooks/Albi-Edits.ipynb`
- `notebooks/transient_leadership_v2.ipynb`
- `notebooks/radical_vs_populist.ipynb`

These appear to be exploratory/reproduction notebooks complementing the scripted implementation.

## 5) Inferred Project Structure (from files)

### Core model direction
A kinetic opinion dynamics framework with coupled opinion/contact variables, leader-follower group structure, and selective control mechanisms.

### Simulation families available
- Test 1: single-leader control comparisons.
- Test 2: two-leader controlled competition (symmetric vs asymmetric).
- Test 3: extended multi-control leader scenarios.
- Separate radical-vs-populist exploratory analysis in notebook/figures.

## 6) Ambiguous Items Requiring Human Review
- Precise canonical status of each notebook (analysis vs production reproduction).
- Whether `Template_Paper.pdf` should remain versioned in-repo.
- Whether additional raw outputs exist externally and should be imported into `results/experiments/`.

## 7) Organization Decisions Made
- Kept one active simulation script in `src/` and archived the close variant.
- Moved slide deck to `reports/` alongside PDFs for publication artifacts.
- Re-homed top-level figure outputs into `results/figures/` experiment-group folders.
- Did not delete ambiguous artifacts; used `archive/` when uncertain.
