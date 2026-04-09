# Inventory

## Important Files Found

- `src/albi2025_reproduction.py`
- `src/albi2025_reproduction_v2.py`
- `notebooks/Albi-Edits.ipynb`
- `notebooks/radical_vs_populist.ipynb`
- `notebooks/transient_leadership_v2.ipynb`
- `reports/Kinetic Model - Ongoing.pdf`
- `reports/Opinion Dynamics - Transient Leader-Follower in Control (Math 266E).pdf`
- `docs/Opinion Dynamics - Transient Leader-Follower in Control (Math 266E).pptx`
- `figures/rad_pop_main.png`
- `figures/rad_pop_w.png`
- `figures/test1_means.png`
- `figures/test1_snapshots.png`
- `figures/test2_snapshots.png`
- `figures/test3_config1.png`
- `figures/test3_config2.png`
- `figures/test3_config3.png`

## Files Moved

- Top-level Python scripts moved to `src/`
- Top-level notebooks moved to `notebooks/`
- Project/report PDFs moved to `reports/`
- Slide deck moved to `docs/`
- PNG outputs moved to `figures/`
- Likely reference papers and templates moved to `archive/`

## Files Left Ambiguous

- `archive/Template_Paper.pdf`: could be a draft built from a template or a template-derived export; kept conservatively
- `src/albi2025_reproduction.py` and `src/albi2025_reproduction_v2.py`: both retained pending a decision on the canonical version
- `notebooks/Albi-Edits.ipynb`: appears to compare revised and original code, but its long-term role should be clarified

## Possible Duplicates Or Redundant Artifacts

- `src/albi2025_reproduction.py` and `src/albi2025_reproduction_v2.py` appear closely related
- `reports/Opinion Dynamics - Transient Leader-Follower in Control (Math 266E).pdf` and `docs/Opinion Dynamics - Transient Leader-Follower in Control (Math 266E).pptx` cover the same project topic in different formats
- `archive/Control of kinetic opinion dynamics in popularity-adaptive social networks.pdf` and `archive/Mean-Field Selective Optimal Control via Transient Leadership.pdf` are likely external reference papers rather than primary project outputs

## Recommended Next Cleanup Steps

- Decide which script and notebook versions are canonical and archive superseded variants
- Add dependency and execution instructions for the Python and notebook workflows
- Review whether archived PDFs should remain in the public repository
- Add lightweight provenance notes for generated figures
- Consider a later pass to separate reproducible source outputs from one-off exploratory artifacts
