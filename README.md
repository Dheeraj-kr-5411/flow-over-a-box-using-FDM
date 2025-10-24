# flow-over-a-box-using-FDM
A 2D CFD simulation of laminar flow past over square obstacle using FDM in python.
OBJECTIVE: To simulate 2D incompressible flow around a square box using the Finite Difference Method (FDM) and analyze:
               1.Flow field evolution and pathlines around the obstacle.
              2.Time variation of Drag (Cᴅ) and Lift (Cʟ) coefficients.
              3.Flow behavior at different Reynolds numbers.
              
Governing Equations:
The 2D incompressible Navier–Stokes equations in Cartesian form:
![OIP](https://github.com/user-attachments/assets/0ec4ba43-aa3e-4756-b588-728ee93fbd3d)

NUMERICAL SETUP:
| Parameter           | Symbol                   | Value       |
| ------------------- | ------------------------ | ----------- |
| Domain size         | (L_x * L_y)         | 2.0 × 1.0 m |
| Grid resolution     | (n_x * n_y)         | 225 × 100   |
| Time step           | Δt                       | 0.001 s     |
| Kinematic viscosity | ν                        | 0.01 m²/s   |
| Inlet velocity      | Uₐ                       | 1.0 m/s     |
| Reynolds number     | Re = UL/ν                | ≈ 200       |
| Pressure solver     | Iterative Gauss–Seidel   |             |
| Scheme              | Explicit FDM (2nd order) |             |

Obstacle:
A square box centered in the domain from x = 0.8–1.0 and y = 0.4–0.6, modeled as a no-slip
boundary.

Lift and Drag Coefficients:
The aerodynamic coefficients are estimated from the pressure differences around the box:
CD​=2(p_front​−p_back​)/ρU^2
CL​=2(p_top​−p_bottom​)​/ρU^2
These are recorded at every time step to track vortex shedding and force oscillations.


