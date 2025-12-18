---
layout: projects
title: Adaptive Mesh Refinement
permalink: /projects/iga-amr/
links:
  - label: Paper 1 (2022) - CMAME
    url: https://doi.org/10.1016/j.cma.2022.114993
  - label: Paper 2 (2023) - CMAME
    url: https://doi.org/10.1016/j.cma.2023.116075
  - label: Paper 3 (2024) - CMAME
    url: https://doi.org/10.1016/j.cma.2024.117132
  - label: Paper 4 (2025) - Engineering with Computers
    url: https://doi.org/10.1007/s00366-025-02133-z
---

## 1. The Need for Adaptivity

Isogeometric Analysis (IGA) aims to unify Computer-Aided Design (CAD) and Finite Element Analysis (FEA) by using the same spline-based basis functions (like NURBS) for both geometry and simulation. In any mesh-based method such as FEA/IGA, accuracy is directly linked to the density of the mesh. High-stress areas, material interfaces, or complex topological boundaries require a very **fine mesh**. However, applying a fine mesh globally across the entire design domain leads to:

* **Prohibitive Computational Costs:** Massive increase in memory and CPU time.
* **Redundancy:** Wasting resources on regions with low gradients or simple physics.

**Adaptive Mesh Refinement (AMR)** solves this by dynamically identifying regions that require higher resolution and refining the mesh only in those specific areas.

---

## 2. The NURBS Bottleneck: Adaptivity in IGA

Standard IGA relies on **NURBS (Non-Uniform Rational B-Splines)**. While NURBS are the industry standard for CAD, they possess a major flaw for simulation: **Tensor Product Structure**.

In a tensor product mesh, if you want to add a single knot (refinement) to increase detail in one corner, that knot must propagate across the **entire row or column** of the domain. This results in "global" refinement when only "local" refinement was intended.

<div style="text-align: center;">
<img src="/assets/projects/refinement.png" alt="" style="width: 600px; height: auto;">
</div>
---

## 3. PHT-Splines: The Local Refinement Solution

To enable true AMR, we must move toward a different class of splines. **PHT-Splines (Polynomial Splines over Hierarchical T-meshes)** are specifically designed for this purpose.

### Key Features of PHT-Splines:

* **Hierarchical Structure:** They utilize a "tree-based" data structure (similar to Quadtrees in 2D or Octrees in 3D).
* **Local Refinement:** You can refine a single element without affecting the rest of the mesh.
* **Nested Spaces:** Each level of refinement is mathematically nested within the previous one, ensuring stable convergence.

<div style="text-align: center;">
<img src="/assets/projects/quadtree.jpg" alt="" style="width: 600px; height: auto;">
<p style="font-style: italic; color: #555; margin-top: 8px;">
    Tree structure of PHT-Splines
    </p>
</div>

<div style="text-align: center;">
<img src="/assets/projects/pht_basis.jpg" alt="" style="width: 600px; height: auto;">
<p style="font-style: italic; color: #555; margin-top: 8px;">
    Local refinement in PHT-Splines
    </p>
</div>

---

## 4. The GIFT Framework: Bridging CAD and PHT

A major conflict arises here: **NURBS** are essential for maintaining CAD consistency, but **PHT-splines** are necessary for efficient refinement. Simply switching to PHT-splines ruins the "Isogeometric" promise of using the original CAD geometry.

This is solved by the **GIFT Framework (Geometry-Independent Field approximaTion)**.

### How GIFT Works:

1. **Geometry Representation:** The CAD geometry remains defined by its original **NURBS** description (ensuring perfect geometric accuracy).
2. **Field Approximation:** The solution field (displacements, densities, etc.) is approximated using **PHT-splines**.
3. **Independence:** Because the analysis field is mathematically independent of the geometric description, we can refine the PHT-mesh adaptively while the underlying CAD shape remains unchanged.

<div style="text-align: center;">
<img src="/assets/projects/gift.jpg" alt="" style="width: 600px; height: auto;">
<p style="font-style: italic; color: #555; margin-top: 8px;">
    Idea of the GIFT framework
    </p>
</div>
---

## 5. Performance in Topology Optimization

The application of Adaptive IGA using PHT-splines and the GIFT framework has shown transformative results in **Topology Optimization** problems.During the optimization process, the material boundaries shift. AMR allows the mesh to "follow" the evolving shape, refining only at the material interfaces where the densities are intermediate or the gradient is highest.

### Proven Benefits:

* **Significant Reduction in Degrees of Freedom (DOF):** Achieve the same accuracy as a fine global mesh with up to 80–90% fewer equations.
* **Reduced CPU Time:** Faster solver iterations due to smaller system matrices.
* **Memory Efficiency:** Drastically lower memory footprint, allowing for higher-resolution designs on standard hardware.
* **Optimized Element Count:** Only placing elements where they contribute to the structural integrity of the design.

---

## 6. Representative results

<div style="text-align: center;">
<img src="/assets/projects/amr3.jpg" alt="" style="width: 600px; height: auto;">
<p style="font-style: italic; color: #555; margin-top: 8px;">
    Adaptively refined mesh in a 2D plane stress problem
    </p>
</div>

<div style="text-align: center;">
<img src="/assets/projects/amr4.jpg" alt="" style="width: 600px; height: auto;">
<p style="font-style: italic; color: #555; margin-top: 8px;">
    Adaptively refined mesh in a 3D domain
    </p>
</div>

<div style="text-align: center;">
<img src="/assets/projects/amr2.jpg" alt="" style="width: 500px; height: auto;">
<p style="font-style: italic; color: #555; margin-top: 8px;">
    Reduction in CPU time compared to global refinement   
    </p>
</div>

<div style="text-align: center;">
<img src="/assets/projects/amr1.jpg" alt="" style="width: 600px; height: auto;">
<p style="font-style: italic; color: #555; margin-top: 8px;">
    Reduction in all computational parameters in comparison to global refinement   
    </p>
</div>


## Key Contributions
- Adaptive refinement strategies tailored for optimization problems  
- Coupling of AMR with sensitivity analysis  
- Reduced computational effort without compromising design quality  

<!-- ## Overview
This project explores adaptive refinement strategies in structural optimization to improve computational efficiency while retaining solution accuracy.

## Motivation
Uniform refinement in optimization leads to excessive computational cost. Adaptive strategies allow refinement to be focused in regions of interest such as material boundaries and high-gradient zones.

## Methodology
Adaptive mesh refinement is driven by error indicators and optimization sensitivities. The framework is implemented within an isogeometric setting to preserve solution smoothness.



## Representative Results
Adaptive optimization examples show significant reductions in degrees of freedom compared to uniformly refined models.

## Related Publications / Material
Supporting publications and numerical studies will be listed. -->
