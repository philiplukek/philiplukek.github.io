---
layout: projects
title: FALCON v1.0.0 - GUI-based Framework for Isogeometric Analysis
permalink: /projects/gui-iga/
links:
  - label: FALCON - Avkalan Labs 
    url: https://www.philipluke.com/iga/
---

**FALCON** was developed as a tool for the **Indian Space Research Organisation (ISRO - VSSC)**, in strategic collaboration with **Avkalan Labs**.

The primary objective of FALCON v 1.0.0 is to bridge the gap between high-fidelity CAD modeling and complex numerical simulations, providing a seamless workflow for aerospace and structural engineers.

---

## 1. Motivation
While IGA offers superior accuracy by using exact CAD geometry, its practical application has historically been limited by the complexity of script-based workflows. FALCON addresses this by:

* Removing the need for manual coding of analysis scripts for end-users.
* Providing an intuitive, "what-you-see-is-what-you-get" (WYSIWYG) environment.
* Enabling engineers to focus on structural behavior rather than mathematical implementation.

---

## 2. Implementation & Backend Development

The strength of FALCON lies in its **modular subroutine architecture**. Unlike standard black-box FEA tools, FALCON is built on a custom-coded Python backend that manages the heavy mathematical lifting of spline theory.

### Core Subroutine Development

* **Spline Engine:** Custom subroutines were developed to handle NURBS basis function evaluation, knot insertion, and degree elevation across multiple dimensions.
* **Integration Modules:** Specialized Gauss quadrature subroutines ensure precise numerical integration over the physical domain, maintaining the "exact geometry" advantage of IGA.
* **Assembly Logic:** The framework uses an optimized global stiffness matrix assembly routine that accounts for the high-order continuity (C^p-1) inherent in splines.
* **Python Integration:** The backend is implemented in Python, utilizing libraries like NumPy and SciPy for high-performance linear algebra, while the frontend is built using robust GUI libraries to ensure cross-platform stability.

---

## 3. Software Capabilities

FALCON v1.0.0 is designed for versatility, supporting a wide range of structural configurations and analysis types.

### Modeling Domains

* **2D Analysis:** Plane stress and plane strain configurations.
* **3D Analysis:** Solid modeling for complex aerospace components.
* **Plate Modeling:** High-order continuity in IGA makes it exceptionally efficient for thin-walled structures, avoiding the "locking" issues found in traditional FEA.

### Analysis Modules

* **Linear Static Analysis:** For predicting displacements and stresses under constant loads.

<video controls style="display: block; margin: 0 auto; width: 80%;">
  <source src="/assets/projects/falcon.mp4" type="video/mp4">
</video>

* **Eigenvalue Analysis:** To determine natural frequencies and mode shapes, ensuring structural stability during launch conditions.

<video controls style="display: block; margin: 0 auto; width: 80%;">
  <source src="/assets/projects/falcon2.mp4" type="video/mp4">
</video>

---

## 4. The GUI Workflow

The FALCON interface is divided into three functional zones: Pre-processing, Solver, and Post-processing.

### Pre-processing & Visualization

Users can visually define the simulation environment:

* **NURBS Geometry:** Import or create geometries directly within the interface.
* **Visual BCs & Loading:** Boundary conditions (fixed supports, rollers) and loads (point loads, pressures) are applied via a mouse-driven interface directly on the spline patches.

### Post-processing

Results are rendered in a dedicated visualizer that supports:

* **Displacement Contours:** High-resolution mapping of structural deformation.
* **Mode Shapes:** For eigenvalue analysis, users can animate natural frequency vibrations.
* **Stress Distributions:** Visualizing Von Mises and principal stresses across the exact NURBS surface.

---

## 6. Key Contributions

* **Early Implementation:** One of the few GUI-based IGA frameworks developed specifically for the Indian aerospace sector.
* **CAD-Analysis Unification:** Eliminates the "meshing" phase by performing analysis directly on the geometry.
* **Research & Teaching:** A modular architecture that allows for the easy addition of new subroutines (e.g., non-linear analysis or thermal modules).

---



<!-- ## Overview
This project involves the development of a standalone graphical user interface (GUI) for isogeometric analysis, aimed at bridging the gap between CAD-based geometry modeling and numerical simulation.

## Motivation
Despite the advantages of IGA, its adoption in practice is often limited by the lack of accessible software tools. This project addresses this gap by providing an intuitive GUI-driven environment for geometry creation, analysis setup, and result visualization.

## Methodology
The framework integrates spline-based geometry modeling, isogeometric meshing, boundary condition specification, and solver modules within a unified GUI. The backend numerical engine is implemented in Python, ensuring modularity and extensibility.

## Key Contributions
- One of the early GUI-based implementations of isogeometric analysis  
- Seamless integration of geometry, analysis, and post-processing  
- Modular architecture suitable for research and teaching applications  

## Representative Results
The framework has been validated against benchmark problems in linear static and eigenvalue analysis.

## Related Publications / Material
User manuals, demonstrations, and related publications will be provided. -->
