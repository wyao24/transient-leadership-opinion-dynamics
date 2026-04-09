# Project Overview

## Research Goal
The project studies controlled opinion formation in large interacting populations using kinetic and mean-field tools. The primary objective is to understand how selective control on leader subpopulations influences collective opinion patterns, especially when social influence is mediated by a popularity/contact variable.

## Combined Modeling Ingredients

### 1. Popularity-adaptive kinetic opinion dynamics
Particles carry opinion and contact (popularity/connectivity) states. Interaction strengths and compromise mechanisms depend on these coupled variables.

### 2. Leader-follower selective control
Leaders are modeled as distinguished groups receiving control actions (opinion-targeting, contact-targeting, or both), while the broader population evolves through controlled/uncontrolled interactions.

### 3. Transient leadership perspective
Rather than static dominance, scenario design reflects time-evolving leadership influence and competitive configurations (e.g., multiple leaders with symmetric/asymmetric control intensity).

## Why this is novel in repository context
Within this repository, novelty lies in the **integration** of:
- popularity-adaptive contact-opinion coupling,
- selective mean-field control mechanisms,
- multi-scenario numerical exploration (single leader, competing leaders, extended control settings),
- exploratory radical-vs-populist analysis.

This integration is represented across scripts, notebooks, reports, and organized figure artifacts.

## Scope and Limits
This repository provides computational and documentary artifacts for the above framework, but currently does not expose a fully standardized experiment runner/CLI. Reproducibility is possible through script-level function calls and notebook workflows, with further engineering planned.
