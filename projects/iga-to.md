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

## 1. What is Structural Optimization?

Structural optimization is a mathematical approach used to find the best distribution of material within a defined space to sustain loads efficiently. It is generally categorized into three distinct levels of complexity:

| Type | What is Optimized? | Flexibility |
| --- | --- | --- |
| **Sizing Optimization** | Dimensions of existing components (e.g., thickness of a beam, diameter of a bolt). | Low |
| **Shape Optimization** | The external contours or boundaries of a predefined geometry. | Medium |
| **Topology Optimization** | The layout, connectivity, and number of holes within the design space. | **High** |

---

## 2. Topology Optimization & SIMP

**Topology Optimization (TO)** is the most powerful of the three. It starts with a solid block of "virtual material" and mathematically "chisels" away the unnecessary parts.

The most common approach is the **SIMP (Solid Isotropic Material with Penalization)** method. In SIMP, we assign a density variable $\rho$ to every point in the domain:

* $\rho = 1$: Solid material.
* $\rho = 0$: Void (empty space).
* $0 < \rho < 1$: Intermediate "gray" material (penalized to drive it toward 0 or 1).

---

## 3. The Traditional Approach: FEM-Based TO

In traditional frameworks, the design domain is discretized using a **Finite Element Method (FEM)** mesh. The densities are typically defined **element-wise**, meaning each square or cube in the mesh has one single density value.

### Issues with FEM-Based Optimization:

1. **Checkerboarding:** Solutions often result in alternating solid/void cells that are physically impossible to manufacture.
2. **Mesh Dependency:** Refining the mesh changes the final shape, meaning the solution isn't objective.
3. **Jagged Boundaries:** The final design has "pixelated" edges, requiring very fine meshes and  manual cleanup in CAD software before manufacturing.
<!-- 4. **Non-Smooth Sensitivities:** Because elements are only C^0 continuous (they only touch at the corners), the stress and strain calculations at boundaries are less accurate. -->

---

## 4. Isogeometric topology optimization (ITO)

**Isogeometric Analysis (IGA)** replaces the jagged elements of FEM with the smooth, high-order curves used in CAD: **NURBS (Non-Uniform Rational B-Splines)**. Instead of assigning densities to elements, ITO formulates the framework **directly on spline-based discretizations**.

* **Spline Representation:** The optimized geometry is defined by control points. The density is no longer a "staircase" of blocks but a **Continuous Density Function (CDF)**.
* **Continuous Density:** Because NURBS basis functions are C^k continuous (smoothly changing), the material density varies smoothly across the design domain. This naturally eliminates checkerboarding without needing complex artificial filters.
* **Geometric Exactness:** The boundaries are represented by smooth splines from the start. What you see in the optimization result is exactly what you can send to a CNC machine or 3D printer with minimal post-processing.

---

## 5. Methodology

In ITO, the material density field $\rho(\xi, \eta)$ is approximated using the same basis functions used for the structural analysis. This ensures a "continuous" transition of material:

$$\mathbb{X}(\xi, \eta) = \sum_{i=1}^{n} \sum_{j=1}^{m} R_{i,j}(\xi, \eta) \cdot \rho_{i,j}$$

#### Where:
* $\mathbb{X}(\xi, \eta)$: The continuous density at any point in the parametric space.
* $R_{i,j}(\xi, \eta)$: The NURBS basis functions (ensuring $C^k$ continuity).
* $\rho_{i,j}$: The **design variables** (densities assigned to each control point), bounded such that $0 \le d_{i,j} \le 1$.

## 6. Representative results

### Continuous topology optimization using IGA
<div style="text-align: center;">
<img src="/assets/projects/ito_1.png" alt="" style="width: 600px; height: auto;">
</div>
In comparison with disrete-density FEM, continuous density function with IGA provides a smooth, manufacturable design for the same mesh.

### Topology optimization of complex multi-patch structures with non-design domains 

<div style="text-align: center;">
<img src="/assets/projects/ito_2.png" alt="" style="width: 600px; height: auto;">
</div>

### Optimization of complex 3D domains

<div style="text-align: center;">
<img src="/assets/projects/ito.gif" alt="" style="width: 400px; height: auto;">
</div>

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

<!-- 
### Penalized Young's Modulus (SIMP-IGA)
The effective stiffness at any point is governed by the penalization power $p$:

$$E(\rho) = E_{min} + \rho^p (E_0 - E_{min})$$

This formulation allows the optimizer to move the "control points" of the density field, resulting in smooth, high-performance organic shapes that are inherently ready for manufacturing. -->



<!-- ## Motivation and context

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
investigation. -->
