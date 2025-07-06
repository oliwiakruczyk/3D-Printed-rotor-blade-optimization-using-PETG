# 3D-Printed Rotor Blade Optimization Using PETG

> **Numerical investigations of the influence of the filling density in 3D printing on the strength of the rotor’s blade profile**  
> *Oliwia Kruczyk – Master’s Thesis, Wrocław University of Science and Technology, 2025*

---

## ✈Why This Project?

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

## 🧪 Building the Foundation: Physical Testing

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


## 💻 Going Digital: Simulation & Modeling

With real-world data in hand, we moved into simulation. The blade model was first meshed and analyzed in **ANSYS Mechanical**, using an **orthotropic material model** derived from test data.

<p align="center">
  <img src="https://github.com/oliwiakruczyk/3d-printed-rotor-blade/assets/150608343/ghi34567890" alt="FEA Mesh" width="600"><br>
  <em>Figure 3: Blade profile meshed for structural simulation</em>
</p>

To simulate real operating conditions, **aerodynamic loads** were calculated in **ANSYS CFX**, using a **two-domain mixing-plane CFD setup**.

<p align="center">
  <img src="https://github.com/oliwiakruczyk/3d-printed-rotor-blade/assets/150608343/jkl45678901" alt="CFD Pressure" width="600"><br>
  <em>Figure 4: Pressure field on rotor blade surface</em>
</p>

These pressures were mapped back into the FEA model to replicate turbine operation—including centrifugal forces from rotation.

<p align="center">
  <img src="https://github.com/oliwiakruczyk/3d-printed-rotor-blade/assets/150608343/mno56789012" alt="von Mises Stress" width="600"><br>
  <em>Figure 5: von Mises stress distribution under combined loads</em>
</p>

---

## 🔁 Validation: Numbers Meet Reality

To verify that the simulations reflected physical behavior, FEA results were compared directly to experimental force–displacement curves:

<p align="center">
  <img src="https://github.com/oliwiakruczyk/3d-printed-rotor-blade/assets/150608343/pqr67890123" alt="Validation Plot" width="600"><br>
  <em>Figure 6: Close agreement between simulation and lab data</em>
</p>

Error levels were kept under 5 %, confirming that the simulation workflow could reliably predict blade behavior.

---

## Design Optimization

With a validated model, the final step was to **find the sweet spot**: the best trade-off between weight and strength. A parametric study revealed that:

- **80 % infill** offered the **best safety factor–to–mass ratio**
- Safety factor ≥ 1.4 was maintained across all loads

<p align="center">
  <img src="https://github.com/oliwiakruczyk/3d-printed-rotor-blade/assets/150608343/stu78901234" alt="Infill Optimization" width="600"><br>
  <em>Figure 7: Infill vs. safety factor and weight</em>
</p>

---

