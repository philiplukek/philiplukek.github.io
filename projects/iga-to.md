---
layout: projects
title: Isogeometric Topology Optimization
subtitle: A continuity-preserving framework for topology optimization using spline-based analysis
permalink: /projects/iga-to/
links:
  - label: Adaptive isogeometric topology optimization using PHT splines
    url: https://doi.org/10.1016/j.cma.2022.114993
  - label: A continuous field adaptive mesh refinement algorithm for isogeometric topology optimization using PHT-Splines
    url: https://doi.org/10.1016/j.cma.2023.116075
---

## Motivation and context

Topology optimization has become a standard computational tool for
structural design; however, most formulations rely on classical finite
element discretizations, which suffer from geometric approximation
errors and limited continuity across element boundaries.

Isogeometric analysis (IGA) offers an attractive alternative by
employing spline-based basis functions that exactly represent CAD
geometry while providing higher-order continuity. This project
investigates the integration of IGA into density-based topology
optimization frameworks.

---

## Technical contributions

The key contributions of this project include:

- Development of a spline-based topology optimization framework using
  NURBS and multi-patch geometries
- Continuity-preserving sensitivity analysis within an isogeometric
  setting
- Efficient treatment of design variables defined directly on control
  points
- Demonstration of improved convergence behavior compared to classical
  finite element approaches

---

## Methodology overview

The optimization problem is formulated as a compliance minimization
problem under a volume constraint, discretized using isogeometric
analysis. Density variables are associated with spline control points,
and material interpolation is performed using a SIMP-type approach.

Both single-patch and multi-patch geometries are considered to
demonstrate the robustness of the formulation.

---

## Representative results

Numerical examples include two-dimensional benchmark problems and
plate/shell structures, highlighting:

- Smooth material distributions
- Reduced numerical instabilities
- Improved stress field regularity due to higher continuity

(Representative figures and contour plots will be added here.)

---

## Current status

This project forms a core component of my doctoral research and has
resulted in peer-reviewed journal publications. Extensions to adaptive
refinement and phase-field formulations are currently under
investigation.
