# 3D-Printed-rotor-blade-optimization-using-PETG

---

## Experimental Testing

PETG samples were printed at 30%, 50%, 70% and 100% infill and tested using:

- **ASTM D638** (Tensile test)
- **ASTM D790** (Flexural test)

### Tensile Strength vs. Infill Density

![Tensile Strength Graph](plots/tensile_strength_vs_infill.png)  
*Figure 1: Increase in tensile strength with higher infill. Data averaged from 3 specimens per group.*

### Flexural Modulus vs. Infill Density

![Flexural Modulus Graph](plots/flexural_modulus_vs_infill.png)  
*Figure 2: Flexural stiffness grows significantly between 30% and 70% infill.*

---

## Simulation Models

### Mesh of the Blade Geometry in ANSYS

![FEA Mesh](plots/blade_mesh.png)  
*Figure 3: Structured mesh of the PETG blade profile.*

### CFD Simulation (ANSYS CFX) Pressure Distribution

![CFD Pressure](plots/cfd_pressure_distribution.png)  
*Figure 4: Aerodynamic pressure field on rotor blade from steady-state simulation.*

### Structural Stress from FEA (Coupled Load)

![FEA von Mises Stress](plots/fea_stress_vonmises.png)  
*Figure 5: Von Mises stress distribution due to aerodynamic and centrifugal loads.*

---

## Material Calibration & Validation

PETG material model was defined as orthotropic in ANSYS Mechanical.

### Experimental vs. Simulated Force-Displacement (Tensile)

![Tensile Validation](plots/validation_tensile_fd_curve.png)  
*Figure 6: Validation of FEA with tensile test data (100% infill sample).*

---

## Design Optimization

A parametric study was performed to determine the optimal infill for safety and weight.

###  Mass vs. Safety Factor for Various Infill Levels

![Mass vs Safety Factor](plots/mass_vs_safety_factor.png)  
*Figure 7: Optimum balance found near 80% infill (target SF ≥ 1.4).*

---

## Thesis Details

- 🎓 **Author**: Oliwia Kruczyk  
- 🏫 **University**: Wrocław University of Science and Technology  
- 📚 **Thesis Title**: *Numerical investigations of the influence of the filling density in 3D printing on the strength of the rotor’s blade profile*  


🔬 *This project supports research on low-cost renewable energy solutions using additive manufacturing and multiphysics simulation tools.*
