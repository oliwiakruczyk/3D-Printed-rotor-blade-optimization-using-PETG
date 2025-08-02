# 3D-Printed Rotor Blade Optimization Using PETG

> **Numerical investigations of the influence of the filling density in 3D printing on the strength of the rotor’s blade profile**  
> *Oliwia Kruczyk – Master’s Thesis, Wrocław University of Science and Technology, 2025*

---

## Why This Project?

With the growing demand for localized, low-cost wind energy in urban areas, small vertical-axis wind turbines (VAWTs) are becoming an attractive solution. But manufacturing strong, lightweight, and customizable rotor blades is still a challenge—especially with accessible materials like PETG and consumer-grade 3D printers.

This project set out to answer a simple but powerful question:

**How does the internal structure—infill density—of 3D-printed PETG blades affect their mechanical strength and performance in real turbine conditions?**

---

## Where We Started

We began by evaluating three common 3D printing materials: PLA, ABS, and PETG. PETG stood out for its:

- **Better ductility** than PLA  
- **Less warping** than ABS  
- **Reliable performance** under stress

Once PETG was selected, the real work began.

---
Project timeline and execution plan for the design and simulation of a 3D-printed H-Darrieus turbine blade
<img width="2123" height="1153" alt="iScreen Shoter - Microsoft Excel - 250802153738" src="https://github.com/user-attachments/assets/956a3f38-c516-4ccb-bd43-9fbd3a217838" />


## Building the Foundation: Physical Testing

To characterize the mechanical behavior of PETG, we conducted two types of standardized mechanical tests:

- **Tensile tests** (ASTM D638) — with samples printed at different **layer heights**  
- **Flexural tests** (ASTM D790) — with samples printed at different **infill densities** (30 %, 50 %, 70 %, 100 %)

The aim was to investigate how **layer resolution** and **internal structure** influence strength and stress response.

<p align="center">
  <img src="https://github.com/user-attachments/assets/fcbff8e3-eae1-4c2b-86eb-35b4cd3e3608" alt="Tensile Stress–Strain Graph" width="600"><br>
  <em>Figure 1: Stress–strain curves from tensile tests at different layer heights</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/b7da0ae9-65e7-45bc-bea9-357a47094caf" alt="Flexural Max Stress Graph" width="600"><br>
  <em>Figure 2: Maximum internal stresses under flexural loading for different infill densities</em>
</p>

### Key Insights:

- **Tensile performance** is strongly affected by **layer height** due to interlayer bonding quality — lower heights yield more ductile behavior.
- **Flexural strength** increases with **infill density**, leading to stiffer, stronger structures but at the cost of added weight.

### Comparing Test Results with Manufacturer Data

To validate material quality and printing parameters, we compared experimental results with manufacturer specifications:

- **Ultimate tensile strength**: max ~52 MPa, lower than the nominal 61.4 MPa  
- **Young’s modulus**: max ~1200 MPa, significantly below the nominal 2990 MPa  
- **Strain at failure**: exceeded the reference value of 5.3 % in several configurations

<p align="center">
  <img src="https://github.com/user-attachments/assets/81980577-1702-4f02-94cc-7e96b9bafb5a"><br>
  <em>Figure 3: Ultimate tensile strength across all configurations</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/06f85e39-696e-4ebf-80f3-4f5bbf0e87cd"><br>
  <em>Figure 4: Young’s modulus (E) for all configurations</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/ffd7fb8d-dfdc-4798-a6c0-5670619abae4" alt="Strain at Failure Comparison" width="600"><br>
  <em>Figure 5: Strain at failure (ε<sub>b</sub>) compared with nominal value</em>
</p>

These results revealed that while PETG shows lower stiffness than expected, its ductility remains high — making it suitable for components requiring energy absorption rather than rigidity.


### Best Performing Print Setup: XY_0.28

Out of the nine tested configurations, the **XY orientation** (flat on bed) with **0.28 mm layer height** demonstrated the most favorable mechanical properties:

- **Ultimate tensile strength**: 54.0 MPa  
- **Young’s modulus**: 1000 MPa  
- **Strain at failure**: 8.1 %

This configuration outperformed both thinner layers (0.1 mm and 0.2 mm) and other orientations (XZ and Z), due to two key factors:

- Alignment between **load direction and filament deposition** (XY orientation), improving interlayer bonding  
- **Thicker layers** (0.28 mm) retain more heat, enhancing thermal adhesion

These findings align with previous work by **Gibson et al. [11]** and **Ngo et al. [20]**, who showed that flat-printed specimens with larger layer heights often achieve superior mechanical performance.

---

### Infill Density Trade-Off

While tensile tests were conducted on **100 % infill** samples to measure maximum strength, this level was not practical for final blade design due to weight and time constraints.

Following both literature recommendations and experimental trends, a **70 % infill** was selected for the structural model:

Thus, **70 % infill** was chosen as a compromise between:
- Mechanical performance  
- Weight savings  
- Print time  
- Simulation realism

---

### Material Model Assumptions for Simulation

The final orthotropic PET-G material model assumes:

| Parameter                       | Value                          |
|--------------------------------|--------------------------------|
| Print orientation              | XY (flat)                      |
| Layer height                   | 0.28 mm                        |
| Infill                         | 70 % grid                      |
| Young’s modulus (XY)           | 1000 MPa                       |
| Young’s modulus (Z)            | 300 MPa                        |
| Poisson’s ratio                | 0.35 (estimated)               |
| Yield strength                 | 45 MPa (≈ 83 % of σ<sub>max</sub>) |
| Behavior                       | Elastic, orthotropic           |

This model captures the **anisotropic** nature of FDM-printed PET-G and allows accurate stress prediction under realistic operational loading.

---

## CFD Simulation Setup and Results

To simulate the aerodynamic loads acting on the 3D-printed rotor blades, a **Computational Fluid Dynamics (CFD)** model was created in **ANSYS CFX**. The goal was to obtain realistic pressure distributions for use in structural analysis.

---

### Geometry Simplification

To reduce computational complexity and focus on the 3D-printed components, the **original rotor assembly** was simplified by removing the aluminum shaft and support rods. The resulting model retained only the three twisted PETG blades and their integrated mounts.

<p align="center">
  <img src="https://github.com/user-attachments/assets/de8416b8-3a53-4a9b-aeaf-a271592764c6" width="600"><br>
  <em>Figure 9: Full rotor vs. simplified geometry for CFD and FEA</em>
</p>

---



### Mesh Strategy

The mesh was created using **Patch Conforming tetrahedral elements**, with:

- **Fine meshing** in the rotating zone  
- **Inflation layers** around blades to capture boundary layers  
- **Coarser meshing** in the outer domain to reduce computation time  

The final mesh consisted of **~5 million elements** and **~878,000 nodes**.

<p align="center">
  <img src="https://github.com/user-attachments/assets/380643b2-55c8-43d6-a028-7b8afadded22" width="600"><br>
  <em>Figure 10: Refined mesh near blades with visible boundary layers</em>
</p>

---

### Boundary Conditions

The CFD simulation used the following conditions:

- **Inlet**: 5 m/s airflow in X direction, medium turbulence  
- **Outlet**: static pressure = 0 Pa  
- **Opening**: applied to top, bottom, and sides to simulate ambient air  
- **Rotating wall**: blades with no-slip, smooth condition  
- **Interfaces**: Mixing Plane between rotor and stator domains (360° pitch)

<p align="center">
  <img src="https://github.com/user-attachments/assets/d14cac5e-b3fa-4cda-bd5a-7ae3fc9f3c7e" width="600"><br>
  <em>Figure 11: Boundary conditions and domain decomposition</em>
</p>

---

### CFD Results

Due to computational constraints, a **steady-state “frozen rotor”** model was used instead of a full 6-DOF transient setup. This choice preserves pressure distributions needed for structural loading, at a fraction of the simulation cost.

#### Velocity Field

The velocity contour plot reveals **circular acceleration** near the blade tips, with velocities reaching over **30 m/s** (6× the inlet speed). A **wake region** of reduced velocity forms behind the rotor.

<p align="center">
  <img src="https://github.com/user-attachments/assets/a6b51af7-ece3-4dd6-97c6-25cca1c4d75d" width="600"><br>
  <em>Figure 12: Velocity contour in rotor midplane — acceleration near blade tips</em>
</p>

#### Pressure Distribution

Significant **low-pressure zones** appear near the leading edges of blades, driving aerodynamic lift and rotation. Pressure differences reach up to **200 Pa** across surfaces.

<p align="center">
  <img src="https://github.com/user-attachments/assets/a7d4d280-d8be-41a4-a736-c6ed6f837a1b" width="600"><br>
  <em>Figure 13: Static pressure distribution in rotor plane</em>
</p>

#### Flow Vectors & Streamlines

Velocity vectors show **vortex shedding** and **recirculation** behind the rotor. The 3D streamlines illustrate complex **swirl patterns** near blade tips and a turbulent wake downstream.

<p align="center">
  <img src="https://github.com/user-attachments/assets/7902b379-625c-4c68-8bfd-a753774c0759" width="600"><br>
  <em>Figure 14: Velocity vectors — recirculation and wake asymmetry</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/381c176b-e596-450b-a857-84af9a221fff" width="600"><br>
  <em>Figure 15: 3D streamlines colored by velocity magnitude</em>
</p>

---

## Structural FEA Model and Coupling with CFD

To assess the structural integrity of the PET-G rotor blades under aerodynamic and inertial loading, a **Finite Element Analysis (FEA)** model was developed in **ANSYS Mechanical**.

---

### Material Model and Blade Setup

The rotor blades were printed in **XY orientation**, with **0.28 mm layer height** and **70 % grid infill**. To reflect the anisotropic nature of 3D-printed PET-G, a **linear orthotropic elastic model** was implemented.

| Property                          | Value         |
|----------------------------------|---------------|
| Young’s modulus (XY)             | 700 MPa       |
| Young’s modulus (Z)              | 210 MPa       |
| Shear modulus (XY)               | 280 MPa       |
| Shear modulus (XZ, YZ)           | 140 MPa       |
| Poisson’s ratio (XY / others)    | 0.35 / 0.30   |
| Density                          | 910 kg/m³     |
| Yield strength                   | 31.5 MPa      |

<p align="center">
  <img src="https://github.com/user-attachments/assets/11b2d684-7dba-4da7-a4a3-c698758f30c3" width="600"><br>
  <em>Figure 16: Finite element mesh of the rotor blade with local refinements</em>
</p>

---

### Boundary Conditions and Loads

- **Fixed supports** were applied at the blade roots  
- A **rotational speed** of 37.5 rad/s was defined around the turbine axis  
- **Standard gravity** (9.81 m/s²) was applied in Z-direction  
- **Aerodynamic pressure field** from CFD was mapped directly onto blade surfaces

<p align="center">
  <img src="https://github.com/user-attachments/assets/ce0ecb0f-422a-4f8c-8f9f-3a3b218fbcbe" width="600"><br>
  <em>Figure 17: Applied boundary conditions </em>
</p>

---

### FEA Results

#### Total Deformation

Maximum blade displacement: **~3.04 mm**, observed at the upper tip.  
Deformation remained within acceptable limits.

<p align="center">
  <img src="https://github.com/user-attachments/assets/7a530100-8ded-446d-8cb6-13947463e3b7" width="600"><br>
  <em>Figure 18: Total deformation of rotor blades</em>
</p>

#### Equivalent Stress (von Mises)

Peak equivalent stress: **~22.04 MPa**, concentrated near upper blade surfaces.  
Static safety factor: **31.5 / 22.04 ≈ 1.43**

<p align="center">
  <img src="https://github.com/user-attachments/assets/f07f1c2c-fa60-4a1c-9121-b97842a4204d" width="600"><br>
  <em>Figure 19: von Mises stress distribution under combined loading</em>
</p>

#### Principal Stress

Maximum principal stress: **~20.79 MPa**, located near high curvature zones.  
Stress concentrations correlate with von Mises hotspots.

<p align="center">
  <img src="https://github.com/user-attachments/assets/ac694b00-5379-4b47-97b8-dd93e5c623ae" width="600"><br>
  <em>Figure 20: Maximum principal stress in blade </em>
</p>

---

### Interpretation and Design Feedback

- **The structure remained elastic** under combined centrifugal and aerodynamic loading  
- However, the **safety factor ~1.43** is relatively tight — especially for 3D-printed parts  
- Stress hotspots suggest the need for:
  - Fillets near blade–hub transitions  
  - Higher infill ratios (e.g., 80 %)  
  - Improved print quality to reduce voids and layer delamination risk

---

### Summary of Coupled CFD–FEA Results
<p align="center">
| Metric                                | Value        |
|--------------------------------------|--------------|
| Max tangential velocity (CFD)        | 12.8 m/s     |
| Max pressure difference (CFD)        | 200 Pa       |
| Max total deformation (FEA)          | 3.04 mm      |
| Max von Mises stress (FEA)           | 22.04 MPa    |
| Max principal stress (FEA)           | 20.79 MPa    |
| Yield strength (PET-G, 70 % infill)  | 31.5 MPa     |
| Static safety factor (FEA)           | ≈ 1.43       |

---
</p>
### Design Implications

- **Reserve strength**: raising infill to 80–90 % or adding ribs would improve safety  
- **Dynamic effects**: future work should include **harmonic or transient analysis**  
- **Print variability**: quality control is critical — a 15 % material drop breaks the margin

---

*Conclusion: PET-G blades printed in XY orientation with 70 % infill safely withstand steady aerodynamic and inertial loads — but margin is limited. Future design iterations should improve geometry and manufacturing robustness.*


## Design Optimisation: Finding the Ideal Infill

To balance structural integrity and material efficiency, a parametric optimisation study was carried out to identify the optimal **infill density** for the 3D-printed PET-G rotor blades.

### Objectives and Constraints

The optimisation sought to:

- Maximise the **safety factor** (σ<sub>Y</sub>/σ<sub>vM,max</sub>)
- Minimise the **blade mass**
- Keep **tip deformation** under 5.0 mm

Infill densities below **70 %** were excluded due to excessive deformation. Densities above **90 %** yielded diminishing returns in strength.

---

### Methodology

- **Design variable**: infill density (ρ<sub>infill</sub>), varied from 70 % to 90 % in 5 % steps  
- **Material properties**: scaled linearly with ρ<sub>infill</sub>  
- **Load inputs**: aerodynamic pressure from CFD + rotational inertia + gravity  
- **Simulations**: FEA sweeps in ANSYS Workbench with consistent geometry and mesh

<p align="center">
  <img src="https://github.com/user-attachments/assets/ac694b00-5379-4b47-97b8-dd93e5c623ae" width="600"><br>
  <em>Figure 21: Safety factor (blue) and blade mass (red) vs. infill density</em>
</p>

---

### Key Results
<p align="center">
| Infill [%] | Mass [kg] | Deformation [mm] | σ<sub>vM,max</sub> [MPa] | SF   |
|------------|-----------|------------------|--------------------------|-------|
| 70         | 13.63     | 3.80             | 22.04                    | 1.43  |
| 75         | 15.65     | 3.94             | 23.39                    | 1.45  |
| 80         | 17.80     | 4.09             | 24.74                    | 1.45  |
| 85         | 20.10     | 4.24             | 26.12                    | 1.47  |
| 90         | 22.53     | 4.38             | 27.59                    | 1.47  |

---
</p>
### Interpretation & Trade-offs

- Safety factor **saturates** at ~1.45–1.47 beyond 80 % infill  
- Blade **mass increases linearly**, ~0.45 kg per +5 % infill  
- **All variants** meet deformation and strength criteria  
- Gains in SF beyond 80 % are **marginal**, while **mass penalty grows**

 **80 % infill** offers the **best compromise** between mass and safety.

---

### Final Recommendation

- **Selected configuration**: 80 % grid infill, PET-G, XY orientation, 0.28 mm layers  
- **Safety factor**: 1.45  
- **Blade mass**: 17.8 kg  
- **Max deformation**: 4.09 mm  

This configuration meets all design constraints while maintaining printability and simulation compatibility. Higher infill levels add weight without meaningful stress reduction, while lower infill compromises strength margins.

---

### Limitations & Future Work

> Although the results are robust, simplifications remain.

- Linear scaling of material properties (nonlinear behavior not captured)  
- Steady-state CFD input (no dynamic loads, gusts, or startup torque)  
- No thermal/humidity sensitivity or layer adhesion defects  
- No fatigue or resonance analysis

### Suggested Extensions

- **Spin testing** with displacement tracking  
- **Transient CFD–FEA** coupling  
- **Fiber-reinforced PET-G** for improved stiffness  
- **Topology or gradient infill optimisation**  
- **Fatigue testing** under cyclic wind loading

---

*Conclusion: The 80 % infill blade delivers optimal strength-to-mass performance for printed PET-G turbines and provides a reliable, manufacturable design for prototyping and deployment.*







