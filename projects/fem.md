---
layout: projects
title: Finite element methods
permalink: /projects/fem/
links:
  - label: Github Repo
    url: https://github.com/philiplukek/FEM
---

This writeup highlights the foundational principles of the **Finite Element Method (FEM)** and documents the specialized code development completed during my PhD coursework. This work involved building a custom FEM solver from the ground up, focusing on the core numerical subroutines for axial and plane stress/strain problems.

---

## 1. Introduction to Finite Element Method (FEM)

The Finite Element Method is a numerical technique used to find approximate solutions to boundary value problems for partial differential equations. It works by "discretizing" a complex, continuous geometry into a finite number of smaller, simpler shapes called **elements**.

By solving the governing equations for each individual element and "assembling" them back together, we can predict how a structure will react to external forces, heat, or vibration.

---

## 2. Mathematical Formulation

The core of FEM is the transformation of a continuous physical system into a discrete system of algebraic equations. The general equilibrium equation for a static structural problem is expressed as:

$$[K] \{u\} = \{F\}$$

Where:

* **[K]**: The Global Stiffness Matrix (representing the material and geometric properties).
* **\{u\}**: The Global Displacement Vector (the unknowns we solve for).
* **\{F\}**: The Global Force Vector (applied loads and boundary conditions).

For an individual element, the stiffness matrix k_e is derived using the principle of virtual work or the Galerkin method:

$$k_e = \int_{\Omega_e} B^T D B \, d\Omega_e$$

---

## 3. Custom Implementation: PhD Coursework

A significant portion of my doctoral training involved the development of a standalone FEM library from scratch. Unlike commercial software, these subroutines were written manually to gain a deep "under-the-hood" understanding of numerical stability and matrix assembly.

### Development Methodology

At the time of development, the code followed a **procedural architecture**, where distinct functions were authored for specific problem types. While not initially utilizing Object-Oriented Programming (OOP), this approach allowed for an granular focus on the unique physics of 1D vs. 2D domains.

### 1D Axial Problems

The 1D solver was designed for maximum flexibility in linear structural analysis:

* **Domain Agnostic:** Capable of generating and analyzing any straight-line domain.
* **Infinite Discretization:** The algorithm supports an arbitrary number of elements, allowing for convergence studies by simply increasing the element density.
* **Subroutines:** Custom functions for local stiffness calculation, global assembly, and imposition of Dirichlet boundary conditions.

---

### 2D Plane Problems

Transitioning to 2D introduced significant complexity, particularly in the relationship between geometry and discretization.

* **Quadrilateral-to-Triangular Logic:** The solver is optimized for quadrilateral domains. It employs a custom-developed meshing logic that automatically subdivides these quadrilateral design spaces into **triangular elements** (Constant Strain Triangles).
* **Custom Meshing Algorithm:** Instead of using third-party meshers, I developed a proprietary meshing routine to handle node numbering and element connectivity specifically for rectangular and skewed quadrilateral shapes.
* **Capabilities:** The 2D engine effectively solves plane stress and plane strain problems, providing accurate displacement and stress distributions.

---

## 4. Key Takeaways from Scratch Development

Building these solvers from a "blank page" provided insights that are often lost when using commercial packages:

1. **Direct Stiffness Method:** Mastery of the assembly process and the importance of bandwidth minimization.
2. **Meshing Logic:** Understanding the challenges of maintaining a consistent Jacobian and avoiding element distortion in 2D.
3. **Numerical Precision:** Dealing with the trade-offs between computational speed and the precision of the system solver.

This foundational work served as the precursor to my more advanced research in **Isogeometric Analysis (IGA)**, where the lessons learned in manual FEM meshing informed the transition to spline-based discretizations.

---