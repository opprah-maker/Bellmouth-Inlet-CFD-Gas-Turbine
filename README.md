# Bellmouth Inlet : CFD Optimisation for a Gas Turbine

> Design and CFD optimisation of an elliptical bellmouth inlet to minimise inlet pressure
> losses and maximise mass flow rate for a gas turbine engine. Solved in ANSYS Fluent
> with the standard $k-\epsilon$ turbulence model.

[![ANSYS Fluent](https://img.shields.io/badge/ANSYS%20Fluent-CFD-FFB71B?logo=ansys&logoColor=black)]()
[![Bellmouth](https://img.shields.io/badge/Geometry-Elliptical%20inlet-blue)]()
[![Report PDF](https://img.shields.io/badge/Report-PDF-red?logo=adobe-acrobat-reader&logoColor=white)]()

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Report (PDF)](#2-report-pdf)
3. [Geometry &amp; Mesh](#3-geometry--mesh)
4. [Boundary Conditions](#4-boundary-conditions)
5. [Key Results](#5-key-results)
6. [Figure Reference &amp; Captions](#6-figure-reference--captions)
7. [How to Reproduce](#7-how-to-reproduce)
8. [Topics](#8-topics)

---

## 1. Project Overview

This repository contains the CFD study of a bellmouth (flow-conditioning) inlet for a gas
turbine engine. The objective is to:

- Minimise the total-pressure loss coefficient $\zeta = (p_{t,\infty} - p_{t,\text{exit}})/(p_{t,\infty} - p_\infty)$
- Maximise the mass flow rate $\dot{m} = \rho A V$ for a given upstream stagnation pressure
- Characterise the wall-shear, static-pressure, and velocity contours

The validation uses the **von K\&aacute;rm\&aacute;n integral boundary layer method** for
adverse pressure gradient flows.

---

## 2. Report (PDF)

| Document | File |
|---|---|
| Baseline Design : Bellmouth inlet CFD | [`reports/Baseline-Design.pdf`](reports/Baseline-Design.pdf) |

---

## 3. Geometry &amp; Mesh

| Parameter | Value |
|---|---|
| Inlet diameter | $D = 100\,\text{mm}$ |
| Wall thickness | $t = 2\,\text{mm}$ |
| Ellipse ratio | $a/b = 0.5$ |
| Inlet length | $L = 4D$ |
| Mesh elements | $\sim 1.2\,\text{M}$ (unstructured tetrahedra) |
| $y^+$ on the wall | $< 1$ (inflation layers) |

---

## 4. Boundary Conditions

| Boundary | Type | Value |
|---|---|---|
| Inlet | Mass flow inlet | $\dot{m} = 1.0\,\text{kg/s}$ |
| Outlet | Pressure outlet | $p_g = 0\,\text{Pa}$ |
| Bellmouth wall | No-slip wall | Standard wall functions |
| Symmetry plane | Symmetry | : |

---

## 5. Solver

- ANSYS Fluent, pressure-based, steady
- Standard $k-\epsilon$ turbulence model with enhanced wall treatment
- Second-order upwind discretisation
- Convergence: residuals $< 10^{-5}$

---

## 6. Key Results

| Metric | Value |
|---|---|
| Mass flow rate | $\dot{m} = 1.0\,\text{kg/s}$ |
| Total-pressure recovery | $\eta_p > 0.99$ |
| Inlet distortion (DC60) | $< 0.05$ |
| Wall shear stress (peak) | $\tau_w \approx 4.2\,\text{Pa}$ |

---

## 7. Figure Reference &amp; Captions

All 23 figures from the bellmouth inlet CFD report. Each is linked to its file in `images/`.

| Fig. | File | Description |
|---|---|---|
| 1 | [`figure-01.png`](images/figure-01.png) | Inlet geometry — elliptical bellmouth with D = 100 mm, ellipse ratio a/b = 0.5 |
| 2 | [`figure-02.jpeg`](images/figure-02.jpeg) | Inlet geometry detail — leading-edge curvature and wall thickness |
| 3 | [`figure-03.png`](images/figure-03.png) | Computational domain — inlet plenum, bellmouth, and downstream pipe |
| 4 | [`figure-04.jpeg`](images/figure-04.jpeg) | Mesh overview — unstructured tetrahedra with inflation layers on the wall |
| 5 | [`figure-05.png`](images/figure-05.png) | Mesh quality — skewness distribution (max < 0.85) |
| 6 | [`figure-06.jpeg`](images/figure-06.jpeg) | Mesh quality — orthogonal quality distribution (min > 0.15) |
| 7 | [`figure-07.png`](images/figure-07.png) | Boundary layer mesh — inflation layers near the wall with y+ < 1 |
| 8 | [`figure-08.png`](images/figure-08.png) | Mesh independence study — pressure drop vs. element count |
| 9 | [`figure-09.png`](images/figure-09.png) | Velocity contour — throughflow showing acceleration through the bellmouth |
| 10 | [`figure-10.png`](images/figure-10.png) | Static pressure contour — pressure recovery downstream of the throat |
| 11 | [`figure-11.png`](images/figure-11.png) | Total pressure contour — total-pressure loss distribution |
| 12 | [`figure-12.png`](images/figure-12.png) | Dynamic pressure contour — q = 0.5 rho V^2 distribution |
| 13 | [`figure-13.png`](images/figure-13.png) | Wall shear stress — viscous stress on the bellmouth surface |
| 14 | [`figure-14.png`](images/figure-14.png) | Velocity profile at exit — uniform profile confirming flow conditioning |
| 15 | [`figure-15.png`](images/figure-15.png) | Pressure coefficient Cp — surface distribution along the bellmouth |
| 16 | [`figure-16.png`](images/figure-16.png) | Total pressure recovery eta_p — axial distribution showing recovery |
| 17 | [`figure-17.jpeg`](images/figure-17.jpeg) | Velocity vector plot — secondary flow visualisation |
| 18 | [`figure-18.png`](images/figure-18.png) | Streamlines — 3D streamlines coloured by velocity magnitude |
| 19 | [`figure-19.jpg`](images/figure-19.jpg) | Validation — CFD vs. von Karman integral boundary layer method |
| 20 | [`figure-20.jpg`](images/figure-20.jpg) | Validation — pressure drop vs. mass flow rate comparison |
| 21 | [`figure-21.jpg`](images/figure-21.jpg) | Validation — discharge coefficient Cd vs. Reynolds number |
| 22 | [`figure-22.jpg`](images/figure-22.jpg) | Contour plot — static pressure on the symmetry plane |
| 23 | [`figure-23.jpg`](images/figure-23.jpg) | Contour plot — velocity magnitude on the symmetry plane |

---

## 8. How to Run

This work was performed inside ANSYS Workbench. To reproduce:

1. Reconstruct the bellmouth geometry in **ANSYS DesignModeler** (an elliptical contour
   with $a/b = 0.5$ revolved around the centreline).
2. Generate the mesh in **ANSYS Meshing** with inflation layers on the wall such that
   $y^+ < 1$ for the expected $Re$.
3. Open **ANSYS Fluent**:
   - Set the inlet as a mass flow inlet at $\dot{m} = 1.0\,\text{kg/s}$.
   - Enable the standard $k-\epsilon$ model with enhanced wall treatment.
   - Use second-order upwind for momentum, $k$, and $\epsilon$.
   - Run to convergence with residuals $< 10^{-5}$.
4. Post-process the contours in **CFD-Post** to extract the static, dynamic, and total
   pressure fields, the wall-shear stress, and the velocity magnitude on the symmetry plane.

The original ANSYS Workbench project files (`.wbpj`, `.agdb`, `.msh`, `.cas.h5`, `.set`,
`.mshdb`) are very large (several GB) and are not stored in this repository. The five
CFD contour plots that document the simulation outputs are in `images/`.

---

## 9. Topics

`cfd` `ansys-fluent` `bellmouth-inlet` `gas-turbine` `aerospace-engineering` `aerodynamics`
`fluid-dynamics` `heat-transfer` `von-karman` `boundary-layer` `turbomachinery`
`engineering-simulation`
