# Elliptical Bellmouth Inlet Design and CFD Optimization for Gas Turbine Aero-Engines

This repository contains the design, simulation setup, and quantitative CFD analysis of an optimized elliptical bellmouth inlet for a gas turbine aero-engine. The objective of this study is to minimize pressure losses and maximize mass flow rate at the compressor inlet under various operating conditions.

---

## 🎯 Quantitative Design Parameters
* **Inlet Geometry**: Elliptical profile.
  * **Inlet Diameter ($D_i$)**: $322.2\text{ mm}$
  * **Exit Diameter ($D_e$)**: $150\text{ mm}$ (Throat)
  * **Contour Ratio**: Exit diameter is $2.14$ times smaller than the inlet diameter to achieve a smooth area convergence.
* **Fluid Properties**: Air at standard sea-level conditions.
  * **Density ($\rho$)**: $1.2256 \text{ kg/m}^3$
  * **Pressure ($P$)**: $101,325 \text{ Pa}$
  * **Target Inlet Mass Flow Rate ($\dot{m}$)**: $1.0\text{ kg/s}$
  * **Design Inlet Freestream Velocity**: $90\text{ m/s}$

---

## 📐 Governing Physical & Numerical Models

### 1. Mathematical Framework
Flow behavior through the convergent bellmouth is governed by Bernoulli's principle for inviscid, incompressible flow:
$$P_1 + \frac{1}{2}\rho v_1^2 = P_2 + \frac{1}{2}\rho v_2^2 = \text{Constant}$$

To capture turbulence and boundary layer effects, the viscous **Standard $k-\epsilon$ (SKE)** turbulence model was solved:

* **Turbulent Kinetic Energy ($k$) transport**:
  $$u_i \frac{\partial k}{\partial x_i} - \frac{\partial}{\partial x_i} \left[ \left(\nu + \frac{\nu_t}{\sigma_k}\right) \frac{\partial k}{\partial x_i} \right] = P_k - \epsilon$$

* **Dissipation ($\epsilon$) transport**:
  $$u_j \frac{\partial \epsilon}{\partial x_i} - \frac{\partial}{\partial x_i} \left[ \left(\nu + \frac{\nu_t}{\sigma_\epsilon}\right) \frac{\partial \epsilon}{\partial x_i} \right] = \frac{\epsilon}{k} C_{1\epsilon} P_k - C_{2\epsilon} \frac{\epsilon^2}{k}$$

Where model constants are: $C_\mu = 0.09$, $C_{1\epsilon} = 1.44$, $C_{2\epsilon} = 1.92$, $\sigma_k = 1.0$, $\sigma_\epsilon = 1.3$.

### 2. Mesh & Grid Discretization
* **Topology**: Unstructured triangular mesh.
* **Elements**: $7,805$ elements, $4,085$ nodes.
* **Mesh Metrics**:
  * **Orthogonal Quality**: $> 95\%$ (ideal for convergence)
  * **Skewness**: $< 0.1$

### 3. Boundary Conditions
* **Inlet**: Pressure Inlet, Gauge Total Pressure = $101,325\text{ Pa}$.
  * Turbulent Intensity = $5\%$
  * Turbulent Viscosity Ratio = $10$
* **Outlet**: Pressure Outlet, $P_{\text{outlet}} = 96,366.32\text{ Pa}$ (derived from Bernoulli's equation for a throat velocity of $90\text{ m/s}$).
* **Walls**: Stationary, No-Slip condition ($\vec{v} = 0$). Roughness height set to $0$ and roughness constant $C_s = 0.5$.

---

## 📊 CFD Simulation Results & Contours
All contours were generated using ANSYS Fluent post-processing and are saved under the `images/` directory:

1. **Static Pressure Distribution**: Displays high static pressure accumulation at the wide elliptical inlet ($101,325\text{ Pa}$) transitioning to a low static pressure region at the throat due to flow acceleration.
2. **Dynamic Pressure Contour**: Illustrates the buildup of dynamic pressure as the flow accelerates through the convergent nozzle.
3. **Velocity Magnitude Contour & Vector Plots**: Confirms the boundary layer no-slip condition along the walls and illustrates smooth, unseparated streamlines entering the compressor face.
4. **Wall Shear Stress**: Illustrates that shear stress remains near zero in the bellmouth inlet but increases near the nozzle throat due to high velocity gradients ($\frac{\partial u}{\partial y}$).

*Check out the [Images Folder](file:///C:/Users/LLM-Test/.gemini/antigravity-ide/scratch/opprah-portfolio/Bellmouth-Inlet-CFD-Gas-Turbine/images/) for the simulation results.*
