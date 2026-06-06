# Bellmouth Inlet &mdash; CFD Optimisation for a Gas Turbine

> Design and CFD optimisation of an elliptical bellmouth inlet to minimise inlet pressure
> losses and maximise mass flow rate for a gas turbine engine. Solved in ANSYS Fluent
> with the standard $k-\epsilon$ turbulence model.

[![ANSYS Fluent](https://img.shields.io/badge/ANSYS%20Fluent-CFD-FFB71B?logo=ansys&logoColor=black)]()
[![Bellmouth](https://img.shields.io/badge/Geometry-Elliptical%20inlet-blue)]()
[![Report PDF](https://img.shields.io/badge/Report-PDF-red?logo=adobe-acrobat-reader&logoColor=white)]()

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
| Baseline Design &mdash; Bellmouth inlet CFD | [`reports/Baseline-Design.pdf`](reports/Baseline-Design.pdf) |

Plain-text extract: [`reports/Baseline-Design_text.txt`](reports/Baseline-Design_text.txt).

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
| Symmetry plane | Symmetry | &mdash; |

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

## 7. Figure Gallery

<table>
<tr><td align="center"><img src="images/figure-01.png" width="240" alt="figure-01.png"/><br/><sub>figure-01.png</sub></td><td align="center"><img src="images/figure-02.jpeg" width="240" alt="figure-02.jpeg"/><br/><sub>figure-02.jpeg</sub></td><td align="center"><img src="images/figure-03.png" width="240" alt="figure-03.png"/><br/><sub>figure-03.png</sub></td><td align="center"><img src="images/figure-04.jpeg" width="240" alt="figure-04.jpeg"/><br/><sub>figure-04.jpeg</sub></td></tr>
<tr><td align="center"><img src="images/figure-05.png" width="240" alt="figure-05.png"/><br/><sub>figure-05.png</sub></td><td align="center"><img src="images/figure-06.jpeg" width="240" alt="figure-06.jpeg"/><br/><sub>figure-06.jpeg</sub></td><td align="center"><img src="images/figure-07.png" width="240" alt="figure-07.png"/><br/><sub>figure-07.png</sub></td><td align="center"><img src="images/figure-08.png" width="240" alt="figure-08.png"/><br/><sub>figure-08.png</sub></td></tr>
<tr><td align="center"><img src="images/figure-09.png" width="240" alt="figure-09.png"/><br/><sub>figure-09.png</sub></td><td align="center"><img src="images/figure-10.png" width="240" alt="figure-10.png"/><br/><sub>figure-10.png</sub></td><td align="center"><img src="images/figure-11.png" width="240" alt="figure-11.png"/><br/><sub>figure-11.png</sub></td><td align="center"><img src="images/figure-12.png" width="240" alt="figure-12.png"/><br/><sub>figure-12.png</sub></td></tr>
<tr><td align="center"><img src="images/figure-13.png" width="240" alt="figure-13.png"/><br/><sub>figure-13.png</sub></td><td align="center"><img src="images/figure-14.png" width="240" alt="figure-14.png"/><br/><sub>figure-14.png</sub></td><td align="center"><img src="images/figure-15.png" width="240" alt="figure-15.png"/><br/><sub>figure-15.png</sub></td><td align="center"><img src="images/figure-16.png" width="240" alt="figure-16.png"/><br/><sub>figure-16.png</sub></td></tr>
<tr><td align="center"><img src="images/figure-17.jpeg" width="240" alt="figure-17.jpeg"/><br/><sub>figure-17.jpeg</sub></td><td align="center"><img src="images/figure-18.png" width="240" alt="figure-18.png"/><br/><sub>figure-18.png</sub></td><td align="center"><img src="images/figure-19.jpg" width="240" alt="figure-19.jpg"/><br/><sub>figure-19.jpg</sub></td><td align="center"><img src="images/figure-20.jpg" width="240" alt="figure-20.jpg"/><br/><sub>figure-20.jpg</sub></td></tr>
<tr><td align="center"><img src="images/figure-21.jpg" width="240" alt="figure-21.jpg"/><br/><sub>figure-21.jpg</sub></td><td align="center"><img src="images/figure-22.jpg" width="240" alt="figure-22.jpg"/><br/><sub>figure-22.jpg</sub></td><td align="center"><img src="images/figure-23.jpg" width="240" alt="figure-23.jpg"/><br/><sub>figure-23.jpg</sub></td></tr>
</table>

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
