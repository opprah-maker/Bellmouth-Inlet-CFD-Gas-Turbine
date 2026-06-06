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
8. [3D Gaussian Splat Visualisations](#8-3d-gaussian-splat-visualisations)
9. [Topics](#9-topics)

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

| Fig. | Preview | Description |
|---|---|---|
| 1 | <a href="images/figure-01.png"><img src="images/figure-01.png" width="120" alt="Figure 1"></a> | Inlet geometry — elliptical bellmouth with D = 100 mm, ellipse ratio a/b = 0.5 |
| 2 | <a href="images/figure-02.jpeg"><img src="images/figure-02.jpeg" width="120" alt="Figure 2"></a> | Inlet geometry detail — leading-edge curvature and wall thickness |
| 3 | <a href="images/figure-03.png"><img src="images/figure-03.png" width="120" alt="Figure 3"></a> | Computational domain — inlet plenum, bellmouth, and downstream pipe |
| 4 | <a href="images/figure-04.jpeg"><img src="images/figure-04.jpeg" width="120" alt="Figure 4"></a> | Mesh overview — unstructured tetrahedra with inflation layers on the wall |
| 5 | <a href="images/figure-05.png"><img src="images/figure-05.png" width="120" alt="Figure 5"></a> | Mesh quality — skewness distribution (max < 0.85) |
| 6 | <a href="images/figure-06.jpeg"><img src="images/figure-06.jpeg" width="120" alt="Figure 6"></a> | Mesh quality — orthogonal quality distribution (min > 0.15) |
| 7 | <a href="images/figure-07.png"><img src="images/figure-07.png" width="120" alt="Figure 7"></a> | Boundary layer mesh — inflation layers near the wall with y+ < 1 |
| 8 | <a href="images/figure-08.png"><img src="images/figure-08.png" width="120" alt="Figure 8"></a> | Mesh independence study — pressure drop vs. element count |
| 9 | <a href="images/figure-09.png"><img src="images/figure-09.png" width="120" alt="Figure 9"></a> | Velocity contour — throughflow showing acceleration through the bellmouth |
| 10 | <a href="images/figure-10.png"><img src="images/figure-10.png" width="120" alt="Figure 10"></a> | Static pressure contour — pressure recovery downstream of the throat |
| 11 | <a href="images/figure-11.png"><img src="images/figure-11.png" width="120" alt="Figure 11"></a> | Total pressure contour — total-pressure loss distribution |
| 12 | <a href="images/figure-12.png"><img src="images/figure-12.png" width="120" alt="Figure 12"></a> | Dynamic pressure contour — q = 0.5 rho V^2 distribution |
| 13 | <a href="images/figure-13.png"><img src="images/figure-13.png" width="120" alt="Figure 13"></a> | Wall shear stress — viscous stress on the bellmouth surface |
| 14 | <a href="images/figure-14.png"><img src="images/figure-14.png" width="120" alt="Figure 14"></a> | Velocity profile at exit — uniform profile confirming flow conditioning |
| 15 | <a href="images/figure-15.png"><img src="images/figure-15.png" width="120" alt="Figure 15"></a> | Pressure coefficient Cp — surface distribution along the bellmouth |
| 16 | <a href="images/figure-16.png"><img src="images/figure-16.png" width="120" alt="Figure 16"></a> | Total pressure recovery eta_p — axial distribution showing recovery |
| 17 | <a href="images/figure-17.jpeg"><img src="images/figure-17.jpeg" width="120" alt="Figure 17"></a> | Velocity vector plot — secondary flow visualisation |
| 18 | <a href="images/figure-18.png"><img src="images/figure-18.png" width="120" alt="Figure 18"></a> | Streamlines — 3D streamlines coloured by velocity magnitude |
| 19 | <a href="images/figure-19.jpg"><img src="images/figure-19.jpg" width="120" alt="Figure 19"></a> | Validation — CFD vs. von Karman integral boundary layer method |
| 20 | <a href="images/figure-20.jpg"><img src="images/figure-20.jpg" width="120" alt="Figure 20"></a> | Validation — pressure drop vs. mass flow rate comparison |
| 21 | <a href="images/figure-21.jpg"><img src="images/figure-21.jpg" width="120" alt="Figure 21"></a> | Validation — discharge coefficient Cd vs. Reynolds number |
| 22 | <a href="images/figure-22.jpg"><img src="images/figure-22.jpg" width="120" alt="Figure 22"></a> | Contour plot — static pressure on the symmetry plane |
| 23 | <a href="images/figure-23.jpg"><img src="images/figure-23.jpg" width="120" alt="Figure 23"></a> | Contour plot — velocity magnitude on the symmetry plane |

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

## 8. 3D Gaussian Splat Visualisations

Four figures from this project were also reconstructed as interactive 3D Gaussian splat previews using TripoSR (stabilityai/TripoSR, CPU inference) plus a custom mesh-to-splat converter. The splats contain about 100 000 surface samples each, with marching-cubes resolution 192. Drag to orbit, scroll to zoom.

### 8.1 Inlet mesh layout (from figure 3)

<iframe src="https://opprah-maker.github.io/splat/?s=bell_03" width="100%" height="500" style="border:1px solid #ddd;border-radius:8px;" loading="lazy" title="3D Gaussian Splat: bellmouth inlet mesh"></iframe>

[View in full screen](https://opprah-maker.github.io/splat/?s=bell_03)

### 8.2 Static pressure field (from figure 8)

<iframe src="https://opprah-maker.github.io/splat/?s=bell_08" width="100%" height="500" style="border:1px solid #ddd;border-radius:8px;" loading="lazy" title="3D Gaussian Splat: bellmouth pressure field"></iframe>

[View in full screen](https://opprah-maker.github.io/splat/?s=bell_08)

### 8.3 Lip-region mesh refinement (from figure 2)

<iframe src="https://opprah-maker.github.io/splat/?s=bell_02" width="100%" height="500" style="border:1px solid #ddd;border-radius:8px;" loading="lazy" title="3D Gaussian Splat: bellmouth mesh refinement"></iframe>

[View in full screen](https://opprah-maker.github.io/splat/?s=bell_02)

### 8.4 Wall shear stress (from figure 6)

<iframe src="https://opprah-maker.github.io/splat/?s=bell_06" width="100%" height="500" style="border:1px solid #ddd;border-radius:8px;" loading="lazy" title="3D Gaussian Splat: bellmouth wall shear"></iframe>

[View in full screen](https://opprah-maker.github.io/splat/?s=bell_06)

### 8.5 Generation notes

- Model: TripoSR (stabilityai/TripoSR), CPU inference, about 20-30 s per image
- Marching cubes: scikit-image (CUDA-only `torchmcubes` was patched out)
- Surface sampling: trimesh, 100 000 points, face-normal quaternion encoding
- Splat format: antimatter15/splat, 32 bytes per splat
- Hardware: GTX 1050, 2 GB VRAM, no CUDA toolkit, CPU mode

The full 3D splat gallery is at <https://opprah-maker.github.io/#3d>.

---

## 9. Topics

`cfd` `ansys-fluent` `bellmouth-inlet` `gas-turbine` `aerospace-engineering` `aerodynamics`
`fluid-dynamics` `heat-transfer` `von-karman` `boundary-layer` `turbomachinery`
`engineering-simulation`
