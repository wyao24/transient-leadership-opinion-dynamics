# Methods

## 1. Kinetic Modeling Viewpoint
The project models opinion dynamics through binary interactions among particles/agents. Each interaction updates state variables (opinion and contacts/popularity) with deterministic drift and stochastic perturbation components.

At scale, this induces a kinetic equation for the joint density over state space, with Boltzmann-type interaction structure.

## 2. Mean-Field and Fokker–Planck Interpretation
The scripts and reports are aligned with the standard asymptotic pipeline:
- microscopic binary interaction law,
- kinetic Boltzmann-type formulation,
- quasi-invariant/small-interaction scaling,
- drift-diffusion (Fokker–Planck-type) approximation for macroscopic analysis.

The code primarily implements the particle side, while PDE interpretation is documented in report materials.

## 3. Control Mechanisms
Control enters in two channels:
- **Opinion control**: steering selected leader-group opinions toward prescribed targets.
- **Contact control**: modifying contact dynamics for selected groups, affecting influence structure.

Scenarios combine these controls in no-control, single-channel, and joint-control settings.

## 4. Numerical Simulation Approach

### Nanbu-like particle scheme
The primary script uses a Monte Carlo binary-interaction loop where particle pairs are sampled and updated per time step. This is a standard kinetic simulation strategy for high-dimensional interacting systems.

### Density diagnostics
Joint and marginal densities are reconstructed from particle samples using histograms, with optional Gaussian smoothing for visualization stability.

### Scenario-based experimentation
Experiments are encoded as scenario lists with group-specific control activation, enabling side-by-side comparison under shared initial conditions.

## 5. Practical Runtime Modes
The script supports runtime presets (`fast`, `balanced`, `paper`) to trade off computational cost and fidelity. This is useful for exploratory development vs. closer reproduction runs.
